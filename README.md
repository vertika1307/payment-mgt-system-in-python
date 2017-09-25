# payment-mgt-system-in-python
import time
import datetime
from Tkinter import* 
import tkMessageBox

root = Tk()
root.title("Pay Management")
root.geometry('1350x650+0+0')

#==========================================frames declaration===========================================
Tops = Frame(root,width=1350,height=70, bd=8, relief="solid")
Tops.pack(side=TOP)
f1=Frame(root,width=600,height=600,bd=8,relief="raise")
f1.pack(side=LEFT)

f2=Frame(root,width=300,height=700,bd=8,relief="raise")
f2.pack(side=RIGHT)

f1a=Frame(f1,width=600,height=200,bd=20,relief="raise")
f1a.pack(side=TOP)
f1b=Frame(f1,width=600,height=200,bd=20,relief="raise")
f1b.pack(side=TOP)
lb1info=Label(Tops,font=('arial',60,'bold'),text="  Payment Management Systems  ",bd=10)
lb1info.grid(row=0,column=0)



#==========================================exit============================
def iExit():
    qExit=tkMessageBox.askyesno("Pay Management", "Do you want to exit the system")
    if qExit > 0:
        root.destroy()
        return


#===============================reset====================================
def Reset():
    Name.set("")
    Address.set("")
    Employer.set("")
    NINumber.set("")
    HoursWorked.set("")
    HourlyRate.set("")
    Tax.set("")
    Overtime.set("")
    GrossPay.set("")
    NetPay.set("")
    txtPaySlip.delete("1.0",END)



#==========================enter info====================================
def EnterInfo():
    txtPaySlip.insert(END,"\t\tPay Slip\n\n")
    txtPaySlip.insert(END,'Name:\t\t' +Name.get() +"\n\n" )
    txtPaySlip.insert(END,'Address:\t\t' +Address.get() +"\n\n" )
    txtPaySlip.insert(END,'Employer:\t\t' +Employer.get() +"\n\n" )
    txtPaySlip.insert(END,'NINumber:\t\t' +NINumber.get() +"\n\n" )
    txtPaySlip.insert(END,'HoursWorked:\t\t' +HoursWorked.get() +"\n\n" )
    txtPaySlip.insert(END,'HourlyRate:\t\t' +HourlyRate.get() +"\n\n" )
    txtPaySlip.insert(END,'Tax:\t\t' +Tax.get() +"\n\n" )
    txtPaySlip.insert(END,'Overtime:\t\t' +Overtime.get() +"\n\n" )
    txtPaySlip.insert(END,'GrossPay:\t\t' +GrossPay.get() +"\n\n" )
    txtPaySlip.insert(END,'NetPay:\t\t' +NetPay.get() +"\n\n" )




#==============================weekly wages======================================
def WeeklyWages():
    HoursWorkedPerWeek=float(HoursWorked.get())
    WagesPerHours=float(HourlyRate.get())

    GrossPay1=(WagesPerHours*HoursWorkedPerWeek)
    PaymentDue="@" ,str ('%.2f' % ( GrossPay1))
    GrossPay.set(PaymentDue)

    Tax1=(GrossPay1*0.2)
    Taxables="@" ,str ('%.2f' % (Tax1))
    Tax.set(Taxables)

    NetPay1=(GrossPay1-Tax1)
    NetPays="@" ,str ('%.2f' % (NetPay1))
    NetPay.set(NetPays)


    if HoursWorkedPerWeek > 40:
        overTimeHours =((HoursWorkedPerWeek-40)+WagesPerHours*1.5)
        Overtimehrs="@", str ('%.2f' %(overTimeHours))
        Overtime.set(Overtimehrs)
    
    elif HoursWorkedPerWeek <= 40:
        overTimeHours = ((40-HoursWorkedPerWeek)+WagesPerHours*1.5)
        Overtimehrs="@", str ('%.2f' %(overTimeHours))
        Overtime.set(Overtimehrs)
    return


    


    
#=================================variables=========================================================

Name=StringVar()
Address=StringVar()
Employer=StringVar()
NINumber=StringVar()
HoursWorked=StringVar()
HourlyRate=StringVar()
Tax=StringVar()
Overtime=StringVar()
GrossPay=StringVar()
NetPay=StringVar()
DateofOrder=StringVar()
DateofOrder.set(time.strftime("%d/%m/%y"))





#======================================labels========================================================
lb1info=Label(f1a,text="Name",font=('arial',16,'bold'),bd=20).grid(row=0,column=0)
lb1info=Label(f1a,text="Address", font=('arial',16,'bold'),bd=16).grid(row=0,column=2)
lb1info=Label(f1a,text="Employer",font=('arial',16,'bold'),bd=20).grid(row=1,column=0)
lb1info=Label(f1a,text="NI Number",font=('arial',16,'bold'),bd=20).grid(row=1,column=2)
lb1info=Label(f1a,text="Hours Worked",font=('arial',16,'bold'),bd=20).grid(row=2,column=0)
lb1info=Label(f1a,text="Hourly Rate",font=('arial',16,'bold'),bd=20).grid(row=2,column=2)
lb1info=Label(f1a,text="Tax",font=('arial',16,'bold'),bd=20).grid(row=3,column=0)
lb1info=Label(f1a,text="Overtime",font=('arial',16,'bold'),bd=20).grid(row=3,column=2)
lb1info=Label(f1a,text="Gross Pay",font=('arial',16,'bold'),bd=20).grid(row=4,column=0)
lb1info=Label(f1a,text="Net Pay",font=('arial',16,'bold'),bd=20).grid(row=4,column=2)




#====================================text============================================================
etxtName=Entry(f1a,textvariable=Name, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtName.grid(row=0,column=1)
etxtAddress=Entry(f1a,textvariable=Address, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtAddress.grid(row=0,column=3)
etxtEmployer=Entry(f1a,textvariable=Employer, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtEmployer.grid(row=1,column=1)
etxtNINumber=Entry(f1a,textvariable=NINumber, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtNINumber.grid(row=1,column=3)
etxtHoursWorked=Entry(f1a,textvariable=HoursWorked, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtHoursWorked.grid(row=2,column=1)
etxtHourlyRate=Entry(f1a,textvariable=HourlyRate, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtHourlyRate.grid(row=2,column=3)
etxtTax=Entry(f1a,textvariable=Tax, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtTax.grid(row=3,column=1)
etxtOvertime=Entry(f1a,textvariable=Overtime, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtOvertime.grid(row=3,column=3)
etxtGrossPay=Entry(f1a,textvariable=GrossPay, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtGrossPay.grid(row=4,column=1)
etxtNetPay=Entry(f1a,textvariable=NetPay, font=('arial',16,'bold'),bd=16,width=22,justify='left')
etxtNetPay.grid(row=4,column=3)



lb1PaySlip=Label(f2,textvariable=DateofOrder,font=('arial',21,'bold'),bd=20).grid(row=0,column=0)
txtPaySlip=Text(f2,height=22, width = 34,bd=16,font=('arial',12,'bold'))
txtPaySlip.grid(rows=1,column=0)


#=================================button===============================================

btnSalary=Button(f1b,text="Weekly Wages",padx=16,pady=16,bd=8,fg="black",
                font=('arial',16,'bold'),width=14,height=1,command =WeeklyWages).grid(row=0,column=0)
btnReset=Button(f1b,text="Reset",padx=16,pady=16,bd=8,fg="black",
                font=('arial',16,'bold'),width=14,height=1,command =Reset).grid(row=0,column=1)
btnPaySlip=Button(f1b,text="View PaySlip",padx=16,pady=16,bd=8,fg="black",
                  font=('arial',16,'bold'),width=14,height=1,command =EnterInfo).grid(row=0,column=2)
btnExit=Button(f1b,text="Exit System",padx=16,pady=16,bd=8,fg="black",
               font=('arial',16,'bold'),width=14,height=1,command =iExit).grid(row=0,column=3)



                                
root.mainloop()

