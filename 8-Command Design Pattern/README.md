# Command Pattern - Document and Ride Service

## Overview

This project demonstrates the **Command Design Pattern** using two different examples: a document editor and a ride service application (similar to a ride-hailing app like Uber). The **Command Pattern** is a behavioral design pattern that turns a request into a stand-alone object, allowing the parameterization of clients with different requests and the queuing of operations.

## Design Pattern: Command

The **Command Pattern** encapsulates a request as an object, thereby allowing for the parameterization of methods with different requests, queue or log requests, and support undoable operations.

### Key Features:
- **Decoupling**: The invoker of the command doesn't need to know the specifics of how the command is executed.
- **Encapsulation**: The command object encapsulates the details of the action to be performed and allows easy extension.
- **Reusability**: New commands can be created without modifying existing code, promoting flexibility.

## Components

### 1. **Command Interface**

Defines the `execute()` method that concrete commands will implement:
- `ActionListenerCommand` for the Document example.
- `Command` for the Ride Service example.

### 2. **Concrete Command Classes**

These classes implement the command interface and execute the action by invoking methods on the receiver:
- In the Document example: `ActionOpen` and `ActionSave` are the concrete commands that open and save documents.
- In the Ride Service example: `RideRequestCommand` and `CancelRideCommand` are the commands that request or cancel rides.

### 3. **Receiver**

The receiver is the object that knows how to perform the operations:
- In the Document example, the receiver is the `Document` class, which opens or saves documents.
- In the Ride Service example, the receiver is the `RideService` class, which processes ride requests and cancellations.

### 4. **Invoker**

The invoker asks the command to carry out the request:
- `MenuOptions` is the invoker for the document commands.
- `RideRequestInvoker` is the invoker for the ride service commands.

## Code Examples

### Example 1: Document Command Pattern

This example simulates document operations (open and save):

```java
public class DocumentDemo {
    public static void main(String[] args) {
        Document doc = new Document(); // Receiver - performing action

        // Create concrete commands
        ActionListenerCommand clickOpen = new ActionOpen(doc);
        ActionListenerCommand clickSave = new ActionSave(doc);

        // Invoker
        MenuOptions menu = new MenuOptions();

        // Client code only adds commands to the menu
        menu.addCommand(clickOpen);
        menu.addCommand(clickSave);

        menu.executeCommands();
    }
}