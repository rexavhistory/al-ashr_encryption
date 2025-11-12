# al-ashr_encryption
# CLASSICAL AL-ASHR CIPHER (TRUE POLYALPHABETIC ENCRYPTION)

This web application implements the Classical Al-Ashr Cipher, a time-based encryption method that ensures true polyalphabetic substitution. It works by mapping characters to a random second within a flexible, predefined time range.

## 1. KEY PRINCIPLE

The cipher converts each character into a **random time** (HH:MM:SS) that falls within a pre-defined time slot. Since one character can yield many different times, it effectively defeats simple frequency analysis.

## 2. KEY FEATURES

* **True Polyalphabetic:** Same character encrypts to different times.
* **Flexible Key Parameters:** User-defined Character Set, Range Duration (in seconds), and Start Time Offset.
* **Multi-language Support** (English/Indonesian).

## 3. REQUIRED PARAMETERS (THE KEYS)

All three parameters must be **identical** for both the sender and receiver to ensure correct decryption.

| PARAMETER | DESCRIPTION | EXAMPLE |
|---|---|---|
| **Character Set** | The exact list of all valid characters (A-Z, 0-9, symbols). | ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789 |
| **Range Duration** | The length of the time slot allocated to each character (in **SECONDS**). | 1500 (for 25 minutes) |
| **Start Time Offset** | The time added to the final cipher time (HH:MM:SS). | 07:00:00 |

## 4. ENCRYPTION/DECRYPTION FLOW

### ENCRYPTION:

1.  **Map to Base Range:** Character's position determines its base time range (starting from 0 seconds).
2.  **Random Selection:** A random second is chosen within that base range (P_AMT).
3.  **Apply Offset:** P_AMT is shifted by the **Start Time Offset** (HH:MM:SS) to produce the final Ciphertext time.

### DECRYPTION:

1.  **Remove Offset:** Ciphertext time is converted to seconds, and the **Start Time Offset** is subtracted (using modulo 86400) to recover the P_AMT (Base Second).
2.  **Find Index:** P_AMT is divided by the **Range Duration** to find the original character's index.
3.  **Recover Character:** The character at the recovered index from the **Character Set** is outputted.

## 5. USAGE GUIDE

1.  **Language:** Use the toggle button to select your language.
2.  **Set Keys:** Input the three matching parameters in the "Classical Parameters" section.
3.  **Encrypt:** Enter Plaintext, click the **ENCRYPT** button. Output will be a comma-separated list of times (HH:MM:SS).
4.  **Decrypt:** Copy the list of times into the Ciphertext box and click the **DECRYPT** button.

## NOTE ON SECURITY

This is a Classical Cipher. Its security relies entirely on keeping the three key parameters (Character Set, Duration, and Start Time) **secret** from unauthorized parties.
