# White Noise

[White Noise](fb.com/WhiteNoiseGRE) is a space-engineering team from the National Technical University of Athens and currently consists of 6 members ( in alphabetical order ) :

* Dimitris Bralios 
* Chariton Charitonidis
* Iasonas Nikolaou
* Spyros Pavlatos
* George Rapakoulias
* Miltiadis Stouras

Our team won 1st prize in the [CanSat in Greece 2018](cansat.gr) competition.

# DrillSat

![DrillSat](DrillSat.jpg?raw=true "DrillSat")

Our goal was to develop a CanSat that can help in exploring new planets, as a part of our idea to use CubeSats in space exploration. Specifically, our CanSat, after a successful landing with the parachute, is able to use its [leg mechanism](https://www.youtube.com/watch?v=kTSUgSXn8OM) and rise into a position from which it can dig its drills to the ground and measure the soil's moisture with a sensor we developed.

# Electronics System 

The circuit consists of three boards. PCB1 connects an Arduino Pro Mini, an SD socket and a UV sensor (ML8511). PCB2 connects an XBee, the Solar Charger and a BMP sensor. The Solar Charger is a modified and shrunk version of the Adafruit board. 

PCB1 and PCB2 were designed on fritzing while the solar charger was designed on EAGLE.

## Sensor Subsystem

### Ultra Violet
The UV light sensor used is ML8511 mounted on a board. Equipped with an internal amplifier it converts the photo-diode current to voltage, outputing voltage linearly related to the UV light intensity measured in mW/cm2. The sensor output is stable across the operating temperature range, from -25C up to 75C, altough silght error is introduced away from the configuration temperature. Slight error is introduced by the temperature, although the operational temperature range is from -25C up to 75C. The spectral response is highest in the range 280 - 390nm which covers the UV-B spectrum and significant percentage of the UV-A spectrum. The typical supply current is around 300uA at the operational voltage of 3V.

### Pressure & Temperature
The sensor used to mesure temperature and barometric pressure is BMP280. The interface used to communicate with the microctroller is I2C. The pressure and temperature data, using the barometric formula, can give the current height with an accuracy of 1m. The operating pressure range is up to 9000m above sea level and from -40C to 85C regarding the temperature range, while the typical current draw is 2.7uA. 
