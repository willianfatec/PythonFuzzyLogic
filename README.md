# PythonFuzzyLogic
The library for working with fuzzy logic in python

[![Maintainability](https://api.codeclimate.com/v1/badges/0e2daeaf81fad51863fb/maintainability)](https://codeclimate.com/github/alsprogrammer/PythonFuzzyLogic/maintainability)
[![Test Coverage](https://api.codeclimate.com/v1/badges/0e2daeaf81fad51863fb/test_coverage)](https://codeclimate.com/github/alsprogrammer/PythonFuzzyLogic/test_coverage)

### What is this repository for? ###

This library is developed to be used for modelling the fuzzy sets and fuzzy controllers. The library cab be used both
in production and for educational purposes.

Version 0.1a

### The example ###

    from fuzzypy import *

    # Create a fuzzy variable
    fuzzy_temp = FuzzyVariable() # Temperature

    # Define the membership functions
    hot = TriFunc(20, 25, 50)
    norm = TriFunc(15, 20, 25)
    cold = TrapecFunc(0, 5, 10, 20)

    # Determine the fuzzy terms
    temp_is_hot = fuzzy_temp.is_(hot)  # The temperature is hot
    temp_is_norm = fuzzy_temp.is_(norm)  # The temperature is normal
    temp_is_cold = fuzzy_temp.is_(cold)  # The temperature is cold

    # Create an output fuzzy variable
    fuzzy_blow = FuzzyVariable()  # The speed of the fan

    # and its membership functions
    slow = TriFunc(0, 0, 750)
    fast = TriFunc(250, 1000, 1000)

    # Determine the rules
    blow_slow = FuzzyRule(temp_is_cold | temp_is_norm, fuzzy_blow, slow)  # If the temperature is cold or normal then fan speed is slow
    blow_fast = FuzzyRule(temp_is_hot, fuzzy_blow, fast)  # If the temperature is hot then fan speed is fast

    # Let the temperature be 30 degrees
    fuzzy_temp.value = 30

    # Lets find the limits of the variables
    print("Temp lower limit is {}".format(fuzzy_temp.low_limit))
    print("Temp upper limit is {}".format(fuzzy_temp.upp_limit))
    print("Blow lower limit is {}".format(fuzzy_blow.low_limit))
    print("Blow upper limit is {}".format(fuzzy_blow.upp_limit))

    print("The temperature is {}".format(fuzzy_temp.value))
    fan_speed = apply_defuzzyfy_COG([blow_slow, blow_fast])  # then the fan speed is
    print("Defuzzyfied values are {}".format(fan_speed))  # it could be more then one value
    print("Or defuzzyfied fan speed is {}".format(fuzzy_blow.value))  # and we can check the value of the fan speen directly

    fuzzy_temp.value = 13  # and now the temp is 13 degrees
    apply_defuzzyfy_COG([blow_slow, blow_fast])  # let us find the fan speed
    print("Now the temperature is {}, and the fan speed is {}".format(fuzzy_temp.value, fuzzy_blow.value))  # and print it


### How do I get set up? ###

Under construction now.
* Summary of set up
* Configuration
* Dependencies
* Database configuration
* How to run tests
* Deployment instructions

### Contribution guidelines ###

Under construction now.
* Writing tests
* Code review
* Other guidelines
