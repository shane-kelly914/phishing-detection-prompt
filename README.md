# Phishing Detection Prompt

A structured prompt that turns Claude into a phishing analyst, built as an applied project after completing Anthropic's [AI Fluency: Framework & Foundations](https://www.anthropic.com/ai-fluency) course.

## Overview

This project explores how careful prompt design can produce consistent, useful security analysis from a general-purpose language model. The prompt evaluates emails against a defined risk rubric and produces a structured 8-section breakdown including red flags, legitimate signals, and recommended action.

## Project Structure

```
├── prompt/                  # The system prompt and design notes
├── test-cases/              # Mock phishing and legitimate emails
├── results/                 # Claude's analysis of each test case
└── reflection.md            # Lessons learned and AI Fluency framework application
```

## Test Results

| # | Scenario | Expected | Actual | Match |
|---|----------|----------|--------|-------|
| 01 | Internal coworker request | Low | Low | ✓ |
| 02 | Fake security alert | High | High | ✓ |
| 03 | FedEx delivery scam | High | High | ✓ |

## Methodology

1. Designed a phishing-analyst prompt with an explicit Low/Medium/High rubric and structured output format
2. Generated mock emails using AI to cover legitimate, suspicious, and clearly malicious cases
3. Ran each email through the prompt and evaluated the output for accuracy, depth, and false-positive control
4. Documented limitations and improvement areas

## Key Design Choices

- **Defined rubric** reduces inconsistent judgments across runs
- **Structured 8-section output** makes results comparable across emails
- **Explicit false-positive guard** prevents over-flagging routine business communication
- **Confidence level** is separated from risk rating to acknowledge analysis limits

## Limitations

This prompt analyzes message body text only. It cannot inspect email headers, verify sender authentication, sandbox links, or scan attachments. It is a triage aid, not a replacement for proper email security infrastructure.

## Future Improvements

- Email header analysis (SPF/DKIM/DMARC integration)
- Real sanitized phishing samples from APWG/PhishTank
- Python wrapper for `.eml` file input
- Cross-model consistency testing

## About This Project

Built as a hands-on application of Anthropic's AI Fluency framework — specifically the four practices of Delegation, Description, Discernment, and Diligence. See [`reflection.md`](./reflection.md) for details.

## License

MIT
