# Project Reflection

## What I Built

A structured prompt that turns Claude into a phishing analyst, paired with a small test suite of mock emails to evaluate prompt consistency and depth of analysis.

## Applying the AI Fluency Framework

**Delegation** — I designed the prompt to handle pattern recognition (urgency cues, suspicious domains, generic greetings) while explicitly noting where human verification is required (actual sender headers, link inspection in a sandbox, organizational context).

**Description** — Writing the prompt forced me to articulate exactly what phishing looks like. Translating tacit knowledge into a Low/Medium/High rubric was harder than expected and revealed gaps in my own mental model.

**Discernment** — The first test case (legitimate coworker email) was deliberately included to check for false positives. A prompt that flags benign messages is worse than no prompt at all in a real SOC environment.

**Diligence** — I tested against three distinct scenarios rather than just confirming the prompt works on obvious phishing. I also documented limitations honestly rather than overselling capability.

## What Worked

- The structured 8-section output made analyses easy to compare across runs
- The explicit false-positive guard prevented over-flagging on the legitimate test case
- Separating "Risk Level" from "Confidence Level" produced more nuanced output

## Limitations

- The prompt only analyzes message body text. It cannot inspect actual email headers, sender authentication (SPF/DKIM/DMARC), or attachment payloads.
- Test cases are AI-generated, not real-world samples. Real phishing campaigns include obfuscation tactics (zero-width characters, image-based text, lookalike Unicode) that a body-only prompt can't catch.
- A determined attacker writing a targeted spear-phishing email could potentially produce a message that passes this rubric.

## What I'd Add Next

- Integration with email header analysis (SPF/DKIM/DMARC results)
- A larger test set including real sanitized phishing samples from public databases (APWG, PhishTank)
- A simple Python wrapper that takes an .eml file as input and returns a structured analysis
- Comparison testing across multiple models to evaluate consistency
