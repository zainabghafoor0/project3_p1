# Huffman Coding - Part 1: Scanner/Tokenizer

**Name:** Zainab Ghafoor  
**ID:** 008259427  
**GitHub repository link:** [[https://github.com/zainabghafoor0/project3_p1.git](https://github.com/zainabghafoor0/project3_p1.git)]

## Project Description

This repository implements a **text tokenizer (Scanner)** for Part 1 of the Huffman Coding project. The scanner reads `.txt` files and extracts words according to specific tokenization rules. **Valid tokens** are sequences of letters (a-z, A-Z) with optional internal apostrophes, all converted to lowercase. **Separators** include digits, punctuation, hyphens/dashes, whitespace, and non-ASCII characters. The output is written one token per line to `input_output/<basename>.tokens`.

## Collaboration & Sources

* **Work:** All code in `Scanner.cpp` written and tested independently. Also, few modification in `main.cpp`
* **Starter Code:** `main.cpp`, `utils.cpp/.hpp` provided by instructor (Professor Kooshesh)
* **Bug Fix:** Corrected `main.cpp` line 32 to pass input file path instead of output file path to Scanner constructor

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

**Note:** Input files must be in the `input_output/` directory. Pass only the filename, not the full path.

### Testing on Blue

**One-time setup:**

```bash
# Copy test scripts
cp /home/faculty/kooshesh/cs315_f2025_p3_part1/compile_and_test.bash .
cp /home/faculty/kooshesh/cs315_f2025_p3_part1/copy_files.bash .

# Copy sample input files to input_output/
bash copy_files.bash
```

**Run automated test:**

```bash
bash compile_and_test.bash TheBells.txt
```

This compiles, runs, and compares output against reference files in:  
`/home/faculty/kooshesh/cs315_f2025_p3_part1/part1_tokens_files/`

**Manual comparison:**

```bash
diff -u input_output/TheBells.tokens /home/faculty/kooshesh/cs315_f2025_p3_part1/part1_tokens_files/TheBells.tokens
```

## Sample Output

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

## Testing Results

Tested successfully with sample files on blue:
- `TheBells.txt` - ✓ Passed
- `call_of_the_wild.txt` - ✓ Passed
- All outputs match reference `.tokens` files

No compilation warnings with `-Wall` flag.

---

**Course:** CS 315 - Fall 2025  
**Instructor:** Professor Ali Kooshesh  
**Assignment:** Project 3, Part 1
