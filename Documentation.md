# Documentação do Código

## 1. Configuração da Interface Gráfica

### 1.1 Configuração Inicial da Interface

```python
from customtkinter import *
from CTkMessagebox import CTkMessagebox
from PIL import Image, ImageTk
from tkinter import Toplevel, Label, Canvas
import random
import time
import os
```

Esta seção importa as bibliotecas necessárias para a interface gráfica, manipulação de imagens, geração de números aleatórios e controle de tempo.

### 1.2 Configuração da Janela Principal

```python
app = CTk()
app.geometry("900x600")
app.resizable(0, 0)
set_appearance_mode("dark")
```

Cria uma instância da classe `CTk`, configura as dimensões da janela principal, define a janela como não redimensionável e escolhe o modo escuro para a aparência.

### 1.3 Funções de Informações

```python
def MostrarInformaçao():
    CTkMessagebox(title="Informações sobre a aplicação", 
                  message="""
Bem vindo! Vamos dar início ao jogo.\n
Para jogar é bem simples:\n
1. Escolha uma caixinha branca, ou da esquerda ou da direita, e tente encontrar a nota de 100 reais.
2. No início de cada rodada posicione o mouse no círculo vermelho.
3. Cuidado! Se demorar muito para escolher, voltará para o início do jogo.""")
```

A função `MostrarInformaçao()` exibe uma caixa de mensagem com informações sobre como jogar a aplicação.

### 1.4 Frame Lateral e Logotipo

```python
sidebar_frame = CTkFrame(master=app, fg_color="#070F1F", width=200, height=800, corner_radius=0)
sidebar_frame.pack_propagate(0)
sidebar_frame.pack(fill="y", anchor="w", side="left")

base_path = os.path.dirname(os.path.abspath(__file__))
image_path = os.path.join(base_path, 'assets/GPDOC.png')
logo_img_data = Image.open(image_path)
logo_img = CTkImage(dark_image=logo_img_data, light_image=logo_img_data, size=(100, 110))

CTkLabel(master=sidebar_frame, text="", image=logo_img).pack(pady=(38, 0), anchor="center")
CTkLabel(master=sidebar_frame, text="Para mais informações").pack(pady=(38, 0), anchor="center")
```

Esta parte configura um frame lateral com um logotipo. `sidebar_frame` é uma estrutura lateral de cor escura com uma imagem de logotipo no topo.

### 1.5 Botões de Informações

```python
informationApp = CTkButton(master=sidebar_frame, text="Instruções 1", command=MostrarInformaçao).pack(pady=(10,0), anchor="center")
```

Cria um botão na lateral chamado "Instruções 1", que, quando clicado, chama a função `MostrarInformaçao()`.

## 2. Lógica e Funcionalidades do Jogo

### 2.1 Função IniciarJogo()

```python
def IniciarJogo():
    new_window = Toplevel(app)
    new_window.geometry("900x300")
    nota_50_img = Image.open(os.path.join("assets", "50.jpg"))
    nota_2_img = Image.open(os.path.join("assets", "2.jpg"))
    # Restante do código...
```

A função `IniciarJogo()` configura a janela da Fase 1 do jogo, carrega imagens das notas e define lógica para os botões e temporizador.

### 2.2 Funcionalidades do Jogo

```python
def acertou():
    # Código de resposta quando o usuário acerta
    # ...
def errou():
    # Código de resposta quando o usuário erra
    # ...
```

Funções que são chamadas quando o usuário acerta ou erra. Atualizam a pontuação, mostram a imagem correspondente e configuram o próximo passo do jogo.

### 2.3 Configuração do Temporizador

```python
def countdown():
    # Função de temporizador que atualiza o rótulo de contagem regressiva
    # ...
def start_timer():
    # Função para iniciar o temporizador
    # ...
def stop_timer():
    # Função para pausar o temporizador
    # ...
```

Funções que gerenciam o temporizador na Fase 1 do jogo.

### 2.4 Execução do Jogo

```python
inciarJogoUm = CTkButton(master=app, text="iniciar Jogo!", text_color="#fff", command=IniciarJogo).pack(anchor="center", pady=(0, 5),padx=(25, 0))
```

Botão na interface principal que inicia a Fase 1 do jogo quando clicado.

### 2.5 Configuração da Fase 2 - iniciarSegundoJogo()

```python
def iniciarSegundoJogo():
    new_window = Toplevel(app)
    new_window.geometry("900x300")
    nota_100_img = Image.open(os.path.join("assets", "100.jpg"))
    nota_50_img = Image.open(os.path.join("assets", "50.jpg"))
    nota_2_img = Image.open(os.path.join("assets", "2.jpg"))
    # Restante do código...
```

A função `iniciarSegundoJogo()` configura a janela da Fase 2 do jogo, semelhante à Fase 1, mas com lógica adaptada.

### 2.6 Funcionalidades Específicas da Fase 2

```python
def acertou():
    # Código específico para a Fase 2 quando o usuário acerta
    # ...
def errou():
    # Código específico para a Fase 2 quando o usuário erra
    # ...
```

Funções chamadas quando o usuário acerta ou erra na Fase 2, considerando o tempo médio de resposta.

### 2.7 Botão para Iniciar a Fase 2

```

python
inciarSegundoJogo = CTkButton(master=app, text="Iniciar Segundo Jogo!", text_color="#fff", command=iniciarSegundoJogo).pack(anchor="center", pady=(0, 5),padx=(25, 0))
```

Botão na interface principal que inicia a Fase 2 do jogo quando clicado.

## 3. Interface Gráfica e Interação do Usuário

### 3.1 Configuração de Elementos Gráficos

```python
CTkLabel(app, text="Escolha a caixinha que você acha que está a nota de R$ 50", font=("Helvetica", 15)).pack(pady=(30, 0))
canvas = Canvas(app, bg="#BACCC7", height=350, width=600)
canvas.pack(pady=(20, 0))
canvas.create_oval(280, 110, 320, 150, fill="red")
# Restante do código...
```

Configuração de rótulos e elementos gráficos na interface principal.

### 3.2 Interação com o Usuário

```python
def validate_input(event):
    # Função chamada ao inserir valores nas entradas para validar se são dígitos ou backspace
    # ...
entrada.bind("<Key>", validate_input)
```

Função de validação para garantir que o usuário insira apenas dígitos ou backspace nas entradas.