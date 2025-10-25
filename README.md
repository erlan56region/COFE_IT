<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>iFix Pro | Премиум ремонт Apple техники с гарантией</title>
    <style>
        :root {
            --primary: #0071e3;
            --primary-dark: #0056b3;
            --secondary: #6e44ff;
            --accent: #00c9a7;
            --text: #1d1d1f;
            --text-light: #86868b;
            --bg: #ffffff;
            --bg-secondary: #f5f5f7;
            --bg-dark: #1d1d1f;
            --card-bg: #ffffff;
            --shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
            --shadow-hover: 0 20px 60px rgba(0, 0, 0, 0.12);
            --border-radius: 20px;
            --transition: all 0.4s ease;
        }

        .dark-mode {
            --primary: #2997ff;
            --primary-dark: #0071e3;
            --text: #ffffff;
            --text-light: #a1a1a6;
            --bg: #000000;
            --bg-secondary: #1d1d1f;
            --card-bg: #1d1d1f;
            --shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
            --shadow-hover: 0 20px 60px rgba(0, 0, 0, 0.4);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
            background-color: var(--bg);
            color: var(--text);
            line-height: 1.6;
            overflow-x: hidden;
            transition: var(--transition);
        }

        /* Loading Screen */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--bg);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.6s ease-out, visibility 0.6s ease-out;
        }

        .loading-screen.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .loader {
            width: 60px;
            height: 60px;
            border: 3px solid var(--bg-secondary);
            border-top: 3px solid var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(0, 0, 0, 0.1);
            z-index: 1000;
            transition: var(--transition);
        }

        .dark-mode header {
            background: rgba(0, 0, 0, 0.95);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 80px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 24px;
            font-weight: 700;
            color: var(--text);
            text-decoration: none;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: var(--primary);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .nav-links {
            display: flex;
            gap: 40px;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text);
            font-weight: 500;
            position: relative;
            transition: var(--transition);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: var(--transition);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .theme-toggle {
            background: none;
            border: none;
            color: var(--text);
            cursor: pointer;
            padding: 8px;
            border-radius: 50%;
            transition: var(--transition);
            font-size: 20px;
        }

        .theme-toggle:hover {
            background: var(--bg-secondary);
        }

        .cta-button {
            background: var(--primary);
            color: white;
            padding: 12px 28px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .cta-button:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
            box-shadow: var(--shadow-hover);
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, var(--bg) 0%, var(--bg-secondary) 100%);
            padding: 120px 0 80px;
        }

        .hero-content {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 80px;
            align-items: center;
        }

        .hero-text h1 {
            font-size: 3.5rem;
            font-weight: 700;
            line-height: 1.1;
            margin-bottom: 24px;
            color: var(--text);
        }

        .hero-text p {
            font-size: 1.25rem;
            color: var(--text-light);
            margin-bottom: 40px;
            max-width: 500px;
        }

        .hero-stats {
            display: flex;
            gap: 40px;
            margin-top: 60px;
        }

        .stat {
            text-align: center;
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary);
            display: block;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .hero-visual {
            position: relative;
            display: flex;
            justify-content: center;
        }

        .device-showcase {
            position: relative;
            width: 400px;
            height: 400px;
        }

        .device {
            position: absolute;
            background: var(--card-bg);
            border-radius: 24px;
            padding: 20px;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-light);
        }

        .device:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .device-1 {
            top: 0;
            left: 0;
            z-index: 3;
            animation: float 6s ease-in-out infinite;
            width: 200px;
            height: 400px;
        }

        .device-2 {
            top: 50px;
            right: 0;
            z-index: 2;
            animation: float 6s ease-in-out infinite 2s;
            width: 300px;
            height: 200px;
        }

        .device-3 {
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1;
            animation: float 6s ease-in-out infinite 4s;
            width: 150px;
            height: 150px;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        /* Services Grid */
        .services {
            padding: 120px 40px;
            background: var(--bg-secondary);
        }

        .section-header {
            text-align: center;
            max-width: 800px;
            margin: 0 auto 80px;
        }

        .section-title {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 20px;
            color: var(--text);
        }

        .section-subtitle {
            font-size: 1.25rem;
            color: var(--text-light);
            line-height: 1.6;
        }

        .services-grid {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .service-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 40px;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--accent));
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .service-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 24px;
            color: white;
            font-size: 24px;
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 16px;
            color: var(--text);
        }

        .service-card p {
            color: var(--text-light);
            margin-bottom: 24px;
        }

        .service-price {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .btn-secondary {
            background: var(--bg-secondary);
            color: var(--text);
            padding: 12px 24px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: var(--transition);
            border: 1px solid var(--text-light);
            display: inline-block;
        }

        .btn-secondary:hover {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        /* Process Section */
        .process {
            padding: 120px 40px;
            background: var(--bg);
        }

        .process-steps {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            position: relative;
        }

        .process-steps::before {
            content: '';
            position: absolute;
            top: 60px;
            left: 0;
            right: 0;
            height: 2px;
            background: var(--bg-secondary);
            z-index: 1;
        }

        .step {
            text-align: center;
            position: relative;
            z-index: 2;
        }

        .step-number {
            width: 80px;
            height: 80px;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: 700;
            margin: 0 auto 24px;
            position: relative;
        }

        .step-content {
            background: var(--card-bg);
            padding: 30px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .step h3 {
            font-size: 1.25rem;
            margin-bottom: 12px;
            color: var(--text);
        }

        .step p {
            color: var(--text-light);
        }

        /* Portfolio Section */
        .portfolio {
            padding: 120px 40px;
            background: var(--bg-secondary);
        }

        .portfolio-grid {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .portfolio-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .portfolio-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .portfolio-image {
            height: 250px;
            background-color: var(--bg);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .portfolio-image::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(0,113,227,0.1) 0%, rgba(110,68,255,0.1) 100%);
        }

        .device-model {
            font-size: 4rem;
            opacity: 0.7;
        }

        .portfolio-content {
            padding: 25px;
        }

        .portfolio-content h3 {
            font-size: 1.25rem;
            margin-bottom: 10px;
            color: var(--text);
        }

        .portfolio-content p {
            color: var(--text-light);
            margin-bottom: 15px;
            font-size: 0.95rem;
        }

        .portfolio-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 20px;
            padding-top: 15px;
            border-top: 1px solid rgba(0,0,0,0.1);
        }

        .dark-mode .portfolio-meta {
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        .portfolio-date {
            color: var(--text-light);
            font-size: 0.85rem;
        }

        .portfolio-tag {
            background: var(--primary);
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        /* CTA Section */
        .cta-section {
            padding: 120px 40px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .cta-content {
            max-width: 800px;
            margin: 0 auto;
            position: relative;
            z-index: 2;
        }

        .cta-title {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 20px;
        }

        .cta-subtitle {
            font-size: 1.25rem;
            margin-bottom: 40px;
            opacity: 0.9;
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
        }

        /* Footer */
        footer {
            background: var(--bg-dark);
            color: white;
            padding: 80px 40px 40px;
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 60px;
            margin-bottom: 60px;
        }

        .footer-column h3 {
            color: white;
            margin-bottom: 24px;
            font-size: 1.25rem;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 12px;
        }

        .footer-links a {
            color: #86868b;
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: white;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 12px;
            color: #86868b;
        }

        .social-links {
            display: flex;
            gap: 16px;
            margin-top: 24px;
        }

        .social-link {
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
            color: white;
            text-decoration: none;
        }

        .social-link:hover {
            background: var(--primary);
            transform: translateY(-2px);
        }

        .copyright {
            text-align: center;
            padding-top: 40px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #86868b;
        }

        /* Responsive */
        @media (max-width: 1024px) {
            .hero-content {
                grid-template-columns: 1fr;
                text-align: center;
                gap: 60px;
            }

            .hero-stats {
                justify-content: center;
            }

            .device-showcase {
                width: 300px;
                height: 300px;
            }
        }

        @media (max-width: 768px) {
            .nav-container {
                padding: 0 20px;
            }

            .nav-links {
                display: none;
            }

            .hero-content,
            .services,
            .process,
            .portfolio,
            .cta-section {
                padding: 80px 20px;
            }

            .section-title {
                font-size: 2.5rem;
            }

            .cta-title {
                font-size: 2.5rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .btn-secondary {
                width: 100%;
                max-width: 300px;
                text-align: center;
            }

            .hero-text h1 {
                font-size: 2.5rem;
            }

            .device-showcase {
                width: 250px;
                height: 250px;
            }

            .device-1 {
                width: 150px;
                height: 300px;
            }

            .device-2 {
                width: 200px;
                height: 150px;
            }

            .device-3 {
                width: 120px;
                height: 120px;
            }
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loader"></div>
    </div>

    <!-- Header -->
    <header>
        <div class="nav-container">
            <a href="#" class="logo">
                <div class="logo-icon">iF</div>
                iFix Pro
            </a>
            
            <ul class="nav-links">
                <li><a href="#services">Услуги</a></li>
                <li><a href="#process">Как мы работаем</a></li>
                <li><a href="#portfolio">Примеры работ</a></li>
                <li><a href="#contacts">Контакты</a></li>
            </ul>
            
            <div class="nav-actions">
                <button class="theme-toggle" id="themeToggle">🌓</button>
                <a href="tel:+78001234567" class="cta-button">
                    📞 +7 (800) 123-45-67
                </a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <div class="hero-text">
                <h1>Ремонт Apple техники с гарантией 2 года</h1>
                <p>Профессиональный сервисный центр с выездным ремонтом. Используем только оригинальные запчасти и современное оборудование.</p>
                <div class="cta-buttons">
                    <a href="#services" class="cta-button">Наши услуги</a>
                    <a href="#contacts" class="btn-secondary">Вызвать мастера</a>
                </div>
                <div class="hero-stats">
                    <div class="stat">
                        <span class="stat-number">15 000+</span>
                        <span class="stat-label">Устройств отремонтировано</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number">98%</span>
                        <span class="stat-label">Довольных клиентов</span>
                    </div>
                    <div class="stat">
                        <span class="stat-number">45 мин</span>
                        <span class="stat-label">Среднее время ремонта</span>
                    </div>
                </div>
            </div>
            <div class="hero-visual">
                <div class="device-showcase">
                    <div class="device device-1">iPhone</div>
                    <div class="device device-2">MacBook</div>
                    <div class="device device-3">Watch</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <div class="section-header">
            <h2 class="section-title">Наши услуги</h2>
            <p class="section-subtitle">Полный спектр услуг по ремонту техники Apple с гарантией качества и использованием оригинальных запчастей</p>
        </div>
        <div class="services-grid">
            <div class="service-card">
                <div class="service-icon">📱</div>
                <h3>Ремонт iPhone</h3>
                <p>Замена экрана, аккумулятора, динамиков, камеры и других компонентов. Диагностика и восстановление после воды.</p>
                <div class="service-price">от 1 990 ₽</div>
                <a href="#" class="btn-secondary">Подробнее</a>
            </div>
            <div class="service-card">
                <div class="service-icon">💻</div>
                <h3>Ремонт MacBook</h3>
                <p>Замена клавиатуры, матрицы, ремонт материнской платы, чистка от пыли, замена термопасты, апгрейд комплектующих.</p>
                <div class="service-price">от 3 990 ₽</div>
                <a href="#" class="btn-secondary">Подробнее</a>
            </div>
            <div class="service-card">
                <div class="service-icon">⌚️</div>
                <h3>Ремонт Apple Watch</h3>
                <p>Замена дисплея, корпуса, аккумулятора, ремонт модуля связи, восстановление после попадания воды.</p>
                <div class="service-price">от 2 490 ₽</div>
                <a href="#" class="btn-secondary">Подробнее</a>
            </div>
            <div class="service-card">
                <div class="service-icon">🎧</div>
                <h3>Ремонт AirPods</h3>
                <p>Замена кейса, наушников, ремонт платы зарядки, чистка микрофонов, восстановление аккумулятора.</p>
                <div class="service-price">от 1 490 ₽</div>
                <a href="#" class="btn-secondary">Подробнее</a>
            </div>
            <div class="service-card">
                <div class="service-icon">🔄</div>
                <h3>Восстановление данных</h3>
                <p>Восстановление данных после повреждения, удаления или сбоя системы. Работаем с любыми носителями информации.</p>
                <div class="service-price">от 2 990 ₽</div>
                <a href="#" class="btn-secondary">Подробнее</a>
            </div>
            <div class="service-card">
                <div class="service-icon">🏠</div>
                <h3>Выездной ремонт</h3>
                <p>Мастер приедет к вам в удобное время и место. Полный комплекс услуг с выездом по всему городу.</p>
                <div class="service-price">от 1 000 ₽</div>
                <a href="#" class="btn-secondary">Подробнее</a>
            </div>
        </div>
    </section>

    <!-- Process Section -->
    <section class="process" id="process">
        <div class="section-header">
            <h2 class="section-title">Как мы работаем</h2>
            <p class="section-subtitle">Простой и прозрачный процесс ремонта, который экономит ваше время и гарантирует качество</p>
        </div>
        <div class="process-steps">
            <div class="step">
                <div class="step-number">1</div>
                <div class="step-content">
                    <h3>Заявка</h3>
                    <p>Оставьте заявку на сайте или позвоните нам для записи на диагностику</p>
                </div>
            </div>
            <div class="step">
                <div class="step-number">2</div>
                <div class="step-content">
                    <h3>Диагностика</h3>
                    <p>Бесплатная диагностика устройства для точного определения проблемы</p>
                </div>
            </div>
            <div class="step">
                <div class="step-number">3</div>
                <div class="step-content">
                    <h3>Ремонт</h3>
                    <p>Профессиональный ремонт с использованием оригинальных запчастей</p>
                </div>
            </div>
            <div class="step">
                <div class="step-number">4</div>
                <div class="step-content">
                    <h3>Готово</h3>
                    <p>Тестирование устройства и передача его вам с гарантией на работу</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section class="portfolio" id="portfolio">
        <div class="section-header">
            <h2 class="section-title">Примеры работ</h2>
            <p class="section-subtitle">Реальные кейсы ремонта Apple техники, выполненные нашими специалистами</p>
        </div>
        <div class="portfolio-grid">
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <div class="device-model">📱</div>
                </div>
                <div class="portfolio-content">
                    <h3>Замена экрана iPhone 14 Pro</h3>
                    <p>Клиент уронил телефон, в результате чего появились трещины на дисплее. Выполнена замена оригинального OLED-экрана с сохранением True Tone.</p>
                    <div class="portfolio-meta">
                        <span class="portfolio-date">15 января 2025</span>
                        <span class="portfolio-tag">Выполнено</span>
                    </div>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <div class="device-model">💻</div>
                </div>
                <div class="portfolio-content">
                    <h3>Ремонт MacBook Pro 16" после залития</h3>
                    <p>Ноутбук пострадал от пролитого кофе. Выполнена чистка материнской платы, замена клавиатуры и трекпада. Устройство восстановлено полностью.</p>
                    <div class="portfolio-meta">
                        <span class="portfolio-date">10 января 2025</span>
                        <span class="portfolio-tag">Выполнено</span>
                    </div>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <div class="device-model">⌚️</div>
                </div>
                <div class="portfolio-content">
                    <h3>Замена аккумулятора Apple Watch Series 7</h3>
                    <p>Часы быстро разряжались. Установлен новый оригинальный аккумулятор. Время работы восстановлено до заводских показателей.</p>
                    <div class="portfolio-meta">
                        <span class="portfolio-date">8 января 2025</span>
                        <span class="portfolio-tag">Выполнено</span>
                    </div>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <div class="device-model">🎧</div>
                </div>
                <div class="portfolio-content">
                    <h3>Ремонт AirPods Pro 2</h3>
                    <p>Правый наушник перестал работать. Диагностика показала проблему с платой. Выполнен ремонт с сохранением шумоподавления.</p>
                    <div class="portfolio-meta">
                        <span class="portfolio-date">5 января 2025</span>
                        <span class="portfolio-tag">Выполнено</span>
                    </div>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <div class="device-model">📱</div>
                </div>
                <div class="portfolio-content">
                    <h3>Восстановление данных с поврежденного iPhone 13</h3>
                    <p>Устройство не включалось после падения в воду. Удалось восстановить все важные данные: фото, контакты, сообщения.</p>
                    <div class="portfolio-meta">
                        <span class="portfolio-date">3 января 2025</span>
                        <span class="portfolio-tag">Выполнено</span>
                    </div>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <div class="device-model">💻</div>
                </div>
                <div class="portfolio-content">
                    <h3>Апгрейд MacBook Air M1</h3>
                    <p>Клиенту требовалось увеличить объем памяти. Выполнена замена SSD на 1ТБ с сохранением всех данных и гарантии на работу.</p>
                    <div class="portfolio-meta">
                        <span class="portfolio-date">28 декабря 2024</span>
                        <span class="portfolio-tag">Выполнено</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section" id="contacts">
        <div class="cta-content">
            <h2 class="cta-title">Готовы починить ваше устройство?</h2>
            <p class="cta-subtitle">Свяжитесь с нами прямо сейчас и получите бесплатную диагностику и консультацию специалиста</p>
            <div class="cta-buttons">
                <a href="tel:+78001234567" class="cta-button">Позвонить</a>
                <a href="#contacts" class="btn-secondary">Записаться онлайн</a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
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
                <ul class="footer-links">
                    <li><a href="#">Ремонт iPhone</a></li>
                    <li><a href="#">Ремонт MacBook</a></li>
                    <li><a href="#">Ремонт iPad</a></li>
                    <li><a href="#">Ремонт Apple Watch</a></li>
                    <li><a href="#">Ремонт AirPods</a></li>
                </ul>
            </div>
            <div class="footer-column">
                <h3>Компания</h3>
                <ul class="footer-links">
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
                        📞 +7 (800) 123-45-67
                    </div>
                    <div class="contact-item">
                        ✉️ info@ifixpro.ru
                    </div>
                    <div class="contact-item">
                        📍 г. Москва, ул. Примерная, д. 123
                    </div>
                    <div class="contact-item">
                        🕒 Пн-Вс: 10:00 - 20:00
                    </div>
                </div>
            </div>
        </div>
        <div class="copyright">
            <p>&copy; 2025 iFix Pro. Все права защищены.</p>
        </div>
    </footer>

    <script>
        // Loading screen
        window.addEventListener('load', () => {
            setTimeout(() => {
                const loadingScreen = document.getElementById('loadingScreen');
                if (loadingScreen) {
                    loadingScreen.classList.add('hidden');
                }
            }, 1000);
        });

        // Theme toggle
        const themeToggle = document.getElementById('themeToggle');
        
        // Check for saved theme or prefered scheme
        const currentTheme = localStorage.getItem('theme') || 'light';
        
        if (currentTheme === 'dark') {
            document.body.classList.add('dark-mode');
            themeToggle.textContent = '☀️';
        } else {
            themeToggle.textContent = '🌓';
        }
        
        themeToggle.addEventListener('click', () => {
            document.body.classList.toggle('dark-mode');
            const theme = document.body.classList.contains('dark-mode') ? 'dark' : 'light';
            localStorage.setItem('theme', theme);
            
            // Update button icon
            if (theme === 'dark') {
                themeToggle.textContent = '☀️';
            } else {
                themeToggle.textContent = '🌓';
            }
        });

        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    // Calculate position considering fixed header
                    const headerHeight = document.querySelector('header').offsetHeight;
                    const targetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - headerHeight;
                    
                    window.scrollTo({
                        top: targetPosition,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Header background on scroll
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 100) {
                header.style.background = 'rgba(255, 255, 255, 0.98)';
                if (document.body.classList.contains('dark-mode')) {
                    header.style.background = 'rgba(0, 0, 0, 0.98)';
                }
            } else {
                header.style.background = 'rgba(255, 255, 255, 0.95)';
                if (document.body.classList.contains('dark-mode')) {
                    header.style.background = 'rgba(0, 0, 0, 0.95)';
                }
            }
        });

        // Add animation on scroll for elements
        const animateOnScroll = () => {
            const elements = document.querySelectorAll('.service-card, .step, .stat, .portfolio-card');
            
            elements.forEach(element => {
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < window.innerHeight - elementVisible) {
                    element.style.opacity = "1";
                    element.style.transform = "translateY(0)";
                }
            });
        };

        // Initialize elements for animation
        document.querySelectorAll('.service-card, .step, .stat, .portfolio-card').forEach(element => {
            element.style.opacity = "0";
            element.style.transform = "translateY(30px)";
            element.style.transition = "opacity 0.6s ease, transform 0.6s ease";
        });

        // Listen for scroll events
        window.addEventListener('scroll', animateOnScroll);
        // Initial check
        animateOnScroll();
    </script>
</body>
</html>
