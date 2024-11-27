# Installation

In slm.toml add:
```
diodes = { git = "JITx-Inc/diodes", version = "0.2.0" }
```

# ESD224DQAR ESD diode
## create-esd-pool
Create a Circuit Pool of [ESD224](https://www.ti.com/lit/ds/symlink/esd224.pdf?ts=1732603822506) ESD protection diode arrays.

This function is a generator and expects to be called from a
`pcb-module` context.
```
val esd = diodes/ESD224DQAR/create-esd-pool(2, GND)
require protected-pairs:dual-pair[4] from esd
topo-pair(src => protected-pairs[1].A => protected-pairs[1].B => dst)
```
### ports
Each array supports:
- Two `dual-pair` bundles
- Four `pass-through` bundles

### Parameters
- num-ICs:Int Total number of ICs to instantiate in the pool
- GND:JITXObject Net for the ground that the ICs will terminate to.
