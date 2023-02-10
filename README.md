# applied_collected_information
Mainly notes about 3D printing hardware

1. How use Orange Pi with Klipper and ADXL345

KLIPPER
- Install Armbian to Orange Pi
   - Add user (installation ask to do that)
   - Make updates (apt update, apt upgrade)
   
- Install KIAUH to Orange Pi
   - Install GIT
     - [sudo apt-get install git -y]
   - Copy KIAUH to user home (not at root)
     - [cd ~]
     - [git clone https://github.com/th33xitus/kiauh.git]
   - Start KIAUH
     - [./kiauh/kiauh.sh}
   - Use KIAUH to install Klipper, Moonraker (, FLUIDD and KlipperScreen)
   
- Configure Klipper to your printer.
   - Depens your printer, use Klipper documentation.

ADXL345
- You must get SPI to work
   - to /boot/armbianEnv.txt file
      Check if there is overlays line and it contains spi-spidev
      Check if there is param_spidev_spi_bus=1 line
   - Bus must be 1, if you use Orange Pi expansion pins. Pin number are same than raspberry pi 3 has, but RPi use SPI bus 0 there and OPi use bus 1.
   - Remeber boot OPi after changes.
   - Use Klipper documentation to add ADXL345 to Klipper.
   - Changes:
     - When install nympy, use command ~/klippy-env/bin/pip3 install -v numpy==1.18
     - Remeber add line spi_bus:spidev1.0 to printer.cfg file below to [adxl345].
     
 These works fine at Orange Pi Zero (Allwinner H2+ and 512mb)
 System load stays when print below 1 (usually something like 0.20) and before ADXL345 adding memory was 22% occupied, now it is 29% level.
 
 Input shaping works like it works, printing works like it works. Just same than RPi configurations.
 
