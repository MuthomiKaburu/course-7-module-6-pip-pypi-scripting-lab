# 🛠️ Automation Tool: Log Generator

## 📌 Overview

This project is a **modular Python automation tool** that generates log files from structured input data. It demonstrates the use of:

* Python scripting
* File I/O operations
* Input validation
* External package integration
* Reproducible environments using `requirements.txt`
* Test-driven development using `pytest`

The tool is designed to be executed from the command line and produces a timestamped log file.

---

## 🎯 Objectives

The goal of this project is to:

* Build a reusable Python script that processes and logs data
* Use third-party packages (e.g., `requests`)
* Ensure code is modular and testable
* Output structured results to a file
* Maintain reproducibility with dependency tracking

---

## ⚙️ Features

* ✅ Generates log files with date-based filenames
* ✅ Validates input before processing
* ✅ Raises appropriate errors for invalid data
* ✅ Writes structured entries to a `.txt` file
* ✅ Supports empty input (creates an empty log file)
* ✅ Fully compatible with automated tests (`pytest`)
* ✅ Can be executed directly from the command line

---

## 🧱 Project Structure

```
course-7-module-6-pip-pypi-scripting-lab/
│
├── generate_log.py          # Main script
├── requirements.txt         # Project dependencies
├── test_generate_log.py     # Unit tests
└── log_YYYYMMDD.txt         # Generated output file
```

---

## 🧪 Functionality Breakdown

### `generate_log(data)`

This is the core function responsible for:

1. **Input Validation**

   * Ensures `data` is a list
   * Raises `ValueError` if invalid

2. **Filename Generation**

   * Uses current date:

     ```
     log_YYYYMMDD.txt
     ```

3. **File Writing**

   * Writes each entry in the list to a new line

4. **Return Value**

   * Returns the filename (critical for testing)

---

## 💻 Code Implementation

```python
from datetime import datetime
import os

def generate_log(data):
    if not isinstance(data, list):
        raise ValueError("Data must be a list")

    filename = f"log_{datetime.now().strftime('%Y%m%d')}.txt"

    with open(filename, "w") as file:
        for entry in data:
            file.write(f"{entry}\n")

    print(f"Log written to {filename}")
    return filename
```

---

## 📦 Installation & Setup

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd course-7-module-6-pip-pypi-scripting-lab
```

---

### 2. Create and activate virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

---

### 3. Install dependencies

```bash
pip install requests
```

---

### 4. Save dependencies

```bash
pip freeze > requirements.txt
```

---

## ▶️ Running the Script

```bash
python generate_log.py
```

---

## 📄 Example Output

### Terminal Output

```
Log written to log_20260323.txt
```

### Generated File Content

```
Entry one
Entry two
Entry three
```

---

## 🧪 Running Tests

This project uses `pytest` for testing.

```bash
pytest test_generate_log.py
```

### ✔️ What is tested

* File is created successfully
* Filename format is correct
* File content matches input
* Errors are raised for invalid input
* Empty list creates an empty file

---

## ⚠️ Error Handling

| Scenario            | Behavior                   |
| ------------------- | -------------------------- |
| Input is not a list | Raises `ValueError`        |
| Empty list          | Creates empty file         |
| File write failure  | Python exception is raised |

---

## 🔁 Reproducibility

Dependencies are tracked in:

```
requirements.txt
```

To reinstall:

```bash
pip install -r requirements.txt
```

---

## 🚀 Future Improvements

* Add CSV export support
* Add logging levels (INFO, ERROR)
* Add CLI arguments (`argparse`)
* Integrate more APIs for dynamic log data

---

## 👨‍💻 Author

**Muthomi Kaburu**

---

## 📜 License

This project is for educational purposes (Moringa School Lab).
