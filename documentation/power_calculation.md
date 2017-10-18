Metrics
-dac normal mode operation sinks 1.4mA
-current regulators sink 0.2mA on analogue dim input signal
-dac outputs can source up to 25mA per channel
-i2c comm current sink is nedlidgible (uA)
-isolator side 2 sinks up to 3.1 mA
-psoc normal mode operation sinks 4.5mA
-photon normal mode operation sinks up to 100mA average, 430mA peak

Analysis
- mcus will supply 6 analogue dim signals
- dacs will have no problem supplying 0.2mA per analogue dim signal
- dacs will have no problem supplying 0.2mA * 6 = 1.2mA collectively
- max mcu normal mode operation sinks 100mA

Calculation
- dac normal operation sink + x6 current regulator analogue dim signal sink + isolator side 2 sink + max mcu normal mode operation sink = 1.4mA + 1.2mA + 3.1mA + max(4.5mA, 100mA)

Result
- if using psoc, 3v3 current draw = 10.2mA
- if using photon, 3v3 current draw = 105.7mA

Implications
- using a linear regulator to drop from 24V to 3.3V @ 10.2mA current draw (psoc) will dissipate ~210mW and @ 105.7mA current draw (photon) will dissipate ~2.2W
- the linear regulator can only dissipate up to 370mW so need to use a switching regulator due to photon mcu option