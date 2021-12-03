from tkinter import *
from pytube import YouTube

root = Tk()
root.geometry("500x300")
root.resizable(0,0)
root.title("YouTube Video Downloader")
root.configure(bg = "White")

Label(root, text = "Please paste the link below", font = "Arial 15 bold").pack()

link = StringVar()
link_input = Entry(root, textvariable = link, font = "Arial 10", bg = "gray", width = "65").place(x=20, y=50)

def downloader():
#Concept 1
    #url = YouTube(str(link.get()))
    #video = url.streams.first()
    #video.download()   # works

#Concept 2
    #url = str(link.get())
    #YouTube(url).streams.first().download()     # works

#Concept 3
    url = str(link.get())
    yt = YouTube(url)
    yt.streams.filter(progressive=True, file_extension='mp4').order_by("resolution").desc().first().download()  #works

Button(root, text='DOWNLOAD', font='arial 15 bold', bg='pale violet red', padx=2, command=downloader).place(x=180,y=150)

root.mainloop()
