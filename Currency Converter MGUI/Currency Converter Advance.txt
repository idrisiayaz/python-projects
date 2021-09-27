from tkinter import *
from tkinter import font

class CurrencyConverter:
    def __init__(self):
        window = Tk()
        window.title("Currency Converter")
        window.geometry("400x300")
        window.resizable(width=False,height=False)
        window.iconbitmap(r'C:\\Users\\idris\\python\\contacts\\icons\\ce.ico')


        bg = PhotoImage(file="C:\\Users\\idris\\python\\contacts\\icons\\bank.png")
        bglabel = Label(window,image=bg)
        bglabel.place(x=0,y=0)
        

        Label(window,font="helvetica 12 bold",text="Amount to convert").grid(row=1,column=1,sticky=W)
        Label(window,font="helvetica 12 bold",text="Conversion Rate   ").grid(row=2,column=1 , sticky=W)
        Label(window,font="helvetica 12 bold",text="Converted Amount").grid(row=3,column=1,sticky=W)

        self.ac = StringVar()
        Entry(window,textvariable=self.ac,justify=RIGHT).grid(row=1,column=2)
        self.cr = StringVar()
        Entry(window,textvariable=self.cr,justify=RIGHT).grid(row=2,column=2)
        self.ca = StringVar()
        lblConvertedAmount = Label(window,font="helvetica 12 bold",textvariable=self.ca,justify=RIGHT).grid(row=3,column=2,sticky=E)
   
        btconvert = Button(window,text="Convert",font="helvetica 12 bold",command=self.convertamount).grid(row=4,column=2,sticky=E)
        btclear = Button(window,text="Clear",font="helvetica 12 bold",command=self.delete).grid(row=4,column=6,padx=25,pady=25,sticky=E)

        window.mainloop()

    def convertamount(self):
        a = float(self.cr.get())
        convert = float(self.ac.get()) * a
        self.ca.set(format(convert,'10.2f'))

    def delete(self):
        self.ac.set("")
        self.cr.set("")
        self.ca.set("")

CurrencyConverter()