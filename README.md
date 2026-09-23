# Experiment: Implementation of GPIO Interfacing with Raspberry Pi using Python – LED, Push Button, and Sensor

## 1. AIM

To implement and simulate **GPIO interfacing with Raspberry Pi using Python** by controlling an **LED**, reading the input from a **push button**, and interfacing a **sensor** using the **Wokwi online simulator**.

## 2. APPARATUS REQUIRED

| S.No. | Component        |    Quantity |
| ----- | ---------------- | ----------: |
| 1     | Raspberry Pi     |           1 |
| 2     | LED              |           1 |
| 3     | Push Button      |           1 |
| 4     | Resistor – 220 Ω |           1 |
| 5     | Sensor           |           1 |
| 6     | Breadboard       |           1 |
| 7     | Jumper Wires     | As required |
| 8     | Computer/Laptop  |           1 |

### Software Required

* **Wokwi Online Simulator**
* **Python 3**
* **Raspberry Pi GPIO Python library**

> Since this practical is being simulated, **Wokwi** is considered the software/simulation platform.

## 3. THEORY

GPIO stands for **General Purpose Input/Output**. Raspberry Pi GPIO pins can be programmed as either **input** or **output**.

* **Output:** Used to control devices such as LEDs.
* **Input:** Used to read devices such as push buttons and sensors.
* A Python program is used to configure and control the GPIO pins.

In this experiment:

1. The **LED** is connected to a GPIO output pin.
2. The **push button** is connected to a GPIO input pin.
3. The **sensor** is connected to another GPIO input pin.
4. Python is used to read the input and control the LED accordingly.

## 4. GPIO PIN CONNECTIONS

| Component                  | Raspberry Pi GPIO   | Function |
| -------------------------- | ------------------- | -------- |
| LED Anode                  | GPIO 17             | Output   |
| LED Cathode                | GND through 220 Ω   | Ground   |
| Push Button                | GPIO 27             | Input    |
| Push Button other terminal | GND                 | Ground   |
| Sensor VCC                 | 5V/3.3V as required | Power    |
| Sensor GND                 | GND                 | Ground   |
| Sensor OUT                 | GPIO 22             | Input    |

**Note:** The exact sensor connections depend on the sensor model used in your Wokwi circuit.

## 5. BLOCK DIAGRAM

```text
              ┌──────────────────────┐
              │     Raspberry Pi     │
              │                      │
              │   GPIO 17 ───────────┼────> LED
              │                      │
              │   GPIO 27 <──────────┼──── Push Button
              │                      │
              │   GPIO 22 <──────────┼──── Sensor
              │                      │
              └──────────────────────┘
                         │
                         ▼
                       GND
```

<img width="1200" height="630" alt="1772130665569" src="https://github.com/user-attachments/assets/a7c38f56-e7d5-459e-8b07-e117ae760f29" />

## 6. ALGORITHM

1. Start the program.
2. Import the required GPIO and time libraries.
3. Set the GPIO numbering mode.
4. Configure the LED pin as an **output**.
5. Configure the push button pin as an **input**.
6. Configure the sensor pin as an **input**.
7. Continuously read the push button and sensor.
8. If the required input condition is detected, turn ON the LED.
9. Otherwise, turn OFF the LED.
10. Repeat the process continuously.
11. Stop the program and clean up the GPIO pins.

## 7. PYTHON PROGRAM

```python
import RPi.GPIO as GPIO
import time

# GPIO pin numbers
LED = 17
BUTTON = 27
SENSOR = 22

# GPIO setup
GPIO.setmode(GPIO.BCM)

GPIO.setup(LED, GPIO.OUT)
GPIO.setup(BUTTON, GPIO.IN, pull_up_down=GPIO.PUD_UP)
GPIO.setup(SENSOR, GPIO.IN)

try:
    while True:

        button_state = GPIO.input(BUTTON)
        sensor_state = GPIO.input(SENSOR)

        # Turn ON LED when button is pressed
        # or sensor detects an input
        if button_state == GPIO.LOW or sensor_state == GPIO.HIGH:
            GPIO.output(LED, GPIO.HIGH)
            print("LED ON")
        else:
            GPIO.output(LED, GPIO.LOW)
            print("LED OFF")

        time.sleep(0.2)

except KeyboardInterrupt:
    print("Program stopped")

finally:
    GPIO.cleanup()
```

### Important

If your **Wokwi sensor is a specific sensor** such as **PIR, ultrasonic, LDR, DHT11, etc.**, the Python code and connections should be changed accordingly. So I would prefer to see your PDF before you submit this.

## 8. PROCEDURE

1. Open the **Wokwi** simulator.
2. Create a Raspberry Pi-based project.
3. Add the required LED, resistor, push button, sensor and connecting wires.
4. Connect the LED to **GPIO 17** through a 220 Ω resistor.
5. Connect the push button to **GPIO 27**.
6. Connect the sensor output to **GPIO 22**.
7. Connect the required VCC and GND connections.
8. Enter the Python program.
9. Run the simulation.
10. Press the push button and observe the LED.
11. Activate the sensor and observe the LED response.
12. Verify that the LED turns ON when the programmed input condition occurs.

## 9. EXPECTED OUTPUT

```text
LED OFF
LED OFF
LED ON
LED ON
LED OFF
```

When the **push button is pressed** or the **sensor detects the required condition**, the LED glows.

When neither input condition is active, the LED remains OFF.

## 10. RESULT

The **GPIO interfacing of LED, push button, and sensor with Raspberry Pi using Python** was successfully implemented and simulated using the **Wokwi simulator**.

