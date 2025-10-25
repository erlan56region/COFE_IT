<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>iFix Pro | Профессиональный ремонт техники Apple</title>
    <style>
        :root {
            --apple-white: #f5f5f7;
            --apple-black: #1d1d1f;
            --apple-gray: #86868b;
            --apple-blue: #0071e3;
            --apple-light-gray: #d2d2d7;
            --apple-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', sans-serif;
        }
        
        body {
            background-color: var(--apple-white);
            color: var(--apple-black);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            background-color: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.05);
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }
        
        .logo {
            display: flex;
            align-items: center;
            font-size: 24px;
            font-weight: 700;
            color: var(--apple-black);
            text-decoration: none;
        }
        
        .logo-icon {
            margin-right: 10px;
            font-size: 28px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 30px;
        }
        
        nav ul li a {
            text-decoration: none;
            color: var(--apple-black);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: var(--apple-blue);
        }
        
        .header-actions {
            display: flex;
            align-items: center;
        }
        
        .phone-link {
            background-color: var(--apple-blue);
            color: white;
            padding: 10px 20px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
        }
        
        .phone-link:hover {
            background-color: #0056b3;
        }
        
        .phone-icon {
            margin-right: 8px;
        }
        
        /* Hero Section */
        .hero {
            padding: 160px 0 100px;
            background: var(--apple-gradient);
            color: white;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            font-weight: 700;
        }
        
        .hero p {
            font-size: 1.25rem;
            max-width: 700px;
            margin: 0 auto 30px;
            opacity: 0.9;
        }
        
        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        
        .btn {
            padding: 14px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            display: inline-block;
        }
        
        .btn-primary {
            background-color: white;
            color: var(--apple-blue);
        }
        
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        .btn-secondary {
            background-color: transparent;
            color: white;
            border: 2px solid white;
        }
        
        .btn-secondary:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        /* Services Section */
        .services {
            padding: 100px 0;
            background-color: white;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }
        
        .section-title h2 {
            font-size: 2.5rem;
            margin-bottom: 15px;
        }
        
        .section-title p {
            color: var(--apple-gray);
            max-width: 600px;
            margin: 0 auto;
        }
        
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .service-card {
            background-color: var(--apple-white);
            border-radius: 16px;
            padding: 30px;
            transition: transform 0.3s, box-shadow 0.3s;
            text-align: center;
        }
        
        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }
        
        .service-icon {
            font-size: 48px;
            margin-bottom: 20px;
            color: var(--apple-blue);
        }
        
        .service-card h3 {
            margin-bottom: 15px;
            font-size: 1.5rem;
        }
        
        .service-card p {
            color: var(--apple-gray);
            margin-bottom: 20px;
        }
        
        .service-price {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--apple-black);
            margin-bottom: 20px;
        }
        
        .service-link {
            color: var(--apple-blue);
            text-decoration: none;
            font-weight: 600;
            display: inline-flex;
            align-items: center;
        }
        
        .service-link:hover {
            text-decoration: underline;
        }
        
        /* Process Section */
        .process {
            padding: 100px 0;
            background-color: var(--apple-white);
        }
        
        .process-steps {
            display: flex;
            justify-content: space-between;
            margin-top: 50px;
            position: relative;
        }
        
        .process-steps::before {
            content: '';
            position: absolute;
            top: 40px;
            left: 0;
            right: 0;
            height: 2px;
            background-color: var(--apple-light-gray);
            z-index: 1;
        }
        
        .step {
            text-align: center;
            position: relative;
            z-index: 2;
            flex: 1;
        }
        
        .step-number {
            width: 80px;
            height: 80px;
            background-color: var(--apple-blue);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: 700;
            margin: 0 auto 20px;
        }
        
        .step h3 {
            margin-bottom: 10px;
        }
        
        .step p {
            color: var(--apple-gray);
            max-width: 250px;
            margin: 0 auto;
        }
        
        /* CTA Section */
        .cta {
            padding: 100px 0;
            background: var(--apple-gradient);
            color: white;
            text-align: center;
        }
        
        .cta h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        
        .cta p {
            font-size: 1.25rem;
            max-width: 700px;
            margin: 0 auto 40px;
            opacity: 0.9;
        }
        
        .cta-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
        }
        
        /* Footer */
        footer {
            background-color: var(--apple-black);
            color: var(--apple-light-gray);
            padding: 80px 0 40px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 60px;
        }
        
        .footer-column h3 {
            color: white;
            margin-bottom: 25px;
            font-size: 1.25rem;
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column ul li {
            margin-bottom: 15px;
        }
        
        .footer-column ul li a {
            color: var(--apple-light-gray);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-column ul li a:hover {
            color: white;
        }
        
        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
        }
        
        .contact-icon {
            margin-right: 10px;
            font-size: 18px;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background-color 0.3s;
        }
        
        .social-link:hover {
            background-color: var(--apple-blue);
        }
        
        .copyright {
            text-align: center;
            padding-top: 40px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 0.9rem;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                padding: 15px 0;
            }
            
            nav ul {
                margin: 20px 0;
            }
            
            nav ul li {
                margin: 0 10px;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 100%;
                max-width: 300px;
                text-align: center;
            }
            
            .process-steps {
                flex-direction: column;
                gap: 40px;
            }
            
            .process-steps::before {
                display: none;
            }
            
            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-container">
            <a href="#" class="logo">
                <span class="logo-icon">🔧</span>
                iFix Pro
            </a>
            <nav>
                <ul>
                    <li><a href="#services">Услуги</a></li>
                    <li><a href="#process">Процесс</a></li>
                    <li><a href="#reviews">Отзывы</a></li>
                    <li><a href="#contacts">Контакты</a></li>
                </ul>
            </nav>
            <div class="header-actions">
                <a href="tel:+78001234567" class="phone-link">
                    <span class="phone-icon">📞</span>
                    +7 (800) 123-45-67
                </a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h1>Профессиональный ремонт техники Apple</h1>
            <p>Быстро, качественно и с гарантией. Вернем вашим устройствам прежнюю производительность уже сегодня!</p>
            <div class="hero-buttons">
                <a href="#services" class="btn btn-primary">Наши услуги</a>
                <a href="#contacts" class="btn btn-secondary">Записаться на ремонт</a>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <div class="container">
            <div class="section-title">
                <h2>Наши услуги</h2>
                <p>Мы специализируемся на ремонте всей линейки продукции Apple с использованием оригинальных запчастей</p>
            </div>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">📱</div>
                    <h3>Ремонт iPhone</h3>
                    <p>Замена экрана, аккумулятора, динамиков и других компонентов</p>
                    <div class="service-price">от 1 990 ₽</div>
                    <a href="#" class="service-link">Подробнее →</a>
                </div>
                <div class="service-card">
                    <div class="service-icon">💻</div>
                    <h3>Ремонт MacBook</h3>
                    <p>Диагностика, замена клавиатуры, матрицы, ремонт материнской платы</p>
                    <div class="service-price">от 3 990 ₽</div>
                    <a href="#" class="service-link">Подробнее →</a>
                </div>
                <div class="service-card">
                    <div class="service-icon">⌚️</div>
                    <h3>Ремонт Apple Watch</h3>
                    <p>Замена дисплея, корпуса, аккумулятора и других компонентов</p>
                    <div class="service-price">от 2 490 ₽</div>
                    <a href="#" class="service-link">Подробнее →</a>
                </div>
                <div class="service-card">
                    <div class="service-icon">🎧</div>
                    <h3>Ремонт AirPods</h3>
                    <p>Замена кейса, наушников, ремонт платы зарядки и чистка</p>
                    <div class="service-price">от 1 490 ₽</div>
                    <a href="#" class="service-link">Подробнее →</a>
                </div>
                <div class="service-card">
                    <div class="service-icon">📱</div>
                    <h3>Восстановление данных</h3>
                    <p>Восстановление данных после повреждения, удаления или сбоя системы</p>
                    <div class="service-price">от 2 990 ₽</div>
                    <a href="#" class="service-link">Подробнее →</a>
                </div>
                <div class="service-card">
                    <div class="service-icon">🔧</div>
                    <h3>Диагностика</h3>
                    <p>Полная диагностика устройства для выявления неисправностей</p>
                    <div class="service-price">Бесплатно</div>
                    <a href="#" class="service-link">Подробнее →</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Process Section -->
    <section class="process" id="process">
        <div class="container">
            <div class="section-title">
                <h2>Как мы работаем</h2>
                <p>Простой и понятный процесс ремонта, который экономит ваше время и нервы</p>
            </div>
            <div class="process-steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <h3>Заявка</h3>
                    <p>Оставьте заявку на сайте или позвоните нам для записи на диагностику</p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <h3>Диагностика</h3>
                    <p>Бесплатная диагностика устройства для точного определения проблемы</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <h3>Ремонт</h3>
                    <p>Профессиональный ремонт с использованием оригинальных запчастей</p>
                </div>
                <div class="step">
                    <div class="step-number">4</div>
                    <h3>Готово</h3>
                    <p>Тестирование устройства и передача его вам с гарантией на работу</p>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta" id="contacts">
        <div class="container">
            <h2>Готовы починить ваше устройство?</h2>
            <p>Свяжитесь с нами прямо сейчас и получите бесплатную диагностику</p>
            <div class="cta-buttons">
                <a href="tel:+78001234567" class="btn btn-primary">Позвонить</a>
                <a href="#" class="btn btn-secondary">Записаться онлайн</a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>iFix Pro</h3>
                    <p>Профессиональный ремонт техники Apple с 2018 года. Мы используем только оригинальные запчасти и даем гарантию на все виды работ.</p>
                    <div class="social-links">
                        <a href="#" class="social-link">VK</a>
                        <a href="#" class="social-link">TG</a>
                        <a href="#" class="social-link">IG</a>
                        <a href="#" class="social-link">YT</a>
                    </div>
                </div>
                <div class="footer-column">
                    <h3>Услуги</h3>
                    <ul>
                        <li><a href="#">Ремонт iPhone</a></li>
                        <li><a href="#">Ремонт MacBook</a></li>
                        <li><a href="#">Ремонт iPad</a></li>
                        <li><a href="#">Ремонт Apple Watch</a></li>
                        <li><a href="#">Ремонт AirPods</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Компания</h3>
                    <ul>
                        <li><a href="#">О нас</a></li>
                        <li><a href="#">Отзывы</a></li>
                        <li><a href="#">Вакансии</a></li>
                        <li><a href="#">Блог</a></li>
                        <li><a href="#">Контакты</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Контакты</h3>
                    <div class="contact-info">
                        <div class="contact-item">
                            <span class="contact-icon">📞</span>
                            <span>+7 (800) 123-45-67</span>
                        </div>
                        <div class="contact-item">
                            <span class="contact-icon">✉️</span>
                            <span>info@ifixpro.ru</span>
                        </div>
                        <div class="contact-item">
                            <span class="contact-icon">📍</span>
                            <span>г. Москва, ул. Примерная, д. 123</span>
                        </div>
                        <div class="contact-item">
                            <span class="contact-icon">🕒</span>
                            <span>Пн-Вс: 10:00 - 20:00</span>
                        </div>
                    </div>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2025 iFix Pro. Все права защищены.</p>
            </div>
        </div>
    </footer>

    <script>
        // Плавная прокрутка для якорных ссылок
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 100,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // Изменение прозрачности хедера при скролле
        window.addEventListener('scroll', function() {
            const header = document.querySelector('header');
            if (window.scrollY > 100) {
                header.style.backgroundColor = 'rgba(255, 255, 255, 0.95)';
            } else {
                header.style.backgroundColor = 'rgba(255, 255, 255, 0.9)';
            }
        });
    </script>
</body>
</html>
