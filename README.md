# Seren

import tkinter as tk
from tkinter import messagebox

class MentalHealthTracker:
    def __init__(self, root):
        self.root = root
        self.root.title("Mental Health Tracker")

        # Create input fields
        self.emotions_label = tk.Label(root, text="Emotions (separate with commas):")
        self.emotions_label.pack()
        self.emotions_entry = tk.Entry(root, width=50)
        self.emotions_entry.pack()

        self.symptoms_label = tk.Label(root, text="Symptoms (separate with commas):")
        self.symptoms_label.pack()
        self.symptoms_entry = tk.Entry(root, width=50)
        self.symptoms_entry.pack()

        self.triggers_label = tk.Label(root, text="Triggers (separate with commas):")
        self.triggers_label.pack()
        self.triggers_entry = tk.Entry(root, width=50)
        self.triggers_entry.pack()

        # Create buttons
        self.submit_button = tk.Button(root, text="Submit", command=self.calculate_health_score)
        self.submit_button.pack()

        self.quit_button = tk.Button(root, text="Quit", command=root.quit)
        self.quit_button.pack()

    def calculate_health_score(self):
        emotions = self.emotions_entry.get().split(",")
        symptoms = self.symptoms_entry.get().split(",")
        triggers = self.triggers_entry.get().split(",")

        # Calculate health score based on input
        health_score = 100
        for emotion in emotions:
            if emotion.lower() in ["sad", "anxious", "depressed"]:
                health_score -= 10
        for symptom in symptoms:
            if symptom.lower() in ["headache", "fatigue", "insomnia"]:
                health_score -= 10
        for trigger in triggers:
            if trigger.lower() in ["stress", "anxiety", "fear"]:
                health_score -= 10

        # Provide solutions based on health score
        if health_score < 50:
            solution = "Seek professional help immediately."
        elif health_score < 80:
            solution = "Practice stress-reducing techniques, such as meditation or deep breathing."
        else:
            solution = "Continue practicing healthy habits and stress management techniques."

        # Display health score and solution
        messagebox.showinfo("Health Score", f"Your health score is: {health_score}\n{solution}")

if __name__ == "__main__":
    root = tk.Tk()
    app = MentalHealthTracker(root)
    root.mainloop()
