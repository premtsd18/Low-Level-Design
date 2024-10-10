# Desktop Builder - Builder Design Pattern

## Overview

This project demonstrates the **Builder Design Pattern** by constructing different types of desktops (Dell and HP) step by step, allowing the creation of complex objects in a flexible and maintainable manner. The **Builder Pattern** separates the construction of an object from its representation, ensuring that the same construction process can create different types of products.

## Design Pattern: Builder

The **Builder Design Pattern** is a creational design pattern used to construct a complex object step by step. It is especially useful when creating objects with multiple components or configurations, providing more control over the construction process and promoting clean, maintainable code.

## Components

1. **Desktop**: The product class that holds the desktop's specifications, including:
    - Motherboard
    - Processor
    - Memory
    - Storage
    - Graphics Card

   The `Desktop` class provides setters and getters for these attributes, as well as a `display()` method to print the specifications of the desktop.

2. **DesktopBuilder (Abstract Class)**: An abstract class that defines the blueprint for building a desktop. It contains methods like `buildMotherboard()`, `buildProcessor()`, `buildMemory()`, `buildStorage()`, and `buildGraphicsCard()`, which are implemented by concrete builders.

3. **DellDesktopBuilder**: A concrete builder class that builds a Dell desktop by setting Dell-specific components (e.g., Dell motherboard, 32GB RAM, NVIDIA RTX 3080).

4. **HpDesktopBuilder**: A concrete builder class that builds an HP desktop by setting HP-specific components (e.g., HP motherboard, 16GB RAM, integrated graphics).

5. **DesktopDirector**: The director class that manages the construction process. It takes a `DesktopBuilder` object and calls the appropriate building methods to create a desktop.

6. **DesktopBuilderDemo**: The main class that demonstrates how to build desktops using the builder pattern. It builds a Dell and an HP desktop and displays their specifications.

## Usage

1. **Building a Dell Desktop**:
   The `DesktopDirector` uses the `DellDesktopBuilder` to construct a Dell desktop by calling all the build steps (motherboard, processor, memory, storage, graphics card).

   ```java
   DellDesktopBuilder dellDesktopBuilder = new DellDesktopBuilder();
   Desktop dellDesktop = director.buildDesktop(dellDesktopBuilder);
   dellDesktop.display();