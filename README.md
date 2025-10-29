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
            --header-height: 80px;
            --ease-out-quint: cubic-bezier(0.22, 1, 0.36, 1);
            --success-color: #34C759;
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
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
        }

        /* Header */
        .header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
            background-color: var(--primary-color);
            z-index: 1000;
            height: var(--header-height);
            border-bottom: 1px solid var(--gray-color);
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--text-color);
        }

        .logo i {
            color: var(--accent-color);
        }

        .nav-buttons {
            display: flex;
            gap: 1rem;
        }

        .theme-toggle, .contact-btn {
            background: transparent;
            border: 2px solid var(--accent-color);
            padding: 10px 20px;
            border-radius: 25px;
            color: var(--accent-color);
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .contact-btn {
            background: var(--accent-color);
            color: white;
        }

        .theme-toggle:hover, .contact-btn:hover {
            transform: translateY(-2px);
        }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 4rem 0;
        }

        .hero h1 {
            font-size: 3rem;
            font-weight: 800;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero p {
            font-size: 1.3rem;
            color: var(--gray-color);
            max-width: 700px;
            margin: 0 auto 2rem;
        }

        .features {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 2rem;
        }

        .feature {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 1rem 1.5rem;
            background: var(--card-bg);
            border-radius: 15px;
        }

        /* Premium Features */
        .premium-features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 2rem;
            margin: 4rem 0;
        }

        .premium-card {
            background: var(--card-bg);
            border-radius: 24px;
            padding: 2.5rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .premium-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-color), #5856D6);
        }

        .premium-icon {
            width: 80px;
            height: 80px;
            margin: 0 auto 1.5rem;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            color: white;
        }

        .premium-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        .premium-card p {
            color: var(--gray-color);
            margin-bottom: 2rem;
        }

        .premium-badge {
            display: inline-block;
            background: var(--success-color);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
        }

        .premium-list {
            list-style: none;
            text-align: left;
            margin-bottom: 2rem;
        }

        .premium-list li {
            margin-bottom: 0.8rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .premium-list i {
            color: var(--success-color);
        }

        .premium-button {
            width: 100%;
            padding: 14px;
            background: var(--accent-color);
            color: white;
            border: none;
            border-radius: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .premium-button:hover {
            background: #0056CC;
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
            transition: transform 0.3s ease;
        }

        .service-card:hover {
            transform: translateY(-5px);
        }

        .service-image {
            width: 100%;
            height: 220px;
            background: linear-gradient(135deg, var(--accent-color), #5856D6);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 3rem;
        }

        .service-info {
            padding: 1.5rem;
        }

        .service-name {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .service-description {
            color: var(--gray-color);
            margin-bottom: 1.5rem;
        }

        .service-price {
            font-size: 1.4rem;
            font-weight: 800;
            color: var(--accent-color);
            margin-bottom: 1.5rem;
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
        }

        /* Portfolio Section */
        .portfolio {
            margin-top: 6rem;
            padding: 4rem 0;
        }

        .portfolio h2 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: var(--text-color);
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .portfolio-item {
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 8px 30px rgba(0,0,0,0.12);
            transition: all 0.3s ease;
            background: var(--card-bg);
        }

        .portfolio-item:hover {
            transform: translateY(-5px);
        }

        .portfolio-image {
            width: 100%;
            height: 250px;
            object-fit: cover;
            display: block;
        }

        .portfolio-info {
            padding: 1.5rem;
        }

        .portfolio-title {
            font-size: 1.4rem;
            margin-bottom: 1rem;
            color: var(--text-color);
        }

        .portfolio-description {
            color: var(--gray-color);
            line-height: 1.6;
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
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }

        .modal-content {
            background: var(--primary-color);
            padding: 2rem;
            border-radius: 24px;
            max-width: 500px;
            width: 100%;
            position: relative;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-large {
            max-width: 600px;
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
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid var(--card-bg);
            border-radius: 12px;
            background: var(--primary-color);
            color: var(--text-color);
            font-size: 1rem;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--accent-color);
        }

        .form-row {
            display: flex;
            gap: 1rem;
        }

        .form-row .form-group {
            flex: 1;
        }

        /* Footer */
        .footer {
            margin-top: 6rem;
            padding: 3rem 0;
            border-top: 1px solid var(--gray-color);
            text-align: center;
            color: var(--gray-color);
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin: 2rem 0;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 1rem 1.2rem;
            background: var(--card-bg);
            border-radius: 15px;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .contact-item:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .contact-link {
            color: inherit;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .contact-link:hover {
            color: var(--accent-color);
        }

        /* Clickable phone and email styles */
        .clickable-contact {
            cursor: pointer;
            transition: color 0.3s ease;
        }

        .clickable-contact:hover {
            color: var(--accent-color);
        }

        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .features {
                flex-direction: column;
            }
            
            .premium-features {
                grid-template-columns: 1fr;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
            
            .portfolio-grid {
                grid-template-columns: 1fr;
            }
            
            .contact-info {
                flex-direction: column;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }

            .portfolio h2 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <header class="header" id="mainHeader">
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
    
    <div class="container">
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

        <!-- Premium Features -->
        <section class="premium-features">
            <div class="premium-card">
                <div class="premium-icon">
                    <i class="fas fa-user-cog"></i>
                </div>
                <div class="premium-badge">Выезд специалиста</div>
                <h3>Выезд инженера на дом или в офис</h3>
                <p>Наш специалист приедет к вам в удобное время для диагностики и ремонта на месте</p>
                <ul class="premium-list">
                    <li><i class="fas fa-check"></i> Бесплатный выезд по городу</li>
                    <li><i class="fas fa-check"></i> Работаем 7 дней в неделю</li>
                    <li><i class="fas fa-check"></i> Диагностика на месте за 15 минут</li>
                    <li><i class="fas fa-check"></i> Срочный выезд в течение часа</li>
                </ul>
                <button class="premium-button" id="engineerCallBtn">
                    <i class="fas fa-calendar-check"></i>
                    Вызвать инженера
                </button>
            </div>

            <div class="premium-card">
                <div class="premium-icon">
                    <i class="fas fa-bolt"></i>
                </div>
                <div class="premium-badge">Мгновенная оплата</div>
                <h3>Оплата в один клик</h3>
                <p>Оплачивайте услуги моментально без лишних действий и ожиданий</p>
                <ul class="premium-list">
                    <li><i class="fas fa-check"></i> Безопасные платежи</li>
                    <li><i class="fas fa-check"></i> Мгновенное подтверждение</li>
                    <li><i class="fas fa-check"></i> Все виды карт и электронные кошельки</li>
                    <li><i class="fas fa-check"></i> Сохранение платежных данных</li>
                </ul>
                <button class="premium-button" id="quickPayBtn">
                    <i class="fas fa-credit-card"></i>
                    Оплатить онлайн
                </button>
            </div>
        </section>
        
        <main>
            <div class="services-grid" id="servicesGrid">
                <!-- Services will be loaded here -->
            </div>
        </main>

        <!-- Portfolio Section -->
        <section class="portfolio" id="portfolio">
            <h2>Примеры наших работ</h2>
            <div class="portfolio-grid" id="portfolioGrid">
                <!-- Portfolio items will be loaded here -->
            </div>
        </section>
        
        <footer class="footer">
            <div class="contact-info">
                <div class="contact-item" onclick="callPhone('+74951234567')">
                    <i class="fas fa-clock"></i>
                    <span>Пн-Вс: 9:00-21:00</span>
                </div>
                <div class="contact-item" onclick="callPhone('+74951234567')">
                    <i class="fas fa-phone"></i>
                    <span class="clickable-contact">+7 (495) 123-45-67</span>
                </div>
                <div class="contact-item" onclick="sendEmail('info@appleservice.pro')">
                    <i class="fas fa-envelope"></i>
                    <span class="clickable-contact">info@appleservice.pro</span>
                </div>
                <div class="contact-item" onclick="openMap()">
                    <i class="fas fa-map-marker-alt"></i>
                    <span class="clickable-contact">Москва, ул. Тверская, 15</span>
                </div>
            </div>
            <p>© 2025 Apple Service Pro. Мы не являемся официальным представителем Apple Inc.</p>
        </footer>
    </div>

    <!-- Contact Modal -->
    <div class="modal" id="contactModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Связаться с нами</h3>
                <button class="modal-close" id="modalClose">&times;</button>
            </div>
            <div class="contact-info">
                <div class="contact-item" onclick="callPhone('+74951234567')">
                    <i class="fas fa-phone"></i>
                    <span class="clickable-contact">+7 (495) 123-45-67</span>
                </div>
                <div class="contact-item" onclick="sendEmail('info@appleservice.pro')">
                    <i class="fas fa-envelope"></i>
                    <span class="clickable-contact">info@appleservice.pro</span>
                </div>
                <div class="contact-item" onclick="openMap()">
                    <i class="fas fa-map-marker-alt"></i>
                    <span class="clickable-contact">Москва, ул. Тверская, 15</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <span>Пн-Вс: 9:00-21:00</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Engineer Call Modal -->
    <div class="modal" id="engineerModal">
        <div class="modal-content modal-large">
            <div class="modal-header">
                <h3>Вызов инженера на дом</h3>
                <button class="modal-close" id="engineerModalClose">&times;</button>
            </div>
            <form id="engineerForm">
                <div class="form-group">
                    <label for="clientName">Ваше имя *</label>
                    <input type="text" id="clientName" name="clientName" required placeholder="Иван Иванов">
                </div>
                
                <div class="form-group">
                    <label for="clientPhone">Телефон *</label>
                    <input type="tel" id="clientPhone" name="clientPhone" required placeholder="+7 (999) 123-45-67">
                </div>
                
                <div class="form-group">
                    <label for="clientEmail">Email</label>
                    <input type="email" id="clientEmail" name="clientEmail" placeholder="ivan@example.com">
                </div>
                
                <div class="form-group">
                    <label for="clientAddress">Адрес выезда *</label>
                    <textarea id="clientAddress" name="clientAddress" rows="2" required placeholder="г. Москва, ул. Тверская, д. 15, кв. 10"></textarea>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="deviceType">Тип устройства *</label>
                        <select id="deviceType" name="deviceType" required>
                            <option value="">Выберите устройство</option>
                            <option value="iphone">iPhone</option>
                            <option value="macbook">MacBook</option>
                            <option value="ipad">iPad</option>
                            <option value="apple-watch">Apple Watch</option>
                            <option value="airpods">AirPods</option>
                            <option value="imac">iMac</option>
                            <option value="other">Другое</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="deviceModel">Модель устройства</label>
                        <input type="text" id="deviceModel" name="deviceModel" placeholder="iPhone 14 Pro">
                    </div>
                </div>

                <div class="form-group">
                    <label for="problemDescription">Описание проблемы *</label>
                    <textarea id="problemDescription" name="problemDescription" rows="4" placeholder="Опишите проблему с вашим устройством..." required></textarea>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="preferredDate">Предпочтительная дата *</label>
                        <input type="date" id="preferredDate" name="preferredDate" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="preferredTime">Предпочтительное время *</label>
                        <select id="preferredTime" name="preferredTime" required>
                            <option value="">Выберите время</option>
                            <option value="09:00-11:00">09:00 - 11:00</option>
                            <option value="11:00-13:00">11:00 - 13:00</option>
                            <option value="13:00-15:00">13:00 - 15:00</option>
                            <option value="15:00-17:00">15:00 - 17:00</option>
                            <option value="17:00-19:00">17:00 - 19:00</option>
                            <option value="19:00-21:00">19:00 - 21:00</option>
                        </select>
                    </div>
                </div>

                <div class="form-group">
                    <label for="additionalNotes">Дополнительные пожелания</label>
                    <textarea id="additionalNotes" name="additionalNotes" rows="2" placeholder="Особые требования или комментарии..."></textarea>
                </div>

                <div class="form-group">
                    <label style="display: flex; align-items: flex-start; gap: 10px; font-weight: normal; cursor: pointer;">
                        <input type="checkbox" name="agreeTerms" required style="margin-top: 2px;">
                        <span>Я согласен на обработку персональных данных и с <a href="#" style="color: var(--accent-color);">условиями сервиса</a> *</span>
                    </label>
                </div>

                <button type="submit" class="premium-button">
                    <i class="fas fa-paper-plane"></i>
                    Заказать выезд инженера
                </button>
            </form>
        </div>
    </div>

    <script>
        // Данные услуг
        const APPLE_SERVICES = [
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
        ];

        // Данные портфолио
        const PORTFOLIO_ITEMS = [
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
            }
        ];

        // Функции для контактов
        function callPhone(phoneNumber) {
            if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
                // Мобильное устройство - звоним
                window.location.href = `tel:${phoneNumber}`;
            } else {
                // Компьютер - показываем номер
                alert(`Позвоните нам: ${phoneNumber}`);
            }
        }

        function sendEmail(emailAddress) {
            if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
                // Мобильное устройство - открываем почтовое приложение
                window.location.href = `mailto:${emailAddress}`;
            } else {
                // Компьютер - открываем почтовый клиент
                window.location.href = `mailto:${emailAddress}?subject=Запрос с сайта Apple Service Pro&body=Здравствуйте! Я заинтересован в ваших услугах.`;
            }
        }

        function openMap() {
            const address = "Москва, ул. Тверская, 15";
            if (/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
                // Мобильное устройство - открываем карты
                window.open(`https://yandex.ru/maps/?text=${encodeURIComponent(address)}`, '_blank');
            } else {
                // Компьютер - открываем Яндекс Карты
                window.open(`https://yandex.ru/maps/?text=${encodeURIComponent(address)}`, '_blank');
            }
        }

        // Инициализация приложения
        document.addEventListener('DOMContentLoaded', function() {
            // Загрузка услуг
            loadServices();
            
            // Загрузка портфолио
            loadPortfolio();
            
            // Настройка обработчиков событий
            setupEventListeners();
            
            // Настройка формы выезда инженера
            setupEngineerForm();
        });

        function loadServices() {
            const servicesGrid = document.getElementById('servicesGrid');
            servicesGrid.innerHTML = '';

            APPLE_SERVICES.forEach(service => {
                const serviceCard = document.createElement('div');
                serviceCard.className = 'service-card';
                
                serviceCard.innerHTML = `
                    <div class="service-image" style="background: ${service.color}">
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
                
                servicesGrid.appendChild(serviceCard);
            });

            // Добавляем обработчики для кнопок услуг
            document.querySelectorAll('.service-button').forEach(button => {
                button.addEventListener('click', function() {
                    const serviceName = this.getAttribute('data-service');
                    openContactModal();
                    console.log('Выбрана услуга:', serviceName);
                });
            });
        }

        function loadPortfolio() {
            const portfolioGrid = document.getElementById('portfolioGrid');
            portfolioGrid.innerHTML = '';

            PORTFOLIO_ITEMS.forEach(item => {
                const portfolioItem = document.createElement('div');
                portfolioItem.className = 'portfolio-item';
                
                portfolioItem.innerHTML = `
                    <img class="portfolio-image" 
                         src="${item.image}" 
                         alt="${item.title}"
                         loading="lazy">
                    <div class="portfolio-info">
                        <h3 class="portfolio-title">${item.title}</h3>
                        <p class="portfolio-description">${item.description}</p>
                        <div style="margin-top: 0.5rem; font-size: 0.9rem; color: var(--accent-color);">
                            <i class="fas fa-tag"></i> ${item.category}
                        </div>
                    </div>
                `;
                
                portfolioGrid.appendChild(portfolioItem);
            });
        }

        function setupEventListeners() {
            // Переключение темы
            document.getElementById('themeToggle').addEventListener('click', toggleTheme);
            
            // Модальные окна
            document.getElementById('contactBtn').addEventListener('click', openContactModal);
            document.getElementById('modalClose').addEventListener('click', closeContactModal);
            document.getElementById('engineerCallBtn').addEventListener('click', openEngineerModal);
            document.getElementById('engineerModalClose').addEventListener('click', closeEngineerModal);
            document.getElementById('quickPayBtn').addEventListener('click', openQuickPayModal);
            
            // Закрытие модальных окон по клику на фон
            document.getElementById('contactModal').addEventListener('click', function(e) {
                if (e.target === this) closeContactModal();
            });
            
            document.getElementById('engineerModal').addEventListener('click', function(e) {
                if (e.target === this) closeEngineerModal();
            });
        }

        function setupEngineerForm() {
            const form = document.getElementById('engineerForm');
            const dateInput = document.getElementById('preferredDate');
            
            // Устанавливаем минимальную дату (завтра)
            const tomorrow = new Date();
            tomorrow.setDate(tomorrow.getDate() + 1);
            const minDate = tomorrow.toISOString().split('T')[0];
            dateInput.min = minDate;
            
            form.addEventListener('submit', function(e) {
                e.preventDefault();
                
                // Проверка согласия с условиями
                const agreeCheckbox = document.querySelector('input[name="agreeTerms"]');
                if (!agreeCheckbox.checked) {
                    alert('Пожалуйста, согласитесь с условиями обработки персональных данных');
                    return;
                }

                const formData = new FormData(this);
                const data = Object.fromEntries(formData);
                
                console.log('Заявка на выезд инженера:', data);
                alert('Заявка успешно отправлена! Мы свяжемся с вами в течение 15 минут.');
                
                closeEngineerModal();
                this.reset();
            });

            // Маска для телефона
            const phoneInput = document.getElementById('clientPhone');
            phoneInput.addEventListener('input', function(e) {
                let x = e.target.value.replace(/\D/g, '').match(/(\d{0,1})(\d{0,3})(\d{0,3})(\d{0,2})(\d{0,2})/);
                e.target.value = !x[2] ? x[1] : '+' + x[1] + ' (' + x[2] + (x[3] ? ') ' + x[3] + (x[4] ? '-' + x[4] : '') + (x[5] ? '-' + x[5] : '') : '');
            });
        }

        function toggleTheme() {
            document.body.classList.toggle('dark-theme');
            const themeToggle = document.getElementById('themeToggle');
            const isDark = document.body.classList.contains('dark-theme');
            
            themeToggle.innerHTML = isDark 
                ? '<i class="fas fa-sun"></i> Светлая тема'
                : '<i class="fas fa-moon"></i> Тёмная тема';
                
            localStorage.setItem('theme', isDark ? 'dark' : 'light');
        }

        function openContactModal() {
            document.getElementById('contactModal').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeContactModal() {
            document.getElementById('contactModal').style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        function openEngineerModal() {
            document.getElementById('engineerModal').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeEngineerModal() {
            document.getElementById('engineerModal').style.display = 'none';
            document.body.style.overflow = 'auto';
        }

        function openQuickPayModal() {
            alert('Функция оплаты в один клик будет доступна в ближайшее время!');
        }

        // Загрузка темы из localStorage
        const savedTheme = localStorage.getItem('theme');
        if (savedTheme === 'dark') {
            document.body.classList.add('dark-theme');
            document.getElementById('themeToggle').innerHTML = '<i class="fas fa-sun"></i> Светлая тема';
        }
    </script>
</body>
</html>
