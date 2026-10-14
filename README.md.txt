# Arduino Calculator (Calculatrice Arduino)

A simple calculator built with an Arduino, a 16x2 LCD and a 4x4 matrix keypad.
Simulated on Wokwi.

![Screenshot](images/screenshot.png)

▶️ **Live simulation:** https://wokwi.com/projects/476800158118943745

## Features

- Addition, subtraction, multiplication and division
- Operator precedence (`*` and `/` are done before `+` and `-`)
- Decimal numbers and negative numbers
- Expression up to 32 characters, shown on line 1 of the LCD
- Result shown on line 2, aligned to the right
- Continue calculating from the previous result
- Error messages: `Erreur` (syntax) and `Div par 0` (division by zero)
- Long press on `=` clears everything, long press on `.` deletes the last character

## Components

| Component | Quantity |
|-----------|----------|
| Arduino Uno | 1 |
| LCD 16x2 (HD44780) | 1 |
| 4x4 matrix keypad | 1 |
| Potentiometer (LCD contrast) | 1 |
| Wires | - |

## Wiring

**LCD (4-bit mode)**

| LCD pin | Arduino pin |
|---------|-------------|
| RS | 13 |
| E | 12 |
| D4 | 11 |
| D5 | 10 |
| D6 | 9 |
| D7 | 8 |

**Keypad**

| Keypad | Arduino pins |
|--------|--------------|
| Rows 1–4 | 7, 6, 5, 4 |
| Columns 1–4 | A0, A1, A2, A3 |

The full circuit is in `diagram.json`.

## Keypad layout

```
1 2 3 +
4 5 6 -
7 8 9 *
. 0 = /
```

- `=` (short press): calculate
- `=` (long press, 0.8 s): clear all
- `.` (long press, 0.8 s): backspace

## How to run

**Online (easiest):** open the Wokwi link above and press the green Play button.

**On real hardware:**
1. Install the [Arduino IDE](https://www.arduino.cc/en/software).
2. Install the **Keypad** library (Sketch → Include Library → Manage Libraries → search "Keypad" by Mark Stanley and Alexander Brevig).
3. Open `sketch.ino`, select your board and port, and click Upload.

## Libraries

- `LiquidCrystal` (built into Arduino)
- `Keypad`

## How it works

1. The keypad sends key presses to `handleKey()`.
2. The typed expression is stored as text in `expr`.
3. On `=`, `evaluate()` splits the text into numbers and operators, does `*` and `/` first, then `+` and `-`.
4. `formatResult()` removes useless zeros and the result is displayed.

## Author

Your Name – Your School / Year – [GitHub profile](https://https://github.com/hamidoui)

## License

MIT License – see the `LICENSE` file.