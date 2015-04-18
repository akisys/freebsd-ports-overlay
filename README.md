# freebsd-ports
FreeBSD Ports Overlay

## Integration requirements

Package: portshaker

Configuration example: /usr/local/etc/portshaker.conf

```sh
# vim:set syntax=sh:
# $Id$

#---[ Base directory for mirrored Ports Trees ]---
mirror_base_dir="/build/cache/portshaker"

#---[ Directories where to merge ports ]---
ports_trees="poudriere"

poudriere_ports_tree="/build/ports/default"
poudriere_merge_from="freebsd akisys"
```

Configuration example: /usr/local/etc/portshaker.d/freebsd

```sh
#!/bin/sh
. /usr/local/share/portshaker/portshaker.subr

method="git"
git_clone_uri="https://github.com/freebsd/freebsd-ports.git"
git_branch="master"
run_portshaker_command $*
```

Configuration example: /usr/local/etc/portshaker.d/akisys

```sh
#!/bin/sh
. /usr/local/share/portshaker/portshaker.subr

method="git"
git_clone_uri="https://github.com/akisys/freebsd-ports.git"
git_branch="master"
run_portshaker_command $*
```

## Furthermore

Change the paths according to your filesystem layout.

