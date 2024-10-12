# Payment Gateway - Singleton Design Pattern

## Overview

This project demonstrates the **Singleton Design Pattern** using a payment gateway manager. The **Singleton Pattern** ensures that only one instance of a class is created and provides a global point of access to that instance. In this example, the `PaymentGatewayManager` is designed to manage payment processing with only one instance being created, even in a multi-threaded environment.

## Design Pattern: Singleton

The **Singleton Design Pattern** restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system.

### Key Features:
- **Single Instance**: Only one instance of `PaymentGatewayManager` will ever be created.
- **Thread Safety**: The singleton instance is created in a thread-safe manner using `ReentrantLock` and **double-checked locking**.
- **Lazy Initialization**: The singleton instance is initialized only when first accessed (lazy loading).

## Components

### 1. **PaymentGatewayManager (Singleton Class)**

- **getInstance()**: This method provides a global point of access to the singleton instance. It uses **double-checked locking** with `ReentrantLock` to ensure that the instance is created only once in a thread-safe manner.
- **processPayment()**: Simulates processing a payment of a specified amount.

### 2. **PaymentGateway (Main Class)**

- This class demonstrates the creation of a singleton instance and verifies that only one instance of `PaymentGatewayManager` is created, even when attempting to create multiple instances.

## Code Example

```java
public class PaymentGateway {
    public static void main(String[] args) {
        PaymentGatewayManager paymentGateway = PaymentGatewayManager.getInstance();
        paymentGateway.processPayment(100.0);

        // Attempt to create another instance (should return the existing instance)
        PaymentGatewayManager anotherPaymentGateway = PaymentGatewayManager.getInstance();

        // Check if both instances are the same.
        if (paymentGateway == anotherPaymentGateway) {
            System.out.println("Both instances are the same. Singleton pattern is working.");
        } else {
            System.out.println("Singleton pattern is not working correctly.");
        }
    }
}