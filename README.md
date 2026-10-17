# TwinDesk

> ⭐ **If you find this project useful, please give it a star!** It helps others discover it and motivates continued development.
>
> ⭐ **اگر این پروژه برایتان مفید بود، لطفاً به آن ستاره (Star) بدهید!** این کار به دیگران در کشف پروژه کمک می‌کند و انگیزهٔ توسعهٔ بیشتر را فراهم می‌آورد.

---

## English

This is a fork of [InukaAsith/TwinDesk](https://github.com/InukaAsith/TwinDesk) by **Javad Hamed** ([javadhamed-ctrl](https://github.com/javadhamed-ctrl)), with a fix for the Windows Firewall self-check bug (see below).

### About TwinDesk

Use two computers as one desk: Mac, Windows and Linux on the same network. Share screens, mouse and keyboard, clipboard, files, sound, notifications, terminals and apps.

TwinDesk pairs two computers on your local network. One app on each side does the job of a software KVM, a second-monitor app, a clipboard and file-sharing tool and a remote-app viewer. Everything travels directly between the two machines over an encrypted link. There's no cloud account and no relay server.

### What you can do

- **Use one computer as a second screen** — Extend your Mac onto the PC with a real virtual display, or mirror it. Low-latency H.264 over WebRTC.
- **One mouse and keyboard for both** — Push the pointer off the edge of the screen and keep working on the other computer.
- **Clipboard both ways** — Copy on one computer and paste on the other.
- **Files and folders** — Drag files across the screen edge and drop them anywhere.
- **Apps from the other computer** — Open the PC's apps on the Mac (or vice versa), each in its own window.
- **Notifications** — See one computer's notifications on the other as native notifications.
- **Terminal** — Open a shell on the other computer without passwords.
- **Sound** — Hear one computer on the other, in either direction.

### Platforms

| Pair | Status |
|---|---|
| Mac ↔ Windows PC | Every feature above |
| Mac ↔ Mac | Every feature above |
| PC ↔ PC | Every feature above |
| Linux ↔ Mac, PC or Linux | Every feature above |

### Ports

TCP **47800** (control link) and UDP **47801** (discovery) on the local network.

### Build and run

You need [Node.js](https://nodejs.org) 18+ on every platform.

**Windows 10 / 11**

```
cd windows
npm install
npm run build:helper
npm start
npm run dist
```

The Setup screen offers to add the firewall rule and set the network to Private. It can also install the optional Virtual Display Driver for Extend.

### Windows Firewall self-check fix (this fork)

**Problem:** TwinDesk's firewall self-check runs PowerShell non-elevated. On Windows, `Get-NetFirewallApplicationFilter` returns an empty result for non-administrator users, so the check always reports *"TwinDesk isn't allowed through Windows Firewall on this network."* and discovery stays blocked in the UI even when the firewall rules are correctly in place.

**Fix (this fork):** The check now runs elevated (one UAC prompt) and reads the result from a temp file (working around the fact that `runElevated` loses stdout, and stripping the UTF-8 BOM that PowerShell 5.1 writes). Firewall rules for TCP 47800 and UDP 47801 (inbound/outbound, all profiles) are also added.

### Privacy

TwinDesk only talks to computers you have paired with, directly over your local network. It has no accounts, telemetry or cloud relay.

### License

TwinDesk is free software, licensed under the [GNU General Public License v3.0](LICENSE). Copyright © 2026 inukaasith. Parts are adapted from [DeskPad](https://github.com/Stengo/DeskPad) (MIT).

---

## فارسی

این یک فورک از [InukaAsith/TwinDesk](https://github.com/InukaAsith/TwinDesk) توسط **جواد حامد** ([javadhamed-ctrl](https://github.com/javadhamed-ctrl)) است که مشکل چک فایروال ویندوز را رفع می‌کند (توضیح در بخش انگلیسی بالا).

### دربارهٔ TwinDesk

دو کامپیوتر را به‌عنوان یک میز واحد استفاده کنید: مک، ویندوز و لینوکس در یک شبکه. اشتراک‌گذاری صفحه، ماوس و کیبورد، کلیپ‌بورد، فایل‌ها، صدا، اعلان‌ها، ترمینال و برنامه‌ها.

TwinDesk دو کامپیوتر را در شبکهٔ محلی شما جفت می‌کند. یک برنامه در هر طرف کار یک KVM نرم‌افزاری، برنامهٔ مانیتور دوم، ابزار اشتراک‌گذاری کلیپ‌بورد و فایل و نمایشگر برنامهٔ راه دور را انجام می‌دهد. همه‌چیز مستقیماً بین دو ماشین از طریق یک لینک رمزگذاری‌شده منتقل می‌شود. حساب ابری و سرور رله‌ای وجود ندارد.

### کارهایی که می‌توانید انجام دهید

- **استفاده از یک کامپیوتر به‌عنوان مانیتور دوم** — مک خود را روی PC با یک نمایشگر مجازی واقعی گسترش دهید یا آینه کنید.
- **یک ماوس و کیبورد برای هر دو** — نشانگر را از لبهٔ صفحه خارج کنید و روی کامپیوتر دیگر کار کنید.
- **کلیپ‌بورد دوطرفه** — روی یک کامپیوتر کپی کنید و روی دیگری پیست کنید.
- **فایل‌ها و پوشه‌ها** — فایل‌ها را از لبهٔ صفحه بکشید و هر جایی رها کنید.
- **برنامه‌های کامپیوتر دیگر** — برنامه‌های PC را روی مک (یا برعکس) در پنجرهٔ جداگانه باز کنید.
- **اعلان‌ها** — اعلان‌های یک کامپیوتر را به‌صورت اعلان بومی روی دیگری ببینید.
- **ترمینال** — بدون رمز عبور یک شل روی کامپیوتر دیگر باز کنید.
- **صدا** — صدای یک کامپیوتر را در جهت‌های مختلف روی دیگری بشنوید.

### پلتفرم‌ها

| جفت | وضعیت |
|---|---|
| مک ↔ PC ویندوز | همهٔ قابلیت‌های بالا |
| مک ↔ مک | همهٔ قابلیت‌های بالا |
| PC ↔ PC | همهٔ قابلیت‌های بالا |
| لینوکس ↔ مک، PC یا لینوکس | همهٔ قابلیت‌های بالا |

### پورت‌ها

TCP **47800** (لینک کنترل) و UDP **47801** (کشف) در شبکهٔ محلی.

### ساخت و اجرا

به [Node.js](https://nodejs.org) نسخهٔ 18 یا بالاتر روی همهٔ پلتفرم‌ها نیاز دارید.

**ویندوز 10 / 11**

```
cd windows
npm install
npm run build:helper
npm start
npm run dist
```

صفحهٔ Setup پیشنهاد افزودن قاعدهٔ فایروال و تنظیم شبکه به Private را می‌دهد. همچنین می‌تواند درایور نمایشگر مجازی اختیاری برای Extend را نصب کند.

### رفع مشکل چک فایروال ویندوز (این فورک)

**مشکل:** چک فایروال TwinDesk پاورشل را بدون ارتقا (non-elevated) اجرا می‌کند. در ویندوز، `Get-NetFirewallApplicationFilter` برای کاربران غیر-ادمین نتیجهٔ خالی برمی‌گرداند، بنابراین چک همیشه پیام «TwinDesk isn't allowed through Windows Firewall on this network.» را نمایش می‌دهد و کشف (discovery) در رابط کاربری حتی وقتی قاعده‌های فایروال درست هستند مسدود می‌ماند.

**رفع (این فورک):** چک اکنون به‌صورت elevated (یک پنجرهٔ UAC) اجرا می‌شود و نتیجه را از یک فایل موقت می‌خواند (با توجه به اینکه `runElevated` خروجی stdout را از دست می‌دهد و BOM یونیکد ۸ که پاورشل ۵.۱ می‌نویسد پاک می‌شود). قاعده‌های فایروال برای TCP 47800 و UDP 47801 (ورودی/خروجی، همهٔ پروفایل‌ها) نیز افزوده می‌شوند.

### حریم خصوصی

TwinDesk فقط با کامپیوترهایی که جفت کرده‌اید مستقیماً از طریق شبکهٔ محلی صحبت می‌کند. حساب، تله‌متری یا سرور رله‌ای ندارد.

### مجوز

TwinDesk نرم‌افزار آزاد است و تحت [GNU General Public License v3.0](LICENSE) منتشر می‌شود. Copyright © 2026 inukaasith. بخش‌هایی از [DeskPad](https://github.com/Stengo/DeskPad) (MIT) اقتباس شده‌اند.

---

⭐ **اگر این پروژه برایتان مفید بود، لطفاً ستاره بدهید!** / **If you found this useful, please star the repo!** ⭐