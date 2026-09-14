# mnc-skills-marketplace

مستودع "سوق مهارات" (marketplace) للمركز الوطني للمناهج — نقطة توزيع مركزية على GitHub للمهارات المخصصة لوكلاء Claude Code، بحيث يضيف كل عضو في الفريق المستودع مرة واحدة، ثم تصله التحديثات لاحقًا تلقائيًا دون إرسال ملفات يدويًا.

يحتوي حاليًا على حزمة واحدة: **mnc-arabic-writing-standards** (معايير الصياغة اللغوية والإملائية والتحرير العربي السليم).

## خطوة أولى (لك فقط، قبل مشاركة الرابط)

بعد إنشاء مستودع فعلي على GitHub تحت حساب/منظمة المركز، ارفعي محتوى هذا المجلد كما هو:

```bash
git init
git add .
git commit -m "إضافة سوق مهارات المركز: معايير الصياغة والتحرير العربي"
git branch -M main
git remote add origin https://github.com/cdc14102020-png/mnc-skills-marketplace.git
git push -u origin main
```

الرابط والاسم أعلاه مضبوطان مسبقًا على حساب `cdc14102020-png` ومستودع `mnc-skills-marketplace`. **ملاحظة مهمة**: لكي يعمل أمر الإضافة المختصر أدناه (`owner/repo`)، يجب أن يكون المستودع عامًا (Public) على GitHub — إن غيّرتِه لاحقًا إلى خاص، أخبريني لنستخدم أسلوب رابط بديل.

## خطوة ثانية (يرسلها كل عضو بالفريق — مرة واحدة فقط، بحسابه الخاص)

كل عضو في الفريق يفتح Claude Code (سواء من الطرفية أو أي واجهة تُشغّله) ويكتب هذين الأمرين مرة واحدة فقط:

```
/plugin marketplace add cdc14102020-png/mnc-skills-marketplace
/plugin install mnc-arabic-writing-standards@mnc-agent-skills
```

بعد هذه الخطوة، أصبحت المهارة مثبتة عنده ومتاحة تلقائيًا لوكيله كلما احتاجها — بشكل مستقل تمامًا عن حسابك أو حسابات بقية الفريق.

## عندما تُحدَّثين المهارة لاحقًا

1. عدّلي الملفات داخل `plugins/mnc-arabic-writing-standards/skills/mnc-arabic-writing-standards/`.
2. ارفعي التعديل بأمر عادي: `git add . && git commit -m "وصف التعديل" && git push`.
3. عند كل فرد بالفريق، Claude Code يتحقق من التحديثات تلقائيًا؛ ومن أراد تحديثًا فوريًا بدل انتظار الفحص التلقائي، يكتب:

```
/plugin marketplace update
```

لا حاجة لإعادة إرسال أي ملف أو تكرار خطوة التثبيت — التحديث يصل من نفس الرابط الذي أضافوه أول مرة.

## بنية المستودع

```
mnc-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json                  # فهرس السوق: يشير إلى الحزمة أدناه
├── plugins/
│   └── mnc-arabic-writing-standards/
│       ├── .claude-plugin/
│       │   └── plugin.json               # بطاقة تعريف الحزمة (الاسم، الإصدار، الوصف)
│       └── skills/
│           └── mnc-arabic-writing-standards/
│               ├── SKILL.md
│               └── references/
├── README.md                              # هذا الملف
```

## إضافة مهارات مستقبلية لنفس السوق

كل مهارة جديدة تُضاف كحزمة مستقلة تحت `plugins/<اسم-الحزمة>/`، مع تسجيلها في `.claude-plugin/marketplace.json` ضمن مصفوفة `plugins`. لا حاجة لإنشاء مستودع GitHub جديد لكل مهارة — مستودع واحد يكفي لعدة حزم.
