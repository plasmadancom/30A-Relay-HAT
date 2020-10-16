# 30A Relay HAT

* [Web GUI Live Demo](https://io.plasmadan.com/30arelayhat)
* [Easy Installer](#easy-installer)
* [Arduino Wiring](#arduino-wiring)
* [Setup Guide](https://github.com/plasmadancom/HAT-GUI/#setup-guide)

A Raspberry Pi HAT I/O board which offers an impressive 30A switching capability. Ideally suited to automation or industrial control, switching of household appliances, industrial machinery or automotive applications.

## Features

* 2 opto-isolated SPDT power relays
* 30A / 15A @ 250V AC (NO / NC) [*](#maximum-ratings)
* 2oz copper PCB ensures maximum current flow
* Easy to use [interactive web GUI](#interactive-web-gui)
* Based on the MCP23008 8-port [GPIO expander](#built-in-gpio-expander)
* Jumper selectable [I2C address](#i2c-addressing) & [GPIO voltage](#device-compatibility) (3.3V / 5V)
* Can be used with 3.3V or 5V I2C host devices (eg, [Arduino](#arduino-wiring))
* Built-in user programmable ID EEPROM
* Conforms to Raspberry Pi [HAT Specifications](https://github.com/raspberrypi/hats)

## Interactive Web GUI
<p align="center">
    <a href="https://io.plasmadan.com/30arelayhat" target="_blank" rel="nofollow">
        <img alt="30A Relay HAT Web GUI" src="https://github.com/plasmadancom/HAT-GUI/raw/master/img/hat-gui.gif">
    </a>
</p>

Once installed on your Raspberry Pi, this interactive GUI allows quick &amp; easy control of your 30A Relay HAT without the need for any coding. It is designed to be both a user guide &amp; quick reference to the 30A Relay HAT pinout. The GUI is fully responsive and adapts to any screen size.

Check-out the [Live Demo.](https://io.plasmadan.com/30arelayhat)

## Easy Installer

Our easy installer takes care of the setup process automatically.

```
sudo wget https://git.plasmadan.com/install.sh
sudo sh install.sh
```

This script will automatically enable I2C, install the required packages and setup the Web GUI.

Alternatively, you can install manually. See our [setup guide](https://github.com/plasmadancom/HAT-GUI/#setup-guide).

## Built-in GPIO Expander

Featuring the well-documented MCP23008 8 channel GPIO expander, 30A Relay HAT is easy to setup and control via I2C. Channels 0-1 are utilised for the relays, giving you an extra 6 GPIOs for use with your project.

## Arduino Wiring

We built 30A Relay HAT to work with any device featuring an I2C bus. It can be used with either 3.3V devices (eg, Raspberry Pi) or 5V devices (eg, Arduino); by selecting the appropriate jumper (see [device compatibility](#device-compatibility)).

## Maximum Ratings

* 30A / 15A @ 250V AC (NO / NC) *

Exceeding these limits may overload the PCB.

__* 30A is no small fry! You must take into account the type of load you're switching. Study the [relay datasheet](https://github.com/plasmadancom/30A-Relay-HAT/docs/HF165FD-datasheet.pdf)! In open air 30A Relay HAT can safely handle 30A (resistive load) but beware of heat build-up with prolonged use.__

## DC Switching

DC is much more difficult to switch compared to AC. 30A Relay HAT is not rated to switch DC since it uses AC relays, however provided you stick to **low** voltages and keep the current reasonable, you should be fine. However this is entirely at your own risk and will likely reduce the operational life of the relays. Automotive applications at 12V DC should be fine also. We recommend a **maximum** 20A / 10A @ 30V DC (NO / NC).

Alternatively try our [CTRL HAT](https://github.com/plasmadancom/CTRL-HAT) boards which work with DC power-MOSFETs.

## Electrical Safety

Mains voltage electricity is extremely dangerous. There is significant risk of death through electrocution, fire or explosion if not wired and fused correctly.

If using with mains voltages Appliance HAT must be installed in an electrically insulated enclosure by a qualified electrician and maintain at-least a 2mm air gap between all conductive parts of the Raspberry Pi ([source](http://www.creepage.com)).

## Isolating the Relays

Removing the LINK jumper from 30A Relay HAT will disconnect 5V power to the relays. This allows you to power the relays from a dedicated supply if required.

## Back-Powering

Using a decent power supply, such as the official Raspberry Pi adaptor, you can expect to pull around 1.5A from the 5V pins on a Raspberry Pi. You can use up to 8 30A Relay HATs with a single Raspberry Pi. That's up to 16 1W relays, 16 LEDs and 8 GPIO expanders which all need power. It's easy to see how quickly we can go over the limit, especially if the GPIO expanders are used to drive other devices. Back-powering can solve this.

The easiest way to back-power 30A Relay HAT is using the 5V power pins. Alternatively, solder directly to the supplementary power-in pads.

__* Note: Back-powering is for 30A Relay HAT, not for Raspberry Pi. Remove the LINK jumper when back-powering to avoid damaging your Pi.__

## I2C Addressing

| Address | A2 | A1 | A0 |
| :---: | :---: | :---: | :---: |
| 0x20 | | | |
| 0x21 | | | &#x2B1B; |
| 0x22 | | &#x2B1B; | |
| 0x23 | | &#x2B1B; | &#x2B1B; |
| 0x24 | &#x2B1B; | | |
| 0x25 | &#x2B1B; | | &#x2B1B; |
| 0x26 | &#x2B1B; | &#x2B1B; | |
| 0x27 | &#x2B1B; | &#x2B1B; | &#x2B1B; |

## Device Compatibility

30A Relay HAT is fully compatible with all **40-way** Raspberry Pi models and clones.

| Device Model | Compatibility |
| --- | :---: |
| Raspberry Pi 1 Model A+/B/B+ | &#x2714;&#xFE0F; |
| Raspberry Pi 2 Model B | &#x2714;&#xFE0F; |
| Raspberry Pi 3 Model B+ | &#x2714;&#xFE0F; |
| Raspberry Pi 4 | &#x2714;&#xFE0F; |
| Raspberry Pi Zero | &#x2714;&#xFE0F; |
| Asus Tinker Board | &#x2714;&#xFE0F; |
| Orange Pi | &#x2714;&#xFE0F; |
| Odroid | &#x2714;&#xFE0F; |
| ATMegaZero | &#x2714;&#xFE0F; |

To use with Arduino or any other 5V device the 3V3 jumper must be moved to 5V. Use the SDA &amp; SDL breakout pins for I2C communication.

## Mechanical

<p align="center">
    <a href="https://raw.githubusercontent.com/plasmadancom/HAT-RACK/master/img/30a-relay-hat-v1.1-dimensions.svg">
        <img alt="Mechanical Drawing" src="/img/30a-relay-hat-v1.1-dimensions.svg" width="600">
    </a>
</p>

## Known Compatible Cases

* [The Pi Hut Modular RPi 2/3 Case](https://thepihut.com/products/modmypi-modular-rpi-b-plus-case-black)
* [The Pi Hut Modular Raspberry Pi 4 Case](https://thepihut.com/products/modular-raspberry-pi-4-case-black)
* [The Pi Hut Cluster HAT Case v3.0](https://thepihut.com/products/cluster-hat-case)
* [Multicomp Raspberry Pi HAT Case](https://thepihut.com/products/raspberry-pi-hat-case)

## Where to Go From Here

Integrating 30A Relay HAT with your own projects is easy, just follow any guide which uses the MCP23008 or MCP23017 expander. We have provided some example Python scripts to get you started (see [here](https://github.com/plasmadancom/30A-Relay-HAT/tree/master/python_examples)).

## License

MIT © Dan Jones - [PlasmaDan.com](https://plasmadan.com)
