#Attendance-management-system
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class AttendanceManagementSystem {
    private Map<String, Boolean> attendance;

    public AttendanceManagementSystem() {
        attendance = new HashMap<>();
    }

    // Method to mark attendance
    public void markAttendance(String studentID, boolean present) {
        attendance.put(studentID, present);
    }

    // Method to display attendance
    public void displayAttendance() {
        System.out.println("Attendance:");
        for (Map.Entry<String, Boolean> entry : attendance.entrySet()) {
            System.out.println("Student ID: " + entry.getKey() + ", Present: " + entry.getValue());
        }
    }

    public static void main(String[] args) {
        AttendanceManagementSystem ams = new AttendanceManagementSystem();
        Scanner scanner = new Scanner(System.in);
        boolean running = true;

        while (running) {
            System.out.println("1. Mark Attendance");
            System.out.println("2. Display Attendance");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter student ID: ");
                    String studentID = scanner.nextLine();
                    System.out.print("Is the student present? (true/false): ");
                    boolean present = scanner.nextBoolean();
                    ams.markAttendance(studentID, present);
                    break;
                case 2:
                    ams.displayAttendance();
                    break;
                case 3:
                    running = false;
                    break;
                default:
                    System.out.println("Invalid choice.");
            }
        }

        scanner.close();
    }
}