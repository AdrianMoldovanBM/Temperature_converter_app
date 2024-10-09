# Temperature converter app
Excited to announce the creation of a new temperature converter app in Python, utilizing Google Colab. 
This project aims to deliver an intuitive and efficient solution for converting temperatures between Celsius, Fahrenheit, and Kelvin.
It provides greater flexibility by allowing users to input and convert between any of the three temperature scales.
It also includes good error handling for both invalid numeric inputs and conversion choices.

# Code:
    def temperature_converter():
    # Prompt the user to select the input temperature type
    while True:
        temp_type_input = input("What is the temperature type you are providing? Choose 'celsius', 'fahrenheit', or 'kelvin': ").lower()
        
        if temp_type_input in ["celsius", "fahrenheit", "kelvin"]:
            break
        
        # Dealing with invalid inputs
        else:
            print("Invalid input. Please enter 'celsius', 'fahrenheit', or 'kelvin'.")
    
    # Input validation for the temperature value
    while True:
        try:
            number_input = float(input(f"Please enter the temperature in {temp_type_input}: "))
            break
        except ValueError:
            print("Invalid input. Please enter a valid number.")
    
    # Prompt to convert to a different temperature scale
    while True:
        convert_to = input("Convert to 'celsius', 'fahrenheit', or 'kelvin': ").lower()
        
        # Ensure the user doesn't choose the same type of conversion
        if convert_to == temp_type_input:
            print(f"You're trying to convert {temp_type_input} to {temp_type_input}. Please choose a different unit.")
            continue

        # The process of calculation
        if convert_to in ["celsius", "fahrenheit", "kelvin"]:
            if temp_type_input == "celsius":
                if convert_to == "fahrenheit":
                    result = number_input * 1.8 + 32
                    print(f"{result:.2f}\u00B0F")
                elif convert_to == "kelvin":
                    result = number_input + 273.15
                    print(f"{result:.2f} K")

            elif temp_type_input == "fahrenheit":
                if convert_to == "celsius":
                    result = (number_input - 32) / 1.8
                    print(f"{result:.2f}\u00B0C")
                elif convert_to == "kelvin":
                    result = (number_input - 32) / 1.8 + 273.15
                    print(f"{result:.2f} K")

            elif temp_type_input == "kelvin":
                if convert_to == "celsius":
                    result = number_input - 273.15
                    print(f"{result:.2f}\u00B0C")
                elif convert_to == "fahrenheit":
                    result = (number_input - 273.15) * 1.8 + 32
                    print(f"{result:.2f}\u00B0F")
            
            return result

        # Dealing with invalid inputs    
        else:
            print("Invalid input. Please enter 'celsius', 'fahrenheit', or 'kelvin'.")

# Execution:            
print(temperature_converter())
