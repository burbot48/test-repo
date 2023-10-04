
from PIL import Image,ImageTk
import tkinter
#from  barcode_generator import barcode_maker
from datetime import datetime
import math
import barcode
from barcode.writer import ImageWriter

root = tkinter.Tk()
label = tkinter.Label(root, text = "Boş Kasa Girişinde Okutunuz")
label.pack()
img = None
tkimg = [None]  # This, or something like it, is necessary because if you do not keep a reference to PhotoImage instances, they get garbage collected.

delay = 20000   # in milliseconds

def barcode_maker(number):
    #Define content of the barcode as a string
    
    #Get the required barcode format
    barcode_format = barcode.get_barcode_class('code128')
    
    #Generate barcode and render as image
    my_barcode = barcode_format(number, writer=ImageWriter())
      
    #Save barcode as PNG
    my_barcode.save("barcode")
    
def loopCapture():
    
    now = datetime.now() # current date and time
    date_time = float(now.strftime("%Y%m%d%H%M"))
    date_time=math.ceil(date_time)*2
   
    barcode_maker("BK"+str(date_time))
    
    
    image_path="barcode.png"
    
    #    img = fetch_image(URL,USERNAME,PASSWORD)
    
    #pil_img = Image.open(image_path).resize((400,300), Image.ANTIALIAS)
    pil_img = Image.open(image_path).resize((400,300))
    w, h = pil_img.size
    
    left = 0
    right = w
    upper = 0
    lower = 3*h/4
    
    img2 = pil_img.crop([ left, upper, right, lower])
    tkimg[0] = ImageTk.PhotoImage(img2)
    #label = tkinter.Label(root, text = "Boş Kasa Girişinde Okutunuz")
    label.pack()
    label.config(image=tkimg[0])
    root.update_idletasks()
    root.after(delay, loopCapture)

loopCapture()
root.mainloop()
