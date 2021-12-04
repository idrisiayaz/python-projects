from os import times
from tkinter import *

import json

element = json.load(open("wordbook.json"))
window = Tk()

def conversion():
    word = dollars.get()
    if word in element:
        t1.delete("0.1",END)
        return t1.insert(END, element[word])
    elif word.lower() in element:
        t1.delete("0.1",END)
        return t1.insert(END, element[word.lower()])
    elif word.upper() in element:
        t1.delete("0.1",END)
        return t1.insert(END, element[word.upper()])
    elif word.title() in element:
        t1.delete("0.1",END)
        return t1.insert(END, element[word.title()])
    else:
        t1.delete("0.1",END)
        return t1.insert(END,"sorry cant find word")
    
b1 = Button(window, text="SEARCH" ,command=conversion)
b1.grid(row=0,column=0)

dollars = StringVar()
e1 = Entry(window ,textvariable=dollars)
e1.grid(row=0,column=1)

t1 = Text(window , height=5 , width=60)
t1.grid(row=0,column=3)


window.mainloop()



