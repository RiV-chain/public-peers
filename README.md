# v6Space Public Peers

This repository contains peering information for publicly accessible nodes on
the v6Space™ decentralized overlay network.

Note that not all peers in this repository are guaranteed to be online. In most cases, public peers should be accessible by adding the string provided
for each peer to the `Peers: []` section of your `mesh.conf` configuration
file.

Example in `mesh.conf`:
```
Peers:
[
  tcp://a.b.c.d:e
  tcp://d.c.b.a:e
  tcp://[a:b:c::d]:e
  tcp://[d:c:b::a]:e
]
```

### How do I add more peers?

Always try to pick peers that are as close to you geographically as possible, as
this will keep the latency of the decentralized overlay network down.

If you are using a home connection then you should avoid peering with any nodes
that are far away, as you may end up carrying traffic for the rest of the
decentralized mesh network.

For normal usage, you probably only need 2 or 3 peers.

### TLS Peers

Peering connections over TLS (Transport Layer Security) are fully supported. This advanced peering method encapsulates the v6Space™ mesh protocol within a standard TLS 1.3 session, providing enhanced security and network compatibility.

#### Benefits of TLS Peering:

**Firewall Bypass**: TLS peering helps bypass restrictive firewalls and corporate networks that may block or throttle standard mesh traffic by making v6Space™ connections appear as regular HTTPS traffic.

**Deep Packet Inspection Evasion**: Advanced network monitoring systems using DPI (Deep Packet Inspection) cannot easily identify or block v6Space™ traffic when it's wrapped in TLS, as it appears identical to standard web traffic.

**Enhanced Security**: TLS provides an additional layer of encryption on top of v6Space™'s built-in end-to-end encryption, creating a double-encrypted tunnel for maximum security.

**Network Compatibility**: TLS peering works through most proxy servers, load balancers, and enterprise network infrastructure that may interfere with raw TCP connections.

#### Configuration:

TLS public peers are identified by the prefix `tls://` instead of `tcp://`:

```
Peers:
[
  tls://peer.example.com:443
  tls://[2001:db8::1]:443
  tcp://backup-peer.example.com:19019
]
```

#### Performance Considerations:

- **Latency**: TLS handshake adds ~50-100ms initial connection time
- **CPU Overhead**: Additional encryption/decryption uses ~5-10% more CPU
- **Bandwidth**: TLS adds minimal overhead (~1-2% due to padding and headers)
- **Reliability**: TLS connections are generally more stable through NAT/firewalls

#### When to Use TLS Peering:

- **Corporate Networks**: Behind restrictive enterprise firewalls
- **Public WiFi**: Hotels, airports, cafes with traffic filtering
- **Censored Regions**: Countries with internet restrictions
- **High-Security Environments**: When maximum encryption is required
- **Backup Connectivity**: As fallback when standard peering fails


### Security Considerations

- Only connect to trusted peers from reputable sources
- Verify peer addresses before adding them to your configuration
- Use TLS connections when possible for enhanced security
- Regularly update your peer list to maintain network connectivity
- Monitor your network traffic and peer connections

### Support

For more information about v6Space™ and peer management:
- [v6Space GitHub Repository](https://github.com/RiV-chain/v6Space)
