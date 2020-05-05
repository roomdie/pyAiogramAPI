# pyAiogramAPI
Asynchronous, extensible Python implementation for <a href="https://core.telegram.org/bots/api">Telegram Bot API</a><br/>
Original docs here <a href="https://aiogram.readthedocs.io">Aiogram API</a>

<div>
	<a class="reference external image-reference" href="https://t.me/aiogram_live"><img alt="[Telegram] aiogram live" src="https://img.shields.io/badge/telegram-aiogram-blue.svg?style=flat-square"></a>
	<a class="reference external image-reference" href="https://pypi.python.org/pypi/aiogram"><img alt="PyPi Package Version" src="https://img.shields.io/pypi/v/aiogram.svg?style=flat-square"></a>
	<a class="reference external image-reference" href="https://pypi.python.org/pypi/aiogram"><img alt="PyPi status" src="https://img.shields.io/pypi/status/aiogram.svg?style=flat-square"></a>
	<a class="reference external image-reference" href="https://pypi.python.org/pypi/aiogram"><img alt="PyPi downloads" src="https://img.shields.io/pypi/dm/aiogram.svg?style=flat-square"></a>
	<a class="reference external image-reference" href="https://pypi.python.org/pypi/aiogram"><img alt="Supported python versions" src="https://img.shields.io/pypi/pyversions/aiogram.svg?style=flat-square"></a>
	<a class="reference external image-reference" href="https://core.telegram.org/bots/api"><img alt="Telegram Bot API" src="https://img.shields.io/badge/Telegram%20Bot%20API-4.8-blue.svg?style=flat-square&amp;logo=telegram"></a>
	<a class="reference external image-reference" href="http://docs.aiogram.dev/en/latest/?badge=latest"><img alt="Documentation Status" src="https://img.shields.io/readthedocs/aiogram?style=flat-square"></a>
	<a class="reference external image-reference" href="https://github.com/aiogram/aiogram/issues"><img alt="Github issues" src="https://img.shields.io/github/issues/aiogram/aiogram.svg?style=flat-square"></a>
	
</div>

* [Quick Start.](#quick-start)
* [Your first bot.](#your-first-bot)
## Quick Start.

* Installation using pip:
```
$ pip install aiogram
```

* Installation from source:
```
git clone https://github.com/aiogram/aiogram.git
cd aiogram
python setup.py install
```

### Recommendations

* Use **uvloop** instead of default asyncio loop.
```
pip install uvloop
```

* Use **ujson** instead of the default json module.
```
pip install ujson
```
* Use aiohttp speedups:

	* Use **cchardet** instead of the chardet module.
	```
	pip install cchardet
	```
	* Use **aiodns** for speeding up DNS resolving.
	```
	pip install aiodns
	```
	* Installing speedups altogether.<br/>
	The following will get you aiohttp along with cchardet, aiodns and 	brotlipy in one bundle.
	```
	pip install aiohttp[speedups]
	```

## Your first bot.

### Token
You need to get a **Token** from the bot in Telegram <a href="https://t.me/BotFather">@BotFather</a>.
As well as basic knowledge of the Python and <a href="https://core.telegram.org/bots/api">API Telegram Bot.</a>

## A simple echo bot 
At first you have to import all necessary modules:
```python
import logging
from aiogram import Bot, Dispatcher, executor, types
```
Then you have to initialize bot and dispatcher instances. Make sure to actually replace TOKEN with your own API token:
```python
API_TOKEN = 'TOKEN'

# Configure logging
logging.basicConfig(level=logging.INFO)

# Initialize bot and dispatcher
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)
```
Next step: let's define a message handler which handles incoming /start and /help commands:
```python
@dp.message_handler(commands=['start', 'help'])
async def send_welcome(message: types.Message):
    await message.reply("Hello, I'm bot.")
```
_A function which is decorated by a message handler can have an arbitrary name
(try renaming the send_welcome function with any name)_

Let's add another handler:
```python
@dp.message_handler()
async def echo(message: types.Message):
    await message.answer(message.text)
```
This one echoes all incoming text messages back to the sender.
If you have already used other libraries for creating bots, then perhaps you remember that to send a message you had to do this:
```python
bot.send_message(message.chat.id, message.text)
```
But in Aiogram need like this:
```python
await message.answer(message.text)
```

Last step: we now have a basic bot which replies a static message to "/start" and "/help" commands and which echoes the rest of the sent messages. To start the bot, add the following to our source file:
```python
if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
```

Our source file now looks like this:
```python
import logging
from aiogram import Bot, Dispatcher, executor, types

API_TOKEN = 'TOKEN'

# Configure logging
logging.basicConfig(level=logging.INFO)

# Initialize bot and dispatcher
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)


@dp.message_handler(commands=['start', 'help'])
async def send_welcome(message: types.Message):
    await message.reply("Hello, I'm bot.")


@dp.message_handler()
async def echo(message: types.Message):
    await message.answer(message.text)
    
if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
```
