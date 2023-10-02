import java.util.Date;

public class BankAccount implements Cloneable {

    private int accountNumber;
    private int balance;
    private Date createDate;

    // constructor for creating a bank account
    public BankAccount(int accountNumber, int balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
        this.createDate = new java.util.Date();
    }

    // deposit money
    public int deposit(int amount) {
        balance = balance + amount;
        return balance;
    }

    // withdraw money
    public int withdraw(int amount) throws Exception {
        if (amount < 0)
            throw new Exception("Amount cannot be negative");
        balance = balance - amount;
        return balance;
    }

    @Override
    public Object clone() {
        try {
            // shallow copy
            BankAccount bankClone = (BankAccount) super.clone();

            // deep copy on createDate
            bankClone.createDate = (java.util.Date) (createDate.clone());

            return bankClone;
        } catch (CloneNotSupportedException ex) {
            return null;
        }
    }

    public static void main(String[] args) {
        // creating bank account object and cloning so that the second object is equal to the first
        BankAccount bank1 = new BankAccount(757, 1000);
        BankAccount bank2 = (BankAccount) bank1.clone();

        // print statement
        System.out.println("True: " + bank1 + " is equivalent to " + bank2);
    }
}
