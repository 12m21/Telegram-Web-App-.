<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق الكسب من الإعلانات</title>
    
    <script src="https://telegram.org/js/telegram-web-app.js"></script>

    <style>
        /* تصميم CSS بسيط ومناسب لواجهة تيليجرام */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--tg-theme-bg-color, #f4f4f4); /* استخدام ألوان تيليجرام الثيمية */
            color: var(--tg-theme-text-color, #333);
            text-align: center;
            padding: 20px;
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
        }

        .container {
            width: 100%;
            max-width: 400px;
            padding: 20px;
            background-color: var(--tg-theme-secondary-bg-color, #ffffff);
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h1 {
            color: var(--tg-theme-text-color, #007bff);
            margin-bottom: 20px;
        }

        #adContainer {
            background-color: #e9ecef;
            border: 1px solid #ccc;
            height: 150px;
            line-height: 150px;
            margin: 20px 0;
            font-size: 1.2em;
            color: #6c757d;
            border-radius: 8px;
            animation: pulse 1.5s infinite; /* تأثير بسيط لجذب الانتباه */
        }
        
        @keyframes pulse {
            0% {box-shadow: 0 0 0 0 rgba(0, 123, 255, 0.4);}
            70% {box-shadow: 0 0 0 10px rgba(0, 123, 255, 0);}
            100% {box-shadow: 0 0 0 0 rgba(0, 123, 255, 0);}
        }

        button {
            background-color: var(--tg-theme-button-color, #007bff);
            color: var(--tg-theme-button-text-color, white);
            border: none;
            padding: 12px 25px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
            transition: background-color 0.3s;
            width: 100%;
            margin-top: 15px;
        }

        button:disabled {
            background-color: #6c757d;
            cursor: not-allowed;
        }

        #status {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>منطقة الكسب</h1>
        
        <div id="adContainer">
            مكان الإعلان (10 ثواني مشاهدة)
        </div>

        <p id="status">الرصيد الحالي: **0 نقطة**</p>

        <button id="adButton">ابدأ مشاهدة الإعلان</button>
        
        <p style="font-size: 0.8em; color: #888; margin-top: 20px;">
            ملاحظة: تحتاج إلى ربط هذه الواجهة ببرمجة البوت (بايثون) لتسجيل النقاط فعلياً.
        </p>
    </div>

    <script>
        // المتغيرات
        let currentScore = 0;
        const button = document.getElementById('adButton');
        const statusText = document.getElementById('status');
        const adDuration = 10; // مدة الإعلان بالثواني

        // تهيئة تطبيق الويب الخاص بتيليجرام
        const tg = window.Telegram.WebApp;
        tg.ready();
        
        // إخفاء الزر الرئيسي لتليجرام لتركيز المستخدم على الواجهة
        tg.MainButton.hide();

        // دالة التعامل مع النقر على الزر
        button.addEventListener('click', function() {
            // التحقق من حالة الزر لمنع الضغط المتعدد
            if (button.disabled) return;

            // بدء عملية المشاهدة
            button.disabled = true;
            let timer = adDuration;
            button.textContent = `جاري المشاهدة... (${timer} ثانية)`;
            
            // تحديث المؤقت
            const interval = setInterval(() => {
                timer--;
                button.textContent = `جاري المشاهدة... (${timer} ثانية)`;
                
                if (timer <= 0) {
                    clearInterval(interval);
                    
                    // نهاية المشاهدة: إضافة النقاط
                    const points = 5; 
                    currentScore += points;
                    
                    statusText.innerHTML = `الرصيد الحالي: <strong>${currentScore} نقطة</strong>.`;
                    
                    button.textContent = 'شاهد الإعلان التالي';
                    button.disabled = false;

                    // **********************************************
                    // الخطوة الأهم: إرسال البيانات إلى البوت الخلفي (Python)
                    // **********************************************
                    
                    try {
                        // إرسال البيانات التي تحتاج إلى تسجيلها في قاعدة البيانات
                        tg.sendData(`action=view_ad&points=${points}&user_id=${tg.initDataUnsafe.user.id}`);
                        
                        // إظهار رسالة قصيرة للمستخدم (اختياري)
                        if (tg.showPopup) {
                             tg.showPopup({
                                 message: `تم إضافة ${points} نقطة بنجاح!`
                             });
                        }

                    } catch (e) {
                         // في حال عدم التشغيل داخل بيئة تيليجرام
                         console.error("خطأ: تعذر إرسال البيانات إلى البوت، هل أنت في بيئة تيليجرام؟", e);
                         statusText.style.color = 'red';
                         statusText.textContent += ' (خطأ في الاتصال بالبوت)';
                    }
                }
            }, 1000);
        });

        // تحسين تجربة المستخدم: إظهار الرصيد الأولي من البوت عند الفتح
        window.onload = function() {
             // عند فتح التطبيق، نطلب من البوت إرسال الرصيد الأولي 
             // (هذه الوظيفة تحتاج إلى برمجة في جانب بايثون)
             // tg.sendData('action=request_initial_score');
             
             // استخدام اسم المستخدم في الزاوية
             if (tg.initDataUnsafe && tg.initDataUnsafe.user) {
                 const name = tg.initDataUnsafe.user.first_name || "عزيزي المستخدم";
                 document.querySelector('h1').textContent = `أهلاً بك يا ${name}!`;
             }
        };

    </script>
</body>
</html>
