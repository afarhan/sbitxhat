# sbitxhat
Raspberry Pi HAT for SDR experimenters

Get the latest on the sBitx hat from https://github.com/afarhan/sbitxhat

In FDIM Conference of 2024, HF Signals gifted sBitx Hat PCBs to promote experimentation with SDRs. 
This is a repository for the circuit diagram and future software drivers.

The HAT has three subsystems:
1. Si5351 clock generator. This can generate upto three clocks from 10 KHz to around 200 MHz.
2. WM8731, this is a low noise dual channel (stereo) audio codec that samples at 96 ksps.
3. All other GPIO pins are brought out on the side of the Raspberry Pi connector.


Using the Hat:
1. The sbitxhat has been tested to work well on Raspberry Pi Zero 2 W and Raspberry Pi 4B. It is assumed that it will also work well with other models of Raspberry Pi.
2. The WM8731 gets confused with any other device is added to the same I2C bus, hence the Si5351 uses I2C protocol over two GPIO lines by through library that toggles the bits to get it done (bit banging).
2. To enable the audio codec, add the following line to the /boot/config.txt of the Raspberry Pi:
  dtoverlay=audioinjector-wm8731-audio
3. To use the Si5351, add the following files to your project from https://github.com/sbitx :
   i2cbb.c, i2cbb.h, si5351v2.c, si5351.h
4. To compile the Si5351 code, you will also need WiringPi library.


Things to do:
1. Move the Si5351 to kernel I2C on the lines used by the sBitx Hat.
2. Create a library with simple APIs to manage the audio and the clocks
       
