## Virtual Memory

We have a need to run programs that are too large to fit entirely in memory.

The idea of virtual memory, that that each program has its own address space,
which is broken up into chunks called pages. Each page is a contiguous range of
addresses. These pages are mapped onto physical memory but not all pages have
to be in physical memory at the same time to run the program.

When a program references a part of its address space that is in physical
memory, the hardware performs the necessary mapping on the fly. When the program
references a part of its address space that is not in physical memory, the
operating system is altered to go get the missing piece and re-execute the instruction
that failed.

### Paging

Most virtual memory systems use a technique called paging. On any computer, programs
reference a set of memory addresses. When a program executes an instruction like
`MOV REG,1000`, it does so to copy the content of a memory address `1000` to `REG`.

- The CPU sends virtual memory addresses to the MMU
- The MMU sends physical addresses to the memory

These program generated addresses are called _virtual addresses_ and form the virtual
address space. On computers without virtual memory, the virtual address is put directly
onto the memory bus and causes the physical memory word with the same address to be read
or written.

When virtual memory is used, the virtual addresses do not go directly to the memory bus.
Instead they go to an _MMU_ or _Memory Management Unit_ that maps the virtual addresses
onto the physical memory addresses.

Virtual address space consists of fixed-size units called pages. The corresponding
units in the physical memory are called _page frames_. Pages and page frames are generally
the same size. Transfers between RAM and disk are always in whole frames.

#### Page Tables

In a simple implementation, the mapping of virtual addresses onto physical addresses can
be summarized as follows: the virtual address is split into a virtual page number and an
offset. For example, with a 16-bit address and a 4kb page size, the upper 4 bits could specify
one of the 16 virtual pages and the lower 12 bits would then specify the byte offset (0-4095) within
the selected page. However a split with 3 or 5 or some other number of bits for the page is also
possible.

The virtual page number is used as an index into the page table to find the entry for
that virtual page. Fomr the page table entry, the page frame number (if any) is found. The
page frame number is attached to the high order end of the offset, replacing the virtual
page number, to form a physical address that can be send to the memory.

The purpose of a page table is to map virtual pages onto page frames.

#### Translation Lookaside Buffers

Consider a 1-byte instruction that copies one register to another. Without paging,
this instruction only takes on memory reference, to fetch the instruction. With paging,
at least one additional memory reference will be needed, to access the page table.
This would effectively reduce memory performance by half and nobody would consider
using paging.

The solution to this problem is based on the observations that most programs tend to make a large
number of references to a small number of pages. Only a small fraction of the page table
entries are heavily read, the rest are barely used.

The solution is to equip computers with a small hardware device for mapping virtual addresses
to physical addresses without going through a page table. The device is called a
_TLB (Translation Lookaside Buffer)_. It is usually inside the MMU and consists of
a small number of entries, rarely more than 256. Each enrty contains information about one page,
including the virtual page number, a bit that is set when the page is modified, the protection
code (read/write/execute permissions), and the physical page frame in which the page is located.

When a virtual address is presented to the MMU for translation, the hardware first checks to
see if its virtual page number is presented in the TLB by comparing it to all the entries
simultaneously. This requires special hardware which all MMUs with TLBs have.
If a valid match is found and the access does not violate the protectin bits, the page
frame is taken directly from the TLB, without going to the page table. If the virtual page number
is present in the TLB but the instruction is trying to write on a read-only page,
a protection fault is generated.

When the virtual page number os not in the TLB, the MMU detects the miss and does an ordinary page
table lookup. It then evicts one of the entries from the TLB and replaces it with
the page table entry that was just looked up. Thus if the page is used again soon, the lookup
will result in a TLB hit rather than a miss. When an entry is purged from the TLB,
the modified bit is copied back into the page table entry in memory. The other avlues are already there,
except the reference bit.

#### Multilevel Page Tables

Multilevel page tables allow for many more addresses to be stored. For example,
we have a 32-bit address that is partitioned into a 10-bit `PT1` field, a 10-bit
`PT2` field, and a 12 bit offset field. `PT1` references the index in the first table
and `PT2` references the index in the second table. If pages are 4kb, this gives us
$2^20$ of them.

The trick to multilevel page tables is to avoid keeping all the page tables in memory
at the same time. Those that are not needed should not be kept around.

#### Inverted Page Tables

An alternative to increasing levels in a paging hierarchy is known as _inverted page tables_.
In this design, there is one entry per page frame in real memory, rather than one entry
per page of virtual address space. For example, with 64-bit virtual addresses, a 4kb page
size, and 4GB of TAM, an inverted page table requires only 1,048,576 entries.
The entry keeps track of which (process, virtual page) is located in the page frame.

Although inverted page tables save lots of space, at least when the virtual address space is much
larger than the physical memory, they have a serious downside. Virtual-to-physical
translation becomes much harder. When process n references virtual page p, the hardware can no longer find
the physical page by using p as an index into the page table. Instead, it must search
the entire inverted page table for an entry (n, p). Furthermore, this search must
be done on every memory reference, not just page faults.

The way out of this dilemma is to make use of the TLB. If the TLB can hold all of the
heavily used pages, translation can happen just as fast as with regular page tables.
On a TLB miss, however, the inverted page table has to be searched in software.
