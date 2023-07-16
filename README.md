import tkinter as tk
from tkinter import messagebox

class BakeryOrder:
    def __init__(self, master):
        self.master = master
        master.title("T&N Bakery")

        # Create input labels and entry boxes
        self.cupcake_lbl = tk.Label(master, text="Cupcake ($7.99)")
        self.cupcake_ent = tk.Entry(master)
        self.cookie_lbl = tk.Label(master, text="Cookie ($3.99)")
        self.cookie_ent = tk.Entry(master)
        self.cake_lbl = tk.Label(master, text="Cake ($17.99)")
        self.cake_ent = tk.Entry(master)
        self.cake_pop_lbl = tk.Label(master, text="Cake Pop ($1.99)")
        self.cake_pop_ent = tk.Entry(master)
        self.brownie_lbl = tk.Label(master, text="Brownie ($5.99)")
        self.brownie_ent = tk.Entry(master)
        self.brookie_lbl = tk.Label(master, text="Brookie ($6.99)")
        self.brookie_ent = tk.Entry(master)

        # Create order button
        self.order_btn = tk.Button(master, text="Place Order", command=self.calculate_total)

        # Create exit button
        self.exit_btn = tk.Button(master, text="Exit", command=master.quit)

        # Pack labels, entry boxes and buttons to the form
        self.cupcake_lbl.pack()
        self.cupcake_ent.pack()
        self.cookie_lbl.pack()
        self.cookie_ent.pack()
        self.cake_lbl.pack()
        self.cake_ent.pack()
        self.cake_pop_lbl.pack()
        self.cake_pop_ent.pack()
        self.brownie_lbl.pack()
        self.brownie_ent.pack()
        self.brookie_lbl.pack()
        self.brookie_ent.pack()
        self.order_btn.pack()
        self.exit_btn.pack()

    def calculate_total(self):
        try:
            # Get input values and calculate total price
            cupcake = int(self.cupcake_ent.get())
            cookie = int(self.cookie_ent.get())
            cake = int(self.cake_ent.get())
            cake_pop = int(self.cake_pop_ent.get())
            brownie = int(self.brownie_ent.get())
            brookie = int(self.brookie_ent.get())

            total_price = (cupcake + cookie + cake) * 8.99 + \
                          (cake_pop + brownie + brookie) * 1.99
            total_price *= 1.07 # Add 7% sales tax

            # Display total price in a message box
            messagebox.showinfo("Total Price", f"Your total bill is ${total_price:.2f}")
        except ValueError:
            # Display error message if input is invalid
            messagebox.showerror("Invalid Input", "Please enter a valid integer for each item.")

# Create main window
root = tk.Tk()

# Create bakery order form
order_form = BakeryOrder(root)

# Run main loop
root.mainloop()
