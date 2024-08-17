# Question

Design a parking system for a parking lot with three kinds of parking spaces: big, medium, and small. Each size has a fixed number of slots.

Implementation

Implement the `ParkingSystem` class with the following methods:

`ParkingSystem(int big, int medium, int small)`

- **Description**: Initializes an object of the `ParkingSystem` class. The number of slots for each parking space is provided as part of the constructor.

- **Parameters**:
  - `big` (int): Number of big parking spaces.
  - `medium` (int): Number of medium parking spaces.
  - `small` (int): Number of small parking spaces.

`bool addCar(int carType)`

- **Description**: Checks whether there is a parking space available for the car based on its type. The carType can be one of three kinds: big, medium, or small, represented by `1`, `2`, and `3` respectively. A car can only park in a parking space of its carType.

- **Parameters**:

  - `carType` (int): Type of the car (1 for big, 2 for medium, 3 for small).

- **Returns**:
  - `true` if there is an available parking space for the carType and the car is successfully parked.
  - `false` if no space is available for the carType.

## Leetcode Link

[1603. Design Parking System](https://leetcode.com/problems/design-parking-system/)

## Solution

### Java Solution 1

```java
class ParkingSystem {
    int beeg;
    int meed;
    int smol;

    public ParkingSystem(int big, int medium, int small) {
        beeg = big;
        meed = medium;
        smol = small;
    }

    public boolean addCar(int carType) {
        if(carType == 1 && beeg > 0) {
            beeg--;
            return true;
        } else if(carType == 2 && meed > 0) {
            meed--;
            return true;
        } else if(carType == 3 && smol > 0) {
            smol--;
            return true;
        }
        return false;
    }
}
```

### Java Solution 2

```java
int[] count;
public ParkingSystem(int big, int medium, int small) {
    count = new int[]{big, medium, small};
}

public boolean addCar(int carType) {
    return count[carType - 1]-- > 0;
}
```
