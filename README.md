# Password Security Auditor

A lightweight browser-based utility for evaluating password strength and checking whether a password has appeared in known data breaches using the Have I Been Pwned (HIBP) k-anonymity API.

## Overview

This project analyzes a password in real time and provides:

- Shannon entropy estimation in bits
- Visual strength classification
- Estimated offline crack time based on a 10 billion guesses/second model
- HIBP breach detection using a privacy-preserving k-anonymity approach

The app runs entirely in the browser and does not send the full password to the HIBP service. Instead, it hashes the password locally with SHA-1, sends only the first 5 characters of the hash prefix, and checks the returned suffix against the HIBP range API.

## Features

- Password visibility toggle
- Real-time strength meter
- Entropy scoring and rating
- Offline crack-time estimate
- Breach lookup using HIBP k-anonymity
- No backend or server required

## How it works

1. The user enters a password.
2. The app calculates character pool size and Shannon entropy:
   - lowercase letters
   - uppercase letters
   - digits
   - symbols
3. The entropy result is converted into a strength rating and crack-time estimate.
4. When the user clicks "Check Breach", the app:
   - computes a SHA-1 hash locally in the browser
   - sends only the first 5 hash characters to the HIBP API
   - compares the result to the known breach suffix list
   - reports whether the password appears in breached data

## Run locally

Because this is a single-page static site, you can run it in either of these ways:

### Option 1: Open directly in a browser

- Open `index.html` directly in your browser.

### Option 2: Serve locally

From the project folder, run:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

## Privacy and security notes

- The password itself is never transmitted to HIBP.
- Only the first 5 characters of the SHA-1 hash prefix are sent.
- The app uses browser-native Web Crypto APIs for hashing.
- This tool is intended for educational and personal-security awareness purposes.

## Project structure

```text
.
├── index.html
├── README.md
```

## License

This project is provided as-is for educational and security-focused use.
