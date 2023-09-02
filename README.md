# calories-burn-calculator

# Function to validate and get a valid gender input from the user
def get_gender_input():
    while True:
        gender = input("Enter gender (male/female): ").strip().lower()
        if gender in ["male", "female"]:
            return gender
        else:
            print("Invalid input. Please enter 'male' or 'female'.")

# Function to validate and get a valid age input from the user
def get_age_input():
    while True:
        try:
            age = int(input("Enter age in years: "))
            if 1 <= age <= 150:  # Assuming a reasonable age range
                return age
            else:
                print("Invalid age. Please enter a valid age between 1 and 150.")
        except ValueError:
            print("Invalid input. Please enter a valid age as a whole number.")

# Function to validate and get a valid weight input from the user
def get_weight_input():
    while True:
        try:
            weight = int(input("Enter weight in kilograms: "))
            if 1 <= weight <= 500:  # Assuming a reasonable weight range
                return weight
            else:
                print("Invalid weight. Please enter a valid weight between 1 and 500.")
        except ValueError:
            print("Invalid input. Please enter a valid weight as a whole number.")

# Function to validate and get a valid heart rate input from the user
def get_heart_rate_input():
    while True:
        try:
            heart_rate = int(input("Enter heart rate: "))
            if 1 <= heart_rate <= 250:  # Assuming a reasonable heart rate range
                return heart_rate
            else:
                print("Invalid heart rate. Please enter a valid heart rate between 1 and 250.")
        except ValueError:
            print("Invalid input. Please enter a valid heart rate as a whole number.")

# Function to validate and get a valid workout duration input from the user
def get_workout_duration_input():
    while True:
        try:
            duration = int(input("Enter duration of workout in hours: "))
            if 1 <= duration <= 24:  # Assuming a reasonable workout duration range
                return duration
            else:
                print("Invalid duration. Please enter a valid duration between 1 and 24 hours.")
        except ValueError:
            print("Invalid input. Please enter a valid duration as a whole number.")

# Function to calculate calories burnt during a workout
def calculate_calories_burnt(gender, age, weight, heart_rate, time):
    if gender == "male":
        calories = ((age * 0.2017) + (weight * 0.09036) + (heart_rate * 0.6309) - 55.0969) * time / 4.184
    elif gender == "female":
        calories = ((age * 0.074) + (weight * 0.05741) + (heart_rate * 0.4472) - 20.4022) * time / 4.184
    else:
        return "Invalid gender input, please enter 'male' or 'female'."

    return calories

# Get user inputs with validation
gender = get_gender_input()
age = get_age_input()
weight = get_weight_input()
heart_rate = get_heart_rate_input()
time = get_workout_duration_input()

# Calculate calories burnt
burned_cals = calculate_calories_burnt(gender, age, weight, heart_rate, time)

# Display the result
if isinstance(burned_cals, str):
    print(burned_cals)  # Print the error message
else:
    print("You burned {:.2f} calories during your workout.".format(burned_cals))
