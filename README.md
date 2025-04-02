import asyncio
import random

import dp
from aiogram import Bot, Dispatcher, types
from aiogram.filters import (Command)
bot = Bot(token="7610017962:AAFFId6XegDOkERYIga0fPZ1gRdmeF6HFFw")
@dp.message(Command("go"))
dp=["камень", "ножницы", "бумага"]
async def cmd_go(massage:types.massage):
    print("Вы ввели команду /go")
    await massage.answer("/go")
    b=random.choice(dp)
    text=massage.text.replace("/go","").strip()
    if text==b:
        await massage.answer("ничья")
    elif(b=="камень" and text=="бумага")or(b=="бумага" and text=="ножницы")or(b=="ножницы" and text=="камень"):
        await massage.answer("победил)")
    else: await massage.answer("проиграл(")
    async def main():
        await dp.start_polling(bot)
        if __name__ == "__main__":
            print("бот начал работать")
            asyncio.run(main())
