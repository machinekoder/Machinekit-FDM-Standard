# FDM Specific INI parameters
There are few sections in the INI file specific for 3D printing.

## Heaters

Machinekit has section for each heating element. These are named `EXTRUDER_n` for the extruders (n is the number of the extruder), `HBP` for the heated build platform and `HBC` for the heated build chamber. It supports the following parameters:


**PID_PGAIN** P gain value of the PID component

**PID_IGAIN** I gain value of the PID component

**PID_DGAIN** D gain value of the PID component

**PID_MAXERRORI** Maximum I error values of PID component

**PID_BIAS** Bias value of the PID component

**PWM_MAX** PWM value limitation (0-1)

**TEMP_RANGE_POS_ERROR** Positive temperature error range value. The temperature range specifies how much temperature tolerance should be accepted for the temperature to be in range.

**TEMP_RANGE_NEG_ERROR** Negative temperature error range value

**TEMP_LIMIT_MIN** The minimum temperature limit for this heater. Temperatures outside the limit lead to triggering a error.

**TEMP_LIMIT_MAX** The maximum temperature limit for this heater.

**TEMP_STANDBY** The standby temperature for this heater.

**THERMISTOR** Thermistor table to use for this heater.

## Probing