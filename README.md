# 🤖 QABrain-Ai-Bot 

**Bot Username:** @QABrain_Bot

QA Brain is an AI-powered Telegram bot built using **n8n + OpenAI** that helps users with QA testing and cybersecurity learning in a simple command-based interface.

---

## 🚀 Features

### 🔹 /start

Welcomes the user and introduces the bot.

* Provides a quick overview of what the bot does
* Guides user to use `/help` command

---

### 🔹 /help

Displays all available commands with examples.

Includes:

* `/bugreport`
* `/testcases`
* `/new`

Also helps users understand how to properly use each command.

---

### 🔹 /bugreport

Convert raw bug descriptions into a **professional QA bug report (HTML format)**

**Example:**

```
/bugreport Login page crashes on invalid password
```

**Output Includes:**

* Bug Title
* Steps to Reproduce
* Expected Result
* Actual Result
* Severity / Priority

---

### 🔹 /testcases

Generate structured test cases from given features or inputs.

**Example:**

```
/testcases Login page email field, password field, login button, forgot password link
```

**Output Includes:**

* Test Case ID
* Steps
* Expected Results
* Multiple scenarios

---

### 🔹 /new

Get a random cybersecurity vulnerability.

**Output Includes:**

* Vulnerability Name
* Explanation
* Technical Working
* Safe Practical Demo (lab-based only)
* Prevention Methods
* Tools
* Learning Resources
* Practice Labs

---

## 🧠 Input Validation & Handling

The bot ensures users provide meaningful input before processing.

### ❌ Empty Input Handling

If user sends commands without proper input:

**Example:**

```
/testcases
```

**Response:**

```
❌ Please provide features or fields to generate test cases.

📌 Example:
/testcases Login page email field, password field
```

---

**Example:**

```
/bugreport
```

**Response:**

```
❌ Please describe the bug properly.

📌 Example:
/bugreport Login page crashes on invalid password
```

---

### ✅ Validation Logic

* Input is trimmed and checked
* Minimum input length ensured
* Commands are validated before processing
* Only valid inputs are sent to AI

---

## ⚙️ Execution Flow & User Experience

### ⏳ Processing Indicator

When a user sends a command:

* The bot first sends a **"Generating..."** message

**Purpose:**

* Inform user that request is being processed
* Handle delay caused by AI response time

---

### 🤖 AI Processing

* OpenAI processes the request
* Generates structured output based on the command

---

### ✅ Final Response

After processing:

* Final result is sent to the user
* For file-based outputs, a confirmation message is also sent:

```
Your Test Case File has been generated successfully!
Thank you for using QABrain AI 🚀
```

---

## ⚙️ Workflow Overview (n8n)

The bot is built using a structured n8n workflow:

### 🔹 Telegram Trigger

* Captures incoming user messages
* Extracts chat_id and text

---

### 🔹 Switch Node

* Routes commands:

  * `/start`
  * `/help`
  * `/bugreport`
  * `/testcases`
  * `/new`

---

### 🔹 Edit Fields (Set Node)

* Stores:

  * chat_id
  * user input text

---

### 🔹 IF Nodes (Validation)

* Checks:

  * Empty input
  * Valid command usage

* Routes:

  * ✅ Valid → AI
  * ❌ Invalid → Error message

---

### 🔹 OpenAI Node

* Generates:

  * Bug reports
  * Test cases
  * Cybersecurity content

---

### 🔹 Telegram Nodes

Used for:

* Sending "Generating..." message
* Sending final response
* Sending validation/error messages

---

### 🔹 File Conversion Node

* Converts output into file (HTML/Text)
* Sends file to user

---

## 🧪 Testing

The bot was tested with multiple scenarios:

### ✅ Functional Testing

* Valid `/bugreport` → proper QA report
* Valid `/testcases` → structured test cases
* `/new` → random vulnerability output

---

### ⚠️ Edge Case Testing

* Empty `/testcases` → handled correctly
* Empty `/bugreport` → handled correctly
* Invalid inputs → blocked and guided

---

## 📸 Outputs & Screenshots

All workflow screenshots, outputs, and test results are available in:

📁 **/Results**

---

## 🛠 Tech Stack

* n8n
* OpenAI API
* Telegram Bot API

---

## 📌 Notes

* Bug reports are generated in **HTML format**
* Cybersecurity content is **safe and ethical (lab-based only)**
* Designed for QA learning and automation

