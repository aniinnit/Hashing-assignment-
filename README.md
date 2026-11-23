# Hashing-assignment-
Akpabio Aniekanabasi Tobechukwu 24/13680
# Hashing Demo (SHA-256)


A Python script that hashes a word, a sentence and a paragraph, then checks the results against the five characteristics of hashing.

## Requirements

- Python 3.6 or newer
- No extra packages (uses the built-in `hashlib` module)

## How to run

```bash
python hashing_demo.py
```

## What the script does

1. Hashes a **word** (`cybersecurity`)
2. Hashes a **sentence** (`Hashing is a one-way function used to protect data integrity.`)
3. Hashes a **paragraph** of 5 lines
4. Demonstrates each characteristic of hashing

## Sample output

| Input | SHA-256 digest |
|---|---|
| Word | `64a1e1972b663b35a8c06b453ce018251efef00925fb414217f6087f179031b8` |
| Sentence | `38572a38ce94ed4f1298966d4f595207c88a997f49cfef75bf93438e388b2d45` |
| Paragraph | `c0b334c19e3029524441e23454854cbb007e202cd4f7e9a10937d8db2ac3cf73` |

## Comparison with the characteristics of hashing

| # | Characteristic | Result in this demo |
|---|---|---|
| 1 | Fixed length digest | Inputs of 13, 61 and 275 characters all produced a 64-character hex digest (256 bits). |
| 2 | Same input gives same digest | Hashing `cybersecurity` twice gave identical output. |
| 3 | Small change gives a very different digest | Adding one full stop changed 124 of 256 bits (48%). This is the avalanche effect. |
| 4 | Hard to reverse | `hashlib` has no unhash function. Only guessing inputs (brute force or dictionary attack) works, and it is practical only for tiny, guessable inputs. |
| 5 | Collisions are theoretically possible | SHA-256 has no known collisions, so the demo truncates the hash to 2 hex characters. `message20` and `message31` collided after 32 tries. |

## Notes

- SHA-256 is used because it is secure and widely used. MD5 and SHA-1 are considered broken because practical collisions have been found.
- To try another algorithm, change `hashlib.sha256` in the `sha256_hash` function (for example `hashlib.md5` or `hashlib.sha1`). The digest length will change, which still follows characteristic 1: fixed length *for a given algorithm*.
- For storing passwords in real systems, use a salted, slow hash such as bcrypt, scrypt or Argon2 instead of plain SHA-256.
