from tkinter import *
from tkinter import font

class LoanCalculator:
    def __init__(self):
        window = Tk()
        window.geometry("500x375")
        window.resizable(height=False,width=False)
        window.title("Loan Calculator")
        window.iconbitmap(r'C:\\Users\\idris\\python\\contacts\\icons\\loan.ico')
        bgimage = PhotoImage(file="C:\\Users\\idris\\python\\contacts\\icons\\loans.png")
        bglbl = Label(window,image=bgimage)
        bglbl.place(x=0,y=0)
    
 
        Label(window,font="helvetica 12 bold",text="Annual Interest Rate :",bg="brown").grid(row=1,column=1,padx=10,pady=10,ipadx=20,ipady=0)
        Label(window,font="helvetica 12 bold",text="Number of Years       :",bg="brown").grid(row=2,column=1 ,padx=10,ipadx=20,ipady=0)
        Label(window,font="helvetica 12 bold",text="Loan Amount             :",bg="brown").grid(row=3,column=1,padx=10,pady=10,ipadx=20,ipady=0)
        Label(window,font="helvetica 12 bold",text="Monthly Payment       :",bg="brown").grid(row=4,column=1,padx=10,ipadx=20,ipady=0)
        Label(window,font="helvetica 12 bold",text="Total Interest Amount:",bg="brown").grid(row=5,column=1,padx=10,pady=10,ipadx=20,ipady=0)
        Label(window,font="helvetica 12 bold",text="Total payment               :",bg="brown").grid(row=6,column=1 ,padx=10,ipadx=20,ipady=0)
        
        self.annualinterestrate = StringVar()
        Entry(window,font="helvetica 12 bold",textvariable=self.annualinterestrate).grid(row=1,column=2)
        self.numberofyears = StringVar()
        Entry(window,font="helvetica 12 bold",textvariable=self.numberofyears).grid(row=2,column=2)
        self.loanamount = StringVar()
        Entry(window,font="helvetica 12 bold",textvariable=self.loanamount).grid(row=3,column=2)
        self.monthlypayment = StringVar()
        Label(window,font="helvetica 12 bold",textvariable=self.monthlypayment,bg="black",fg="white").grid(row=4,column=2,ipadx=20)
        self.totalinterestamount = StringVar()
        Label(window,font="helvetica 12 bold",textvariable=self.totalinterestamount,bg="black",fg="white").grid(row=5,column=2,ipadx=20)
        self.totalpayment = StringVar()
        Label(window,font="helvetica 12 bold",textvariable=self.totalpayment,bg="black",fg="white").grid(row=6,column=2,ipadx=20)
        
        btimage = PhotoImage(file="C:\\Users\\idris\\python\\contacts\\icons\\dre.png")
        generatepayment = Button(window,text="Generate",image=btimage,border=0,fg="black",font="helvetica 12 bold",command=self.generatepayment).grid(row=7,column=2,pady=10,sticky=E)
        btclear = Button(window,text="CLEAR",font="helvetica 12 bold",bg="brown",fg="black",command=self.clear).grid(row=8,column=2,pady=10,ipadx=35,ipady=0,sticky=E)
       
        window.mainloop()
    
    def generatepayment(self):
        a = self.getmonthlypayment(
            float(self.loanamount.get()),
            float(self.annualinterestrate.get()) / 1200,
            float(self.numberofyears.get()))
        self.monthlypayment.set(format(a,'10.2f'))

        ttlpayment = float(self.monthlypayment.get()) * 12 \
            * int(self.numberofyears.get())
        self.totalpayment.set(format(ttlpayment,'10.2f'))

        totalintamount = ttlpayment - float(self.loanamount.get()) 
        self.totalinterestamount.set(format(totalintamount,'10.2f'))



    def getmonthlypayment(self,loanamount,monthlyinterestrate,numberofyears):
        monthlypymt = loanamount * monthlyinterestrate / (1-1/(1+monthlyinterestrate)** (numberofyears*12))
        return monthlypymt

        
    def clear(self):
        self.annualinterestrate.set("")
        self.numberofyears.set("")
        self.loanamount.set("")
        self.monthlypayment.set("")
        self.totalinterestamount.set("")
        self.totalpayment.set("")
            

LoanCalculator()
