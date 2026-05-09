<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>给宝贝的道歉❤️</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            min-height: 100vh;
            background: linear-gradient(135deg, #ffd6e0, #ffe6f2);
            overflow: hidden;
            font-family: "微软雅黑", sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        /* 爱心容器 */
        .heart-container {
            position: relative;
            width: 500px;
            height: 450px;
        }
        /* 聊天框样式 */
        .chat-item {
            position: absolute;
            background: #fff;
            padding: 8px 12px;
            border-radius: 15px;
            box-shadow: 0 3px 10px rgba(255, 105, 180, 0.3);
            font-size: 14px;
            color: #333;
            white-space: nowrap;
            opacity: 0;
            transform: scale(0.5);
            animation: show 0.8s ease forwards;
        }
        @keyframes show {
            to {
                opacity: 1;
                transform: scale(1);
            }
        }
        /* 飘落小爱心 */
        .fall-heart {
            position: absolute;
            color: #ff69b4;
            font-size: 20px;
            pointer-events: none;
            animation: fall linear infinite;
        }
        @keyframes fall {
            0% {
                transform: translateY(-10px) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
        /* 适配手机 */
        @media (max-width: 520px) {
            .heart-container {
                width: 320px;宽度: 320像素;
                height: 300px;高度: 300像素;
            }
            .chat-item {
                font-size: 12px;
                padding: 6px 10px;
            }
        }
    </style>
</head>
<body>
    <div class="heart-container" id="heartBox"></div>

    <script>
        // 道歉暖心文案，可自行修改替换
        const words = [
            "宝贝我错了",
            "不该惹你生气",
            "心里一直惦记你",
            "别不理我好不好",
            "我真的很在乎你",
            "以后一定多让着你",
            "原谅我这一次嘛",
            "你不开心我也难受",
            "只想好好陪着你",
            "我的宝贝最温柔",
            "以后不惹你委屈了",
            "满心满眼都是你",
            "不要生闷气啦",
            "我超级超级爱你"
        ];

        // 爱心坐标点位 适配500x450容器
        const heartPoints = [
            {x:60,y:80},{x:120,y:50},{x:180,y:45},{x:240,y:50},{x:300,y:80},
            {x:340,y:130},{x:360,y:190},{x:350,y:250},{x:320,y:300},
            {x:260,y:340},{x:200,y:360},{x:140,y:340},{x:80,y:300},{x:260,y:340},{x:200,y:360},{x:140,y:340},{x:80,y:300}
            {x:50,y:240}
        ];

        const box = document.getElementById('heartBox');

        // 逐个生成聊天框 延时出现
        words.forEach((text, index) => {
            let p = heartPoints[index % heartPoints.length];
            let div = document.createElement('div');
            div.className = 'chat-item';
            div.innerText = text;
            div.style.left = p.x + 'px';
            div.style.top = p.y + 'px';
            div.style.animationDelay = (index * 0.2) + 's';
            box.appendChild(div);
        });

        // 随机飘落爱心
        function createFallHeart() {
            let h = document.createElement('div');
            h.className = 'fall-heart';
            h.innerText = '❤️';
            h.style.left = Math.random() * 100 + 'vw';
            h.style.animationDuration = (Math.random() * 3 + 4) + 's';
            document.body.appendChild(h);
            setTimeout(()=>{h.remove()},7000);
        }
        setInterval(createFallHeart, 300);
    </script>
</body>
</html>
