import tkinter as tk
import random

questions = [
    {"question": "What color is the sky on a clear day?", "options": ["Blue", "Green", "Red", "Yellow"], "answer": "Blue"},
    {"question": "What color do you get when you mix red and yellow?", "options": ["Orange", "Purple", "Brown", "Pink"], "answer": "Orange"},
    {"question": "What color symbolizes nature and life?", "options": ["Red", "Blue", "Green", "Black"], "answer": "Green"},
    {"question": "Which color is often associated with royalty?", "options": ["Purple", "White", "Grey", "Orange"], "answer": "Purple"},
    {"question": "What color are bananas?", "options": ["Blue", "Yellow", "Green", "Brown"], "answer": "Yellow"},
    {"question": "Which color represents purity?", "options": ["Black", "White", "Red", "Gold"], "answer": "White"},
    {"question": "What color is made by mixing red and blue?", "options": ["Pink", "Purple", "Orange", "Green"], "answer": "Purple"},
    {"question": "What color is the grass?", "options": ["Green", "Yellow", "Brown", "Black"], "answer": "Green"},
    {"question": "Which color is often used for danger signs?", "options": ["Red", "Blue", "Yellow", "Green"], "answer": "Red"},
    {"question": "What color do you get when you mix blue and yellow?", "options": ["Green", "Purple", "Red", "Pink"], "answer": "Green"},
    {"question": "What color is a stop sign?", "options": ["Red", "Blue", "Yellow", "Green"], "answer": "Red"},
    {"question": "What color is an emerald?", "options": ["Green", "Blue", "Yellow", "Purple"], "answer": "Green"},
    {"question": "Which color is a mix of black and white?", "options": ["Grey", "Brown", "Pink", "Blue"], "answer": "Grey"},
    {"question": "Which color symbolizes love?", "options": ["Red", "Blue", "Green", "Yellow"], "answer": "Red"},
    {"question": "What color do you get when you mix white and red?", "options": ["Pink", "Purple", "Orange", "Brown"], "answer": "Pink"},
    {"question": "Which color is used for peace?", "options": ["White", "Black", "Red", "Blue"], "answer": "White"},
    {"question": "What color are oranges?", "options": ["Orange", "Red", "Yellow", "Pink"], "answer": "Orange"},
    {"question": "Which color represents energy and passion?", "options": ["Red", "Blue", "Grey", "Brown"], "answer": "Red"},
    {"question": "What color is the ocean?", "options": ["Blue", "Green", "Brown", "Grey"], "answer": "Blue"},
    {"question": "What color is the sun?", "options": ["Yellow", "Red", "Orange", "White"], "answer": "Yellow"}
]

random.shuffle(questions)
score = 0
current_q = 0
total_q = len(questions)

def load_question():
    global current_q
    frame.config(bg=random.choice(["#FDE68A", "#DBEAFE", "#FECACA", "#D1FAE5", "#E0F2FE"]))
    q = questions[current_q]
    question_label.config(text=f"Q{current_q + 1} of {total_q}: {q['question']}")
    for i in range(4):
        options[i].config(text=q['options'][i], value=q['options'][i], state="normal")
    selected_option.set("")
    result_label.config(text="", bg=frame.cget("bg"))
    submit_btn.config(state="normal")
    next_btn.pack_forget()

def show_message(text, color):
    result_label.config(text=text, bg=color)
    root.after(300, lambda: result_label.config(bg=frame.cget("bg")))

def check_answer():
    global current_q, score
    selected = selected_option.get()
    if selected == "":
        show_message("Please choose an option!", "#FDE68A")
        return
    for opt in options:
        opt.config(state="disabled")
    submit_btn.config(state="disabled")
    if selected == questions[current_q]['answer']:
        score += 1
        show_message("Correct!", "#A7F3D0")
    else:
        show_message(f"Wrong! Answer: {questions[current_q]['answer']}", "#FCA5A5")
    next_btn.pack(pady=10)
    score_label.config(text=f"Score: {score}/{total_q}")

def next_question():
    global current_q
    current_q += 1
    if current_q < len(questions):
        load_question()
    else:
        show_result()

def show_result():
    for widget in frame.winfo_children():
        widget.destroy()
    percentage = int((score / total_q) * 100)
    if percentage >= 80:
        message = "Excellent!"
    elif percentage >= 50:
        message = "Good!"
    else:
        message = "Try Again!"
    result_text = f"Quiz Over!\nYour Score: {score}/{total_q}\nPercentage: {percentage}%\n{message}"
    result = tk.Label(frame, text=result_text, font=('Arial', 18, 'bold'), bg="#E0F2FE", fg="#1E3A8A")
    result.pack(pady=40)
    tk.Button(frame, text="Play Again", font=('Arial', 14), bg="#60A5FA", command=restart_game).pack(pady=20)

def restart_game():
    global score, current_q
    score = 0
    current_q = 0
    random.shuffle(questions)
    for widget in frame.winfo_children():
        widget.destroy()
    setup_quiz()

def setup_quiz():
    frame.config(bg="#E0F2FE")
    question_label.pack(pady=25)
    for opt in options:
        opt.pack(anchor='w', padx=60)
    submit_btn.pack(pady=10)
    result_label.pack(pady=10)
    score_label.pack(pady=5)
    load_question()

root = tk.Tk()
root.title("Color Quiz Game")
root.geometry("600x450")
root.config(bg="#E0F2FE")

frame = tk.Frame(root, bg="#E0F2FE")
frame.pack(expand=True, fill='both')

question_label = tk.Label(frame, text="", font=('Arial', 17, 'bold'), bg="#E0F2FE", fg="#111827")
selected_option = tk.StringVar()

options = [tk.Radiobutton(frame, text="", variable=selected_option, value="", font=('Arial', 14),
                          bg="#E0F2FE", anchor='w', selectcolor="#BFDBFE") for _ in range(4)]

submit_btn = tk.Button(frame, text="Submit", font=('Arial', 14), bg="#93C5FD", command=check_answer)
next_btn = tk.Button(frame, text="Next Question", font=('Arial', 14), bg="#60A5FA", command=next_question)
result_label = tk.Label(frame, text="", font=('Arial', 14, 'bold'), bg="#E0F2FE", fg="#111827")
score_label = tk.Label(frame, text=f"Score: 0/{total_q}", font=('Arial', 12, 'bold'), bg="#E0F2FE", fg="#1E3A8A")

setup_quiz()
root.mainloop()
