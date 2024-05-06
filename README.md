class Student:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname
        self.grades = {}

    def add_grade(self, course, grade):
        if course in self.grades:
            self.grades[course].append(grade)
        else:
            self.grades[course] = [grade]

    def average_grade(self, course):
        if course in self.grades:
            return sum(self.grades[course]) / len(self.grades[course])
        else:
            return 0

class Lecturer:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname
        self.grades = {}

    def add_grade(self, course, grade):
        if course in self.grades:
            self.grades[course].append(grade)
        else:
            self.grades[course] = [grade]

    def average_grade(self, course):
        if course in self.grades:
            return sum(self.grades[course]) / len(self.grades[course])
        else:
            return 0

def average_grade_students(students, course):
    total_grades = []
    for student in students:
        total_grades.extend(student.grades.get(course, []))
    if total_grades:
        return sum(total_grades) / len(total_grades)
    else:
        return 0

def average_grade_lecturers(lecturers, course):
    total_grades = []
    for lecturer in lecturers:
        total_grades.extend(lecturer.grades.get(course, []))
    if total_grades:
        return sum(total_grades) / len(total_grades)
    else:
        return 0

# Создаем экземпляры студентов
student1 = Student("John", "Doe")
student2 = Student("Jane", "Smith")

# Создаем экземпляры лекторов
lecturer1 = Lecturer("Dr.", "Smith")
lecturer2 = Lecturer("Prof.", "Johnson")

# Добавляем оценки студентам
student1.add_grade("Python", 8)
student1.add_grade("Python", 9)
student2.add_grade("Python", 7)

# Добавляем оценки лекторам
lecturer1.add_grade("Python", 8)
lecturer1.add_grade("Python", 9)
lecturer2.add_grade("Python", 7)

# Вызываем методы для подсчета средней оценки
print(f"Average grade for students in Python course: {average_grade_students([student1, student2], 'Python')}")
print(f"Average grade for lecturers in Python course: {average_grade_lecturers([lecturer1, lecturer2], 'Python')}")