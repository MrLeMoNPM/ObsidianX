# obsidianx-teleconsole (Python)

کلاینت پایتون برای اتصال به پل TCP پلاگین **ObsidianX TeleConsole** روی سرور PocketMine-MP.
Python client for connecting to the **ObsidianX TeleConsole** plugin's TCP bridge on a PocketMine-MP server.

ساخته | Built by: **MrLeMoNIR x amirxd**

## نصب | Install

```bash
pip install -e .
```

## استفاده سریع (Sync) | Quick usage (sync)

```python
from obsidianx_teleconsole import ObsidianXClient

with ObsidianXClient(host="127.0.0.1", port=25566, token="YOUR_TOKEN") as client:
    print(client.send_command("say Hello!"))
```

## استفاده Async | Async usage

```python
import asyncio
from obsidianx_teleconsole import AsyncObsidianXClient

async def main():
    client = AsyncObsidianXClient(host="127.0.0.1", port=25566, token="YOUR_TOKEN")
    await client.connect()
    print(await client.send_command("list"))
    await client.close()

asyncio.run(main())
```

## دریافت لاگ زنده‌ی کنسول | Receiving the live console log

اگر `log-stream.enabled: true` در کانفیگ پلاگین باشد، سرور به‌صورت خودکار (هر ۲ ثانیه یک‌بار، دسته‌ای) لاگ کنسول را برای شما می‌فرستد. فقط یک `on_log` بدهید:

If `log-stream.enabled: true` in the plugin's config, the server automatically pushes the console log to you (batched, every 2 seconds). Just pass an `on_log`:

```python
from obsidianx_teleconsole import ObsidianXClient

def on_log(text: str) -> None:
    print("[LIVE LOG]", text)

with ObsidianXClient(host="127.0.0.1", port=25566, token="YOUR_TOKEN", on_log=on_log) as client:
    ...
```

نسخه‌ی Async هم `on_log` می‌پذیرد و می‌تواند یک تابع معمولی یا یک coroutine باشد:
The async client also accepts `on_log`, and it can be either a regular function or a coroutine:

```python
async def on_log(text: str) -> None:
    print("[LIVE LOG]", text)

client = AsyncObsidianXClient(host="127.0.0.1", port=25566, token="YOUR_TOKEN", on_log=on_log)
```

پیش‌نیاز روی سرور PocketMine-MP: پلاگین TeleConsole باید نصب باشد و `tcp-bridge.enabled: true` در `config.yml` آن تنظیم شده باشد.
Prerequisite on the PocketMine-MP server: the TeleConsole plugin must be installed with `tcp-bridge.enabled: true` set in its `config.yml`.

برای یک بات تلگرام کامل و آماده، به پوشه‌ی `examples/` نگاه کنید.
For a complete, ready-to-run Telegram bot, see the `examples/` folder.

## بات روبیکا | Rubika bot

یک بات کامل برای [روبیکا](https://rubika.ir) هم در `examples/rubika_bot.py` قرار دارد، با محافظت قوی در برابر محدودیت ارسال روبیکا (که خیلی حساس‌تر از تلگرام است). توضیح کامل در `examples/RUBIKA.md`.

A complete bot for [Rubika](https://rubika.ir) is also available at `examples/rubika_bot.py`, with strong protection against Rubika's flood limits (which are far stricter than Telegram's). Full details in `examples/RUBIKA.md`.
