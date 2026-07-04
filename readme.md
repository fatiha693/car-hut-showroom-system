# Car Hut — Offline Car Showroom Management System

A Java-based offline management system for a car showroom, handling buyers, sellers, vehicle inventory, and invoicing through a clean, package-organized object-oriented design.

## Overview

Car Hut simulates the day-to-day operations of a car showroom: tracking which vehicles are available, recording buyer and seller information, and generating invoices for completed sales. The system runs entirely offline, persisting data through structured text files rather than a database — making it lightweight, dependency-free, and easy to run anywhere a JDK is installed.

This project was originally built as a refactoring lab exercise, with an emphasis on organizing a growing codebase into clean, well-separated packages rather than keeping all logic in a single monolithic class.

## Architecture

The codebase is organized into purpose-driven packages under `edu.iutcs.cr`:

```
src/edu/iutcs/cr/
├── Main.java              # Application entry point
├── persons/               # Buyer and seller entity classes
├── system/                # Core business logic (showroom operations, invoicing)
└── vehicles/              # Car/vehicle entity classes
```

| Package | Responsibility |
|---|---|
| `persons` | Represents the people in the system — buyers and sellers — encapsulating their identity and transaction-relevant data |
| `vehicles` | Represents inventory — vehicle attributes such as make, model, and pricing |
| `system` | Coordinates the showroom's core operations: matching buyers to available vehicles, processing sales, and generating invoices |
| (root) | `Main.java` wires the system together and serves as the runnable entry point |

This separation follows the **Single Responsibility Principle** — each package owns one concern (people, inventory, or business logic), which makes the system easier to extend (e.g., adding a financing module) without touching unrelated code.

## Data Persistence

Rather than requiring a database setup, Car Hut persists its state in plain text files at the project root:

- **`buyers.txt`** — records of registered buyers
- **`sellers.txt`** — records of registered sellers
- **`cars.txt`** — vehicle inventory
- **`invoices.txt`** — generated sales invoices

This flat-file approach keeps the project fully self-contained and runnable with zero external setup — ideal for demonstrating core logic without infrastructure overhead.

## Getting Started

### Prerequisites
- Java Development Kit (JDK) 8+

### Compile
```bash
javac -d out -sourcepath src src/edu/iutcs/cr/*.java src/edu/iutcs/cr/persons/*.java src/edu/iutcs/cr/system/*.java src/edu/iutcs/cr/vehicles/*.java
```

### Run
```bash
java -cp ./out edu.iutcs.cr.Main
```

> On Windows, use `.\out` in place of `./out` for the classpath.

## What This Project Demonstrates

- **Package-based architecture** — organizing a Java application into logically separated modules instead of a flat, single-package structure
- **Separation of concerns** — entity classes (`persons`, `vehicles`) are kept independent of business/operational logic (`system`)
- **File-based persistence** — reading and writing structured application state without a database layer
- **Refactoring discipline** — this project began as a lab exercise specifically focused on taking a working but poorly organized codebase and restructuring it into cleaner, more maintainable form

## Possible Extensions

- Replace flat-file storage with a lightweight embedded database (e.g., SQLite) for more robust data integrity
- Add input validation and error handling around file I/O
- Introduce a simple CLI menu or GUI for interactive use rather than editing text files directly
- Add unit tests around `system` package logic (sale processing, invoice generation)

## Author

**fatiha693**

## License

This project is for educational purposes as part of coursework on object-oriented refactoring and software design.
