# Order Status Tracker - Observer Design Pattern

## Overview

This project demonstrates the **Observer Design Pattern** using an order status tracker. The **Observer Pattern** is a behavioral design pattern where an object (subject) maintains a list of its dependents (observers) and notifies them automatically of any state changes. In this example, an `Order` object tracks its status, and various observers like `Customer`, `Restaurant`, `DeliveryDriver`, and `CallCenter` are notified whenever the status of the order changes.

## Design Pattern: Observer

The **Observer Pattern** defines a one-to-many relationship between a subject and its observers. Whenever the state of the subject changes, all its observers are notified and updated automatically. This pattern is useful when multiple objects need to react to changes in another object, but without tight coupling between them.

### Key Features:
- **Observers**: Objects that need to be notified of changes in the subject (such as customers, restaurants, drivers, and call centers).
- **Subject**: The object being observed (in this case, the order).
- **Decoupling**: The subject and observers are loosely coupled, making the system flexible and extensible.

## Components

### 1. **Observer Interface**

- The `Observer` interface defines the `update(Order order)` method that all concrete observers must implement. This method is called by the subject when the order status changes.

### 2. **Concrete Observers**

- **Customer**: Represents a customer tracking their order.
- **Restaurant**: Represents the restaurant preparing the order.
- **DeliveryDriver**: Represents the delivery driver responsible for delivering the order.
- **CallCenter**: Represents a call center that tracks the order.

### 3. **Order (Subject)**

- The `Order` class is the subject that is being observed. It maintains a list of observers and notifies them whenever its status changes.
- Methods:
  - `attach(Observer observer)`: Adds an observer to the list.
  - `detach(Observer observer)`: Removes an observer from the list.
  - `setStatus(String newStatus)`: Updates the order status and notifies all observers of the change.

## Code Example

```java
public class OrderStatus {
    public static void main(String[] args) {
        // Create an order
        Order order1 = new Order(123);

        // Create customers, restaurants, drivers, and a call center to track the order
        Customer customer1 = new Customer("Customer 1");
        Restaurant restaurant1 = new Restaurant("Rest 1");
        DeliveryDriver driver1 = new DeliveryDriver("Driver 1");
        CallCenter callCenter = new CallCenter();

        // Attach observers to the order
        order1.attach(customer1);
        order1.attach(restaurant1);
        order1.attach(driver1);
        order1.attach(callCenter);

        // Simulate order status updates
        order1.setStatus("Out for Delivery");

        // Detach an observer (if needed)
        order1.detach(callCenter);

        // Simulate more order status updates
        order1.setStatus("Delivered");
    }
}