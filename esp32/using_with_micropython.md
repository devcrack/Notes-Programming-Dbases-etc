1. install esptool. Is preferable do this in a virtualenvironment. 
```pip install esptool```
2. Add your user to dialout group:
   ```sudo adduser $your_user dialout```
   
   Be secure to logout after of do this.
3. Download the firmware required for the board from here: https://micropython.org/download/esp32/

4. Erase your esp32 board: ```esptool.py --port /dev/ttyUSB0 erase_flash```

5. Install the downloaded firmware: ```esptool.py --chip esp32 --port /dev/ttyUSB0 write_flash -z 0x1000 esp32-20220618-v1.19.1.bin```


### Install picocom for comunicate with the board

1. Install it using the command: ```sudo apt install picocom``

2. Using for comunicate with the board: ```picocom -b 115200 /dev/ttyUSB0```
Once you connect to the board you will see a python terminar as always. 
You can type programs in the python shell . That shell is running in ESP32

You can make a test blinking the integrated led to the board using the library machine: ```from machine import Pin```. 
Then we can write the following program 

```python
from machine import Pin
from time import sleep

p = Pin(2, Pin.OUT)

while True:
   p.value(1)
   sleep(0.5) # half of a second
   p.value(0)
   sleep(0.5)

```
And in that way we can start to play with our ESP32 board :blush:

For exit from picocom use Ctrl + A, Ctrl + X

### Example tiny dummy program
```python
import time 
from machine import Pin

led1 = Pin(13, Pin.OUT)
led2 = Pin(12, Pin.OUT)
led3 = Pin(27, Pin.OUT)

while True:
   led1.value(1)
   led2.value(0)
   led3.value(0)
   time.sleep(0.2)
   led1.value(0)
   led2.value(1)
   time.sleep(0.2)
   led2.value(0)
   led3.value(1)
   time.sleep(0.2)
```   


# Notes
In our board the pin attached to integrated led board is the Number 2.
