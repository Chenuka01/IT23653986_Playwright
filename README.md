# Playwright Test Automation for Chat Translator

This repository contains the test automation project for the Chat Translator system (Singlish to Sinhala).

## Project Structure
- `IT23653986_test_automation.py`: The main Python script using Playwright for browser automation.
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
Open PowerShell and go to the project folder first:
```powershell
cd D:\test_automation-IT23653986\IT23653986
```

Then execute the automation script with the existing test cases:
```powershell
python .\IT23653986_test_automation.py --excel "D:\test_automation-IT23653986\IT23653986\IT23653986 - Assignment 1 - Test cases.xlsx" --sheet " Test cases" --header-row 1 --input-col "Input" --expected-col "Expected output" --actual-col "Actual output" --status-col "Status" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 10000 --retry-wait-ms 1500 --retries 10 --type-delay-ms 80 --slow-mo-ms 300 --save-every 1 --keep-open
```

Use the full Excel path shown above to avoid file-not-found errors caused by running the command from a different folder.

The column options are important:
- `--input-col "Input"` uses the Singlish sentence that must be typed into the website.
- `--expected-col "Expected output"` reads the expected Sinhala output.
- `--actual-col "Actual output"` writes the generated result back to Excel.
- `--status-col "Status"` writes PASS or FAIL.

Do not use `Singlish input types covered` as the input column. Values such as `Requests` are test categories, not the actual Singlish input text.

## Configuration Parameters
- `--excel`: Path to the Excel file containing test cases.
- `--sheet`: Excel sheet name. The provided workbook uses `" Test cases"` with a leading space.
- `--header-row`: Header row number. Use `1` for the provided workbook.
- `--input-col`: Excel column containing the Singlish input text. Use `"Input"`.
- `--expected-col`: Excel column containing the expected Sinhala output. Use `"Expected output"`.
- `--actual-col`: Excel column where the actual result is saved. Use `"Actual output"`.
- `--status-col`: Excel column where PASS or FAIL is saved. Use `"Status"`.
- `--url`: The website URL to test.
- `--wait-ms`: Initial wait time for the translation to appear.
- `--retry-wait-ms`: Time to wait between retries if output hasn't updated.
- `--retries`: Number of times to check for an output update.
- `--type-delay-ms`: Delay between typing each character.
- `--slow-mo-ms`: Slows down Playwright operations (useful for visual debugging).
- `--save-every`: Saves the workbook after every N rows. Use `1` to save after each test case.
- `--keep-open`: Keeps the browser open after the run for checking/debugging.

## Common Errors

### Python cannot open the script file
If you see:
```text
can't open file 'D:\test_automation-IT23653986\IT23653986_test_automation.py'
```

You are running the command from the parent folder without including the `IT23653986` subfolder. Run:
```powershell
cd D:\test_automation-IT23653986\IT23653986
```

Then run the command from the Run the Tests section.

### Excel file not found
If you see:
```text
Error: File 'D:\test_automation-IT23653986\IT23653986 - Assignment 1 - Test cases.xlsx' not found.
```

Use the full Excel path:
```powershell
--excel "D:\test_automation-IT23653986\IT23653986\IT23653986 - Assignment 1 - Test cases.xlsx"
```

### The script reads `Requests` instead of the Singlish sentence
`Requests` belongs to the `Singlish input types covered` column. The real input text is in the `Input` column.

Fix it by running with:
```powershell
--header-row 1 --input-col "Input"
```
