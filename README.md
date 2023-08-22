# import java.util.ArrayList;
import java.util.Scanner;

class Contributor {
    String id;
    String emailId;
    String name;
    String password;

    void input() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter ID: ");
        id = scanner.nextLine();
        System.out.print("Enter Email ID: ");
        emailId = scanner.nextLine();
        System.out.print("Enter Name: ");
        name = scanner.nextLine();
        System.out.print("Enter Password: ");
        password = scanner.nextLine();
    }

    void print() {
        System.out.println("ID: " + id);
        System.out.println("Email ID: " + emailId);
        System.out.println("Name: " + name);
        System.out.println("Password: " + password);
    }
}

public class Main {
    public static void main(String[] args) {
        ArrayList<Contributor> contributors = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nMenu:");
            System.out.println("1. Add a new Contributor");
            System.out.println("2. Print the Contributor");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume the newline

            switch (choice) {
                case 1:
                    Contributor contributor = new Contributor();
                    contributor.input();
                    contributors.add(contributor);
                    System.out.println("Contributor added.");
                    break;

                case 2:
                    if (contributors.isEmpty()) {
                        System.out.println("No contributors to print.");
                    } else {
                        System.out.println("\nSelect a Contributor:");
                        for (int i = 0; i < contributors.size(); i++) {
                            System.out.println((i + 1) + ". " + contributors.get(i).name);
                        }
                        System.out.print("Enter the index of the contributor: ");
                        int contributorIdx = scanner.nextInt();
                        if (contributorIdx >= 1 && contributorIdx <= contributors.size()) {
                            contributors.get(contributorIdx - 1).print();
                        } else {
                            System.out.println("Invalid index.");
                        }
                    }
                    break;

                case 3:
                    System.out.println("Exiting the program.");
                    System.exit(0);
                    break;

                default:
                    System.out.println("Invalid choice. Please select again.");
            }
        }
    }
}
