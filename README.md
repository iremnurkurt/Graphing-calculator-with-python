# Graphing-calculator-with-python
Graph calculator code for python
from tkinter import *

class Calculator:
    def __init__(self, master):
        self.master = master
        master.title("Graphing Calculator")

        # Screen
        self.screen = Text(master, state='disabled', width=50, height=10, background="black", foreground="white")
        self.screen.grid(row=0, column=0, columnspan=4, padx=5, pady=5)
        self.screen.configure(state='normal')
        self.equation = ''

        # Number and action buttons
        button_texts = [
            "7", "8", "9", "/",
            "4", "5", "6", "*",
            "1", "2", "3", "-",
            "0", ".", "C", "+"
        ]
        row = 1
        col = 0
        for button_text in button_texts:
            button = Button(master, text=button_text, width=5, height=2, command=lambda x=button_text:self.button_click(x))
            button.grid(row=row, column=col, padx=5, pady=5)
            col += 1
            if col > 3:
                col = 0
                row += 1

        # Equal and clear buttons
        equal_button = Button(master, text="=", width=5, height=2, command=self.calculate)
        equal_button.grid(row=5, column=2, padx=5, pady=5)

        clear_button = Button(master, text="AC", width=5, height=2, command=self.clear_screen)
        clear_button.grid(row=5, column=0, padx=5, pady=5)

    def button_click(self, text):
        self.equation += str(text)
        self.screen.delete('1.0', END)
        self.screen.insert(END, self.equation)

    def clear_screen(self):
        self.equation = ''
        self.screen.delete('1.0', END)

    def calculate(self):
        try:
            self.equation = str(eval(self.equation))
            self.screen.delete('1.0', END)
            self.screen.insert(END, self.equation)
        except:
            self.screen.delete('1.0', END)
            self.screen.insert(END, 'Error')

root = Tk()
my_gui = Calculator(root)
root.mainloop()


 

































