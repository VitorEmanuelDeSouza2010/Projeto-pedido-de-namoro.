# Projeto-pedido-de-namoro.
Este é um projeto estudantil

from tkinter import *
import random

root = Tk()
root.title("Quer namorar comigo?")
root.geometry("400x200")
root.resizable(False, False)
root.configure(bg = "#000000")

def move_Button(event):
    x = random.randint(50,350) # Gerar uma nova posição aleatória entre 50 e 350
    y = random.randint(50,150) # Gerar uma nova posição aleatória entre 50 e 150

    # Verificar se a nova posição x e y não colidem com o botão SIM
    if(x < sim_button.winfo_x() - 50 or x > sim_button.winfo_x() + 50) or ( y < sim_button.winfo_y() - 50 or y > sim_button.winfo_y() + 50):
        nao_button.place(x=x, y=y)# Posicionar o botão "não" na nova posição

def show_response(response):
    if response == "sim":
        label_response.config(text="Você disse SIM!", fg="#32CD32")
    elif response == "nao":
        label_response.config(text="Você disse NÃO!", fg="#FF2600")

sim_button = Button(root, text= "SIM", width= 10, command= lambda: show_response("sim"))
nao_button = Button(root, text= "NÃO", width= 10, command= lambda: show_response("nao"))
sim_button.configure(bg= '#32CD32', fg= "#FFFFFF", font=('Helvetica', 12))
nao_button.configure(bg= "#FF2600", fg= "#FFFFFF", font=('Helvetica', 12))

label_question = Label(root, text= "Quer namorar comigo?", font=('Helvetica', 14), bg= ("#000000"), fg= ("#F0F0F0"))
label_response = Label(root, text= "", font=('Helvetica', 14), bg= ("#000000"))

sim_button.place(x=100, y=75)
nao_button.place(x=250, y=75)
label_question.place(x=50, y=20)
label_response.place(x=120, y=130)

nao_button.bind("<Motion>", move_Button)

root.mainloop()
