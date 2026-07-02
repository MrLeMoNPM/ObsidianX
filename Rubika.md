# بات کنسول ObsidianX برای روبیکا | ObsidianX Console Bot for Rubika

فایل `rubika_bot.py` همان قابلیت «رمز مشترک + اجرای دستور در کنسول + لاگ زنده» را با کتابخونه‌ی [Rubka](https://rubika.ir) پیاده‌سازی می‌کند — با تمرکز ویژه روی جلوگیری از محدودیت ارسال (Flood/Spam Limit)، چون **روبیکا نسبت به تلگرام بسیار حساس‌تر است و خیلی سریع‌تر یک بات را اسپم تشخیص می‌دهد.**

`rubika_bot.py` implements the same "shared password + console commands + live log" flow using the [Rubka](https://rubika.ir) library — with special focus on avoiding flood/spam limits, because **Rubika is far more sensitive than Telegram and flags bots as spam much faster.**

## نصب | Install

```bash
cd clients/python
pip install -e .
cd examples
pip install -r requirements_rubika.txt
```

سپس در بالای `rubika_bot.py` این مقادیر را پر کن:
Then fill in these values at the top of `rubika_bot.py`:

```python
RUBIKA_BOT_TOKEN = "..."       # توکن بات روبیکا | your Rubika bot token
OBSIDIANX_HOST = "127.0.0.1"
OBSIDIANX_PORT = 25566
OBSIDIANX_TOKEN = "..."        # همان tcp-bridge.token در config.yml پلاگین
CONSOLE_PASSWORD = "..."       # رمزی که کاربران روبیکا باید وارد کنند
```

اجرا:
Run:

```bash
python rubika_bot.py
```

## چطور جلوی محدودیت روبیکا را می‌گیریم؟ | How we avoid Rubika's flood limit

فایل `rubika_rate_limiter.py` یک صف‌بندی هوشمند دارد که دو کار می‌کند:

The `rubika_rate_limiter.py` module implements smart queuing that does two things:

1. **فاصله‌ی سراسری بین پیام‌ها** — هیچ‌وقت بیش از یک پیام در هر `MIN_SEND_INTERVAL_SECONDS` ثانیه (پیش‌فرض ۲ ثانیه) ارسال نمی‌شود، حتی اگر ده‌ها اتفاق همزمان بخواهند پیام بفرستند.
   **Global spacing between messages** — never more than one message per `MIN_SEND_INTERVAL_SECONDS` (default 2s), even if dozens of events want to send at once.

2. **ادغام پیام‌های هم‌زمان یک چت** — اگر چند پیام برای همان چت قبل از نوبتش صف شوند (مثلاً چند خط لاگ پشت‌سرهم)، به‌جای چند پیام جدا، در **یک پیام** ادغام می‌شوند.
   **Merging simultaneous messages for the same chat** — if several messages for the same chat queue up before their turn (e.g. several log lines in a row), they get merged into **one** message instead of being sent separately.

3. **تشخیص و عقب‌نشینی خودکار** — اگر روبیکا خطایی شبیه به محدودیت ارسال برگرداند (کلماتی مثل `limit`, `flood`, `429` در پیام خطا)، بات خودکار ۱۰ تا ۳۰ ثانیه صبر می‌کند و دوباره تلاش می‌کند.
   **Automatic detection and backoff** — if Rubika returns an error that looks like a rate limit (keywords like `limit`, `flood`, `429` in the error), the bot automatically waits 10–30 seconds and retries.

### توصیه‌های اضافی برای روبیکا | Additional recommendations for Rubika

- در کانفیگ پلاگین (`config.yml`)، مقدار `log-stream.interval-seconds` را برای روبیکا بالاتر از پیش‌فرض تلگرام (۲ ثانیه) بگذار — مثلاً `5` یا `8` — چون این باعث می‌شود پیام‌های لاگ کمتری در واحد زمان تولید شوند و صف ادغام کمتر تحت فشار باشد:
  In the plugin's `config.yml`, set `log-stream.interval-seconds` higher than Telegram's default (2s) for Rubika — e.g. `5` or `8` — since this produces fewer log messages per unit time and keeps the merge queue less pressured:

  ```yaml
  log-stream:
    enabled: true
    interval-seconds: 6
    max-batch-length: 2500
  ```

- اگر با چند چت (چند کاربر) همزمان کار می‌کنی، `MIN_SEND_INTERVAL_SECONDS` را روی `2.0` یا بالاتر نگه دار؛ کمتر کردنش ریسک اسپم‌شدن را زیاد می‌کند.
  If you're serving several chats at once, keep `MIN_SEND_INTERVAL_SECONDS` at `2.0` or higher; lowering it increases spam-flagging risk.
- هیچ‌وقت مستقیماً `bot.send_message(...)` را به‌جای `sender.send(...)` صدا نزن — این کار محدودیت نرخ را دور می‌زند.
  Never call `bot.send_message(...)` directly instead of `sender.send(...)` — doing so bypasses the rate limiter entirely.

## دکمه‌ها | Buttons

بعد از ورود موفق، یک کیبورد با دو دکمه نمایش داده می‌شود:
After a successful login, a keypad with two buttons is shown:

- **📊 وضعیت | Status** — تعداد چت‌های فعال و صف ارسال فعلی را نشان می‌دهد.
  Shows the number of active chats and the current send queue size.
- **🚪 خروج | Logout** — دسترسی کنسول را برای آن چت لغو می‌کند.
  Revokes console access for that chat.

## اضافه کردن قابلیت‌های جدید | Adding new features

این فایل عمداً ساده نگه داشته شده تا راحت قابل توسعه باشد:
This file is deliberately kept simple so it's easy to extend:

- برای اضافه‌کردن دکمه‌ی جدید: یک `ChatKeypadBuilder().button(id="btn_x", text="...")` به `build_console_keypad()` اضافه کن و یک `@bot.on_callback("btn_x")` جدید بنویس.
  To add a new button: add a `ChatKeypadBuilder().button(id="btn_x", text="...")` to `build_console_keypad()` and write a new `@bot.on_callback("btn_x")`.
- برای هر پیامی که می‌فرستی، همیشه از `await sender.send(chat_id, text)` استفاده کن، نه `bot.send_message` مستقیم — تا محدودیت نرخ همیشه رعایت شود.
  For anything you send, always use `await sender.send(chat_id, text)`, never `bot.send_message` directly — so the rate limit is always respected.
