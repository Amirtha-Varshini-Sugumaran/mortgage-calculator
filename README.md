# Mortgage Calculator

## Project Overview

This repository contains a small Java command-line mortgage calculator. The program accepts loan inputs from the terminal, applies the standard fixed-rate mortgage formula, and prints the estimated monthly payment in currency format.

Key capabilities:

- Accept principal, annual interest rate, and loan period from standard input.
- Convert annual interest into monthly interest.
- Calculate the number of monthly payments.
- Apply the amortized mortgage payment formula.
- Format the result with Java's built-in currency formatter.

## Architecture

```mermaid
flowchart LR
    user["Terminal user"]
    input["Scanner input"]
    validation["Numeric parsing"]
    formula["Mortgage formula"]
    format["Currency formatting"]
    output["Monthly payment output"]

    user --> input
    input --> validation
    validation --> formula
    formula --> format
    format --> output
```

End-to-end flow:

1. The user starts the Java program from a terminal.
2. `Scanner` reads principal, annual interest rate, and loan period.
3. The program derives monthly interest and total payment count.
4. The amortization formula calculates the monthly payment.
5. `NumberFormat` renders the result as a currency string.

## Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Language | Java | Core application logic |
| Input | `java.util.Scanner` | Terminal input parsing |
| Calculation | `java.lang.Math` | Exponentiation for amortization formula |
| Output | `java.text.NumberFormat` | Currency formatting |
| Runtime | JDK | Compilation and execution |

## Data Flow

1. Ingestion: terminal prompts collect principal, annual interest rate, and loan period.
2. Processing: annual interest is converted to monthly interest and years are converted to payment count.
3. Storage: no persistent storage is used; values live in memory for a single run.
4. Transformation: numeric inputs are transformed into a monthly mortgage payment.
5. Serving: the monthly payment is printed to standard output.

## Setup Instructions

### Prerequisites

- JDK 17 or later
- Terminal or command prompt

### Environment Variables

No environment variables are required.

### Docker Setup

Docker is not required. The program runs directly with the JDK.

### Local Run Steps

Compile:

```bash
javac Mortgage_Calculator.java
```

Run:

```bash
java Mortgage_Calculator
```

## Project Structure

```text
.
|-- Mortgage_Calculator.java  # CLI mortgage calculator implementation
|-- README.md                 # Maintainer documentation
|-- .gitignore                # Local-only exclusions
```

## Key Components

### ETL Pipeline

There is no batch ETL pipeline. The calculator has a direct input-processing-output flow for one terminal session.

### Streaming Pipeline

No streaming pipeline is included.

### dbt Models

No dbt models are included because the project has no database or warehouse.

### API Layer

No API layer is included. The interface is terminal-based.

### Data Quality Checks

The current program relies on Java numeric parsing. Future input validation should reject negative principal values, zero or negative loan terms, and invalid interest-rate values with clear messages.

## Testing

Manual verification:

```bash
javac Mortgage_Calculator.java
java Mortgage_Calculator
```

Recommended future automated tests:

- Extract the mortgage formula into a pure method.
- Add unit tests for common principal, interest-rate, and loan-period combinations.
- Add validation tests for invalid numeric inputs.

## Troubleshooting

| Issue | Fix |
|---|---|
| `javac` is not recognized | Install a JDK and ensure it is on `PATH` |
| `java Mortgage_Calculator` cannot find the class | Run the command from the repository root after compiling |
| Input fails with a parsing error | Enter numbers only, without currency symbols or percent signs |
| Output differs by currency symbol | `NumberFormat` uses the machine's default locale |

## Future Improvements

- Extract calculation logic into a reusable method.
- Add input validation and retry prompts.
- Add automated unit tests.
- Support extra monthly payments.
- Support locale selection for currency output.
- Add a small CLI help flag.
