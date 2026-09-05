# E-commerce Product Review System

A software quality engineering project focused on developing and testing a web-based **E-commerce Product Review System** using FastAPI. The project emphasizes backend development, automated testing, API validation, UI testing, continuous integration, and performance testing.

> **Project Type:** Academic Group Project
> **Team Size:** 2 members

---

## Overview

The E-commerce Product Review System provides a simple platform for managing products and submitting product reviews.

The project was developed with a strong focus on **Software Quality Engineering (SQE)** practices rather than only application development. Alongside the FastAPI application, the project includes multiple levels of automated testing, API validation, UI testing, continuous integration, and performance testing.

---

## Key Features

* Product listing and product-specific pages
* Product review submission
* RESTful API endpoints
* Server-rendered HTML pages using Jinja2
* Pydantic-based data models
* Automated unit and integration testing
* Selenium-based UI testing
* Postman API collection
* GitHub Actions CI workflow
* Performance testing with ApacheBench
* Automated HTML test reports
* JSON-based product data storage

---

## Technology Stack

### Backend

* Python
* FastAPI
* Uvicorn
* Pydantic
* Jinja2

### Testing & Quality Assurance

* pytest
* Selenium
* Chrome / ChromeDriver
* Postman
* ApacheBench

### DevOps & Automation

* GitHub Actions
* Bash scripting
* Automated test execution
* HTML test reporting

### Data Storage

* JSON

---

## Application Structure

The application provides both web pages and API endpoints.

### Web Interface

* Home page
* Product detail pages
* Product review submission

### API

The backend exposes endpoints for:

* Retrieving all products
* Retrieving individual products
* Managing product reviews

The API and web interface share the same backend application.

---

## Testing

Testing was a major component of the project, covering multiple levels of the application.

### Unit & Integration Testing

The project uses **pytest** for automated API and application testing.

```bash
pytest tests/test_api.py -q
```

### UI Testing

A Selenium-based test automates the process of submitting a product review through the web interface.

```bash
pytest tests/test_ui_selenium.py -q
```

The Selenium test requires Chrome and a compatible ChromeDriver installation.

### Test Reporting

The project can generate HTML test reports for easier inspection of test results.

```bash
PYTHONPATH=$(pwd) pytest -q --html=reports/report.html
```

---

## API Testing

A **Postman collection** is included for validating the application's API endpoints.

```text
postman_collection.json
```

The collection can be imported into Postman to execute and verify the available API operations.

---

## Continuous Integration

The repository includes a **GitHub Actions workflow** that automatically runs the test suite.

This demonstrates the use of automated quality checks as part of the development workflow.

```text
Code Change
     │
     ▼
GitHub Repository
     │
     ▼
GitHub Actions
     │
     ▼
Automated Tests
     │
     ▼
Test Results
```

---

## Performance Testing

The project also includes performance testing scripts using **ApacheBench (ab)**.

Performance test results are stored in the repository under:

```text
performance_reports/
```

The project therefore considers not only functional correctness but also application performance under request load.

---

## Software Quality Engineering Practices

The project demonstrates several practical SQE concepts:

* Unit testing
* Integration testing
* End-to-end UI testing
* API testing
* Automated testing
* Continuous integration
* Test reporting
* Performance testing
* Regression-oriented automated checks
* Quality assurance through multiple testing layers

---

## Repository Structure

```text
SQE-Ecommerce-Review-Project/
│
├── .github/
│   └── workflows/
│
├── app/
│
├── performance_reports/
│
├── test_reports/
│
├── tests/
│
├── Ecommerce_Product_Review_System_Documentation.docx
├── ci_run.sh
├── performance_tests.sh
├── postman_collection.json
├── products.json
├── requirements.txt
└── README.md
```

---

## Running Locally

### 1. Create a virtual environment

```bash
python -m venv .venv
```

Activate it:

**Linux/macOS**

```bash
source .venv/bin/activate
```

**Windows**

```bash
.venv\Scripts\activate
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Start the application

```bash
uvicorn app.main:app --reload --port 8000
```

The application will be available at:

```text
http://localhost:8000
```

---

## Project Documentation

The repository also contains the project documentation:

```text
Ecommerce_Product_Review_System_Documentation.docx
```

This document provides additional details about the system and project work.

---

## Team

This was a **two-member academic group project** developed as part of the Software Quality Engineering course.

The project provided practical experience in combining backend development with systematic software testing and quality assurance practices.

---

## Academic Context

**Course:** Software Quality Engineering (SQE)
**Project Type:** Group Academic Project
**Team Size:** 2 members
**Primary Focus:** Backend Development, Software Testing & Quality Assurance

---

## Learning Outcomes

Through this project, we gained practical experience with:

* Building REST APIs with FastAPI
* Structuring a Python backend application
* Writing automated tests with pytest
* Performing integration testing
* Automating browser-based tests with Selenium
* Validating APIs using Postman
* Automating tests through GitHub Actions
* Generating test reports
* Performing basic performance testing
* Applying software quality engineering practices to a working application
