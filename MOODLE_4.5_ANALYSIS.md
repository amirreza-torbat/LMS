# تحلیل جامع Moodle v4.5 - لیست کامل فیچرها، ماژول‌ها و کامپوننت‌ها

> نسخه: 4.5 (Build: 20241007) - Branch 405 - $version 2024100700.00
> تاریخ انتشار: 7 اکتبر 2024 - کلون شده از github.com/moodle/moodle tag v4.5.0
> متدولوژی: لوپ ۱۰۰٪ دقت - اسکن تمام دایرکتوری‌های پلاگین، plugininfo، lib، و مستندات UPGRADING + release notes

## ۱. معماری هسته
- **Core LMS**: PHP, MariaDB/PostgreSQL/MySQL, Moodle Bootstrap
- **Component System**: `core\component` autoloader, plugin types registry
- **Plugin Types**: 40+ نوع پلاگین رسمی (plugininfo)
- **Subsystems**: 60+ زیرسیستم هسته (admin, ai, analytics, badges, blog, cache, calendar, cohort, comment, communication, competency, completion, contentbank, course, customfield, dataformat, enrol, files, grade, group, h5p, media, message, mnet, question, reportbuilder, search, tag, user, etc.)
- **Libraries**: lib/classes با 100+ کلاس core (access, analytics, antivirus, chart, context, dml, event, external, file, form, hook, lock, message, navigation, output, privacy, task, etc.)

## ۲. انواع پلاگین رسمی (از lib/classes/plugininfo)
`aiplacement`, `aiprovider`, `antivirus`, `auth`, `availability`, `block`, `cachelock`, `cachestore`, `calendartype`, `communication`, `contenttype`, `coursereport`, `customfield`, `dataformat`, `editor`, `enrol`, `fileconverter`, `filter`, `format`, `general`, `gradeexport`, `gradeimport`, `gradereport`, `gradingform`, `h5plib`, `local`, `media`, `message`, `mlbackend`, `mnetservice`, `mod`, `paygw`, `plagiarism`, `portfolio`, `profilefield`, `qbank`, `qbehaviour`, `qformat`, `qtype`, `report`, `repository`, `search`, `smsgateway`, `theme`, `tool`, `webservice`

## ۳. لیست کامل پلاگین‌ها به تفکیک نوع

### Activity Modules (mod) - 24 ماژول - مسیر `mod`
- `assign`
- `bigbluebuttonbn`
- `book`
- `chat`
- `choice`
- `data`
- `feedback`
- `folder`
- `forum`
- `glossary`
- `h5pactivity`
- `imscp`
- `label`
- `lesson`
- `lti`
- `page`
- `quiz`
- `resource`
- `scorm`
- `subsection`
- `survey`
- `url`
- `wiki`
- `workshop`

### Blocks (blocks) - 43 بلوک - مسیر `blocks`
- `accessreview`
- `activity_modules`
- `activity_results`
- `admin_bookmarks`
- `badges`
- `blog_menu`
- `blog_recent`
- `blog_tags`
- `calendar_month`
- `calendar_upcoming`
- `comments`
- `completionstatus`
- `course_list`
- `course_summary`
- `feedback`
- `globalsearch`
- `glossary_random`
- `html`
- `login`
- `lp`
- `mentees`
- `mnet_hosts`
- `myoverview`
- `myprofile`
- `navigation`
- `news_items`
- `online_users`
- `private_files`
- `recent_activity`
- `recentlyaccessedcourses`
- `recentlyaccesseditems`
- `rss_client`
- `search_forums`
- `section_links`
- `selfcompletion`
- `settings`
- `site_main_menu`
- `social_activities`
- `starredcourses`
- `tag_flickr`
- `tag_youtube`
- `tags`
- `timeline`

### Authentication (auth) - 11 - مسیر `auth`
- `cas`
- `email`
- `ldap`
- `lti`
- `manual`
- `mnet`
- `nologin`
- `none`
- `oauth2`
- `shibboleth`
- `webservice`

### Enrolment (enrol) - 14 - مسیر `enrol`
- `category`
- `cohort`
- `database`
- `fee`
- `flatfile`
- `guest`
- `imsenterprise`
- `ldap`
- `lti`
- `manual`
- `meta`
- `mnet`
- `paypal`
- `self`

### Text Filters (filter) - 13 - مسیر `filter`
- `activitynames`
- `algebra`
- `codehighlighter`
- `data`
- `displayh5p`
- `emailprotect`
- `emoticon`
- `glossary`
- `mathjaxloader`
- `mediaplugin`
- `multilang`
- `tex`
- `urltolink`

### Course Formats (format) - 4 - مسیر `course/format`
- `singleactivity`
- `social`
- `topics`
- `weeks`

### Question Types (qtype) - 19 - مسیر `question/type`
- `calculated`
- `calculatedmulti`
- `calculatedsimple`
- `ddimageortext`
- `ddmarker`
- `ddwtos`
- `description`
- `essay`
- `gapselect`
- `match`
- `missingtype`
- `multianswer`
- `multichoice`
- `numerical`
- `ordering`
- `random`
- `randomsamatch`
- `shortanswer`
- `truefalse`

### Question Behaviours (qbehaviour) - 11 - مسیر `question/behaviour`
- `adaptive`
- `adaptivenopenalty`
- `deferredcbm`
- `deferredfeedback`
- `immediatecbm`
- `immediatefeedback`
- `informationitem`
- `interactive`
- `interactivecountback`
- `manualgraded`
- `missing`

### Question Import/Export Formats (qformat) - 7 - مسیر `question/format`
- `aiken`
- `blackboard_six`
- `gift`
- `missingword`
- `multianswer`
- `xhtml`
- `xml`

### Question Bank Plugins (qbank) - 19 - مسیر `question/bank`
- `bulkmove`
- `columnsortorder`
- `comment`
- `customfields`
- `deletequestion`
- `editquestion`
- `exportquestions`
- `exporttoxml`
- `history`
- `importquestions`
- `managecategories`
- `previewquestion`
- `statistics`
- `tagquestion`
- `usage`
- `viewcreator`
- `viewquestionname`
- `viewquestiontext`
- `viewquestiontype`

### Themes (theme) - 2 هسته - مسیر `theme`
- `boost`
- `classic`

### Site Reports (report) - 20 - مسیر `report`
- `backups`
- `competency`
- `completion`
- `configlog`
- `courseoverview`
- `eventlist`
- `infectedfiles`
- `insights`
- `log`
- `loglive`
- `outline`
- `participation`
- `performance`
- `progress`
- `questioninstances`
- `security`
- `stats`
- `status`
- `themeusage`
- `usersessions`

### Admin Tools (tool) - 41 - مسیر `admin/tool`
- `admin_presets`
- `analytics`
- `availabilityconditions`
- `behat`
- `brickfield`
- `capability`
- `cohortroles`
- `componentlibrary`
- `customlang`
- `dataprivacy`
- `dbtransfer`
- `filetypes`
- `generator`
- `httpsreplace`
- `installaddon`
- `langimport`
- `licensemanager`
- `log`
- `lp`
- `lpimportcsv`
- `lpmigrate`
- `messageinbound`
- `mfa`
- `mobile`
- `monitor`
- `moodlenet`
- `multilangupgrade`
- `oauth2`
- `phpunit`
- `policy`
- `profiling`
- `recyclebin`
- `replace`
- `spamcleaner`
- `task`
- `templatelibrary`
- `unsuproles`
- `uploadcourse`
- `uploaduser`
- `usertours`
- `xmldb`

### Grade Reports (gradereport) - 7 - مسیر `grade/report`
- `grader`
- `history`
- `outcomes`
- `overview`
- `singleview`
- `summary`
- `user`

### Grade Exports (gradeexport) - 4 - مسیر `grade/export`
- `ods`
- `txt`
- `xls`
- `xml`

### Grade Imports (gradeimport) - 3 - مسیر `grade/import`
- `csv`
- `direct`
- `xml`

### Grading Forms (gradingform) - 2 - مسیر `grade/grading/form`
- `guide`
- `rubric`

### Availability Conditions (availability) - 6 - مسیر `availability/condition`
- `completion`
- `date`
- `grade`
- `group`
- `grouping`
- `profile`

### Repositories (repository) - 21 - مسیر `repository`
- `areafiles`
- `contentbank`
- `coursefiles`
- `dropbox`
- `equella`
- `filesystem`
- `flickr`
- `flickr_public`
- `googledocs`
- `local`
- `merlot`
- `nextcloud`
- `onedrive`
- `recent`
- `s3`
- `upload`
- `url`
- `user`
- `webdav`
- `wikimedia`
- `youtube`

### Portfolio (portfolio) - 4 - مسیر `portfolio`
- `download`
- `flickr`
- `googledocs`
- `mahara`

### Message Outputs (message) - 3 - مسیر `message/output`
- `airnotifier`
- `email`
- `popup`

### Text Editors (editor) - 3 - مسیر `lib/editor`
- `atto`
- `textarea`
- `tiny`

### Atto Editor Plugins - 32 - مسیر `lib/editor/atto/plugins`
- `accessibilitychecker`
- `accessibilityhelper`
- `align`
- `backcolor`
- `bold`
- `charmap`
- `clear`
- `collapse`
- `emojipicker`
- `emoticon`
- `equation`
- `fontcolor`
- `h5p`
- `html`
- `image`
- `indent`
- `italic`
- `link`
- `managefiles`
- `media`
- `noautolink`
- `orderedlist`
- `recordrtc`
- `rtl`
- `strike`
- `subscript`
- `superscript`
- `table`
- `title`
- `underline`
- `undo`
- `unorderedlist`

### TinyMCE Editor Plugins - 11 - مسیر `lib/editor/tiny/plugins`
- `accessibilitychecker`
- `aiplacement`
- `autosave`
- `equation`
- `h5p`
- `html`
- `link`
- `media`
- `noautolink`
- `premium`
- `recordrtc`

### Media Players (media) - 5 - مسیر `media/player`
- `html5audio`
- `html5video`
- `videojs`
- `vimeo`
- `youtube`

### Cache Stores (cachestore) - 5 - مسیر `cache/stores`
- `apcu`
- `file`
- `redis`
- `session`
- `static`

### Cache Locks (cachelock) - 1 - مسیر `cache/locks`
- `file`

### Data Formats (dataformat) - 6 - مسیر `dataformat`
- `csv`
- `excel`
- `html`
- `json`
- `ods`
- `pdf`

### Payment Gateways (paygw) - 1 - مسیر `payment/gateway`
- `paypal`

### SMS Gateways (smsgateway) - 1 - مسیر `sms/gateway`
- `aws`

### Search Engines (search) - 2 - مسیر `search/engine`
- `simpledb`
- `solr`

### Custom Field Types (customfield) - 6 - مسیر `customfield/field`
- `checkbox`
- `date`
- `number`
- `select`
- `text`
- `textarea`

### Content Bank Types (contenttype) - 1 - مسیر `contentbank/contenttype`
- `h5p`

### Communication Providers (communication) - 2 - مسیر `communication/provider`
- `customlink`
- `matrix`

### AI Placements (aiplacement) - 2 - مسیر `ai/placement`
- `courseassist`
- `editor`

### AI Providers (aiprovider) - 2 - مسیر `ai/provider`
- `azureai`
- `openai`

### Antivirus (antivirus) - 1 - مسیر `lib/antivirus`
- `clamav`

### Calendar Types (calendartype) - 1 - مسیر `calendar/type`
- `gregorian`

### File Converters (fileconverter) - 2 - مسیر `files/converter`
- `googledrive`
- `unoconv`

### User Profile Fields (profilefield) - 6 - مسیر `user/profile/field`
- `checkbox`
- `datetime`
- `menu`
- `social`
- `text`
- `textarea`

### ML Backends (mlbackend) - 2 - مسیر `lib/mlbackend`
- `php`
- `python`

### MNet Services (mnetservice) - 1 - مسیر `mnet/service`
- `enrol`

### H5P Libraries (h5plib) - 1 - مسیر `h5p/h5plib`
- `v127`

### Webservices (webservice) - 2 - مسیر `webservice`
- `rest`
- `soap`

## ۴. توضیح تک‌تک Activity Modules (24)
- **assign**: تکلیف - ارسال فایل، متن آنلاین، داوری، بازخورد، گروهی، تلاش مجدد، UI جدید 4.5 با فیلتر و sticky footer
- **bigbluebuttonbn**: کلاس مجازی BigBlueButton - یکپارچه با BBB
- **book**: کتاب - محتوای چندصفحه‌ای با فصل‌بندی
- **chat**: چت - گفتگوی همزمان متنی
- **choice**: انتخاب - نظرسنجی تک‌سوال چندگزینه‌ای
- **data**: پایگاه داده - فعالیت ساخت پایگاه داده سفارشی با فیلدها
- **feedback**: بازخورد - نظرسنجی سفارشی (غیرنمره‌ای)
- **folder**: پوشه - نمایش مجموعه فایل‌ها
- **forum**: انجمن - بحث متنی با انواع (عمومی، Q&A، تک‌بحث)
- **glossary**: واژه‌نامه - اصطلاحات با تایید و لینک خودکار
- **h5pactivity**: فعالیت H5P - محتوای تعاملی H5P با نمره‌دهی
- **imscp**: بسته IMS - نمایش بسته IMS Content
- **label**: برچسب - متن/رسانه بین فعالیت‌ها
- **lesson**: درس - مسیر یادگیری شاخه‌ای با سوال
- **lti**: ابزار خارجی LTI 1.3 - اتصال به ابزارهای خارجی
- **page**: صفحه - یک صفحه محتوایی
- **quiz**: آزمون - بانک سوال، انواع سوال، بازخورد، Safe Exam Browser، نمره‌دهی مجدد انتخابی 4.5
- **resource**: فایل - نمایش یک فایل
- **scorm**: اسکورم - بسته SCORM 1.2 و 2004 با ردیابی
- **subsection**: زیربخش - **جدید 4.5** - بخش تو در تو برای سلسله‌مراتب دوره، قابل نمایش در course index
- **survey**: نظرسنجی - پرسشنامه‌های استاندارد COLLES, ATTLS
- **url**: پیوند - لینک به URL خارجی
- **wiki**: ویکی - صفحات مشارکتی
- **workshop**: کارگاه - ارزیابی همتایان با معیار

## ۵. زیرسیستم‌های هسته (Core Subsystems) - 60+
- admin: مدیریت سایت، تنظیمات، ابزارها
- ai: **جدید 4.5** - زیرسیستم هوش مصنوعی - placement (courseassist, editor) و provider (openai, azureai) - تولید متن/تصویر، خلاصه‌سازی
- analytics: یادگیری ماشین - مدل‌های پیش‌بینی، insights، bulk actions
- auth: احراز هویت - 11 پلاگین
- availability: دسترسی شرطی - 6 شرط
- backup: پشتیبان‌گیری و بازیابی دوره
- badges: نشان‌ها - Open Badges 3.0 در 4.5، صدور، backpack
- blocks: بلوک‌ها - 43 بلوک
- blog: وبلاگ سایت/کاربر/دوره
- cache: کش - stores (apcu, file, redis, session, static) و locks
- calendar: تقویم - رویدادهای سایت/دوره/کاربر/گروه، type gregorian
- cohort: گروه‌های سراسری - bulk delete جدید 4.5
- comment: نظرات
- communication: ارتباط - provider matrix, customlink - اتاق پیام کلاس
- competency: شایستگی - framework, plan, evidence, report source جدید 4.5
- completion: تکمیل فعالیت/دوره - معیارها
- contentbank: بانک محتوا - contenttype h5p
- course: مدیریت دوره - format (topics, weeks, social, singleactivity), report, customfield numeric جدید 4.5
- customfield: فیلد سفارشی - 6 نوع
- dataformat: خروجی داده - 6 فرمت
- enrol: ثبت‌نام - 14 روش
- favourites: علاقه‌مندی‌ها
- files: مدیریت فایل - converter (googledrive, unoconv), filepicker, alias
- filter: فیلتر متن - 13 فیلتر
- grade: نمره - report (7), export (4), import (3), grading form (rubric, guide), history, outcomes
- group: گروه و گروه‌بندی
- h5p: H5P - کتابخانه v127, ویرایشگر
- lib: کتابخانه‌های هسته - component, dml, form, event, task, output, privacy, etc.
- local: پلاگین‌های محلی (خالی در هسته)
- login: ورود
- media: پخش رسانه - 5 پلیر
- message: پیام‌رسانی - output (popup, email, airnotifier), notification improvements 4.5
- mnet: شبکه Moodle
- mod: ماژول‌های فعالیت
- moodlenet: یکپارچگی MoodleNet
- my: داشبورد کاربر
- notes: یادداشت‌ها
- payment: پرداخت - gateway paypal
- plagiarism: تشخیص سرقت
- portfolio: پورتفولیو - 4
- privacy: حریم خصوصی - dataprivacy tool
- question: بانک سوال - type (19), behaviour (11), format (7), bank (19)
- rating: امتیازدهی
- report: گزارش‌های سایت - 20
- reportbuilder: **سازنده گزارش سفارشی** - sourceهای جدید 4.5: competencies, user badges, comments, course categories, role, cohort filter, timezone/language
- repository: مخزن فایل - 21
- rss: RSS
- search: جستجو - engine simpledb, solr
- sms: **جدید 4.5** - زیرسیستم SMS - gateway aws
- tag: برچسب
- theme: پوسته - boost, classic - Font Awesome 6 در 4.5
- user: کاربر - profile field 6 نوع, bulk, tours
- webservice: وب‌سرویس - rest, soap, ws جدید: core_badges_get_badge, private files, remove submissions, progress bar API

## ۶. ویژگی‌های جدید و بهبودهای کلیدی Moodle 4.5

### ۶.۱ Major UX Improvements
- **Course Subsections (mod_subsection)**: سلسله‌مراتب دوره - زیربخش‌های قابل باز/بسته شدن، نمایش در course index، صفحه بخش واکنش‌گرا، breadcrumb، backup/restore، گزارش‌ها، mobile app پشتیبانی
- **Assignment Improvements Phase 1**: صفحه ارسال بازطراحی - تمام عرض، هدر/فوتر ثابت (sticky), فیلتر marker/active participants/initials/user search/workflow بهبود یافته، منوهای متنی، دسترسی آسان به bulk actions
- **Font Awesome 6**: ارتقای آیکن‌ها به FA6، حذف آیکن‌های غیر SVG، emoji-data برای emoticon

### ۶.۲ AI Subsystem (جدید)
- **AI Placement**: courseassist (کمک به ساخت دوره), editor (داخل ویرایشگر Tiny)
- **AI Provider**: openai, azureai - قابل افزودن توسط ادمین
- قابلیت‌ها: تولید متن/تصویر برای محتوا، خلاصه‌سازی محتوا، TinyMCE AI
- API: rate limiter, process_base, aiactions/responses

### ۶.۳ SMS Subsystem (جدید)
- نوع پلاگین جدید smsgateway - پیاده‌سازی aws
- برای MFA، نوتیفیکیشن

### ۶.۴ Quiz & Question
- بهبود UI مدیریت دسته‌بندی سوالات: drag & drop, سه نقطه action
- امکان نمره‌دهی مجدد (regrade) برای سوالات انتخابی (MDL-79546)
- سوال Ordering (جدید در نسخه‌های قبل اما بهبود یافته)
- Safe Exam Browser: امکان غیرفعال‌سازی قالب حتی اگر استفاده شده
- Drag-and-drop: پشتیبانی از محتوای فیلتر شده در پاسخ‌ها
- Help text برای Choices در ddwtos

### ۶.۵ Report Builder
- bulk delete cohorts (MDL-52046)
- Competencies custom report source (MDL-76889)
- Cohort condition/filter در Course Participants
- Custom report date filter by minute
- Filter by custom fields در Cohort report
- User reporting by timezone & language (MDL-81399)
- Author filter در Files report
- File report plugin/area filter
- Aggregation در system reports
- بهبود: task log صفحه عادی نه popup، فیلتر اعداد با float محلی

### ۶.۶ Assignment & Grade
- اعلان به دانشجو: Quiz about to open, Assignment due in 7 days/48 hours, overdue
- تنظیمات: default grade & scale, grant attempts automatically
- امکان تنظیم file types برای تکلیف
- Collapse comments در تکلیف
- Gradebook: جستجوی بهبود یافته, layout جدید

### ۶.۷ TinyMCE & Editor
- TinyMCE به عنوان ویرایشگر پیش‌فرض (از 4.2)
- **Screen recording**: ضبط صفحه و صدای سیستم + ضبط ویدئو داخل ویرایشگر (جدید 4.5)
- Atto همچنان موجود (32 پلاگین)
- Tiny plugins: 11 پلاگین شامل aiplacement, autosave, premium

### ۶.۸ Badges & Competency
- Open Badges 3.0 پیاده‌سازی
- امکان داشتن نشان‌های هم‌نام در یک دوره
- Workflow نشان‌ها روان‌تر
- Competency: منبع گزارش سفارشی

### ۶.۹ Notification Improvements Phase 2
- اعلان‌های تکلیف/کوییز بهبود یافته

### ۶.۱۰ Other Highlights
- Stealth activity links برای معلم غیر ویرایشگر
- ویرایش پیام خوش‌آمد دوره توسط معلم
- فیلد عددی برای customfield دوره
- فیدبک Questions منوی ثانویه
- گزینه مخفی کردن فرم ورود در صفحه لاگین
- تاریخ شروع/پایان در External database course creation
- Availability restriction info default change
- Hook برای توسعه homepage پیش‌فرض
- امنیت: logout دیگر sessionها هنگام reset پسورد، حذف خودکار EXIF، جایگزینی RC4 با کتابخانه استاندارد

## ۷. لیست کامل قابلیت‌های کلیدی (Feature Matrix) - 100+ فیچر

- Course Management: ایجاد/ویرایش/حذف دوره، دسته‌بندی، فرمت‌ها (topics/weeks/social/singleactivity), بخش‌بندی، زیربخش (4.5), تکمیل، دسترسی شرطی, Stealth, drag-drop, bulk edit
- User Management: احراز هویت 11 روش, پروفایل 6 فیلد, cohort, group/grouping, role/capability, bulk upload, user tours, MFA
- Enrolment: 14 روش (manual, self, cohort, guest, category, meta, etc.), paypal, fee, پرداخت
- Activities: 24 فعالیت (assign, quiz, forum, lesson, workshop, data, glossary, wiki, choice, feedback, survey, lti, scorm, h5pactivity, book, bigbluebuttonbn, etc.)
- Resources: 6 منبع (book, file/resource, folder, label, page, url, imscp)
- Blocks: 43 بلوک (myoverview, timeline, navigation, calendar_month/upcoming, completionstatus, etc.)
- Gradebook: نمره‌دهی, 7 گزارش, 4 خروجی, 3 ورودی, rubric/guide, history, outcomes, singleview, grader
- Question Bank: 19 نوع سوال, 11 رفتار, 7 فرمت ورودی/خروجی, 19 پلاگین بانک (managecategories, preview, tag, comment, etc.)
- Quiz: بانک سوال, رفتارها, Safe Exam Browser, نمره‌دهی مجدد انتخابی, دسته‌بندی drag-drop
- Assignment: ارسال فایل/متن/چندرسانه‌ای, داوری, بازخورد, گروهی, تلاش مجدد خودکار, UI جدید 4.5
- Forum: انواع انجمن, امتیازدهی, RSS, جستجو, whole forum grading
- H5P: فعالیت H5P, کتابخانه v127, content bank, ویرایشگر
- SCORM: SCORM 1.2/2004, گزارش نموداری, ردیابی تکمیل
- LTI: LTI 1.3 Advantage, ابزار خارجی
- BigBlueButton: کلاس مجازی یکپارچه
- Competency: چارچوب شایستگی, طرح یادگیری, evidence, گزارش
- Badges: نشان Open Badges 3.0, backpack, صدور خودکار
- Completion: ردیابی تکمیل فعالیت/دوره, معیارها
- Availability: دسترسی شرطی بر اساس تاریخ/نمره/گروه/پروفایل/تکمیل
- Calendar: تقویم سایت/دوره/کاربر/گروه, نوع gregorian, export
- Messaging: پیام داخلی, خروجی popup/email/airnotifier, اتاق پیام کلاس (communication matrix)
- Notifications: اعلان تکلیف/کوییز جدید 4.5
- Reports: 20 گزارش سایت (log, loglive, participation, completion, competency, insights, etc.)
- Report Builder: سازنده گزارش سفارشی با منابع جدید 4.5
- Analytics: مدل‌های پیش‌بینی, ML backend php/python, insights
- AI: تولید متن/تصویر, خلاصه‌سازی, TinyMCE AI
- Search: موتور simpledb/solr, globalsearch block
- Tags: برچسب‌گذاری, tag areas
- Blog: وبلاگ سایت/دوره/کاربر
- Notes: یادداشت
- Comments: نظرات
- Rating: امتیازدهی
- Portfolio: خروجی به mahara, googledocs, flickr, download
- Repository: 21 مخزن (dropbox, nextcloud, s3, googledocs, youtube, etc.)
- File Management: filepicker, drag-drop, alias, converter googledrive/unoconv, antivirus clamav
- Media: پلیر html5audio/video, videojs, youtube, vimeo
- Filters: 13 فیلتر (multilang, mathjax, tex, emoticon, glossary, etc.)
- Editors: Atto (32), Tiny (11), textarea
- Custom Fields: فیلد سفارشی دوره/سوال - 6 نوع + numeric جدید 4.5
- Content Bank: بانک محتوا H5P
- Communication: provider matrix/customlink
- SMS: gateway aws
- Payment: gateway paypal
- Security: XSS, CSRF, EXIF removal, RC4 replacement, session logout, public path checker
- Backup/Restore: پشتیبان‌گیری دوره, IMSCC, Moodle2
- Web Services: REST/SOAP, 200+ توابع خارجی, WS جدید 4.5
- Mobile App: پشتیبانی Ionic 8, offline, course subsection, private files
- Accessibility: accessibilitychecker در Atto/Tiny, screen reader, Font Awesome 6
- Internationalization: چندزبانه, multilang filter, customlang tool
- Themes: Boost/Classic, SCSS, templatelibrary, componentlibrary
- Admin Tools: 41 ابزار (dataprivacy, recyclebin, uploadcourse/user, capability, log, task, etc.)
- Privacy: GDPR, dataprivacy, messageinbound, policy
- Performance: cache (5 stores), profiling, performance report
- MNet: شبکه Moodle
- MoodleNet: یکپارچگی
- Hooks: after_config, after_http_headers, etc. جدید 4.5

## ۸. آمار کلی
- کل فایل‌ها: ~28,899
- Activity Modules: 24
- Blocks: 43
- Auth: 11, Enrol: 14, Filter: 13, Format: 4
- QType: 19, QBehaviour: 11, QFormat: 7, QBank: 19
- Report: 20, Tool: 41, Grade Report: 7
- Repository: 21, Portfolio: 4, Message: 3
- Editor: 3 (Atto 32 plugins, Tiny 11 plugins)
- Media: 5, Cache Store: 5, DataFormat: 6
- و ده‌ها نوع دیگر

## ۹. نتیجه‌گیری برای پروژه LMS مگفا
- Moodle 4.5 یک مرجع کامل برای تمام نیازهای RFP مگفا است: از SCORM/xAPI/H5P تا AI, SMS, Report Builder, Competency, Badges
- معماری Moodle ماژولار است اما هسته آن سنگین است؛ برای پروژه مگفا می‌توان از ایده Plugin Loader و Generic Container الهام گرفت اما هسته سبک‌تر ساخت
- فیچرهای جدید 4.5 مثل Subsection, AI Subsystem, Assignment UI, Quiz Regrade مستقیماً با نیازهای RFP (مسیر یادگیری هوشمند، گزارش پیشرفته، UX ساده) هم‌راستا هستند
- برای تطابق با RFP: باید Enterprise (AD/LDAP, HRIS, Skill-Gap, Recommender) و Academic (SIS, Rules Engine, ترم/واحد) را روی هسته Moodle یا هسته اختصاصی پیاده کرد
