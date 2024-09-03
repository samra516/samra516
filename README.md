public class BankAccount {
    // Instance variable
    private String accountHolderName;
    private double balance;

    // Static variable
    private static int numberOfAccounts = 0;

    // Constructor
    public BankAccount(String accountHolderName, double initialBalance) {
        this.accountHolderName = accountHolderName;
        this.balance = initialBalance;
        numberOfAccounts++; // Increment the static variable
    }

    // Instance method
    public void deposit(double amount) {
        // Local variable
        double fee = 0.00; // Assume no fee for simplicity
        if (amount > 0) {
            balance += amount - fee;
            System.out.println("Deposited: $" + amount);
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    // Instance method
    public void withdraw(double amount) {
        // Local variable
        double fee = 1.00; // Assume a fee for withdrawal
        if (amount > 0 && amount + fee <= balance) {
            balance -= amount + fee;
            System.out.println("Withdrew: $" + amount);
        } else {
            System.out.println("Insufficient funds or invalid amount.");
        }
    }

    // Instance method
    public void printAccountDetails() {
        System.out.println("Account Holder: " + accountHolderName);
        System.out.println("Balance: $" + balance);
        System.out.println("Total Accounts: " + numberOfAccounts); // Access static variable
    }

    // Static method
    public static void printTotalAccounts() {
        System.out.println("Total Accounts: " + numberOfAccounts);
    }
    
    public static void main(String[] args) {
        BankAccount account1 = new BankAccount("Alice", 1000.00);
        BankAccount account2 = new BankAccount("Bob", 500.00);

        account1.deposit(200.00);
        account1.withdraw(150.00);
        account1.printAccountDetails();

        account2.deposit(100.00);
        account2.withdraw(50.00);
        account2.printAccountDetails();

        // Static method call
        BankAccount.printTotalAccounts();
    }
}
