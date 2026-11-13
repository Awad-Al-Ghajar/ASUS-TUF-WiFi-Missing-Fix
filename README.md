# Fix: Missing Wi-Fi Icon & Disappearing WLAN Adapter on ASUS TUF Gaming Laptops (Windows 10/11)
# حل مشكلة اختفاء أيقونة الواي فاي وكرت الشبكة في لابتوبات ASUS TUF Gaming

[![Windows](https://img.shields.io/badge/OS-Windows%2010%20%7C%2011-blue?logo=windows)](https://www.microsoft.com/windows)
[![Laptop](https://img.shields.io/badge/Series-ASUS%20TUF%20Gaming-orange)](https://www.asus.com/)
[![Wi-Fi Card](https://img.shields.io/badge/Adapter-Realtek%20RTL8852BE%20%7C%20MediaTek%20MT7921-green)](#)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20العربية-lightgrey)](#)

**🌐 Language / اللغة:** [English Version](#-english-version) | [النسخة العربية](#-النسخة-العربية)

---

<a name="-english-version"></a>
## 🇺🇸 English Version

A complete step-by-step troubleshooting guide to permanently resolve the recurring issue where the Wi-Fi option disappears from the taskbar and the WLAN adapter vanishes from Device Manager on **ASUS TUF Gaming** laptops (such as **FA506**, **FX506**, **FA507**, and **FX507**).

### 📋 Symptoms
* The Wi-Fi icon and toggle completely disappear from the Windows Quick Settings / System Tray upon boot or waking from sleep.
* Under **Device Manager > Network adapters**, the wireless card (e.g., `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC` or `MediaTek Wi-Fi 6 MT7921`) is completely missing, leaving only the Ethernet controller (`Realtek PCIe GbE Family Controller`) and `WAN Miniport` entries.
* Multiple reboots or running **Network Reset** temporarily restores Wi-Fi, only for the issue to return after the next shutdown.

### 🔍 Root Causes
1. **Windows Fast Startup Conflict:** Keeps the wireless adapter in an unstable hybrid-sleep state during shutdown, preventing proper hardware initialization on the next cold boot.
2. **Static Charge Buildup:** Residual electrical charge on the motherboard causes the PCIe M.2 WLAN slot to hang until power-cycled.
3. **Generic Windows Drivers:** Windows Update often installs outdated or generic inbox drivers instead of the stable OEM drivers provided by ASUS.

### 🛠️ Step-by-Step Resolution

#### Step 1: Perform a Static Discharge (Hard Reset)
*Use this step immediately if your Wi-Fi adapter is currently missing from Device Manager.*
1. Completely shut down the laptop (**Start > Power > Shut down**).
2. Unplug the AC power adapter and disconnect all external USB peripherals.
3. Press and hold the **Power Button** continuously for **30–40 seconds**.
4. Reconnect the power adapter and turn the laptop back on.
5. **Verification:** Open **Device Manager > Network adapters** and confirm that your wireless adapter reappears in the list.

#### Step 2: Disable Windows Fast Startup (Prevents Recurrence)
1. Open **Control Panel** (switch *View by* to **Small icons** if needed) and select **Power Options**.
2. Click **Choose what the power buttons do** on the left sidebar.
3. Click **Change settings that are currently unavailable** at the top (requires administrator privileges).
4. Scroll down to **Shutdown settings** and **uncheck** `Turn on fast startup (recommended)`.
5. Click **Save changes**.

#### Step 3: Install the Official OEM Wireless Driver from ASUS
1. Check the exact model number on the bottom sticker of your laptop (e.g., `FA506NF`) and note your wireless chip model (e.g., `Realtek RTL8852BE`).
2. Visit the official [ASUS Support Download Center](https://www.asus.com/support/download-center/).
3. Enter your exact laptop model > go to **Driver & Tools** > select your OS (**Windows 11 64-bit** or **Windows 10 64-bit**).
4. Expand the **Networking** section and download the latest **Realtek Wireless LAN Driver** (or **MediaTek** / **Intel**, matching your hardware).
   > **Tip:** It is also recommended to download and install the matching **Realtek Bluetooth Driver** from the same section, as both modules share the same combo chip.
5. Right-click the downloaded installer (`.exe` or `Install.bat`), select **Run as administrator**, complete the setup, and **restart** your laptop.

#### Step 4: Verify Device Status & Power Management
1. Right-click the **Start** button and open **Device Manager**.
2. Expand **Network adapters**, double-click your wireless card (e.g., `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC`), and verify under the **General** tab that **Device status** reads: *"This device is working properly."*
3. *(Optional — depends on Windows Modern Standby support)*: If the **Power Management** tab is visible at the top, uncheck **Allow the computer to turn off this device to save power** and click **OK**.

### ⚠️ Hardware Note (If the Issue Persists)
In certain ASUS TUF chassis designs, the M.2 Wi-Fi card is mounted directly underneath the primary NVMe SSD, exposing it to sustained heat. If the card continues to vanish even after applying all software fixes above:
* Open the back cover, reseat the Wi-Fi card, and clean the gold contacts/slot.
* Alternatively, upgrade the card to an **Intel AX200** or **Intel AX210** M.2 Wi-Fi module, which resolves thermal dropout issues permanently.

---

<a name="-النسخة-العربية"></a>
## 🇸🇦 النسخة العربية

دليل شامل خطوة بخطوة لحل مشكلة اختفاء أيقونة وخيار الواي فاي (Wi-Fi) من شريط المهام واختفاء كرت الشبكة اللاسلكية من إدارة الأجهزة نهائياً في لابتوبات **ASUS TUF Gaming** (مثل موديلات **FA506** و **FX506** و **FA507** و **FX507**).

### 📋 أعراض المشكلة
* اختفاء أيقونة وخيار الواي فاي تماماً عند تشغيل اللابتوب أو الخروج من وضع السكون.
* عند فتح **إدارة الأجهزة (Device Manager)** > **محولات الشبكة (Network adapters)**، يختفي كرت الواي فاي (مثل `Realtek 8852BE Wireless LAN WiFi 6` أو `MediaTek MT7921`) ويظهر كرت السلك (`Realtek PCIe GbE`) فقط.
* عودة الشبكة مؤقتاً بعد تكرار إعادة التشغيل أو عمل **إعادة ضبط الشبكة (Network Reset)**، ثم تكرار المشكلة في المرة القادمة.

### 🔍 الأسباب الرئيسية
1. **تعارض ميزة بدء التشغيل السريع (Fast Startup):** تبقي كرت الواي فاي في حالة سبات غير مستقرة عند إيقاف تشغيل الجهاز، مما يمنع إقلاعه بشكل سليم عند التشغيل التالي.
2. **تراكم الشحنات الكهربائية الساكنة:** يسبب تعليق دوائر الطاقة الخاصة بمنفذ كرت الشبكة على اللوحة الأم.
3. **تعريفات ويندوز الافتراضية:** يقوم تحديث ويندوز أحياناً بتثبيت تعريف عام أو قديم بدلاً من التعريف الرسمي المستقر من شركة ASUS.

### 🛠️ خطوات الحل الجذري

#### الخطوة 1: تفريغ الشحنات الساكنة (Hard Reset) لإعادة إظهار الكرت
*تُستخدم هذه الخطوة فوراً إذا كان كرت الواي فاي مختفياً حالياً من إدارة الأجهزة.*
1. أوقف تشغيل اللابتوب بالكامل (**ابدأ > الطاقة > إيقاف التشغيل**).
2. افصل كابل الشاحن وأي أجهزة خارجية متصلة (ماوس، فلاشة، إلخ).
3. اضغط باستمرار على **زر التشغيل (Power)** لمدة **30 إلى 40 ثانية** متواصلة.
4. أعد توصيل الشاحن وشغّل اللابتوب.
5. **التحقق:** افتح **إدارة الأجهزة > محولات الشبكة** وتأكد من عودة ظهور اسم كرت الواي فاي في القائمة.

#### الخطوة 2: تعطيل ميزة بدء التشغيل السريع في ويندوز (لمنع تكرار المشكلة)
1. افتح **لوحة التحكم (Control Panel)** (غيّر طريقة العرض إلى **أيقونات صغيرة** إذا لزم الأمر) واختر **خيارات الطاقة (Power Options)**.
2. من القائمة الجانبية اختر **تحديد ما تفعله أزرار الطاقة (Choose what the power buttons do)**.
3. اضغط في الأعلى على **تغيير الإعدادات غير المتوفرة حالياً (Change settings that are currently unavailable)**.
4. انزل إلى قسم **إعدادات إيقاف التشغيل** وأزل علامة الصح من أمام **تشغيل بدء التشغيل السريع (مستحسن)**.
5. اضغط على **حفظ التغييرات (Save changes)**.

#### الخطوة 3: تحميل وتثبيت التعريف الرسمي من موقع ASUS
1. اقرأ رقم الموديل الدقيق من الملصق أسفل اللابتوب (مثال: `FA506NF`) ونوع شريحة الواي فاي (مثال: `Realtek RTL8852BE`).
2. ادخل إلى مركز تحميل تعريفات ASUS الرسمي: [ASUS Support Download Center](https://www.asus.com/support/download-center/).
3. اكتب رقم موديل جهازك > اختر **Driver & Tools** > حدد نظام التشغيل (**Windows 11 64-bit** أو **Windows 10 64-bit**).
4. افتح قسم **Networking** وحمّل أحدث إصدار من **Realtek Wireless LAN Driver** (أو **MediaTek** / **Intel** حسب نوع الكرت لديك).
   > **نصيحة:** يُنصح أيضاً بتحميل وتثبيت تعريف البلوتوث **Realtek Bluetooth Driver** من نفس القسم لأن الشريحتين مدمجتان معاً.
5. اضغط بالزر الأيمن على ملف التثبيت المحمّل (`.exe` أو `Install.bat`)، اختر **تشغيل كمسؤول (Run as administrator)**، أكمل التثبيت، ثم **أعد تشغيل اللابتوب**.

#### الخطوة 4: التأكد من حالة الكرت وإدارة الطاقة
1. اضغط بالزر الأيمن على زر **ابدأ** وافتح **إدارة الأجهزة (Device Manager)**.
2. وسّع قائمة **محولات الشبكة**، اضغط مرتين على كرت الواي فاي (مثل `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC`)، وتأكد في تبويب **عام** أن حالة الجهاز هي: **"يعمل هذا الجهاز بشكل صحيح."**
3. *(اختياري — يعتمد على إصدار ويندوز)*: إذا ظهر تبويب **إدارة الطاقة (Power Management)** في الأعلى، أزل علامة الصح من أمام **السماح للكمبيوتر بإيقاف تشغيل هذا الجهاز لتوفير الطاقة** واضغط **موافق**.

### ⚠️ ملاحظة عتادية (في حال استمرار المشكلة)
في بعض تصاميم لابتوبات ASUS TUF، يقع كرت الواي فاي أسفل وحدة التخزين (NVMe SSD) مباشرة، مما يعرضه لحرارة مستمرة. إذا استمر اختفاء الكرت حتى بعد تطبيق جميع الخطوات البرمجية أعلاه:
* افتح الغطاء الخلفي، أخرج كرت الواي فاي، ونظّف مدخله وأطرافه الذهبية ثم أعد تركيبه بإحكام.
* أو استبدل الكرت بشريحة **Intel AX200** أو **Intel AX210** التي تحل مشاكل الحرارة وفصل الإشارة بشكل نهائي.

---

## 🏷️ Keywords / الوسوم
`asus-tuf` `wifi-missing` `realtek-rtl8852be` `mediatek-mt7921` `windows-11` `network-adapter-missing` `fa506` `fx506` `troubleshooting` `اختفاء-الواي-فاي` `اسوس-تاف`
