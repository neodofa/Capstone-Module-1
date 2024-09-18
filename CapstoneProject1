# CAPSTONE PROJECT

import os
from datetime import datetime

# STUDENT DATA
student_data = {
    1: {'SID': '202401',
        'Name': 'Ezra Komar',
        'DOB': '03/03/2000',
        'Class': '9A',
        'Subject': 'Math',
        'Score': 98},
    2: {'SID': '202402',
        'Name': 'Randall Mamat',
        'DOB': '21/06/2000',
        'Class': '9D',
        'Subject': 'Art',
        'Score': 87},
    3: {'SID': '202403',
        'Name': 'Rafif Saliman',
        'DOB': '21/01/2000',
        'Class': '9C',
        'Subject': 'Biology',
        'Score': 93},
    4: {'SID': '202404',
        'Name': 'Nima Yono',
        'DOB': '25/08/2000',
        'Class': '9C',
        'Subject': 'Business',
        'Score': 82},
    5: {'SID': '202405',
        'Name': 'Barri Pa Ri',
        'DOB': '20/09/2000',
        'Class': '9C',
        'Subject': 'Computer',
        'Score': 100}
}

# LIST OF VALID CLASSES
grade_list = ['9A', '9B', '9C', '9D']

# MAIN MENU
menu_list = {
    'main_menu': {
        1: 'View students',
        2: 'Add student',
        3: 'Update student information',
        4: 'Delete student',
        0: 'Exit'
    }
}

# CLEAR CONSOLE SCREEN
def clear_screen():
    if os.name == 'posix':
        os.system('clear')
    else:
        os.system('cls')

# FUNCTION TO VALIDATE STUDENT'S CLASS
def validate_class(class_input):
    if class_input in grade_list:
        return True
    else:
        print(f"Invalid class. Please choose from: {', '.join(grade_list)}")
        return False

# FUNCTION TO DISPLAY MENU
def display_menu(menu_name):
    print("\n=== Mentari School Student Management System ===")
    for key, value in menu_list[menu_name].items():
        print(f"{key}. {value}")
    
    while True:
        try:
            menu_input = int(input("\nPlease select a menu option: "))
            return menu_input
        except ValueError:
            print("Invalid input! Please enter a number.")

# FUNCTION TO VIEW STUDENTS
def view_students():
    clear_screen()
    print("\n--- Student List ---")
    print(f"{'ID':<5} {'SID':<10} {'Name':<20} {'Class':<6} {'Subject':<10} {'Score':<5}")
    print("-" * 60)
    for student_id, student in student_data.items():
        print(f"{student_id:<5} {student['SID']:<10} {student['Name']:<20} {student['Class']:<6} {student['Subject']:<10} {student['Score']:<5}")
    
    return_to_menu()

# FUNCTION TO VALIDATE STUDENT SCORE
def validate_score(score_input):
    try:
        score = int(score_input)
        if 0 <= score <= 100:
            return True, score
        else:
            print("Score must be between 0 and 100.")
            return False, None
    except ValueError:
        print("Invalid input! Please enter a valid number (0-100) for the score.")
        return False, None
    
# FUNCTION TO VALIDATE DOB
def validate_dob(dob_input):
    try:
        # TRY TO PARSE THE DATE USING THE EXPECTED FORMAT
        dob = datetime.strptime(dob_input, "%d/%m/%Y")
        # OPTIONALLY, CHECK IF THE DATE IS NOT IN THE FUTURE
        if dob > datetime.now():
            print("Date of birth cannot be in the future.")
            return False, None
        return True, dob_input
    except ValueError:
        # IF THE DATE IS NOT IN THE CORRECT FORMAT, RAISE AN ERROR
        print("Invalid date format! Please enter in the format dd/mm/yyyy.")
        return False, None

# FUNCTION TO VALIDATE STUDENT ID
def validate_student_id(sid):
    if len(sid) != 6 or not sid.isdigit():
        print("Student ID must be a 6-digit number.")
        return False
    for student in student_data.values():
        if student['SID'] == sid:
            print("Student ID already exists! Please enter a unique ID.")
            return False
    return True
    
# FUNCTION TO ADD A NEW STUDENT
def add_student():
    clear_screen()
    print("\n--- Add a New Student ---")
    new_id = max(student_data.keys()) + 1
    
    # VALIDATE STUDENT ID
    while True:
        sid = input("Enter Student ID (e.g., 202406): ")
        if validate_student_id(sid):
            break
    
    name = input("Enter Name: ")
    
    # VALIDATE DATE OF BIRTH
    while True:
        dob_input = input("Enter Date of Birth (dd/mm/yyyy): ")
        valid, dob = validate_dob(dob_input)
        if valid:
            break
    
    # VALIDATING CLASS
    while True:
        class_name = input("Enter Class (e.g., 9A): ")
        if validate_class(class_name):
            break
    
    subject = input("Enter Subject (e.g., Math, Art, Biology, etc.): ")
    
    # VALIDATING SCORE
    while True:
        score_input = input("Enter Score (0-100): ")
        valid, score = validate_score(score_input)
        if valid:
            break
    
    student_data[new_id] = {'SID': sid, 'Name': name, 'DOB': dob, 'Class': class_name, 'Subject': subject, 'Score': score}
    print("\nStudent added successfully!")
    
    return_to_menu()

# FUNCTION TO UPDATE STUDENT INFORMATION
def update_student():
    clear_screen()
    print("\n--- Update Student Information ---")
    
    # ASK FOR STUDENT ID
    sid = input("\nEnter the Student ID to update: ")

    # SEARCH FOR STUDENT BY SID
    for student_id, student in student_data.items():
        if student['SID'] == sid:
            print("\nLeave blank to skip updating that field.")

            # VALIDATE NAME
            name = input(f"New Name (current: {student['Name']}): ")
            if name:
                student['Name'] = name

            # VALIDATE DATE OF BIRTH
            while True:
                dob_input = input(f"New Date of Birth (current: {student['DOB']}), enter in format dd/mm/yyyy: ")
                if dob_input == "":
                    break
                valid, dob = validate_dob(dob_input)
                if valid:
                    student['DOB'] = dob
                    break

            # VALIDATE CLASS (GRADE)
            while True:
                class_name = input(f"New Class (current: {student['Class']}): ")
                if class_name == "":
                    break
                if validate_class(class_name):
                    student['Class'] = class_name
                    break

            # VALIDATE SUBJECT
            subject = input(f"New Subject (current: {student['Subject']}): ")
            if subject:
                student['Subject'] = subject

            # VALIDATE SCORE
            while True:
                score_input = input(f"New Score (current: {student['Score']}), must be between 0-100: ")
                if score_input == "":
                    break
                valid, score = validate_score(score_input)
                if valid:
                    student['Score'] = score
                    break

            print("\nStudent data updated successfully!")
            return_to_menu()
            return

    print("\nStudent not found.")
    return_to_menu()

# FUNCTION TO DELETE STUDENT
def delete_student():
    clear_screen()
    print("\n--- Delete Student ---")

    # ASK FOR STUDENT ID TO DELETE
    sid = input("\nEnter the Student ID to delete: ")

    # SEARCH FOR STUDENT BY SID
    for student_id, student in list(student_data.items()):
        if student['SID'] == sid:
            del student_data[student_id]
            print("\nStudent deleted successfully!")
            return_to_menu()
            return

    print("\nStudent not found.")
    return_to_menu()

# FUNCTION TO RETURN TO MAIN MENU
def return_to_menu():
    while True:
        choice = input("\nPress 9 to return to the main menu: ")
        if choice == '9':
            break
        else:
            print("Invalid choice! Please press 9 to return to the main menu.")

# MAIN LOOP OF THE PROGRAM
def main():
    while True:
        clear_screen()
        user_choice = display_menu('main_menu')
        
        if user_choice == 1:
            view_students()
        elif user_choice == 2:
            add_student()
        elif user_choice == 3:
            update_student()
        elif user_choice == 4:
            delete_student()
        elif user_choice == 0:
            clear_screen()
            print("Thank you, goodbye!")
            break
        else:
            print("Invalid choice, please try again.")
            return_to_menu()

# RUN THE PROGRAM
main()
