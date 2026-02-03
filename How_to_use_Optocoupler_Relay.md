# How to Use an Optocoupler Relay Module (Arduino)

## 1. How it works

An **optocoupler relay module** uses an **optocoupler (optical isolator)** to electrically isolate the Arduino control side from the load side.

- Arduino sends a digital signal to the **CTR (control) pin**
- The optocoupler’s internal LED turns on and drives the relay circuit
- The relay switches the external circuit (lamp, motor, etc.)
- Optical isolation improves **safety** and reduces electrical noise

For this module, the control logic is:

> **LOW = ON (triggered)**  
> **HIGH = OFF (released)**

---

## 2. Pin definition (4-pin module)

| Pin | Function |
|-----|----------|
| VCC | Power supply (5V) |
| GND | Ground |
| CTR | Control signal from Arduino |
| NC  | Relay output (Normally Closed) |

---

## 3. Components required

- Arduino (UNO / Nano / Mega)
- Optocoupler relay module (4-pin: VCC, GND, CTR, NC)
- Breadboard
- Jumper wires
- (Optional) low-voltage load (LED, small motor, or lamp)

---

## 4. Wiring

| Module Pin | Arduino Pin |
|------------|-------------|
| VCC | 5V |
| GND | GND |
| CTR | D7 |
| NC  | External load (optional) |

> Note:  
> - The **CTR pin is active LOW** (LOW = ON).  
> - If no load is connected, you can still verify operation using the indicator LED or relay sound.

---

## 5. Test code

```cpp
#define CTR_PIN 7   // CTR connected to Arduino D7

void setup() {
  pinMode(CTR_PIN, OUTPUT);
  digitalWrite(CTR_PIN, HIGH);  // Default state (relay OFF, active LOW)
}

void loop() {
  digitalWrite(CTR_PIN, LOW);   // Relay ON
  delay(2000);

  digitalWrite(CTR_PIN, HIGH);  // Relay OFF
  delay(2000);
}
```
## 6. How to verify

1. Upload the code to the Arduino.  
2. Observe the relay module:
   - The indicator LED turns **ON and OFF every 2 seconds**.
   - A clicking sound may be heard from the relay.
3. (Optional) Connect a low-voltage load to the **NC** terminal and observe it switching.

### Expected behavior

- Relay turns **ON for 2 seconds**  
- Relay turns **OFF for 2 seconds**  
- This cycle repeats continuously
