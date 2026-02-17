# Lab 3: Data Loss Prevention (DLP)

## Introduction
Protect sensitive data from being uploaded to AI services.

## Steps
1. Navigate to **DLP** -> **Profiles**.
2. Enable built-in profiles (e.g., Credit Card numbers, SSN).
3. Create a Custom Profile for company-specific secrets (e.g., API keys).
4. Create a Gateway HTTP policy to "Block" uploads matching these profiles to AI domains.

## Verification
- Try to paste a fake credit card number into an AI chat.
- The request should be blocked by the Gateway.
