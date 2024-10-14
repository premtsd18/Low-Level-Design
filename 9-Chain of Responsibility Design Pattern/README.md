# Swiggy Order Processing - Chain of Responsibility Design Pattern

## Overview

This project demonstrates the **Chain of Responsibility Design Pattern** using an order processing system for a food delivery service (similar to Swiggy). The **Chain of Responsibility Pattern** allows a request (in this case, an order) to be passed through a chain of handlers, where each handler either processes the request or passes it to the next handler in the chain.

## Design Pattern: Chain of Responsibility

The **Chain of Responsibility Pattern** is a behavioral design pattern that allows multiple objects (handlers) to process a request without the sender needing to know which object will handle it. This pattern promotes flexibility and loose coupling, making it easier to add or remove handlers in the chain.

### Key Features:
- **Decoupling**: The sender of a request is decoupled from the actual processing of the request, allowing handlers to be added or removed dynamically.
- **Flexible Chain**: Handlers can process requests in a flexible and extensible manner, as each handler only handles its specific part of the process.
- **Extensibility**: New handlers can be added without modifying existing code.

## Components

### 1. **OrderHandler (Abstract Class)**

This is the abstract base class that defines the structure for all concrete handlers. It contains:
- A reference to the next handler in the chain (`nextHandler`).
- The abstract method `processOrder()`, which concrete handlers must implement.

### 2. **Concrete Handlers**

Each concrete handler implements the `processOrder()` method and is responsible for a specific part of the order processing:
- **OrderValidationHandler**: Validates the order.
- **PaymentProcessingHandler**: Processes payment for the order.
- **OrderPreparationHandler**: Prepares the order.
- **DeliveryAssignmentHandler**: Assigns a delivery driver to the order.
- **OrderTrackingHandler**: Tracks the order once it's out for delivery.

### 3. **Client (SwiggyOrder)**

The client class creates a chain of handlers by linking them together. It sends an order request to the first handler (`OrderValidationHandler`), which processes the request and passes it to the next handler in the chain. The chain continues until the request is fully processed.

## Code Example

```java
public class SwiggyOrder {
    public static void main(String[] args) {
        // Create a chain of responsibility for order processing
        OrderHandler orderProcessingChain = new OrderValidationHandler(
            new PaymentProcessingHandler(
                new OrderPreparationHandler(
                    new DeliveryAssignmentHandler(
                        new OrderTrackingHandler(null))))); 
                        // The last handler has no next handler

        // Simulate an order being placed
        String order = "Pizza";
        orderProcessingChain.processOrder(order);
    }
}