<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apple Service Pro - Ремонт техники Apple</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @property --gradient-angle {
            syntax: '<angle>';
            initial-value: 0deg;
            inherits: false;
        }

        @property --mouse-x {
            syntax: '<percentage>';
            initial-value: 0%;
            inherits: false;
        }

        @property --mouse-y {
            syntax: '<percentage>';
            initial-value: 0%;
            inherits: false;
        }

        :root {
            --primary-color: #ffffff;
            --secondary-color: #000000;
            --accent-color: #007AFF;
            --text-color: #1D1D1F;
            --gray-color: #86868B;
            --transition-time: 0.6s;
            --card-bg: #F5F5F7;
            --header-height: 80px;
            --ease-out-quint: cubic-bezier(0.22, 1, 0.36, 1);
            --ease-in-out-back: cubic-bezier(0.68, -0.6, 0.32, 1.6);
        }

        .dark-theme {
            --primary-color: #000000;
            --secondary-color: #ffffff;
            --accent-color: #0A84FF;
            --text-color: #F5F5F7;
            --gray-color: #86868B;
            --card-bg: #1D1D1F;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background-color: var(--primary-color);
            color: var(--text-color);
            min-height: 100vh;
            line-height: 1.6;
            padding-top: var(--header-height);
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
        }

        /* Header Styles */
        .header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
            border-bottom: 1px solid var(--gray-color);
            background-color: var(--primary-color);
            z-index: 1000;
            transition: all 0.4s var(--ease-out-quint);
            transform: translateY(0);
            height: var(--header-height);
            backdrop-filter: blur(20px);
            background-color: rgba(255, 255, 255, 0.85);
        }

        .dark-theme .header {
            background-color: rgba(0, 0, 0, 0.85);
        }

        .header.hidden {
            transform: translateY(-100%);
        }

        .header.scrolled {
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.12);
            border-bottom: 1px solid transparent;
            backdrop-filter: blur(30px);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-color);
            position: relative;
        }

        .logo::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--accent-color), #5856D6);
            transition: width 0.6s var(--ease-out-quint);
        }

        .logo:hover::after {
            width: 100%;
        }

        .logo i {
            color: var(--accent-color);
            transition: transform 0.6s var(--ease-in-out-back);
        }

        .logo:hover i {
            transform: scale(1.2) rotate(15deg);
        }

        .nav-buttons {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .theme-toggle, .contact-btn {
            background: transparent;
            border: 2px solid var(--accent-color);
            padding: 10px 20px;
            border-radius: 25px;
            color: var(--accent-color);
            cursor: pointer;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.4s var(--ease-out-quint);
            position: relative;
            overflow: hidden;
        }

        .theme-toggle::before, .contact-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.6s;
        }

        .theme-toggle:hover::before, .contact-btn:hover::before {
            left: 100%;
        }

        .theme-toggle:focus,
        .contact-btn:focus,
        .service-button:focus,
        .scroll-to-top:focus {
            outline: 2px solid var(--accent-color);
            outline-offset: 2px;
        }

        .contact-btn {
            background: var(--accent-color);
            color: white;
        }

        .theme-toggle:hover, .contact-btn:hover {
            transform: translateY(-2px) scale(1.05);
            box-shadow: 0 8px 25px rgba(0, 122, 255, 0.3);
        }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 6rem 0 4rem;
            margin-bottom: 3rem;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: radial-gradient(circle at var(--mouse-x) var(--mouse-y), 
                        rgba(0, 122, 255, 0.03) 0%, 
                        transparent 50%);
            pointer-events: none;
            transition: background 0.1s;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 800;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--accent-color), #5856D6, #BF5AF2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 200% 200%;
            animation: gradientShift 8s ease infinite;
            line-height: 1.1;
        }

        .hero p {
            font-size: 1.3rem;
            color: var(--gray-color);
            max-width: 700px;
            margin: 0 auto 2rem;
            animation: fadeInUp 1s var(--ease-out-quint) 0.3s both;
        }

        .features {
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
            margin-top: 2rem;
        }

        .feature {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.1rem;
            padding: 1rem 1.5rem;
            background: var(--card-bg);
            border-radius: 15px;
            transition: all 0.4s var(--ease-out-quint);
            animation: fadeInUp 1s var(--ease-out-quint) 0.6s both;
        }

        .feature:nth-child(2) {
            animation-delay: 0.8s;
        }

        .feature:nth-child(3) {
            animation-delay: 1s;
        }

        .feature:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .feature i {
            color: var(--accent-color);
            font-size: 1.3rem;
        }

        /* Services Grid */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .service-card {
            background: var(--card-bg);
            border-radius: 24px;
            overflow: hidden;
            box-shadow: 0 4px 20px rgba(0,0,0,0.08);
            transform: translateY(0);
            transition: all 0.6s var(--ease-out-quint);
            position: relative;
            border: 1px solid rgba(0,0,0,0.05);
            opacity: 0;
            animation: cardEntrance 0.8s var(--ease-out-quint) forwards;
        }

        .service-card:nth-child(1) { animation-delay: 0.1s; }
        .service-card:nth-child(2) { animation-delay: 0.2s; }
        .service-card:nth-child(3) { animation-delay: 0.3s; }
        .service-card:nth-child(4) { animation-delay: 0.4s; }
        .service-card:nth-child(5) { animation-delay: 0.5s; }
        .service-card:nth-child(6) { animation-delay: 0.6s; }

        .service-card::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 24px;
            padding: 2px;
            background: conic-gradient(from var(--gradient-angle), 
                          var(--accent-color), #5856D6, #BF5AF2, var(--accent-color));
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            opacity: 0;
            transition: opacity 0.6s var(--ease-out-quint);
        }

        .service-card:hover {
            transform: translateY(-12px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
        }

        .service-card:hover::before {
            opacity: 1;
            animation: gradientRotate 3s linear infinite;
        }

        .service-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
            display: block;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            transition: transform 0.6s var(--ease-out-quint);
        }

        .service-card:hover .service-image {
            transform: scale(1.05);
        }

        .service-info {
            padding: 2rem;
            position: relative;
        }

        .service-name {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--text-color);
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .service-name i {
            color: var(--accent-color);
            transition: transform 0.4s var(--ease-out-quint);
        }

        .service-card:hover .service-name i {
            transform: scale(1.2) rotate(10deg);
        }

        .service-description {
            color: var(--gray-color);
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }

        .service-price {
            font-size: 1.4rem;
            font-weight: 800;
            color: var(--accent-color);
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .service-features {
            list-style: none;
            margin-bottom: 2rem;
        }

        .service-features li {
            margin-bottom: 0.6rem;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: transform 0.3s var(--ease-out-quint);
        }

        .service-features li:hover {
            transform: translateX(8px);
        }

        .service-features i {
            color: #34C759;
            font-size: 1rem;
        }

        .service-button {
            width: 100%;
            padding: 14px;
            background: var(--accent-color);
            color: white;
            border: none;
            border-radius: 14px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            transition: all 0.4s var(--ease-out-quint);
            position: relative;
            overflow: hidden;
        }

        .service-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.6s;
        }

        .service-button:hover::before {
            left: 100%;
        }

        .service-button:hover {
            background: #0056CC;
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 10px 25px rgba(0, 122, 255, 0.4);
        }

        /* Portfolio Section */
        .portfolio {
            margin-top: 6rem;
            padding: 4rem 0;
            position: relative;
        }

        .portfolio::before {
            content: '';
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, var(--accent-color), #5856D6);
            border-radius: 2px;
        }

        .portfolio h2 {
            text-align: center;
            font-size: clamp(2rem, 4vw, 3rem);
            margin-bottom: 4rem;
            color: var(--text-color);
            opacity: 0;
            animation: fadeInUp 1s var(--ease-out-quint) 0.2s both;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
        }

        .portfolio-item {
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 8px 30px rgba(0,0,0,0.12);
            transition: all 0.6s var(--ease-out-quint);
            background: var(--card-bg);
            border: 1px solid rgba(0,0,0,0.05);
            opacity: 0;
            animation: cardEntrance 0.8s var(--ease-out-quint) forwards;
            animation-delay: calc(var(--item-index) * 0.1s);
        }

        .portfolio-item:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }

        .portfolio-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            display: block;
            transition: transform 0.8s var(--ease-out-quint);
        }

        .portfolio-item:hover .portfolio-image {
            transform: scale(1.1);
        }

        .portfolio-info {
            padding: 2rem;
            position: relative;
        }

        .portfolio-title {
            font-size: 1.4rem;
            margin-bottom: 1rem;
            color: var(--text-color);
            transition: color 0.3s var(--ease-out-quint);
        }

        .portfolio-item:hover .portfolio-title {
            color: var(--accent-color);
        }

        .portfolio-description {
            color: var(--gray-color);
            font-size: 1rem;
            line-height: 1.6;
        }

        /* Loading States */
        .loading {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 200px;
            font-size: 1.2rem;
            color: var(--gray-color);
        }

        .spinner {
            width: 50px;
            height: 50px;
            border: 3px solid transparent;
            border-top: 3px solid var(--accent-color);
            border-right: 3px solid var(--accent-color);
            border-radius: 50%;
            animation: spin 1s linear infinite, colors 3s ease-in-out infinite;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            backdrop-filter: blur(10px);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            animation: modalEnter 0.4s var(--ease-out-quint);
        }

        .modal-content {
            background: var(--primary-color);
            padding: 3rem;
            border-radius: 24px;
            max-width: 500px;
            width: 90%;
            box-shadow: 0 30px 80px rgba(0,0,0,0.4);
            transform: scale(0.9);
            animation: modalContentEnter 0.4s var(--ease-out-quint) forwards;
            position: relative;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 1.8rem;
            cursor: pointer;
            color: var(--text-color);
            transition: all 0.3s var(--ease-out-quint);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .modal-close:hover {
            background: var(--card-bg);
            transform: rotate(90deg);
        }

        /* Scroll to top button */
        .scroll-to-top {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            width: 60px;
            height: 60px;
            background: var(--accent-color);
            color: white;
            border: none;
            border-radius: 50%;
            cursor: pointer;
            display: none;
            align-items: center;
            justify-content: center;
            font-size: 1.4rem;
            z-index: 999;
            transition: all 0.4s var(--ease-out-quint);
            box-shadow: 0 8px 30px rgba(0, 122, 255, 0.4);
            backdrop-filter: blur(10px);
        }

        .scroll-to-top:hover {
            transform: translateY(-5px) scale(1.1);
            box-shadow: 0 15px 40px rgba(0, 122, 255, 0.6);
        }

        .scroll-to-top.visible {
            display: flex;
            animation: bounceIn 0.6s var(--ease-out-quint);
        }

        /* Footer */
        .footer {
            margin-top: 8rem;
            padding: 4rem 0;
            border-top: 1px solid var(--gray-color);
            text-align: center;
            color: var(--gray-color);
            position: relative;
            overflow: hidden;
        }

        .footer::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 1px;
            background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 3rem;
            flex-wrap: wrap;
            margin: 2.5rem 0;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 1rem 1.5rem;
            background: var(--card-bg);
            border-radius: 15px;
            transition: all 0.4s var(--ease-out-quint);
        }

        .contact-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        /* Advanced Animations */
        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        @keyframes gradientRotate {
            0% { --gradient-angle: 0deg; }
            100% { --gradient-angle: 360deg; }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes cardEntrance {
            from {
                opacity: 0;
                transform: translateY(60px) scale(0.9);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes colors {
            0%, 100% { border-top-color: var(--accent-color); border-right-color: var(--accent-color); }
            25% { border-top-color: #5856D6; border-right-color: #5856D6; }
            50% { border-top-color: #FF2D55; border-right-color: #FF2D55; }
            75% { border-top-color: #34C759; border-right-color: #34C759; }
        }

        @keyframes modalEnter {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes modalContentEnter {
            to { transform: scale(1); }
        }

        @keyframes bounceIn {
            0% { transform: scale(0.3); opacity: 0; }
            50% { transform: scale(1.05); }
            70% { transform: scale(0.9); }
            100% { transform: scale(1); opacity: 1; }
        }

        /* Magnetic button effect */
        .magnetic {
            transition: transform 0.3s var(--ease-out-quint);
        }

        /* Scroll progress indicator */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            width: 0%;
            height: 3px;
            background: linear-gradient(90deg, var(--accent-color), #5856D6);
            z-index: 1001;
            transition: width 0.1s;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            :root {
                --header-height: 70px;
            }

            .container {
                padding: 1rem;
            }
            
            .header {
                padding: 0.8rem 1rem;
            }
            
            .hero {
                padding: 4rem 0 2rem;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
            
            .portfolio-grid {
                grid-template-columns: 1fr;
            }
            
            .features {
                flex-direction: column;
                align-items: center;
            }
            
            .contact-info {
                flex-direction: column;
                gap: 1rem;
            }

            .nav-buttons {
                gap: 0.5rem;
            }

            .theme-toggle, .contact-btn {
                padding: 8px 16px;
                font-size: 0.9rem;
            }

            .scroll-to-top {
                bottom: 1rem;
                right: 1rem;
                width: 50px;
                height: 50px;
            }

            .service-card:hover {
                transform: translateY(-5px) scale(1.01);
            }
        }

        /* Reduced motion support */
        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }
        }
    </style>
</head>
<body>
    <div class="scroll-progress" id="scrollProgress"></div>
    
    <header class="header" id="mainHeader">
        <div class="logo">
            <i class="fab fa-apple"></i>
            <span>Apple Service Pro</span>
        </div>
        <div class="nav-buttons">
            <button class="theme-toggle magnetic" id="themeToggle">
                <i class="fas fa-moon"></i>
                Тёмная тема
            </button>
            <button class="contact-btn magnetic" id="contactBtn">
                <i class="fas fa-phone"></i>
                Связаться
            </button>
        </div>
    </header>
    
    <div class="container">
        <section class="hero" id="hero">
            <h1>Профессиональный ремонт техники Apple</h1>
            <p>Официальный сервисный центр с оригинальными запчастями и гарантией до 2 лет. Вернём ваше устройство к жизни в кратчайшие сроки!</p>
            
            <div class="features">
                <div class="feature">
                    <i class="fas fa-check-circle"></i>
                    <span>Оригинальные запчасти</span>
                </div>
                <div class="feature">
                    <i class="fas fa-check-circle"></i>
                    <span>Гарантия до 2 лет</span>
                </div>
                <div class="feature">
                    <i class="fas fa-check-circle"></i>
                    <span>Бесплатная диагностика</span>
                </div>
            </div>
        </section>
        
        <main>
            <div class="services-grid" id="servicesGrid">
                <div class="loading">
                    <div class="spinner"></div>
                    Загружаем услуги...
                </div>
            </div>
        </main>

        <!-- Раздел с примерами работ -->
        <section class="portfolio" id="portfolio">
            <h2>Примеры наших работ</h2>
            <div class="portfolio-grid" id="portfolioGrid">
                <!-- Portfolio items will be generated by JavaScript -->
            </div>
        </section>
        
        <footer class="footer">
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <span>Пн-Вс: 9:00-21:00</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>+7 (495) 123-45-67</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>Москва, ул. Тверская, 15</span>
                </div>
            </div>
            <p>© 2025 Apple Service Pro. Мы не являемся официальным представителем Apple Inc.</p>
        </footer>
    </div>

    <!-- Кнопка прокрутки наверх -->
    <button class="scroll-to-top" id="scrollToTop">
        <i class="fas fa-chevron-up"></i>
    </button>

    <!-- Modal -->
    <div class="modal" id="contactModal" role="dialog" aria-labelledby="modalTitle" aria-hidden="true">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modalTitle">Связаться с нами</h3>
                <button class="modal-close" id="modalClose">&times;</button>
            </div>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>+7 (495) 123-45-67</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>Москва, ул. Тверская, 15</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <span>Пн-Вс: 9:00-21:00</span>
                </div>
            </div>
        </div>
    </div>

    <script type="module">
        // Константы и данные
        const APPLE_SERVICES = Object.freeze([
            {
                id: 1,
                name: "Ремонт iPhone",
                icon: "fas fa-mobile-alt",
                description: "Полный спектр услуг по ремонту iPhone любой модели. Замена экрана, аккумулятора, камеры и других компонентов.",
                price: "от 1 990 ₽",
                features: ["Диагностика бесплатно", "Оригинальные дисплеи", "Гарантия 1 год", "Ремонт за 30 минут"],
                color: "linear-gradient(135deg, #007AFF, #5856D6)"
            },
            {
                id: 2,
                name: "Ремонт MacBook",
                icon: "fas fa-laptop",
                description: "Профессиональный ремонт MacBook всех поколений. Чистка, замена клавиатуры, матрицы и ремонт материнской платы.",
                price: "от 3 990 ₽",
                features: ["Бесплатная диагностика", "Оригинальные запчасти", "Срочный ремонт", "Гарантия 2 года"],
                color: "linear-gradient(135deg, #34C759, #30D158)"
            },
            {
                id: 3,
                name: "Ремонт iPad",
                icon: "fas fa-tablet-alt",
                description: "Качественный ремонт iPad и iPad Pro. Восстановление экрана, замена батареи, ремонт после попадания влаги.",
                price: "от 2 490 ₽",
                features: ["Оригинальные стекла", "Сохранение данных", "Ремонт за 1 день", "Гарантия 1 год"],
                color: "linear-gradient(135deg, #FF2D55, #FF375F)"
            },
            {
                id: 4,
                name: "Ремонт Apple Watch",
                icon: "fas fa-clock",
                description: "Ремонт умных часов Apple Watch. Замена стекла, дисплея, корпуса и аккумулятора.",
                price: "от 1 790 ₽",
                features: ["Оригинальные детали", "Герметизация", "Ремонт за 2 часа", "Гарантия 6 месяцев"],
                color: "linear-gradient(135deg, #FF9500, #FF9F0A)"
            },
            {
                id: 5,
                name: "Ремонт AirPods",
                icon: "fas fa-headphones",
                description: "Восстановление работы AirPods. Замена аккумуляторов, ремонт кейсов, чистка динамиков.",
                price: "от 990 ₽",
                features: ["Оригинальные батареи", "Чистка ультразвуком", "Ремонт за 1 час", "Гарантия 3 месяца"],
                color: "linear-gradient(135deg, #BF5AF2, #BF5AF2)"
            },
            {
                id: 6,
                name: "Восстановление данных",
                icon: "fas fa-hdd",
                description: "Срочное восстановление данных с любых устройств Apple после сбоев, падений и попадания жидкости.",
                price: "от 2 990 ₽",
                features: ["Бесплатный анализ", "Высокая вероятность", "Конфиденциальность", "Срочное выполнение"],
                color: "linear-gradient(135deg, #32D74B, #30D158)"
            }
        ]);

        const PORTFOLIO_ITEMS = Object.freeze([
            {
                id: 1,
                title: "Замена дисплея iPhone 12 Pro",
                description: "Полная замена OLED-дисплея с сохранением оригинального True Tone. Устройство работает как новое!",
                image: "https://images.unsplash.com/photo-1605236453806-6ff36851218e?w=600&h=400&fit=crop",
                category: "iPhone"
            },
            {
                id: 2,
                title: "Чистка и замена термопасты MacBook Pro",
                description: "Профилактическая чистка системы охлаждения и замена термоинтерфейса. Устранены перегревы.",
                image: "https://images.unsplash.com/photo-1541807084-5c52b6b3adef?w=600&h=400&fit=crop",
                category: "MacBook"
            },
            {
                id: 3,
                title: "Восстановление iPad Air после падения",
                description: "Замена стекла и дигитайзера с калибровкой сенсорного слоя. Экран снова идеально откликается.",
                image: "https://images.unsplash.com/photo-1544244015-0df4b3ffc6b0?w=600&h=400&fit=crop",
                category: "iPad"
            },
            {
                id: 4,
                title: "Ремонт Apple Watch Series 6",
                description: "Замена аккумулятора и герметизация корпуса для сохранения водонепроницаемости.",
                image: "https://images.unsplash.com/photo-1551816230-ef5deaed4a26?w=600&h=400&fit=crop",
                category: "Apple Watch"
            },
            {
                id: 5,
                title: "Замена клавиатуры MacBook Pro",
                description: "Установка новой клавиатуры с полной калибровкой и тестированием всех клавиш.",
                image: "https://images.unsplash.com/photo-1496181133206-80ce9b88a853?w=600&h=400&fit=crop",
                category: "MacBook"
            },
            {
                id: 6,
                title: "Восстановление данных с поврежденного iPhone",
                description: "Спасение важной информации после серьезного повреждения устройства водой.",
                image: "https://images.unsplash.com/photo-1558494949-ef010cbdcc31?w=600&h=400&fit=crop",
                category: "Восстановление данных"
            },
            {
                id: 7,
                title: "Ремонт материнской платы MacBook",
                description: "Комплексный ремонт материнской платы с заменой компонентов BGA-пайки.",
                image: "https://images.unsplash.com/photo-1593640408182-31c70c8268f5?w=600&h=400&fit=crop",
                category: "MacBook"
            },
            {
                id: 8,
                title: "Замена корпуса iPhone 13",
                description: "Полная замена корпуса с сохранением всех оригинальных компонентов.",
                image: "https://images.unsplash.com/photo-1592750475338-74b7b21085ab?w=600&h=400&fit=crop",
                category: "iPhone"
            }
        ]);

        // Утилиты
        const createElement = (tag, classes = [], attributes = {}) => {
            const element = document.createElement(tag);
            if (classes.length) element.classList.add(...classes);
            Object.entries(attributes).forEach(([key, value]) => {
                element.setAttribute(key, value);
            });
            return element;
        };

        const animateOnScroll = (elements, options = {}) => {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.animationPlayState = 'running';
                    }
                });
            }, {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px',
                ...options
            });

            elements.forEach(element => {
                element.style.animationPlayState = 'paused';
                observer.observe(element);
            });
        };

        const debounce = (func, wait) => {
            let timeout;
            return (...args) => {
                clearTimeout(timeout);
                timeout = setTimeout(() => func.apply(this, args), wait);
            };
        };

        // Класс приложения
        class AppleServiceApp {
            #servicesGrid;
            #portfolioGrid;
            #themeToggle;
            #contactBtn;
            #contactModal;
            #modalClose;
            #scrollToTop;
            #mainHeader;
            #scrollProgress;
            #hero;
            #isDarkTheme = false;
            #lastScrollY = 0;
            #isScrolling = false;

            constructor() {
                this.#initializeElements();
                this.#init();
                this.loadTheme();
            }

            #initializeElements() {
                this.#servicesGrid = document.getElementById('servicesGrid');
                this.#portfolioGrid = document.getElementById('portfolioGrid');
                this.#themeToggle = document.getElementById('themeToggle');
                this.#contactBtn = document.getElementById('contactBtn');
                this.#contactModal = document.getElementById('contactModal');
                this.#modalClose = document.getElementById('modalClose');
                this.#scrollToTop = document.getElementById('scrollToTop');
                this.#mainHeader = document.getElementById('mainHeader');
                this.#scrollProgress = document.getElementById('scrollProgress');
                this.#hero = document.getElementById('hero');
            }

            #init() {
                this.#loadServices();
                this.#loadPortfolio();
                this.#setupEventListeners();
                this.#setupScrollAnimations();
                this.#setupImageLoading();
                this.#setupScrollHandler();
                this.#setupMagneticButtons();
                this.#setupMouseTracking();
            }

            async #loadServices() {
                await this.#simulateLoading(1500);
                this.#renderServices();
            }

            async #loadPortfolio() {
                await this.#simulateLoading(1000);
                this.#renderPortfolio();
            }

            #simulateLoading(delay) {
                return new Promise(resolve => setTimeout(resolve, delay));
            }

            #renderServices() {
                this.#servicesGrid.innerHTML = '';
                
                const serviceCards = APPLE_SERVICES.map(service => 
                    this.#createServiceCard(service)
                );
                
                this.#servicesGrid.append(...serviceCards);
                this.#addServiceEventListeners();
            }

            #createServiceCard(service) {
                const card = createElement('div', ['service-card']);
                
                card.innerHTML = `
                    <div class="service-image" style="background: ${service.color}; display: flex; justify-content: center; align-items: center; color: white; font-size: 3rem;">
                        <i class="${service.icon}"></i>
                    </div>
                    <div class="service-info">
                        <h3 class="service-name">
                            <i class="${service.icon}"></i>
                            ${service.name}
                        </h3>
                        <p class="service-description">${service.description}</p>
                        <div class="service-price">${service.price}</div>
                        <ul class="service-features">
                            ${service.features.map(feature => `
                                <li><i class="fas fa-check"></i>${feature}</li>
                            `).join('')}
                        </ul>
                        <button class="service-button magnetic" data-service="${service.name}">
                            <i class="fas fa-tools"></i>
                            Заказать ремонт
                        </button>
                    </div>
                `;
                
                return card;
            }

            #renderPortfolio() {
                const portfolioItems = PORTFOLIO_ITEMS.map((item, index) => 
                    this.#createPortfolioItem(item, index)
                );
                
                this.#portfolioGrid.append(...portfolioItems);
            }

            #createPortfolioItem(item, index) {
                const portfolioItem = createElement('div', ['portfolio-item']);
                portfolioItem.style.setProperty('--item-index', index);
                
                portfolioItem.innerHTML = `
                    <img class="portfolio-image" 
                         src="${item.image}" 
                         alt="${item.title}"
                         loading="lazy"
                         onerror="this.src='data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSI2MDAiIGhlaWdodD0iNDAwIiBmaWxsPSIjRjVGNUY3Ii8+CjxwYXRoIGQ9Ik0zMDAgMjAwTDM1MCAyNTBMMzAwIDMwMEwyNTAgMjUwTDMwMCAyMDBaIiBmaWxsPSIjMDA3QUZGIi8+Cjx0ZXh0IHg9IjMwMCIgeT0iMzUwIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTgiIGZpbGw9IiM4Njg2OEIiPk5vIGltYWdlPC90ZXh0Pgo8L3N2Zz4K'">
                    <div class="portfolio-info">
                        <h3 class="portfolio-title">${item.title}</h3>
                        <p class="portfolio-description">${item.description}</p>
                        <div style="margin-top: 0.5rem; font-size: 0.9rem; color: var(--accent-color);">
                            <i class="fas fa-tag"></i> ${item.category}
                        </div>
                    </div>
                `;
                
                return portfolioItem;
            }

            #setupImageLoading() {
                document.addEventListener('error', (e) => {
                    if (e.target.tagName === 'IMG' && e.target.classList.contains('portfolio-image')) {
                        e.target.src = 'data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSI2MDAiIGhlaWdodD0iNDAwIiBmaWxsPSIjRjVGNUY3Ii8+CjxwYXRoIGQ9Ik0zMDAgMjAwTDM1MCAyNTBMMzAwIDMwMEwyNTAgMjUwTDMwMCAyMDBaIiBmaWxsPSIjMDA3QUZGIi8+Cjx0ZXh0IHg9IjMwMCIgeT0iMzUwIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmb250LWZhbWlseT0iQXJpYWwiIGZvbnQtc2l6ZT0iMTgiIGZpbGw9IiM4Njg2OEIiPk5vIGltYWdlPC90ZXh0Pgo8L3N2Zz4K';
                    }
                }, true);
            }

            #setupMagneticButtons() {
                const magneticButtons = document.querySelectorAll('.magnetic');
                
                magneticButtons.forEach(button => {
                    button.addEventListener('mousemove', (e) => {
                        const rect = button.getBoundingClientRect();
                        const x = e.clientX - rect.left;
                        const y = e.clientY - rect.top;
                        
                        const centerX = rect.width / 2;
                        const centerY = rect.height / 2;
                        
                        const moveX = (x - centerX) * 0.2;
                        const moveY = (y - centerY) * 0.2;
                        
                        button.style.transform = `translate(${moveX}px, ${moveY}px)`;
                    });
                    
                    button.addEventListener('mouseleave', () => {
                        button.style.transform = 'translate(0, 0)';
                    });
                });
            }

            #setupMouseTracking() {
                this.#hero.addEventListener('mousemove', (e) => {
                    const rect = this.#hero.getBoundingClientRect();
                    const x = ((e.clientX - rect.left) / rect.width) * 100;
                    const y = ((e.clientY - rect.top) / rect.height) * 100;
                    
                    this.#hero.style.setProperty('--mouse-x', `${x}%`);
                    this.#hero.style.setProperty('--mouse-y', `${y}%`);
                });
            }

            #setupScrollHandler() {
                let ticking = false;
                
                const handleScroll = () => {
                    const currentScrollY = window.scrollY;
                    const scrollHeight = document.documentElement.scrollHeight - window.innerHeight;
                    const scrollProgress = (currentScrollY / scrollHeight) * 100;
                    
                    // Progress bar
                    this.#scrollProgress.style.width = `${scrollProgress}%`;
                    
                    // Scroll to top button
                    if (currentScrollY > 300) {
                        this.#scrollToTop.classList.add('visible');
                    } else {
                        this.#scrollToTop.classList.remove('visible');
                    }
                    
                    // Header logic
                    if (currentScrollY > 100) {
                        this.#mainHeader.classList.add('scrolled');
                        
                        if (currentScrollY > this.#lastScrollY && currentScrollY > 100) {
                            this.#mainHeader.classList.add('hidden');
                        } else {
                            this.#mainHeader.classList.remove('hidden');
                        }
                    } else {
                        this.#mainHeader.classList.remove('hidden');
                        this.#mainHeader.classList.remove('scrolled');
                    }
                    
                    this.#lastScrollY = currentScrollY;
                    ticking = false;
                };
                
                const onScroll = () => {
                    if (!ticking) {
                        requestAnimationFrame(handleScroll);
                        ticking = true;
                    }
                };
                
                window.addEventListener('scroll', onScroll, { passive: true });
            }

            #addServiceEventListeners() {
                const orderButtons = document.querySelectorAll('.service-button');
                orderButtons.forEach(button => {
                    button.addEventListener('click', () => {
                        const serviceName = button.dataset.service;
                        this.#openOrderModal(serviceName);
                    });
                });
            }

            #setupEventListeners() {
                this.#themeToggle.addEventListener('click', () => this.#toggleTheme());
                this.#contactBtn.addEventListener('click', () => this.#openContactModal());
                this.#modalClose.addEventListener('click', () => this.#closeContactModal());
                this.#scrollToTop.addEventListener('click', () => this.#scrollToTopHandler());
                
                this.#contactModal.addEventListener('click', (e) => {
                    if (e.target === this.#contactModal) {
                        this.#closeContactModal();
                    }
                });

                document.addEventListener('keydown', (e) => {
                    if (e.key === 'Escape' && this.#contactModal.style.display === 'flex') {
                        this.#closeContactModal();
                    }
                });

                window.addEventListener('resize', debounce(() => this.#handleResize(), 250));
            }

            #setupScrollAnimations() {
                const serviceCards = document.querySelectorAll('.service-card');
                const portfolioItems = document.querySelectorAll('.portfolio-item');
                
                animateOnScroll([...serviceCards, ...portfolioItems]);
            }

            #scrollToTopHandler() {
                window.scrollTo({
                    top: 0,
                    behavior: 'smooth'
                });
            }

            #toggleTheme() {
                this.#isDarkTheme = !this.#isDarkTheme;
                
                // View Transitions API для плавной смены темы
                if (document.startViewTransition) {
                    document.startViewTransition(() => {
                        document.body.classList.toggle('dark-theme', this.#isDarkTheme);
                    });
                } else {
                    document.body.classList.toggle('dark-theme', this.#isDarkTheme);
                }
                
                this.#themeToggle.innerHTML = this.#isDarkTheme 
                    ? '<i class="fas fa-sun"></i> Светлая тема'
                    : '<i class="fas fa-moon"></i> Тёмная тема';
                
                localStorage.setItem('theme', this.#isDarkTheme ? 'dark' : 'light');
            }

            #openContactModal() {
                this.#contactModal.style.display = 'flex';
                this.#contactModal.setAttribute('aria-hidden', 'false');
                document.body.style.overflow = 'hidden';
            }

            #closeContactModal() {
                this.#contactModal.style.display = 'none';
                this.#contactModal.setAttribute('aria-hidden', 'true');
                document.body.style.overflow = 'auto';
            }

            #openOrderModal(serviceName) {
                this.#openContactModal();
                console.log(`Selected service: ${serviceName}`);
            }

            #handleResize() {
                console.log('Window resized');
            }

            loadTheme() {
                const savedTheme = localStorage.getItem('theme');
                if (savedTheme === 'dark') {
                    this.#isDarkTheme = true;
                    document.body.classList.add('dark-theme');
                    this.#themeToggle.innerHTML = '<i class="fas fa-sun"></i> Светлая тема';
                }
            }
        }

        // Инициализация приложения
        document.addEventListener('DOMContentLoaded', () => {
            const app = new AppleServiceApp();
        });

        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                navigator.serviceWorker.register('/sw.js')
                    .then(registration => {
                        console.log('SW registered: ', registration);
                    })
                    .catch(registrationError => {
                        console.log('SW registration failed: ', registrationError);
                    });
            });
        }
    </script>
</body>
</html>
