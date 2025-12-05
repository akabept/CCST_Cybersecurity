# DHCP (Dynamic Host Configuration Protocol) Ports
DHCP (Dynamic Host Configuration Protocol) relies on two well-known ports: UDP (User Datagram Protocol) ports 67 and 68. These ports serve distinct purposes, facilitating communication between DHCP servers and clients.

## Port 67: DHCP Server Port
* Used by the DHCP server to listen for client requests
* Receives DHCPDISCOVER messages from clients and responds with DHCPOFFER messages
* Essential for the server-side functionality of DHCP

## Port 68: DHCP Client Port
* Used by DHCP clients to send requests to the DHCP server
* Sends DHCPREQUEST messages to the server and receives DHCPACK (acknowledgment) or DHCPNAK (negative acknowledgment) responses
* Crucial for client-side functionality, enabling devices to obtain IP addresses and network configurations

## Summary
In summary, the primary difference between ports 67 and 68 is their direction of communication:
* Port 67 is the server-side port, where the DHCP server listens for and responds to client requests.
* Port 68 is the client-side port, where devices send requests to the DHCP server and receive responses.

This distinction ensures seamless communication and IP address assignment within a network, making DHCP a vital protocol for modern network infrastructures.