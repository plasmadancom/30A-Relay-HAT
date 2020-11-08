# Updating the 30A Relay HAT EEPROM

Check the EEPROM is reachable.

```
i2cdetect -y 0
```

You should see a grid showing 0x50 like below.

<p align="center">
    <img alt="i2cdetect -y 0 output" src="https://github.com/plasmadancom/CTRL-HAT/raw/master/img/i2cdetect_eeprom.gif">
</p>

If you get an error, make sure I2C bus 0 is enabled in `/boot/config.txt`.

```
sudo sh -c "echo 'dtparam=i2c_vc=on' >> /boot/config.txt"
sudo reboot
```

Install EEPROM utilities.

```
sudo svn checkout https://github.com/raspberrypi/hats/trunk/eepromutils
cd eepromutils
sudo make
```

## Write the Complied Configuration File

```
sudo wget https://github.com/plasmadancom/30A-Relay-HAT/raw/master/eeprom/30a-relay-hat.eep
```

Short the CFG pin to ground on your 30A Relay HAT to disable write protection, then write to EEPROM.

```
sudo ./eepflash.sh -w -t=24c32 -f=30a-relay-hat.eep
```

## Compile the Configuration File Yourself

```
sudo wget https://github.com/plasmadancom/30A-Relay-HAT/raw/master/eeprom/30a-relay-hat.txt
```

Make your desired changes to 30a-relay-hat.txt and compile.

```
sudo ./eepmake 30a-relay-hat.txt 30a-relay-hat.eep
```

Write to EEPROM.

```
sudo ./eepflash.sh -w -t=24c32 -f=30a-relay-hat.eep
```

## Testing

Reboot to load the device-tree from the EEPROM.

```
sudo reboot
```

Read product name from the EEPROM.

```
cd /proc/device-tree/hat/
more product
```

You should see the product name: 30A Relay HAT.

## Reference

[HOWTO: Raspi HAT EEPROM and device-tree](https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=108134)