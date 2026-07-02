# WebScoketRepo

YouTube URL:
https://youtu.be/cTTS_D3m1nU




🪙 Crypto Order Book — شرح المشروع
شو هو المشروع؟
موقع يعرض سجل الطلبات الحي للعملات الرقمية، زي شاشة Binance الحقيقية — الأسعار تتحدث كل 100ms بدون ما تعيد تحميل الصفحة.

⚙️ التقنيات المستخدمة
Backend:

ASP.NET Core MVC على .NET 10
WebSocket ثنائي الاتجاه — السيرفر يتصل بـ Binance ويمرر البيانات للمتصفح مباشرة
IAsyncEnumerable + Channel — لتمرير البيانات بشكل stream داخلي آمن
Binance WebSocket API — مجاني وبيانات حقيقية 100%

Frontend:

Vanilla JavaScript مع WebSocket API
واجهة مستوحاة من Binance الحقيقي
تحديث الأسعار كل 100ms بدون reload


🏗️ هيكل المشروع
المتصفح  ←─ WebSocket ─→  Controller  ←─ IAsyncEnumerable ─→  BinanceService  ←─ WebSocket ─→  Binance API

✨ المميزات
Order Book:

جدول Bids باللون الأخضر وAsks باللون الأحمر
شريط حجم مرئي لكل سطر يوضح قوة الطلب
أفضل 15 سعر بيع و15 سعر شراء

إحصائيات Live:

Last Price, Best Bid, Best Ask
Spread (الفرق بين أفضل بيع وشراء)
Spread %
وقت آخر تحديث

تبديل العملات:

BTC/USDT, ETH/USDT, BNB/USDT, SOL/USDT
بضغطة زر واحدة بدون reload

Reconnect تلقائي:

إذا انقطع الاتصال يعيد الاتصال بعد 3 ثواني تلقائياً


🧠 الميزة الذكية — Arbitrage Detection
النظام يراقب الـ Spread باستمرار ويحسب متوسطه على آخر 50 قراءة.
إذا الـ Spread الحالي تجاوز 1.5x المتوسط وكان أكبر من 0.05% — يطلع تنبيه أصفر:
⚡ Wide spread: 0.0821% vs avg 0.0312% - possible opportunity
يعني في فرق كبير بين سعر الشراء والبيع، وهاد ممكن يكون فرصة للمتداولين.
