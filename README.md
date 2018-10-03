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

The electronics system of the CanSat is comprised of an Arduino microcontroller, a UV sensor, a pressure and temperature sensor, a GPS, an XBee RF module, a conductivity sensor  and powered by a LiPo battery and four solar panels. The system apart from the battery the solar panels and the GPS, has to fit on top of two legs of the CanSat inside a space of 7x35x71mm. Due to that two PCBs were designed so the electronics can be mounted onto them. Also the structure has to be robust and survive any stresses, as well as operate continuously for 4 hours, constricting the power budget.

We have three boards on this repo. PCB1 connects an Arduino Pro Mini, an SD socket and a UV sensor (ML8511). PCB2 connects an XBee, the Solar Charger and a BMP sensor. The Solar Charger is a modified and shrunk version of the Adafruit board. 

PCB1 and PCB2 were designed on fritzing while the solar charger was designed on EAGLE.

## Sensor Subsystem

### Ultra Violet
The UV light sensor used is ML8511 mounted on a board. Equipped with an internal amplifier it converts the photo-diode current to voltage, outputing voltage linearly related to the UV light intensity measured in mW/cm2. The sensor output is stable across the operating temperature range, from -25C up to 75C, altough silght error is introduced away from the configuration temperature. Slight error is introduced by the temperature, although the operational temperature range is from -25C up to 75C. The spectral response is highest in the range 280 - 390nm which covers the UV-B spectrum and significant percentage of the UV-A spectrum. The typical supply current is around 300uA at the operational voltage of 3V.

### Pressure & Temperature
The sensor used to mesure temperature and barometric pressure is BMP280. The interface used to communicate with the microctroller is I2C. The pressure and temperature data, using the barometric formula, can give the current height with an accuracy of 1m. The operating pressure range is up to 9000m above sea level and from -40C to 85C regarding the temperature range, while the typical current draw is 2.7uA. 

### Conductivity Sensor

The conductivity sensor of the ground is implemented as a voltage divider. Two high speed steel drills are used space 18.2mm apart that penetrate 20mm in depth. One drill is connected to the ground voltage level while the other to +3.3V level through a 10KOhm resistor. Then the second drill is connected to an analogue pin of the microcontroller, as a result given the voltage at that pin and the resistance of the drills, we can specify the resistance between them.

### GPS

The GPS module used is the LEA-6H, which is mounted on the top of the CanSat. Typical supply current is 41mA and 47mA during the acquisition phase and the horizontal accuracy is 2.5m.

## Communication & Data Handling

### Microcontroller

The selected microcontroller board is the Arduino Pro Mini, using the ATmega328P, an 8-bit AVR microprocessor. It runs at 3.3V and 8MHz and has 14 input/output pins, 6 of them analog. The available program memory size is 32KByte, as well as 1024 Bytes of non volatile EEPROM memory, used to make the CanSat state-aware after possible power offs.

### RF Module

The RF module used for communication with the ground station is the XBee Pro S5 operating at 868MHz. It runs on 3.3 V consuming 60 mA at stand-by mode and 200 mA on packet emission and has a sensitivity of -112 dBm. It is used with an external antenna with 3 dBi gain. The same XBee module is also used on the ground station. The two modules are programmed to operate on AT Mode with ground station’s XBee being the coordinator and cansat’s XBee a router. Both modules transmit at a power of 25mW which is the legal local limit at 868MHz.

## Power Subsystem

A Polymer Lithium Ion battery, charged by four solar panels, is powering the CanSat. The battery has a voltage output of 3.7V and a capacity of 980mAh. Four 30.5mm by 58.5mm solar panels connected in serially, are used to charge the battery through the MCP73871. Then a low-dropout regulator drops the voltage down to 3.3V powering every piece of electronics, except for the GPS which has an onboard regulator and the the three motors.
