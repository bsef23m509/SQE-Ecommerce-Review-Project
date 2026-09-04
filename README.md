# E-commerce Product Review System — Software Quality Engineering

A FastAPI-based e-commerce product review system developed as a **Software Quality Engineering (SQE)** course project. The project focuses not only on application development but also on **software testing, test automation, API validation, performance testing, test reporting, and Continuous Integration (CI)**.

## Overview

The system provides a simple web interface and REST API for viewing products and submitting product reviews. Product data and reviews are stored in a JSON file, while the application uses Pydantic models for data validation.

The primary focus of this project is applying software quality practices to a working application through multiple levels of testing and automated validation.

## Key Features

* FastAPI backend with REST API endpoints
* Server-rendered web pages using Jinja2 templates
* Product listing and product detail pages
* Product review submission with rating validation
* Pydantic-based data models
* Automated API testing with `pytest`
* UI test automation with Selenium
* API validation using Postman
* Performance testing using ApacheBench (`ab`)
* HTML test report generation
* Timestamped performance test reports
* Local CI test runner script
* GitHub Actions workflow for automated CI testing
* Automated test report artifact generation

## Testing & Quality Assurance

The project implements testing at multiple levels to evaluate application correctness and behavior.

### API Testing

The `pytest` API test suite verifies:

* Successful retrieval of all products
* Retrieval of individual products
* Handling of non-existent products
* Successful review submission
* Missing review validation
* Missing rating validation
* Invalid rating values
* Appropriate HTTP status codes

The tests use FastAPI's `TestClient` to test the application endpoints directly.

### UI Testing

Selenium is used to automate a browser-based user interaction:

1. Open a product page
2. Enter a product review
3. Select a rating
4. Submit the review
5. Verify that the submitted review appears on the page

This provides an example of automated end-to-end UI testing.

### API Validation with Postman

A Postman collection is included for manually validating the application's API endpoints.

The collection contains requests for:

* `GET /api/products`
* `GET /api/products/{id}`
* `POST /product/{id}/reviews`

This provides an additional method of validating API behavior outside the automated test suite.

### Performance Testing

The `performance_tests.sh` script uses **ApacheBench (`ab`)** to evaluate the performance of selected endpoints.

The following scenarios are tested:

* `GET /api/products` — 100 requests with 10 concurrent requests
* `GET /api/products/1` — 100 requests with 10 concurrent requests
* `POST /product/1/reviews` — 50 requests with 5 concurrent requests

Performance results are automatically stored in timestamped directories containing raw output and Markdown reports.

## Continuous Integration

The repository includes a **GitHub Actions CI workflow** that runs automatically on:

* Pushes to the repository
* Pull requests

The workflow:

1. Checks out the repository
2. Sets up Python 3.13
3. Creates a virtual environment
4. Installs project dependencies
5. Starts the FastAPI application
6. Executes the complete `pytest` suite
7. Generates an HTML test report
8. Stops the application server
9. Uploads the test report as a GitHub Actions artifact

This provides automated verification of the application whenever changes are pushed or proposed through a pull request.

## Local CI Runner

The `ci_run.sh` script provides a local equivalent of the CI testing process.

It:

* Activates the Python virtual environment
* Starts the FastAPI server
* Runs the complete test suite
* Generates an HTML report
* Stops the server after testing

## Project Structure

```text
SQE-Ecommerce-Review-Project/
│
├── .github/
│   └── workflows/
│       └── pytest.yml
│
├── app/
│   ├── static/
│   ├── templates/
│   ├── __init__.py
│   ├── main.py
│   └── models.py
│
├── performance_reports/
│   └── <timestamp>/
│       └── ...
│
├── test_reports/
│   ├── assets/
│   └── report.html
│
├── tests/
│   ├── conftest.py
│   ├── test_api.py
│   └── test_ui_selenium.py
│
├── .gitignore
├── ci_run.sh
├── performance_tests.sh
├── postman_collection.json
├── products.json
├── requirements.txt
├── Ecommerce_Product_Review_System_Documentation.docx
└── README.md
```

## Application Architecture

The application is implemented using **FastAPI** and consists of:

* **FastAPI application** — handles HTTP requests and API routes
* **Pydantic models** — defines product and review data structures
* **Jinja2 templates** — renders the web interface
* **JSON data storage** — stores product and review information
* **Pytest** — automated API and integration testing
* **Selenium** — browser-based UI automation
* **Postman** — API validation
* **ApacheBench** — performance testing
* **GitHub Actions** — continuous integration

## API Endpoints

| Method | Endpoint                        | Purpose                     |
| ------ | ------------------------------- | --------------------------- |
| `GET`  | `/api/products`                 | Retrieve all products       |
| `GET`  | `/api/products/{product_id}`    | Retrieve a specific product |
| `POST` | `/product/{product_id}/reviews` | Submit a product review     |
| `GET`  | `/`                             | Product listing web page    |
| `GET`  | `/product/{product_id}`         | Product detail web page     |

### Review Validation

Review submissions validate:

* Presence of review text
* Presence of rating
* Rating range from **1 to 5**
* Existence of the requested product

Invalid requests return appropriate HTTP error responses.

## Running the Project

### 1. Clone the Repository

```bash
git clone https://github.com/bsef23m509/SQE-Ecommerce-Review-Project.git
cd SQE-Ecommerce-Review-Project
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it:

**Linux / macOS**

```bash
source .venv/bin/activate
```

**Windows**

```bash
.venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the Application

```bash
uvicorn app.main:app --reload --port 8000
```

The application will be available at:

```text
http://localhost:8000
```

## Running Tests

### Run API Tests

```bash
pytest tests/test_api.py -q
```

### Run Selenium UI Tests

The Selenium test requires a compatible Chrome/ChromeDriver setup.

```bash
pytest tests/test_ui_selenium.py -q
```

### Run the Complete Test Suite

```bash
PYTHONPATH=$(pwd) pytest -q --html=test_reports/report.html
```

### Run the Local CI Script

```bash
./ci_run.sh
```

### Run Performance Tests

ApacheBench (`ab`) must be installed and available in the system PATH.

```bash
./performance_tests.sh
```

Performance reports are generated under:

```text
performance_reports/<timestamp>/
```

## Test Reporting

The project generates HTML test reports using `pytest-html`.

Reports can be found under:

```text
test_reports/report.html
```

GitHub Actions also uploads the generated test report as a workflow artifact, allowing test results to be inspected after a CI run.

## Documentation

The repository includes additional project documentation:

```text
Ecommerce_Product_Review_System_Documentation.docx
```

The documentation provides supplementary material related to the system and its software quality/testing work.

## Technologies & Tools

* **Python**
* **FastAPI**
* **Pydantic**
* **Jinja2**
* **Pytest**
* **pytest-html**
* **Selenium**
* **Postman**
* **ApacheBench**
* **GitHub Actions**
* **HTML / CSS / JavaScript**

## Learning Outcomes

This project provided practical experience with:

* Designing and testing REST APIs
* Unit and integration testing
* Automated browser-based testing
* API testing with Postman
* Test-driven quality validation
* Test report generation
* Performance and load testing
* Continuous Integration workflows
* Automating application testing through shell scripts
* Structuring software quality documentation
* Integrating testing into a software development workflow

## Course Context

This project was developed as part of the **Software Quality Engineering (SQE)** coursework during my BS Software Engineering studies.

The repository is maintained as an academic record of the implementation, testing strategies, automation, documentation, and quality assurance practices explored during the course.
