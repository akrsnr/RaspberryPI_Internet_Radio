# Raspberry PI-based Internet Radio

It is my one of mandatory undergraduate projects in which radio stations being able to stream over IP/URL can be listened. Detailed explanation follows. (If the following photo doesn't appear, [click here](https://photos.app.goo.gl/QeWyVxJw9yiyN9DW6))

![enter image description here](https://lh3.googleusercontent.com/p1l_oPajLNE1K4OeajQv6zvVBBHi1jDBZA_FtwvAwANzyz_qBXgeE0DxUEh-bZ3kw-cPVsLrEs2Zk7Y4WkE8guMTD-rRQMSMYoCeFUacUPl4fCaGlns3Wi0nuV9szN1dS8k8y2EleMuik_vPtflsnh6yZTRa67lxVZexmZqhkiAWxKzHpnhKmIS4fHJ_6oYEzPmvI0bE3oUiLGTcJePJhAf04VISV26Aq7JHo7PHDFm6e6-A5FouPfljmIi8-dfNtYlhaX3041OZPdIaQuFjFrazxeQ7UNslXbcSPYamxR-Tl88R9yl82EyjyVIukDGbu-LlZQ82X1SoUzAJrPU7NDUnA05eZxUKGjovT8b7KTK71BqdO4_rOABQ_AYY1vfPjMUtI7_LbexDVT3jfdmpPd0p4zlQeNSTijP8dr7DZJiMpN_CvQYa3SwaQHpjAq7CP35blqmLtKAbVe9guo9qZU58CNbk_ix1Tsx5qe2plcOtdOg1KJRTSqyhqhU6uMVfs3oHLUphuZAJAKNE22TqpgrkegIuxtSY1uE-67lrjpymMWR8K_3Z619VaafwDJLrVMpHM0WElkiVQZcwxN2-js7t9nqqxGoikvLrW3AEKYnuinXUsZFpAiRmwtNfzwL13rpReNAeQPyB8TQcyFua828=w2744-h1502-no)

## Project's Language

Python


## Components

 - KY040 Rotary Encoder
 - 10K Potentiometer
 - Raspberry PI Zero W or any version of Raspberry no matter
 - 20 x 4 LCD Display
 - 12V Amplifier PAM 8610 Stereo
 - (8Ω / 10W) x 2 Speaker
 - ~240V or whatever in your country to 5V and 12V converter power suppliers (their quality is important since there is need to be regulated to prevent noise yet I use mobile phone 5V adapter to run my Raspberry PI Zero W)
 - MCP3008 analog to digital converter microchip

## Prerequisite softwares

 - amixer
 - mplayer

## Files

The following files involve required codes.

`lcd.py`   ⇒ LCD display

`soner.py` ⇒ KY040's codes with child process which is Mplayer

`volume.py` ⇒ Potentiometer

`radyoCs.py` ⇒ Read and reserve urls which are in urls.txt

`urls.txt` ⇒ Radio Station's IPs or URLs
<!---   `   -->

## How it works

Firstly, remember one of the rule of thumbs:
> **Don't reinvent the wheel**

The fact that there are applications of the components means we can use instructions existing already [KY040's module](https://github.com/martinohanlon/KY040) and [ how to connect it](http://codelectron.com/rotary-encoder-with-raspberry-pi/) --- [For 10K potentiometer(volume)](https://learn.adafruit.com/reading-a-analog-in-and-controlling-audio-volume-with-the-raspberry-pi/overview). Lastly, [20x4 LCD Display](https://www.raspberrypi-spy.co.uk/2012/08/20x4-lcd-module-control-using-python/)

We need to create a subprocess by `fork` and to communicate with the child running `mplayer` we need PIPE. What we need from `mplayer` is

 - Station Name
 - Track Artist
 - Track Name
 
 Then we parse and write the information FIFO created to communicate with LCD display. 

## Steps and Photos

You can glance at photos what I did overall on [its album](https://photos.app.goo.gl/JMBCkShdmKQEzthB7).

## Self-criticism

I **very too much** like and interested in Object-Oriented Programming Concept and Design Patterns, nonetheless, I (couldn't)didn't follow my intention. I still feel bad for the case :/
