## How to Use a Keypad with Arduino

To use a **4×3 matrix keypad** with an Arduino, you must first identify the **rows and columns**, then connect them correctly to the Arduino’s digital pins.

### 1. Identify Rows and Columns
A matrix keypad is made up of **rows** and **columns**.

- Count the **number of rows** on the keypad (usually visible from the front layout).
- The number of rows tells you how many pins are used for rows.
- The remaining pins are used for columns.

**Example:**  
If the keypad has **4 rows**, then the **first 4 pins** (from left to right) are **row pins**, and the remaining pins are **column pins**.  
A 4×3 keypad therefore has **4 row pins + 3 column pins = 7 pins total**.

### 2. Connect the Keypad to the Arduino
Connect each row and column pin from the keypad to a **digital pin** on the Arduino Uno.

**Example wiring:**

| Keypad Pin | Function | Arduino Pin |
|-----------|----------|-------------|
| Pin 1 | Row 1 (R1) | D9 |
| Pin 2 | Row 2 (R2) | D8 |
| Pin 3 | Row 3 (R3) | D7 |
| Pin 4 | Row 4 (R4) | D6 |
| Pin 5 | Column 1 (C1) | D5 |
| Pin 6 | Column 2 (C2) | D4 |
| Pin 7 | Column 3 (C3) | D3 |

> Any digital pins can be used. Just make sure the same pin numbers are defined correctly in your Arduino code.

### 3. Keypad Layout (4×3)
![alt text](<Keypadlayout.png>)

---

## 4. Arduino Code

Install the **Keypad** library first:  
`Arduino IDE → Sketch → Include Library → Manage Libraries → Search "Keypad"`

```cpp
#include <Keypad.h>
// The ROWS and COLS depend on layout
const byte ROWS = 4;
const byte COLS = 3; 
// Align with layout
char keys[ROWS][COLS] = {
  {'1','2','3'},
  {'4','5','6'},
  {'7','8','9'},
  {'*','0','#'}
};

byte rowPins[ROWS] = {9, 8, 7, 6};   // R1–R4
byte colPins[COLS] = {5, 4, 3};      // C1–C3

Keypad keypad = Keypad(makeKeymap(keys), rowPins, colPins, ROWS, COLS);

void setup() {
  Serial.begin(9600);
  Serial.println("Keypad test started");
}

void loop() {
  char key = keypad.getKey();
  if (key) {
    Serial.print("Pressed: ");
    Serial.println(key);
  }
}
```
## 5. How to Verify the Keypad

1. Upload the code to the Arduino.
2. Open **Tools → Serial Monitor**.
3. Set the baud rate to **9600**.
4. Press any key on the keypad.

### Expected Result
- Each key press is displayed in the Serial Monitor.
- The printed character matches the key pressed.
