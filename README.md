# some-dz-2
import tkinter as tk


score1 = 0
score2 = 0
WIN_SCORE = 10

def player1_click(event):
    global score1
    if score1 < WIN_SCORE and score2 < WIN_SCORE:
        score1 += 1
        label_p1.config(text=f"Гравець 1: {score1}")
        check_winner()

def player2_click(event):
    global score2
    if score1 < WIN_SCORE and score2 < WIN_SCORE:
        score2 += 1
        label_p2.config(text=f"Гравець 2: {score2}")
        check_winner()

def check_winner():
    if score1 == WIN_SCORE:
        result.config(text="🏆 Переміг Гравець 1!")
    elif score2 == WIN_SCORE:
        result.config(text="🏆 Переміг Гравець 2!")


root = tk.Tk()
root.title("Гра для двох")
root.geometry("500x300")


label_title = tk.Label(root, text="Хто швидше натискає?", font=("Arial", 20))
label_title.pack(pady=10)

label_p1 = tk.Label(root, text="Гравець 1: 0", font=("Arial", 16), fg="blue")
label_p1.pack()

label_p2 = tk.Label(root, text="Гравець 2: 0", font=("Arial", 16), fg="green")
label_p2.pack()

result = tk.Label(root, text="", font=("Arial", 18), fg="red")
result.pack(pady=10)

info = tk.Label(
    root,
    text="Гравець 1 — ліва кнопка миші\nГравець 2 — клавіша S",
    font=("Arial", 12)
)
info.pack()


root.bind("<Button-1>", player1_click)   # Ліва кнопка миші
root.bind("s", player2_click)             # Клавіша S
root.bind("S", player2_click)

root.mainloop()
