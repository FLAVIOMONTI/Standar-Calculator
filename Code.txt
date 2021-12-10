from tkinter import *
root=Tk()

root.title("Calculator")
root.geometry("230x170") # window size
myFrame=Frame(root)
myFrame.pack()

operation="" 			# operation selected with user. start empty . is a Global variable 
result=0
operator=0 	 			# variable that will take the final result of operations. 
flag_operator= ""		# operation selected with user. start empty . is a Global variable

# ---- button all numbers---------------
bot_all=StringVar()

def numbers_all(num):
	global operation
	if operation != "":
		bot_all.set(num)
		operation=""
	else:
		bot_all.set(bot_all.get() + num)

# --------Funcion Suma------
def suma_display(num):
	global operation
	global result
	global flag_operator
	result+=float(num)
	operation="+"
	bot_all.set(result)
	flag_operator="+"
	
#--------Funtion Resta-------
def resta_display(num):
	global operation
	global result
	global flag_operator
	result+=float(num)
	operation="-"
	bot_all.set(result)
	flag_operator="-"

#--------Funtion Multip-------
def multip_display(num):
	global operation
	global result
	global flag_operator
	result+=float(num)
	operation="*"
	bot_all.set(result)
	flag_operator="*"

#--------Funtion division-------
def divi_display(num):
	global operation
	global result
	global flag_operator
	result+=float(num)
	operation="/"
	bot_all.set(result)
	flag_operator="/"

# --------Funtion result------
def result_display(num):
	global flag_operator
	global result
	global operator
	if flag_operator == "+":
		operator= result + float(num)
	elif flag_operator == "-":
		operator= result - float(num)
	elif flag_operator == "/":
		operator= result / float(num)
	elif flag_operator == "*":
		operator= result * float(num)
	bot_all.set(operator)			# final Result that will appear in display
	operator=0
	result=0
	
# --------Funtion Clear------
def clear_dislpay():
	global flag_operator
	global result
	global operator
	bot_all.set(0)
	operator=0
	result=0
	operation=""
	flag_operator=""
# -------------- DISPLAY-------------
display=Entry(myFrame, bg="black", fg="#03f943", justify="right", font = "bold", textvariable=bot_all)
display.grid(row=1, column=1, padx="1", pady="5", columnspan="5", sticky=W+E)

# --------------ROW 2----------------

button7=Button(myFrame, text="7", width="4", bg="white", command=lambda:numbers_all("7"))
button7.grid(row=2, column=1)
button8=Button(myFrame, text="8", width="4", bg="white", command=lambda:numbers_all("8"))
button8.grid(row=2, column=2)
button9=Button(myFrame, text="9", width="4", bg="white", command=lambda:numbers_all("9"))
button9.grid(row=2, column=3)
button_div=Button(myFrame, text="/", width="4", command=lambda:divi_display(bot_all.get()))
button_div.grid(row=2, column=4)

#-----------ROW 3-----------------

button4=Button(myFrame, text="4", width="4", bg="white", command=lambda:numbers_all("4"))
button4.grid(row=3, column=1)
button5=Button(myFrame, text="5", width="4", bg="white", command=lambda:numbers_all("5"))
button5.grid(row=3, column=2)
button6=Button(myFrame, text="6", width="4", bg="white", command=lambda:numbers_all("6"))
button6.grid(row=3, column=3)
button_mult=Button(myFrame, text="x", width="4", command=lambda:multip_display(bot_all.get()))
button_mult.grid(row=3, column=4)

#-----------------ROW 4----------
button1=Button(myFrame, text="1", width="4", bg="white", command=lambda:numbers_all("1"))
button1.grid(row=4, column=1)
button2=Button(myFrame, text="2", width="4", bg="white", command=lambda:numbers_all("2"))
button2.grid(row=4, column=2)
button3=Button(myFrame, text="3", width="4", bg="white", command=lambda:numbers_all("3"))
button3.grid(row=4, column=3)
button_resta=Button(myFrame, text="-", width="4", command=lambda:resta_display(bot_all.get()))
button_resta.grid(row=4, column=4)

#------------------ROW 5----------

button0=Button(myFrame, text="0", width="4", bg="white", command=lambda:numbers_all("0"))
button0.grid(row=5, column=1)
button_coma=Button(myFrame, text=",", width="4", command=lambda:numbers_all("."))
button_coma.grid(row=5, column=3)
button_mas=Button(myFrame, text="+", width="4", command=lambda:suma_display(bot_all.get()))
button_mas.grid(row=5, column=4)
button_clear=Button(myFrame, text="C", width="4", command=lambda:clear_dislpay())
button_clear.grid(row=5, column=2)

#-------------EQUAL-------------

button_equal=Button(myFrame, text="=", height="2", width="4", bg="light blue", command=lambda:result_display(bot_all.get()))
button_equal.grid(row=4, column=5, rowspan=2)



root.mainloop()