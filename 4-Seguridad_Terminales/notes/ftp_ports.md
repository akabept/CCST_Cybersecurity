# FTP (File Transfer Protocol) Ports
FTP (File Transfer Protocol) uses two primary TCP ports: Port 20 and Port 21. Understanding their distinct roles is crucial for configuring FTP services and troubleshooting connectivity issues.

## Port 20: Data Transfer Port
* Used for transferring data files between an FTP client and server
* Enables the actual movement of files between the client and server
* Typically used for active mode FTP sessions, where the server initiates a connection to the client's random port

## Port 21: Command and Control Port
* Used for sending commands and receiving responses to control the FTP session
* Establishes the initial connection between the FTP client and server
* Automatically opens to transfer file data in passive mode FTP sessions

## Summary
In summary, Port 20 is dedicated to data transfer, while Port 21 handles command and control functions. This separation allows for efficient and secure file transfer operations.