# login-screen
Tela inicial de login => usuario : admin ou joao => senha : admin ou 1234

from tkinter import *
from tkinter import Tk, ttk
from tkinter import messagebox

# cores
cor0 = "#f0f3f5"  #black
cor1 = "#feffff"  #white
cor2 = "#3fb5a3"  #green
cor3 = "#38576b"  #value
cor4 = "#403d3d"  #letters

#criando janela
janela = Tk()
janela.title('')
janela.geometry('310x300')
janela.configure(bg=cor1)
janela.resizable(width=FALSE,height=FALSE)

#dividir a janela
frame_cima = Frame(janela,width=310,height=50,bg=cor1,relief='flat')
frame_cima.grid(row=0,column=0,pady=1,padx=0,stick=NSEW)

frame_baixo = Frame(janela,width=310,height=250,bg=cor1,relief='flat')
frame_baixo.grid(row=1,column=0,pady=1,padx=0,stick=NSEW)

#configurando frame de cima
label_nome = Label(frame_cima, text='LOGIN',anchor=NE,font=('Ive 20 bold'),bg=cor1,fg=cor4)
label_nome.place(x=5,y=5)

label_linha = Label(frame_cima, text='', width=280,font=('Ive 1'),bg=cor2,fg=cor4)
label_linha.place(x=10,y=45)

#configurando usuário
credenciais = ['joao','1234']
def verificar_senha():
    nome = entry_nome.get()
    senha =entry_pass.get()

    if nome == 'admin' and senha == 'admin':
        messagebox.showinfo('Login','Seja bem vindo Admin')
        # apagar o que tiver na janela
        for widget in frame_cima.winfo_children():
            widget.destroy()
        for widget in frame_baixo.winfo_children():
            widget.destroy()

        nova_janelaadm()

    elif credenciais[0] == nome and credenciais [1] == senha:
        messagebox.showinfo('Login','Seja bem vindo '+ credenciais[0])

        #apagar o que tiver na janela
        for widget in frame_cima.winfo_children():
            widget.destroy()
        for widget in frame_baixo.winfo_children():
                widget.destroy()

        nova_janela()

    else:
        messagebox.showwarning('Erro','Verifique o nome e a senha')

#função após verificação
def nova_janela():
    #configurando frame de cima
    label_nome = Label(frame_cima, text='Usuário: ' + credenciais[0], anchor=NE, font=('Ive 17 bold'), bg=cor1, fg=cor4)
    label_nome.place(x=5, y=5)

    label_linha = Label(frame_cima, text='', width=280, font=('Ive 1'), bg=cor2, fg=cor4)
    label_linha.place(x=10, y=45)

    #configurando frame de baixo
    label_nome = Label(frame_baixo, text='Seja bem vindo ' + credenciais[0],  font=('Ive 17 bold'), bg=cor1, fg=cor4)
    label_nome.place(x=35, y=105)

def nova_janelaadm():
    label_nome = Label(frame_cima, text='Usuário: Admin', anchor=NE, font=('Ive 17 bold'), bg=cor1, fg=cor4)
    label_nome.place(x=5, y=5)

    label_linha = Label(frame_cima, text='', width=280, font=('Ive 1'), bg=cor2, fg=cor4)
    label_linha.place(x=10, y=45)

    # configurando frame de baixo
    label_nome = Label(frame_baixo, text='Seja bem vindo Admin' , font=('Ive 17 bold'), bg=cor1, fg=cor4)
    label_nome.place(x=25, y=105)


#configurando frame de baixo
label_nome = Label(frame_baixo, text='Nome *',anchor=NW,font=('Ive 10'),bg=cor1,fg=cor4)
label_nome.place(x=10,y=20)
entry_nome = Entry(frame_baixo,width=25,justify='left',font=('', 15),highlightthickness=1,relief='solid')
entry_nome.place(x=14,y=50)

label_pass = Label(frame_baixo, text='Senha*',anchor=NW,font=('Ive 10'),bg=cor1,fg=cor4)
label_pass.place(x=10,y=100)
entry_pass = Entry(frame_baixo,width=25,justify='left', show='*',font=('', 15),highlightthickness=1,relief='solid')
entry_pass.place(x=14,y=130)

b_confirmar = Button(frame_baixo, command=verificar_senha, text='Entrar',width=39,height=2,font=('Ive 8 bold'),bg=cor2,fg=cor1,relief=RAISED,overrelief=RIDGE)
b_confirmar.place(x=15,y=180)

janela.mainloop()
