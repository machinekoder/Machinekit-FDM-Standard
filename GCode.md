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

Turn on the cooling fan at half speed immediately. `I0` equals to not immediate, all other values evaluate to immediate if I is specified.

### [M109](./subroutines/m109.ngc): Set Extruder Temperature and Wait
Example: `M109 S185`

Set extruder heater temperature in degrees celsius and wait for this temperature to be achieved.

#### Multiple Exruders
Similar to M104 this command supports the additional P parameter for specifying the extruder.

Example: `M109 P1 S100`

Set the temperature of the device attached to the second temperature sensor to 100 °C and wait for the temperature to be reached.

### [M140](./subroutines/m140.ngc): Bed Temperature (Fast)
Example: `M140 S55`

Set the temperature of the build bed to 55 °C and return control to the host immediately (i.e. before that temperature has been reached by the bed).

### [M141](./subroutines/m141.ngc): Chamber Temperature (Fast)
Example: `M141 S30`

Set the temperature of the chamber to 30 °C and return control to the host immediately (i.e. before that temperature has been reached by the chamber).

### [M190](./subroutines/m190.ngc): Wait for bed temperature to reach target temp
Example: `M190 S60`

Set the temperature of the build bed to 60 °C and wait for the temperature to be reached.

### [M191](./subroutines/m191.ngc): Wait for chamber temperature to reach target temp
Example: `M191 S60`

Set the temperature of the build chamber to 60 °C and wait for the temperature to be reached.

### [M226](./subroutines/m226.ngc): Gcode Initiated Pause
Example: `M226`

Initiates a pause in the same way as if the pause button is pressed. That is, program execution is stopped and the printer waits for user interaction. This matches the behaviour of M1 in the [NIST RS274NGC G-code standard](http://www.nist.gov/manuscript-publication-search.cfm?pub_id=823374).

### [M306](./subroutines/m306.ngc): Set home offset calculated from toolhead position
Example: `M306 Z0`

The values specified are added to the calculated end stop position when the axes are referenced. The calculated value is derived from the distance of the toolhead from the current axis zero point.

The user would typically place the toolhead at the zero point of the axis and issue the M306 command.

### [M400](./subroutines/m400.ngc): Wait for current moves to finish
Example: `M400`

Finishes all current moves and and thus clears the buffer. That's identical to `G4 P0`.

### [M420](./subroutines/m420.ngc): Set RGBW Colors as PWM
Usage: `M420 R<Red PWM (0-255)> E<Green PWM (0-255)> B<Blue PWM (0-255)> W<White PWM (0-255)>`

Example: `M420 R255 E255 B255 W255`

Set the color of your RGBW LEDs that are connected to PWM-enabled pins. Note, the Green color is controlled by the E value instead of the G value due to the G code being a primary code that cannot be overridden.

### [M600](./subroutines/m600.ngc): Calibrate Z axis
Example: `M600`

Calibrates the Z axis by probing the distance to the build bed.

### [M601](./subroutines/m600.ngc): Probe Z axis
Example: `M600`

Probes the Z axis at the current position.