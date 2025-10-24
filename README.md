




<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CofeIT- Ремонт iPhone</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Сброс стилей и базовые настройки */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Helvetica Neue', Arial, sans-serif;
        }

        :root {
            --primary-color: #007AFF;
            --secondary-color: #5856D6;
            --text-primary: #1D1D1F;
            --text-secondary: #86868B;
            --background: #FFFFFF;
            --card-background: #F5F5F7;
            --nav-background: rgba(255, 255, 255, 0.8);
            --border-radius: 12px;
            --spacing-xs: 8px;
            --spacing-sm: 16px;
            --spacing-md: 24px;
            --spacing-lg: 32px;
            --spacing-xl: 48px;
            --spacing-xxl: 64px;
            --transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* Темная тема */
        body.dark-theme {
            --primary-color: #0A84FF;
            --secondary-color: #5E5CE6;
            --text-primary: #F5F5F7;
            --text-secondary: #AEAEB2;
            --background: #1C1C1E;
            --card-background: #2C2C2E;
            --nav-background: rgba(28, 28, 30, 0.8);
        }

        body {
            background-color: var(--background);
            color: var(--text-primary);
            line-height: 1.5;
            overflow-x: hidden;
            transition: var(--transition);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 var(--spacing-sm);
        }

        /* Навигация */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: var(--spacing-sm) 0;
            position: sticky;
            top: 0;
            background-color: var(--nav-background);
            backdrop-filter: blur(20px);
            z-index: 100;
            transition: var(--transition);
        }

        .logo {
            display: flex;
            align-items: center;
            font-weight: 600;
            font-size: 1.25rem;
        }

        .logo-icon {
            width: 24px;
            height: 24px;
            margin-right: var(--spacing-xs);
            background-color: var(--primary-color);
            border-radius: 6px;
            transition: var(--transition);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: var(--spacing-md);
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-primary);
            font-weight: 500;
            transition: color 0.2s;
        }

        .nav-links a:hover {
            color: var(--primary-color);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-primary);
        }

        /* Переключатель темы */
        .theme-toggle {
            display: flex;
            align-items: center;
            margin-left: var(--spacing-md);
            cursor: pointer;
            position: relative;
        }

        .toggle-track {
            width: 50px;
            height: 24px;
            background-color: var(--card-background);
            border-radius: 50px;
            position: relative;
            transition: var(--transition);
            box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.1);
        }

        .toggle-thumb {
            position: absolute;
            top: 2px;
            left: 2px;
            width: 20px;
            height: 20px;
            background-color: white;
            border-radius: 50%;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        .toggle-icon {
            font-size: 12px;
            transition: var(--transition);
        }

        .sun-icon {
            color: #FF9500;
        }

        .moon-icon {
            color: #8E8E93;
        }

        body.dark-theme .toggle-track {
            background-color: var(--primary-color);
        }

        body.dark-theme .toggle-thumb {
            transform: translateX(26px);
        }

        body.dark-theme .sun-icon {
            opacity: 0;
            transform: rotate(90deg);
        }

        body.dark-theme .moon-icon {
            opacity: 1;
            transform: rotate(0);
        }

        body:not(.dark-theme) .sun-icon {
            opacity: 1;
            transform: rotate(0);
        }

        body:not(.dark-theme) .moon-icon {
            opacity: 0;
            transform: rotate(-90deg);
        }

        /* Герой секция */
        .hero {
            padding: var(--spacing-xxl) 0;
            text-align: center;
            background: linear-gradient(135deg, var(--card-background) 0%, var(--background) 100%);
            transition: var(--transition);
        }

        .hero h1 {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: var(--spacing-sm);
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            transition: var(--transition);
        }

        .hero p {
            font-size: 1.25rem;
            color: var(--text-secondary);
            max-width: 600px;
            margin: 0 auto var(--spacing-lg);
            transition: var(--transition);
        }

        .btn {
            display: inline-block;
            padding: var(--spacing-sm) var(--spacing-lg);
            background-color: var(--primary-color);
            color: white;
            border-radius: var(--border-radius);
            text-decoration: none;
            font-weight: 600;
            transition: var(--transition);
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            background-color: #0056CC;
            transform: translateY(-2px);
        }

        .btn-secondary {
            background-color: transparent;
            color: var(--primary-color);
            border: 1px solid var(--primary-color);
        }

        .btn-secondary:hover {
            background-color: rgba(0, 122, 255, 0.1);
        }

        /* Секция услуг */
        .services {
            padding: var(--spacing-xxl) 0;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: var(--spacing-xl);
            transition: var(--transition);
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: var(--spacing-lg);
        }

        .service-card {
            background-color: var(--card-background);
            border-radius: var(--border-radius);
            padding: var(--spacing-lg);
            transition: var(--transition);
        }

        .service-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }

        .service-icon {
            width: 48px;
            height: 48px;
            background-color: var(--primary-color);
            border-radius: 12px;
            margin-bottom: var(--spacing-md);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.25rem;
            transition: var(--transition);
        }

        .service-card h3 {
            font-size: 1.25rem;
            margin-bottom: var(--spacing-sm);
            transition: var(--transition);
        }

        .service-card p {
            color: var(--text-secondary);
            margin-bottom: var(--spacing-md);
            transition: var(--transition);
        }

        /* Галерея работ */
        .gallery {
            padding: var(--spacing-xxl) 0;
            background-color: var(--card-background);
            transition: var(--transition);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: var(--spacing-md);
        }

        .gallery-item {
            border-radius: var(--border-radius);
            overflow: hidden;
            position: relative;
            aspect-ratio: 1 / 1;
            background-color: var(--background);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-secondary);
            font-size: 0.9rem;
            transition: var(--transition);
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .gallery-item:hover img {
            transform: scale(1.05);
        }

        /* Секция преимуществ */
        .advantages {
            padding: var(--spacing-xxl) 0;
        }

        .advantages-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: var(--spacing-lg);
        }

        .advantage-item {
            text-align: center;
            padding: var(--spacing-lg);
        }

        .advantage-icon {
            width: 64px;
            height: 64px;
            background-color: var(--primary-color);
            border-radius: 16px;
            margin: 0 auto var(--spacing-md);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
            transition: var(--transition);
        }

        .advantage-item h3 {
            font-size: 1.25rem;
            margin-bottom: var(--spacing-sm);
            transition: var(--transition);
        }

        .advantage-item p {
            color: var(--text-secondary);
            transition: var(--transition);
        }

        /* Футер */
        footer {
            background-color: var(--text-primary);
            color: white;
            padding: var(--spacing-xxl) 0 var(--spacing-lg);
            transition: var(--transition);
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: var(--spacing-xl);
            margin-bottom: var(--spacing-xl);
        }

        .footer-column h3 {
            font-size: 1.125rem;
            margin-bottom: var(--spacing-md);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: var(--spacing-xs);
        }

        .footer-links a {
            color: #86868B;
            text-decoration: none;
            transition: color 0.2s;
        }

        .footer-links a:hover {
            color: white;
        }

        .footer-bottom {
            text-align: center;
            padding-top: var(--spacing-lg);
            border-top: 1px solid #333336;
            color: #86868B;
        }

        /* Анимации для плавного появления элементов */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .animate-fade-in-up {
            animation: fadeInUp 0.6s ease-out forwards;
        }

        .service-card, .gallery-item, .advantage-item {
            opacity: 0;
            animation: fadeInUp 0.6s ease-out forwards;
        }

        /* Задержки для анимации появления карточек */
        .service-card:nth-child(1) { animation-delay: 0.1s; }
        .service-card:nth-child(2) { animation-delay: 0.2s; }
        .service-card:nth-child(3) { animation-delay: 0.3s; }
        .service-card:nth-child(4) { animation-delay: 0.4s; }
        .service-card:nth-child(5) { animation-delay: 0.5s; }
        .service-card:nth-child(6) { animation-delay: 0.6s; }

        /* Адаптивность для мобильных устройств */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                background-color: var(--background);
                flex-direction: column;
                padding: var(--spacing-md);
                box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
                transition: var(--transition);
            }

            .nav-links.active {
                display: flex;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .hero p {
                font-size: 1rem;
            }

            .section-title {
                font-size: 1.75rem;
            }

            .theme-toggle {
                margin-left: auto;
                margin-right: var(--spacing-md);
            }
        }

        /* Адаптивность для 4K мониторов */
        @media (min-width: 2000px) {
            .container {
                max-width: 1800px;
            }

            .hero h1 {
                font-size: 4rem;
            }

            .hero p {
                font-size: 1.5rem;
                max-width: 800px;
            }

            .section-title {
                font-size: 3.5rem;
            }

            .services-grid, .gallery-grid, .advantages-grid {
                gap: var(--spacing-xl);
            }

            .service-card, .advantage-item {
                padding: var(--spacing-xl);
            }

            .service-icon, .advantage-icon {
                width: 64px;
                height: 64px;
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Навигация -->
    <nav>
        <div class="container">
            <div class="logo">
                <div class="logo-icon"></div>
                COFEIT
            </div>
            <ul class="nav-links">
                <li><a href="#services">Услуги</a></li>
                <li><a href="#gallery">Работы</a></li>
                <li><a href="#advantages">Преимущества</a></li>
                <li><a href="#contact">Контакты</a></li>
            </ul>
            <div class="theme-toggle" id="themeToggle">
                <div class="toggle-track">
                    <div class="toggle-thumb">
                        <i class="fas fa-sun toggle-icon sun-icon"></i>
                        <i class="fas fa-moon toggle-icon moon-icon"></i>
                    </div>
                </div>
            </div>
            <button class="mobile-menu-btn">☰</button>
        </div>
    </nav>

    <!-- Герой секция -->
    <section class="hero">
        <div class="container">
            <h1>Профессиональный ремонт iPhone</h1>
            <p>Официальный сервисный центр Apple. Качественный ремонт вашего устройства с гарантией.</p>
            <div style="display: flex; gap: var(--spacing-sm); justify-content: center; flex-wrap: wrap;">
                <a href="#contact" class="btn">Записаться на ремонт</a>
                <a href="#services" class="btn btn-secondary">Наши услуги</a>
            </div>
        </div>
    </section>

    <!-- Секция услуг -->
    <section class="services" id="services">
        <div class="container">
            <h2 class="section-title">Наши услуги</h2>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon"><i class="fas fa-mobile-alt"></i></div>
                    <h3>Замена дисплея</h3>
                    <p>Профессиональная замена экрана на оригинальные компоненты с калибровкой True Tone.</p>
                    <a href="#" class="btn btn-secondary">Подробнее</a>
                </div>
                <div class="service-card">
                    <div class="service-icon"><i class="fas fa-battery-three-quarters"></i></div>
                    <h3>Замена аккумулятора</h3>
                    <p>Установка новых оригинальных аккумуляторов с восстановлением индикации здоровья батареи.</p>
                    <a href="#" class="btn btn-secondary">Подробнее</a>
                </div>
                <div class="service-card">
                    <div class="service-icon"><i class="fas fa-camera"></i></div>
                    <h3>Ремонт камеры</h3>
                    <p>Диагностика и ремонт систем камер, включая замену объективов и сенсоров.</p>
                    <a href="#" class="btn btn-secondary">Подробнее</a>
                </div>
                <div class="service-card">
                    <div class="service-icon"><i class="fas fa-tint"></i></div>
                    <h3>Устранение последствий попадания влаги</h3>
                    <p>Чистка платы, восстановление контактов и замена поврежденных компонентов.</p>
                    <a href="#" class="btn btn-secondary">Подробнее</a>
                </div>
                <div class="service-card">
                    <div class="service-icon"><i class="fas fa-bolt"></i></div>
                    <h3>Ремонт систем питания</h3>
                    <p>Диагностика и ремонт цепей питания, замена контроллеров и восстановление стабильной работы.</p>
                    <a href="#" class="btn btn-secondary">Подробнее</a>
                </div>
                <div class="service-card">
                    <div class="service-icon"><i class="fas fa-volume-up"></i></div>
                    <h3>Ремонт динамиков и микрофонов</h3>
                    <p>Замена аудиокомпонентов с сохранением водозащиты и качества звука.</p>
                    <a href="#" class="btn btn-secondary">Подробнее</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Галерея работ -->
    <section class="gallery" id="gallery">
        <div class="container">
            <h2 class="section-title">Примеры наших работ</h2>
            <div class="gallery-grid">
                <!-- Здесь будут 10 изображений примеров работ -->
                <div class="gallery-item">
                    <div>Замена дисплея iPhone 15 Pro</div>
                </div>
                <div class="gallery-item">
                    <div>Ремонт после попадания влаги</div>
                </div>
                <div class="gallery-item">
                    <div>Замена аккумулятора iPhone 14</div>
                </div>
                <div class="gallery-item">
                    <div>Ремонт камеры iPhone 13 Pro</div>
                </div>
                <div class="gallery-item">
                    <div>Замена корпуса iPhone 12</div>
                </div>
                <div class="gallery-item">
                    <div>Ремонт системной платы</div>
                </div>
                <div class="gallery-item">
                    <div>Восстановление после падения</div>
                </div>
                <div class="gallery-item">
                    <div>Замена разъема Lightning</div>
                </div>
                <div class="gallery-item">
                    <div>Ремонт кнопок и переключателей</div>
                </div>
                <div class="gallery-item">
                    <div>Обслуживание iPhone 15 Pro Max</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Секция преимуществ -->
    <section class="advantages" id="advantages">
        <div class="container">
            <h2 class="section-title">Почему выбирают нас</h2>
            <div class="advantages-grid">
                <div class="advantage-item">
                    <div class="advantage-icon"><i class="fas fa-check-circle"></i></div>
                    <h3>Оригинальные запчасти</h3>
                    <p>Используем только оригинальные компоненты Apple с сохранением всех функций.</p>
                </div>
                <div class="advantage-item">
                    <div class="advantage-icon"><i class="fas fa-user-tie"></i></div>
                    <h3>Опытные мастера</h3>
                    <p>Наши специалисты прошли сертификацию Apple и имеют многолетний опыт.</p>
                </div>
                <div class="advantage-item">
                    <div class="advantage-icon"><i class="fas fa-clock"></i></div>
                    <h3>Быстрый ремонт</h3>
                    <p>Большинство ремонтов выполняем в течение 1-2 часов в вашем присутствии.</p>
                </div>
                <div class="advantage-item">
                    <div class="advantage-icon"><i class="fas fa-shield-alt"></i></div>
                    <h3>Гарантия качества</h3>
                    <p>Предоставляем гарантию до 12 месяцев на все виды ремонтных работ.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Футер -->
    <footer id="contact">
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>COFEIT</h3>
                    <p>Профессиональный ремонт устройств Apple с 2010 года.</p>
                </div>
                <div class="footer-column">
                    <h3>Контакты</h3>
                    <ul class="footer-links">
                        <li><a href="tel:+78001234567">+7 (800) 123-45-67</a></li>
                        <li><a href="mailto:info@ifixpro.ru">info@ifixpro.ru</a></li>
                        <li>Москва, ул. Тверская, д. 10</li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Часы работы</h3>
                    <ul class="footer-links">
                        <li>Пн-Пт: 10:00 - 20:00</li>
                        <li>Сб-Вс: 11:00 - 18:00</li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Услуги</h3>
                    <ul class="footer-links">
                        <li><a href="#">Ремонт iPhone</a></li>
                        <li><a href="#">Ремонт iPad</a></li>
                        <li><a href="#">Ремонт MacBook</a></li>
                        <li><a href="#">Ремонт Apple Watch</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2025 COFEIT. Все права защищены.</p>
            </div>
        </div>
    </footer>

    <script>
        // Мобильное меню
        document.querySelector('.mobile-menu-btn').addEventListener('click', function() {
            document.querySelector('.nav-links').classList.toggle('active');
        });

        // Плавная прокрутка для якорных ссылок
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if(targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if(targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // Закрываем мобильное меню после клика
                    document.querySelector('.nav-links').classList.remove('active');
                }
            });
        });

        // Переключатель темы
        const themeToggle = document.getElementById('themeToggle');
        const body = document.body;
        
        // Проверяем сохраненную тему в localStorage или системные настройки
        const savedTheme = localStorage.getItem('theme') || 
                          (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
        
        // Применяем сохраненную тему
        if (savedTheme === 'dark') {
            body.classList.add('dark-theme');
        }
        
        // Обработчик переключения темы
        themeToggle.addEventListener('click', () => {
            body.classList.toggle('dark-theme');
            
            // Сохраняем выбор пользователя
            const isDark = body.classList.contains('dark-theme');
            localStorage.setItem('theme', isDark ? 'dark' : 'light');
        });

        // Анимация появления элементов при прокрутке
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('animate-fade-in-up');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        // Наблюдаем за карточками услуг, галереи и преимуществ
        document.querySelectorAll('.service-card, .gallery-item, .advantage-item').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>
</html>
