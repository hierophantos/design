## Primea Hypervisor

### Brief Overview

Primea Hypervisor is a [exoKernel](https://en.wikipedia.org/wiki/Exokernel) or microkernel like system. The Hypervisor doesn't assume any hardware model. It does assume that there is some communication medium that hardware has access to. The hypervisor also partially orders messages within the system so that the message order of all the container is deterministic. 

## Containers
Containers are an abstract for a computational unit. This could be in the form of a VM such as an Javascript VM, a wasm JIT or in the form of actual hardware. The containers create a uniform wrap around the computational unit so that the Hypervisor can interact with them in a uniform way. Each container can be considered an [actor](https://en.wikipedia.org/wiki/Actor_model). 

## Communication
The hypervisor has a simple communication model that is inspired from capabilities based OS.
**Channels** connect containers and allows them to perform bi-directional communication. Each container that is connected to a channel see a **port** which is internal labeled. Ports are accessed by the container vai references to them. Furthermore ports can thought of as a capability to send and receive message from the connecting container. 

## Messages
Messages can container Port references and Data. When references to ports are sent in a message the sender loses access to the port and the receiving container gains access to the port.

## State
Each container is has a state associated with it. The state contains the container's nonce (which is incremented each time the container creates a new port), its ports (if any) and any other arbitrary data. Individual containers can specify there state. Thier state is mutable if desired.

## IDs
Each container instance has a unique ID. The ID is defined by a tuple containing the parents ID and the nonce.

