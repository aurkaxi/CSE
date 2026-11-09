inside refers to the addresses which must be translated. outside refers to the addresses which are not in control of an organization. these network addresses in which the translation of the addresses will be done.
![[nat inside outside diagram.png]]
1. inside local address: an ip address that is assigned to a host on the intside local network. the address is probably not an ip address assigned by the service provider i.e., these are private addresses. this is the inside host seen from the inside network
2. inside globaj address: ip address that represents one or more inside local ip address to the outside world. this is the inside host as seen from the outside network
3. outside local address: this is the actual ip address of the destination host in the local network after translation
4. outside global address: this is the outside host as seen from the outside network. it is the ip address of the outside destination host before translation
