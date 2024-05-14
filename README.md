# Py-test-ping
Um projeto simples para pingar um ip









import PySimpleGUI as sg # type: ignore
import os
import time
# Defina o layout da janela
layout = [
    [sg.Text("Digite o IP:", text_color="#21160e", background_color="#d4c2b2")],
    [sg.Input(key="-INPUT-", size=(15,3))],
    [sg.Button("Testar", size=(5,2),button_color=("black", "#ebe9df")), sg.Button("Sair", size=(5,2),button_color=("black", "#ebe9df"))],
    [sg.Output(size=(20, 10))],  # Janela de mensagens
]
# Crie a janela
window = sg.Window("Py test ping", layout, no_titlebar=True, background_color="#d4c2b2")

# Loop de eventos
while True:
    event, values = window.read()
    if event == sg.WIN_CLOSED or event == "Sair":
        break
    elif event == "Testar":
        entrada = values["-INPUT-"]  
        if entrada =="":
            print("error voce deve inserir um ip") 
        else: 
            while True:
                print("Aguarde!")
                response = os.system("ping -a " + entrada)
                if response == 0:
                    print("--------------")
                    print(entrada +'\n'+ "Conexao estabelecida")
                    print("--------------")
                else:
                    print("--------------")
                    print(entrada +'\n'+ "Conexao NAO estabelecida")
                    print("--------------")
                break
# Feche a janela
window.close()
