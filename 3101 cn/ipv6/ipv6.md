# what is ipv6
Internet Protocol version 6 (IPv6) is the most recent version of the Internet Protocol (IP), developed by the Internet Engineering Task Force IETF to deal with the long-anticipated problem of IPv4 address exhaustion. It uses 128-bit addresses, yielding an address space of $2^128$ addresses. 
IPv6 addresses are represented as eight groups of four hexadecimal digits each, separated by colons. example `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
# What is the hexadecimal representation used in IPv6?
An IPv6 address uses a 128-bit number represented as **eight groups of four hexadecimal digits** separated by colons `x:x:x:x:x:x:x:x`.
- **Length:** 128 bits total, split into **eight 16-bit blocks** (called hextets or quartets).

- **Separators:** Each of the eight blocks is separated by a **colon (`:`)**.

- **Hex Digits:** Each 16-bit block contains **four hexadecimal characters** (for a total of 32 hex characters across the entire address).

- **Character Set:** Uses numbers **`0–9`** (representing values 0 through 9) and letters **`A–F`** or **`a–f`** (representing values 10 through 15). Hexadecimal characters are not case-sensitive.

- **Nibble Mapping:** Each single hexadecimal character represents a **4-bit nibble** (4 bits × 32 characters = 128 bits).
# What is the purpose of the :: notation in IPv6?
The `::` (double colon) notation in IPv6 is used to **compress consecutive blocks of all-zero 16-bit groups (hextets)**, shortening long addresses and making them easier to read and write.

Key Rules and Purpose

- **Zero Compression:** Instead of writing out multiple continuous blocks of `0000`, you can replace them once with `::`.

- **Single Use Restriction:** The `::` symbol can only appear **once** in a single IPv6 address. Allowing it more than once would cause ambiguity when trying to expand the address back to its full 128-bit length (since you wouldn't know how many zeros belonged to each gap).

- **Example:**
    - **Uncompressed:** `2001:0db8:0000:0000:0000:0000:0000:0001`
    - **Compressed using `::`:** `2001:db8::1` (leading zeros are also dropped)
# What is IPv6 address compression?
**IPv6 address compression** is a set of notation rules used to shorten the written or typed representation of an **IPv6 address** without changing its actual 128-bit value.

Standard IPv6 addresses are 128 bits long, written as eight groups (called _hextets_) of four hexadecimal digits separated by colons (e.g., `2001:0db8:0000:0042:0000:8a2e:0370:7334`). Because these full strings are long and hard for humans to read, two primary rules are applied to compress them:

The Two Compression Rules

- **Omit Leading Zeros (Rule 1)**
    - You can drop leading (leftmost) zeros inside any 16-bit hextet.
    - _Example:_ `0042` becomes `42`, and `0370` becomes `370`. (Note: You cannot remove trailing zeros like `4200`).
    - _Example:_ `0000` inside a hextet can be shortened to a single `0`.

- **Replace Consecutive Zero Hextets with a Double Colon `::` (Rule 2)**
    - A single, contiguous sequence of one or more all-zero hextets can be replaced with a double colon (`::`).
    - _Important constraint:_ The `::` shortcut **can only be used once** in any single IPv6 address. Using it more than once creates ambiguity because a `::` does not specify how many zero hextets were removed. If there are multiple zero sequences of equal length, standard practice is to replace the longest one (or the leftmost one). 
Example
- **Full IPv6 Address:** `2001:0db8:0000:0000:0000:0000:1428:57ab`
- **After Compression:** `2001:db8::1428:57ab`

# What is the difference between IPv4 and IPv6 address length?
IPv4 uses a **32-bit** address length, while IPv6 uses a **128-bit** address length.

Key Length & Scale Comparison

- **IPv4 Address Length:** 32 bits (4 bytes), which creates roughly **4.3 billion** (2³²) unique addresses.

- **IPv6 Address Length:** 128 bits (16 bytes), which creates roughly **340 undecillion** (2¹²⁸ or 3.4 × 10³⁸) unique addresses.
# Explain the major limitations of IPv4 that led to the development of IPv6.
IPv4 uses a 32-bit address system that yields roughly 4.3 billion unique IP addresses. The explosive growth of personal computers, smartphones, and Internet of Things (IoT) devices caused this limited pool to run out.

Major Limitations of IPv4

- **Address Shortage:** A 32-bit architecture limits total addresses to about \(2^{32}\) (\(4.3\) billion), which cannot support modern global demand.

- **Reliance on NAT (Network Address Translation):** To delay address depletion, networks adopted NAT to let multiple private devices share a single public IP address. This workaround breaks true end-to-end connectivity and adds processing overhead to routers.

- **Complex Configuration:** IPv4 requires manual IP setup or dynamic host configuration through DHCP, which increases the risk of human or administrative errors.

- **Lack of Built-in Security:** IPv4 was designed without native security features; encryption and authentication (like IPsec) are optional add-ons rather than core protocol components.

- **Inefficient Routing and Large Tables:** IPv4 does not scale well for hierarchical addressing, causing core internet routing tables to grow massive and complex.

- **Poor Quality of Service (QoS) Support:** Traffic prioritization is weak in IPv4, making it harder to handle real-time data like live video and voice calls smoothly. 

- **Router-Based Fragmentation and Broadcasts:** IPv4 relies heavily on broadcast traffic (which increases unnecessary network load) and forces intermediate routers to handle packet fragmentation, reducing performance.

# List the major features of IPv6.
IPv6 (Internet Protocol version 6) features a 128-bit address space, a fixed 40-byte header, and native support for modern network requirements.

Major Features of IPv6

- **Expanded Address Space:** Uses 128-bit addresses (up from IPv4's 32 bits), generating roughly 3.4 × 10³⁸ unique addresses to eliminate exhaustion and remove the need for Network Address Translation (NAT).

- **Simplified Header Format:** Features a fixed 40-byte base header that drops or moves several IPv4 fields to optional extension headers, allowing faster packet forwarding and better routing efficiency.

- **Stateless Address Autoconfiguration (SLAAC):** Enables devices to self-configure and generate their own unique IP addresses on a network without relying on a DHCP server.

- **No Broadcast Support (Multicast & Anycast):** Replaces IPv4 broadcast communication with **multicast** (sending data to a subscribed group) and **anycast** (routing data to the nearest node in a group), significantly reducing network congestion.

- **Built-in / Extension IPsec:** Integrates IP Security (IPsec) for authentication and encryption via extension headers, improving end-to-end data security.

- **Quality of Service (QoS):** Uses a **Traffic Class** field and a **Flow Label** field in the header to identify and prioritize real-time traffic (such as audio and video streams).

- **Built-in Mobility Support:** Allows mobile devices to roam across different networks while keeping a consistent global IP address. 

- **Extension Headers:** Allows extra networking options to be chained after the base header without cluttering the main packet flow.

# Compare IPv4 and IPv6

| Feature                               | IPv4                                                                                                                | IPv6                                                                                                                                           |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Address Length**                    | 32-bit                                                                                                              | 128-bit                                                                                                                                        |
| **Total Addresses**                   | ~4.3 billion (nearly exhausted)                                                                                     | ~340 undecillion (virtually inexhaustible)                                                                                                     |
| **Notation Format**                   | Dotted-decimal (e.g., `192.168.0.1`)                                                                                | Hexadecimal colon-separated (e.g., `2001:db8::1`)                                                                                              |
| **Header Size**                       | flexible header size (20–60 bytes) with a checksum and options that increase router processing overhead             | streamlined, fixed **40-byte header** with no checksum, allowing routers to process packets faster.                                            |
| **Security (IPsec)**                  | lacks native security features; data encryption and authentication must be added via external protocols like IPsec. | built directly into the protocol architecture for native data authentication and encryption.                                                   |
| **Configuration**                     | Manual or built directly into the protocol architecture for native data authentication and encryption. DHCP         | SLAAC (Stateless Address Autoconfiguration) or DHCPv6. allowing devices to automatically generate their own network addresses upon connecting. |
| **Network Address Translation (NAT)** | Required to extend address space                                                                                    | Not required (uses direct end-to-end routing)                                                                                                  |
| **Communication Types**               | Unicast, Broadcast, Multicast                                                                                       | Unicast, Multicast, Anycast (no broadcast)                                                                                                     |
| **Fragmentation**                     | Handled by both senders and routers                                                                                 | Handled _only_ by the sending device                                                                                                           |
# Compress the following IPv6 address:
1. 
original= `2001:0DB8:0000:0000:0000:0000:0000:0001`
step 1: remove leading zeros inside each 16-bit block (hextet)
2001 => 2001
0DB8 => DB8
0000 => 0
0001 => 1
`2001:DB8:0:0:0:0:0:1`
step 2: Replace the longest sequence of consecutive all-zero blocks with a double colon `::`.
`0:0:0:0:0:0` => `::`

result: `2001:db8::1`

2. `FE80:0000:0000:0000:021C:7EFF:FE23:4567` => `fe80::21c:7eff:fe23:4567`
3. `2001:0DB8:0000:0001:0000:0000:0000:0010` => `2001:db8:0:1::10`

# Expand the following IPv6 address
1. `2001:DB8::1`

**Count visible groups**: There are 3 groups (`2001`, `DB8`, `1`).
**Find missing zeros**: An IPv6 address has 8 groups. The `::` replaces 5 missing groups of zeros (8 - 3 = 5).
**Restore hidden zeros**: Replace `::` with `0000:0000:0000:0000:0000`.
**Pad leading zeros**: Expand `DB8` to `0db8` and `1` to `0001` to make every group 4 digits long.

result: `2001:0db8:0000:0000:0000:0000:0000:0001`
2. `FE80::ABCD:1234` => `fe80:0000:0000:0000:0000:0000:abcd:1234`
