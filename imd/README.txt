--Insulation Monitoring Device (IMD)
-Luca Previati

This module is used in high-voltage Automotive electrical systems to check the insulation between the batteries and the chassis itself.
It is required from regulation purposes and it has to be equivalent in insulation characteristics and functionalities to the provided model from the competition organization.

The model used in this project is the following:
Sendyne SIM1000 (https://sendyne.com/Products/SIM100%20Isolation%20Monitor.html)
It interlaces with insulated CAN 2.0B modules to the voltage between batteries and chassis, and it provides a USB-CAN dongle adapter with proprietary software.

However, in addiction to the IMD module, we implement a different USB-to-CAN adapter that is compatible with Arduino microcontrollers, as it is much easier to program and use in this context
than the one provided directly in the Sendyne SIM1000 kit.
We chose to adopt the following module:
Longan Serial CAN Module (https://docs.longan-labs.cc/1030001/)
This module provides direct CAN-USB connection to work directly with Arduino boards, providing a full Arduino library and connectivity cables for communication.

---

As we need to implement this system on the car, we need an autonomous device that does the following steps:

* Read the resistance value from the Sendyne IMD module
* Convert the CAN data provided in a serial stream with the USB-CAN dongle
* Invert the value of pin D5 on the Arduino microcontroller connected to the CAN adapter:
    * if the value is less than 300KΩ, pull down the D5 pin on the Arduino
    * if the value is greater or higher than 300KΩ, pull high the D5 pin