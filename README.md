from aiogram import Bot, Dispatcher, executor, types
TOKEN = "6627111140:AAEu5m5sliiFQjlixZW94S29n8Jtfh3yQDc"
bot = Bot(token=TOKEN)
dp = Dispatcher(bot)
@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
   await message.reply("Привет!\nЯ Жанна!\nОтправь мне любое сообщение, а я тебе обязательно отвечу.")
@dp.message_handler() #Создаём новое событие, которое запускается в ответ на любой текст, введённый пользователем.
async def echo(message: types.Message): #Создаём функцию с простой задачей — отправить обратно тот же текст, что ввёл пользователь.
   await message.answer(message.text)
if __name__ == '__main__':
   executor.start_polling(dp, skip_updates=True)
