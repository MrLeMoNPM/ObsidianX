# ObsidianX — PocketMine-MP Library Pack

**ساخته شده توسط | Built by:** `MrLeMoNIR x amirxd`

یک پک کتابخونه‌ای برای سرورهای PocketMine-MP که شامل چند پلاگین وانیلا/یوتیلیتی و یک پل اختصاصی بین **کنسول سرور** و **تلگرام** است.
A curated PocketMine-MP server pack bundling several vanilla/utility plugins plus a custom-built bridge between your **server console** and **Telegram**.

---

## 📦 محتویات پک | What's inside

| پلاگین / Plugin | نسخه / Version | سازنده اصلی / Original Author | توضیح / Description |
|---|---|---|---|
| **PocketMine-MP** (NG fork) | 5.30.2 | PMMP Team | هسته سرور / Core server software |
| **TeleConsole** ✨ جدید/NEW | 1.1.0 | **MrLeMoNIR x amirxd** | پل کنسول ↔ تلگرام + پل TCP برای Python/Node.js / Console ↔ Telegram bridge + TCP bridge for Python/Node.js |
| AZVanillaMobs | 1.0.0 | BeeAZ | موب‌های وانیلا با AI بهینه / Optimized vanilla mob AI |
| BubbleElevator | 1.0.1 | MadoxMC | ستون حباب آب وانیلا / Vanilla bubble columns |
| CustomKnockBack | 0.0.1 | MadoxMc | تنظیم ناک‌بک سفارشی / Custom knockback tuning |
| Elytra | 0.0.4 | JavierLeon9966, MadoxMc | بال‌پره و فایرورک بوست / Elytra + firework boost |
| LiveXYZ | 1.0.1 | dktapps | نمایش لحظه‌ای مختصات بازیکن / Real-time player coordinates |
| MacePM | 1.0.2 | XeonCh | سلاح Mace و Wind Charge / Mace & Wind Charge |
| NetherPortal | 1.0.0 | BeeAZ, AEDXDEV, MadoxMc | پورتال جهنم وانیلا / Vanilla Nether portals |
| PersonaSkin | 1.3.2 | PresentKim | پشتیبانی اسکین‌های Persona / Persona-skin support |
| PetsChoice | 0.0.1 | MadoxMC | سیستم انتخاب پت / Pet selection system |
| PiggyFactions | 2.1.1 | DaPigGuy, MadoxMc | سیستم فکشن کامل / Full factions system |
| Sponge | 0.3.0 | Catalyst Serendipity Team | بلاک اسفنج وانیلا / Vanilla sponge block |
| VanillaGenerator | 0.0.5 | Muqsit | جنریتور دنیای وانیلا / Vanilla world generator |
| VanillaHopper | 2.2.2 | ColinHDev | مکانیک هاپر وانیلا / Vanilla hopper mechanics |
| VanillaMinecarts | 1.0.0 | pixelwhiz | ماینکارت و ریل وانیلا / Vanilla minecarts & rails |

> هر پلاگین با همان نام و نسخه‌ی اصلی‌اش، **بدون هیچ تغییری در کد یا نویسنده**، در این پک قرار گرفته است. تمام حقوق این پلاگین‌ها متعلق به سازندگان اصلی آن‌هاست.
> Every plugin above ships **unmodified**, with its original author credit intact. All rights to these plugins remain with their original creators — ObsidianX simply bundles them together for convenience.

---

## ⚡ نصب سریع | Quick install

1. فایل `PocketMine-MP.phar` را اجرا کنید تا سرور شما بالا بیاید (یکبار اجرا کنید تا پوشه‌ها ساخته شوند).
   Run `PocketMine-MP.phar` once so your server generates its folder structure.
2. تمام فایل‌های داخل پوشه `plugins/` این پک را داخل پوشه `plugins/` سرور خودتان کپی کنید.
   Copy everything inside this pack's `plugins/` folder into your server's own `plugins/` folder.
3. سرور را Restart کنید.
   Restart the server.

```bash
java -jar PocketMine-MP.phar
```
> توجه: PocketMine-MP روی PHP اجرا می‌شود نه جاوا؛ از launcher رسمی PMMP (start.cmd / start.sh) برای اجرا استفاده کنید.
> Note: PocketMine-MP runs on PHP, not Java — use the official PMMP launcher (`start.cmd` / `start.sh`) to start it.

---

## 🤖 TeleConsole — پل تلگرام به کنسول سرور | Telegram ↔ Console Bridge

### ✨ امکانات | Features

- **ورود با رمز مشترک، همین و تمام** — یک رمز در کانفیگ تعیین می‌کنید؛ هرکس آن رمز را در بات وارد کند، دسترسی کامل به کنسول پیدا می‌کند.
  **A single shared password, that's it** — set one password in the config; anyone who enters it in the bot gets full console access.
- بعد از ورود، هر پیامی که بفرستید مستقیماً به‌عنوان دستور در کنسول سرور اجرا می‌شود و خروجی‌اش برایتان برمی‌گردد.
  Once logged in, anything you send runs directly as a console command, and the output comes back to you.
- **لاگ زنده‌ی کنسول** هم به‌صورت خودکار برای شما ارسال می‌شود — یعنی هر چیزی که در کنسول سرور چاپ می‌شود (join/leave بازیکن‌ها، خطاها، پیام‌های پلاگین‌های دیگر و غیره) را در تلگرام هم می‌بینید.
  You also automatically receive the **live console log** — everything printed to the server console (player joins/leaves, errors, messages from other plugins, etc.) shows up in Telegram too.
- لاگ‌ها به‌صورت دسته‌ای (Batch) و با فاصله‌ی زمانی مشخص (پیش‌فرض هر ۲ ثانیه) ارسال می‌شوند، نه خط‌به‌خط؛ این‌طور تلگرام هرگز بات را به‌خاطر ارسال پیام زیاد در ثانیه محدود یا اسپم تشخیص نمی‌دهد.
  Logs are sent in batches at a fixed interval (2 seconds by default), not line-by-line — this way Telegram never rate-limits or flags the bot as spam for sending too many messages per second.
- محدودیت تلاش رمز: بعد از ۵ تلاش ناموفق، آن چت به مدت ۵ دقیقه قفل می‌شود.
  Password attempt limiting: after 5 failed attempts, that chat is locked out for 5 minutes.
- کاملاً **Async**: هیچ‌کدام از این کارها (Polling تلگرام، خواندن لاگ، ارسال پیام) روی Thread اصلی سرور اجرا نمی‌شوند؛ صفر تاثیر روی TPS.
  Fully **async**: none of this (Telegram polling, reading the log, sending messages) runs on the server's main thread — zero TPS impact.
- ساخته‌شده با **UltraRequest** (کتابخونه HTTP اختصاصی amirxd) برای ارسال‌های خروجی.
  Built on **UltraRequest** (amirxd's own async HTTP library) for outgoing sends.

### 🧭 دو روش اتصال | Two ways to connect

| روش / Mode | برای چه کسی خوب است / Best for |
|---|---|
| **۱) بات کاملاً داخل PHP** (همین بخش) | کسانی که فقط می‌خواهند سریع یک بات تلگرام راه بیندازند بدون نوشتن کد جداگانه |
| **۲) پل TCP برای Python / Node.js** ✨ | کسانی که می‌خواهند منطق بات خودشان را به Python یا Node.js بنویسند — به بخش [«اتصال از Python / Node.js»](#-اتصال-از-python--nodejs--پل-tcp--connecting-from-python--nodejs--tcp-bridge) پایین‌تر نگاه کنید |

می‌توانید فقط یکی را فعال کنید یا هر دو را همزمان.
Enable just one, or both at the same time.

### 🔧 راه‌اندازی گام‌به‌گام | Step-by-step setup

**۱) ساخت بات تلگرام | Create your Telegram bot**

1. در تلگرام به [@BotFather](https://t.me/BotFather) پیام دهید.
   Message [@BotFather](https://t.me/BotFather) on Telegram.
2. دستور `/newbot` را بزنید و یک نام و یوزرنیم برای بات انتخاب کنید.
   Send `/newbot` and choose a name + username for your bot.
3. BotFather یک **توکن** به شکل `123456789:AAExxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` به شما می‌دهد. این توکن را کپی کنید.
   BotFather gives you a **token** like `123456789:AAExxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` — copy it.

**۲) تنظیم کانفیگ | Configure the plugin**

بعد از یک بار اجرا و توقف سرور، این فایل ساخته می‌شود:
After running the server once and stopping it, this file will exist:

```
plugins_data/TeleConsole/config.yml
```

آن را باز کنید و مقادیر را پر کنید:
Open it and fill in the values:

```yaml
bot-token: "123456789:AAExxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
password: "یک-رمز-قوی-اینجا-بگذارید"
poll-timeout: 15
reply-to-telegram: true
max-reply-length: 3500

log-stream:
  enabled: true
  interval-seconds: 2
  max-batch-length: 3500
```

| کلید / Key | توضیح / Description |
|---|---|
| `bot-token` | توکنی که از BotFather گرفتید / The token you got from BotFather |
| `password` | رمزی که هر کاربر تلگرام باید برای دسترسی به کنسول وارد کند — **این را با هیچکس که نمی‌خواهید دسترسی کنسول داشته باشد به اشتراک نگذارید** / The password every Telegram user must enter to get console access — **never share this with anyone you don't want to have console access** |
| `reply-to-telegram` | اگر `true` باشد، خروجی دستور به تلگرام برمی‌گردد / If `true`, command output is sent back to Telegram |
| `max-reply-length` | حداکثر طول پاسخ قبل از بریده‌شدن (محدودیت تلگرام ۴۰۹۶ کاراکتر است) / Max reply length before truncation (Telegram's hard limit is 4096 characters) |
| `log-stream.enabled` | فعال/غیرفعال کردن ارسال لاگ زنده / Enable/disable live log streaming |
| `log-stream.interval-seconds` | هر چند ثانیه یک‌بار، لاگ‌های جمع‌شده در یک پیام ارسال شوند (کمتر از ۱ ثانیه توصیه نمی‌شود) / How often accumulated logs are sent as one message (less than 1 second is not recommended) |
| `log-stream.max-batch-length` | حداکثر طول هر پیام لاگ (خطوط قدیمی‌تر بریده می‌شوند) / Max length of each log message (older lines get truncated) |

**۳) ری‌استارت و تست | Restart and test**

1. سرور را Restart کنید.
   Restart the server.
2. در تلگرام به بات خود پیام `/start` بدهید.
   Send `/start` to your bot on Telegram.
3. بات از شما رمز را می‌خواهد؛ رمزی که در `config.yml` گذاشتید را ارسال کنید.
   The bot will ask for the password; send the one you set in `config.yml`.
4. بعد از تایید، هر دستوری را امتحان کنید، مثلاً:
   Once confirmed, try any command, for example:
   - `list` → لیست بازیکنان آنلاین / list of online players
   - `say Hello from Telegram!`
   - `whitelist add YourName`
5. کمی صبر کنید — به‌زودی لاگ زنده‌ی کنسول هم شروع به رسیدن می‌کند.
   Wait a moment — the live console log will soon start arriving too.

> هرکس رمز را بداند و در بات وارد کند، دسترسی کامل کنسول (هم‌سطح Op) پیدا می‌کند. اگر چند نفر باید دسترسی داشته باشند، همین یک رمز را با آن‌ها به اشتراک بگذارید — نیازی به آیدی یا تنظیمات جداگانه نیست.
> Anyone who knows the password and enters it in the bot gets full (Op-level) console access. If multiple people need access, just share this one password with them — no separate IDs or settings needed.

### 🛠️ دستورات داخل سرور | In-server commands

| دستور / Command | توضیح / Description |
|---|---|
| `/teleconsole status` | وضعیت اتصال تلگرام، پل TCP، و لاگ زنده را نشان می‌دهد / Shows Telegram, TCP bridge, and live-log status |
| `/teleconsole reload` | کانفیگ را دوباره می‌خواند (نیاز به Restart برای اعمال کامل) / Reloads the config (a full restart is recommended to fully apply) |

اسم‌های مستعار: `/tgbridge`, `/tc`
Aliases: `/tgbridge`, `/tc`

### 🐍 🟢 اتصال از Python / Node.js — پل TCP | Connecting from Python / Node.js — TCP Bridge

اگر می‌خواهید بات تلگرام (یا هر بات دیگری) را به زبان **Python** یا **Node.js** بنویسید و از طریق آن به کنسول سرور دستور بفرستید، این بخش برای شماست.

If you want to write your Telegram bot (or any other bot) in **Python** or **Node.js** and send commands to the server console through it, this section is for you.

#### ۱) فعال کردن پل TCP در کانفیگ | Enable the TCP bridge in the config

فایل `plugins_data/TeleConsole/config.yml` را باز کنید و بخش `tcp-bridge` را ویرایش کنید:
Open `plugins_data/TeleConsole/config.yml` and edit the `tcp-bridge` section:

```yaml
tcp-bridge:
  enabled: true
  host: "127.0.0.1"
  port: 25566
  token: "یک-توکن-طولانی-و-تصادفی-اینجا-بگذارید"
```

| کلید / Key | توضیح / Description |
|---|---|
| `enabled` | باید `true` باشد تا پل TCP فعال شود / Must be `true` to enable the TCP bridge |
| `host` | آی‌پی که پل روی آن گوش می‌دهد؛ برای امنیت بیشتر روی `127.0.0.1` بگذارید مگر بات شما روی سرور دیگری اجرا می‌شود / The IP the bridge listens on; keep it `127.0.0.1` unless your bot runs on a different machine |
| `port` | پورت TCP (باید در فایروال باز باشد اگر `host` غیر از `127.0.0.1` است) / TCP port (must be opened in the firewall if `host` isn't `127.0.0.1`) |
| `token` | رشته‌ای که بات شما برای احراز هویت استفاده می‌کند — نقش همان «رمز» بخش تلگرام را دارد، فقط برای اتصال مستقیم / A string your bot uses to authenticate — plays the same role as the "password" in the Telegram section, just for direct connections |

سرور را Restart کنید. در لاگ باید ببینید:
Restart the server. You should see in the log:
```
پل TCP برای اتصال بات‌های Python/Node.js فعال شد روی 127.0.0.1:25566
TCP bridge for Python/Node.js bots started on 127.0.0.1:25566
```

#### ۲) پروتکل ارتباطی | The wire protocol

پل روی TCP خام کار می‌کند: هر پیام یک JSON در یک خط (newline-delimited JSON) است.

The bridge speaks raw TCP with newline-delimited JSON.

```
→ ارسال / send:    {"type":"auth","token":"YOUR_TOKEN"}\n
← دریافت / receive: {"type":"auth_result","ok":true}\n

→ ارسال / send:    {"type":"command","command":"say hi","request_id":"abc123"}\n
← دریافت / receive: {"type":"output","request_id":"abc123","command":"say hi","output":"..."}\n

← دریافت بدون درخواست / unsolicited receive (live log): {"type":"log","output":"..."}\n
```

`request_id` اختیاری است اما توصیه می‌شود تا بتوانید پاسخ‌ها را با درخواست‌های خودتان جفت کنید. پیام‌های `"type":"log"` بدون درخواست قبلی و به‌صورت خودکار برای هر کلاینت متصل و احراز‌هویت‌شده ارسال می‌شوند.

`request_id` is optional but recommended so you can match responses to your own requests. `"type":"log"` messages arrive unsolicited and are automatically broadcast to every connected, authenticated client.

#### ۳) استفاده از کتابخونه‌ی رسمی پایتون | Using the official Python library

```bash
cd clients/python
pip install -e .
```

نمونه‌ی ساده (Sync) با دریافت لاگ زنده:
Simple example (sync) with live log reception:

```python
from obsidianx_teleconsole import ObsidianXClient

def on_log(text):
    print("[LIVE LOG]", text)

with ObsidianXClient(host="127.0.0.1", port=25566, token="YOUR_TOKEN", on_log=on_log) as client:
    output = client.send_command("say Hello from Python!")
    print(output)
```

نمونه‌ی Async (برای بات‌های asyncio مثل python-telegram-bot v20+):
Async example (for asyncio bots like python-telegram-bot v20+):

```python
import asyncio
from obsidianx_teleconsole import AsyncObsidianXClient

async def on_log(text):
    print("[LIVE LOG]", text)

async def main():
    client = AsyncObsidianXClient(host="127.0.0.1", port=25566, token="YOUR_TOKEN", on_log=on_log)
    await client.connect()
    output = await client.send_command("list")
    print(output)
    await client.close()

asyncio.run(main())
```

یک بات تلگرام کامل و آماده در `clients/python/examples/telegram_bot.py` قرار دارد که همان جریان **رمز مشترک + لاگ زنده** را با Python پیاده‌سازی می‌کند — فقط توکن تلگرام، توکن پل، و رمز عبور را داخل فایل عوض کنید و اجرا کنید:

A ready-made Telegram bot in `clients/python/examples/telegram_bot.py` implements the exact same **shared-password + live log** flow in Python — just edit the Telegram token, bridge token, and password at the top of the file and run it:

```bash
cd clients/python/examples
pip install -r requirements.txt
python telegram_bot.py
```

**می‌خوای به‌جای تلگرام از روبیکا استفاده کنی؟ | Want to use Rubika instead of Telegram?**
یک بات کامل و آماده برای [روبیکا](https://rubika.ir) هم در `clients/python/examples/rubika_bot.py` قرار دارد، با محافظت ویژه در برابر محدودیت ارسال روبیکا (که خیلی سریع‌تر از تلگرام یک بات را اسپم تشخیص می‌دهد). راهنمای کامل: `clients/python/examples/RUBIKA.md`.
A complete, ready-made bot for [Rubika](https://rubika.ir) is also available at `clients/python/examples/rubika_bot.py`, with special protection against Rubika's flood limits (which flag bots as spam much faster than Telegram). Full guide: `clients/python/examples/RUBIKA.md`.

#### ۴) استفاده از کتابخونه‌ی رسمی Node.js | Using the official Node.js library

```javascript
const { ObsidianXClient } = require('obsidianx-teleconsole');

(async () => {
  const client = new ObsidianXClient({ host: '127.0.0.1', port: 25566, token: 'YOUR_TOKEN' });
  client.on('log', (text) => console.log('[LIVE LOG]', text));

  await client.connect();
  const output = await client.sendCommand('say Hello from Node.js!');
  console.log(output);
})();
```

یک بات تلگرام کامل و آماده (همان جریان رمز مشترک + لاگ زنده) در `clients/nodejs/examples/telegram_bot.js` قرار دارد:
A ready-made Telegram bot (same shared-password + live log flow) is in `clients/nodejs/examples/telegram_bot.js`:

```bash
cd clients/nodejs/examples
npm install
node telegram_bot.js
```

(قبل از اجرا، توکن تلگرام، توکن پل، و رمز عبور را در بالای فایل عوض کنید.)
(Before running, edit the Telegram token, bridge token, and password at the top of the file.)

#### ۵) نکات مهم پل TCP | Important notes about the TCP bridge

- پل کاملاً **Async و بدون-مسدودکننده** است.
  The bridge is fully **async and non-blocking**.
- می‌توانید چند بات (Python + Node.js + هر چیز دیگری) را همزمان به همین پورت وصل کنید.
  You can connect multiple bots simultaneously to the same port.
- پیام‌های لاگ زنده به‌صورت خودکار برای همه‌ی کلاینت‌های متصل و احراز‌هویت‌شده broadcast می‌شوند، درست مثل رفتار بخش تلگرام.
  Live log messages are automatically broadcast to every connected, authenticated client — same behavior as the Telegram side.

### 🔒 نکات امنیتی | Security notes

- رمز عبور (`password`) و توکن پل TCP (`tcp-bridge.token`) را مثل یک رمز عبور Root نگه دارید — هرکس این‌ها را داشته باشد به کنسول سرور دسترسی کامل پیدا می‌کند.
  Treat the `password` and the TCP bridge token (`tcp-bridge.token`) like root passwords — anyone who has them gets full console access.
- بعد از ۵ تلاش رمز اشتباه، آن چت تلگرام به مدت ۵ دقیقه قفل می‌شود تا حدس‌زدن خودکار رمز سخت‌تر شود.
  After 5 wrong password attempts, that Telegram chat is locked out for 5 minutes to make brute-forcing harder.
- اگر می‌خواهید دسترسی را بعداً از کسی بگیرید، فقط رمز را در `config.yml` تغییر دهید و `/teleconsole reload` بزنید (یا سرور را Restart کنید) — همه باید دوباره وارد شوند.
  To revoke someone's access later, just change the password in `config.yml` and run `/teleconsole reload` (or restart the server) — everyone will need to log in again.

## 🧵 معماری فنی TeleConsole | TeleConsole architecture

- یک **Thread اختصاصی** (`TelegramPollThread`) به‌صورت دائمی و مستقل از Thread اصلی سرور، با تکنیک Long-Polling به API تلگرام متصل می‌ماند و پیام‌های جدید را می‌گیرد.
  A **dedicated Thread** (`TelegramPollThread`) stays connected to the Telegram API via long-polling, completely independent of the server's main thread.
- وقتی پیام جدیدی برسد، با مکانیزم `SleeperHandler` (همان سیستمی که RakLib برای بیدار کردن Thread اصلی استفاده می‌کند) Thread اصلی سرور بدون نیاز به Poll کردن مداوم، بیدار و آگاه می‌شود — یعنی صفر هزینه‌ی اضافه روی تیک سرور.
  When a new message arrives, the server's main thread is woken up via `SleeperHandler` (the same mechanism RakLib uses) — zero extra cost on the server tick, no constant polling.
- اجرای دستور و دریافت خروجی آن، در Thread اصلی و با یک `ConsoleCommandSender` سفارشی انجام می‌شود تا امنیت و سازگاری کامل با تمام پلاگین‌های دیگر حفظ شود.
  Command execution happens safely on the main thread through a custom `ConsoleCommandSender`, keeping full compatibility with every other plugin.
- **لاگ زنده** با یک `ConsoleLogAttachment` پیاده‌سازی شده که مستقیماً به لاگر اصلی PocketMine (`AttachableThreadSafeLogger`) متصل می‌شود؛ هر خط لاگ در یک صف Thread-safe جمع می‌شود و هر ۲ ثانیه (قابل تنظیم) یک‌بار به‌صورت دسته‌ای، پاک‌سازی‌شده از کدهای رنگی، به تلگرام و کلاینت‌های TCP ارسال می‌شود — این batching دقیقاً همان چیزی است که جلوی محدودیت نرخ ارسال تلگرام (Flood Control) را می‌گیرد.
  **Live log** is implemented via a `ConsoleLogAttachment` hooked directly into PocketMine's core logger (`AttachableThreadSafeLogger`); every log line is queued thread-safely and flushed as a color-stripped batch every 2 seconds (configurable) to both Telegram and TCP clients — this batching is exactly what keeps the bot under Telegram's flood-control rate limits.
- ارسال پاسخ‌ها و لاگ‌ها به تلگرام از طریق **UltraRequest** (`Amirxd\UltraRequest`) و `AsyncPool` داخلی PocketMine انجام می‌شود — کاملاً async و بدون مسدود کردن سرور.
  Replies and logs are sent to Telegram through **UltraRequest** (`Amirxd\UltraRequest`) using PocketMine's own `AsyncPool` — fully async, never blocking the server.
- پل TCP (`ConsoleBridgeServerThread`) روی همین اصل کار می‌کند: یک Thread جدا با `stream_socket_server` خام به اتصالات چندگانه گوش می‌دهد، پیام‌ها را با `stream_select` غیرمسدودکننده می‌خواند، و از طریق همان مکانیزم `ThreadSafeArray` + `SleeperHandler` دستورات و پیام‌های لاگ را رد و بدل می‌کند.
  The TCP bridge (`ConsoleBridgeServerThread`) follows the same principle: a separate thread listens for multiple connections using plain `stream_socket_server`, reads non-blockingly via `stream_select`, and exchanges commands and log messages through the same `ThreadSafeArray` + `SleeperHandler` mechanism.

## 📜 لایسنس و حقوق | License & credits

- پلاگین **TeleConsole** و کارهای جمع‌آوری/بسته‌بندی این پک: **MrLeMoNIR x amirxd** — تحت MIT License.
  The **TeleConsole** plugin and the curation/packaging of this pack: **MrLeMoNIR x amirxd** — MIT License.
- کتابخونه‌های کلاینت **Python** (`obsidianx-teleconsole`) و **Node.js** (`obsidianx-teleconsole`) برای اتصال بات‌های خارجی به پل TCP: **MrLeMoNIR x amirxd** — تحت MIT License.
  The **Python** (`obsidianx-teleconsole`) and **Node.js** (`obsidianx-teleconsole`) client libraries for connecting external bots to the TCP bridge: **MrLeMoNIR x amirxd** — MIT License.
- کتابخونه **UltraRequest**: ساخته‌ی **amirxd**.
  The **UltraRequest** library: created by **amirxd**.
- تمام پلاگین‌های دیگر در این پک، تحت لایسنس اصلی خودشان باقی می‌مانند و حقوق آن‌ها متعلق به نویسندگان اصلی است. این پک هیچ ادعای مالکیتی روی آن پلاگین‌ها ندارد.
  All other plugins in this pack remain under their own original licenses, and all rights belong to their original authors. This pack makes no ownership claim over them.
- **PocketMine-MP**: تحت LGPL-3.0 توسط تیم PMMP.
  **PocketMine-MP**: LGPL-3.0, by the PMMP Team.

## ❓ سوالات متداول | FAQ

**سرور بالا نمی‌آید؟ | Server won't start?**
مطمئن شوید نسخه PHP شما با نسخه‌ی موردنیاز PocketMine-MP این پک سازگار است و افزونه‌های لازم (curl، mbstring، …) نصب‌اند.
Make sure your PHP version matches what this PocketMine-MP build requires, and that required extensions (curl, mbstring, …) are installed.

**بات تلگرام جواب نمی‌دهد؟ | Bot doesn't respond?**
1. توکن `bot-token` را دوباره چک کنید.
   Double-check the `bot-token`.
2. مطمئن شوید `password` در `config.yml` خالی نیست.
   Make sure `password` in `config.yml` isn't empty.
3. مطمئن شوید حداقل یک بار `/start` را به بات زده‌اید.
   Make sure you've sent `/start` to the bot at least once.

**رمز را فراموش کرده‌ام یا می‌خواهم عوضش کنم؟ | I forgot the password, or want to change it?**
فقط مقدار `password` را در `config.yml` تغییر دهید و `/teleconsole reload` بزنید یا سرور را Restart کنید.
Just change the `password` value in `config.yml` and run `/teleconsole reload` or restart the server.

**بات Python/Node.js من نمی‌تواند به پل TCP وصل شود؟ | My Python/Node.js bot can't connect to the TCP bridge?**
1. مطمئن شوید `tcp-bridge.enabled: true` است و سرور را Restart کرده‌اید.
   Make sure `tcp-bridge.enabled: true` and you restarted the server.
2. `host` و `port` داخل کد بات با مقادیر داخل `config.yml` یکسان باشند.
   Make sure the `host`/`port` in your bot's code match what's in `config.yml`.
3. توکن پل (`tcp-bridge.token`) را دقیقاً همان‌طور که در کانفیگ نوشته‌اید، در بات هم وارد کنید.
   Enter the bridge token (`tcp-bridge.token`) in your bot exactly as written in the config.
4. اگر بات روی ماشین دیگری اجرا می‌شود، `host` باید `0.0.0.0` باشد و پورت در فایروال باز باشد.
   If your bot runs on a different machine, `host` must be `0.0.0.0` and the port must be open in the firewall.

**آیا می‌توانم همزمان هم از بات PHP داخلی و هم از پل TCP استفاده کنم؟ | Can I use both the built-in PHP bot and the TCP bridge at once?**
بله، این دو کاملاً مستقل از هم هستند و می‌توانید هر دو را همزمان فعال کنید.
Yes, they're completely independent and can both be enabled at the same time.

**آیا لاگ زنده باعث اسپم‌شدن بات در تلگرام می‌شود؟ | Does the live log spam the bot on Telegram?**
نه — لاگ‌ها هر ۲ ثانیه (قابل تنظیم) یک‌بار به‌صورت دسته‌ای ارسال می‌شوند، نه خط‌به‌خط، دقیقاً برای اینکه از محدودیت نرخ ارسال تلگرام (Flood Control) عبور نکنید.
No — logs are sent in batches every 2 seconds (configurable), not line-by-line, exactly so the bot never hits Telegram's flood-control rate limits.
