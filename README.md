# Inventory-MS
I******Inventory Management System ********  This Program used to Demonstrate  Creating objects and demonstrating Encapsulation, Inheritance, and Polymorphism
Explanation:
•	JDBC Connection: Establishes a connection with the MySQL database.
•	CREATE TABLE Statement: Defines the Inventory table with:
o	id: Primary key.
o	item_name: Name of the inventory item.
o	quantity: Number of units available.
o	price: Cost of each unit.
o	supplier: Optional field for supplier information.
o	date_added: Timestamp for when the item was added.
What This Code Demonstrates
1.	Encapsulation → Private fields with getter/setter methods.
2.	Class & Object → InventoryItem and Transaction are classes, and transaction is an object.
3.	Inheritance → Transaction extends InventoryItem, inheriting its properties/methods.
4.	Polymorphism → The getItemDetails() method is overridden in the Transaction class.
5.	Constructors → Used to initialize objects properly.
 Organized Code Example
1. Base Class (InventoryItem)
java
package org.example;

public class InventoryItem {
    private int itemId;
    private String itemName;
    private double purchasePrice;
    private int quantity;

    // Constructor
    public InventoryItem(int itemId, String itemName, double purchasePrice, int quantity) {
        this.itemId = itemId;
        this.itemName = itemName;
        this.purchasePrice = purchasePrice;
        this.quantity = quantity;
    }

    // Encapsulation - Getters & Setters
    public int getItemId() {
        return itemId;
    }

    public void setItemId(int itemId) {
        this.itemId = itemId;
    }

    public String getItemName() {
        return itemName;
    }

    public void setItemName(String itemName) {
        this.itemName = itemName;
    }

    public double getPurchasePrice() {
        return purchasePrice;
    }

    public void setPurchasePrice(double purchasePrice) {
        this.purchasePrice = purchasePrice;
    }

    public int getQuantity() {
        return quantity;
    }

    public void setQuantity(int quantity) {
        this.quantity = quantity;
    }

    // Polymorphism - A method that can be overridden
    public String getItemDetails() {
        return "Item: " + itemName + ", Price: $" + purchasePrice + ", Quantity: " + quantity;
    }
}
2. Subclass (Transaction) - Implements Inheritance & Polymorphism
java
package org.example;

public class Transaction extends InventoryItem {
    private double sellingPrice;
    private int soldQuantity;
    private double tax;
    private double netProfit;

    // Constructor (Inheritance applied)
    public Transaction(int itemId, String itemName, double purchasePrice, int quantity,
                       double sellingPrice, int soldQuantity, double tax) {
        super(itemId, itemName, purchasePrice, quantity); // Call superclass constructor
        this.sellingPrice = sellingPrice;
        this.soldQuantity = soldQuantity;
        this.tax = tax;
        this.netProfit = calculateNetProfit();
    }

    // Encapsulation - Getters & Setters
    public double getSellingPrice() {
        return sellingPrice;
    }

    public void setSellingPrice(double sellingPrice) {
        this.sellingPrice = sellingPrice;
    }

    public int getSoldQuantity() {
        return soldQuantity;
    }

    public void setSoldQuantity(int soldQuantity) {
        this.soldQuantity = soldQuantity;
    }

    public double getTax() {
        return tax;
    }

    public void setTax(double tax) {
        this.tax = tax;
    }

    public double getNetProfit() {
        return netProfit;
    }

    // Polymorphism - Overriding `getItemDetails()`
    @Override
    public String getItemDetails() {
        return super.getItemDetails() + ", Sold Price: $" + sellingPrice +
                ", Sold Quantity: " + soldQuantity + ", Net Profit: $" + netProfit;
    }

    // Profit Calculation Method
    private double calculateNetProfit() {
        double totalRevenue = sellingPrice * soldQuantity;
        double totalCost = getPurchasePrice() * soldQuantity;
        return totalRevenue - totalCost - tax;
    }
}
3. Main Class (InventoryMain) - Demonstrates Object Creation
java
package org.example;

public class InventoryMain {
    public static void main(String[] args) {
         System.out.println("*******************************************************");
        System.out.println("******Inventory Management System ******** ");
        System.out.println("This Program used to Demonstrate \n"+"Creating objects and demonstrating Encapsulation, Inheritance, and Polymorphism");
        System.out.println("*******************************************************\n");
        Transaction transaction = new Transaction(1, "Laptop",10000, 8,4);

        System.out.println(transaction.getItemDetails()); // Polymorphism applied
    }

        }


What This Code Demonstrates
1.	Encapsulation → Private fields with getter/setter methods.
2.	Class & Object → InventoryItem and Transaction are classes, and transaction is an object.
3.	Inheritance → Transaction extends InventoryItem, inheriting its properties/methods.
4.	Polymorphism → The getItemDetails() method is overridden in the Transaction class.
5.	Constructors → Used to initialize objects properly.


