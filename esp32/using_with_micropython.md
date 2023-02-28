1. install esptool. Is preferable do this in a virtualenvironment. 
```pip install esptool```
2. Add your user to dialout group:
   ```sudo adduser $your_user dialout```
   
   Be secure to logout after of do this.
3. Download the firmware required for the board from here: https://micropython.org/download/esp32/

4. Erase your esp32 board: ```esptool.py --port /dev/ttyUSB0 erase_flash```

5. Install the downloaded firmware: ```esptool.py --chip esp32 --port /dev/ttyUSB0 write_flash -z 0x1000 esp32-20220618-v1.19.1.bin```


