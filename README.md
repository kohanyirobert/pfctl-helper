# pfctl-helper

`pf`, `pfctl` helper scripts to help blocking/allowing certain hosts during
development.

Learn more about `pf` and `pfctl` [here](http://www.nomoa.com/bsd/gateway/pf/valid/pfctl.html).

## Usage

Clone the repo and put the directory into your `PATH` then configure `.conf`
files under `block/` based on `block/sample.conf`.

* **pfe** Enables `pf`.
* **pfd** Disables `pf`.
* **pfc** Clears the current ruleset and reloads the default `/etc/pf.conf`.
* **pfr** Reads and prints the current ruleset.
* **pfb** Blocks addresses configured in a `block/*.conf` file. 

`pfb example` will concat `/etc/pf.conf` and `block/example.conf` and load that
as the new ruleset.

`block/example.conf` can contain multiple block specifications if needed.

```
block return from any to example.com
block return from any to my-host.com
block return from any to ...
```

### Example

```
pfe         # enable pf
pfb example # block whatever defined in block/example.conf
pfc         # reload the default config
pfd         # disable pf
```
