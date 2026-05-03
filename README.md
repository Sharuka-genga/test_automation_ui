# Image Preview Test – Playwright Automation

## Overview
This project automates a test scenario that verifies the **image preview functionality** of the **Image Format Conversion** feature on [pixelssuite.com](https://www.pixelssuite.com/convert-to-png). It uploads a PNG image and checks whether a preview appears on the page. Results are recorded in `execution_results.csv`.

---

## Prerequisites

- Python 3.11 or 3.12 ([download](https://www.python.org/downloads/))
- Google Chrome (recommended) or Playwright will install Chromium automatically

---

## Setup Instructions

### 1. Clone or extract the project

```bash
cd D:\
# If using git:
git clone <your-repo-url> test_automation_ui
cd test_automation_ui

# OR extract the ZIP and navigate:
cd /d D:\test_automation_ui
```

### 2. Install dependencies (one-time)

```bash
pip install -U pip
pip install playwright openpyxl
playwright install
```

---

## Running the Test

From inside the `test_automation_ui` folder:

```bash
python image_preview_test.py --url "https://www.pixelssuite.com/convert-to-png" --slow-mo-ms 2000
```

### Optional arguments

| Argument | Default | Description |
|---|---|---|
| `--url` | see code | Target page URL |
| `--png` | `sample.png` | PNG file to upload |
| `--out-dir` | `results` | Folder for screenshots |
| `--csv` | `execution_results.csv` | Output CSV file |
| `--headless` | False | Run browser in headless mode |
| `--timeout-ms` | 60000 | Max wait time in ms |
| `--slow-mo-ms` | 0 | Slow down actions (ms) |

---

## Checking Results

After the run:

1. Open `execution_results.csv` – it should contain **one data row** with `status = PASS` if the preview was detected.
2. Open the `results/` folder – a screenshot named `preview_pass.png` or `preview_fail.png` will be present.

---

## Project Structure

```
test_automation_ui/
├── image_preview_test.py   # Main Playwright test script
├── execution_results.csv   # Auto-generated test results
├── sample.png              # Default test image (auto-created if missing)
├── README.md               # This file
└── results/                # Screenshots from test runs
    └── preview_pass.png
```

---

## Troubleshooting

- **FileNotFoundError for sample.png**: The script auto-creates a 1×1 PNG if `sample.png` is missing. You can supply your own: `--png path/to/image.png`
- **Browser not found**: Run `playwright install chromium`
- **Timeout errors**: Increase `--timeout-ms` (e.g., `--timeout-ms 90000`) on slow connections
