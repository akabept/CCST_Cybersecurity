<title charset="UTF-8">ICMP Router Discovery Hijacking</title>

# ICMP Router Discovery Hijacking
ICMP Router Discovery Protocol (IRDP) enables hosts to discover routers on their networks by listening for “router advertisement” broadcasts. However, this protocol has a vulnerability that can be exploited to inject hacked paths in routing tables.

## Spoofed Router Advertisements
An attacker can send spoofed IRDP router advertisement messages to a host, causing it to change its default route to a malicious gateway. This can result in a complete denial-of-service (invalid default gateway) or susceptibility to passive sniffing and/or man-in-the-middle attacks (gateway controlled by the attacker).

## How Attackers Inject Hacked Paths
1. Router Advertisement Spoofing: An attacker sends forged IRDP router advertisements to a host, claiming to be a legitimate router on the network.
2. Host Accepts Spoofed Advertisement: The host updates its routing table with the spoofed router’s IP address as the default gateway.
3. Malicious Gateway Established: The attacker controls the spoofed router, allowing them to intercept and manipulate network traffic.

## Mitigation Strategies
1. Disable IRDP: Disable IRDP on hosts and routers to prevent exploitation.
2. Implement Authentication: Implement authentication mechanisms, such as IPsec or TLS, to verify the authenticity of router advertisements.
3. Monitor Network Traffic: Regularly monitor network traffic for suspicious activity and detect potential attacks.

## Conclusion
ICMP Router Discovery Protocol’s vulnerability to spoofed router advertisements can be exploited to inject hacked paths in routing tables. To mitigate this risk, disable IRDP, implement authentication, and monitor network traffic for suspicious activity.