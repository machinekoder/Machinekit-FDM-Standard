## Machinekit Flavor GCode

## GCodes

## MCodes
Machinekit supports a number of FDM specific MCodes inspired by the [RepRap MCodes](http://reprap.org/wiki/G-code). These codes are implemented using remapping. If you are interested in developing your own Machinekit based 3D printer take a look at the [remap file](remap.ini).

### [M104](./subroutines/m104.ngc): Set Extruder Temperature
Example: `M104 S190`

Set the temperature of the current extruder to 190oC and return control to the host immediately (i.e. before that temperature has been reached by the extruder). 

#### Multiple Exruders
M104 can be additionally used to handle all devices using a temperature sensor. It supports the additional P parameter, which is a zero-based index into the list of sensors. For devices without a temp sensor, see M106.

Example: `M104 P1 S100`

Set the temperature of the device attached to the second temperature sensor to 100 °C.

### [M106](./subroutines/m106.ngc): Fan On
Example: `M106 S127`

Turn on the cooling fan at half speed.
Mandatory parameter 'S' declares the PWM value (0-255). M106 S0 turns the fan off.

#### Additional Fans/Devices
Additionally to the above, Machinekit uses M106 to control general devices. It supports the additional P parameter, which is an zero-based index into the list of fans/devices.

Example: `M106 P2 S255`

Turn on device #3 at full speed/wattage.

#### Sync with Motion
By default the M106 command will be executed with the next movement. This default behavior is used since the fan speed is constantly switched during execution and an unsynchronized movement would break look-ahead and path blending. For the purpose of executing a command immediately the M106 supports the additional I parameter.

Example: `M106 I1 S127`

Turn on the cooling fan at half speed immediately. The value of the I parameter is indifferent.

### [M109](./subroutines/m109.ngc): Set Extruder Temperature and Wait
Example: `M109 S185`

Set extruder heater temperature in degrees celsius and wait for this temperature to be achieved.

#### Multiple Exruders
Similar to M104 this command supports the additional P parameter for specifying the extruder.

Example: `M109 P1 S100`

Set the temperature of the device attached to the second temperature sensor to 100 °C and wait for the temperature to be reached.