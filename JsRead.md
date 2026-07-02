# obsidianx-teleconsole (Node.js)

کلاینت Node.js برای اتصال به پل TCP پلاگین **ObsidianX TeleConsole** روی سرور PocketMine-MP.
Node.js client for connecting to the **ObsidianX TeleConsole** plugin's TCP bridge on a PocketMine-MP server.

ساخته | Built by: **MrLeMoNIR x amirxd**

بدون هیچ وابستگی خارجی — فقط ماژول `net` استاندارد Node.js.
Zero external dependencies — uses only Node's built-in `net` module.

## نصب | Install

```bash
npm install ./obsidianx-teleconsole
```

یا در `package.json` پروژه‌ی خودتان:
Or in your own project's `package.json`:

```json
"dependencies": {
  "obsidianx-teleconsole": "file:../path/to/obsidianx-teleconsole"
}
```

## استفاده سریع | Quick usage

```javascript
const { ObsidianXClient } = require('obsidianx-teleconsole');

(async () => {
  const client = new ObsidianXClient({ host: '127.0.0.1', port: 25566, token: 'YOUR_TOKEN' });
  await client.connect();
  console.log(await client.sendCommand('say Hello!'));
  client.close();
})();
```

## دریافت لاگ زنده‌ی کنسول | Receiving the live console log

اگر `log-stream.enabled: true` در کانفیگ پلاگین باشد، سرور به‌صورت خودکار لاگ کنسول را برای شما می‌فرستد (دسته‌ای، هر ۲ ثانیه):

If `log-stream.enabled: true` in the plugin's config, the server automatically pushes the console log to you (batched, every 2 seconds):

```javascript
const { ObsidianXClient } = require('obsidianx-teleconsole');

const client = new ObsidianXClient({ host: '127.0.0.1', port: 25566, token: 'YOUR_TOKEN' });
client.on('log', (text) => console.log('[LIVE LOG]', text));

await client.connect();
```

پیش‌نیاز روی سرور PocketMine-MP: پلاگین TeleConsole باید نصب باشد و `tcp-bridge.enabled: true` در `config.yml` آن تنظیم شده باشد.
Prerequisite on the PocketMine-MP server: the TeleConsole plugin must be installed with `tcp-bridge.enabled: true` set in its `config.yml`.

برای یک بات تلگرام کامل و آماده، به پوشه‌ی `examples/` نگاه کنید.
For a complete, ready-to-run Telegram bot, see the `examples/` folder.
