# Prototype Pattern Example

## Overview

This project demonstrates the **Prototype Design Pattern** using two different scenarios: one for network devices (such as routers and switches) and another for products (such as laptops and smartphones). The Prototype Pattern is a creational design pattern that allows for the cloning of objects, providing an efficient way to duplicate instances without directly calling their constructors.

## Design Pattern: Prototype

The **Prototype Design Pattern** is used when the cost of creating a new object is high and a copy of an existing object can be used as a starting point. This pattern involves implementing a `clone()` method, which allows objects to be copied and modified independently.

### Key Benefits:
- Reduces the cost of creating new objects.
- Helps avoid expensive resource allocation during object creation.
- Provides flexibility to create different configurations by copying and modifying objects.

---

## Components

### 1. **Network Device Example**

- **NetworkDevice**: The abstract base class representing the prototype for network devices. It defines two methods:
    - `clone()`: Used to clone the object.
    - `display()`: Displays the properties of the network device.

- **Router**: A concrete implementation of `NetworkDevice`, representing a router. It includes properties such as `name`, `IP`, and `securityPolicy`.

- **Switch**: Another concrete implementation of `NetworkDevice`, representing a switch with `name` and `protocol`.

- **RouterDemo**: The main class where the prototype pattern is demonstrated by cloning router and switch objects.

### 2. **Product Example**

- **ProductPrototype**: The abstract base class for products that defines the `clone()` and `display()` methods.

- **Product**: A concrete implementation of `ProductPrototype`, representing a product with `name` and `price`.

- **ProductDemo**: The main class where the prototype pattern is demonstrated by cloning product objects.

---

## Usage

### Network Device Example
1. **Cloning Network Devices**:
   In the `RouterDemo` class, both a `Router` and a `Switch` are created and then cloned using the `clone()` method.

2. **Displaying the Clones**:
   The `display()` method is used to print the details of the original devices and their clones. After cloning, their names are updated using the `update()` method.

   Example of creating and cloning a `Router`:
   ```java