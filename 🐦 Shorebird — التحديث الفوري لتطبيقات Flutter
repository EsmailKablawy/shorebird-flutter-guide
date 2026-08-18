<div align="center">

# 🐦 Shorebird — التحديث الفوري لتطبيقات Flutter

**ادفع تحديثات الكود لمستخدمينك في دقائق، بدون انتظار مراجعة المتجر.**

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Shorebird](https://img.shields.io/badge/Shorebird-Code_Push-4A90E2?style=for-the-badge)
![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

</div>

---

## 📖 نظرة عامة

**Shorebird** هي خدمة **Code Push** (تحديثات عبر الهواء / OTA) لتطبيقات Flutter، تتيح لك دفع تحديثات لكود Dart مباشرةً إلى أجهزة المستخدمين — دون المرور بعملية مراجعة المتجر.

أسّسها **Eric Seidel**، أحد مؤسّسي Flutter نفسه، وهي مبنية على محرّك Flutter معدّل يفحص التحديثات ويطبّقها تلقائياً.

---

## 🤔 لماذا Code Push مهم؟

في سير العمل التقليدي، أي تعديل بسيط — إصلاح خطأ، تغيير نص، تحديث بسيط — يتطلّب رحلة كاملة:

> بناء النسخة ← رفعها للمتجر ← **انتظار المراجعة (أيام أحياناً)** ← وصولها للمستخدم

هذا يعني أن إصلاح خطأ حرج في الإنتاج قد يستغرق أياماً حتى يصل لمستخدميك. ومع ذلك، لا تستطيع إجبار المستخدمين على التحديث.

**مع Code Push، تختصر كل هذا:**

| | بدون Code Push | مع Shorebird |
|---|:---:|:---:|
| زمن وصول التحديث | أيام (مراجعة المتجر) | دقائق |
| يحتاج رفع للمتجر؟ | نعم في كل مرة | لا |
| المستخدم يحدّث يدوياً؟ | نعم | لا (تلقائي) |
| إصلاح الأخطاء الحرجة | بطيء | فوري |

---

## ⭐ لماذا Shorebird تحديداً؟

- **لا يتطلّب تعديلات في كودك** — الدمج يستغرق دقائق، وهو بديل مباشر لأمر `flutter build`.
- **متعدّد المنصّات** — يدعم Android و iOS و macOS و Windows و Linux.
- **متوافق مع سياسات المتاجر** — Apple و Google، طالما أن التحديثات لا تغيّر جوهر التطبيق.
- **تلقائي بالكامل** — المحرّك يفحص وينزّل ويطبّق التحديثات في الخلفية دون أي كود إضافي.
- **من صنّاع Flutter** — بُنيت على يد أشخاص يعرفون Flutter من الداخل.

---

## 🧩 مفاهيم أساسية

قبل أن نبدأ، تعرّف على مصطلحين ستراهما كثيراً:

- **Release (إصدار):** نسخة أساسية كاملة تبنيها وترفعها للمتجر. تحمل رقم إصدار فريد.
- **Patch (رقعة):** تحديث تدفعه *فوق* إصدار موجود، دون رفع نسخة جديدة للمتجر. هذا هو "السحر".

> ⚠️ **قاعدة ذهبية:** الـ Patch يحدّث **كود Dart فقط**. أي تغيير في الكود الأصلي (native) أو الأصول (صور، خطوط) يتطلّب Release جديد.

---

## ⚙️ المتطلّبات

- Flutter (نسخة حديثة ومستقرّة)
- `git` مثبّت على جهازك
- حساب مجاني على [Shorebird Console](https://console.shorebird.dev)

---

## 📥 التثبيت

### 1. أنشئ حساباً مجانياً

توجّه إلى [console.shorebird.dev](https://console.shorebird.dev) وسجّل حساباً — يستغرق ثوانٍ.

### 2. ثبّت الـ Shorebird CLI

**على macOS / Linux:**

```bash
curl --proto '=https' --tlsv1.2 https://raw.githubusercontent.com/shorebirdtech/install/main/install.sh -sSf | bash
```

**على Windows (PowerShell):**

```powershell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
iwr -UseBasicParsing 'https://raw.githubusercontent.com/shorebirdtech/install/main/install.ps1' | iex
```

> 💡 يُثبّت هذا الأمر Shorebird مع نسخة Flutter مخصّصة تدعم Code Push، منفصلة عن نسخة Flutter العادية لديك.

### 3. تحقّق من التثبيت

أعد تشغيل الطرفية (Terminal)، ثم شغّل:

```bash
shorebird doctor
```

يجب أن ترى في النهاية: `No issues detected!`

### 4. سجّل الدخول

```bash
shorebird login
```

سيفتح المتصفّح للمصادقة — سجّل بنفس الحساب الذي أنشأته، ثم ارجع للطرفية.

---

## 🔗 الربط مع مشروع Flutter

من داخل مجلّد مشروعك، شغّل:

```bash
shorebird init
```

سيقوم هذا الأمر بـ:

- تحليل مشروعك واكتشاف أي إعدادات خاصّة (مثل الـ flavors)
- إنشاء ملف `shorebird.yaml` في جذر المشروع (يحتوي على `app_id`)
- إضافة `shorebird.yaml` كـ asset في `pubspec.yaml`

> ℹ️ الـ `app_id` **ليس سرّياً**، ويجب رفعه على git.

---

## 🚀 الاستخدام

### الخطوة الأولى: إنشاء Release

هذه النسخة الأساسية التي ترفعها للمتجر. تُبنى بأمر Shorebird (وليس `flutter build`):

```bash
# لـ Android
shorebird release android

# لـ iOS
shorebird release ios
```

بعد اكتمال البناء، ترفع الملف الناتج (`.aab` لأندرويد، `.ipa` لـ iOS) على المتجر يدوياً — عبر Google Play Console، أو App Store Connect / [Transporter](https://apps.apple.com/us/app/transporter/id1450874784).

### الخطوة الثانية: دفع Patch

بعد أن يصبح الإصدار عند المستخدمين، أي تعديل في كود Dart يمكن دفعه فوراً:

```bash
# لـ Android
shorebird patch android

# لـ iOS
shorebird patch --platforms=ios --release-version=<رقم_الإصدار>
```

سيبني Shorebird الـ patch، ويقارنه بالإصدار الأصلي، ويطلب تأكيدك، ثم ينشره. ✅

### كيف يصل التحديث للمستخدم؟

التحديث يُنزّل في الخلفية، ويظهر عند التشغيل **الثاني**:

```
يفتح التطبيق (يُنزَّل الـ patch)  ←  يُغلق التطبيق  ←  يفتح مجدّداً (يظهر التحديث) ✅
```

---

## 📝 ملاحظات مهمة

- **طابِق رقم الإصدار (Build Number):** يجب أن يتطابق رقم الـ build الذي يبنيه Shorebird مع الرقم الذي يُثبَّت على جهاز المستخدم. عدم التطابق يعني أن الـ patch لن يصل.

- **حدّد نسخة Flutter صراحةً:** استخدم `--flutter-version` مع أمر `release` لضمان الاستقرار وتطابق الـ patches مع الإصدار:
  ```bash
  shorebird release ios --flutter-version=3.x.x
  ```
  > الـ Patch يستخدم تلقائياً نفس نسخة Flutter الخاصّة بالإصدار المستهدف — لا حاجة لتحديدها فيه.

- **مرّر متغيّرات البيئة إن وُجدت:** إذا كان مشروعك يعتمد على ملفات بيئة، مرّرها لكل من `release` و `patch` بنفس الطريقة:
  ```bash
  shorebird release ios -- --dart-define-from-file=env/config.json
  shorebird patch --platforms=ios --release-version=<الرقم> -- --dart-define-from-file=env/config.json
  ```

- **Dart فقط في الـ Patch:** التعديلات على الكود الأصلي (native)، الأصول (assets)، أيقونة التطبيق، أو الأذونات — كلها تتطلّب Release جديداً.

- **اختبر قبل النشر:** استخدم `shorebird preview` لتجربة الإصدار على جهاز حقيقي قبل الرفع.

- **حدّث الـ CLI دورياً:**
  ```bash
  shorebird upgrade
  ```

---

## 🔄 دورة العمل باختصار

```
مرّة واحدة لكل إصدار:
  تعديل رقم الإصدار → shorebird release → رفع للمتجر → تثبيت

بعدها لكل تحديث:
  تعديل كود Dart → shorebird patch → يصل للمستخدمين تلقائياً 🎉
```

---

## 📚 مصادر مفيدة

- [التوثيق الرسمي](https://docs.shorebird.dev)
- [Shorebird Console](https://console.shorebird.dev)
- [GitHub](https://github.com/shorebirdtech/shorebird)

---

<div align="center">

**صُنع بـ ❤️ لمجتمع Flutter العربي**

إذا أفادك هذا الدليل، لا تنسَ ⭐ للمستودع!

</div>
