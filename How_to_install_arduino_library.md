# How to Install an Arduino Library

This guide explains two common ways to install Arduino libraries, using the **I2C LCD (LiquidCrystal I2C)** library as an example.

---

## Method 1: Install Arduino Libraries via Website (ZIP File)

### Step 1: Download the Library

For this tutorial, we will install the I2C LCD screen module library.

1. Open the official Arduino library page:
   https://www.arduino.cc/reference/en/libraries/liquidcrystal-i2c/
2. Download **LiquidCrystal_I2C version 1.1.2** as a ZIP file.

![Download library](images/How_to_install_arduino_library/1765899506735.png)

---

### Step 2: Add the ZIP Library in Arduino IDE

1. Open **Arduino IDE**
2. From the top menu, navigate to:

![Add ZIP library](images/How_to_install_arduino_library/1765899608990.png)

---

### Step 3: Select the ZIP File

1. Locate `LiquidCrystal_I2C-1.1.2.zip` (usually in the **Downloads** folder)
2. Click **Open**

![Select ZIP file](images/How_to_install_arduino_library/1765899655160.png)

---

### Step 4: Verify Installation

Once installed, a confirmation message will appear in the Arduino IDE output window, indicating the library has been successfully added.

---

## Method 2: Install a Library Using Arduino Library Manager

### Step 1: Open Arduino IDE

Launch **Arduino IDE**

![Open Arduino IDE](images/How_to_install_arduino_library/1765899801860.png)

---

### Step 2: Open Library Manager

Click the **Library Manager** icon (book icon) on the left-hand toolbar.

![Library Manager icon](images/How_to_install_arduino_library/1765899825625.png)

Sketch → Include Library → Add .ZIP Library...

---

### Step 3: Search and Install the Library

1. In the search bar, type: LiquidCrystal I2C
2. Select **LiquidCrystal I2C by Frank de Brabander**
3. Click **Install**

![Install library](images/How_to_install_arduino_library/1765899856295.png)

---

## Notes

- Both installation methods achieve the same result
- **Library Manager** is recommended for most standard libraries
- **ZIP installation** is useful for older versions or manually downloaded libraries
  





