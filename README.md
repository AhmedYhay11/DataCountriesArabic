### وصف الملف

يحتوي هذا الملف بصيغة JSON على بيانات مجموعة من الدول، مع تفاصيل تتضمن:
- **معرّف الدولة** (`_id`): رمز الدولة المكوّن من حرفين (على سبيل المثال: `"AF"` لأفغانستان).
- **الاسم باللغة العربية** (`name_ar`): اسم الدولة مكتوب باللغة العربية.
- **الاسم باللغة الإنجليزية** (`name_en`): اسم الدولة مكتوب باللغة الإنجليزية.
- **رابط العلم** (`flag`): رابط إلى صورة العلم الخاص بالدولة بصيغة PNG، بحجم عرض 20 بكسل.
                                                                                                                                                                                                        
#### مثال:

```json
{
    "_id": "AF",
    "name_ar": "أفغانستان",
    "name_en": "Afghanistan",
    "flag": "https://flagcdn.com/w20/af.png"
}
```
---


### قراءة ملف JSON في JavaScript، PHP، و Python

#### JavaScript
في JavaScript، يمكن قراءة ملفات JSON محليًا باستخدام `fetch` إذا كنت تعمل مع بيئة متصفح، أو باستخدام Node.js مع `fs` إذا كنت تعمل على جانب الخادم.

##### باستخدام Node.js:
```js
const fs = require('fs');

// قراءة ملف JSON
fs.readFile('countries.json', 'utf-8', (err, data) => {
    if (err) throw err;
    const countries = JSON.parse(data);

    // عرض البيانات
    countries.forEach(country => {
        console.log(`Country: ${country.name_en}, Flag: ${country.flag}`);
    });
});
```

#### PHP
في PHP، يمكنك قراءة الملف باستخدام `file_get_contents` ثم تحويل محتواه إلى مصفوفة باستخدام `json_decode`.

```php
<?php
// قراءة ملف JSON
$jsonData = file_get_contents('countries.json');

// تحليل محتوى JSON إلى مصفوفة
$countries = json_decode($jsonData, true);

// عرض البيانات
foreach ($countries as $country) {
    echo "Country: " . $country['name_en'] . ", Flag: " . $country['flag'] . "\n";
}
?>
```

#### Python
في Python، يمكنك استخدام دالة `open` لقراءة الملف، ثم استخدام `json.loads` لتحليل محتوى JSON.

```python
import json

# قراءة ملف JSON
with open('countries.json', 'r', encoding='utf-8') as file:
    countries = json.load(file)

# عرض البيانات
for country in countries:
    print(f"Country: {country['name_en']}, Flag: {country['flag']}")
```

---

### ملاحظات:
1. تأكد من أن ملف `countries.json` موجود في نفس المسار أو قم بتحديد المسار الكامل إلى الملف.
2. عند العمل مع Node.js، تحتاج إلى تثبيت Node.js أولًا وتشغيله في بيئة الخادم.
3. في PHP و Python، سيتم فتح الملف باستخدام الترميز الصحيح لضمان معالجة البيانات باللغة العربية بشكل صحيح.
