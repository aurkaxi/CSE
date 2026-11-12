In a pilot deployment, one registry is used to keep a governance view of the service metadata, and a separate registry holds the metadata used by the runtime services in production. This means that you do not change runtime service metadata during the service development lifecycle, and changes to development service metadata do not impact runtime operation; at an appropriate point in the development lifecycle, when you are sure that a service is ready for production use, the service metadata is moved from the governance registry to the runtime registry, and the runtime systems adopt it.
Although not intended, primarily, for production use, this topology might be used in production for a small scale SOA environment.

governance
Development teams share access to the content in this registry, typically segregated according to department. All discovery, development, and governance operations are performed here. 

runtime (production)
A limited set of content from the governance registry is promoted to this registry as and when services are ready to go into production, using the WSRR promotion feature. Typically, users do not work directly with this registry, and content is mostly read-only, although additional metadata might be added to registry content, to support ITCAM for SOA for example. Instead, users work in the governance registry, and content is promoted automatically to the runtime registry at the appropriate point in the governance lifecycle. This registry is used for business runtime access.

![[Pasted image 20261112090949.png]]