# Inventory-Management-
A simple database to keep a track of the inventory
class Item:
    def __init__(self, name, quantity, price):
        self.name = name
        self.quantity = quantity
        self.price = price

    def __str__(self):
        return f"Item: {self.name}, Quantity: {self.quantity}, Price: {self.price}"
 class Inventory:
    def __init__(self):
        self.items = {}

    def add_item(self, name, quantity, price):
        if name in self.items:
            print("Item already exists. Use update_item to update the existing item.")
        else:
            self.items[name] = Item(name, quantity, price)
            print(f"Item {name} added to inventory.")

    def update_item(self, name, quantity, price):
        if name in self.items:
            self.items[name].quantity = quantity
            self.items[name].price = price
            print(f"Item {name} updated.")
        else:
            print("Item not found in inventory. Use add_item to add the new item.")

    def display_inventory(self):
        if not self.items:
            print("Inventory is empty.")
        else:
            for item in self.items.values():
                print(item)

    def remove_item(self, name):
        if name in self.items:
            del self.items[name]
            print(f"Item {name} removed from inventory.")
        else:
            print("Item not found in inventory.")
def main():
    inventory = Inventory()

    while True:
        print("\nInventory Management System")
        print("1. Add Item")
        print("2. Update Item")
        print("3. Display Inventory")
        print("4. Remove Item")
        print("5. Exit")
        
        choice = input("Enter your choice: ")

        if choice == '1':
            name = input("Enter item name: ")
            quantity = int(input("Enter item quantity: "))
            price = float(input("Enter item price: "))
            inventory.add_item(name, quantity, price)
        
        elif choice == '2':
            name = input("Enter item name: ")
            quantity = int(input("Enter item quantity: "))
            price = float(input("Enter item price: "))
            inventory.update_item(name, quantity, price)
        
        elif choice == '3':
            inventory.display_inventory()
        
        elif choice == '4':
            name = input("Enter item name to remove: ")
            inventory.remove_item(name)
        
        elif choice == '5':
            break
        
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()

