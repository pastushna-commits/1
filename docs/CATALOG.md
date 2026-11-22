# Каталог плагінів, skills і конекторів

Оновлено: 2026-11-22. Це **індекс за запитом**: у кожну сесію він не вантажиться.
Відкривай його, коли треба знайти потрібний інструмент або активувати новий.

## Принцип «встановлено ≠ завантажено»
- **Конектори (MCP)**: схеми інструментів відкладені (ToolSearch). Постійна вартість мала. Установлюй свободно.
- **Плагіни**: короткі описи їхніх skills потрапляють у **кожну** сесію. Тому ставимо лише плагіни, що закривають реальну прогалину. Решта в розділі «Не встановлено, є в каталозі».
- **Плагіни з hooks або `reach: privileged`** виконують код у кожній сесії. Ставити тільки з окремого дозволу.
- Автоматичного сканування вмісту немає (`content_scan: null` у всіх результатів). «Перевірено» означає: джерело та рівень видавця з каталогу (`anthropic`, `partner`, `community`), склад компонентів, reach, наявність hooks. Код усередині я не аудитував.
- Установлення плагінів і конекторів потребує вашого підтвердження на картці. Самостійно встановити їх із сесії неможливо.

## Перевірені каталоги
1. Плагіни claude.ai (Anthropic Directory): `SearchPlugins`, 12 пошуків за всіма темами запиту.
2. Реєстр MCP-конекторів: `SearchMcpRegistry`, 14 пошуків.
3. Skills акаунта: `ListSkills`, `SearchSkills`. Пошук за темами нових не дав.
4. Локально синхронізовані плагіни (`~/.claude/plugins/synced`).
5. Підключені конектори (`ListConnectors`).

Не перевірялися: GitHub-маркетплейси за межами скоупу репозиторію (`pastushna-commits/1`), npm/PyPI-каталоги MCP. Сесія дозволяє лише каталоги вище.

## A. Уже працює (дублікати не ставилися)
| Назва | Джерело | Призначення | Авторизація | Активація |
|---|---|---|---|---|
| Gmail | конектор, connected | пошта: пошук, чернетки, відповіді | є | `ToolSearch "gmail"` |
| Google Calendar | конектор, connected | календар, події, вільні слоти | є | `ToolSearch "calendar"` |
| Google Drive | конектор, connected | пошук і читання файлів | є | `ToolSearch "drive"` |
| Google Sheets | конектор, connected | таблиці | є | `ToolSearch "sheets"` |
| GitHub | MCP github | код, PR, issues | є | `ToolSearch "github"` |
| docx, pdf (+OCR), xlsx, pptx | skills акаунта | Word, PDF, Excel, презентації | не потрібна | `Skill` за назвою |
| docs, google-workspace | skills акаунта | документи, файли Google | не потрібна | `Skill` |
| deep-research | skills акаунта | багатоджерельні звіти | не потрібна | `Skill` |
| built-in-browser, chrome-browser, computer-use | skills акаунта | браузер, робочий стіл | потрібна десктоп-програма | `Skill` |
| skill-creator, morning, import-memory | skills акаунта | свої skills, ранковий огляд, імпорт пам'яті | не потрібна | `Skill` |
| Productivity (4 skills) | плагін Anthropic, синхронізований | завдання, пам'ять між сесіями | не потрібна | `Skill productivity:*` |
| Data (10 skills) | плагін Anthropic, синхронізований | SQL, аналіз, візуалізації, дашборди | не потрібна | `Skill data:*` |
| dataviz, artifact-* | skills сесії | графіки, сторінки, діаграми | не потрібна | `Skill` |

Примітка: MCP-сервери плагінів Data та Productivity (Slack, Notion, Asana, BigQuery тощо) у цій сесії **не підключилися**: проксі блокує хости (403). Це обмеження мережі середовища. Лише авторизація не допоможе.

## B. Запропоновано до встановлення (картки показано; стан: очікує вашого підтвердження)

### Плагіни першої хвилі (закривають прогалини, мінімум skills)
| Назва | Видавець / reach | Призначення | Авторизація | Активація |
|---|---|---|---|---|
| YouTube Transcriber | community / contained | транскрипти YouTube без ключа | не потрібна | `Skill youtube-transcriber` |
| watch-video | community / contained | відео: кадри + транскрипт (ffmpeg, yt-dlp, Whisper) | ключ Groq/OpenAI лише для хмарного Whisper | `Skill watch-video` |
| Bio Research | **anthropic** / remote | PubMed, клінічні дані, біомедична література | автентифікація кожного MCP | `Skill bio-research:start` |
| Image Deep Research | community / contained | референси, ліцензовані зображення, мудборди | не потрібна | команда `find-reference-images` |
| frontend-design | **anthropic** / contained | якісний фронтенд, сайти | не потрібна | `Skill frontend-design` |
| paper-search | community / contained | пошук статей через OpenAlex | не потрібна | `Skill paper-search` |
| Playwright | partner (Microsoft) / remote | автоматизація браузера | не потрібна | `ToolSearch "playwright"` |

### Конектори (відкладені схеми, дешево тримати)
| Назва | Призначення | Авторизація |
|---|---|---|
| PubMed (authless) | біомедична література | не потрібна |
| Arca FDA, Trials & PubMed (authless) | FDA-настанови, листи, етикетки, пристрої; нормативка | не потрібна |
| Clinical Trials (authless) | ClinicalTrials.gov | не потрібна |
| ICD-10 Codes (authless) | коди МКХ-10 | не потрібна |
| Parallel Search (authless) | вебпошук і витяг сторінок | не потрібна |
| Google Docs | читання й редагування Docs | **очікує авторизації** (Google) |
| Google Slides | презентації Google | **очікує авторизації** (Google) |
| Canva | дизайн, публікації | **очікує авторизації** |
| Zapier | автоматизація повторюваної роботи | **очікує авторизації** |
| Microsoft 365 | Outlook, OneDrive, SharePoint, Teams | **очікує авторизації** |

## C. Потрібне ваше рішення (платне, зовнішні акаунти або передача даних третім сторонам)
| Назва | Чому не встановлено |
|---|---|
| Facebook / соцмережі: Windsor.ai for Social Media, Metricool, Typefully, Posty (плагін), Ayrshare, So-me Studio | публікація й аналітика через сторонній сервіс: потрібні ваші облікові записи; ймовірно платно. Яку мережу й який сервіс обрати? Ayrshare має PreToolUse-hook (відхилено за замовчуванням) |
| Транскрибування: transcribe-so, Scriptivox, Speko, Local Whisper | зовнішній сервіс або локальний сервер на вашому комп'ютері (потрібне підключення папки) |
| Відео: Riverside, Tella, Cardboard, Eddie AI, Brightcove | редагування відео в стороннього сервісу, акаунт або підписка |
| Дизайн: Figma, Adobe, Codesign, Wonder, Subframe, Getty Images | акаунт або ліцензія; Getty платний |
| Сайти й хостинг: Vercel, Netlify, Cloudflare, Supabase, Wix, WordPress, Hostinger | потрібен ваш акаунт; деякі платні. Які використовуєте? |
| Контакти: окремого Google Contacts-конектора в каталозі не знайдено. Fastmail, Multi Mail, Slashy, CRM (HubSpot, Zoho) | залежить від вашого поштового сервісу |
| Вебпошук/скрейпінг: Exa, TinyFish, AWS Web Search | потрібен ключ або акаунт |
| OCR: EasyPDF, myocr.app, PaperOffice | вбудований skill `pdf` уже робить OCR; сторонній сервіс отримував би ваші документи |

## D. Не встановлено свідомо
| Компонент | Причина |
|---|---|
| ai-coding-ok, anchor-memory, research-superpowers, workflow-toolkit, Wiser, n8n Knowledge Base, mana, agent-context-kit, Auto Research, Make Documentation, Compliance ES, React skills | `reach: privileged`: hooks або широкі права виконуються у кожній сесії; суперечить умові економії ліміту |
| Social Media Skills (106 skills) | величезна кількість описів у кожній сесії + privileged |
| Pdf To Excel, docpdf | дублюють вбудовані skills `pdf`/`xlsx`/`docx` |
| Slashy | дублює підключені Gmail і Calendar |
| Cairn Memory, Flow, Configure Memory, Vertiso Memory, KnowMine | дублюють `productivity:memory-management` і `task-management`; зовнішні сховища пам'яті передавали б ваші дані третім сторонам |
| Small Business, equity-research, Legal-плагіни, Marketing for Life Sciences, Hyper Marketing, Sent, RingCentral, Opsera | поза переліком потреб; можна додати на запит |
| Платні/корпоративні конектори (Semrush, Apollo, HubSpot тощо) | не потрібні для заявлених завдань; платні |

## E. Прогалини, які не закрито
- Інструмент для Facebook-публікацій: чекаємо вибору сервісу (розділ C).
- Google Contacts: готового конектора не знайдено.
- Аудіо: локальний Whisper потребує вашого комп'ютера.
- MCP плагінів Data/Productivity: заблоковані мережею середовища (див. примітку у розділі A).

## Як активувати на потребу
1. Конектор: `ToolSearch` з ключовим словом, далі виклик інструмента.
2. Skill: `Skill <назва>` лише коли завдання цього вимагає.
3. Новий плагін: попросіть «додати X з каталогу». Я знайду його через `SearchPlugins` і покажу картку.
4. Вимкнути зайве: у налаштуваннях плагінів claude.ai (перемикач плагіна).
