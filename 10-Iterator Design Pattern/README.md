# Amazon Inventory - Iterator Design Pattern

## Overview

This project demonstrates the **Iterator Design Pattern** using an inventory system for a product collection. The **Iterator Pattern** provides a way to access elements of a collection (in this case, a product inventory) sequentially without exposing the underlying structure of the collection. This pattern is useful when you need to iterate over different types of collections in a uniform way.

## Design Pattern: Iterator

The **Iterator Design Pattern** is a behavioral pattern that provides an object to sequentially access the elements of a collection without exposing its internal structure. The iterator encapsulates the logic for traversal, and the client code can use it to iterate through the collection.

### Key Features:
- **Encapsulation**: The internal structure of the collection (such as lists, arrays, etc.) is hidden from the client.
- **Flexible Iteration**: Different types of collections can provide their own iterator, but the client interacts with them in a uniform way.
- **Separation of Concerns**: The iteration logic is separated from the collection itself, making the code cleaner and more maintainable.

## Components

### 1. **Product Class**

The `Product` class represents the individual items in the inventory. Each product has:
- A `name` (e.g., "Laptop", "Smartphone").
- A `price` (e.g., 99999.99).

### 2. **Iterator Interface**

The `Iterator` interface defines the common interface for iterating over a collection. It provides:
- `first()`: Returns the first element in the collection.
- `next()`: Moves to the next element and returns it.
- `hasNext()`: Checks whether there are more elements to iterate over.

### 3. **Concrete Iterator (ProductIterator)**

The `ProductIterator` class implements the `Iterator` interface and provides the logic for iterating over the product list:
- Keeps track of the current position in the collection.
- Returns products in the order they were added to the inventory.

### 4. **Aggregate (Inventory Class)**

The `Inventory` class is the aggregate that stores the collection of products. It provides:
- A method to add products (`addProduct()`).
- A method to create an iterator (`createIterator()`), which returns a `ProductIterator` for the product list.

### 5. **Client (AmazonInventory Class)**

The `AmazonInventory` class is the client that interacts with the inventory using the iterator:
- It creates the inventory, adds products, and uses the iterator to access and print the product details.

## Code Example

```java
public class AmazonInventory {
    public static void main(String[] args) {
        // Create some products
        Product product1 = new Product("Laptop", 99999.99);
        Product product2 = new Product("Smartphone", 49999.99);
        Product product3 = new Product("Headphones", 7999.99);

        // Create an inventory and add products
        Inventory inventory = new Inventory();
        inventory.addProduct(product1);
        inventory.addProduct(product2);
        inventory.addProduct(product3);

        // Create an iterator and iterate over the products
        Iterator iterator = inventory.createIterator();
        Product currentProduct = iterator.first();

        while (currentProduct != null) {
            System.out.println("Product: " + currentProduct.getName() + ", Price: $" + currentProduct.getPrice());
            currentProduct = iterator.next();
        }
    }
}