# Fix Missing Wi-Fi Icon on ASUS TUF Gaming (FA506NF / Realtek RTL8852BE)
# حل مشكلة اختفاء أيقونة الواي فاي في لابتوبات ASUS TUF Gaming

[English](#english) | [العربية](#arabic)

---

<a name="english"></a>
## English

I ran into a recurring issue on my **ASUS TUF Gaming FA506NF** (running Windows 11) where the Wi-Fi icon would completely disappear from the taskbar, and the **Realtek RTL8852BE** wireless card would vanish from Device Manager—leaving only the Ethernet adapter visible. Rebooting or resetting the network only fixed it temporarily.

After testing several workarounds, these exact steps permanently fixed the problem for me.

### What Happened
* The Wi-Fi toggle disappeared randomly on boot or after waking from sleep.
* Under **Device Manager > Network adapters**, `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC` was completely missing.

### How I Fixed It

#### 1. Hard Reset (Static Discharge)
If your Wi-Fi card is currently missing from Device Manager, do this first to make Windows detect the hardware again:
1. Shut down the laptop completely (**Start > Power > Shut down**).
2. Unplug the charger and remove any connected USB devices.
3. Press and hold the **Power Button** for **35–40 seconds**.
4. Plug the charger back in and boot up. The Wi-Fi adapter should now show up again in Device Manager.

#### 2. Turn Off Windows Fast Startup
Fast Startup puts the network card in a suspended state during shutdown, which prevents it from initializing properly on the next boot.
1. Open **Control Panel** > **Power Options**.
2. Click **Choose what the power buttons do** on the left.
3. Click **Change settings that are currently unavailable** at the top.
4. Uncheck **Turn on fast startup (recommended)** and click **Save changes**.

#### 3. Clean Install the Official ASUS Driver
Windows Update tends to install generic drivers that drop out under load. Installing the OEM version from ASUS solved the stability issue:
1. Go to the [ASUS Support Download Center](https://www.asus.com/support/download-center/) and search for your exact model (in my case, `FA506NF`).
2. Under **Driver & Tools > Networking**, download the official **Realtek Wireless LAN Driver** (version `V6001.15.163.101` worked reliably for me).
3. Right-click the installer, select **Run as administrator**, complete the setup, and restart the laptop.

#### 4. Disable Power Saving on the Adapter (If Available)
1. Open **Device Manager** > **Network adapters**.
2. Right-click `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC` and select **Properties**.
3. If you see a **Power Management** tab, uncheck **Allow the computer to turn off this device to save power** and click **OK**. *(Note: This tab may be hidden on newer Windows 11 builds using Modern Standby).*

### Hardware Note
On some ASUS TUF models, the M.2 Wi-Fi card sits directly beneath the primary NVMe SSD, so heat can cause it to disconnect over time. If the software steps above don't hold, opening the back cover to reseat and clean the Wi-Fi card—or swapping it for an **Intel AX200 / AX210**—will permanently solve it.

---

<a name="arabic"></a>
## العربية

واجهت مشكلة متكررة في جهازي **ASUS TUF Gaming FA506NF** (على نظام ويندوز 11)، حيث كانت أيقونة الواي فاي تختفي فجأة من شريط المهام، ويختفي كرت الشبكة اللاسلكية **Realtek RTL8852BE** بالكامل من إدارة الأجهزة (Device Manager) ولا يبقى سوى كرت السلك. إعادة التشغيل أو عمل Network Reset كان يحل المشكلة مؤقتاً فقط.

بعد تجربة عدة حلول، هذه الخطوات بالترتيب هي التي أنهت المشكلة معي بشكل نهائي.

### وصف المشكلة
* اختفاء خيار وأيقونة الواي فاي عند تشغيل الجهاز أو بعد الخروج من وضع السكون.
* عند فتح **إدارة الأجهزة (Device Manager) > محولات الشبكة (Network adapters)**، يختفي تعريف `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC` تماماً.

### خطوات الحل

#### 1. تفريغ الشحنات الساكنة (Hard Reset)
إذا كان كرت الواي فاي مختفياً حالياً من إدارة الأجهزة، نفذ هذه الخطوة أولاً لإجبار النظام على قراءة الكرت مجدداً:
1. أوقف تشغيل اللابتوب بالكامل (**إيقاف التشغيل / Shut down**).
2. افصل الشاحن وأي أجهزة متصلة بمنافذ USB.
3. اضغط باستمرار على **زر التشغيل (Power)** لمدة **35 إلى 40 ثانية**.
4. أعد توصيل الشاحن وشغّل الجهاز؛ سيعود الكرت للظهور في إدارة الأجهزة.

#### 2. تعطيل ميزة بدء التشغيل السريع (Fast Startup)
هذه الميزة تبقي كرت الشبكة في حالة تعليق عند إطفاء الجهاز وتمنعه من الإقلاع بشكل سليم في المرة التالية:
1. افتح **لوحة التحكم (Control Panel)** > **خيارات الطاقة (Power Options)**.
2. اختر من القائمة الجانبية **تحديد ما تفعله أزرار الطاقة (Choose what the power buttons do)**.
3. اضغط في الأعلى على **تغيير الإعدادات غير المتوفرة حالياً (Change settings that are currently unavailable)**.
4. أزل علامة الصح من أمام **تشغيل بدء التشغيل السريع (Turn on fast startup)** واضغط **حفظ التغييرات**.

#### 3. تثبيت التعريف الرسمي من موقع ASUS
تحديثات ويندوز التلقائية تثبت تعريفات عامة تسبب فصل الكرت باستمرار؛ لذا الأفضل تثبيت تعريف ASUS الرسمي:
1. ادخل إلى [مركز تحميل تعريفات ASUS](https://www.asus.com/support/download-center/) وابحث برقم موديل جهازك الدقيق (في حالتي `FA506NF`).
2. من قسم **Driver & Tools > Networking**، حمّل التعريف الرسمي **Realtek Wireless LAN Driver** (الإصدار `V6001.15.163.101` هو الذي استقر معي).
3. اضغط بالزر الأيمن على ملف التثبيت واختر **تشغيل كمسؤول (Run as administrator)**، أكمل التثبيت، ثم أعد تشغيل الجهاز.

#### 4. إيقاف توفير الطاقة للكرت (إن وُجد)
1. افتح **إدارة الأجهزة (Device Manager)** > **محولات الشبكة**.
2. اضغط بالزر الأيمن على `Realtek 8852BE Wireless LAN WiFi 6 PCI-E NIC` واختر **خصائص (Properties)**.
3. إذا ظهر لك تبويب **إدارة الطاقة (Power Management)**، أزل علامة الصح من أمام **السماح للكمبيوتر بإيقاف تشغيل هذا الجهاز لتوفير الطاقة** واضغط **موافق**. *(ملاحظة: قد لا يظهر هذا التبويب في بعض نسخ ويندوز 11 الحديثة)*.

### ملاحظة بخصوص الهاردوير
في تصميم بعض موديلات ASUS TUF، يقع كرت الواي فاي تحت وحدة التخزين (NVMe SSD) مباشرة، مما يعرضه للحرارة. إذا استمرت المشكلة بعد تطبيق الخطوات البرمجية أعلاه، فالحل النهائي هو فتح الغطاء الخلفي وتنظيف مدخل الكرت وإعادة تركيبه بإحكام، أو استبداله بكرت **Intel AX200 / AX210**.
