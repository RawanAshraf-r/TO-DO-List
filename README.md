# TO-DO-List

import java.util.ArrayList;
import java.util.Scanner;

class Task {
private String title;
private boolean isDone;

public Task(String title) {
    this.title = title;
    this.isDone = false;
}

public String getTitle() {
    return title;
}

public boolean isDone() {
    return isDone;
}

public void markAsDone() {
    isDone = true;
}

@Override
public String toString() {
    return (isDone ? "[x] " : "[ ] ") + title;
}
}

public class ToDoListApp {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
ArrayList tasks = new ArrayList<>();
int choice;

    do {
        System.out.println("\nTo-Do List Menu:");
        System.out.println("1. Add task");
        System.out.println("2. View tasks");
        System.out.println("3. Mark task as done");
        System.out.println("4. Remove task");
        System.out.println("5. Exit");
        System.out.print("Enter your choice: ");

        while (!scanner.hasNextInt()) {
            System.out.print("Invalid input. Enter a number: ");
            scanner.next();
        }

        choice = scanner.nextInt();
        scanner.nextLine();

        switch (choice) {
            case 1:
                System.out.print("Enter task title: ");
                String title = scanner.nextLine();
                tasks.add(new Task(title));
                System.out.println("Task added.");
                break;
            case 2:
                if (tasks.isEmpty()) {
                    System.out.println("No tasks found.");
                } else {
                    for (int i = 0; i < tasks.size(); i++) {
                        System.out.println((i + 1) + ". " + tasks.get(i));
                    }
                }
                break;
            case 3:
                System.out.print("Enter task number to mark as done: ");
                int doneIndex = scanner.nextInt() - 1;
                if (doneIndex >= 0 && doneIndex < tasks.size()) {
                    tasks.get(doneIndex).markAsDone();
                    System.out.println("Task marked as done.");
                } else {
                    System.out.println("Invalid task number.");
                }
                break;
            case 4:
                System.out.print("Enter task number to remove: ");
                int removeIndex = scanner.nextInt() - 1;
                if (removeIndex >= 0 && removeIndex < tasks.size()) {
                    tasks.remove(removeIndex);
                    System.out.println("Task removed.");
                } else {
                    System.out.println("Invalid task number.");
                }
                break;
            case 5:
                System.out.println("Exiting To-Do List. Goodbye!");
                break;
            default:
                System.out.println("Invalid choice.");
        }

    } while (choice != 5);

    scanner.close();
}
}

