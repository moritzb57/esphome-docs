.. _seeed_ac_voltage_sensor:

Grove AC Voltage Sensor
=======================

Introduction
------------
The **Grove AC Voltage Sensor** from SeeedStudio is used for measuring AC voltage. It provides an analog output that is proportional to the AC voltage being measured, which can be processed to compute the actual voltage values. This sensor is integrated as a subcomponent under the `seeed` component in ESPHome.

Example Configuration
---------------------
To configure the **Grove AC Voltage Sensor** as part of the Seeed component in ESPHome, use the following example:

.. code-block:: yaml

    i2c:
      sda: 6
      scl: 7
      id: bus_a

    seeed:
      ac_voltage_sensor:
        - id: my_voltage_sensor
          name: "AC Voltage"
          pin: 3  # GPIO pin connected to the analog output
          device_class: voltage
          unit_of_measurement: "V"
          accuracy_decimals: 2
          voltage_calibration: 0.13
          phase_calibration: 1.7

Configuration Variables
-----------------------
- **id** (*Required*, string): A unique identifier for the voltage sensor.
- **name** (*Required*, string): The name of the sensor that will be displayed in the interface (e.g., Home Assistant).
- **pin** (*Required*, int): The GPIO pin where the analog output of the sensor is connected.
- **voltage_calibration** (*Optional*, float, default: `1.0`): The calibration factor for converting the analog output into the correct voltage value.
- **phase_calibration** (*Optional*, float, default: `1.7`): The phase calibration factor.
- **device_class** (*Optional*, string, default: `voltage`): The device class, used for representing the type of sensor in the frontend.
- **unit_of_measurement** (*Optional*, string, default: `"V"`): The unit of measurement for the sensor output.
- **accuracy_decimals** (*Optional*, int, default: `2`): The number of decimal places to display for the voltage reading.

Additional Information
----------------------
- The sensor outputs an analog signal proportional to the AC voltage being measured. Proper calibration is needed to ensure accurate voltage readings.
- More details can be found on the SeeedStudio product page: https://www.seeedstudio.com/Grove-AC-Voltage-sensor-p-5540.html.


.. _seeed_multi_channel_relay:

Grove 4-Channel SPDT Relay
==========================

Introduction
------------
The **Grove 4-Channel SPDT Relay** allows the control of four independent relays via I2C communication. This component is also configured under the `seeed` component in ESPHome.

Example Configuration
---------------------
Here’s an example configuration for the **Grove 4-Channel SPDT Relay** as part of the Seeed component:

.. code-block:: yaml

    i2c:
      sda: 6
      scl: 7
      id: bus_a

    seeed:
      multi_channel_relay:
        - id: my_relay
          address: 0x11
          i2c_id: bus_a
          channels: 4
          name:
            - "Relay 1"
            - "Relay 2"
            - "Relay 3"
            - "Relay 4"

Configuration Variables
-----------------------
- **id** (*Required*, string): A unique identifier for the relay.
- **address** (*Optional*, hex, default: `0x11`): The I2C address of the relay module.
- **i2c_id** (*Required*, string): The I2C bus where the relay is connected.
- **channels** (*Required*, int, values: `4` or `8`): The number of channels available on the relay module.
- **name** (*Optional*, list, default: `[]`): A list of names for each relay channel. If fewer names are provided than channels, the remaining channels will be named `Relay Channel X` by default.

Additional Information
----------------------
- The relay can control up to 4 or 8 channels depending on the module, and it uses I2C communication.
- More details can be found on the SeeedStudio product page: https://www.seeedstudio.com/Grove-4-Channel-SPDT-Relay-p-3119.html.
