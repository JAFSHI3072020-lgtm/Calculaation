import math
from fractions import Fraction

def get_number(prompt):
    while True:
        num = input(prompt)
        try:
            # Try to evaluate as fraction first
            if '/' in num:
                return float(Fraction(num))
            else:
                return float(num)
        except ValueError:
            print("Invalid input! Please enter a valid number or fraction (e.g., 3/4).")

def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y == 0:
        return "Error: Division by zero!"
    return x / y

def exponent(x, y):
    return x ** y

def modulus(x, y):
    return x % y

def square_root(x):
    if x < 0:
        return "Error: Negative number!"
    return math.sqrt(x)

def logarithm(x, base=10):
    if x <= 0:
        return "Error: Logarithm undefined for non-positive numbers!"
    return math.log(x, base)

def trigonometry(func, x):
    rad = math.radians(x)
    if func == 'sin':
        return math.sin(rad)
    elif func == 'cos':
        return math.cos(rad)
    elif func == 'tan':
        if (x % 180) == 90:
            return "Error: Tangent undefined!"
        return math.tan(rad)
    else:
        return "Invalid function!"

def calculator():
    print("\nAdvanced Python Calculator")
    print("Select operation:")
    print("1. Add (+)")
    print("2. Subtract (-)")
    print("3. Multiply (*)")
    print("4. Divide (/)")
    print("5. Exponent (^)")
    print("6. Modulus (%)")
    print("7. Square Root (√)")
    print("8. Logarithm (log)")
    print("9. Trigonometry (sin, cos, tan)")

    choice = input("Enter choice (1-9): ")

    if choice in ['1','2','3','4','5','6']:
        num1 = get_number("Enter first number: ")
        num2 = get_number("Enter second number: ")

        if choice == '1':
            print(f"Result: {add(num1, num2)}")
        elif choice == '2':
            print(f"Result: {subtract(num1, num2)}")
        elif choice == '3':
            print(f"Result: {multiply(num1, num2)}")
        elif choice == '4':
            print(f"Result: {divide(num1, num2)}")
        elif choice == '5':
            print(f"Result: {exponent(num1, num2)}")
        elif choice == '6':
            print(f"Result: {modulus(num1, num2)}")

    elif choice == '7':
        num = get_number("Enter number: ")
        print(f"Result: {square_root(num)}")

    elif choice == '8':
        num = get_number("Enter number: ")
        base = input("Enter base (default 10): ")
        base = float(base) if base else 10
        print(f"Result: {logarithm(num, base)}")

    elif choice == '9':
        func = input("Enter function (sin, cos, tan): ").lower()
        angle = get_number("Enter angle in degrees: ")
        print(f"Result: {trigonometry(func, angle)}")

    else:
        print("Invalid choice!")

while True:
    calculator()
    again = input("Do you want to perform another calculation? (y/n): ").lower()
    if again != 'y':
        print("Goodbye!")
        break
