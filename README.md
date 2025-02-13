<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thiệp Valentine</title>
    <style>
        body {
            background-color: #434343;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Dancing Script', cursive;
            overflow: hidden;
        }

        .heart {
            position: absolute;
            color: white;
            animation: float 4s linear infinite;
            font-size: 20px;
        }

        @keyframes float {
            0% { transform: translateY(100%); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100%); opacity: 0; }
        }

        .card-container {
            position: relative;
            width: 300px;
            height: 200px;
        }

        .card {
            width: 100%;
            height: 100%;
            position: relative;
            perspective: 1000px;
        }

        .card-content {
            position: relative;
            width: 100%;
            height: 100%;
            background: #9d4583;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 10px;
            font-size: 20px;
            font-weight: bold;
            text-align: center;
            cursor: pointer;
        }

        .card-open {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            background: white;
            color: #9d4583;
            width: 320px;
            height: 220px;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
            text-align: center;
            transition: transform 0.5s;
            z-index: 10;
        }

        .card-open.show {
            transform: translate(-50%, -50%) scale(1);
        }

    </style>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap" rel="stylesheet">
</head>
<body>
    <div class="card-container">
        <div class="card" onclick="openCard()">
            <div class="card-content"> Anh ấn vào đây nha >< </div>
        </div>
        <div class="card-open" id="openedCard">
            <h2>💌 Happy Valentine! 💌</h2>
            <p>Em không ngưỡng mộ bạn trai của người khác,

                vì em biết rằng anh vẫn đang nỗ lực từng ngày.
            
                Em sẽ luôn bên cạnh anh nên anh đừng lo nha.

                                     Em thương anh 💕</p>

            <button onclick="closeCard()">Đóng</button>
        </div>
    </div>

    <script>
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.textContent = '🤍';
            heart.style.left = Math.random() * window.innerWidth + 'px';
            heart.style.bottom = '-50px';
            heart.style.fontSize = (Math.random() * 50 + 50) + 'px';

            document.body.appendChild(heart);

            setTimeout(() => heart.remove(), 4000);
        }

        setInterval(createHeart, 500);

        function openCard() {
            document.getElementById('openedCard').classList.add('show');
            document.getElementById('valentineAudio').play();
        }

        function closeCard() {
            document.getElementById('openedCard').classList.remove('show');
            document.getElementById('valentineAudio').pause();
            document.getElementById('valentineAudio').currentTime = 0;
        }
    </script>
</body>
</html>
