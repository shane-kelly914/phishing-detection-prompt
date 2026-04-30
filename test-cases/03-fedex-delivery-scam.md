# Test Case 03: FedEx Delivery Scam

**Expected Risk Level:** High
**Scenario:** Brand impersonation phishing using a fraudulent FedEx-lookalike domain

## Email

> Subject: Package Delivery Notification
>
> Hello,
>
> We attempted to deliver your package today but were unable to complete delivery due to an address issue.
>
> Please confirm your shipping details here: https://fedex-delivery-update-help.net/track
> Your package will be returned to sender if not updated within 48 hours.
>
> Thank you, FedEx Delivery Team

## Why This Test Matters

Tests detection of brand impersonation and lookalike domains — one of the most common real-world phishing patterns. Also tests whether the prompt notices missing details (no tracking number, no specific package info).
