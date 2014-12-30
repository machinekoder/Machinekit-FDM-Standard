## Machinekit Flavor GCode

## GCodes

## MCodes
Machinekit supports a number of FDM specific MCodes inspired by the [RepRap MCodes](http://reprap.org/wiki/G-code). These codes are implemented using remapping. If you are interested in developing your own Machinekit based 3D printer take a look at the [remap file](remap.ini).

### [M104](./subroutines/m104.ngc): Set Extruder Temperature
Example: `M104 S190`

Set the temperature of the current extruder to 190oC and return control to the host immediately (i.e. before that temperature has been reached by the extruder). 

#### Multiple Exruders

M104 can be additionally used to handle all devices using a temperature sensor. It supports the additional P parameter, which is a zero-based index into the list of sensors in config.h. For devices without a temp sensor, see M106.

Example: `M104 P1 S100`

Set the temperature of the device attached to the second temperature sensor to 100 °C.
