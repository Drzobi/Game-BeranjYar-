<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بازی شالیزار برنج یار</title>
    <!-- اتصال به کتابخانه رسمی مینی‌اپ تلگرام -->
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: 'Tahoma', sans-serif;
            background: linear-gradient(180deg, #e8f5e9 0%, #c8e6c9 100%);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            height: 90vh;
            user-select: none;
            -webkit-user-select: none;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            padding: 15px 30px;
            border-radius: 20px;
            box-shadow: 0 6px 15px rgba(0,0,0,0.08);
            text-align: center;
            width: 80%;
            border: 2px solid #a5d6a7;
        }

        .coin-label {
            font-size: 13px;
            color: #555;
            margin-bottom: 5px;
        }

        .balance {
            font-size: 28px;
            font-weight: bold;
            color: #2e7d32;
        }

        .click-zone {
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            width: 100%;
        }

        .rice-btn {
            font-size: 130px;
            cursor: pointer;
            transition: transform 0.08s ease;
            filter: drop-shadow(0 12px 20px rgba(0,0,0,0.15));
        }

        .rice-btn:active {
            transform: scale(0.88);
        }

        .footer {
            text-align: center;
            color: #1b5e20;
            font-size: 15px;
            font-weight: bold;
            background: rgba(255,255,255,0.6);
            padding: 10px 20px;
            border-radius: 15px;
        }

        .floating-number {
            position: absolute;
            font-size: 32px;
            font-weight: bold;
            color: #fbc02d;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
            animation: floatUp 0.8s ease-out forwards;
            pointer-events: none;
        }

        @keyframes floatUp {
            0% { opacity: 1; transform: translateY(0); }
            100% { opacity: 0; transform: translateY(-90px); }
        }
    </style>
</head>
<body>

    <div class="header">
        <div class="coin-label">موجودی برنج یار کوین (BYC)</div>
        <div class="balance" id="coinCount">0 BYC</div>
    </div>

    <div class="click-zone">
        <div class="rice-btn" id="riceBtn">🌾</div>
    </div>

    <div class="footer">
        روی شالیزار لمس کن و برنج یار کوین جمع کن!
    </div>

    <script>
        // آماده‌سازی مینی‌اپ تلگرام
        const tg = window.Telegram.WebApp;
        tg.expand(); // باز کردن صفحه به‌صورت تمام‌صفحه در تلگرام

        let coins = 0;
        const coinDisplay = document.getElementById('coinCount');
        const riceBtn = document.getElementById('riceBtn');

        riceBtn.addEventListener('click', (e) => {
            coins += 1;
            coinDisplay.textContent = coins + " BYC";

            // ایجاد انیمیشن متحرک +1
            const floatingText = document.createElement('div');
            floatingText.className = 'floating-number';
            floatingText.textContent = '+1';
            floatingText.style.left = (e.clientX - 15) + 'px';
            floatingText.style.top = (e.clientY - 40) + 'px';
            document.body.appendChild(floatingText);

            setTimeout(() => {
                floatingText.remove();
            }, 800);
        });
    </script>
</body>
</html>