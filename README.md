import tkinter as tk

# Constants
MIN_CAMPERS = 5
MAX_CAMPERS = 10

# Global variables
camp_details = []

# Functions
def add_camp():
    """Adds camp details to the list"""
    name = name_entry.get()
    location = location_entry.get()
    num_campers = int(num_campers_entry.get())
    weather = weather_entry.get()
    camp_details.append((name, location, num_campers, weather))
    update_display()

def delete_camp():
    """Deletes the most recent camp details from the list"""
    if len(camp_details) > 0:
        camp_details.pop()
        update_display()

def update_display():
    """Updates the display with the current camp details"""
    display.delete('1.0', tk.END)  # Clear the display
    for name, location, num_campers, weather in camp_details:
        display.insert(tk.END, f"{name} - {location} ({num_campers} campers) - {weather}\n")

# GUI
root = tk.Tk()
root.title("Sunshine Adventure Camp")

name_label = tk.Label(root, text="Leader Name:")
name_entry = tk.Entry(root)
location_label = tk.Label(root, text="Location:")
location_entry = tk.Entry(root)
num_campers_label = tk.Label(root, text="Number of Campers:")
num_campers_entry = tk.Entry(root)
weather_label = tk.Label(root, text="Weather:")
weather_entry = tk.Entry(root)

add_button = tk.Button(root, text="Add Camp", command=add_camp)
delete_button = tk.Button(root, text="Delete Camp", command=delete_camp)

display_label = tk.Label(root, text="Camp Details:")
display = tk.Text(root, height=10)

name_label.grid(row=0, column=0)
name_entry.grid(row=0, column=1)
location_label.grid(row=1, column=0)
location_entry.grid(row=1, column=1)
num_campers_label.grid(row=2, column=0)
num_campers_entry.grid(row=2, column=1)
weather_label.grid(row=3, column=0)
weather_entry.grid(row=3, column=1)

add_button.grid(row=4, column=0)
delete_button.grid(row=4, column=1)

display_label.grid(row=5, column=0)
display.grid(row=6, column=0, columnspan=2)

root.mainloop()
