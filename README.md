# KeePass 2 KDF Analysis Tool

This project is an **educational and defensive security tool** that analyzes the KeePass 2 key derivation and encryption process by testing candidate passwords against a KeePass database header.

The goal is **not to bypass encryption**, but to:

* Understand how KeePass derives encryption keys
* Measure how KDF parameters affect brute-force feasibility
* Demonstrate why strong passwords and sufficient transform rounds matter

The tool is intentionally limited to small password spaces (e.g. 4‑digit PINs or wordlists) for research and testing purposes.

---

## What This Tool Does

* Parses KeePass 2 database headers
* Reproduces the KeePass key derivation process:

  * AES-based transform rounds
  * SHA‑256 hashing
  * Optional PBKDF2‑HMAC‑SHA256 mode
* Attempts password candidates and validates them using encrypted stream start bytes
* Measures how many passwords can be tested per second

---

## Features

* KeePass 2 header parsing
* AES‑256 (ECB & CBC) encryption
* SHA‑256 hashing
* PBKDF2 (optional alternative mode)
* Wordlist or numeric PIN testing
* Performance measurement mode
* Controlled corruption test for research purposes

---

## Requirements

* Python 3.8+
* PyCryptodome

Install dependency:

```bash
pip install pycryptodome
```

---

## Usage

### Basic password test (default: 4‑digit PINs)

```bash
python3 keepass_kdf_analysis.py database.kdbx
```

### Use a wordlist

```bash
python3 keepass_kdf_analysis.py database.kdbx -w wordlist.txt
```

### Measure password attempts per second

```bash
python3 keepass_kdf_analysis.py database.kdbx -m 5
```

### Verbose output

```bash
python3 keepass_kdf_analysis.py database.kdbx -v
```

### Alternative PBKDF2 mode

```bash
python3 keepass_kdf_analysis.py database.kdbx -a
```

---

## Security & Ethics

This project is intended for:

* Educational use
* Cryptographic research

Only test databases you own or have explicit permission to analyze.

---

## Why This Matters

KeePass relies on strong cryptography, but password strength and KDF configuration determine real-world security.
This tool demonstrates how weak passwords can still be vulnerable — even with strong encryption.

---

## License

MIT License
