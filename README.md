# 12_Security_Access_Control_with_leds

# RGB LED Security Access Control System

## Overview

This project extends the security access control system by adding an RGB LED to provide visual feedback based on the entered passcode. When the correct passcode is entered, the RGB LED glows blue, indicating successful access. If an incorrect passcode is entered, the RGB LED glows red, signaling an incorrect attempt. Only numeric keys are allowed for passcode entry.

## Components

- Arduino board (e.g., Uno, Mega)
- 4x4 Keypad
- RGB LED
- Buzzer
- Jumper wires

## Circuit Diagram

1. **Keypad**
   - Connect the row pins of the keypad to digital pins 2, 3, 4, and 5 on the Arduino.
   - Connect the column pins of the keypad to digital pins 6, 7, 8, and 9 on the Arduino.

2. **RGB LED**
   - Connect the red pin of the RGB LED to digital pin 10 on the Arduino.
   - Connect the blue pin of the RGB LED to digital pin 11 on the Arduino.
   - Connect the common cathode (GND) pin of the RGB LED to GND on the Arduino.

3. **Buzzer**
   - Connect the positive (+) pin of the buzzer to digital pin 12 on the Arduino.
   - Connect the negative (-) pin of the buzzer to GND on the Arduino.

## Code Explanation

### Variables and Objects

- `keys[][]`: Array to define the layout of the keypad.
- `rowPins[]` and `colPins[]`: Arrays to define the pins connected to the rows and columns of the keypad.
- `kpd`: Keypad object for reading key presses.
- `keyCode`: Predefined passcode for access control.
- `keyCodeBuffer`: String variable to store the passcode entered by the user.
- `buzzerPin`: Pin connected to the buzzer for sounding the alarm.
- `redPin` and `bluePin`: Pins connected to the red and blue terminals of the RGB LED, respectively.

### Setup

- Serial communication is initialized at 9600 baud.
- Pins connected to the buzzer and RGB LED are set as OUTPUT.
- The RGB LED is turned off initially by setting its pins to LOW.

### Loop

- The code continuously checks for key presses on the keypad.
- If a numeric key (0-9) is pressed, it is appended to the `keyCodeBuffer`.
- If the '#' key is pressed, the entered passcode is compared with the predefined passcode (`keyCode`).
  - If the passcodes match, a message indicating successful access is printed to the Serial Monitor, and the RGB LED glows blue.
  - If the passcodes do not match, an alarm is triggered by activating the buzzer, the RGB LED glows red, and a message indicating an incorrect passcode is printed to the Serial Monitor.
- If an invalid key is pressed, a message indicating an invalid key is printed to the Serial Monitor.

## Usage Instructions

1. Assemble the circuit as per the circuit diagram.
2. Upload the provided code to the Arduino board.
3. Open the Serial Monitor from the Arduino IDE (Tools -> Serial Monitor) to view status messages.
4. Enter the predefined passcode using the keypad.
5. Press '#' to submit the passcode.
6. Observe the behavior of the system:
   - If the passcode is correct, a message indicating successful access is displayed, and the RGB LED glows blue.
   - If the passcode is incorrect, an alarm is triggered, the RGB LED glows red, and a message indicating an incorrect passcode is displayed.

## Example Output

- Entering the correct passcode followed by '#' will display:
  ```
  Passcode is correct
  ```
  and the RGB LED will glow blue.
- Entering an incorrect passcode followed by '#' will trigger the buzzer, the RGB LED will glow red, and display:
  ```
  Passcode is incorrect
  ```

This project enhances the security access control system by providing visual feedback through an RGB LED, making it suitable for applications where visual indicators are necessary.

---

