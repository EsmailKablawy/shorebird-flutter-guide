<div align="center">

# 🐦 Shorebird — تحديث تطبيق الـ Flutter من غير ما تستنى المتجر

**تظبط باج أو تعدّل حاجة، وتوصّلها لليوزرز في دقايق — من غير ما تستنى المراجعة.**

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Shorebird](https://img.shields.io/badge/Shorebird-Code_Push-4A90E2?style=for-the-badge)
![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

</div>

---

## 🐦 إيه هي Shorebird أصلًا؟

باختصار كده، Shorebird خدمة بتخليك تبعت تحديثات لكود الـ Dart بتاعك **على طول لأجهزة اليوزرز**، من غير ما تعدّي على مراجعة المتجر ولا ترفع نسخة جديدة.

اللي عملها واحد اسمه **Eric Seidel**، وده مش أي حد — ده من الناس اللي أسّسوا Flutter نفسها. فالكلام ده جاي من ناس فاهمة Flutter من جواها.

بتشتغل إزاي؟ التطبيق بيبقى فيه نسخة معدّلة من محرك Flutter، وأول ما بيفتح بيبص هل فيه تحديث للكود ولا لأ. لو لقى تحديث، بينزّله في الخلفية، واليوزر بيشوفه أول ما يفتح التطبيق تاني.

---

## 🤔 وليه الموضوع ده مهم من الأساس؟

خلينا نكون واقعيين. في الطريقة العادية، لو عايز تظبط أي حاجة صغيرة — باج، كلمة غلط، تعديل بسيط — لازم تعدّي على الرحلة دي كلها:

> تبني النسخة ← ترفعها للمتجر ← **تستنى المراجعة (ممكن أيام)** ← توصل لليوزر

يعني لو عندك باج بايظ في الـ production، ممكن تفضل مستني كذا يوم عشان الحل يوصل للناس. وبرضه مقدرش تجبر اليوزر إنه يعمل update.

Shorebird بتختصر ده كله:

| | من غير Code Push | مع Shorebird |
|---|:---:|:---:|
| التحديث بيوصل امتى | أيام (مراجعة المتجر) | دقايق |
| محتاج ترفع للمتجر؟ | آه، كل مرة | لأ |
| اليوزر بيعمل update بإيده؟ | آه | لأ، بيتم لوحده |
| حل الباجات المستعجلة | بطيء | فوري |

---

## ⭐ وليه Shorebird بالذات؟

- **مش هتغيّر حاجة في كودك** — الدمج بياخد دقايق، وهي بتبقى بديل مكان `flutter build` عادي كده.
- **بتشتغل على كل حاجة** — Android و iOS و macOS و Windows و Linux.
- **متوافقة مع سياسات المتاجر** — Apple و Google، طول ما التحديث مش بيغيّر جوهر التطبيق.
- **بتشتغل لوحدها** — المحرك بيفحص وينزّل ويطبّق التحديث في الخلفية، وانت مش محتاج تكتب ولا سطر عشان ده يحصل.

---

## 🧩 حاجتين لازم تفهمهم الأول

قبل ما نبدأ، في مصطلحين هتشوفهم كتير:

- **Release (الإصدار):** دي النسخة الكاملة اللي بتبنيها وترفعها للمتجر. بتاخد رقم مميز.
- **Patch (الرقعة):** ده التحديث اللي بتبعته *فوق* إصدار موجود، من غير ما ترفع نسخة جديدة. ودي بقى الحتة الحلوة في الموضوع كله.

> ⚠️ **قاعدة مهمة تحفظها:** الـ Patch بيحدّث **كود Dart بس**. أي تعديل في الكود الـ native أو الملفات (صور، خطوط) لازمله Release جديد.

---

## ⚙️ محتاج إيه قبل ما تبدأ؟

- Flutter (نسخة حديثة ومستقرة)
- `git` متظبط على جهازك
- حساب مجاني على [Shorebird Console](https://console.shorebird.dev)

---

## 📥 التثبيت

### 1. اعمل حساب مجاني

ادخل على [console.shorebird.dev](https://console.shorebird.dev) واعمل حساب — الموضوع ثواني.

### 2. نزّل الـ Shorebird CLI

**لو على macOS / Linux:**

```bash
curl --proto '=https' --tlsv1.2 https://raw.githubusercontent.com/shorebirdtech/install/main/install.sh -sSf | bash
```

**لو على Windows (PowerShell):**

```powershell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
iwr -UseBasicParsing 'https://raw.githubusercontent.com/shorebirdtech/install/main/install.ps1' | iex
```

> 💡 الأمر ده بينزّل Shorebird ومعاها نسخة Flutter مخصوصة بتدعم Code Push، منفصلة تمامًا عن نسخة Flutter العادية اللي عندك.

### 3. اتأكد إن كل حاجة تمام

اقفل الـ Terminal وافتحه تاني، وبعدين شغّل:

```bash
shorebird doctor
```

المفروض تشوف في الآخر: `No issues detected!`

### 4. سجّل دخول

```bash
shorebird login
```

هيفتحلك المتصفح عشان تسجّل — ادخل بنفس الحساب اللي عملته، وبعدين ارجع للـ Terminal.

---

## 🔗 اربطها بمشروع الـ Flutter بتاعك

من جوه فولدر مشروعك، شغّل:

```bash
shorebird init
```

الأمر ده هيعمل الآتي:

- يبص على مشروعك ويشوف لو فيه إعدادات خاصة (زي الـ flavors)
- يعمل ملف `shorebird.yaml` في جذر المشروع (جواه الـ `app_id`)
- يضيف `shorebird.yaml` كـ asset في `pubspec.yaml`

> ℹ️ الـ `app_id` **مش سري**، وعادي جدًا ترفعه على git.

---

## 🚀 نستخدمها إزاي؟

### أول خطوة: تعمل Release

دي النسخة الأساسية اللي بترفعها للمتجر. بتتبني بأمر Shorebird (مش `flutter build`):

```bash
# لـ Android
shorebird release android

# لـ iOS
shorebird release ios
```

بعد ما يخلّص، بترفع الملف الناتج (`.aab` لأندرويد، `.ipa` لـ iOS) على المتجر بإيدك — من Google Play Console، أو App Store Connect / [Transporter](https://apps.apple.com/us/app/transporter/id1450874784).

### تاني خطوة: تبعت Patch

بعد ما الإصدار يبقى عند اليوزرز، أي تعديل في كود Dart تقدر تبعته على طول:

```bash
# لـ Android
shorebird patch android

# لـ iOS
shorebird patch --platforms=ios --release-version=<رقم_الإصدار>
```

Shorebird هيبني الـ patch، ويقارنه بالإصدار الأصلي، ويطلب منك تأكيد، وبعدين ينشره. ✅

### التحديث بيوصل لليوزر إزاي؟

التحديث بينزّل في الخلفية، وبيبان في **تاني مرة** يفتح فيها التطبيق:

```
يفتح التطبيق (بينزّل الـ patch)  ←  يقفل التطبيق  ←  يفتحه تاني (التحديث بان) ✅
```

---

## 📝 ملاحظات مهمة خليك واخد بالك منها

- **خلي رقم الـ Build متطابق:** لازم رقم الـ build اللي Shorebird بتبنيه يبقى مطابق للرقم اللي متثبّت على جهاز اليوزر. لو مش متطابقين، الـ patch مش هيوصل. دي نقطة الناس بتقع فيها كتير.

- **حدّد نسخة Flutter بنفسك:** استخدم `--flutter-version` مع أمر الـ `release` عشان تضمن الاستقرار وإن الـ patches تتطابق مع الإصدار:
  ```bash
  shorebird release ios --flutter-version=3.x.x
  ```
  > الـ Patch بياخد أوتوماتيك نفس نسخة Flutter بتاعة الإصدار اللي بيستهدفه، فمش محتاج تحددها فيه تاني.

- **لو بتستخدم ملفات بيئة، متنساش تبعتها:** لو مشروعك بيعتمد على env file، لازم تبعته مع الـ `release` والـ `patch` بنفس الطريقة:
  ```bash
  shorebird release ios -- --dart-define-from-file=env/config.json
  shorebird patch --platforms=ios --release-version=<الرقم> -- --dart-define-from-file=env/config.json
  ```

- **الـ Patch لـ Dart بس:** أي تعديل في الكود الـ native، أو الملفات (assets)، أو أيقونة التطبيق، أو الصلاحيات — كل ده لازمله Release جديد.

- **جرّب قبل ما تنشر:** استخدم `shorebird preview` عشان تجرّب الإصدار على جهاز حقيقي قبل ما ترفعه.

- **حدّث الـ CLI من وقت للتاني:**
  ```bash
  shorebird upgrade
  ```

---

## 🔄 الخلاصة في سطرين

```
مرة واحدة لكل إصدار:
  تعدّل رقم الإصدار → shorebird release → ترفع للمتجر → تتثبّت

وبعد كده مع كل تحديث:
  تعدّل كود Dart → shorebird patch → يوصل لليوزرز لوحده 🎉
```

---

## 📚 لينكات هتفيدك

- [التوثيق الرسمي](https://docs.shorebird.dev)
- [Shorebird Console](https://console.shorebird.dev)
- [GitHub بتاع Shorebird](https://github.com/shorebirdtech/shorebird)

---

<div align="center">

**اتعمل بحب لمجتمع Flutter العربي**

لو الشرح ده فادك، متنساش تحط ⭐ للريبو!

</div>
