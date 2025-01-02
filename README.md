Typically, this repo is checked out to the top level directory of your ports tree.

As of 2025-01-02, all FreshPorts nodes are using the ports created from this repo.

In this case, it's a poudriere instance:

```
[23:14 pkg01 dvl /usr/local/poudriere/ports/default] % sudo mkdir freshports
[23:14 pkg01 dvl /usr/local/poudriere/ports/default] % sudo chown dvl:dvl freshports
[23:14 pkg01 dvl /usr/local/poudriere/ports/default] % git clone git@github.com:FreshPorts/ports.git freshports
```
