#! /usr/bin/python3
import tkinter
import threading
from tkinter import messagebox
import datetime
from plyer import notification
from tkinter import *

tasks = []
timer = threading
real_timer = threading
ok_thread = True


def get_entry1(event=""):
    text = todo.get()
    h = int(time1.get())
    m = int(time2.get())
    s = int(time3.get())
    todo.delete(0, tkinter.END)
    time1.delete(0, tkinter.END)
    time2.delete(0, tkinter.END)
    time3.delete(0, tkinter.END)
    timea.delete(0, tkinter.END)
    timeb.delete(0, tkinter.END)
    timec.delete(0, tkinter.END)
    todo.focus_set()
    hour = ((h*3600)+(m*60)+(s))
    add_list(text, hour)
    if 0 < hour < 999:
        update_list()

def get_entry2(event=""):
    nh = datetime.datetime.now().strftime('%H')
    nm = datetime.datetime.now().strftime('%M')
    ns = datetime.datetime.now().strftime('%S')
    text = todo.get()
    th = int(timea.get())
    tm = int(timeb.get())
    ts = int(timec.get())
    todo.delete(0, tkinter.END)
    time1.delete(0, tkinter.END)
    time2.delete(0, tkinter.END)
    time3.delete(0, tkinter.END)
    timea.delete(0, tkinter.END)
    timeb.delete(0, tkinter.END)
    timec.delete(0, tkinter.END)
    todo.focus_set()
    thour = ((th*3600)+(tm*60)+(ts))
    nhour = ((int(nh)*3600)+(int(nm)*60)+int(ns))
    if thour>int(nhour):
        hour=(thour-int(nhour))
    else:
        hour=((int(thour)-int(nhour))+(3600*24))
    add_list(text, hour)
    if 0 < hour < 999:
        update_list()

def add_list(text, hour):
    tasks.append([text, hour])
    timer = threading.Timer(hour, time_passed, [text])
    timer.start()


def update_list():
    if todolist.size() > 0:
        todolist.delete(0, "end")
    for task in tasks:
        remains=((task[1])%60)
        remainm=(((task[1])%3600)//60)
        remainh=((task[1])//3600)
        todolist.insert("end", "[" + task[0] + "] Time left: " + str(remainh) + " hours -" + str(remainm) + " minutes -" + str(remains) + " seconds")


def time_passed(task):
    timeinformat = datetime.datetime.now().strftime('%H : %M : %S')
    notification.notify(title="REMINDER", message="Time for " + task + "\n" + timeinformat,timeout=5)
    tkinter.messagebox.showinfo(timeinformat , "Time for : " + task)
    archive.insert("end", "[ " + task + " ] " + timeinformat)


def real_time():
    if ok_thread:
        real_timer = threading.Timer(1.0, real_time)
        real_timer.start()
    for task in tasks:
        if task[1] == 0:
            tasks.remove(task)
        task[1] -= 1
    update_list()



if __name__ == '__main__':
    # application
    app = tkinter.Tk()
    app.geometry("520x550")
    app.title("MRLINUXLOVER - 650  REMINDER")
    app.rowconfigure(0, weight=1)
    app['bg']='#383838'


    # fenetre
    frame = tkinter.Frame(app)
    frame.pack()

    # widgets
    label1 = tkinter.Label(app, bg="#383838", fg="#ffffff", text="Work to do :")
    label2 = tkinter.Label(app, bg="#383838", fg="#ffffff", text="(  H  -  M  -  S  )")
    label3 = tkinter.Label(app, bg="#383838", fg="#ffffff", text="Remain  Time  :")
    label4 = tkinter.Label(app, bg="#383838", fg="#ffffff", text="Time(22-22-22):")
    todo = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=30)
    time1 = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=10)
    time2 = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=10)
    time3 = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=10)
    timea = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=10)
    timeb = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=10)
    timec = tkinter.Entry(app, bg="#636363", fg="#1C0000", width=10)
    send1 = tkinter.Button(app, text='Add', fg="#ffffff", bg='#6186AC', height=3, width=30, command=get_entry1)
    send2 = tkinter.Button(app, text='Add', fg="#fffff1", bg='#6186AC', height=3, width=30, command=get_entry2)
    quit = tkinter.Button(app, text='Exit', fg="#ffffff", bg='#EB6464', height=3, width=30, command=app.destroy)
    todolist = tkinter.Listbox(app, bg="#636363")
    archive = tkinter.Listbox(app, bg="#636363")
    if tasks != "":
        real_time()

    # binding
    app.bind('<Return>', get_entry1)
    
    # widgets placement
    label1.place(x=0, y=30, width=180, height=25)
    label2.place(x=262, y=10, width=200, height=25)
    label3.place(x=180, y=30, width=200, height=25)
    label4.place(x=180, y=60, width=200, height=25)
    todo.place(x=125, y=30, width=80, height=25)
    time1.place(x=325, y=30, width=25, height=25)
    time2.place(x=350, y=30, width=25, height=25)
    time3.place(x=375, y=30, width=25, height=25)
    send1.place(x=415, y=30, width=50, height=25)
    timea.place(x=325, y=60, width=25, height=25)
    timeb.place(x=350, y=60, width=25, height=25)
    timec.place(x=375, y=60, width=25, height=25)
    send2.place(x=415, y=60, width=50, height=25)
    todolist.place(x=60, y = 150, width=400, height=150)
    archive.place(x=60, y = 350, width=400, height=150)
    quit.place(x=410, y=525, width=50, height=25)

    app.mainloop()
    ok_thread = False
    exit()
