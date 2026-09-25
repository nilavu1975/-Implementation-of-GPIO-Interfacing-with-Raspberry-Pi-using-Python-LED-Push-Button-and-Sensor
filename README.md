# Experiment: Implementation of GPIO Interfacing with Raspberry Pi using Python – LED, Push Button, and Sensor

## 1. AIM# Implementation of GPIO Interfacing with Raspberry Pi using MicroPython
## Aim
To implement GPIO interfacing on Raspberry Pi Pico using MicroPython for controlling an LED, reading a push button input, and monitoring a sensor value.

## Apparatus Required
Raspberry Pi Pico (simulated in Wokwi)

1 × LED (with 220Ω resistor)

1 × Push Button (4‑pin type)

1 × Analog Sensor (e.g., potentiometer or IR sensor)

Jumper wires

Breadboard

## Procedure
Connect the LED anode to GP15 via a 220Ω resistor, cathode to GND.

Connect the push button:

One side (pins 1–2) → 3V3

Other side (pins 3–4) → GP14

Configure GP14 with internal pull‑down in code.

Connect the sensor:

VCC → 3V3

GND → GND

OUT → GP26 (ADC0)

Write MicroPython code to:

Turn LED ON when button is pressed.

Read sensor values via ADC and print them to the serial monitor.

Upload and run the code in Wokwi simulator.

## Pin Diagram (Pseudo Representation)
Code
Raspberry Pi Pico
+-----------------------------+
|                             |
| 3V3 -----> Button (pins 1-2)|
| GP14 <---- Button (pins 3-4)|
| GP15 -----> LED (via 220Ω)  |
| GND -----> LED cathode      |
| GP26 <---- Sensor OUT       |
| 3V3 -----> Sensor VCC       |
| GND -----> Sensor GND       |
+-----------------------------+
## Code (MicroPython)
#### python
    from machine import Pin, ADC
    import time

    # LED on GP15
    led = Pin(15, Pin.OUT)

    # Push button on GP14 with pull-down
    button = Pin(14, Pin.IN, Pin.PULL_DOWN)

    # Sensor on ADC0 (GP26)
    sensor = ADC(Pin(26))

    while True:
        # Button control
        if button.value() == 1:   # pressed
            led.value(1)
        else:
            led.value(0)

        # Sensor reading
        sensor_value = sensor.read_u16()
        voltage = (sensor_value / 65535) * 3.3

        print("Sensor:", sensor_value, "Voltage:", voltage)

        time.sleep(0.5)

## Output:

<img width="1024" height="487" alt="image" src="https://github.com/user-attachments/assets/57efc663-11db-4dcf-b96d-271e57d66c3c" />


## Result

The LED glows when the push button is pressed.

The sensor values are read through ADC and displayed in the serial monitor as both raw values and voltage.

Thus, GPIO interfacing with Raspberry Pi Pico using MicroPython is successfully 


g of LED, push button, and sensor with Raspberry Pi using Python** was successfully implemented and simulated using the **Wokwi simulator**.

