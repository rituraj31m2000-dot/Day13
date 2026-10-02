# TCP vs UDP Comparison – Veda Technology Internship (Day 13)

## Objective
Understand transport-layer protocols by comparing TCP and UDP and identifying where each is appropriate.

## Tools Used
- Wireshark
- Web Browser

## What is TCP?
Transmission Control Protocol is a connection-oriented, reliable transport protocol. It sets up a connection with a 3-way handshake (SYN, SYN-ACK, ACK), numbers data segments, acknowledges delivery, retransmits lost packets, and provides flow and congestion control.

## What is UDP?
User Datagram Protocol is a connectionless, lightweight transport protocol. It sends datagrams without a handshake, acknowledgements, or retransmission. It is fast, but delivery and ordering are not guaranteed.

## Comparison

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (ACKs, retransmission) | Unreliable (best effort) |
| Ordering | Guaranteed | Not guaranteed |
| Speed | Slower | Faster |
| Overhead | High (20+ byte header) | Low (8 byte header) |
| Flow/Congestion control | Yes | No |
| Examples | HTTP/HTTPS, FTP, SSH, SMTP | DNS, DHCP, VoIP, video streaming, online games |

## Wireshark Observation
1. Opened a website in the browser while capturing in Wireshark.
2. Filter `tcp`: observed the 3-way handshake (SYN → SYN-ACK → ACK), sequence/ACK numbers, and the FIN/ACK teardown.
3. Filter `udp` (or `dns`): observed DNS queries and responses sent with no handshake and no acknowledgement.

*(Add screenshots here: `screenshots/tcp-handshake.png`, `screenshots/udp-dns.png`)*

## When is UDP preferred?
When speed and low latency matter more than perfect reliability, for example live streaming, VoIP, online gaming, and DNS lookups. A dropped packet is better skipped than delayed by a retransmission.

## Security Notes
- TCP: exposed to SYN flood attacks.
- UDP: exposed to UDP flood and amplification/reflection attacks (e.g. DNS amplification) because there is no handshake to verify the sender.

## Conclusion
TCP is the right choice when accuracy and reliability matter. UDP is the right choice when speed and low overhead matter. The choice depends on the application's needs.
