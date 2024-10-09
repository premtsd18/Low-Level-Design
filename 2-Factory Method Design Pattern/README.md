# Logger System - Factory Method Design Pattern

## Overview

This project demonstrates the **Factory Method Design Pattern** for creating different types of loggers (`InfoLogger`, `DebugLogger`, `ErrorLogger`). The Factory Method Design Pattern allows for the creation of objects in a way that the client code remains decoupled from the actual implementation, promoting flexibility and scalability.

## Design Pattern: Factory Method

The **Factory Method Design Pattern** defines an interface for creating objects but lets subclasses decide which class to instantiate. This allows clients to use the factory without needing to know the specific logger class being created.

In this project, the entire implementation is encapsulated in a single file `LoggerDemo.java`, which contains the logger classes, factory classes, and the demonstration code.

## Components

- **ILogger**: The interface that defines the `log(String msg)` method, which is implemented by all logger classes.
- **InfoLogger**: A concrete logger class for logging informational messages.
- **DebugLogger**: A concrete logger class for logging debug messages.
- **ErrorLogger**: A concrete logger class for logging error messages.
- **LoggerFactory**: Interface for logger factory classes, with a method to create logger instances.
- **InfoLoggerFactory**, **DebugLoggerFactory**, **ErrorLoggerFactory**: Concrete factory classes for creating the respective logger types.
- **LoggerDemo**: The main class demonstrating the use of the factory method pattern to create and use loggers.

## Usage

### 1. Logger Creation
To create a logger, use one of the concrete factory classes (`InfoLoggerFactory`, `DebugLoggerFactory`, `ErrorLoggerFactory`). Based on the log level required, the appropriate logger instance is created.

Example:
```java
LoggerFactory loggerFactory = new InfoLoggerFactory();
ILogger logger = loggerFactory.createLogger();
logger.log("This is an info log message");