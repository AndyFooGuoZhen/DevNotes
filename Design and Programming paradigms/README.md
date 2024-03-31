# System Design

## SOLID

https://www.youtube.com/watch?v=_jDNAf3CzeY

### **S - Single responsibility**

- Each class should have one responsibility
- Do not add too many functions into a class

### O - Open closed

- Classes do not have to be rewritten to add new features
- Open for extension , closes for modification (too many changes are not good)

### L - Liskov substitution

- You should be able to replace an instance of a subclass with a superclass without causing errors
- Example 1  :

![image](https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/fd93204d-3e76-4d11-b2d5-18ca1c4decf8)

- Example 2 (Where liskov principle is violated):

![image](https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/8e82d0c8-b2f2-44f4-b1f2-7bfe1861566a)

- In here, we cant replace electric car with car because the method shiftUp is not supported

### I - Interface segregation

- Larger interfaces can be divided into more smaller ones
- Allows splitting functionality of a class without LSP violation
- Using the previous example, we can create two interfaces called combustionVehicle and ElectricVehicle where we only add the shiftUp method to combustionVehicle class
- Then we can implement the correct interfaces correctly for our classes

### D - Dependency Inversion

- Design software that is losely coupled, allows for easy modifications to be made and tested
- Tightly coupled example :
    - If we were to add a new payment method we need to modify the payment service class too

![image](https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/71d7a5b2-918b-43f9-bfa8-dba359fc39c7)

- Loosely coupled example
    - If we add new payment paymne tmethod (processor), we can just inject it into the service

![image](https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/2d5bf537-2b8b-4051-a486-17458c5f2934)

---

# Pure functions
- Functions that behave deterministicly, always returns expected output. (Same input same output)
- Doesn't affect state of external variables, does not change original value
- Easy to test
- Example of non pure function:
- <img width="400" alt="image" src="https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/37f618c2-f6d8-497e-b656-a1d1dd21c3c0">
- Second example of non pure function ( the array is not copied here, we are modifying the original array):
- <img width="400" alt="image" src="https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/f75cc8ac-1bbd-455b-80d1-b5dbf2c75d3c">
- Pure function (We use the spread operator to create a copy):
- <img width="400" alt="image" src="https://github.com/AndyFooGuoZhen/DevNotes/assets/77149531/d1e2c3b9-2d14-43f2-8dd8-600fe1ee2f92">




