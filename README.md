# API---BOT--PYTHON

import telebot

# *** ATENÇÃO: Substitua pelos seus tokens e IDs ***
BOT_TOKEN = "SEU_TOKEN_DO_BOT"
CHANNEL_ID = -1001234567890  # ID do seu canal
GROUP_ID = -1000987654321    # ID do seu grupo
TOPIC_ID = 123                 # ID do tópico para onde você quer enviar

bot = telebot.TeleBot(BOT_TOKEN)

@bot.message_handler(chat_id=CHANNEL_ID, content_types=['text', 'photo', 'video', 'audio', 'document', 'sticker'])
def clone_message(message):
    """Clona as mensagens do canal para um tópico específico no grupo."""
    try:
        if message.text:
            bot.send_message(GROUP_ID, message.text, message_thread_id=TOPIC_ID)
        elif message.photo:
            bot.send_photo(GROUP_ID, message.photo[-1].file_id, caption=message.caption, message_thread_id=TOPIC_ID)
        elif message.video:
            bot.send_video(GROUP_ID, message.video.file_id, caption=message.caption, message_thread_id=TOPIC_ID)
        elif message.audio:
            bot.send_audio(GROUP_ID, message.audio.file_id, caption=message.caption, message_thread_id=TOPIC_ID)
        elif message.document:
            bot.send_document(GROUP_ID, message.document.file_id, caption=message.caption, message_thread_id=TOPIC_ID)
        elif message.sticker:
            bot.send_sticker(GROUP_ID, message.sticker.file_id, message_thread_id=TOPIC_ID)
    except Exception as e:
        print(f"Erro ao enviar mensagem para o tópico: {e}")

if __name__ == '__main__':
    print("Bot de clonagem iniciado (para um tópico específico). Aguardando mensagens no canal...")
    bot.polling(none_stop=True)

    import telebot

BOT_TOKEN = "meutoken"                                                           CHANNEL_ID = meuid
GROUP_ID = meuid
TOPIC_ID_DESTINO = 143

bot = telebot.TeleBot(BOT_TOKEN)

@channel_post_handler(chat_id=CHANNEL_ID, content_types=['text', 'photo', 'video', 'audio', 'document', 'sticker'])

def clone_message(message):
    """Clona as mensagens do canal para o grupo."""
    try:
        if message.text:
            bot.send_message(GROUP_ID, message.text)
        elif message.photo:
            bot.send_photo(GROUP_ID, message.photo[-1].file_id, caption=message.caption)
        elif message.video:
            bot.send_video(GROUP_ID, message.video.file_id, caption=message.caption)
        elif message.audio:                                                                                                       bot.send_audio(GROUP_ID, message.audio.file_id, caption=message.caption)
        elif message.document:
            bot.send_document(GROUP_ID, message.document.file_id, caption=message.caption)
        elif message.sticker:
            bot.send_sticker(GROUP_ID, message.sticker.file_id)
    except Exception as e:
        print(f"Erro ao enviar mensagem: {e}")

if __name__ == '__main__':
    print("Bot de clonagem iniciado. Aguardando mensagens no canal...")
    bot.polling(none_stop=True)

            >>> running = True
        >>> def f():
        ...     if running:
        ...             fd(50)
        ...             lt(60)
        ...             screen.ontimer(f, 250)
        ...
        >>> f()   # makes the turtle marching around
        >>> running = False
