<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hope zhang - 个人作品集</title>
    <style>
        :root {
            --main-color: #4a4a4a;
            --accent-color: #3498db;
            --bg-color: #f9f9f9;
            --text-color: #333;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Open Sans', sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background: var(--bg-color);
        }

        /* Header 样式 */
        .header {
            padding: 3rem 5%;
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: relative;
        }

        .avatar-container {
            position: relative;
            width: 120px;
            height: 120px;
            cursor: pointer;
            transition: var(--transition);
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            transition: var(--transition);
            clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
        }

        .avatar:hover {
            transform: scale(1.1);
        }

        .avatar-name {
            display: none;
        }

        .identity {
            text-align: center;
            flex-grow: 1;
            padding: 0 3rem;
        }

        .identity p {
            font-size: 2.5rem;
            color: #333;
            font-weight: 700;
            letter-spacing: 2px;
            line-height: 1.4;
            background: linear-gradient(45deg, #333, #666);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
            position: relative;
            display: inline-block;
        }

        .identity p::before,
        .identity p::after {
            content: '';
            position: absolute;
            top: 50%;
            width: 40px;
            height: 2px;
            background: linear-gradient(90deg, transparent, #333, transparent);
        }

        .identity p::before {
            right: 100%;
            margin-right: 20px;
        }

        .identity p::after {
            left: 100%;
            margin-left: 20px;
        }

        .nav {
            display: flex;
            gap: 2.5rem;
        }

        .nav a {
            text-decoration: none;
            color: var(--main-color);
            font-weight: 500;
            transition: var(--transition);
            position: relative;
        }

        .nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--accent-color);
            transition: width 0.3s ease;
        }

        .nav a:hover::after {
            width: 100%;
        }

        /* 主体区域样式 */
        .main {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
        }

        .about {
            text-align: center;
            margin-bottom: 4rem;
            font-size: 1.2rem;
            color: #666;
        }

        /* 视频轮播样式 */
        .carousel {
            height: 500px;
            position: relative;
            perspective: 1000px;
            margin: 2rem auto;
            width: 90%;
            max-width: 1200px;
        }

        .carousel-container {
            position: relative;
            width: 100%;
            height: 100%;
            transform-style: preserve-3d;
            transition: transform 0.8s ease;
        }

        .video-item {
            position: absolute;
            width: 400px;
            height: 300px;
            left: 50%;
            top: 50%;
            transition: all 0.8s ease;
            transform-origin: center;
            cursor: pointer;
        }

        .video-container {
            width: 100%;
            height: 100%;
            overflow: hidden;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .video-container video {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Footer 样式 */
        .footer {
            background: white;
            padding: 3rem 5%;
            margin-top: 4rem;
            text-align: center;
        }

        .social-links {
            margin-bottom: 2rem;
        }

        .social-links a {
            color: var(--main-color);
            text-decoration: none;
            margin: 0 1rem;
            transition: var(--transition);
        }

        .social-links a:hover {
            color: var(--accent-color);
        }

        .contact-info {
            color: #666;
        }

        .contact-info p {
            margin: 0.5rem 0;
        }

        .contact-info .name {
            color: #666;
            margin-bottom: 1rem;
            font-size: 1rem;
            font-weight: normal;
        }

        /* 响应式设计 */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                gap: 1rem;
                padding: 1rem;
            }

            .nav {
                gap: 1rem;
            }

            .video-item {
                width: 300px;
                height: 225px;
            }
        }

        /* 添加轮播箭头样式 */
        .carousel-arrow {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            width: 50px;
            height: 50px;
            background-color: rgba(255, 255, 255, 0.8);
            border: none;
            border-radius: 50%;
            cursor: pointer;
            z-index: 10;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 6px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
        }

        .carousel-arrow:hover {
            background-color: white;
            transform: translateY(-50%) scale(1.1);
        }

        .carousel-arrow.prev {
            left: 20px;
        }

        .carousel-arrow.next {
            right: 20px;
        }

        .carousel-arrow::before {
            content: '';
            width: 12px;
            height: 12px;
            border-style: solid;
            border-width: 2px 2px 0 0;
            display: inline-block;
        }

        .carousel-arrow.prev::before {
            transform: rotate(-135deg);
        }

        .carousel-arrow.next::before {
            transform: rotate(45deg);
        }

        /* 添加平滑滚动效果的CSS */
        html {
            scroll-behavior: smooth;
        }
    </style>
</head>
<body>
    <header class="header">
        <div class="avatar-container">
            <img src="./pic/pic01.JPG" alt="Hope zhang" class="avatar">
        </div>
        <div class="identity">
            <p>发现美，创造美，留下美</p>
        </div>
        <nav class="nav">
            <a href="#about">关于我</a>
            <a href="#works">作品</a>
            <a href="#contact">联系方式</a>
        </nav>
    </header>

    <main class="main">
        <section id="about" class="about">
            <p>喜欢你的样子，喜欢世界的样子</p>
        </section>

        <section id="works" class="carousel">
            <button class="carousel-arrow prev" onclick="prevSlide()"></button>
            <div class="carousel-container">
                <!-- 视频项将通过JavaScript动态添加 -->
            </div>
            <button class="carousel-arrow next" onclick="nextSlide()"></button>
        </section>
    </main>

    <footer id="contact" class="footer">
        <div class="contact-info">
            <p class="name">Hope zhang</p>
            <p>电话: 18311072698</p>
            <p>邮箱: xiaolian-zhang@outlook.com</p>
        </div>
    </footer>

    <script>
        // 头像点击放大效果
        const avatar = document.querySelector('.avatar');
        let isEnlarged = false;

        avatar.addEventListener('click', () => {
            if (!isEnlarged) {
                avatar.style.position = 'fixed';
                avatar.style.top = '50%';
                avatar.style.left = '50%';
                avatar.style.transform = 'translate(-50%, -50%) scale(3)';
                avatar.style.zIndex = '1000';
                isEnlarged = true;
            } else {
                avatar.style.position = 'static';
                avatar.style.transform = 'none';
                avatar.style.zIndex = 'auto';
                isEnlarged = false;
            }
        });

        // 3D轮播实现
        const container = document.querySelector('.carousel-container');
        const videos = [
            './vedio/video1.mp4',
            './vedio/video2.mp4',
            './vedio/video3.mp4',
            './vedio/video4.mp4'
        ];

        let currentIndex = 0;

        // 创建视频元素
        videos.forEach((src, index) => {
            const videoItem = document.createElement('div');
            videoItem.className = 'video-item';
            
            const videoContainer = document.createElement('div');
            videoContainer.className = 'video-container';
            
            const video = document.createElement('video');
            video.controls = true;
            video.preload = 'metadata';
            
            const source = document.createElement('source');
            source.src = src;
            source.type = 'video/mp4';
            
            video.appendChild(source);
            videoContainer.appendChild(video);
            videoItem.appendChild(videoContainer);
            container.appendChild(videoItem);
        });

        const items = document.querySelectorAll('.video-item');

        function updateCarousel() {
            items.forEach((item, index) => {
                let offset = index - currentIndex;
                
                if (offset < -2) offset += items.length;
                if (offset > 2) offset -= items.length;
                
                if (offset === 0) {
                    item.style.transform = `
                        translate(-50%, -50%)
                        translateZ(200px)
                        scale(1.2)
                    `;
                    item.style.opacity = '1';
                    item.style.zIndex = '3';
                } else if (offset === -1) {
                    item.style.transform = `
                        translate(-50%, -50%)
                        translateX(-70%)
                        translateZ(100px)
                        rotateY(45deg)
                        scale(0.8)
                    `;
                    item.style.opacity = '0.7';
                    item.style.zIndex = '2';
                } else if (offset === 1) {
                    item.style.transform = `
                        translate(-50%, -50%)
                        translateX(70%)
                        translateZ(100px)
                        rotateY(-45deg)
                        scale(0.8)
                    `;
                    item.style.opacity = '0.7';
                    item.style.zIndex = '2';
                } else {
                    item.style.transform = `
                        translate(-50%, -50%)
                        translateX(${offset > 0 ? '150%' : '-150%'})
                        scale(0.5)
                    `;
                    item.style.opacity = '0';
                    item.style.zIndex = '1';
                }
            });
        }

        // 添加点击和触摸事件
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowLeft') {
                currentIndex = (currentIndex - 1 + items.length) % items.length;
                updateCarousel();
            } else if (e.key === 'ArrowRight') {
                currentIndex = (currentIndex + 1) % items.length;
                updateCarousel();
            }
        });

        let touchStartX = 0;
        document.addEventListener('touchstart', (e) => {
            touchStartX = e.touches[0].clientX;
        });

        document.addEventListener('touchend', (e) => {
            const touchEndX = e.changedTouches[0].clientX;
            const diff = touchStartX - touchEndX;
            
            if (Math.abs(diff) > 50) {
                if (diff > 0) {
                    currentIndex = (currentIndex + 1) % items.length;
                } else {
                    currentIndex = (currentIndex - 1 + items.length) % items.length;
                }
                updateCarousel();
            }
        });

        // 初始化轮播
        updateCarousel();

        function prevSlide() {
            currentIndex = (currentIndex - 1 + items.length) % items.length;
            updateCarousel();
            pauseAllVideos();
        }

        function nextSlide() {
            currentIndex = (currentIndex + 1) % items.length;
            updateCarousel();
            pauseAllVideos();
        }

        function pauseAllVideos() {
            items.forEach(item => {
                const video = item.querySelector('video');
                if (video) {
                    video.pause();
                }
            });
        }
    </script>
</body>
</html> 
