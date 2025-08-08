# Infernal Cipher
## Category: Reverse Engineering

## 1️⃣ How to Solve the Challenge (Step-by-step)

### Step 1: Understand the challenge

* The program **does NOT store the flag** directly.
* It runs a **simple custom virtual machine** that:

  * Reads your input characters one by one (`INP` instruction).
  * Does some arithmetic and bitwise ops.
  * Compares results with hardcoded expected values.
* The VM returns success only if all character checks pass.

### Step 2: Analyze the bytecode

Look at the `bytecode` array:

* It checks each character in the input (via `0x02` `INP` opcode).
* Then pushes a constant (`0x01` `PUSH` opcode) — a character from the real flag.
* XORs (`0x03`).
* Subtracts 1 (`0x01 0x01` then `0x05`).
* Compares result to zero (`0x06 0x00`).

This means the check is:

```
(input_char XOR expected_char) - 1 == 0
```

or rearranged:

```
input_char XOR expected_char == 1
```

So

```
input_char == expected_char XOR 1
```

### Step 3: Extract expected chars and compute input chars

The expected chars are the `PUSH` values after every `INP`. From the bytecode:

```
'f' (0x66), 'l' (0x6c), 'a' (0x61), 'g' (0x67), '{' (0x7b),
'v' (0x76), 'm' (0x6d), '_' (0x5f), 'b' (0x62), 'a' (0x61),
's' (0x73), 'e' (0x65), 'd' (0x64), '_' (0x5f), 'i' (0x69),
'n' (0x6e), 'f' (0x66), 'e' (0x65), 'r' (0x72), 'n' (0x6e),
'o' (0x6f), '_' (0x5f), 'l' (0x6c), 'o' (0x6f), 'g' (0x67),
'i' (0x69), 'c' (0x63), '}' (0x7d)
```

### Step 4: Calculate correct input chars:

Input char = expected\_char XOR 1

We can write a quick script (or do it manually) to find input chars:

```python
expected = [0x66, 0x6c, 0x61, 0x67, 0x7b,
            0x76, 0x6d, 0x5f, 0x62, 0x61,
            0x73, 0x65, 0x64, 0x5f, 0x69,
            0x6e, 0x66, 0x65, 0x72, 0x6e,
            0x6f, 0x5f, 0x6c, 0x6f, 0x67,
            0x69, 0x63, 0x7d]

input_chars = [chr(c ^ 1) for c in expected]
print("".join(input_chars))
```

Result of the python script:

```
gm`fzwl^c`rde^hogdson^mnfhb|
```

### Step 5: Test input on binary

Run `./inferno` and enter that string:

```
gm`fzwl^c`rde^hogdson^mnfhb|
```

(Verify exact characters from your output)

You will see:

<img width="1390" height="171" alt="image" src="https://github.com/user-attachments/assets/548bb9cc-9684-4fd8-9174-ef0452cf8acb" />


```
You have awakened Ifrit! You may now rule: flag{vm_based_inferno_logic}
```

---

## 2️⃣ Summary:

* You wrote a **custom VM** validating input transformed by XOR + arithmetic.
* The **real flag is never in the binary or memory** as-is.
* The solver reverse engineers the bytecode and recovers input required to pass checks.
* Upon success, the **flag is printed** only.
