from tkinter import *
from tkinter import ttk
import requests

        

def data_get():
    city = city_name.get()
    data = requests.get("https://api.openweathermap.org/data/2.5/weather?q="+city+"&appid=b70de9dd1efb046b9b9535895060cad6").json()
    w1_label.config(text=data["weather"][0]["main"])
    wb_label.config(text=data["weather"][0]["description"])
    temp_label1.config(text=str(int(data["main"]["temp"]-273.15)))
    per_label1.config(text=data["main"]["pressure"])



win = Tk()
win.title("WEATHER APP")
win.config(bg = "light blue")
win.geometry("700x700")

name_label = Label(win,text="WEATHER APP",
                   font=("Time New Roman", 30, "bold"))
name_label.grid(row=0, column=0, columnspan=2, pady=10)

city_name = StringVar()
list_name = ["Ahmedabad","Andhra Pradesh","Arunachal Pradesh ","Assam","Bihar","Chhattisgarh","Goa","Gujarat","Haryana","Himachal Pradesh","Jammu and Kashmir","Jharkhand","Karnataka","Kerala","Madhya Pradesh","Maharashtra","Manipur","Meghalaya","Mizoram","Nagaland","Odisha","Punjab","Rajasthan","Sikkim","Tamil Nadu","Telangana","Tripura","Uttar Pradesh","Uttarakhand","West Bengal","Andaman and Nicobar Islands","Chandigarh","Dadra and Nagar Haveli","Daman and Diu","Lakshadweep","National Capital Territory of Delhi","Puducherry"]
com = ttk.Combobox(win, text="Sensei weather app",values=list_name,
                   font=("Time New Roman", 20,"bold"),textvariable=city_name)
com.grid(row=2, column=1, pady=10)

city_label = Label(win, text="Select a city:", font=("Time New Roman", 20, "bold"))
city_label.grid(row=2, column=0, pady=10, padx=10)


w_label = Label(win, text="Weather Climate", font=("Time New Roman", 20), fg="red", bg="light blue")
w_label.place(x=25, y=260, height=50, width=210)
w1_label = Label(win, text="", font=("Time New Roman", 20), fg="red", bg="blue")
w1_label.place(x=250, y=260, height=50, width=210)

wb_label = Label(win, text="", font=("Time New Roman", 20), fg="red", bg="blue")
wb_label.place(x=250, y=330, height=50, width=210)
wb_label1 = Label(win, text="Weather Description", font=("Time New Roman", 17), fg="red", bg="light blue")
wb_label1.place(x=25, y=330, height=50, width=210)

temp_label = Label(win, text="Temperature", font=("time new roman", 20), fg="red", bg="blue")
temp_label.place(x=25, y=400, height=50, width=200)
temp_label1 = Label(win, text="", font=("time new roman", 17), fg="red", bg="blue")
temp_label1.place(x=250, y=400, height=50, width=200)

per_label = Label(win, text="Pressure", font=("time new roman", 17), fg="red", bg="blue")
per_label.place(x=25, y=470, height=50, width=200)
per_label1 = Label(win, text="", font=("time new roman", 20), fg="red", bg="blue")
per_label1.place(x=250, y=470, height=50, width=200)

done_button = Button(win, text="DONE", font=("Times new roman", 25, "bold"), command=data_get)
done_button.place(y=190, height=60, width=150, x=200)







win.mainloop()
                  
                
a
