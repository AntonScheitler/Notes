## Tasks of the Link Layer
- The link layer is responsible for connecting a device to a local area network and moving data across a single hop
- Link layer technologies, such as cellphone towers and wifi networks, are often used my multiple devices at the same location
- Some technologies, such as fiber optic cables are not shared and only used to send data across routers
- The link layer thus has to deal with encoding, transmitting and coordinating the data traffic
## Packet Transmission
- In order to enable each computer to send packets across the internet, they implement the Carrier Sense Multiple Access with Collision Detection (CSMA/CD)
- Each computer listens, to see if the network is busy
- If it is not, a computer starts sending data, while simultaneously listening to see, if it can receive it's own data
- If it cannot, the network is busy and the computer waits before trying again
- Once a computer has finished sending a packet, it pauses, so that other devices get a chance to send theirs