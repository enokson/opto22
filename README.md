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

### Tag Naming Conventions

groupName_ItemName_childGroupName_childItemName_etc

examples:
```txt
# 1 flow transmitter with 2 alarms and setpoints for those alarms
Tx_FT1_Value
Tx_FT1_Alarms_FL_SP
Tx_FT1_Alarms_FL_Active
Tx_FT1_Alarms_FH_SP
Tx_FT1_Aalrms_FH_Active

# 2 tranmitters (1xFlow, 1xPressure) with 2 alarms each
Tx_FT_Value
Tx_FT_Alarms_FL_SP
Tx_FT_Alarms_FL_Active
Tx_FT_Alarms_FH_SP
Tx_FT_Aalrms_FH_Active
Tx_PT_Value
Tx_PT_Alarms_FL_SP
Tx_PT_Alarms_FL_Active
Tx_PT_Alarms_FH_SP
Tx_PT_Aalrms_FH_Active

# 2 tranmitters (2xFlow) with 2 alarms each
Tx_FT1_Value
Tx_FT1_Alarms_FL_SP
Tx_FT1_Alarms_FL_Active
Tx_FT1_Alarms_FH_SP
Tx_FT1_Aalrms_FH_Active
Tx_FT2_Value
Tx_FT2_Alarms_FL_SP
Tx_FT2_Alarms_FL_Active
Tx_FT2_Alarms_FH_SP
Tx_FT2_Aalrms_FH_Active

# 1 flow transmitter with 2 alarms and (setpoints, downtimers) for those alarms
# 1 pump
# 2 solenoid valves
Tx_FT1_Value
Tx_FT1_Alarms_FL_Active
Tx_FT1_Alarms_FL_SP
Tx_FT1_Alarms_FL_DT_SP
Tx_FT1_Alarms_FL_DT_Delay
Tx_FT1_Alarms_FL_DT_Active
Tx_FT1_Value
Tx_FT1_Alarms_FH_Active
Tx_FT1_Alarms_FH_SP
Tx_FT1_Alarms_FH_DT_SP
Tx_FT1_Alarms_FH_DT_Delay
Tx_FT1_Alarms_FH_DT_Active
Pumps_P1_Run_Rx   # Run Status (Receiving)
Pumps_P1_Run_Tx   # Run Command (Transmitting, outputting to device)
Pumps_P1_Speed_Rx # Current Speed
Pumps_P1_Speed_Tx # Speed Command
Valves_SV1_Open_Rx
Valves_SV1_Open_Tx
Valves_SV1_Close_Rx
Valves_SV1_Close_Tx
Valves_SV1_Fault
Valves_SV1_Traveling
Valves_SV2_Open_Rx
Valves_SV2_Open_Tx
Valves_SV2_Close_Rx
Valves_SV2_Close_Tx
Valves_SV2_Fault
Valves_SV2_Traveling

# Using References to group alarms/interlocks under actuators
Pump_P1_Interlock_Tx_FT1_Value      # Float
Pump_P1_Interlock_Tx_FT1_FL_Active  # Int32
Pump_P1_Interlock_Tx_FT1_FH_Active
Pump_P1_Interlock_Valve_SV1_Open_Rx
Pump_P1_Interlock_Valve_SV2_Close_Rx

```

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
