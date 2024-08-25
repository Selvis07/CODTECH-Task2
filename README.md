def get_grade_input():
    """Function to get grades from the user."""
    grades = []
    while True:
        try:
            grade = input("Enter a grade (or 'done' to finish): ")
            if grade.lower() == 'done':
                break
            grade = float(grade)
            if 0 <= grade <= 100:
                grades.append(grade)
            else:
                print("Please enter a grade between 0 and 100.")
        except ValueError:
            print("Invalid input. Please enter a numeric value or 'done' to finish.")
    return grades

def calculate_average(grades):
    """Function to calculate the average grade."""
    return sum(grades) / len(grades) if grades else 0

def determine_letter_grade(average):
    """Function to determine the letter grade based on the average."""
    if average >= 90:
        return 'A'
    elif average >= 80:
        return 'B'
    elif average >= 70:
        return 'C'
    elif average >= 60:
        return 'D'
    else:
        return 'F'

def calculate_gpa(average):
    """Function to calculate GPA based on the average grade."""
    if average >= 90:
        return 4.0
    elif average >= 80:
        return 3.0
    elif average >= 70:
        return 2.0
    elif average >= 60:
        return 1.0
    else:
        return 0.0

def display_results(average, letter_grade, gpa):
    """Function to display the results."""
    print("\n--- Results ---")
    print(f"Average Grade: {average:.2f}")
    print(f"Letter Grade: {letter_grade}")
    print(f"GPA: {gpa:.2f}")

def main():
    print("Welcome to the Student Grades Tracker!")
    
    grades = get_grade_input()
    if not grades:
        print("No grades were entered.")
        return

    average = calculate_average(grades)
    letter_grade = determine_letter_grade(average)
    gpa = calculate_gpa(average)

    display_results(average, letter_grade, gpa)

if __name__ == "__main__":
    main()
