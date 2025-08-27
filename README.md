

## Explanation of the Code

### 1. Functions for Number System Conversion

I created **four conversion functions** to handle conversions between decimal, binary, and hexadecimal systems:

---

#### a. `decimalToBinary(int num)`

* Converts a decimal integer to its binary string representation.
* Uses repeated division by 2 and prepends either `"0"` or `"1"` to build the binary string.
* Example:

  * Input: `13`
  * Output: `"1101"`

---

#### b. `binaryToDecimal(const string& binStr)`

* Converts a binary string (e.g., `"1101"`) back to a decimal integer.
* Iterates over each character and checks if it's `'0'` or `'1'` (invalid input returns -1).
* Multiplies the accumulated decimal by 2 and adds the current bit.
* Example:

  * Input: `"1101"`
  * Output: `13`

---

#### c. `decimalToHexadecimal(int num)`

* Converts a decimal integer to its hexadecimal string.
* Uses repeated division by 16, using a string `"0123456789ABCDEF"` to map digits to hex characters.
* Example:

  * Input: `254`
  * Output: `"FE"`

---

#### d. `hexadecimalToDecimal(const string& hexStr)`

* Converts a hexadecimal string to a decimal integer.
* Iterates through each hex character, converts it to its decimal value, and accumulates.
* Accepts both uppercase and lowercase hex digits.
* Example:

  * Input: `"FE"`
  * Output: `254`

---

### 2. Demo Function: `demo()`

* Generates a random number between 0 and 99.
* Prints the number and its binary representation using `decimalToBinary`.
* Demonstrates the usage of conversion functions in a simple context.

---

### 3. Menu System in `main()`

* Displays a menu with six options:

  1. Decimal to Binary
  2. Binary to Decimal
  3. Decimal to Hexadecimal
  4. Hexadecimal to Decimal
  5. Demo (random number conversion)
  6. Exit

* Takes user input and calls the corresponding function.

* Validates inputs (e.g., checks for non-negative decimal input and valid characters in binary/hex).

* Loops indefinitely until the user chooses to exit.

---

### Example Session

```
Conversion Menu:
1. Convert Decimal to Binary
2. Convert Binary to Decimal
3. Convert Decimal to Hexadecimal
4. Convert Hexadecimal to Decimal
5. Demo (generate random number and convert to binary)
6. Exit
Enter your choice (1-6): 1
Enter a decimal number: 45
Binary representation: 101101

Conversion Menu:
...
Enter your choice (1-6): 4
Enter a hexadecimal number: 1A3F
Decimal equivalent: 6719

Conversion Menu:
...
Enter your choice (1-6): 5
Random number: 27
Binary representation: 11011
```

---

## Challenges and How I Addressed Them

### 1. Input Validation

* Binary and hexadecimal inputs can be tricky because users might enter invalid characters.
* I added checks to detect invalid inputs and return an error (printing `"Invalid binary number"` or `"Invalid hexadecimal number"`).
* C++ strings don't have built-in base conversion like some higher-level languages, so I had to manually implement validation.

### 2. Conversion Logic

* Implementing decimal to binary and hex required building the string from remainder calculations and prepending digits.
* Edge cases like `0` needed special handling to avoid returning empty strings.

### 3. Menu Interaction and Input Types

* C++ `cin` can sometimes behave unexpectedly if input types don't match or leftover newline characters remain in the buffer.
* Kept inputs straightforward (integers for choices and decimals, strings for binary/hex) to reduce complexity.
* Added checks for invalid menu choices.

### 4. Random Number Generation

* Used `srand(time(0))` once at the start of the program to seed the random number generator.
* The demo function uses `rand() % 100` to keep numbers in a reasonable range.



