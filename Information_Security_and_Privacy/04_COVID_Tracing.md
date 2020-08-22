# COVID-19 Contact Tracing

## Centralised Approach

- Each device has a unique ID, probably downloaded from a central server.
- Your device broadcasts your ID over Bluetooth to surrounding devices.
- These IDs are sent back to the central server, generating a graph of interactions between people.

## Decentralised Approach

- Unique ID is typically generated on your device.
- IDs are broadcast in the same way as a centralised approach.
- If someone was to test positive, they would send their data to the server.
- The server can then broadcast these IDs.
- All of the matching is completed on the device, not the server.

## Venue Checking

- Privacy issues arise when venues are responsible for personal details of customers.
  - Is this being handled by a separate entity.
  - Details could simply be written on a piece of paper for everyone to see.
- This data is then handled the same way as before, being centralised or decentralised.
