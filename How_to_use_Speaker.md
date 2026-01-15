## How to Use a Speaker with Arduino Uno R3

## 1. How to Use the Speaker

A **passive speaker** produces sound when driven by a digital signal from the Arduino.  
The Arduino generates sound using the built-in `tone()` function.

> This guide assumes a **passive speaker with two pins**.

---

## 2. How to Connect the Speaker

### Required Components
- Arduino Uno R3  
- Passive speaker (two pins)  
- Breadboard  
- 1 × resistor (100 Ω–220 Ω)  
- Jumper wires  

### Wiring Principle
- Speaker is connected **in series with a resistor**
- One side goes to a **digital pin**
- The other side goes to **GND**

### Example Wiring

| Component | Connection |
|---------|------------|
| Arduino D9 | → Resistor |
| Resistor | → Speaker |
| Speaker | → Arduino GND |

**Connection order:**  
`Arduino D9 → Resistor → Speaker → GND`


::contentReference[oaicite:0]{index=0}


> Any digital pin can be used, but **D9** is recommended.

---

## 3. Layout (Breadboard)

- Speaker pins **must not be in the same row**
- Resistor must be **in series**, not parallel
- GND should be clearly connected back to Arduino GND


::contentReference[oaicite:1]{index=1}


---

## 4. Arduino Code

Copy and upload the following code:

```cpp
// Speaker connected to digital pin 9
const int speakerPin = 9;

void setup() {
  // No setup required
}

void loop() {
  tone(speakerPin, 1000);   // Play 1000 Hz tone
  delay(1000);              // Sound for 1 second

  noTone(speakerPin);       // Stop sound
  delay(1000);              // Silence for 1 second
}
```
## 5. How to Verify the Speaker

1. Connect the Arduino to the computer using a USB cable.
2. Open **Arduino IDE**.
3. Select the following options:
   - **Tools → Board → Arduino Uno**
   - **Tools → Port → Correct COM port**
4. Click **Upload**.

### Expected Result
- The speaker plays a tone for **1 second**.
- The speaker is silent for **1 second**.
- This pattern repeats continuously.
