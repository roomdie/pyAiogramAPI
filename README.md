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
