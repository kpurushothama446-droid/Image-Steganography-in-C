# 🖼️ IMAGE STEGANOGRAPHY IN C

### LSB-Based Data Hiding | BMP Image Processing | Bit-Level Programming

\<div align="center">

\<img src="[https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=22&pause=1000&color=00E5A8&center=true&vCenter=true&width=850&lines=Hide+Secret+Messages+Inside+Images;LSB+Based+Steganography+Using+C;Binary+Data+%7C+Pixel+Manipulation;BMP+Image+Processing;Encoding+%26+Decoding+Engine](https://readme-typing-svg.demolab.com?font=Fira+Code\&weight=700\&size=22\&pause=1000\&color=00E5A8\&center=true\&vCenter=true\&width=850\&lines=Hide+Secret+Messages+Inside+Images;LSB+Based+Steganography+Using+C;Binary+Data+%7C+Pixel+Manipulation;BMP+Image+Processing;Encoding+%26+Decoding+Engine)" alt="Animated Image Steganography heading"/>

\<br/>

\<img src="[https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c](https://img.shields.io/badge/Language-C-00599C?style=for-the-badge\&logo=c)"/> \<img src="[https://img.shields.io/badge/Technique-LSB%20Steganography-00A98F?style=for-the-badge](https://img.shields.io/badge/Technique-LSB%20Steganography-00A98F?style=for-the-badge)"/> \<img src="[https://img.shields.io/badge/Image%20Format-BMP-3949AB?style=for-the-badge](https://img.shields.io/badge/Image%20Format-BMP-3949AB?style=for-the-badge)"/> \<img src="[https://img.shields.io/badge/Concept-Bit%20Manipulation-orange?style=for-the-badge](https://img.shields.io/badge/Concept-Bit%20Manipulation-orange?style=for-the-badge)"/>

**PURUSHOTHAMA K | EMBEDDED SOFTWARE ENGINEER ASPIRANT**

\</div>

---

## `01 / PROJECT OVERVIEW`

### Hiding Information Inside Digital Images

Image Steganography is a C programming project that demonstrates how secret information can be embedded inside a BMP image using the Least Significant Bit (LSB) technique.

Instead of visibly placing text over an image, the application modifies selected least significant bits of pixel data to store a secret message.

The modified image is called a **Stego Image**. The hidden information can later be extracted through a decoding process.

**Engineering objective:** Understand bit-level data manipulation, binary representation, BMP file structure, file handling and encoding/decoding logic using C.

---

## `02 / PROJECT ARCHITECTURE`

### Encoding and Decoding System

```text
          ENCODING PROCESS
          ────────────────

      ┌───────────────────┐
      │   SOURCE IMAGE    │
      │     BMP FILE      │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │  SECRET MESSAGE   │
      │     INPUT FILE    │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │  MESSAGE TO BITS  │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │   LSB ENCODING    │
      │                   │
      │ Pixel Manipulation│
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │    STEGO IMAGE    │
      │   OUTPUT BMP      │
      └───────────────────┘


          DECODING PROCESS
          ────────────────

      ┌───────────────────┐
      │    STEGO IMAGE    │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │  LSB EXTRACTION   │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │ SIGNATURE CHECK   │
      │   MAGIC STRING    │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │  BITS TO MESSAGE  │
      └─────────┬─────────┘
                |
                ▼
      ┌───────────────────┐
      │ RECOVERED MESSAGE │
      └───────────────────┘
```

---

## `03 / ENCODING PROCESS`

### How Secret Data Is Embedded

**STEP 01 — SOURCE IMAGE**

The program opens the original BMP image and prepares it for data embedding.

**STEP 02 — IMAGE HEADER HANDLING**

The BMP header is preserved so the output file retains its image structure.

**STEP 03 — SECRET MESSAGE**

The application reads the message from the input file.

**STEP 04 — MAGIC STRING**

A predefined identification signature is embedded to help identify the presence of encoded data during decoding.

**STEP 05 — BINARY CONVERSION**

Message characters are processed as binary data.

**STEP 06 — LSB MANIPULATION**

The least significant bits of selected pixel bytes are modified to carry the secret message.

**STEP 07 — OUTPUT GENERATION**

The modified image data is written into a new BMP file.

---

## `04 / DECODING PROCESS`

### Recovering the Hidden Information

**STEP 01 — INPUT STEGO IMAGE**

Open the previously encoded BMP image.

**STEP 02 — HEADER HANDLING**

Process the image header according to the BMP structure and implementation.

**STEP 03 — MAGIC STRING VERIFICATION**

Extract and verify the identification signature.

**STEP 04 — BIT EXTRACTION**

Read the least significant bits from the encoded pixel data.

**STEP 05 — CHARACTER RECONSTRUCTION**

Combine the extracted bits to reconstruct the original message characters.

**STEP 06 — OUTPUT MESSAGE**

Write the recovered secret information into the output file.

---

## `05 / UNDERSTANDING LSB TECHNIQUE`

### Least Significant Bit Manipulation

LSB steganography uses the last bit of a binary value to store hidden information.

Example:

```text
Original pixel byte:

10110110

Secret message bit:

       1

Modified pixel byte:

10110111
```

The least significant bit is modified while the other bits remain unchanged.

### C Programming Logic

```c
pixel = (pixel & 0xFE) | message_bit;
```

The operation clears the last bit and inserts the required message bit.

For extraction:

```c
message_bit = pixel & 0x01;
```

This retrieves the least significant bit.

---

## `06 / BMP IMAGE STRUCTURE`

### Understanding Image Data at Byte Level

BMP files contain a file header, a DIB header and pixel data.

For the common 24-bit BMP format with a 40-byte BITMAPINFOHEADER, the combined standard header size is 54 bytes.

```text
       BMP FILE STRUCTURE

┌─────────────────────────┐
│     FILE HEADER         │
│       14 BYTES          │
├─────────────────────────┤
│      DIB HEADER         │
│       40 BYTES          │
├─────────────────────────┤
│                         │
│      PIXEL DATA         │
│                         │
│    RGB COLOR VALUES     │
│                         │
└─────────────────────────┘
```

The pixel data contains the color information that the LSB technique uses for hiding information.

*The 54-byte layout applies to the specified common BMP header configuration; other BMP variants can have different layouts.*

---

## `07 / TECHNICAL CONCEPTS`

| Concept               | Application                             |
| --------------------- | --------------------------------------- |
| Bit Manipulation      | Modifying LSB values                    |
| Binary Representation | Processing secret message bits          |
| File Handling         | Reading and writing image/message files |
| BMP Structure         | Understanding image headers             |
| Structures            | Organizing file-related data            |
| Pointers              | Accessing and processing byte data      |
| Encoding              | Hiding secret information               |
| Decoding              | Extracting hidden information           |

---

## `08 / DEVELOPMENT ENVIRONMENT`

| Category                | Technology                |
| ----------------------- | ------------------------- |
| Programming Language    | C                         |
| Image Format            | BMP                       |
| Technique               | Least Significant Bit     |
| Development Environment | Linux / WSL               |
| Compiler                | GCC                       |
| Programming Domain      | Low-Level Data Processing |

---

## `09 / PROJECT STRUCTURE`

```text
Image-Steganography-in-C/
│
├── src/
│   ├── main.c
│   ├── encode.c
│   ├── decode.c
│   └── types.h
│
├── include/
│   └── common.h
│
├── README.md
└── .gitignore
```

*Illustrative structure. Replace it with the actual filenames and folders from your project.*

---

## `10 / BUILD AND EXECUTION`

### Prerequisites

- Linux or WSL environment
- GCC compiler
- BMP source image
- Secret message file

### Compilation

Use the actual source filenames from the project.

```bash
gcc *.c -o steganography
```

### Execution

```bash
./steganography
```

Follow the application's prompts to select the encoding or decoding operation and provide the required files.

---

## `11 / ENGINEERING SKILLS DEVELOPED`

- C programming.
- Bitwise operators and binary processing.
- File input and output.
- BMP image structure understanding.
- Pointer-based data manipulation.
- Encoding and decoding algorithms.
- Low-level data processing.
- Debugging and modular programming.

---

## `12 / FUTURE ENHANCEMENTS`

- [ ] Support additional image formats.
- [ ] Improve input validation.
- [ ] Add image capacity verification.
- [ ] Improve error handling.
- [ ] Add encryption before embedding.
- [ ] Implement more robust image integrity checks.

---

## `13 / ABOUT THE DEVELOPER`

\<div align="center">

### PURUSHOTHAMA K

**Embedded C | Bit Manipulation | Linux Programming**

Electrical and Electronics Engineering Graduate

Interested in Embedded Systems, Firmware Development, Linux System Programming and Low-Level Data Processing.



\</div>

---

\<div align="center">

### THINK IN BITS. PROCESS PIXELS. HIDE INFORMATION.

**DESIGN | DEVELOP | DEBUG**

\</div>
