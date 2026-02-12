### How to use Light Sensor 
# Light Sensor (2-pin LDR)

## 1. How it works
A 2-pin light sensor (LDR, Light Dependent Resistor) is a passive component whose resistance changes with light intensity.

- Bright environment → lower resistance  
- Dark environment → higher resistance  

Since Arduino cannot measure resistance directly, the LDR must be connected with a fixed resistor to form a **voltage divider**, and the voltage is read through an **analog pin**.

---

## 2. How to connect

### Components required
- Arduino (UNO / Nano / Mega)
- Breadboard
- Light sensor (2-pin LDR)
- 10kΩ resistor
- Jumper wires

### Wiring steps
1. Insert the LDR into the breadboard, making sure its two pins are in **different rows**
2. Connect one pin of the LDR to **5V**
3. Connect the other pin of the LDR to **A0**
4. Connect one end of a **10kΩ resistor** to **A0**
5. Connect the other end of the resistor to **GND**
6. Connect Arduino **5V** to the breadboard positive rail
7. Connect Arduino **GND** to the breadboard ground rail

### Circuit structure
![alt text](</images/How_to_use_light_sensor/how_to_use_light_sensor.png>)

---

## 3. Layout

- The LDR should be placed across two different rows on the breadboard  
- The junction between the LDR and the resistor is connected to **A0**  
- The resistor must connect from **A0** to **GND**

> Note: The LDR has no polarity. Either pin can be connected to 5V or A0.
---

## 4. Test code

```cpp
int lightPin = A0;
int lightValue = 0;

void setup() {
  Serial.begin(9600);
}

void loop() {
  lightValue = analogRead(lightPin);
  Serial.print("Light value: ");
  Serial.println(lightValue);
  delay(500);
}
```
## 5. How to verify

1. Upload the code to Arduino  
2. Open **Serial Monitor** (9600 baud)  
3. Cover the light sensor → the value should change  
4. Shine a light on the sensor → the value should change again  

### Typical readings
- Dark: 100 – 300  
- Indoor light: 300 – 700  
- Bright light: 700 – 1023  

*(Values may vary depending on environment and resistor value.)*

---

## 6. Notes / Supplement

- A **10kΩ resistor** is recommended, but **4.7kΩ–20kΩ** can also be used  
- This is an **analog sensor** and must be connected to an **analog pin**  
- If the reading is always **0** or **1023**, check the wiring and resistor connection  
