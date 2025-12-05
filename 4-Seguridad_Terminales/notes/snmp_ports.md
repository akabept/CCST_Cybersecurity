# SNMP (Simple Network Management Protocol) communication ports
SNMP (Simple Network Management Protocol) uses two primary ports for communication: 
* UDP 161
* UDP 162

## Port 161 (Default)
* Used by SNMP agents for receiving requests from SNMP managers
* Default port for SNMP agents to listen for incoming queries and commands
* Agents respond to requests from managers on this port

## Port 162 (Trap Port):
* Used by SNMP agents for sending asynchronous notifications (traps) to SNMP managers
* Managers listen on this port for incoming trap messages, which contain event notifications or error reports
* Traps are used for unsolicited notifications, such as device failures or configuration changes

## Summary
In summary, Port 161 is used for:
* Request-response communication between SNMP managers and agents
* Agent-to-manager polling and command execution

Port 162 is used for:
* Asynchronous notification of events or errors from agents to managers (traps)

Both ports operate over UDP, ensuring efficient and lightweight communication for SNMP-based network management.