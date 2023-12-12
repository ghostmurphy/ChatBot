# ChatBot

import telebot
from confiq import *
from time import sleep


bot = telebot.TeleBot(TOKEN)
@bot.message_handler(commands=['start'])
def text(message):
    bot.send_message(message.from_user.id, 'Давай пообщаемся')

@bot.message_handler(commands=['help'])
def text(message):
        bot.send_message(message.from_user.id, 'Чтобы начать общение, напиши "Привет"')
@bot.message_handler(content_types=['text'])
def text(message):
    if message.text == "Привет":
        bot.send_message(message.from_user.id, 'Привет)')
    elif message.text == "Как дела?":
        sleep(5)
        bot.send_message(message.from_user.id, 'Отлично!')

    elif message.text == "Что делаешь?":
        sleep(2)
        bot.send_message(message.from_user.id, 'Общаюсь')
    else:
        bot.send_message(message.from_user.id, 'Я тебя не понял(')

bot.infinity_polling() 
