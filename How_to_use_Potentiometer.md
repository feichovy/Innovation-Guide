# How to use Potentiometer with Arduino R3

## 1. How it works
A potentiometer is a **variable resistor** that outputs a **continuous voltage** depending on the knob position.
![alt text](</images/How_to_use_potentiometer/What-is-a-potentiometer.png>)
- The two outer pins are connected to **5V** and **GND**
- The middle pin (wiper) outputs a voltage between **0V and 5V**
- This output is a **continuous (analog) signal**
- Arduino reads this signal using an **analog input pin**

Because the output voltage changes smoothly, the potentiometer must be connected to **A0 (or any analog pin)** and read using `analogRead()`.

---

## 2. How to connect

### Components required
- Arduino UNO
- Potentiometer (3-pin)
- Jumper wires (female-to-female recommended)

### Wiring steps
1. Connect the **middle pin** of the potentiometer to **A0**
2. Connect **one outer pin** to **5V**
3. Connect the **other outer pin** to **GND**

> Note: The potentiometer pins may not fit directly into a breadboard.  
> Use jumper wires to connect the pins to the breadboard or Arduino.

---

## 3. Layout (Wiring reference)
![alt text](images/How_to_use_potentiometer/Layout.png)

- The **middle pin** is always the signal output
- The two outer pins are the power ends
- Swapping 5V and GND only changes rotation direction


---

## 4. Test code

```cpp
int potPin = A0;     // Middle pin of potentiometer
int potValue = 0;

void setup() {
  Serial.begin(9600);
}

void loop() {
  potValue = analogRead(potPin);
  Serial.print("Potentiometer value: ");
  Serial.println(potValue);
  delay(200);
}
```

## 5. How to verify

1. Upload the code to Arduino  
2. Open **Serial Monitor** (9600 baud)  
3. Slowly rotate the potentiometer knob  

### Expected behavior
- One end: value close to **0**  
- Middle position: value around **512**  
- Other end: value close to **1023**  

The value should change **smoothly and continuously**.

---

## 6. Notes / Supplement

- The potentiometer is an **analog input device**
- The **middle pin** must connect to an **analog pin**
- The potentiometer does **not** need to be inserted into a breadboard to work
- If the value does not change, check that the middle pin is connected to **A0**
- If the direction feels reversed, swap the **5V** and **GND** connections

