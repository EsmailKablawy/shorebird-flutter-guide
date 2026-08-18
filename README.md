<div align="center">

#  تحديث التطبيق من غير ما تستنى المتجر

**تظبط باج أو تعدّل حاجة، وتوصّلها لليوزرز في دقايق — من غير ما تستنى المراجعة.**

![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Shorebird](https://img.shields.io/badge/Shorebird-Code_Push-4A90E2?style=for-the-badge)
![iOS](https://img.shields.io/badge/iOS-000000?style=for-the-badge&logo=apple&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

</div>

---

<div dir="rtl">

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

<table>
<thead>
<tr>
<th>&nbsp;</th>
<th align="center">من غير Code Push</th>
<th align="center">مع Shorebird</th>
</tr>
</thead>
<tbody>
<tr>
<td>التحديث بيوصل امتى</td>
<td align="center">أيام (مراجعة المتجر)</td>
<td align="center">دقايق</td>
</tr>
<tr>
<td>محتاج ترفع للمتجر؟</td>
<td align="center">آه، كل مرة</td>
<td align="center">لأ</td>
</tr>
<tr>
<td>اليوزر بيعمل update بإيده؟</td>
<td align="center">آه</td>
<td align="center">لأ، بيتم لوحده</td>
</tr>
<tr>
<td>حل الباجات المستعجلة</td>
<td align="center">بطيء</td>
<td align="center">فوري</td>
</tr>
</tbody>
</table>

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

</div>

```bash
curl --proto '=https' --tlsv1.2 https://raw.githubusercontent.com/shorebirdtech/install/main/install.sh -sSf | bash
```

<div dir="rtl">

**لو على Windows (PowerShell):**

</div>

```powershell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
iwr -UseBasicParsing 'https://raw.githubusercontent.com/shorebirdtech/install/main/install.ps1' | iex
```

<div dir="rtl">

> 💡 الأمر ده بينزّل Shorebird ومعاها نسخة Flutter مخصوصة بتدعم Code Push، منفصلة تمامًا عن نسخة Flutter العادية اللي عندك.

### 3. اتأكد إن كل حاجة تمام

اقفل الـ Terminal وافتحه تاني، وبعدين شغّل:

</div>

```bash
shorebird doctor
```

<div dir="rtl">

المفروض تشوف في الآخر: `No issues detected!`

### 4. سجّل دخول

</div>

```bash
shorebird login
```

<div dir="rtl">

هيفتحلك المتصفح عشان تسجّل — ادخل بنفس الحساب اللي عملته، وبعدين ارجع للـ Terminal.

---

## 🔗 اربطها بمشروع الـ Flutter بتاعك

من جوه فولدر مشروعك، شغّل:

</div>

```bash
shorebird init
```

<div dir="rtl">

الأمر ده هيعمل الآتي:

- يبص على مشروعك ويشوف لو فيه إعدادات خاصة (زي الـ flavors)
- يعمل ملف `shorebird.yaml` في جذر المشروع (جواه الـ `app_id`)
- يضيف `shorebird.yaml` كـ asset في `pubspec.yaml`

> ℹ️ الـ `app_id` **مش سري**، وعادي جدًا ترفعه على git.

---

## 🚀 نستخدمها إزاي؟

### أول خطوة: تعمل Release

دي النسخة الأساسية اللي بترفعها للمتجر. بتتبني بأمر Shorebird (مش `flutter build`):

</div>

```bash
# لـ Android
shorebird release android

# لـ iOS
shorebird release ios
```

<div dir="rtl">

بعد ما يخلّص، بترفع الملف الناتج (`.aab` لأندرويد، `.ipa` لـ iOS) على المتجر بإيدك — من Google Play Console، أو App Store Connect / [Transporter](https://apps.apple.com/us/app/transporter/id1450874784).

### تاني خطوة: تبعت Patch

بعد ما الإصدار يبقى عند اليوزرز، أي تعديل في كود Dart تقدر تبعته على طول:

</div>

```bash
# لـ Android
shorebird patch android

# لـ iOS
shorebird patch --platforms=ios --release-version=<رقم_الإصدار>
```

<div dir="rtl">

Shorebird هيبني الـ patch، ويقارنه بالإصدار الأصلي، ويطلب منك تأكيد، وبعدين ينشره. ✅

### التحديث بيوصل لليوزر إزاي؟

التحديث بينزّل في الخلفية، وبيبان في **تاني مرة** يفتح فيها التطبيق:

</div>

```
يفتح التطبيق (بينزّل الـ patch)  ←  يقفل التطبيق  ←  يفتحه تاني (التحديث بان) ✅
```

<div dir="rtl">

---

## 📝 ملاحظات مهمة خليك واخد بالك منها

- **خلي رقم الـ Build متطابق:** لازم رقم الـ build اللي Shorebird بتبنيه يبقى مطابق للرقم اللي متثبّت على جهاز اليوزر. لو مش متطابقين، الـ patch مش هيوصل. دي نقطة الناس بتقع فيها كتير.

- **حدّد نسخة Flutter بنفسك:** استخدم `--flutter-version` مع أمر الـ `release` عشان تضمن الاستقرار وإن الـ patches تتطابق مع الإصدار:

</div>

```bash
shorebird release ios --flutter-version=3.x.x
```

<div dir="rtl">

> الـ Patch بياخد أوتوماتيك نفس نسخة Flutter بتاعة الإصدار اللي بيستهدفه، فمش محتاج تحددها فيه تاني.

- **لو بتستخدم ملفات بيئة، متنساش تبعتها:** لو مشروعك بيعتمد على env file، لازم تبعته مع الـ `release` والـ `patch` بنفس الطريقة:

</div>

```bash
shorebird release ios -- --dart-define-from-file=env/config.json
shorebird patch --platforms=ios --release-version=<الرقم> -- --dart-define-from-file=env/config.json
```

<div dir="rtl">

- **الـ Patch لـ Dart بس:** أي تعديل في الكود الـ native، أو الملفات (assets)، أو أيقونة التطبيق، أو الصلاحيات — كل ده لازمله Release جديد.

- **جرّب قبل ما تنشر:** استخدم `shorebird preview` عشان تجرّب الإصدار على جهاز حقيقي قبل ما ترفعه.

- **حدّث الـ CLI من وقت للتاني:**

</div>

```bash
shorebird upgrade
```

<div dir="rtl">

---

## 🔄 الخلاصة في سطرين

</div>

```
مرة واحدة لكل إصدار:
  تعدّل رقم الإصدار → shorebird release → ترفع للمتجر → تتثبّت

وبعد كده مع كل تحديث:
  تعدّل كود Dart → shorebird patch → يوصل لليوزرز لوحده 🎉
```

<div dir="rtl">

---

## 📚 لينكات هتفيدك

- [التوثيق الرسمي](https://docs.shorebird.dev)
- [Shorebird Console](https://console.shorebird.dev)
- [GitHub بتاع Shorebird](https://github.com/shorebirdtech/shorebird)

</div>

---

<div align="center">

**اتعمل بحب لمجتمع Flutter العربي**

لو الشرح ده فادك، متنساش تحط ⭐ للريبو!

</div>
