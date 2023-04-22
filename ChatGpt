import openai
from PyQt5 import QtWidgets, QtCore

def chatBot(text):
    # Imposta la chiave API per OpenAI
    openai.api_key = "xxxxxxxxxxxxxxxxx"
    # Invia il testo all'API di OpenAI e ottiene una risposta
    response = openai.Completion.create(
        engine = "text-davinci-003",
        prompt = text,
        temperature = 0.3,
        max_tokens = 2048,
    )
    # Restituisce il testo della risposta
    return response.choices[0].text

def send_message():
    # Recupera il messaggio inserito dall'utente
    message = message_entry.toPlainText()
    # Cancella il campo di inserimento del messaggio
    message_entry.clear()
    # Invia il messaggio alla funzione chatBot e ottiene una risposta
    response = chatBot(message)
    # Aggiunge il messaggio e la risposta alla cronologia della chat
    chat_history.append("You: " + message + "\n")
    chat_history.append("Bot: " + response + "\n")

def reset_chat():
    # Cancella la cronologia della chat e il campo di inserimento del messaggio
    chat_history.clear()
    message_entry.clear()

# Crea un'applicazione PyQt5
app = QtWidgets.QApplication([])

# Crea una finestra
window = QtWidgets.QWidget()
# Imposta il titolo della finestra
window.setWindowTitle("Chatbot")

# Crea un widget per visualizzare la cronologia della chat
chat_history = QtWidgets.QTextEdit()
# Imposta il widget in sola lettura
chat_history.setReadOnly(True)

# Crea un pulsante per inviare i messaggi
send_button = QtWidgets.QPushButton("Send")
# Imposta le dimensioni del pulsante
send_button.setFixedSize(100, 50)
# Imposta lo stile del pulsante
send_button.setStyleSheet("QPushButton {background-color: #ADD8E6; border-radius: 10px;}")
# Collega il pulsante alla funzione send_message
send_button.clicked.connect(send_message)

# Crea un pulsante per resettare la chat
reset_button = QtWidgets.QPushButton("Reset")
# Imposta le dimensioni del pulsante
reset_button.setFixedSize(100, 50)
# Imposta lo stile del pulsante
reset_button.setStyleSheet("QPushButton {background-color: #FFC0CB; border-radius: 10px;}")
# Collega il pulsante alla funzione reset_chat
reset_button.clicked.connect(reset_chat)

# Crea un widget per inserire i messaggi
message_entry = QtWidgets.QPlainTextEdit()

# Crea un layout orizzontale per i pulsanti
button_layout = QtWidgets.QHBoxLayout()
# Aggiunge il pulsante send al layout
button_layout.addWidget(send_button)
# Aggiunge uno spazio tra i due pulsanti
button_layout.addSpacing(10)
# Aggiunge il pulsante reset al layout
button_layout.addWidget(reset_button)

# Crea un layout verticale per la finestra principale
layout = QtWidgets.QVBoxLayout(window)
# Aggiunge la cronologia della chat al layout principale
layout.addWidget(chat_history)
# Aggiunge il layout dei pulsanti al layout principale
layout.addLayout(button_layout)
# Aggiunge il campo di inserimento dei messaggi al layout principale
layout.addWidget(message_entry)

# Mostra la finestra principale
window.show()
# Esegue l'applicazione PyQt5
app.exec_()
