# Inventory-Management-System-
class Product:
    def __init__(self, product_id, name, price, quantity):
        self.product_id, self.name, self.price, self.quantity = product_id, name, price, quantity

    def update_quantity(self, amount): self.quantity += amount
    def update_price(self, new_price): self.price = new_price
    def __str__(self): return f"ID: {self.product_id}, Name: {self.name}, Price: {self.price}, Quantity: {self.quantity}"

class Inventory:
    def __init__(self): self.products = {}

    def add_product(self, product_id, name, price, quantity):
        if product_id in self.products:
            print("Product ID already exists.")
        else:
            self.products[product_id] = Product(product_id, name, price, quantity)
            print(f"Product {name} added.")

    def remove_product(self, product_id):
        print(f"Product {self.products.pop(product_id, 'not found')} removed.")

    def update_stock(self, product_id, quantity):
        self.products.get(product_id, print("Product not found")).update_quantity(quantity)

    def update_price(self, product_id, price):
        self.products.get(product_id, print("Product not found")).update_price(price)

    def view_product(self, product_id):
        print(self.products.get(product_id, "Product not found"))

    def view_all_products(self):
        print("\n".join(str(p) for p in self.products.values()) or "Inventory is empty.")
