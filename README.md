# Usta (أسطى)

[English](#english) · [العربية](#arabic)

<a id="english"></a>

## English

Usta is a Windows desktop app that runs the plan → implement → review → merge loop between one orchestrator chat per project and the coding-agent CLIs you already pay for: Claude Code, Codex and Antigravity. You talk to the orchestrator; it creates the tasks and hands each one to an agent. The app checks every change before it merges it on your PC, and you step in only for decisions, short manual tests and approvals, in the app or on Telegram. Nothing is ever pushed to GitHub: you push yourself.

### Download

Get the newest `Usta-Setup-<version>.exe` from the [Releases](../../releases) page. Each release lists the installer's SHA-256.

### Requirements

- Windows 64-bit (x64). Tested on Windows 11.
- About 450 MB of disk space for the app, plus room for your projects' task folders.
- [Git for Windows](https://git-scm.com/download/win).
- [Claude Code](https://docs.claude.com/en/docs/claude-code), the standalone CLI, signed in with your own Claude subscription (`claude auth login`). It is required: it runs the orchestrator.
- Optional, for more agents:
  - the Codex CLI: you sign in to it inside Usta with your ChatGPT account;
  - the Antigravity CLI `agy`, signed in with your Google account.
  The app routes around an agent that is missing, signed out, or one you said you don't use.
- Recommended: Node.js on PATH. Claude's usage meter, the faster "ready" signal of orchestrator sessions and many MCP connectors need it.
- Optional: your own Telegram bot (made with BotFather), to answer questions from your phone.

### First run

1. Run `Usta-Setup-<version>.exe`. It installs for your user only (no admin rights), adds Start menu and desktop shortcuts, and opens Usta.
2. The Welcome card asks for your name (the orchestrator and agents call you by it) and which subscriptions you use. Change both later in Settings.
3. Pick your language in Settings → Language (العربية or English). The first start follows your Windows display language.
4. Add a project: **New project** or **Import existing repo** on the Dashboard, then pick a local git repository.
5. Start the orchestrator in the project. If it says Claude Code is not signed in, use **Log in to Claude Code**. On a new folder, click **Trust this folder**.
6. If you use Codex, click **Log in to Codex (app account)** in Agents & subscriptions.
7. Answer the Project start card (setup steps and checks, the project's CLAUDE.md, the lineup), then tell the orchestrator what to build.

Merges wait for your approval in a new project. "Merge automatically" can be turned on in Project settings once at least one check must pass before merging. Every merge is local, and an automatic one can be undone.

### Windows SmartScreen

The installer is not code-signed, so the first time Windows may show "Windows protected your PC". Click **More info**, then **Run anyway**. Check the file's SHA-256 against the release page first if you want to be sure it is the published file:

```powershell
Get-FileHash .\Usta-Setup-<version>.exe -Algorithm SHA256
```

### Updates

Usta updates itself from this repository's releases. It checks when it starts and every 6 hours, downloads a new version in the background, and then shows **Restart to update**. Nothing is installed until you click it. You can choose **Later** or **Skip this version**, or turn checking off in Settings → Updates. Your projects, history and settings stay. You can also install a newer installer over the old one by hand; your data stays then too.

### Privacy: what leaves your PC

- Your prompts, your code and the agents' work go to the providers you chose:
  - to Anthropic, OpenAI and Google through their official CLIs, signed in with your accounts;
  - to any API provider you add (code sent to an API provider passes through that provider);
  - local servers (Ollama, LM Studio) stay on your PC.
- Telegram: only if you pair it. Questions, notices, the morning digest and files you send to the bot go through Telegram's servers.
- Only when you use them: the MCP server registry (browsing connectors), GitHub (searching or installing skills), connectors you add, and your API providers' model lists and balances.
- **Update check:** Usta checks GitHub for a new version when it starts and every 6 hours. The check sends nothing about you or your projects; GitHub sees your IP address, as when you open a web page. Turn it off in Settings → Updates.
- No telemetry: no analytics and no crash reporting. The agent CLIs themselves follow their vendors' own terms.
- Keys you add are stored encrypted with Windows' own protection for your user, never in plain text. The app's local servers listen only on 127.0.0.1.

### Uninstall

Windows Settings → Apps → Usta → Uninstall. What stays on your PC until you delete it:

- the data folder `%APPDATA%\Usta`: projects, tasks, history, settings, the app's Codex sign-in and your encrypted keys;
- its backups in `%APPDATA%\Usta-backups`;
- in each project repository:
  - the app's folder `.usta` (`.delegate` in projects started with an older version), with the project's notes and run records;
  - any task branches that were not merged;
- Claude Code's own session files, kept by Claude Code in your user profile.

### Known limits

- Windows only.
- Executors' network access is only partly blocked on Windows.
- Codex task runs can read the app's data folder (Antigravity and Claude Code task runs cannot).
- The installer is not code-signed.

### License

TODO(Mostafa)

### Support

TODO(Mostafa)

---

<a id="arabic"></a>

<div dir="rtl">

## العربية

أسطى تطبيق لسطح المكتب على Windows يدير دورة الخطة ← التنفيذ ← المراجعة ← الـ merge. يعمل بين منسّق واحد لكل مشروع وأدوات CLI لـ agents البرمجة التي تدفع اشتراكها أصلًا: Claude Code وCodex وAntigravity. تتحدث مع المنسّق، فينشئ المهام ويسلّم كل مهمة إلى agent. ويفحص التطبيق كل تغيير قبل أن يعمل له merge على جهازك. ولا تتدخل أنت إلا للقرارات والاختبارات اليدوية القصيرة والموافقات، من التطبيق أو من Telegram. لا يتم أي push إلى GitHub أبدًا: الـ push تعمله أنت.

### التحميل

حمّل أحدث ملف `Usta-Setup-<version>.exe` من صفحة [Releases](../../releases). كل إصدار يذكر الـ SHA-256 الخاص بملف التثبيت.

### المتطلبات

- Windows بنظام 64-bit (x64). تمت تجربته على Windows 11.
- حوالي 450 ميجابايت للتطبيق، ومساحة لمجلدات مهام مشاريعك.
- [Git for Windows](https://git-scm.com/download/win).
- [Claude Code](https://docs.claude.com/en/docs/claude-code)، أداة الـ CLI المستقلة، مسجَّلة الدخول باشتراك Claude الخاص بك (`claude auth login`). وهي مطلوبة: فهي التي تشغّل المنسّق.
- اختياري، لمزيد من الـ agents:
  - Codex CLI: تسجّل الدخول إليه داخل أسطى بحساب ChatGPT الخاص بك؛
  - Antigravity CLI ‏`agy`، مسجَّل الدخول بحساب Google الخاص بك.
  التطبيق يتخطى الـ agent غير المثبّت، أو غير المسجَّل الدخول، أو الذي قلت إنك لا تستخدمه.
- يُنصح به: Node.js على الـ PATH. يحتاجه عدّاد استخدام Claude، وإشارة الجاهزية الأسرع لجلسات المنسّق، وكثير من الـ connectors من نوع MCP.
- اختياري: bot خاص بك على Telegram (تصنعه بـ BotFather)، لتجيب على الأسئلة من هاتفك.

### أول تشغيل

1. شغّل `Usta-Setup-<version>.exe`. يثبّت التطبيق لمستخدمك فقط (بدون صلاحيات مدير)، ويضيف اختصارات في قائمة Start وعلى سطح المكتب، ثم يفتح أسطى.
2. بطاقة الترحيب تسألك عن اسمك (المنسّق والـ agents ينادونك به)، وعن الاشتراكات التي تستخدمها. يمكنك تغييرهما لاحقًا من الإعدادات.
3. اختر لغتك من الإعدادات ← اللغة (العربية أو English). أول تشغيل يتبع لغة عرض Windows.
4. أضف مشروعًا: **مشروع جديد** أو **استيراد مستودع موجود** من لوحة المتابعة، ثم اختر مستودع git على جهازك.
5. شغّل المنسّق في المشروع. إذا قال إن Claude Code غير مسجَّل الدخول، استخدم **تسجيل الدخول إلى Claude Code**. وفي مجلد جديد، اضغط **الوثوق بهذا المجلد**.
6. إذا كنت تستخدم Codex، اضغط **تسجيل الدخول إلى Codex (حساب أسطى)** في الـ agents والاشتراكات.
7. أجب على بطاقة بداية المشروع (خطوات التجهيز والـ checks، وملف CLAUDE.md للمشروع، والـ lineup)، ثم قل للمنسّق ماذا يبني.

في المشروع الجديد، الـ merge ينتظر موافقتك. يمكن تفعيل «اعمل merge تلقائيًا» من إعدادات المشروع بعد أن يكون هناك check واحد على الأقل لازم ينجح قبل الـ merge. كل merge يتم على جهازك، والـ merge التلقائي يمكن التراجع عنه.

### تحذير SmartScreen في Windows

ملف التثبيت غير موقّع رقميًا، لذلك قد يظهر Windows في أول مرة رسالة «Windows protected your PC». اضغط **More info** ثم **Run anyway**. وإذا أردت التأكد أنه الملف المنشور، قارن الـ SHA-256 الخاص بالملف بما في صفحة الإصدار أولًا:

<div dir="ltr">

```powershell
Get-FileHash .\Usta-Setup-<version>.exe -Algorithm SHA256
```

</div>

### التحديثات

أسطى يحدّث نفسه من إصدارات هذا المستودع. يبحث عن إصدار جديد عند التشغيل وكل 6 ساعات، ويحمّله في الخلفية، ثم يعرض **أعد التشغيل للتحديث**. لا يُثبَّت شيء حتى تضغط عليه. يمكنك اختيار **لاحقًا** أو **تخطَّ هذا الإصدار**، أو إيقاف البحث عن التحديثات من الإعدادات ← التحديثات. مشاريعك وسجلك وإعداداتك تبقى كما هي. ويمكنك أيضًا تثبيت ملف تثبيت أحدث فوق القديم بنفسك، وتبقى بياناتك كذلك.

### الخصوصية: ما الذي يخرج من جهازك

- أوامرك وكودك وشغل الـ agents تذهب إلى المزوّدين الذين اخترتهم:
  - إلى Anthropic وOpenAI وGoogle من خلال أدوات الـ CLI الرسمية الخاصة بهم، مسجَّلة الدخول بحساباتك؛
  - وإلى أي مزوّد API تضيفه (الكود الذي يُرسل إلى مزوّد API يمر عبر هذا المزوّد)؛
  - أما الخوادم المحلية (Ollama وLM Studio) فتبقى على جهازك.
- Telegram: فقط إذا ربطته. الأسئلة والتنبيهات والملخص الصباحي والملفات التي ترسلها إلى الـ bot تمر عبر خوادم Telegram.
- فقط عندما تستخدمها: سجل خوادم MCP (عند تصفح الـ connectors)، وGitHub (عند البحث عن skills أو تثبيتها)، والـ connectors التي تضيفها، وقوائم موديلات وأرصدة مزوّدي API.
- **البحث عن التحديثات:** أسطى يسأل GitHub عن إصدار جديد عند التشغيل وكل 6 ساعات. هذا السؤال لا يرسل شيئًا عنك أو عن مشاريعك، وGitHub يرى عنوان IP الخاص بك فقط، كما يحدث عندما تفتح أي صفحة ويب. يمكنك إيقافه من الإعدادات ← التحديثات.
- لا telemetry: لا تحليلات ولا تقارير أعطال. وأدوات الـ CLI نفسها تتبع شروط الشركات التي تصنعها.
- المفاتيح التي تضيفها تُحفظ مشفّرة بحماية Windows الخاصة بمستخدمك، ولا تُحفظ كنص عادي أبدًا. الخوادم المحلية للتطبيق لا تستمع إلا على 127.0.0.1.

### إزالة التثبيت

إعدادات Windows ← Apps ← Usta ← Uninstall. ما يبقى على جهازك حتى تحذفه بنفسك:

- مجلد البيانات `%APPDATA%\Usta`: المشاريع والمهام والسجل والإعدادات وتسجيل دخول Codex الخاص بالتطبيق ومفاتيحك المشفّرة؛
- نسخه الاحتياطية في `%APPDATA%\Usta-backups`؛
- في كل مستودع مشروع:
  - مجلد التطبيق `.usta` (أو `.delegate` في المشاريع التي بدأت بإصدار أقدم)، وفيه ملاحظات المشروع وسجلات الـ runs؛
  - وأي branches لمهام لم يتم لها merge؛
- ملفات جلسات Claude Code نفسها، التي يحفظها Claude Code في ملف المستخدم الخاص بك.

### حدود معروفة

- Windows فقط.
- وصول المنفّذين إلى الشبكة محجوب جزئيًا فقط على Windows.
- runs مهام Codex تستطيع قراءة مجلد بيانات التطبيق (runs مهام Antigravity وClaude Code لا تستطيع).
- ملف التثبيت غير موقّع رقميًا.

### الترخيص

TODO(Mostafa)

### الدعم

TODO(Mostafa)

</div>
