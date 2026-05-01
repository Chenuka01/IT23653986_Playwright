# Playwright Test Automation for Chat Translator

This repository contains the test automation project for the Chat Translator system (Singlish to Sinhala).

## Project Structure
- `test_automation.py`: The main Python script using Playwright for browser automation.
- `IT23653986 - Assignment 1 - Test cases.xlsx`: Excel file containing the fifty negative test cases and results.

## Setup Instructions

### 1. Prerequisites
Ensure you have Python 3.8+ installed on your system.

### 2. Install Dependencies
Run the following commands in your terminal:
```bash
pip install -U pip
pip install playwright openpyxl
playwright install
```

### 3. Run the Tests
To execute the automation script with the existing test cases:
```bash
python test_automation.py --excel "IT23653986 - Assignment 1 - Test cases.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 10000 --retry-wait-ms 1500 --retries 10 --type-delay-ms 80 --slow-mo-ms 300 --save-every 1 --keep-open
```

## Configuration Parameters
- `--excel`: Path to the Excel file containing test cases.
- `--url`: The website URL to test.
- `--wait-ms`: Initial wait time for the translation to appear.
- `--retry-wait-ms`: Time to wait between retries if output hasn't updated.
- `--retries`: Number of times to check for an output update.
- `--type-delay-ms`: Delay between typing each character.
- `--slow-mo-ms`: Slows down Playwright operations (useful for visual debugging).
