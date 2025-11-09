import tkinter as tk
from tkinter import messagebox

# List of questions, answers, and marks
quiz = [
    {"question": "Who was the founder of Sikhism?", "answer": "Guru Nanak Dev Ji", "marks": 1},
    {"question": "In which year was Guru Nanak Dev Ji born?", "answer": "1469", "marks": 1},
    {"question": "Which Guru compiled the Adi Granth, the holy scripture of Sikhs?", "answer": "Guru Arjan Dev Ji", "marks": 2},
    {"question": "What is the significance of Vaisakhi in Sikhism?", "answer": "Formation of Khalsa in 1699", "marks": 2},
    {"question": "Who was the 10th Sikh Guru?", "answer": "Guru Gobind Singh Ji", "marks": 1},
    {"question": "What are the five Ks of Sikhism?", "answer": "Kesh, Kangha, Kara, Kachera, Kirpan", "marks": 2},
    {"question": "Which battle is Guru Gobind Singh Ji famous for?", "answer": "Battle of Chamkaur", "marks": 2},
    {"question": "Who was the first Sikh martyr?", "answer": "Guru Arjan Dev Ji", "marks": 1},
    {"question": "Where is the Golden Temple located?", "answer": "Amritsar, Punjab, India", "marks": 1},
    {"question": "Which Guru introduced the concept of Langar?", "answer": "Guru Nanak Dev Ji", "marks": 1}
]

class SikhQuizApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Sikh History Quiz")
        self.root.geometry("600x300")
        self.current_question = 0
        self.score = 0

        # Question Label
        self.question_label = tk.Label(root, text="", wraplength=550, font=("Arial", 14))
        self.question_label.pack(pady=20)

        # Answer Entry
        self.answer_entry = tk.Entry(root, width=50)
        self.answer_entry.pack(pady=10)

        # Submit Button
        self.submit_btn = tk.Button(root, text="Submit Answer", command=self.check_answer)
        self.submit_btn.pack(pady=10)

        # Display the first question
        self.display_question()

    def display_question(self):
        if self.current_question < len(quiz):
            self.question_label.config(text=f"Q{self.current_question + 1}: {quiz[self.current_question]['question']}")
            self.answer_entry.delete(0, tk.END)
        else:
            messagebox.showinfo("Quiz Completed", f"You scored {self.score} out of {sum(q['marks'] for q in quiz)}")
            self.root.destroy()

    def check_answer(self):
        user_answer = self.answer_entry.get().strip()
        correct_answer = quiz[self.current_question]["answer"]

        if user_answer.lower() == correct_answer.lower():
            self.score += quiz[self.current_question]["marks"]
            messagebox.showinfo("Correct!", f"Correct! You earned {quiz[self.current_question]['marks']} marks.")
        else:
            messagebox.showerror("Wrong!", f"Wrong! The correct answer is: {correct_answer}\nMarks: {quiz[self.current_question]['marks']}")

        self.current_question += 1
        self.display_question()

# Run the GUI
if __name__ == "__main__":
    root = tk.Tk()
    app = SikhQuizApp(root)
    root.mainloop()
