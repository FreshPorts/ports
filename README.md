Typically, this repo is checked out to the top level directory of your ports tree.

As of 2025-01-02, all FreshPorts nodes are using the ports created from this repo.

In this case, it's a poudriere instance:

```
[23:14 pkg01 dvl /usr/local/poudriere/ports/default] % sudo mkdir freshports
[23:14 pkg01 dvl /usr/local/poudriere/ports/default] % sudo chown dvl:dvl freshports
[23:14 pkg01 dvl /usr/local/poudriere/ports/default] % git clone git@github.com:FreshPorts/ports.git freshports
```
In `/usr/local/etc/poudriere.d/default-make.conf`, these entries were added:

```
VALID_CATEGORIES+=freshports
UID_FILES+=${PORTSDIR}/UIDs ${PORTSDIR}/freshports/UIDs
GID_FILES+=${PORTSDIR}/GIDs ${PORTSDIR}/freshports/GIDs
```

You may have to change `default-make.conf` to reflect your poudriere ports tree name.

```
[23:21 pkg01 dvl /usr/local/poudriere/ports/default/freshports] % sudo poudriere ports -l | grep default
default     git       2024-12-31 04:18:08 /usr/local/poudriere/ports/default
```
