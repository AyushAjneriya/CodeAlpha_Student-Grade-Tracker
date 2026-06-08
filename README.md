# CodeAlpha_Student-Grade-Tracker
import java.util.ArrayList;
import java.util.Scanner;

class Student {
    String name;
    int marks;

    Student(String name, int marks) {
        this.name = name;
        this.marks = marks;
    }
}

public class StudentGradeTracker {

    static ArrayList<Student> students = new ArrayList<>();

    // Add Student
    public static void addStudent(String name, int marks) {
        students.add(new Student(name, marks));
    }

    // Calculate Average
    public static double calculateAverage() {
        if (students.isEmpty()) {
            return 0;
        }

        int sum = 0;

        for (Student s : students) {
            sum += s.marks;
        }

        return (double) sum / students.size();
    }

    // Find Highest Score
    public static int highestScore() {
        if (students.isEmpty()) {
            return 0;
        }

        int highest = students.get(0).marks;

        for (Student s : students) {
            if (s.marks > highest) {
                highest = s.marks;
            }
        }

        return highest;
    }

    
    public static int lowestScore() {
        if (students.isEmpty()) {
            return 0;
        }

        int lowest = students.get(0).marks;

        for (Student s : students) {
            if (s.marks < lowest) {
                lowest = s.marks;
            }
        }

        return lowest;
    }

    // Display Report
    public static void displayReport() {

        System.out.println("\n===== STUDENT REPORT =====");

        for (Student s : students) {
            System.out.println("Name : " + s.name +
                    " | Marks : " + s.marks);
        }

        System.out.println("\nTotal Students : " + students.size());
        System.out.println("Average Score  : " + calculateAverage());
        System.out.println("Highest Score  : " + highestScore());
        System.out.println("Lowest Score   : " + lowestScore());
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter Number of Students: ");
        int n = sc.nextInt();
        sc.nextLine();

        for (int i = 1; i <= n; i++) {

            System.out.println("\nStudent " + i);

            System.out.print("Enter Name: ");
            String name = sc.nextLine();

            System.out.print("Enter Marks: ");
            int marks = sc.nextInt();
            sc.nextLine();

            addStudent(name, marks);
        }

        displayReport();

        sc.close();
    }
}
