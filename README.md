Сайт в разработке 
Сайт в разработке 
Сайт в разработке 
Сайт в разработке 
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Apple Service Pro - Ремонт техники Apple</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #ffffff;
            --secondary-color: #000000;
            --accent-color: #007AFF;
            --text-color: #1D1D1F;
            --gray-color: #86868B;
            --transition-time: 0.6s;
            --card-bg: #F5F5F7;
            --ease-out-quint: cubic-bezier(0.22, 1, 0.36, 1);
            --ease-in-out-back: cubic-bezier(0.68, -0.55, 0.265, 1.55);
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
            transition: background-color var(--transition-time) var(--ease-out-quint), 
                        color var(--transition-time) var(--ease-out-quint);
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
        }

        /* Header Styles */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 3rem;
            padding: 1.5rem 0;
            border-bottom: 1px solid var(--gray-color);
            animation: slideDown 0.8s var(--ease-out-quint) forwards;
            opacity: 0;
            transform: translateY(-20px);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-color);
            transition: all 0.3s var(--ease-out-quint);
        }

        .logo:hover {
            transform: scale(1.05);
        }

        .logo i {
            color: var(--accent-color);
            transition: transform 0.6s var(--ease-out-quint);
        }

        .logo:hover i {
            transform: rotate(15deg) scale(1.2);
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

        .theme-toggle:hover {
            background: var(--accent-color);
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,122,255,0.3);
        }

        .contact-btn {
            background: var(--accent-color);
            color: white;
        }

        .contact-btn:hover {
            background: #0056CC;
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,122,255,0.3);
        }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 4rem 0;
            margin-bottom: 3rem;
            animation: fadeInUp 1s var(--ease-out-quint) 0.3s forwards;
            opacity: 0;
            transform: translateY(30px);
        }

        .hero h1 {
            font-size: 3.5rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
            display: inline-block;
        }

        .hero h1::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 10%;
            width: 80%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--accent-color), transparent);
            border-radius: 3px;
        }

        .hero p {
            font-size: 1.3rem;
            color: var(--gray-color);
            max-width: 700px;
            margin: 0 auto 2rem;
            animation: fadeIn 1s var(--ease-out-quint) 0.6s forwards;
            opacity: 0;
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
            padding: 10px 20px;
            border-radius: 25px;
            background: var(--card-bg);
            transition: all 0.4s var(--ease-out-quint);
            animation: fadeIn 0.8s var(--ease-out-quint) forwards;
            opacity: 0;
            transform: translateY(20px);
        }

        .feature:nth-child(1) { animation-delay: 0.8s; }
        .feature:nth-child(2) { animation-delay: 1s; }
        .feature:nth-child(3) { animation-delay: 1.2s; }

        .feature:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        .feature i {
            color: var(--accent-color);
            transition: transform 0.4s var(--ease-out-quint);
        }

        .feature:hover i {
            transform: scale(1.3) rotate(10deg);
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
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            transform: translateY(0) scale(1);
            transition: all 0.5s var(--ease-out-quint);
            position: relative;
            border: 1px solid rgba(0,0,0,0.05);
            opacity: 0;
            animation: cardAppear 0.8s var(--ease-out-quint) forwards;
        }

        @keyframes cardAppear {
            from {
                opacity: 0;
                transform: translateY(30px) scale(0.95);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .service-card:nth-child(1) { animation-delay: 0.1s; }
        .service-card:nth-child(2) { animation-delay: 0.2s; }
        .service-card:nth-child(3) { animation-delay: 0.3s; }
        .service-card:nth-child(4) { animation-delay: 0.4s; }
        .service-card:nth-child(5) { animation-delay: 0.5s; }
        .service-card:nth-child(6) { animation-delay: 0.6s; }

        .service-card:hover {
            transform: translateY(-15px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
        }

        .service-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
            display: block;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            transition: all 0.6s var(--ease-out-quint);
            position: relative;
            overflow: hidden;
        }

        .service-card:hover .service-image {
            transform: scale(1.1);
        }

        .service-image i {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 4rem;
            color: white;
            transition: all 0.6s var(--ease-out-quint);
        }

        .service-card:hover .service-image i {
            transform: translate(-50%, -50%) scale(1.2) rotate(10deg);
        }

        .service-info {
            padding: 1.8rem;
            position: relative;
            z-index: 1;
        }

        .service-name {
            font-size: 1.5rem;
            margin-bottom: 0.8rem;
            color: var(--text-color);
            display: flex;
            align-items: center;
            gap: 10px;
            transition: color 0.3s var(--ease-out-quint);
        }

        .service-card:hover .service-name {
            color: var(--accent-color);
        }

        .service-name i {
            color: var(--accent-color);
            transition: transform 0.4s var(--ease-out-quint);
        }

        .service-card:hover .service-name i {
            transform: scale(1.3);
        }

        .service-description {
            color: var(--gray-color);
            margin-bottom: 1.5rem;
            line-height: 1.6;
            transition: color 0.3s var(--ease-out-quint);
        }

        .service-price {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--accent-color);
            margin-bottom: 1rem;
            transition: all 0.4s var(--ease-out-quint);
        }

        .service-card:hover .service-price {
            transform: scale(1.1);
        }

        .service-features {
            list-style: none;
            margin-bottom: 1.5rem;
        }

        .service-features li {
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: transform 0.3s var(--ease-out-quint);
        }

        .service-card:hover .service-features li {
            transform: translateX(5px);
        }

        .service-features li:nth-child(1) { transition-delay: 0.05s; }
        .service-features li:nth-child(2) { transition-delay: 0.1s; }
        .service-features li:nth-child(3) { transition-delay: 0.15s; }
        .service-features li:nth-child(4) { transition-delay: 0.2s; }

        .service-features i {
            color: #34C759;
            font-size: 0.9rem;
            transition: transform 0.4s var(--ease-out-quint);
        }

        .service-card:hover .service-features i {
            transform: scale(1.3) rotate(15deg);
        }

        .service-button {
            width: 100%;
            padding: 12px;
            background: var(--accent-color);
            color: white;
            border: none;
            border-radius: 12px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
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
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,122,255,0.3);
        }

        /* Portfolio Section */
        .portfolio {
            margin-top: 5rem;
            padding: 3rem 0;
        }

        .portfolio h2 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: var(--text-color);
            animation: fadeIn 1s var(--ease-out-quint) 0.5s forwards;
            opacity: 0;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .portfolio-item {
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.5s var(--ease-out-quint);
            background: var(--card-bg);
            border: 1px solid rgba(0,0,0,0.05);
            opacity: 0;
            animation: fadeInUp 0.8s var(--ease-out-quint) forwards;
        }

        .portfolio-item:nth-child(1) { animation-delay: 0.1s; }
        .portfolio-item:nth-child(2) { animation-delay: 0.2s; }
        .portfolio-item:nth-child(3) { animation-delay: 0.3s; }
        .portfolio-item:nth-child(4) { animation-delay: 0.4s; }
        .portfolio-item:nth-child(5) { animation-delay: 0.5s; }
        .portfolio-item:nth-child(6) { animation-delay: 0.6s; }
        .portfolio-item:nth-child(7) { animation-delay: 0.7s; }
        .portfolio-item:nth-child(8) { animation-delay: 0.8s; }

        .portfolio-item:hover {
            transform: translateY(-12px) scale(1.03);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }

        .portfolio-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            display: block;
            transition: transform 0.6s var(--ease-out-quint);
        }

        .portfolio-item:hover .portfolio-image {
            transform: scale(1.1);
        }

        .portfolio-info {
            padding: 1.5rem;
            position: relative;
            z-index: 1;
        }

        .portfolio-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: var(--text-color);
            transition: color 0.3s var(--ease-out-quint);
        }

        .portfolio-item:hover .portfolio-title {
            color: var(--accent-color);
        }

        .portfolio-description {
            color: var(--gray-color);
            font-size: 1rem;
            line-height: 1.5;
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
            width: 40px;
            height: 40px;
            border: 4px solid var(--accent-color);
            border-left: 4px solid transparent;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin-right: 1rem;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            backdrop-filter: blur(5px);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            animation: fadeIn 0.4s var(--ease-out-quint) forwards;
        }

        .modal-content {
            background: var(--primary-color);
            padding: 2rem;
            border-radius: 20px;
            max-width: 500px;
            width: 90%;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            transform: scale(0.9);
            animation: modalAppear 0.5s var(--ease-out-quint) forwards;
        }

        @keyframes modalAppear {
            to {
                transform: scale(1);
            }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-color);
            transition: all 0.3s var(--ease-out-quint);
        }

        .modal-close:hover {
            color: var(--accent-color);
            transform: scale(1.2) rotate(90deg);
        }

        /* Footer */
        .footer {
            margin-top: 5rem;
            padding: 3rem 0;
            border-top: 1px solid var(--gray-color);
            text-align: center;
            color: var(--gray-color);
            animation: fadeIn 1s var(--ease-out-quint) 0.7s forwards;
            opacity: 0;
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 3rem;
            flex-wrap: wrap;
            margin: 2rem 0;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.4s var(--ease-out-quint);
            padding: 10px 15px;
            border-radius: 10px;
        }

        .contact-item:hover {
            background: var(--card-bg);
            transform: translateY(-5px);
        }

        .phone-number {
            cursor: pointer;
            transition: all 0.3s var(--ease-out-quint);
            position: relative;
        }

        .phone-number:hover {
            color: var(--accent-color);
            transform: scale(1.05);
        }

        .phone-number::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent-color);
            transition: width 0.4s var(--ease-out-quint);
        }

        .phone-number:hover::after {
            width: 100%;
        }

        /* Animations */
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from { 
                opacity: 0;
                transform: translateY(30px);
            }
            to { 
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .fade-in {
            animation: fadeIn 0.8s var(--ease-out-quint) forwards;
        }

        /* Particles Background */
        .particles-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        .particle {
            position: absolute;
            background: var(--accent-color);
            border-radius: 50%;
            opacity: 0.1;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 0.1;
            }
            50% {
                opacity: 0.15;
            }
            100% {
                transform: translateY(-1000px) rotate(720deg);
                opacity: 0.1;
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .header {
                flex-direction: column;
                gap: 1.5rem;
            }
            
            .hero h1 {
                font-size: 2.5rem;
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
        }
    </style>
</head>
<body>
    <!-- Particles Background -->
    <div class="particles-background" id="particlesBackground"></div>

    <div class="container">
        <header class="header">
            <div class="logo">
                <i class="fab fa-apple"></i>
                <span>Apple Service Pro</span>
            </div>
            <div class="nav-buttons">
                <button class="theme-toggle" id="themeToggle">
                    <i class="fas fa-moon"></i>
                    Тёмная тема
                </button>
                <button class="contact-btn" id="contactBtn">
                    <i class="fas fa-phone"></i>
                    Связаться
                </button>
            </div>
        </header>
        
        <section class="hero">
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
                    <span class="phone-number" id="footerPhone">+7 (495) 123-45-67</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>Москва, ул. Тверская, 15</span>
                </div>
            </div>
            <p>© 2025 Apple Service Pro. Мы не являемся официальным представителем Apple Inc.</p>
        </footer>
    </div>

    <!-- Modal -->
    <div class="modal" id="contactModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Связаться с нами</h3>
                <button class="modal-close" id="modalClose">&times;</button>
            </div>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span class="phone-number" id="modalPhone">+7 (495) 123-45-67</span>
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
        // Modern Animation Engine 2025
        class AnimationEngine2025 {
            constructor() {
                this.observers = [];
                this.init();
            }

            init() {
                this.setupScrollAnimations();
                this.setupHoverAnimations();
                this.setupParticleBackground();
            }

            setupScrollAnimations() {
                const observer = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            this.animateOnScroll(entry.target);
                        }
                    });
                }, {
                    threshold: 0.1,
                    rootMargin: '0px 0px -50px 0px'
                });

                document.querySelectorAll('.service-card, .portfolio-item, .feature').forEach(el => {
                    observer.observe(el);
                });
            }

            animateOnScroll(element) {
                if (element.classList.contains('service-card') || element.classList.contains('portfolio-item')) {
                    element.style.animationPlayState = 'running';
                }
            }

            setupHoverAnimations() {
                // Добавляем дополнительные hover-эффекты
                document.addEventListener('mousemove', (e) => {
                    this.handleMouseMove(e);
                });
            }

            handleMouseMove(e) {
                const cards = document.querySelectorAll('.service-card, .portfolio-item');
                cards.forEach(card => {
                    const rect = card.getBoundingClientRect();
                    const x = e.clientX - rect.left;
                    const y = e.clientY - rect.top;
                    
                    if (x > 0 && x < rect.width && y > 0 && y < rect.height) {
                        const centerX = rect.width / 2;
                        const centerY = rect.height / 2;
                        
                        const angleY = (x - centerX) / 25;
                        const angleX = (centerY - y) / 25;
                        
                        card.style.transform = `perspective(1000px) rotateX(${angleX}deg) rotateY(${angleY}deg) scale3d(1.02, 1.02, 1.02)`;
                    } else {
                        card.style.transform = 'perspective(1000px) rotateX(0) rotateY(0) scale3d(1, 1, 1)';
                    }
                });
            }

            setupParticleBackground() {
                const particlesContainer = document.getElementById('particlesBackground');
                const particleCount = 30;
                
                for (let i = 0; i < particleCount; i++) {
                    const particle = document.createElement('div');
                    particle.className = 'particle';
                    
                    const size = Math.random() * 60 + 10;
                    const posX = Math.random() * 100;
                    const delay = Math.random() * 20;
                    const duration = Math.random() * 20 + 20;
                    
                    particle.style.width = `${size}px`;
                    particle.style.height = `${size}px`;
                    particle.style.left = `${posX}%`;
                    particle.style.animationDelay = `${delay}s`;
                    particle.style.animationDuration = `${duration}s`;
                    
                    particlesContainer.appendChild(particle);
                }
            }

            createRipple(event) {
                const button = event.currentTarget;
                const circle = document.createElement('span');
                const diameter = Math.max(button.clientWidth, button.clientHeight);
                const radius = diameter / 2;

                circle.style.width = circle.style.height = `${diameter}px`;
                circle.style.left = `${event.clientX - button.getBoundingClientRect().left - radius}px`;
                circle.style.top = `${event.clientY - button.getBoundingClientRect().top - radius}px`;
                circle.classList.add('ripple');

                const ripple = button.getElementsByClassName('ripple')[0];
                if (ripple) {
                    ripple.remove();
                }

                button.appendChild(circle);
            }
        }

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
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            }, {
                threshold: 0.1,
                rootMargin: '0px 0px -50px 0px',
                ...options
            });

            elements.forEach(element => observer.observe(element));
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
            #footerPhone;
            #modalPhone;
            #isDarkTheme = false;
            #animationEngine;

            constructor() {
                this.#initializeElements();
                this.#init();
            }

            #initializeElements() {
                this.#servicesGrid = document.getElementById('servicesGrid');
                this.#portfolioGrid = document.getElementById('portfolioGrid');
                this.#themeToggle = document.getElementById('themeToggle');
                this.#contactBtn = document.getElementById('contactBtn');
                this.#contactModal = document.getElementById('contactModal');
                this.#modalClose = document.getElementById('modalClose');
                this.#footerPhone = document.getElementById('footerPhone');
                this.#modalPhone = document.getElementById('modalPhone');
            }

            #init() {
                this.#animationEngine = new AnimationEngine2025();
                this.#loadServices();
                this.#loadPortfolio();
                this.#setupEventListeners();
                this.#setupPhoneCallFunctionality();
                this.#setupImageLoading();
            }

            async #loadServices() {
                // Имитация загрузки данных
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
                const card = createElement('div', ['service-card', 'fade-in']);
                
                card.innerHTML = `
                    <div class="service-image" style="background: ${service.color};">
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
                        <button class="service-button" data-service="${service.name}">
                            <i class="fas fa-tools"></i>
                            Заказать ремонт
                        </button>
                    </div>
                `;
                
                return card;
            }

            #renderPortfolio() {
                const portfolioItems = PORTFOLIO_ITEMS.map(item => 
                    this.#createPortfolioItem(item)
                );
                
                this.#portfolioGrid.append(...portfolioItems);
            }

            #createPortfolioItem(item) {
                const portfolioItem = createElement('div', ['portfolio-item', 'fade-in']);
                
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
                // Ленивая загрузка изображений с Intersection Observer
                const imageObserver = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            const img = entry.target;
                            img.src = img.dataset.src;
                            imageObserver.unobserve(img);
                        }
                    });
                });

                document.querySelectorAll('img[data-src]').forEach(img => {
                    imageObserver.observe(img);
                });
            }

            #addServiceEventListeners() {
                const orderButtons = document.querySelectorAll('.service-button');
                orderButtons.forEach(button => {
                    button.addEventListener('click', (e) => {
                        this.#animationEngine.createRipple(e);
                        const serviceName = button.dataset.service;
                        this.#openOrderModal(serviceName);
                    });
                });
            }

            #setupEventListeners() {
                // Theme toggle
                this.#themeToggle.addEventListener('click', () => this.#toggleTheme());
                
                // Contact modal
                this.#contactBtn.addEventListener('click', () => this.#openContactModal());
                this.#modalClose.addEventListener('click', () => this.#closeContactModal());
                
                // Close modal on backdrop click
                this.#contactModal.addEventListener('click', (e) => {
                    if (e.target === this.#contactModal) {
                        this.#closeContactModal();
                    }
                });

                // Escape key to close modal
                document.addEventListener('keydown', (e) => {
                    if (e.key === 'Escape' && this.#contactModal.style.display === 'flex') {
                        this.#closeContactModal();
                    }
                });

                // Debounced resize handler
                window.addEventListener('resize', debounce(() => this.#handleResize(), 250));
            }

            #setupPhoneCallFunctionality() {
                // Добавляем функциональность вызова по нажатию на номер телефона
                const phoneNumbers = [this.#footerPhone, this.#modalPhone];
                
                phoneNumbers.forEach(phoneElement => {
                    phoneElement.addEventListener('click', () => {
                        this.#initiatePhoneCall();
                    });
                    
                    // Добавляем анимацию при нажатии
                    phoneElement.addEventListener('mousedown', () => {
                        phoneElement.style.transform = 'scale(0.95)';
                    });
                    
                    phoneElement.addEventListener('mouseup', () => {
                        phoneElement.style.transform = 'scale(1)';
                    });
                });
            }

            #initiatePhoneCall() {
                const phoneNumber = '+74951234567';
                
                // Создаем красивую анимацию подтверждения вызова
                const callModal = createElement('div');
                callModal.innerHTML = `
                    <div style="
                        position: fixed;
                        top: 0;
                        left: 0;
                        width: 100%;
                        height: 100%;
                        background: rgba(0,0,0,0.8);
                        display: flex;
                        justify-content: center;
                        align-items: center;
                        z-index: 2000;
                        animation: fadeIn 0.3s ease;
                    ">
                        <div style="
                            background: var(--primary-color);
                            padding: 2rem;
                            border-radius: 20px;
                            text-align: center;
                            max-width: 400px;
                            width: 90%;
                            animation: modalAppear 0.4s cubic-bezier(0.22, 1, 0.36, 1);
                        ">
                            <div style="font-size: 4rem; color: var(--accent-color); margin-bottom: 1rem;">
                                <i class="fas fa-phone"></i>
                            </div>
                            <h3 style="margin-bottom: 1rem; color: var(--text-color);">Вызов сервисного центра</h3>
                            <p style="margin-bottom: 1.5rem; color: var(--gray-color);">
                                Вызываем: <strong>+7 (495) 123-45-67</strong>
                            </p>
                            <div style="display: flex; gap: 1rem; justify-content: center;">
                                <button id="confirmCall" style="
                                    background: var(--accent-color);
                                    color: white;
                                    border: none;
                                    padding: 10px 20px;
                                    border-radius: 10px;
                                    cursor: pointer;
                                    font-weight: 600;
                                ">Позвонить</button>
                                <button id="cancelCall" style="
                                    background: transparent;
                                    color: var(--text-color);
                                    border: 1px solid var(--gray-color);
                                    padding: 10px 20px;
                                    border-radius: 10px;
                                    cursor: pointer;
                                ">Отмена</button>
                            </div>
                        </div>
                    </div>
                `;
                
                document.body.appendChild(callModal);
                
                // Обработчики для кнопок подтверждения/отмены
                document.getElementById('confirmCall').addEventListener('click', () => {
                    // Имитация звонка - в реальном приложении здесь будет window.location.href = 'tel:+74951234567'
                    window.location.href = 'tel:' + phoneNumber;
                    document.body.removeChild(callModal);
                });
                
                document.getElementById('cancelCall').addEventListener('click', () => {
                    document.body.removeChild(callModal);
                });
            }

            #setupScrollAnimations() {
                // Анимация для сервисных карточек
                const serviceCards = document.querySelectorAll('.service-card');
                const portfolioItems = document.querySelectorAll('.portfolio-item');
                
                animateOnScroll([...serviceCards, ...portfolioItems]);
            }

            #toggleTheme() {
                this.#isDarkTheme = !this.#isDarkTheme;
                document.body.classList.toggle('dark-theme', this.#isDarkTheme);
                
                const icon = this.#themeToggle.querySelector('i');
                this.#themeToggle.innerHTML = this.#isDarkTheme 
                    ? '<i class="fas fa-sun"></i> Светлая тема'
                    : '<i class="fas fa-moon"></i> Тёмная тема';
                
                // Сохраняем тему в localStorage
                localStorage.setItem('theme', this.#isDarkTheme ? 'dark' : 'light');
            }

            #openContactModal() {
                this.#contactModal.style.display = 'flex';
                document.body.style.overflow = 'hidden';
            }

            #closeContactModal() {
                this.#contactModal.style.display = 'none';
                document.body.style.overflow = 'auto';
            }

            #openOrderModal(serviceName) {
                this.#openContactModal();
                // Можно добавить логику для предзаполнения формы заказа
                console.log(`Selected service: ${serviceName}`);
            }

            #handleResize() {
                // Логика для обработки изменения размера окна
                console.log('Window resized');
            }

            // Публичные методы
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
            app.loadTheme();
        });

        // Service Worker регистрация (опционально)
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
