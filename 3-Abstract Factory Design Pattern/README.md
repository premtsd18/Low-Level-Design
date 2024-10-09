# UI System - Abstract Factory Design Pattern

## Overview

This project demonstrates the **Abstract Factory Design Pattern** by creating families of related UI components (`Button`, `Textbox`) for different operating systems (Windows and Mac). The Abstract Factory pattern provides an interface for creating related objects without specifying their concrete classes, promoting flexibility and scalability in the UI system.

## Design Pattern: Abstract Factory

The **Abstract Factory Design Pattern** defines an interface (`IFactory`) for creating families of related or dependent objects without specifying their concrete classes. In this project, the concrete factories (`WinFactory`, `MacFactory`) create specific UI components such as buttons and textboxes based on the selected operating system (Windows or Mac).

## Project Structure

All classes are encapsulated within a single `UI.java` file for simplicity. This approach consolidates the entire implementation, making it easier to manage and understand for smaller projects or demonstrations.

### Components

- **IButton**: An interface for the button component, defining the `press()` method.
- **ITextbox**: An interface for the textbox component, defining the `setText()` method.
- **MacButton**: A concrete button class for Mac that implements the `IButton` interface.
- **WinButton**: A concrete button class for Windows that implements the `IButton` interface.
- **MacTextBox**: A concrete textbox class for Mac that implements the `ITextbox` interface.
- **WinTextBox**: A concrete textbox class for Windows that implements the `ITextbox` interface.
- **IFactory**: An abstract factory interface that defines methods to create `IButton` and `ITextbox` objects.
- **MacFactory**: A concrete factory class that creates Mac-specific buttons and textboxes.
- **WinFactory**: A concrete factory class that creates Windows-specific buttons and textboxes.
- **GUIAbstractFactory**: A static factory class that returns the appropriate factory (`MacFactory` or `WinFactory`) based on the OS type.
- **UI**: The main class that demonstrates the use of the Abstract Factory pattern to create and use UI components.

## Usage

1. **User Input**: The user is prompted to enter the type of operating system (`windows` or `mac`).
2. **Factory Selection**: Based on the input, the corresponding factory (`WinFactory` or `MacFactory`) is selected using the `GUIAbstractFactory`.
3. **Component Creation**: The factory creates instances of `IButton` and `ITextbox` specific to the chosen operating system.
4. **Operation**: The `press()` method is called on the `IButton`, and the `setText()` method is called on the `ITextbox`.

### Example

Here is an example of how the Abstract Factory pattern is used to create different UI components based on the OS type:

```java
public class UI {
    public static void main(String[] args) {
        System.out.println("Enter machine OS (windows/mac):");
        Scanner scanner = new Scanner(System.in);
        String osType = scanner.nextLine().toLowerCase();
        scanner.close();

        IFactory factory = GUIAbstractFactory.createFactory(osType);

        if (factory != null) {
            IButton button = factory.createButton();
            button.press();

            ITextbox textBox = factory.createTextbox();
            textBox.setText();
        } else {
            System.out.println("Invalid OS type");
        }
    }
}