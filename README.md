# opto22

## Shell

```
export TERM=st-256color
```

## PAC Control

### git

.gitignore example

```txt
# ignore compiled bits of the program
*.crn
*.crn1
*.crn2
*.crn3
*.ccd
*.con
*.isc

# ignore lock files
*.lisb
*.lidb

# ignore temp files
*.\$idb

# ignore archives
# path/to/archives/
```

### Subroutines

There are developement issues related to subroutines. They cannot be reproduced, but they DO NOT affect code running in production.
To avoid the issue, refrain from stepping into a block just before a subroutine or from setting a breakpoint in a subroutine
while in debug mode.

### Running PAC Control on Linux

My setup:

* The default wine architecture: WINEARCH=win32
* The default wine prefixe: ~/.wine
* Used winetricks for:
  * adding dll comctl32
  * adding dll dxvk
  * There may be some other dlls required
* Used winecfg to change the path of Z:\ from "/" to "/home/\<USER\>/"

I had an issue where the toolbar would not display correctly and in the logs
the errors were prefixed with "fixme". I found a dll called "fixme." I installed it, winetricks installed
the required dlls and it ceased being an issue.

## Misc
### Epic

* Architure: armv7l
* target triplet: arm-poky-linux-gnueabi

```sh
# Get architure
uname -a

# get target triplet
gcc -dumpmachine
```
