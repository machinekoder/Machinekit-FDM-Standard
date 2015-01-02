### Abbreviations
| Abbreviation      | Name    |
| :----: | :-----: |
| FDM | Fused Deposition Modeling |
| HBP | Heated Build Platform |
| HBC | Heated Build Chamber |
| En | Extruder n |
| Fn | Fan n |
| Ln | Light n |
| Sn | Servo n |
| Pn | Probe n |

### Analog Output
| #      | Name    |
| :----: | :-----: |
| 0 | HBP target temperature |
| 1 | HBC target temperature |
| 2 - 11 | E0-E9 target temperature |
| 12 - 21 | F0-F9 speed |
| 22 - 25 | S0-S3 pulse duration |
| 26 | L0 red value |
| 27 | L0 green value |
| 28 | L0 blue value |
| 29 | L0 white value |
| 30 - 37 | L1-L2 RGBW values |
| 38 | Probe selection (for homing) |
| 39 | Probe head X offset |
| 40 | Probe head Y offset |
| 41 | Probe head Z offset |
| 42 | P0 X position |
| 43 | P0 Y position |
| 44 - 49 | P1-P3 XY position |
| 50 | Buzzer frequency |
| 51 | Buzzer duration |

### Analog Input
| #      | Name    |
| :----: | :-----: |
| 0 | HBP measured temperature |
| 1 | HBC measured temperature |
| 2 - 11 | E0-E9 measured temperature |
| 12 - 21 | F0-F9 speed |
| 22 - 25 | S0-S3 pulse duration |
| 26 | L0 red value |
| 27 | L0 green value |
| 28 | L0 blue value |
| 29 | L0 white value |
| 30 - 37 | L1-L2 RGBW values |
| 38 | Probe count |
| 39 | Probe head X offset |
| 40 | Probe head Y offset |
| 41 | Probe head Z offset |
| 42 | P0 X position |
| 43 | P0 Y position |
| 44 - 49 | P1-P3 XY position |
| 50 | Buzzer frequency |
| 51 | Buzzer duration |

### Digital Output
| #      | Name    |
| :----: | :-----: |
| 0 | HBP target temperature trigger |
| 1 | HBC target temperature trigger |
| 2 - 11 | E0-E9 target temperature trigger |
| 12 - 21 | F0-F9 speed trigger |
| 22 - 25 | S0-S3 pulse duration trigger |
| 26 | L0 red value trigger |
| 27 | L0 green value trigger |
| 28 | L0 blue value trigger |
| 29 | L0 white value trigger |
| 30 - 37 | L1-L2 RGBW values trigger |
| 38 | Probe enable |
| 39 | Probe head X offset trigger |
| 40 | Probe head Y offset trigger |
| 41 | Probe head Z offset trigger |
| 42 | P0 X position trigger |
| 43 | P0 Y position trigger |
| 44 - 49 | P1-P3 XY position trigger |
| 50 | Buzzer frequency trigger |
| 51 | Buzzer duration trigger |

### Digital Input
| #      | Name    |
| :----: | :-----: |
| 0 | HBP temperature in range |
| 1 | HBC temperature in range |
| 2 - 11 | E0-E9 temperature in range |

## HAL Remote Components


### HBP, HBC and Extruders
Heated build platform, heated build chamber and extruders have the same interface. The name of the remote components are `fdm-hbp`, `fdm-hbc` and `fdm-e<n>`.

Example interface:

    newcomp fdm-hbp timer=100
    newpin fdm-hbp fdm-hbp.temp.meas float in
    newpin fdm-hbp fdm-hbp.temp.set  float io
    newpin fdm-hbp fdm-hbp.temp.max  float in
    newpin fdm-hbp fdm-hbp.temp.min  float in
    newpin fdm-hbp fdm-hbp.error     bit io
    ready fdm-hbp
    
### Fans
Fans and other PWM controlled devices have a very simple interface:

    newcomp fdm-f0 timer=100
    newpin fdm-f0 fdm-f0.pwm.set float io
    ready fdm-f0

### Lights

    newcomp fdm-l0 timer=100
    newpin fdm-l0 fdm-l0.color.r float io
    newpin fdm-l0 fdm-l0.color.g float io
    newpin fdm-l0 fdm-l0.color.b float io
    newpin fdm-l0 fdm-l0.color.w float io
    ready  fdm-l0