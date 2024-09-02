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
