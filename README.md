# Game Warehouse Management System

A Java-based system for managing virtual game warehouses, players, and materials, providing an interactive way to observe material movement between players and warehouses.

## Overview

This project is a warehouse management system designed to:
- Add or remove materials to/from warehouses.
- Transfer materials between player-owned warehouses.
- Notify an observer about any material changes in warehouses.
- Track player inventories and warehouse data.

## Features

- Player management with multiple warehouses per player.
- Dynamic material addition and removal with capacity validation.
- Transfer materials between warehouses owned by the same player.
- Observer design pattern for real-time notifications.
- Error handling for invalid operations.

## Classes and Methods

### 1. **Main**
The entry point of the program.
- **`main(String[] args)`**: Sets up players, warehouses, and materials. Demonstrates the system's capabilities by adding/removing materials and transferring them between warehouses.

---

### 2. **Player**
Represents a player in the game.

#### Fields:
- **`List<Warehouse<T>> warehouses`**: A list of the player's warehouses.
- **`String playerName`**: The name of the player.

#### Methods:
- **`Player(String playerName)`**: Constructor to create a player with a given name.
- **`String getPlayerName()`**: Returns the player's name.
- **`void addWarehouse(Warehouse<T> warehouse)`**: Adds a warehouse to the player's inventory.
- **`void removeWarehouse(Warehouse<T> warehouse)`**: Removes a warehouse from the player's inventory.
- **`List<Warehouse<T>> getWarehouses()`**: Retrieves all warehouses owned by the player.
- **`Warehouse<T> findWarehouse(int index)`**: Finds a warehouse by index.
- **`int getWarehouseCount()`**: Returns the number of warehouses owned by the player.
- **`int getTotalMaterialQuantity()`**: Calculates the total quantity of materials across all player warehouses.
- **`void moveMaterial(Warehouse<T> sourceWarehouse, T materialType, int quantity, Warehouse<T> destinationWarehouse)`**: Transfers materials between two warehouses.
- **`void outputWarehouseData()`**: Outputs detailed information about all warehouses.

---

### 3. **Warehouse**
Manages materials and notifies observers of changes.

#### Fields:
- **`Map<T, Integer> materials`**: Stores materials and their quantities.
- **`List<ObserverInterface<T>> observers`**: Stores observers monitoring the warehouse.

#### Methods:
- **`Warehouse()`**: Constructor to initialize materials and observers.
- **`void addObserver(ObserverInterface<T> observer)`**: Adds an observer.
- **`void removeObserver(ObserverInterface<T> observer)`**: Removes an observer.
- **`void addMaterial(T materialType, int quantity)`**: Adds a specified quantity of material.
- **`void removeMaterial(T materialType, int quantity)`**: Removes a specified quantity of material.
- **`int getMaterialQuantity(T materialType)`**: Retrieves the quantity of a specific material.
- **`Map<T, Integer> getMaterials()`**: Returns a copy of the materials map.
- **`void outputWarehouseData(int warehouseNumber)`**: Outputs details of the warehouse.

---

### 4. **MaterialType**
Represents a generic material type.

#### Fields:
- **`String name`**: Material name.
- **`String description`**: Material description.
- **`String icon`**: Icon representing the material.
- **`int maxCapacity`**: Maximum allowable quantity.

#### Methods:
- **`String getName()`**: Returns the material name.
- **`String getDescription()`**: Returns the material description.
- **`String getIcon()`**: Returns the material icon.
- **`int getMaxCapacity()`**: Returns the material's maximum capacity.

---

### 5. **ObserverInterface**
Defines the interface for observer classes.

#### Methods:
- **`void onMaterialAdded(T materialType, int quantity)`**: Triggered when a material is added.
- **`void onMaterialRemoved(T materialType, int quantity)`**: Triggered when a material is removed.

---

### 6. **Manager**
Implements `ObserverInterface` to monitor warehouse changes.

#### Methods:
- **`void onMaterialAdded(T materialType, int quantity)`**: Prints a notification for material addition.
- **`void onMaterialRemoved(T materialType, int quantity)`**: Prints a notification for material removal.

---

### 7. **Material Classes**
- **`Iron`**: Represents iron material.
- **`Copper`**: Represents copper material.

Each class extends `MaterialType` and defines specific attributes for the material.

---

## Usage

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>

2. **Compile and Run:** Use your preferred IDE or compile manually:
   ```bash
   javac -d . *.java
   java com.company.Main

3. **Output**:
- Initial warehouse data.
- Notifications when materials are added or removed.
- Updated warehouse data after material movements.
