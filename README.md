# Week 3: Password Cracking with Networkwalks Tools & John the Ripper

## Overview
A hands-on password-recovery project carried out on test PDFs created for the lab. It covers cracking 4 encrypted PDFs using Networkwalks' own hash extraction and cracking tools, plus cracking 1 PDF using John the Ripper (via its Johnny GUI).

| Module | Topic |
|--------|-------|
| **W3-PM1** | Password cracking with Networkwalks tools |
| **W3-PM2** | Password cracking with John the Ripper |

## Why This Matters
- **Understanding attacker capability:** Shows how quickly weak or common passwords can be recovered once a hash is obtained.
- **Hash extraction fundamentals:** Demonstrates how tools like `pdf2john` convert a protected file into a crackable hash format.
- **Dictionary attacks in practice:** Reinforces why common passwords (`password1`, `1qaz2wsx`) are cracked almost instantly.
- **Tool familiarity:** John the Ripper is an industry-standard password-cracking tool used in both offensive and defensive security work.
- **Defender's takeaway:** Highlights why strong, unique passwords and encryption key lengths matter.

## Scope and Ethics
- All PDFs cracked were test files created for this lab exercise, not third-party documents.
- No real user data or production systems were involved.
- These techniques are for authorized, educational password-recovery practice only.

## Task 1: Password Cracking with Networkwalks Tools
**Workflow:** Upload PDF → Networkwalks hash extractor pulls a `pdf2john`/hashcat-compatible hash → Networkwalks cracking tool runs a dictionary attack against the hash → password revealed → PDF unlocked.

| PDF | Key Length | Attempts | Password Found |
|-----|-----------|----------|-----------------|
| Locked PDF 1 | 128-bit | 3456 / 3556 | `good-luck` |
| Locked PDF 2 | 128-bit | 15 / 3556 | `password1` |
| Locked PDF 3 | 128-bit | 15 / 3556 | `password1` |
| Locked PDF 4 | 128-bit | 2078 / 3556 | `1qaz2wsx` |

All 4 PDFs were successfully unlocked, two of which revealed capture-the-flag style confirmation flags.

## Task 2: Password Cracking with John the Ripper
**Workflow:** PDF hash extracted using an online PDF hash extractor → hash loaded into Johnny (GUI for John the Ripper) → dictionary attack run → password cracked.

| Tool | Format | Result |
|------|--------|--------|
| Johnny (John the Ripper) | PDF | 1/1 cracked (100%) → password: `password1` |

## Key Observations
- All passwords cracked were weak, short, or from common password lists, which is why dictionary attacks succeeded within seconds to minutes.
- A 128-bit RC4 PDF encryption key offers no real protection if the password itself is weak, since the attack targets the password, not the encryption algorithm.
- Networkwalks' tools and John the Ripper both rely on the same underlying principle: extract a hash, then test candidate passwords against it.

## Recommendations
1. Use long, random passphrases rather than common words or keyboard patterns for document protection.
2. Avoid reusing the same password across multiple protected files.
3. Where possible, use AES-256 encryption instead of RC4/128-bit for sensitive PDFs.
4. Combine document passwords with other access controls (e.g., restricted sharing, expiry) rather than relying on the password alone.

## Key Skills Demonstrated
Hash extraction, dictionary attacks, password cracking tools (Networkwalks tools, John the Ripper / Johnny), encryption key analysis, and security awareness around password strength.

## Disclaimer
This project is for educational purposes only, using self-created test files. Only attempt password recovery on files you own or have explicit permission to test.

