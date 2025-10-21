<div dir="rtl" align="right">

<h3>Event IDs و Artifacts پیشرفته برای تشخیص دقیق‌تر Lateral Movement</h3>

<h2>Event IDs تکمیلی برای PowerShell Remoting</h2>

<p>علاوه بر Event ID های ذکر شده در بخش قبل، چندین Event ID دیگر نیز برای تشخیص دقیق‌تر PowerShell Remoting وجود دارند. در لاگ <b>Microsoft-Windows-PowerShell/Operational</b>، Event ID <b>4103</b> جزئیات اجرای pipeline در PowerShell را ثبت می‌کند که می‌تواند نشان دهد چه دستوراتی از طریق PowerShell Remoting اجرا شده‌اند. Event ID <b>4104</b> محتوای کامل اسکریپت‌های اجرا شده را ثبت می‌کند، اگرچه خروجی آن‌ها را ثبت نمی‌کند. Event ID <b>53504</b> اطلاعات مربوط به Named Pipe های PowerShell را ثبت می‌کند که شامل حساب کاربری احراز هویت شده است.</p>
<p>در لاگ <b>Windows PowerShell.evtx</b>، Event ID <b>400</b> و <b>403</b> به ترتیب شروع و پایان یک جلسه راه دور را نشان می‌دهند. Event ID <b>800</b> اطلاعات اجرای pipeline و بخش‌هایی از کد اسکریپت را ثبت می‌کند. در لاگ <b>Microsoft-Windows-WinRM/Operational</b>، Event ID <b>91</b> ایجاد یک جلسه جدید و حساب کاربری استفاده شده برای احراز هویت را ثبت می‌کند. Event ID <b>168</b> نیز حساب کاربری احراز هویت شده را ثبت می‌کند. Event ID های <b>80</b>، <b>132</b>، <b>143</b>، <b>166</b> و <b>81</b> همگی رویدادهای مختلف مربوط به WinRM را ثبت می‌کنند که می‌توانند در تحلیل Timeline مفید باشند.</p>

<h2>Event IDs تکمیلی برای PsExec</h2>

<p>برای تشخیص دقیق‌تر PsExec، Event ID <b>5140</b> در لاگ Security (که به طور پیش‌فرض فعال نیست) دسترسی به Network Share Objects را ثبت می‌کند. این رویداد شامل حساب کاربری، آدرس IP مبدا و Share مورد دسترسی (مانند ADMIN$ یا C$) است. Event ID <b>5145</b> بررسی مجوزهای دسترسی به Network Share Objects را ثبت می‌کند. Event ID <b>4648</b> تلاش برای ورود با استفاده از اعتبارنامه‌های صریح (Explicit Credentials) را ثبت می‌کند که اغلب در حملات PsExec مشاهده می‌شود.</p>
<p>اگر Sysmon نصب باشد، Event ID <b>17</b> (PipeEvent - Pipe Created) و Event ID <b>18</b> (PipeEvent - Pipe Connected) ایجاد و اتصال به Named Pipe با نام <code>\pipe\PSEXESVC</code> را ثبت می‌کنند. Event ID <b>3</b> (Network Connection) اتصالات شبکه‌ای به پورت 445 را ثبت می‌کند که می‌تواند نشان‌دهنده استفاده از SMB برای PsExec باشد. Event ID <b>11</b> (FileCreate) ایجاد فایل <code>PSEXESVC.exe</code> در <code>C:\Windows</code> را ثبت می‌کند.</p>

<h2>Event IDs تکمیلی برای RDP</h2>

<p>در لاگ <b>Microsoft-Windows-RemoteDesktopServices-RdpCoreTS/Operational</b>، Event ID <b>131</b> تلاش‌های اتصال را با آدرس IP مبدا ثبت می‌کند. Event ID <b>98</b> یک اتصال RDP موفق را نشان می‌دهد. در لاگ <b>Microsoft-Windows-TerminalServices-RemoteConnectionManager/Operational</b>، Event ID <b>1149</b> یک تلاش موفق برای ورود RDP را نشان می‌دهد، اما این به معنای ورود موفق کامل نیست و می‌تواند برای شناسایی Brute Force یا Network Scanning استفاده شود.</p>
<p>در لاگ <b>Microsoft-Windows-TerminalServices-LocalSessionManager/Operational</b>، Event ID <b>21</b> یک ورود موفق RDP را با نام کاربری و شماره Session ID ثبت می‌کند و می‌تواند با Event ID 4624 Type 10 همبسته شود. Event ID <b>22</b> اعلان شروع Session را ثبت می‌کند. Event ID <b>24</b> قطع اتصال Session را ثبت می‌کند. Event ID <b>25</b> اتصال مجدد به Session را ثبت می‌کند.</p>

<h2>Event IDs تکمیلی برای Scheduled Tasks</h2>

<p>در لاگ <b>Microsoft-Windows-TaskScheduler/Operational</b>، Event ID <b>129</b> به‌روزرسانی ثبت Task را نشان می‌دهد. Event ID <b>140</b> به‌روزرسانی Task را ثبت می‌کند. Event ID <b>141</b> حذف Task را ثبت می‌کند. Event ID <b>200</b> اجرای Task را ثبت می‌کند که شامل نام Task و زمان اجرا است. Event ID <b>201</b> تکمیل Task را ثبت می‌کند که شامل کد خروجی (Exit Code) است و می‌تواند نشان دهد که آیا Task با موفقیت اجرا شده یا با خطا مواجه شده است.</p>
<p>در لاگ Security، Event ID <b>4700</b> فعال شدن یک Task را ثبت می‌کند و Event ID <b>4701</b> غیرفعال شدن یک Task را ثبت می‌کند. این رویدادها می‌توانند نشان دهند که مهاجم در حال تغییر وضعیت Task های موجود است.</p>

<h2>Event IDs تکمیلی برای Services</h2>

<p>در لاگ System، Event ID <b>7035</b> ارسال فرمان Start یا Stop به یک سرویس را ثبت می‌کند. Event ID <b>7036</b> شروع یا توقف واقعی یک سرویس را ثبت می‌کند. Event ID <b>7034</b> کرش شدن یک سرویس را ثبت می‌کند که می‌تواند نشان‌دهنده یک سرویس مخرب ناپایدار باشد. Event ID <b>7040</b> تغییر نوع شروع سرویس (Startup Type) را ثبت می‌کند، مثلاً تغییر از Manual به Automatic که می‌تواند نشانه‌ای از تلاش برای پایداری باشد.</p>
<p>در لاگ Security، Event ID <b>4697</b> نصب یک سرویس جدید را با جزئیات کامل شامل نام سرویس، مسیر فایل اجرایی، نوع سرویس و حساب کاربری ثبت می‌کند.</p>

<h2>Event IDs تکمیلی برای WMI</h2>

<p>در لاگ <b>Microsoft-Windows-WMI-Activity/Operational</b>، Event ID <b>5857</b> فعالیت WMI را تشخیص می‌دهد. Event ID <b>5860</b> ثبت یک Event Consumer موقت را نشان می‌دهد. Event ID <b>5861</b> ثبت یک Event Consumer دائمی را نشان می‌دهد که اغلب برای پایداری استفاده می‌شود. WMI Event Consumers می‌توانند به طور خودکار کد مخرب را در پاسخ به رویدادهای خاص سیستم اجرا کنند.</p>
<p>اگر Sysmon نصب باشد، Event ID <b>19</b> (WmiEvent - WmiEventFilter activity detected)، Event ID <b>20</b> (WmiEvent - WmiEventConsumer activity detected) و Event ID <b>21</b> (WmiEvent - WmiEventConsumerToFilter activity detected) فعالیت‌های مشکوک WMI را ثبت می‌کنند که می‌توانند نشانه‌ای از استفاده از WMI برای پایداری یا اجرای کد باشند.</p>

<h2>Event IDs عمومی برای Lateral Movement</h2>

<p>چندین Event ID عمومی وجود دارند که در تمامی تکنیک‌های Lateral Movement مشترک هستند و باید به طور مداوم نظارت شوند. Event ID <b>4656</b> درخواست یک Handle به یک Object را ثبت می‌کند. Event ID <b>4658</b> بستن Handle به یک Object را ثبت می‌کند. Event ID <b>4660</b> حذف یک Object را ثبت می‌کند. Event ID <b>4663</b> تلاش برای دسترسی به یک Object را ثبت می‌کند. این رویدادها می‌توانند دسترسی به فایل‌ها و رجیستری را نشان دهند.</p>
<p>Event ID <b>4673</b> فراخوانی یک سرویس ممتاز (Privileged Service) را ثبت می‌کند. Event ID <b>4689</b> خروج یک فرآیند را ثبت می‌کند. Event ID <b>4720</b> ایجاد یک حساب کاربری جدید را ثبت می‌کند که می‌تواند نشانه‌ای از ایجاد حساب‌های Backdoor باشد.</p>
<p>Event ID <b>4768</b> درخواست یک Kerberos TGT را ثبت می‌کند. Event ID <b>4769</b> درخواست یک Kerberos Service Ticket را ثبت می‌کند. این رویدادها برای تشخیص حملات مبتنی بر Kerberos مانند Kerberoasting و Golden Ticket بسیار مهم هستند.</p>
<p>Event ID <b>4946</b> تغییر در لیست استثنائات Windows Firewall را ثبت می‌کند که می‌تواند نشان دهد مهاجم در حال باز کردن پورت‌های جدید برای دسترسی راه دور است. Event ID <b>5154</b> اجازه Windows Filtering Platform به یک برنامه برای Listen کردن روی یک پورت را ثبت می‌کند. Event ID <b>5156</b> اجازه یک اتصال توسط Windows Filtering Platform را ثبت می‌کند. Event ID <b>5447</b> تغییر یک فیلتر Windows Filtering Platform را ثبت می‌کند.</p>
<p>Event ID <b>8222</b> در لاگ System ایجاد یک Shadow Copy را ثبت می‌کند که می‌تواند نشانه‌ای از تلاش برای سرقت داده یا آماده‌سازی برای Ransomware باشد. Event ID <b>104</b> پاک شدن لاگ‌های سیستم را ثبت می‌کند که یک نشانه واضح از تلاش برای پاک کردن ردپا است.</p>
<p>Event ID <b>20001</b> در لاگ Application اتصال سخت‌افزار جدید (مانند دستگاه‌های USB) را ثبت می‌کند که می‌تواند برای تشخیص استفاده از دستگاه‌های ذخیره‌سازی قابل حمل برای سرقت داده مفید باشد. Event ID <b>60</b> در لاگ <b>Microsoft-Windows-Bits-Client</b> فعالیت BITS (Background Intelligent Transfer Service) را ثبت می‌کند که مهاجمان اغلب از آن برای دانلود بدافزار یا exfiltration داده استفاده می‌کنند.</p>

<h2>Sysmon Event IDs برای Lateral Movement</h2>

<p>اگر Sysmon در محیط نصب شده باشد، Event ID های بسیار ارزشمندی برای تشخیص Lateral Movement فراهم می‌کند. <b>Sysmon Event ID 1</b> (Process Creation) تمامی فرآیندهای ایجاد شده را با جزئیات کامل شامل Command Line، Parent Process، Hashes و User ثبت می‌کند. این رویداد برای تشخیص اجرای ابزارهای مخرب مانند Mimikatz، PsExec، PowerShell با پارامترهای مشکوک و سایر ابزارها بسیار مهم است.</p>
<p><b>Sysmon Event ID 3</b> (Network Connection) تمامی اتصالات شبکه‌ای را با جزئیات شامل Source IP، Destination IP، Port و Process Name ثبت می‌کند. این رویداد برای شناسایی اتصالات غیرمعمول بین سیستم‌ها، به ویژه اتصالات Workstation-to-Workstation که معمولاً غیرعادی هستند، بسیار مفید است.</p>
<p><b>Sysmon Event ID 5</b> (Process Terminated) پایان فرآیندها را ثبت می‌کند که می‌تواند برای تحلیل Timeline و تعیین مدت زمان اجرای فرآیندهای مشکوک مفید باشد. <b>Sysmon Event ID 7</b> (Image Loaded) بارگذاری DLL ها را ثبت می‌کند که می‌تواند DLL Injection یا بارگذاری DLL های مخرب را نشان دهد.</p>
<p><b>Sysmon Event ID 8</b> (CreateRemoteThread) ایجاد Thread های راه دور را ثبت می‌کند که یک تکنیک رایج برای Process Injection است. <b>Sysmon Event ID 10</b> (ProcessAccess) دسترسی به فرآیندها را ثبت می‌کند که برای تشخیص تلاش‌های Credential Dumping از lsass.exe بسیار حیاتی است.</p>
<p><b>Sysmon Event ID 11</b> (FileCreate) ایجاد فایل‌ها را ثبت می‌کند که می‌تواند نشان دهد مهاجم در حال کپی کردن ابزارها یا بدافزار به سیستم است. <b>Sysmon Event ID 13</b> (RegistryEvent - Value Set) تنظیم مقادیر رجیستری را ثبت می‌کند که برای تشخیص تکنیک‌های پایداری مفید است.</p>
<p><b>Sysmon Event ID 17</b> (PipeEvent - Pipe Created) و <b>Sysmon Event ID 18</b> (PipeEvent - Pipe Connected) ایجاد و اتصال به Named Pipes را ثبت می‌کنند که برای تشخیص PsExec و سایر ابزارهایی که از Named Pipes برای ارتباط استفاده می‌کنند، بسیار مهم است.</p>
<p><b>Sysmon Event ID 22</b> (DNSEvent - DNS query) کوئری‌های DNS را ثبت می‌کند که می‌تواند برای تشخیص ارتباط با دامنه‌های مخرب یا Command and Control servers مفید باشد.</p>

<h2>Artifacts فایل سیستم برای Lateral Movement</h2>

<p>علاوه بر Event Logs، Artifacts متعددی در فایل سیستم باقی می‌مانند که می‌توانند شواهد ارزشمندی از Lateral Movement فراهم کنند. برای <b>PsExec</b>، فایل <code>C:\Windows\psexesvc.exe</code> یا <code>C:\Windows\[random-8-chars].exe</code> (برای Impacket PsExec) به طور موقت ایجاد می‌شود. فایل Prefetch در <code>C:\Windows\Prefetch\PSEXESVC.EXE-*.pf</code> حتی پس از حذف فایل اجرایی باقی می‌ماند و اطلاعات مهمی مانند تعداد اجرا، آخرین زمان اجرا و فایل‌های بارگذاری شده را فراهم می‌کند.</p>
<p>برای <b>RDP</b>، فایل‌های Bitmap Cache در <code>C:\Users\[username]\AppData\Local\Microsoft\Terminal Server Client\Cache\</code> ذخیره می‌شوند. این فایل‌ها با نام‌های <code>bcache##.bmc</code> و <code>cache####.bin</code> وجود دارند و می‌توانند تصاویر صفحه نمایش جلسات RDP را ذخیره کنند که با ابزارهایی مانند BMC-Tools قابل بازسازی هستند.</p>
<p>برای <b>Scheduled Tasks</b>، فایل‌های XML در <code>C:\Windows\System32\Tasks\</code> ذخیره می‌شوند که حاوی تمامی جزئیات Task شامل Command Line، Triggers و Security Settings هستند. فایل‌های قدیمی <code>.job</code> نیز در <code>C:\Windows\Tasks\</code> برای Legacy Tasks وجود دارند. فایل Prefetch برای <code>SCHTASKS.EXE</code> در <code>C:\Windows\Prefetch\SCHTASKS.EXE-*.pf</code> ایجاد می‌شود.</p>
<p>برای <b>Services</b>، فایل‌های اجرایی سرویس در مسیرهای مختلف قرار دارند، اما معمولاً در <code>C:\Windows\System32</code> یا دایرکتوری‌های موقت هستند. فایل‌های Prefetch برای فایل‌های اجرایی سرویس ایجاد می‌شوند.</p>
<p>برای <b>SMB/Network Shares</b>، فایل‌های Prefetch برای <code>NET.EXE</code> و <code>NET1.EXE</code> در <code>C:\Windows\Prefetch\NET.EXE-*.pf</code> و <code>C:\Windows\Prefetch\NET1.EXE-*.pf</code> ایجاد می‌شوند که نشان می‌دهند دستورات <code>net use</code> یا <code>net share</code> اجرا شده‌اند.</p>

<h2>Artifacts رجیستری برای Lateral Movement</h2>

<p>رجیستری ویندوز حاوی Artifacts متعددی است که می‌توانند شواهد Lateral Movement را فراهم کنند. برای <b>Services</b>، کلید <code>HKLM\SYSTEM\CurrentControlSet\Services\[ServiceName]</code> حاوی اطلاعات کامل سرویس شامل <code>ImagePath</code> (مسیر فایل اجرایی)، <code>Start</code> (نوع Startup)، <code>Type</code> (نوع سرویس) و <code>ObjectName</code> (حساب کاربری) است. تحلیل این کلیدها می‌تواند سرویس‌های مشکوک را شناسایی کند.</p>
<p>برای <b>Scheduled Tasks</b> (Legacy)، کلیدهای <code>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tasks</code> و <code>HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tree</code> حاوی اطلاعات Task ها هستند.</p>
<p>برای <b>Terminal Services/RDP</b>، کلید <code>HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server</code> حاوی تنظیمات RDP است. کلید <code>HKCU\Software\Microsoft\Terminal Server Client\Servers</code> حاوی لیست سرورهایی است که کاربر به آن‌ها از طریق RDP متصل شده است.</p>
<p>برای <b>WMI</b>، کلید <code>HKLM\SOFTWARE\Microsoft\WBEM\ESS</code> حاوی اطلاعات مربوط به WMI Event Subscriptions است که می‌توانند برای پایداری استفاده شوند.</p>

<h2>Network Artifacts و پورت‌های رایج</h2>

<p>شناخت پورت‌های رایج مورد استفاده برای Lateral Movement می‌تواند به تحلیلگران کمک کند تا ترافیک مشکوک را شناسایی کنند. <b>RDP</b> از پورت TCP 3389 استفاده می‌کند. <b>SMB</b> از پورت‌های TCP 445 و TCP 139 استفاده می‌کند. <b>WMI</b> از پورت TCP 135 (RPC Endpoint Mapper) و پورت‌های Dynamic در محدوده 49152-65535 استفاده می‌کند. <b>WinRM/PowerShell Remoting</b> از پورت TCP 5985 (HTTP) و TCP 5986 (HTTPS) استفاده می‌کند. <b>PsExec</b> از پورت TCP 445 (SMB) استفاده می‌کند.</p>
<p>تحلیلگران باید به دنبال الگوهای غیرمعمول در ترافیک شبکه باشند، از جمله اتصالات Internal-to-Internal غیرمعمول، اتصالات به Share های ADMIN$، C$ و IPC$، تلاش‌های احراز هویت ناموفق متعدد و سپس موفق (نشانه Brute Force)، و Lateral Movement از Workstation به Workstation که معمولاً غیرعادی است و نشانه‌ای از حمله است.</p>

<h2>نکات تحلیل Timeline</h2>

<p>برای تحلیل موثر Lateral Movement، تحلیلگران باید از تکنیک‌های Timeline Analysis استفاده کنند. <b>Pivot on Logon IDs</b> یعنی همبسته کردن Event ID 4624 با سایر رویدادها با استفاده از Logon ID برای ردیابی تمامی فعالیت‌های یک نشست خاص. <b>Source IP Tracking</b> یعنی دنبال کردن آدرس IP مبدا در سراسر چندین سیستم برای شناسایی مسیر حرکت مهاجم. <b>Account Usage Patterns</b> یعنی ردیابی استفاده غیرمعمول از حساب‌های کاربری در سراسر سیستم‌ها، به ویژه حساب‌هایی که معمولاً برای Lateral Movement استفاده نمی‌شوند.</p>
<p><b>Time-based Analysis</b> یعنی جستجو برای فعالیت‌ها در ساعات غیرکاری یا الگوهای زمانی غیرمعمول. <b>Process Parent-Child Relationships</b> یعنی ردیابی درخت فرآیندها برای شناسایی زنجیره‌های اجرای مشکوک. <b>Network Share Access Patterns</b> یعنی نظارت بر دسترسی به ADMIN$ و C$ که معمولاً برای Lateral Movement استفاده می‌شوند.</p>
<p>با ترکیب تمامی این Event IDs، Artifacts و تکنیک‌های تحلیل، تحلیلگران می‌توانند یک تصویر جامع از فعالیت‌های Lateral Movement در محیط خود به دست آورند و به سرعت تهدیدات را شناسایی و مهار کنند.</p>

</div>
