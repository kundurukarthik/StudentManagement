import java.util.ArrayList;
import java.util.List;
import java.util.Optional;

public class StudentManager {
    private List<Student> students;
    private int nextId;

    public StudentManager() {
        students = new ArrayList<>();
        nextId = 1; // Start IDs from 1
    }

    public void addStudent(String name, double grade) {
        Student student = new Student(nextId++, name, grade);
        students.add(student);
        System.out.println("Student added successfully.");
    }

    public void viewStudents() {
        if (students.isEmpty()) {
            System.out.println("No students available.");
            return;
        }

        System.out.println("Student List:");
        for (Student student : students) {
            System.out.println(student);
        }
    }

    public void deleteStudent(int id) {
        Optional<Student> studentToRemove = students.stream()
            .filter(student -> student.getId() == id)
            .findFirst();

        if (studentToRemove.isPresent()) {
            students.remove(studentToRemove.get());
            System.out.println("Student removed successfully.");
        } else {
            System.out.println("Student with ID " + id + " not found.");
        }
    }
}
