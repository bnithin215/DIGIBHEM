import java.util.Scanner;
import java.util.ArrayList;

class User {
    private String userId;
    private String pin;
    private double balance;
    private ArrayList<String> transactionHistory;

    public User(String userId, String pin, double initialBalance) {
        this.userId = userId;
        this.pin = pin;
        this.balance = initialBalance;
        this.transactionHistory = new ArrayList<>();
    }

    public String getUserId() {
        return userId;
    }

    public double getBalance() {
        return balance;
    }

    public boolean verifyPin(String enteredPin) {
        return pin.equals(enteredPin);
    }

    public void deposit(double amount) {
        balance += amount;
        transactionHistory.add("Deposit: +$" + amount);
    }

    public boolean withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            transactionHistory.add("Withdrawal: -$" + amount);
            return true;
        }
        return false;
    }

    public void transfer(User recipient, double amount) {
        if (withdraw(amount)) {
            recipient.deposit(amount);
            transactionHistory.add("Transfer: -$" + amount + " to " + recipient.getUserId());
        }
    }

    public ArrayList<String> getTransactionHistory() {
        return transactionHistory;
    }
}

public class ATMNprogram {
    public static void main(String[] args) {
        User user = new User("12345", "1234", 1000.0);

        Scanner scanner = new Scanner(System.in);
        String userId;
        String pin;

        System.out.println("Welcome to the ATM");
        System.out.print("Enter User ID: ");
        userId = scanner.nextLine();
        System.out.print("Enter PIN: ");
        pin = scanner.nextLine();

        if (user.verifyPin(pin) && userId.equals(user.getUserId())) {
            System.out.println("Login successful!");
            displayMainMenu(user);
        } else {
            System.out.println("Login failed. Please check your User ID and PIN.");
        }
    }

    public static void displayMainMenu(User user) {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("\nMain Menu:");
            System.out.println("1. Check Balance");
            System.out.println("2. Make a Deposit");
            System.out.println("3. Make a Withdrawal");
            System.out.println("4. Transfer Funds");
            System.out.println("5. View Transaction History");
            System.out.println("6. Quit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Balance: $" + user.getBalance());
                    break;
                case 2:
                    System.out.print("Enter deposit amount: $");
                    double depositAmount = scanner.nextDouble();
                    user.deposit(depositAmount);
                    System.out.println("Deposit successful. New balance: $" + user.getBalance());
                    break;
                case 3:
                    System.out.print("Enter withdrawal amount: $");
                    double withdrawalAmount = scanner.nextDouble();
                    if (user.withdraw(withdrawalAmount)) {
                        System.out.println("Withdrawal successful. New balance: $" + user.getBalance());
                    } else {
                        System.out.println("Insufficient funds.");
                    }
                    break;
                case 4:
                    System.out.print("Enter recipient's User ID: ");
                    String recipientUserId = scanner.next();
                    System.out.print("Enter transfer amount: $");
                    double transferAmount = scanner.nextDouble();
                    // Assuming you have a list of users and can find the recipient user by their User ID
                    // User recipient = findUserById(recipientUserId);
                    // user.transfer(recipient, transferAmount);
                    // Add logic to find the recipient user and complete the transfer.
                    break;
                case 5:
                    System.out.println("Transaction History:");
                    for (String transaction : user.getTransactionHistory()) {
                        System.out.println(transaction);
                    }
                    break;
                case 6:
                    System.out.println("Thank you for using the ATM. Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
