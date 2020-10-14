# Malware

Malware is malicious software. This is different from harmful software that inadvertently causes damage due to design or implementation error.

## Viruses and Worms

### Viruses

- A virus is a computer program that can infect other programs or files by modifying them to include a possibly evolved copy of itself.
- Executed when the host program is run or an infected file is processed.
- Dormant until executed.
- With a certain trigger condition the virus' payload is executed.

### Worms

- Similar to viruses byt different in three ways.
- They propagate continuously without user interaction.
- They spread over networks.
- They exploit software vulnerabilities.
- Worm and virus are often used interchangeably.

#### The Morris Worm (1998)

- Infected 10% of internet devices.
- Led to a denial of service as it overloaded networks.
- Exploited bugs in the Unix finger daemon, sendmail, rsh, and weak passwords.

### Email Based Malware

- Combines both worm and virus properties.
  - Spreads over a network like a worm.
  - Exploits a software vulnerability in the email client like a worm.
  - Infects files like a virus.
  - Spreads through user interaction like a virus.
- Example: ILOVEYOU
  - Spread to users by opening an attachment in MS Outlook that was a VB script.
  - Spread by emailing to each address in the host computer's Outlook addressbook.

## Trojans

- Malware that hides in what users believe to be legitimate software.
- Does not modify executables or files on the host device or propagate themselves like worms.

## Backdoors

- Backdoors allow access to a device bypassing normal authentication mechanisms.
- Often allows some sort of remote administration.
- Can be embedded in a legitimate program or be standalone.
- Often part of a trojan.
- Hardware backdoors are tiny chips added to a device either during manufacturing or at some other point.

## Rootkits

- Remains hidden.
- Controls or manipulates applications or host OS.
- Long term.
- Payload is typically malware such as:
  - A backdoor.
  - A keylogger.
  - Surveillance software for microphones, cameras, sensors, etc.

## Browser Malware

- Largely focused on a push model.
- Drive-by downloads are a pull model.
- Exploits browser-server interaction.
- Exploits browser vulnerabilities.
- Often involves installation of keyloggers, backdoors, and rootkits.
- Often embedded in:
  - Web page ads.
  - Web widgets.
  - Malicious parameters as part of links received in HTML email.

## Ransomware

- Extorts users.
- Two broad types:
  - Encrypts files and demands Bitcoin payment for private key to decrypt.
  - Malware makes files or OS unstable unless payment is made.

## Botnets/Zombies

- Infected computer that can be remotely controlled and reports back to the controlling network.
- A coordinated network of bots.
- Bots further spread the malware, increasing the size of the botnet.
- Used to:
  - Carry out DDoS attacks.
  - Spam campaigns.
  - Install keyloggers.
- Botnets can be rented out.

## Zero-day Exploits

- An attack that exploits a software vulnerability unknown to the developers, users, and public.
- The day the vulnerability becomes publicly known is the day of the first attack.
- There are no fixes, patches, updates that fix it until after the attack is made.

## Intrusion Detection Systems

- Firewalls try to block malicious traffic.
- IDS helps identify what gets through.
- IDS automated system monitoring events, logs, and reporting.
- Used to identify what happened in the event of an attack.
- Passive monitoring.
- Collects events from two sources:
  - Network based, network gateway.
  - Host based.
    - Kernel logs.
    - Application logs.
    - Filesystem changes.
    - Network traffic.
    - Resource use patterns.

## Intrusion Prevention Systems

- Seeks to stop attacks.
- Active monitoring.
- Modify a firewall to stop attacks.
- e.g. fail2ban
- Most modern systems use both IDS to identify an attack and an IPS to stop it.
