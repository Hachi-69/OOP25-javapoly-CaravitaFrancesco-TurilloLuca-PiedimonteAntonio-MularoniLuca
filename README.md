# Javapoly 🎲 🎩

Javapoly is a digital, interactive implementation of the classic property-trading board game. Developed as the final project for the [Object-Oriented Programming course](https://www.unibo.it/it/studiare/insegnamenti-competenze-trasversali-moocs/insegnamenti/insegnamento/2025/378219) during my Computer Science and Engineering studies at the University of Bologna (Cesena Campus).

🏆 **Final Evaluation: 29/30**

This repository is a personal fork of the original group project, highlighting my specific contributions to the application's core logic, architecture, and user interface.

## 🌟 Features

* **Flexible Setup:** Supports 2 to 4 local players.
* **Custom Player Tokens:** Players can choose from classic tokens or upload their own custom images from their local file system.
* **Game Persistence:** Save your progress to a `.json` file and load it later to resume exactly where you left off.
* **Interactive GUI:** Built with JavaFX, featuring a dynamic game board, real-time activity log, and financial control panels.
* **Robust Rules Engine:** Strict enforcement of game states (e.g., jail turns, bankruptcy) and financial transactions.

## 👨‍💻 My Contributions

As a core developer on this project, I took ownership of the primary domain model, defensive programming infrastructure, and critical parts of the setup UI. 

Here are the key areas I designed and implemented:

### 1. Domain Model & Design Patterns
* **Contract-Driven Design:** Engineered the `Player` interface and its concrete implementation (`PlayerImpl`) to ensure strict encapsulation and loose coupling with the UI.
* **State Pattern:** Designed the player's turn logic using the State Pattern (e.g., `FreeState`, `JailedState`, `BankruptState`). This eliminated complex nested `if/else` statements, allowing dynamic behavior changes (like serving jail time) while strictly adhering to the **Open/Closed Principle**.
* **Observer Pattern:** Implemented a reactive architecture where the `Player` notifies registered observers of movement or balance changes, ensuring the JavaFX View updates automatically without tightly coupling the Model to the GUI.

### 2. Defensive Programming & Generics
* **`ValidationUtils`:** Authored a comprehensive, generic utility library inspired by industry standards (like Google Guava and Apache Commons). It intercepts invalid states (e.g., negative balances, null references, empty strings) before they can corrupt the game flow, ensuring high application stability.

### 3. Advanced GUI & I/O Operations
* **Player Setup View:** Developed the initial configuration screens using JavaFX. 
* **Custom File Handling:** Implemented the `FileChooser` logic that allows players to upload custom tokens. Handled cross-platform compatibility by converting local absolute paths to standard URIs (`file.toURI().toString()`).
* **Functional Programming:** Utilized Java **Stream API** and Lambda Expressions to dynamically parse, filter, and validate user inputs (e.g., preventing duplicate player names) efficiently.

### 4. Serialization & Testing
* **JSON Integration:** Integrated Jackson annotations (`@JsonCreator`, `@JsonProperty`) directly into the Model to support complex object serialization, ensuring custom token paths and jail turns are perfectly restored upon loading a game.
* **Automated Testing:** Wrote comprehensive JUnit 6 test suites (`PlayerImplTest`, `ValidationUtilsTest`) to verify the integrity of the financial transactions, state transitions, and boundary validations.

## 🛠️ Tech Stack

* **Language:** Java 21+
* **GUI Framework:** JavaFX
* **Serialization:** Jackson (JSON)
* **Testing:** JUnit 6
* **Architecture:** MVC (Model-View-Controller)

## 👥 The Team

This project was a collaborative effort developed by the following team:

* **Luca Turillo** - Model (Player, ValidationUtils) and View (Player Setup, Token Customization)

* Antonio Piedimonte

* Francesco Caravita

* Luca Mularoni

## You can find the detailed report in `report.pdf`

## ⚖️ License & Disclaimer

This project is licensed under the [GNU GPLv3](LICENSE). 

**Disclaimer:** *Javapoly* is a non-commercial, academic project created strictly for educational purposes as part of a university course. 
"Monopoly", its game board design, mechanics, and related trademarks are the property of **Hasbro, Inc.** This software is not affiliated with, endorsed by, or sponsored by Hasbro. The source code is provided as a showcase of Object-Oriented Programming skills and software architecture, with absolutely no intention of commercialization or copyright infringement.
