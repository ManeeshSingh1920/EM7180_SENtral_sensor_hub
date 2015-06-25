EM7180_SENtral_sensor_hub
=========================

![](https://cloud.githubusercontent.com/assets/6698410/8147322/5626d762-1219-11e5-9cda-015815a06b23.jpg)

*EM7180 sensor hub with Invensense's MPU6500 gyro/accelerometer, Asahi Kasei's AK8963C magnetometer, and ST's M24512DFC I2C EEPROM on a board directly mountable onto the Teensy Cortex ARM M4 microcontroller.*

There are two kinds of files in this repository. 

The FirmwareUpload.ino file is a sketch that takes the firmware file xxx.fw (~22 kbyte) generated by the EM7180 [SENtral Tool Kit Configuration](http://www.emdeveloper.com/?page_id=105) tool and writes it to an ST Microelectronics M24512DFM/C EEPROM from an SD card. Both the SD card and the [SENtral breakout board](https://www.tindie.com/products/onehorse/em7180-sentral-sensor-hub-with-bmx055-motion-sensor/) need to be connected to a microcontroller; I use the Teensy 3.1. The SENtral breakout board is connected to the Teensy 3.1 I2C port on pins 16 and 17 and the SD card reader is connected to the SPI port on pins 10-13. Once the firmware is loaded onto the EEPROM it doesn't have to be done again unless the firmware changes or is updated; the SENtral reads the firmware upon power on and gets the information it needs about the particular sensors on the board.

The other files are sketches that further configure the SENtral for either normal mode, where it manages the BMX055 or LSM9DS0 or MPU6500+AK8963C sensors as slaves providing scaled sensor output and quaternions,or pass-through mode, where the Teensy microcontroller can directly communicate with the BMX055 or LSM9DS0 or MPU6500+AK8963C motion sensors and the MS5637/BMP280 pressure sensor.

These are the three major motion sensor inputs I am planning to implement in the short term. These will allow me to test the dependence of the quality of the motion sensor input data on the resulting sensor fusion solution using the same fusion algorithms and fusion engine.

The SENtral is configurable and the firmware, including the sensor fusion algorithms, can be programmed by the (sophisticated) user. It's just not easy.

Later, I will add altimetry to the sensor fusion algorithm as well as some other refinements. This is a great platform for testing sensor fusion algorithms and  new motion sensors.

This project is a work in progress...
