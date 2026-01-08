# How to Use a Force Sensor (FSR) with Arduino Uno R3

## 1. How It Works
A force sensor (FSR) changes its resistance when pressure is applied.  
- No pressure → very high resistance  
- More pressure → lower resistance  

Since Arduino cannot measure resistance directly, the FSR is used together with a fixed resistor to form a voltage divider, allowing Arduino to read force as an analog voltage.

---

## 2. How to Connect

### Required Components
- Force Sensor (FSR)
- 1 × 10 kΩ resistor
- Arduino Uno R3
- Breadboard and jumper wires

### Wiring Steps
1. Connect one pin of the FSR to **5V** on Arduino.
2. Connect the other pin of the FSR to **A0**.
3. Connect a 10 kΩ resistor:
   - One end to **A0**
   - The other end to **GND**

> The FSR has no polarity. Either pin can be used.

---

## 2*. Layout (If Have)
- The FSR has two pins only.
- It must always be used with a fixed resistor.
- Do not connect the FSR directly to A0 without a resistor.
![alt text](<images/How_to_use_Force_Sensor/fritzing_example_bb_2.png>)
---

## 3. Arduino Code

```cpp
const int fsrPin = A0;   // Force sensor connected to A0

void setup() {
  Serial.begin(9600);
  Serial.println("FSR test started");
}

void loop() {
  int fsrValue = analogRead(fsrPin);  // Read value (0–1023)

  Serial.print("FSR reading: ");
  Serial.println(fsrValue);

  delay(200);
}
```
## 4. How to Verify

1. Upload the code to the Arduino Uno.
2. Open **Tools → Serial Monitor**.
3. Set the baud rate to **9600**.
4. Press the force sensor with different strengths.

### Expected Result
- No pressure → very low value  
- Light pressure → small increase  
- Strong pressure → larger value  
- The value changes smoothly with applied force  

---

## 5. Notes: How to Choose the Resistor

The fixed resistor determines which **pressure range** the sensor is most sensitive to.

- **Larger resistor (e.g. 47 kΩ)**
  - More sensitive to light pressure
  - Output saturates quickly
  - Suitable for touch or gentle pressing

- **Medium resistor (e.g. 10 kΩ)**
  - Balanced response
  - Good for general laboratory experiments
  - Recommended default value

- **Smaller resistor (e.g. 1 kΩ – 4.7 kΩ)**
  - Less sensitive to light pressure
  - Better for higher force
  - Suitable for heavy pressing or load detection

> **In summary:**  
> Resistor value selects the effective force measurement range, not the accuracy.
