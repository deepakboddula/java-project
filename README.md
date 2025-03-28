# java-project Task -1. ATM INTERFACE

import java.util.Scanner;

class ATM {
    private static final String CORRECT_PIN = "1234";  // Default PIN for simplicity
    private static double balance = 10000.00;         // Initial balance

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // User Authentication
        if (authenticateUser(scanner)) {
            displayMenu(scanner);
        } else {
            System.out.println("Authentication failed. Exiting...");
        }

        scanner.close();
    }

    // Authenticate User with Card and PIN
    private static boolean authenticateUser(Scanner scanner) {
        System.out.print("Enter Card Number (dummy for now): ");
        String cardNumber = scanner.nextLine();  // In a real system, this would be used to authenticate
        
        System.out.print("Enter PIN: ");
        String pin = scanner.nextLine();
        
        return pin.equals(CORRECT_PIN);
    }

    // Display transaction menu
    private static void displayMenu(Scanner scanner) {
        int choice;
        do {
            System.out.println("\nATM Menu:");
            System.out.println("1. Balance Inquiry");
            System.out.println("2. Cash Withdrawal");
            System.out.println("3. Cash Deposit");
            System.out.println("4. Funds Transfer");
            System.out.println("5. Change PIN");
            System.out.println("6. Exit");
            System.out.print("Enter choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    checkBalance();
                    break;
                case 2:
                    cashWithdrawal(scanner);
                    break;
                case 3:
                    cashDeposit(scanner);
                    break;
                case 4:
                    fundsTransfer(scanner);
                    break;
                case 5:
                    changePIN(scanner);
                    break;
                case 6:
                    System.out.println("Thank you for using ATM. Exiting...");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 6);
    }

    // Check Account Balance
    private static void checkBalance() {
        System.out.println("Your current balance is: $" + balance);
    }

    // Cash Withdrawal
    private static void cashWithdrawal(Scanner scanner) {
        System.out.print("Enter amount to withdraw: $");
        double amount = scanner.nextDouble();
        
        if (amount > balance) {
            System.out.println("Insufficient funds. Transaction denied.");
        } else {
            balance -= amount;
            System.out.println("You have withdrawn $" + amount);
            printReceipt("Withdrawal", amount);
        }
    }

    // Cash Deposit
    private static void cashDeposit(Scanner scanner) {
        System.out.print("Enter amount to deposit: $");
        double amount = scanner.nextDouble();
        
        balance += amount;
        System.out.println("You have deposited $" + amount);
        printReceipt("Deposit", amount);
    }

    // Funds Transfer (This example assumes transfer to a dummy account)
    private static void fundsTransfer(Scanner scanner) {
        System.out.print("Enter transfer amount: $");
        double amount = scanner.nextDouble();
        
        if (amount > balance) {
            System.out.println("Insufficient funds. Transfer failed.");
        } else {
            balance -= amount;
            System.out.println("Transferred $" + amount + " to the account.");
            printReceipt("Funds Transfer", amount);
        }
    }

    // Change PIN (Simple change process)
    private static void changePIN(Scanner scanner) {
        System.out.print("Enter new PIN: ");
        String newPIN = scanner.nextLine();
        
        // For security purposes, in a real system, this should involve more validation.
        System.out.println("PIN changed successfully.");
    }

    // Print Transaction Receipt
    private static void printReceipt(String transactionType, double amount) {
        System.out.println("\nReceipt:");
        System.out.println("Transaction Type: " + transactionType);
        System.out.println("Amount: $" + amount);
        System.out.println("Remaining Balance: $" + balance);
        System.out.println("-----------------------------");
    }
}




#TASK-2 ELECTRICITY BILL MANAGEMENT SYSTEM 

import java.util.Scanner;

public class ElectricityBillManagement {

    public static void main(String[] args) {
        // Create Scanner object for input
        Scanner scanner = new Scanner(System.in);
        
        // Input for user details
        System.out.print("Enter the customer name: ");
        String customerName = scanner.nextLine();
        
        System.out.print("Enter the number of units consumed: ");
        double unitsConsumed = scanner.nextDouble();
        
        // Calculate bill based on units consumed
        double ratePerUnit = 5.0; // Example rate per unit
        double billAmount = unitsConsumed * ratePerUnit;
        
        // Display the bill
        System.out.println("\nElectricity Bill for " + customerName);
        System.out.println("Units Consumed: " + unitsConsumed);
        System.out.println("Rate per Unit: " + ratePerUnit);
        System.out.println("Total Bill Amount: " + billAmount);
        
        scanner.close(); // Close the scanner
    }
}






#TASK-3 DEVELOP A CURRENCY CONVERTER 


import java.util.Scanner;

public class CurrencyConverter {

    public static void main(String[] args) {
        // Create Scanner object for input
        Scanner scanner = new Scanner(System.in);

        // Predefined exchange rates
        double usdToEur = 0.85;
        double usdToGbp = 0.75;
        double usdToInr = 74.0;
        
        System.out.println("Welcome to the Currency Converter!");
        System.out.print("Enter the amount in USD: ");
        double amountInUSD = scanner.nextDouble();
        
        System.out.println("Select the target currency:");
        System.out.println("1. EUR (Euro)");
        System.out.println("2. GBP (British Pound)");
        System.out.println("3. INR (Indian Rupee)");
        
        System.out.print("Enter your choice (1/2/3): ");
        int choice = scanner.nextInt();
        
        double convertedAmount = 0.0;
        
        // Perform conversion based on user's choice
        switch(choice) {
            case 1:
                convertedAmount = amountInUSD * usdToEur;
                System.out.println(amountInUSD + " USD = " + convertedAmount + " EUR");
                break;
            case 2:
                convertedAmount = amountInUSD * usdToGbp;
                System.out.println(amountInUSD + " USD = " + convertedAmount + " GBP");
                break;
            case 3:
                convertedAmount = amountInUSD * usdToInr;
                System.out.println(amountInUSD + " USD = " + convertedAmount + " INR");
                break;
            default:
                System.out.println("Invalid choice. Please select a valid option.");
        }

        scanner.close(); // Close the scanner
    }
}


