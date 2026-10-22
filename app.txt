
def calculate average(marks):
    if not marks:
        raise Value Error("Marks cannot be empty")
    return sum(marks) / Len(marks)


if __name__ == "__main__":
    marks = [80, 75, 90, 85, 70]
    average = calculate average(marks)

    print("Student Management System")
    print("Marks:", marks)
    print("Average:", average)
