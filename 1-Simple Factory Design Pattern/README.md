# Logger System using Simple Factory Design Pattern

## Overview

This project demonstrates the use of the **Simple Factory Design Pattern** to create different types of loggers (`DebugLogger`, `ErrorLogger`, `InfoLogger`) based on the log level provided. The factory design pattern allows the creation of objects without exposing the instantiation logic to the client, promoting loose coupling and flexibility.

## Key Concepts

### Factory Design Pattern
In this project, the `LoggerFactory` class serves as the factory responsible for creating instances of different loggers. Depending on the log level (INFO, DEBUG, ERROR), it creates an appropriate logger object to handle the log messages.

The factory pattern simplifies object creation and centralizes the logic for instantiating logger objects, making the system more maintainable and scalable.

### Components
- **ILogger.java**: Interface that defines the contract for all logger classes. It declares the `log(String message)` method that each logger must implement.
- **InfoLogger.java**: Concrete implementation of `ILogger` that handles logging for informational messages.
- **DebugLogger.java**: Concrete implementation of `ILogger` that handles logging for debug messages.
- **ErrorLogger.java**: Concrete implementation of `ILogger` that handles logging for error messages.
- **LogLevel.java**: Enum that defines the different log levels (INFO, DEBUG, ERROR).
- **LoggerFactory.java**: Factory class responsible for creating logger objects based on the log level.
- **Main.java**: Entry point of the application where the loggers are utilized.

## Files

- **ILogger.java**: Defines the interface for the logger types.
- **InfoLogger.java**: Logs information messages.
- **DebugLogger.java**: Logs debug messages.
- **ErrorLogger.java**: Logs error messages.
- **LogLevel.java**: Enum defining log levels.
- **LoggerFactory.java**: Factory class to create logger objects based on the log level.
- **Main.java**: Example usage of the logger system.

## Usage

### 1. Logger Creation
To create a logger, use the `LoggerFactory` class. It will return the appropriate logger based on the log level passed.

Example:
```java
ILogger logger = LoggerFactory.getLogger(LogLevel.INFO);
logger.log("This is an info message");