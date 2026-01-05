## Analogue Stick (5-Pin) with Arduino Uno R3

### 1. How to Use the Analogue Stick

A 5-pin analogue stick is an input device that detects movement in two directions (X and Y) and also includes a built-in push button.  
The Arduino reads the position of the stick as analogue values and reads the button as a digital signal.

**Pin description:**

| Pin | Description |
|-----|------------|
| **VCC** | Power supply, usually 5V |
| **GND** | Ground |
| **VRx / X** | Horizontal movement (left and right) |
| **VRy / Y** | Vertical movement (up and down) |
| **SW** | Push button (pressing the stick down) |

The X and Y pins output analogue values ranging from **0 to 1023**, depending on the stick position.

---

### 2. How to Connect the Analogue Stick

The recommended way to connect the analogue stick to the Arduino Uno R3 is to use **Dupont jumper wires (female-to-male)**.  
The female ends connect to the stick pins, and the male ends connect to the Arduino headers.

**Connection example:**

| Analogue Stick | Arduino Uno R3 |
|---------------|----------------|
| **VCC** | **5V** |
| **GND** | **GND** |
| **VRx / X** | **A0** |
| **VRy / Y** | **A1** |
| **SW** | **D2** |

> The X and Y pins must be connected to analogue input pins (A0–A5).

---

### 3. Arduino Code

The following code reads the X axis, Y axis, and button state, and prints the values to the Serial Monitor.

```cpp
const int xPin = A0;   // X-axis
const int yPin = A1;   // Y-axis
const int swPin = 2;   // Button (SW)

void setup() {
  Serial.begin(9600);
  pinMode(swPin, INPUT_PULLUP);
  Serial.println("Analogue stick test started");
}

void loop() {
  int xValue = analogRead(xPin);
  int yValue = analogRead(yPin);
  int swValue = digitalRead(swPin);

  Serial.print("X: ");
  Serial.print(xValue);
  Serial.print(" | Y: ");
  Serial.print(yValue);
  Serial.print(" | SW: ");
  Serial.println(swValue);

  delay(200);
}
```
### 4. How to Verify the Analogue Stick

1. Upload the code to the Arduino.
2. Open **Tools → Serial Monitor**.
3. Set the baud rate to **9600**.
4. Move the analogue stick and press it down.

**Expected behaviour:**
- When the stick is centered, X and Y values are close to **512**.
- Moving the stick changes the values smoothly between **0 and 1023**.
- Pressing the stick changes `SW` from **1** to **0**.

### 5. Notes and Supplement (Stable Readings)

It is normal for the X and Y values to change slightly even when the analogue stick is not moving.

- The analogue stick uses potentiometers to generate analogue signals.
- Analogue signals are sensitive to small electrical noise.
- The center position is a small range, not a single fixed value.

These small fluctuations are expected and do not indicate a hardware problem.

#### Supplement: Averaged Reading Example

```cpp
const int xPin = A0;
const int yPin = A1;
const int swPin = 2;

int readAverage(int pin) {
  long total = 0;
  for (int i = 0; i < 10; i++) {
    total += analogRead(pin);
  }
  return total / 10;
}

void setup() {
  Serial.begin(9600);
  pinMode(swPin, INPUT_PULLUP);
  Serial.println("Analogue stick test (averaged)");
}

void loop() {
  int xValue = readAverage(xPin);
  int yValue = readAverage(yPin);
  int swValue = digitalRead(swPin);

  Serial.print("X: ");
  Serial.print(xValue);
  Serial.print(" | Y: ");
  Serial.print(yValue);
  Serial.print(" | SW: ");
  Serial.println(swValue);

  delay(200);
}
```