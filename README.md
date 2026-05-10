# CodeAlpha_Task 
import java.util.ArrayList;
import java.util.Scanner;

class Student {
    String name;
    double marks;

    //Constructor
    Student(String name, double marks) {
        this.name = name;
        this.marks = marks;
    }
}

public class StudentGradeTracker {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        System.out.print("Enter number of students: ");
        int n = sc.nextInt();
        sc.nextLine(); // consume newline

        // Input student details
        for (int i = 0; i < n; i++) {
            System.out.println("\nEnter details for Student " + (i + 1));

            System.out.print("Name: ");
            String name = sc.nextLine();

            System.out.print("Marks: ");
            double marks = sc.nextDouble();
            sc.nextLine();

            students.add(new Student(name, marks));
        }

        // Variables for calculations
        double total = 0;
        double highest = students.get(0).marks;
        double lowest = students.get(0).marks;

        String highestStudent = students.get(0).name;
        String lowestStudent = students.get(0).name;

        // Process data
        for (Student s : students) {
            total += s.marks;

            if (s.marks > highest) {
                highest = s.marks;
                highestStudent = s.name;
            }

            if (s.marks < lowest) {
                lowest = s.marks;
                lowestStudent = s.name;
            }
        }

        double average = total / students.size();

        // Display Summary Report
        System.out.println("\n===== STUDENT SUMMARY REPORT =====");

        for (Student s : students) {
            System.out.println("Name: " + s.name + " | Marks: " + s.marks);
        }

        System.out.println("\nAverage Marks: " + average);
        System.out.println("Highest Marks: " + highest + " (Student: " + highestStudent + ")");
        System.out.println("Lowest Marks: " + lowest + " (Student: " + lowestStudent + ")");

        sc.close();
    }
}
