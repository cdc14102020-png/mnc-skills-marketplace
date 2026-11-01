# سوق المهارات

مستودع سوق (marketplace) لمهارات وكلاء Claude Code. يضيفه كل عضو في الفريق مرة واحدة، وتصله التحديثات بعد ذلك دون إرسال أي ملف.

## الحزم المتاحة

| الحزمة | الوصف | أمر التثبيت |
|---|---|---|
| mnc-sibawayh-arabic-rules | مهارة سيبويه: المرجع اللغوي المعتمد من خبير اللغة العربية لضبط الإملاء والتحرير والأسلوب | `/plugin install mnc-sibawayh-arabic-rules@mnc-agent-skills` |

## التثبيت (مرة واحدة لكل عضو)

يكتب العضو هذين الأمرين في Claude Code:

```
/plugin marketplace add cdc14102020-png/mnc-skills-marketplace
/plugin install mnc-sibawayh-arabic-rules@mnc-agent-skills
```

يجب أن يبقى المستودع عامًا (Public) ليعمل الأمر الأول بهذه الصيغة المختصرة.

## التحديث

1. تُعدَّل ملفات المهارة داخل `plugins/mnc-sibawayh-arabic-rules/skills/mnc-sibawayh-arabic-rules/`.
2. يُرفع رقم الإصدار في `plugins/mnc-sibawayh-arabic-rules/.claude-plugin/plugin.json`، ليلتقط الأعضاء التحديث.
3. يُرفع التعديل إلى المستودع (Commit ثم Push).
4. يكتب العضو الأمر التالي للحصول على التحديث فورًا:

```
/plugin marketplace update
```

## بنية المستودع

```
mnc-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json            # فهرس السوق
├── plugins/
│   └── mnc-sibawayh-arabic-rules/
│       ├── .claude-plugin/
│       │   └── plugin.json         # بطاقة الحزمة: الاسم والإصدار والوصف
│       └── skills/
│           └── mnc-sibawayh-arabic-rules/
│               ├── SKILL.md
│               └── references/
└── README.md
```

## إضافة مهارات جديدة

تُضاف كل مهارة جديدة حزمةً مستقلة تحت `plugins/<اسم-الحزمة>/`، وتُسجَّل في مصفوفة `plugins` داخل `.claude-plugin/marketplace.json`. يكفي مستودع واحد لعدة حزم.

## ملاحظة

مستخدمو Cowork وClaude على الويب يحصلون على مهارات المركز من مكتبة مهارات المنظمة، ويرفعها مدير النظام من لوحة الإدارة. هذا المستودع مخصص لمستخدمي Claude Code.
