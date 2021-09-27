import tkinter
from tkinter import *
from tkinter import messagebox
import random
from random import shuffle

answer = ["Mumbai","Indore","kolkatta","India"]

question = []

for i in answer:
    words = list(i)
    shuffle(words)
    question.append(words)

num = random.randint(0,len(question)-1)

def initial():
    global question,num
    lb1.configure(text=question[num])

def answercheck():
    global question, num, answer
    userinput = e1.get()
    if userinput ==answer[num] :
        messagebox.showinfo('Success' , 'Your answer was correct!')
    else:
        messagebox.showinfo( 'Wrong' ,'Yuour answer was wrong!')
        e1.delete(0,END)


def reset():
    global question,num,answer
    num = random.randint(0,len(question)-1)
    lb1.configure(text=question[num])
    e1.delete(0,END)


window = Tk()
window.geometry("300x300")
window.configure(background='#02B290')
window.title("jumblebot")
window.iconbitmap(r"pikachu.ico")

lb1 = Label(window, font= 'times 20',bg='#50DBB4')
lb1.pack(pady=30,ipady=10,ipadx=10)

dollars = StringVar()
e1 = Entry(window, textvariable=dollars ,bg='#CAD5E2')
e1.pack(ipady=5, ipadx=5)

b1 = Button(window, text='CHECK' , width=20 ,command=answercheck , bg='#FF6666')
b1.pack(pady=40)

b2 = Button(window, text='RESET' , width=20 , command=reset ,bg='#B9345A')
b2.pack(pady=5)

initial()
window.mainloop()


