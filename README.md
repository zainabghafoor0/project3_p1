# Huffman Coding - Part 1: Scanner/Tokenizer

**Name:** Zainab Ghafoor  
**ID:** 008259427  
**GitHub repository link:** [[https://github.com/zainabghafoor0/project3_p1.git](https://github.com/zainabghafoor0/project3_p1.git)]

## Project Description

This repository implements a **text tokenizer (Scanner)** for Part 1 of the Huffman Coding project. The scanner reads `.txt` files and extracts words according to specific tokenization rules. **Valid tokens** are sequences of letters (a-z, A-Z) with optional internal apostrophes, all converted to lowercase. **Separators** include digits, punctuation, hyphens/dashes, whitespace, and non-ASCII characters. The output is written one token per line to `input_output/<basename>.tokens`.

## Collaboration & Sources

* **Work:** All code in `Scanner.cpp` written and tested independently. Minor modifications in `main.cpp` file
* **Starter Code:** `main.cpp`, `utils.cpp/.hpp`

## Implementation Details

### Key Components

**Scanner Class** (`Scanner.cpp/.hpp`):
- `Scanner(path)` - Constructor stores input file path
- `tokenize(vector<string>&)` - Tokenizes file into memory vector
- `readWord(istream&)` - Static method implementing tokenization rules
  - Skips non-letter characters until a letter is found
  - Builds words from letters (a-z, A-Z) converted to lowercase
  - Includes apostrophes only if followed by another letter (internal apostrophes)
  - Stops at any separator character

**Tokenization Rules**:
- Valid: `"don't"` → `don't`, `"Poe's"` → `poe's`
- Separators exclude: `"bells—"` → `bells`, `"bells,"` → `bells`
- Case normalized: `"Edgar"` → `edgar`

### Files
- `Scanner.cpp/.hpp` - Tokenizer implementation
- `main.cpp` - Program entry point (fixed bug on line 32)
- `utils.cpp/.hpp` - File validation and error handling utilities
- `input_output/` - Directory for input `.txt` files and output `.tokens` files

## How to Run

### Compilation

```bash
g++ -std=c++20 -Wall *.cpp -o huffman_part1
```

### Execution

```bash
./huffman_part1 input_output/TheBells.txt
```

Or with any other input file:

```bash
./huffman_part1 input_output/call_of_the_wild.txt
```
### Show output:
```bash
cat input_output/TheBells.tokens
```
For input call_of_the_wild.txt file:

```bash
./huffman_part1 input_output/call_of_the_wild.tokens
```

## Sample Input and Output

**Input:** `input_output/TheBells.txt` (excerpt)
```
Edgar Allan Poe's "The Bells":

Hear the sledges with the bells—
Silver bells!
What a world of merriment their melody foretells!
```

**Output:** `input_output/TheBells.tokens` (excerpt)
```
edgar
allan
poe's
the
bells
hear
the
sledges
with
the
bells
silver
bells
what
a
world
of
merriment
their
melody
foretells
```

**Manual comparison:**

```bash
diff -u input_output/call_of_the_wild.tokens /home/faculty/kooshesh/cs315_f2025_p3_part1/part1_tokens_files/call_of_the_wild.tokens
```
**Manual comparison Output Succeeded**
