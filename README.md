Сайт в разработке
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ИП Рахметов А.К. - Водоснабжение и отопление</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #0056b3;
            --primary-dark: #003d82;
            --secondary: #00b894;
            --dark: #343a40;
            --light: #f8f9fa;
            --gray: #6c757d;
            --white: #ffffff;
            --black: #0a0a0a;
            --shadow: 0 5px 15px rgba(0,0,0,0.08);
            --transition: all 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            --radius: 12px;
        }
        
        /* Темная тема */
        .dark-theme {
            --primary: #4dabf7;
            --primary-dark: #339af0;
            --secondary: #00d9a5;
            --dark: #1a1a1a;
            --light: #2d2d2d;
            --gray: #a0a0a0;
            --white: #e0e0e0;
            --shadow: 0 5px 15px rgba(0,0,0,0.3);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
        }
        
        html {
            scroll-behavior: smooth;
        }
        
        body {
            color: var(--dark);
            line-height: 1.6;
            overflow-x: hidden;
            background-color: var(--white);
            transition: background-color 0.5s ease, color 0.5s ease;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        a {
            text-decoration: none;
            color: inherit;
        }
        
        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: var(--white);
            padding: 14px 28px;
            border-radius: var(--radius);
            font-weight: 600;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            font-size: 16px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 86, 179, 0.2);
        }
        
        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.7s;
        }
        
        .btn:hover::before {
            left: 100%;
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 86, 179, 0.3);
        }
        
        .btn:active {
            transform: translateY(-1px);
        }
        
        section {
            padding: 100px 0;
        }
        
        h2 {
            font-size: 42px;
            margin-bottom: 50px;
            text-align: center;
            position: relative;
            font-weight: 700;
        }
        
        h2::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            border-radius: 2px;
        }
        
        /* Переключатель темы */
        .theme-toggle {
            position: fixed;
            bottom: 25px;
            right: 25px;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary);
            color: var(--white);
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 1000;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: none;
        }
        
        .theme-toggle:hover {
            transform: scale(1.1) rotate(15deg);
        }
        
        /* Шапка */
        header {
            background-color: var(--white);
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: var(--transition);
            backdrop-filter: blur(10px);
        }
        
        header.scrolled {
            padding: 0;
            box-shadow: 0 5px 30px rgba(0,0,0,0.15);
        }
        
        .header-inner {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            transition: var(--transition);
        }
        
        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 12px;
            font-size: 32px;
        }
        
        .logo-subtitle {
            font-size: 12px;
            color: var(--gray);
            margin-top: 2px;
        }
        
        .desktop-nav ul {
            display: flex;
            list-style: none;
        }
        
        .desktop-nav ul li {
            margin-left: 30px;
            position: relative;
        }
        
        .desktop-nav ul li a {
            font-weight: 500;
            transition: var(--transition);
            padding: 5px 0;
            position: relative;
        }
        
        .desktop-nav ul li a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: var(--transition);
            border-radius: 1px;
        }
        
        .desktop-nav ul li a:hover::after {
            width: 100%;
        }
        
        .desktop-nav ul li a:hover {
            color: var(--primary);
        }
        
        .phone {
            font-weight: 700;
            font-size: 18px;
            display: flex;
            align-items: center;
        }
        
        .phone i {
            margin-right: 10px;
            color: var(--primary);
        }
        
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--primary);
            transition: var(--transition);
        }
        
        .mobile-menu-btn:hover {
            transform: scale(1.1);
        }
        
        /* Мобильная навигация */
        .mobile-nav {
            display: none;
            width: 100%;
            text-align: center;
            padding: 20px 0;
            background: var(--white);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transform: translateY(-20px);
            opacity: 0;
            transition: var(--transition);
        }
        
        .mobile-nav.active {
            display: block;
            transform: translateY(0);
            opacity: 1;
        }
        
        .mobile-nav ul {
            flex-direction: column;
            list-style: none;
        }
        
        .mobile-nav ul li {
            margin: 12px 0;
        }
        
        .mobile-nav ul li a {
            font-weight: 500;
            padding: 12px 0;
            display: block;
            transition: var(--transition);
            font-size: 18px;
        }
        
        .mobile-nav ul li a:hover {
            color: var(--primary);
            transform: translateX(5px);
        }
        
        /* Герой секция */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1600566752355-35792bedcfea?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80') no-repeat center center/cover;
            color: var(--white);
            text-align: center;
            padding: 220px 0 140px;
            margin-top: 80px;
            position: relative;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(0,86,179,0.3) 0%, rgba(0,184,148,0.3) 100%);
            z-index: 1;
        }
        
        .hero .container {
            position: relative;
            z-index: 2;
        }
        
        .hero h1 {
            font-size: 58px;
            margin-bottom: 25px;
            font-weight: 800;
            animation: fadeInUp 1s ease;
        }
        
        .hero p {
            font-size: 22px;
            margin-bottom: 45px;
            max-width: 750px;
            margin-left: auto;
            margin-right: auto;
            animation: fadeInUp 1s ease 0.2s both;
        }
        
        .hero .btn {
            animation: fadeInUp 1s ease 0.4s both;
        }
        
        /* Услуги */
        .services {
            background-color: var(--light);
        }
        
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 35px;
        }
        
        .service-card {
            background-color: var(--white);
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            transform: translateY(0);
        }
        
        .service-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }
        
        .service-img {
            height: 220px;
            overflow: hidden;
        }
        
        .service-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }
        
        .service-card:hover .service-img img {
            transform: scale(1.15);
        }
        
        .service-content {
            padding: 30px;
        }
        
        .service-content h3 {
            margin-bottom: 15px;
            font-size: 24px;
            color: var(--dark);
        }
        
        .service-content p {
            color: var(--gray);
            line-height: 1.7;
        }
        
        /* Каталог */
        .catalog-section {
            padding: 100px 0;
            background-color: var(--white);
        }
        
        .catalog-filters {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 50px;
        }
        
        .catalog-filter-btn {
            padding: 10px 24px;
            background: var(--white);
            border: 1px solid #ddd;
            border-radius: 30px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .catalog-filter-btn:hover, .catalog-filter-btn.active {
            background: var(--primary);
            color: var(--white);
            border-color: var(--primary);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 86, 179, 0.2);
        }
        
        .catalog-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .product-card {
            background: var(--white);
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            position: relative;
            transform: translateY(0);
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }
        
        .product-img {
            height: 220px;
            overflow: hidden;
            position: relative;
        }
        
        .product-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }
        
        .product-card:hover .product-img img {
            transform: scale(1.1);
        }
        
        .product-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--primary);
            color: var(--white);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            z-index: 2;
        }
        
        .product-content {
            padding: 25px;
        }
        
        .product-content h3 {
            margin-bottom: 12px;
            font-size: 20px;
            color: var(--dark);
            line-height: 1.4;
        }
        
        .product-content p {
            color: var(--gray);
            font-size: 15px;
            margin-bottom: 15px;
            min-height: 70px;
            line-height: 1.6;
        }
        
        .product-features {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }
        
        .product-feature {
            background: var(--light);
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 12px;
            color: var(--dark);
        }
        
        .product-price {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 20px;
        }
        
        .product-actions {
            display: flex;
            gap: 12px;
        }
        
        .product-actions .btn {
            flex: 1;
            padding: 12px;
            font-size: 14px;
        }
        
        .product-actions .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
            box-shadow: none;
        }
        
        .product-actions .btn-outline:hover {
            background: var(--primary);
            color: var(--white);
        }
        
        /* Модальное окно товара */
        .product-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 20px;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .product-modal.active {
            display: flex;
            opacity: 1;
        }
        
        .product-modal-content {
            background: var(--white);
            border-radius: var(--radius);
            max-width: 1000px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            transform: scale(0.9);
            transition: transform 0.3s ease;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        
        .product-modal.active .product-modal-content {
            transform: scale(1);
        }
        
        .product-modal-close {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0,0,0,0.1);
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            color: var(--gray);
            z-index: 10;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }
        
        .product-modal-close:hover {
            background: rgba(0,0,0,0.2);
            transform: rotate(90deg);
        }
        
        .product-modal-body {
            display: flex;
            flex-wrap: wrap;
        }
        
        .product-modal-img {
            flex: 1;
            min-width: 350px;
            height: 450px;
        }
        
        .product-modal-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: var(--radius) 0 0 var(--radius);
        }
        
        .product-modal-info {
            flex: 1;
            min-width: 350px;
            padding: 40px;
        }
        
        .product-modal-info h3 {
            font-size: 28px;
            margin-bottom: 20px;
            color: var(--dark);
            line-height: 1.3;
        }
        
        .product-modal-price {
            font-size: 32px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 25px;
        }
        
        .product-modal-description {
            margin-bottom: 25px;
            color: var(--gray);
            line-height: 1.7;
        }
        
        .product-modal-specs {
            margin-bottom: 30px;
        }
        
        .product-modal-specs h4 {
            margin-bottom: 15px;
            font-size: 20px;
            color: var(--dark);
        }
        
        .specs-list {
            list-style: none;
        }
        
        .specs-list li {
            padding: 10px 0;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
        }
        
        .spec-name {
            font-weight: 500;
        }
        
        .spec-value {
            color: var(--gray);
        }
        
        .product-modal-actions {
            display: flex;
            gap: 15px;
        }
        
        .product-modal-actions .btn {
            flex: 1;
            padding: 15px;
        }
        
        /* О компании */
        .about-section {
            padding: 100px 0;
        }
        
        .about {
            display: flex;
            align-items: center;
            gap: 60px;
        }
        
        .about-img {
            flex: 1;
            height: 500px;
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transform: translateX(-20px);
            opacity: 0;
            transition: all 0.8s ease;
        }
        
        .about-img.animated {
            transform: translateX(0);
            opacity: 1;
        }
        
        .about-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }
        
        .about-content {
            flex: 1;
            transform: translateX(20px);
            opacity: 0;
            transition: all 0.8s ease 0.2s;
        }
        
        .about-content.animated {
            transform: translateX(0);
            opacity: 1;
        }
        
        .about-content h2 {
            text-align: left;
        }
        
        .about-content h2::after {
            left: 0;
            transform: none;
        }
        
        .about-content p {
            margin-bottom: 20px;
            line-height: 1.7;
        }
        
        .stats {
            display: flex;
            justify-content: space-between;
            margin-top: 40px;
        }
        
        .stat-item {
            text-align: center;
            padding: 20px;
            border-radius: var(--radius);
            background: var(--light);
            transition: var(--transition);
            flex: 1;
            margin: 0 10px;
        }
        
        .stat-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        
        .stat-number {
            font-size: 42px;
            font-weight: 800;
            color: var(--primary);
            display: block;
            transition: all 1.5s ease;
        }
        
        .stat-text {
            font-size: 16px;
            color: var(--gray);
            margin-top: 10px;
        }
        
        /* Контакты */
        .contacts {
            background-color: var(--light);
        }
        
        .contacts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 40px;
        }
        
        .contact-info {
            background-color: var(--white);
            padding: 40px;
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            transition: var(--transition);
            transform: translateY(20px);
            opacity: 0;
        }
        
        .contact-info.animated {
            transform: translateY(0);
            opacity: 1;
        }
        
        .contact-info:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
        }
        
        .contact-info h3 {
            margin-bottom: 25px;
            color: var(--primary);
            font-size: 24px;
        }
        
        .contact-item {
            margin-bottom: 20px;
            display: flex;
            align-items: flex-start;
        }
        
        .contact-item i {
            margin-right: 15px;
            color: var(--primary);
            width: 20px;
            text-align: center;
            font-size: 20px;
            margin-top: 2px;
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: var(--transition);
            background: var(--white);
            color: var(--dark);
        }
        
        .form-control:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(0, 86, 179, 0.1);
            outline: none;
        }
        
        textarea.form-control {
            min-height: 120px;
            resize: vertical;
        }
        
        /* Подвал */
        footer {
            background-color: var(--dark);
            color: var(--white);
            padding: 80px 0 30px;
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 40px;
            margin-bottom: 50px;
        }
        
        .footer-column {
            flex: 1;
            min-width: 220px;
        }
        
        .footer-column h3 {
            margin-bottom: 25px;
            font-size: 20px;
            position: relative;
            padding-bottom: 12px;
        }
        
        .footer-column h3::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 40px;
            height: 3px;
            background: var(--primary);
            border-radius: 2px;
        }
        
        .footer-column ul {
            list-style: none;
        }
        
        .footer-column ul li {
            margin-bottom: 12px;
        }
        
        .footer-column ul li a {
            transition: var(--transition);
        }
        
        .footer-column ul li a:hover {
            color: var(--primary);
            padding-left: 5px;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 25px;
        }
        
        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 45px;
            height: 45px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            transition: var(--transition);
        }
        
        .social-links a:hover {
            background: var(--primary);
            transform: translateY(-3px);
        }
        
        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            font-size: 15px;
            color: rgba(255, 255, 255, 0.7);
        }
        
        /* Модальное окно */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 20px;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        
        .modal.active {
            display: flex;
            opacity: 1;
        }
        
        .modal-content {
            background: var(--white);
            border-radius: var(--radius);
            padding: 40px;
            max-width: 550px;
            width: 100%;
            position: relative;
            transform: scale(0.9);
            transition: transform 0.3s ease;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        
        .modal.active .modal-content {
            transform: scale(1);
        }
        
        .close-modal {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0,0,0,0.1);
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            color: var(--gray);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }
        
        .close-modal:hover {
            background: rgba(0,0,0,0.2);
            transform: rotate(90deg);
        }
        
        .modal-content h3 {
            margin-bottom: 25px;
            font-size: 28px;
            color: var(--dark);
        }
        
        .notification {
            position: fixed;
            bottom: 30px;
            right: 30px;
            padding: 18px 30px;
            background: var(--primary);
            color: var(--white);
            border-radius: var(--radius);
            box-shadow: var(--shadow);
            transform: translateX(150%);
            transition: transform 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            z-index: 1000;
            font-weight: 500;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        /* Анимации */
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
        
        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        /* Адаптивность */
        @media (max-width: 1200px) {
            .container {
                max-width: 960px;
            }
        }
        
        @media (max-width: 992px) {
            .container {
                max-width: 720px;
            }
            
            .about {
                flex-direction: column;
                gap: 40px;
            }
            
            .about-content h2 {
                text-align: center;
            }
            
            .about-content h2::after {
                left: 50%;
                transform: translateX(-50%);
            }
            
            .stats {
                justify-content: space-around;
            }
            
            .product-modal-body {
                flex-direction: column;
            }
            
            .product-modal-img {
                height: 300px;
                min-width: 100%;
            }
            
            .product-modal-img img {
                border-radius: var(--radius) var(--radius) 0 0;
            }
            
            .product-modal-info {
                min-width: 100%;
            }
        }
        
        @media (max-width: 768px) {
            .container {
                max-width: 540px;
            }
            
            .desktop-nav {
                display: none;
            }
            
            .mobile-menu-btn {
                display: block;
            }
            
            .header-inner {
                flex-wrap: wrap;
            }
            
            .phone {
                margin-top: 15px;
                width: 100%;
                justify-content: center;
            }
            
            .hero h1 {
                font-size: 42px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            h2 {
                font-size: 36px;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
            
            .catalog-grid {
                grid-template-columns: 1fr;
            }
            
            .contacts-grid {
                grid-template-columns: 1fr;
            }
            
            .stats {
                flex-direction: column;
                gap: 20px;
            }
            
            .stat-item {
                margin: 0;
            }
            
            .footer-content {
                flex-direction: column;
                gap: 30px;
            }
            
            .product-modal-actions {
                flex-direction: column;
            }
        }
        
        @media (max-width: 576px) {
            .container {
                padding: 0 20px;
            }
            
            section {
                padding: 80px 0;
            }
            
            h2 {
                font-size: 32px;
            }
            
            .hero {
                padding: 180px 0 100px;
            }
            
            .hero h1 {
                font-size: 36px;
            }
            
            .catalog-filters {
                justify-content: flex-start;
                overflow-x: auto;
                padding-bottom: 10px;
            }
            
            .catalog-filter-btn {
                white-space: nowrap;
            }
            
            .product-modal-info {
                padding: 25px;
            }
            
            .modal-content {
                padding: 30px 25px;
            }
            
            .theme-toggle {
                width: 50px;
                height: 50px;
                bottom: 20px;
                right: 20px;
            }
        }
        
        @media (max-width: 400px) {
            .hero h1 {
                font-size: 32px;
            }
            
            .hero p {
                font-size: 16px;
            }
            
            .btn {
                padding: 12px 24px;
                font-size: 15px;
            }
            
            .service-content, .product-content {
                padding: 20px;
            }
            
            .contact-info {
                padding: 25px;
            }
        }
    </style>
</head>
<body>
    <!-- Шапка -->
    <header id="header">
        <div class="container">
            <div class="header-inner">
                <div class="logo">
                    <i class="fas fa-tint"></i>
                    <div>
                        ИП Рахметов А.К.
                        <div class="logo-subtitle">ИНН 561902398552</div>
                    </div>
                </div>
                <button class="mobile-menu-btn" id="mobileMenuBtn" aria-label="Открыть меню">
                    <i class="fas fa-bars"></i>
                </button>
                <nav class="desktop-nav">
                    <ul>
                        <li><a href="#services">Услуги</a></li>
                        <li><a href="#catalog">Каталог</a></li>
                        <li><a href="#about">О компании</a></li>
                        <li><a href="#contacts">Контакты</a></li>
                    </ul>
                </nav>
                <div class="phone">
                    <i class="fas fa-phone"></i>
                    +7 (3532) 123-45-67
                </div>
            </div>
            <nav class="mobile-nav" id="mobileNav">
                <ul>
                    <li><a href="#services">Услуги</a></li>
                    <li><a href="#catalog">Каталог</a></li>
                    <li><a href="#about">О компании</a></li>
                    <li><a href="#contacts">Контакты</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Герой секция -->
    <section class="hero">
        <div class="container">
            <h1>Водоснабжение и отопление</h1>
            <p>Профессиональные услуги по монтажу и обслуживанию систем водоснабжения и отопления для домов и предприятий в Оренбурге и Оренбургской области</p>
            <a href="#contacts" class="btn pulse" id="contactBtn">Связаться с нами</a>
        </div>
    </section>

    <!-- Услуги -->
    <section id="services" class="services">
        <div class="container">
            <h2>Наши услуги</h2>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-img">
                        <img src="https://images.unsplash.com/photo-1622743643089-83ae5d606c4b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Монтаж систем водоснабжения" loading="lazy">
                    </div>
                    <div class="service-content">
                        <h3>Монтаж систем водоснабжения</h3>
                        <p>Проектирование и установка систем водоснабжения для частных домов, квартир и коммерческих объектов в Оренбурге и области.</p>
                    </div>
                </div>
                <div class="service-card">
                    <div class="service-img">
                        <img src="https://images.unsplash.com/photo-1617864065587-0e5d0289c930?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Отопление" loading="lazy">
                    </div>
                    <div class="service-content">
                        <h3>Отопление</h3>
                        <p>Монтаж и обслуживание систем отопления любого типа: радиаторное, теплые полы, воздушное отопление для Оренбурга и области.</p>
                    </div>
                </div>
                <div class="service-card">
                    <div class="service-img">
                        <img src="https://images.unsplash.com/photo-1581094794321-8410e6a0d6d1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="Канализация" loading="lazy">
                    </div>
                    <div class="service-content">
                        <h3>Канализация</h3>
                        <p>Установка и ремонт канализационных систем, включая локальные очистные сооружения для Оренбурга и Оренбургской области.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Каталог -->
    <section id="catalog" class="catalog-section">
        <div class="container">
            <h2>Каталог товаров</h2>
            <div class="catalog-filters">
                <button class="catalog-filter-btn active" data-filter="all">Все товары</button>
                <button class="catalog-filter-btn" data-filter="pumps">Насосы</button>
                <button class="catalog-filter-btn" data-filter="boilers">Котлы</button>
                <button class="catalog-filter-btn" data-filter="radiators">Радиаторы</button>
                <button class="catalog-filter-btn" data-filter="pipes">Трубы и фитинги</button>
                <button class="catalog-filter-btn" data-filter="water-heaters">Водонагреватели</button>
                <button class="catalog-filter-btn" data-filter="cryology">Криология</button>
            </div>
            <div class="catalog-grid" id="catalogGrid">
                <!-- Товары будут загружены через JavaScript -->
            </div>
        </div>
    </section>

    <!-- Модальное окно товара -->
    <div class="product-modal" id="productModal">
        <div class="product-modal-content">
            <button class="product-modal-close" id="productModalClose" aria-label="Закрыть">&times;</button>
            <div class="product-modal-body">
                <div class="product-modal-img">
                    <img id="modalProductImage" src="" alt="">
                </div>
                <div class="product-modal-info">
                    <h3 id="modalProductName"></h3>
                    <div class="product-modal-price" id="modalProductPrice"></div>
                    <div class="product-modal-description" id="modalProductDescription"></div>
                    <div class="product-modal-specs">
                        <h4>Характеристики</h4>
                        <ul class="specs-list" id="modalProductSpecs">
                            <!-- Спецификации будут добавлены через JavaScript -->
                        </ul>
                    </div>
                    <div class="product-modal-actions">
                        <button class="btn" id="modalProductOrder">Заказать</button>
                        <button class="btn btn-outline" id="modalProductConsult">Консультация</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- О компании -->
    <section id="about" class="about-section">
        <div class="container">
            <div class="about">
                <div class="about-img" id="aboutImage">
                    <img src="https://images.unsplash.com/photo-1581094794321-8410e6a0d6d1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80" alt="О компании" loading="lazy">
                </div>
                <div class="about-content" id="aboutContent">
                    <h2>О компании</h2>
                    <p><strong>ИП Рахметов А.К.</strong> (ИНН 561902398552) специализируется на услугах в области водоснабжения и отопления с 2010 года. Мы предлагаем полный комплекс услуг от проектирования до монтажа и обслуживания систем в Оренбурге и Оренбургской области.</p>
                    <p>Наша команда состоит из опытных специалистов, которые используют современное оборудование и материалы для обеспечения высокого качества работ.</p>
                    <div class="stats">
                        <div class="stat-item">
                            <span class="stat-number" id="yearsCounter">0</span>
                            <span class="stat-text">Лет опыта</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number" id="projectsCounter">0</span>
                            <span class="stat-text">Выполненных проектов</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number" id="clientsCounter">0</span>
                            <span class="stat-text">Довольных клиентов</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Контакты -->
    <section id="contacts" class="contacts">
        <div class="container">
            <h2>Контакты</h2>
            <div class="contacts-grid">
                <div class="contact-info" id="contactInfo">
                    <h3>Контактная информация</h3>
                    <div class="contact-item">
                        <i class="fas fa-user-tie"></i>
                        <div><strong>ИП Рахметов А.К.</strong></div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-id-card"></i>
                        <div>ИНН: 561902398552</div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-map-marker-alt"></i>
                        <div>г. Оренбург, ул. Примерная, д. 123</div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-phone"></i>
                        <div>+7 (3532) 123-45-67</div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-envelope"></i>
                        <div>info@rahmetov-orenburg.ru</div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-clock"></i>
                        <div>Пн-Пт: 9:00-18:00</div>
                    </div>
                    <div class="contact-item">
                        <i class="fas fa-map-marked-alt"></i>
                        <div>Работаем по всему Оренбургу и области</div>
                    </div>
                    <div class="social-links">
                        <a href="#" aria-label="ВКонтакте"><i class="fab fa-vk"></i></a>
                        <a href="#" aria-label="Telegram"><i class="fab fa-telegram"></i></a>
                        <a href="#" aria-label="WhatsApp"><i class="fab fa-whatsapp"></i></a>
                        <a href="#" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
                    </div>
                </div>
                <div class="contact-info" id="contactForm">
                    <h3>Форма обратной связи</h3>
                    <form id="contact-form">
                        <div class="form-group">
                            <label for="name">Ваше имя</label>
                            <input type="text" id="name" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="phone">Ваш телефон</label>
                            <input type="tel" id="phone" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="location">Ваш населенный пункт</label>
                            <input type="text" id="location" class="form-control" placeholder="Оренбург или область">
                        </div>
                        <div class="form-group">
                            <label for="message">Сообщение</label>
                            <textarea id="message" class="form-control" rows="4"></textarea>
                        </div>
                        <button type="submit" class="btn">Отправить</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Подвал -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>Компания</h3>
                    <ul>
                        <li><a href="#about">О нас</a></li>
                        <li><a href="#services">Услуги</a></li>
                        <li><a href="#catalog">Каталог</a></li>
                        <li><a href="#contacts">Контакты</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Услуги</h3>
                    <ul>
                        <li><a href="#">Водоснабжение</a></li>
                        <li><a href="#">Отопление</a></li>
                        <li><a href="#">Канализация</a></li>
                        <li><a href="#">Криология</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Контакты</h3>
                    <ul>
                        <li><strong>ИП Рахметов А.К.</strong></li>
                        <li>ИНН: 561902398552</li>
                        <li>+7 (3532) 123-45-67</li>
                        <li>info@rahmetov-orenburg.ru</li>
                        <li>г. Оренбург, ул. Примерная, д. 123</li>
                        <li>Работаем по Оренбургу и области</li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                &copy; 2025 ИП Рахметов А.К. (ИНН 561902398552). Все права защищены. Обслуживаем Оренбург и Оренбургскую область.
            </div>
        </div>
    </footer>

    <!-- Переключатель темы -->
    <button class="theme-toggle" id="themeToggle" aria-label="Переключить тему">
        <i class="fas fa-moon" id="themeIcon"></i>
    </button>

    <!-- Модальное окно -->
    <div class="modal" id="modal">
        <div class="modal-content">
            <button class="close-modal" id="closeModal" aria-label="Закрыть">&times;</button>
            <h3>Быстрая консультация</h3>
            <form id="quick-form">
                <div class="form-group">
                    <label for="quick-name">Ваше имя</label>
                    <input type="text" id="quick-name" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="quick-phone">Ваш телефон</label>
                    <input type="tel" id="quick-phone" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="quick-location">Ваш населенный пункт</label>
                    <input type="text" id="quick-location" class="form-control" placeholder="Оренбург или область">
                </div>
                <button type="submit" class="btn">Позвоните мне</button>
            </form>
        </div>
    </div>

    <!-- Уведомление -->
    <div class="notification" id="notification">
        Сообщение отправлено успешно!
    </div>

    <script>
        // Современный движок анимаций для 2025 года
        class AnimationEngine {
            constructor() {
                this.observers = [];
                this.init();
            }
            
            init() {
                // Инициализация Intersection Observer для анимаций при скролле
                this.scrollObserver = new IntersectionObserver((entries) => {
                    entries.forEach(entry => {
                        if (entry.isIntersecting) {
                            entry.target.classList.add('animated');
                        }
                    });
                }, { threshold: 0.1 });
                
                // Наблюдаем за элементами с анимацией
                document.querySelectorAll('.about-img, .about-content, .contact-info').forEach(el => {
                    this.scrollObserver.observe(el);
                });
            }
            
            // Плавное появление элемента
            fadeIn(element, duration = 500) {
                element.style.opacity = 0;
                element.style.display = 'block';
                
                let start = null;
                const animate = (timestamp) => {
                    if (!start) start = timestamp;
                    const progress = timestamp - start;
                    const opacity = Math.min(progress / duration, 1);
                    element.style.opacity = opacity;
                    
                    if (progress < duration) {
                        requestAnimationFrame(animate);
                    }
                };
                
                requestAnimationFrame(animate);
            }
            
            // Плавное исчезновение элемента
            fadeOut(element, duration = 500) {
                let start = null;
                const initialOpacity = parseFloat(getComputedStyle(element).opacity);
                
                const animate = (timestamp) => {
                    if (!start) start = timestamp;
                    const progress = timestamp - start;
                    const opacity = Math.max(initialOpacity - (progress / duration), 0);
                    element.style.opacity = opacity;
                    
                    if (progress < duration) {
                        requestAnimationFrame(animate);
                    } else {
                        element.style.display = 'none';
                    }
                };
                
                requestAnimationFrame(animate);
            }
        }

        // Данные товаров
        const products = [
            {
                id: 1,
                name: "Насосная станция Grundfos JPBasic 3",
                description: "Автоматическая насосная станция для водоснабжения дома",
                price: "12 500 ₽",
                image: "https://images.unsplash.com/photo-1615992174118-9b8e9be025e7?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
                features: ["Автоматика", "Мощность 750 Вт", "Производительность 3 м³/ч"],
                category: "pumps",
                badge: "Хит",
                fullDescription: "Насосная станция Grundfos JPBasic 3 предназначена для автоматического водоснабжения загородных домов, дач и других объектов. Оснащена защитой от сухого хода и перегрева.",
                specifications: [
                    { name: "Производительность", value: "3 м³/ч" },
                    { name: "Напор", value: "40 м" },
                    { name: "Мощность", value: "750 Вт" },
                    { name: "Глубина всасывания", value: "8 м" },
                    { name: "Объем гидробака", value: "24 л" },
                    { name: "Материал корпуса", value: "Нержавеющая сталь" }
                ]
            },
            {
                id: 2,
                name: "Газовый котел Baxi Eco Four 24F",
                description: "Настенный двухконтурный газовый котел для отопления и ГВС",
                price: "45 800 ₽",
                image: "https://images.unsplash.com/photo-1603712610496-5368a70c7f80?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
                features: ["Двухконтурный", "КПД 93%", "Мощность 24 кВт"],
                category: "boilers",
                badge: "Акция",
                fullDescription: "Газовый котел Baxi Eco Four 24F - надежное решение для отопления и горячего водоснабжения квартиры или частного дома. Оснащен современной системой управления и защитой.",
                specifications: [
                    { name: "Мощность отопления", value: "24 кВт" },
                    { name: "Мощность ГВС", value: "24 кВт" },
                    { name: "КПД", value: "93%" },
                    { name: "Расход газа", value: "2,78 м³/ч" },
                    { name: "Температура ГВС", value: "35-60°C" },
                    { name: "Габариты", value: "730x400x299 мм" }
                ]
            },
            {
                id: 3,
                name: "Биметаллический радиатор Global Style Plus 500",
                description: "Секционный биметаллический радиатор для систем отопления",
                price: "8 200 ₽",
                image: "https://images.unsplash.com/photo-1617864065587-0e5d0289c930?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
                features: ["Биметалл", "Высота 500 мм", "Теплоотдача 185 Вт"],
                category: "radiators",
                badge: "Популярный",
                fullDescription: "Биметаллический радиатор Global Style Plus 500 сочетает в себе высокую теплоотдачу и долговечность. Подходит для систем центрального и автономного отопления.",
                specifications: [
                    { name: "Теплоотдача секции", value: "185 Вт" },
                    { name: "Межосевое расстояние", value: "500 мм" },
                    { name: "Рабочее давление", value: "35 бар" },
                    { name: "Испытательное давление", value: "52,5 бар" },
                    { name: "Объем секции", value: "0,19 л" },
                    { name: "Вес секции", value: "2,15 кг" }
                ]
            },
            {
                id: 4,
                name: "Трубы полипропиленовые Valtec PP-R 20мм",
                description: "Полипропиленовые трубы для систем отопления и водоснабжения",
                price: "85 ₽/м",
                image: "https://images.unsplash.com/photo-1558618047-3c8c76ca7d13?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2064&q=80",
                features: ["Полипропилен", "Диаметр 20 мм", "Рабочая t: 95°C"],
                category: "pipes",
                badge: "Скидка",
                fullDescription: "Полипропиленовые трубы Valtec PP-R предназначены для систем холодного и горячего водоснабжения, а также отопления. Не подвержены коррозии и имеют длительный срок службы.",
                specifications: [
                    { name: "Наружный диаметр", value: "20 мм" },
                    { name: "Толщина стенки", value: "2,8 мм" },
                    { name: "Рабочая температура", value: "95°C" },
                    { name: "Рабочее давление", value: "25 бар" },
                    { name: "Коэффициент линейного расширения", value: "0,15 мм/м°C" },
                    { name: "Теплопроводность", value: "0,24 Вт/м°C" }
                ]
            },
            {
                id: 5,
                name: "Водонагреватель Thermex Champion Silverheat 100",
                description: "Накопительный водонагреватель для обеспечения ГВС",
                price: "18 900 ₽",
                image: "https://images.unsplash.com/photo-1581093458791-8a6b22bb640e?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
                features: ["Объем 100 л", "Мощность 1,5 кВт", "Вертикальный"],
                category: "water-heaters",
                badge: "Новинка",
                fullDescription: "Накопительный водонагреватель Thermex Champion Silverheat 100 обеспечивает стабильное горячее водоснабжение для семьи из 3-4 человек. Оснащен системой защиты от коррозии.",
                specifications: [
                    { name: "Объем", value: "100 л" },
                    { name: "Мощность", value: "1,5 кВт" },
                    { name: "Нагрев до 60°C", value: "3 ч 15 мин" },
                    { name: "Максимальная температура", value: "75°C" },
                    { name: "Рабочее давление", value: "0,7-6 бар" },
                    { name: "Габариты", value: "493x970 мм" }
                ]
            },
            {
                id: 6,
                name: "Циркуляционный насос Wilo Star-RS 25/4",
                description: "Циркуляционный насос для систем отопления",
                price: "6 800 ₽",
                image: "https://images.unsplash.com/photo-1615992174118-9b8e9be025e7?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
                features: ["Три скорости", "Напор 4 м", "Производительность 3 м³/ч"],
                category: "pumps",
                badge: "",
                fullDescription: "Циркуляционный насос Wilo Star-RS 25/4 предназначен для циркуляции теплоносителя в системах отопления. Имеет три скорости работы и низкий уровень шума.",
                specifications: [
                    { name: "Производительность", value: "3 м³/ч" },
                    { name: "Напор", value: "4 м" },
                    { name: "Мощность", value: "48 Вт" },
                    { name: "Присоединительный размер", value: "1 дюйм" },
                    { name: "Максимальная температура", value: "110°C" },
                    { name: "Уровень шума", value: "< 45 дБ" }
                ]
            },
            // Товары криологии
            {
                id: 7,
                name: "Чиллер Trane CGAM 60",
                description: "Центральный холодильный агрегат для систем кондиционирования",
                price: "850 000 ₽",
                image: "https://images.unsplash.com/photo-1558618047-3c8c76ca7d13?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2064&q=80",
                features: ["Мощность 60 кВт", "Водяное охлаждение", "Энергоэффективность A++"],
                category: "cryology",
                badge: "Профессиональный",
                fullDescription: "Чиллер Trane CGAM 60 - это центральный холодильный агрегат с водяным охлаждением для систем кондиционирования и промышленного охлаждения. Обеспечивает высокую энергоэффективность и надежность.",
                specifications: [
                    { name: "Холодопроизводительность", value: "60 кВт" },
                    { name: "Потребляемая мощность", value: "18,5 кВт" },
                    { name: "Тип хладагента", value: "R410A" },
                    { name: "Уровень шума", value: "65 дБ" },
                    { name: "Габариты", value: "1800x900x1200 мм" },
                    { name: "Вес", value: "450 кг" }
                ]
            },
            {
                id: 8,
                name: "Фанкойл Carrier 42CQ",
                description: "Внутренний блок фанкойла для систем чиллер-фанкойл",
                price: "32 500 ₽",
                image: "https://images.unsplash.com/photo-1581094794321-8410e6a0d6d1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
                features: ["Кассетный тип", "Расход воздуха 1200 м³/ч", "4-х трубная система"],
                category: "cryology",
                badge: "Популярный",
                fullDescription: "Фанкойл Carrier 42CQ кассетного типа предназначен для систем чиллер-фанкойл. Обеспечивает эффективное охлаждение и нагрев воздуха в помещениях коммерческого назначения.",
                specifications: [
                    { name: "Холодопроизводительность", value: "5,8 кВт" },
                    { name: "Теплопроизводительность", value: "8,2 кВт" },
                    { name: "Расход воздуха", value: "1200 м³/ч" },
                    { name: "Уровень шума", value: "42 дБ" },
                    { name: "Габариты", value: "840x840x300 мм" },
                    { name: "Вес", value: "32 кг" }
                ]
            }
        ];

        // Инициализация движка анимаций
        const animationEngine = new AnimationEngine();

        // Функция для анимации счетчика
        function animateCounter(element, start, end, duration, suffix = '') {
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                const currentValue = Math.floor(progress * (end - start) + start);
                element.textContent = currentValue + suffix;
                if (progress < 1) {
                    window.requestAnimationFrame(step);
                }
            };
            window.requestAnimationFrame(step);
        }

        // Функция для запуска счетчиков при загрузке страницы
        function initCounters() {
            const yearsCounter = document.getElementById('yearsCounter');
            const projectsCounter = document.getElementById('projectsCounter');
            const clientsCounter = document.getElementById('clientsCounter');
            
            // Запускаем анимацию счетчиков с небольшой задержкой для лучшего эффекта
            setTimeout(() => {
                animateCounter(yearsCounter, 0, 15, 2000);
                animateCounter(projectsCounter, 0, 1200, 2500);
                animateCounter(clientsCounter, 0, 98, 1800, '%');
            }, 500);
        }

        // Инициализация каталога
        function initCatalog() {
            const catalogGrid = document.getElementById('catalogGrid');
            
            // Очистка контейнера
            catalogGrid.innerHTML = '';
            
            // Создание карточек товаров
            products.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-card';
                productCard.setAttribute('data-category', product.category);
                productCard.innerHTML = `
                    <div class="product-img">
                        <img src="${product.image}" alt="${product.name}" loading="lazy">
                        ${product.badge ? `<div class="product-badge">${product.badge}</div>` : ''}
                    </div>
                    <div class="product-content">
                        <h3>${product.name}</h3>
                        <p>${product.description}</p>
                        <div class="product-features">
                            ${product.features.map(feature => `<span class="product-feature">${feature}</span>`).join('')}
                        </div>
                        <div class="product-price">${product.price}</div>
                        <div class="product-actions">
                            <button class="btn" data-product-id="${product.id}">Подробнее</button>
                            <button class="btn btn-outline" data-product-id="${product.id}">Заказать</button>
                        </div>
                    </div>
                `;
                catalogGrid.appendChild(productCard);
            });
            
            // Инициализация фильтров каталога
            initCatalogFilters();
            
            // Инициализация обработчиков событий для кнопок товаров
            initProductButtons();
            
            // Инициализация модального окна товара
            initProductModal();
        }
        
        // Инициализация фильтров каталога
        function initCatalogFilters() {
            const filterButtons = document.querySelectorAll('.catalog-filter-btn');
            filterButtons.forEach(button => {
                button.addEventListener('click', () => {
                    // Убираем активный класс у всех кнопок
                    filterButtons.forEach(btn => btn.classList.remove('active'));
                    // Добавляем активный класс текущей кнопке
                    button.classList.add('active');
                    
                    const filter = button.getAttribute('data-filter');
                    filterCatalog(filter);
                });
            });
        }
        
        // Фильтрация каталога
        function filterCatalog(filter) {
            const productCards = document.querySelectorAll('.product-card');
            productCards.forEach(card => {
                if (filter === 'all' || card.getAttribute('data-category') === filter) {
                    card.style.display = 'block';
                    setTimeout(() => {
                        card.style.opacity = '1';
                        card.style.transform = 'translateY(0)';
                    }, 10);
                } else {
                    card.style.opacity = '0';
                    card.style.transform = 'translateY(20px)';
                    setTimeout(() => {
                        card.style.display = 'none';
                    }, 300);
                }
            });
        }
        
        // Инициализация обработчиков событий для кнопок товаров
        function initProductButtons() {
            document.addEventListener('click', (e) => {
                if (e.target.matches('.product-card .btn') || e.target.closest('.product-card .btn')) {
                    const button = e.target.matches('.btn') ? e.target : e.target.closest('.btn');
                    const productId = button.getAttribute('data-product-id');
                    
                    if (button.classList.contains('btn-outline')) {
                        // Заказ товара
                        orderProduct(productId);
                    } else {
                        // Просмотр подробной информации
                        viewProductDetails(productId);
                    }
                }
                
                // Клик по карточке товара (кроме кнопок)
                if (e.target.closest('.product-card') && !e.target.matches('.btn') && !e.target.closest('.btn')) {
                    const productCard = e.target.closest('.product-card');
                    const productId = productCard.querySelector('.btn').getAttribute('data-product-id');
                    viewProductDetails(productId);
                }
            });
        }
        
        // Просмотр детальной информации о товаре
        function viewProductDetails(productId) {
            const product = products.find(p => p.id == productId);
            if (product) {
                const modal = document.getElementById('productModal');
                const modalImage = document.getElementById('modalProductImage');
                const modalName = document.getElementById('modalProductName');
                const modalPrice = document.getElementById('modalProductPrice');
                const modalDescription = document.getElementById('modalProductDescription');
                const modalSpecs = document.getElementById('modalProductSpecs');
                
                // Заполнение модального окна данными товара
                modalImage.src = product.image;
                modalImage.alt = product.name;
                modalName.textContent = product.name;
                modalPrice.textContent = product.price;
                modalDescription.textContent = product.fullDescription;
                
                // Очистка и заполнение спецификаций
                modalSpecs.innerHTML = '';
                product.specifications.forEach(spec => {
                    const li = document.createElement('li');
                    li.innerHTML = `
                        <span class="spec-name">${spec.name}</span>
                        <span class="spec-value">${spec.value}</span>
                    `;
                    modalSpecs.appendChild(li);
                });
                
                // Открытие модального окна
                modal.classList.add('active');
                document.body.style.overflow = 'hidden';
            }
        }
        
        // Заказ товара
        function orderProduct(productId) {
            const product = products.find(p => p.id == productId);
            if (product) {
                // Открытие модального окна заказа
                openModal();
                console.log(`Заказ товара: ${product.name}`);
            }
        }
        
        // Инициализация модального окна товара
        function initProductModal() {
            const modal = document.getElementById('productModal');
            const closeButton = document.getElementById('productModalClose');
            const orderButton = document.getElementById('modalProductOrder');
            const consultButton = document.getElementById('modalProductConsult');
            
            // Закрытие модального окна
            closeButton.addEventListener('click', () => {
                closeProductModal();
            });
            
            // Заказ товара из модального окна
            orderButton.addEventListener('click', () => {
                closeProductModal();
                openModal();
            });
            
            // Консультация по товару
            consultButton.addEventListener('click', () => {
                closeProductModal();
                openModal();
            });
            
            // Закрытие по клику вне модального окна
            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    closeProductModal();
                }
            });
            
            // Закрытие по клавише Escape
            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape' && modal.classList.contains('active')) {
                    closeProductModal();
                }
            });
        }
        
        // Закрытие модального окна товара
        function closeProductModal() {
            const modal = document.getElementById('productModal');
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
        }
        
        // Базовая функциональность
        function initBaseFunctionality() {
            // Мобильное меню
            const mobileMenuBtn = document.getElementById('mobileMenuBtn');
            const mobileNav = document.getElementById('mobileNav');
            
            if (mobileMenuBtn) {
                mobileMenuBtn.addEventListener('click', () => {
                    mobileNav.classList.toggle('active');
                    mobileMenuBtn.querySelector('i').classList.toggle('fa-bars');
                    mobileMenuBtn.querySelector('i').classList.toggle('fa-times');
                });
            }
            
            // Плавная прокрутка
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href');
                    if (targetId === '#') return;
                    
                    const targetElement = document.querySelector(targetId);
                    
                    if (targetElement) {
                        const headerHeight = document.getElementById('header').offsetHeight;
                        const targetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - headerHeight;
                        
                        window.scrollTo({
                            top: targetPosition,
                            behavior: 'smooth'
                        });
                        
                        // Закрытие мобильного меню после клика
                        if (mobileNav) {
                            mobileNav.classList.remove('active');
                            mobileMenuBtn.querySelector('i').classList.add('fa-bars');
                            mobileMenuBtn.querySelector('i').classList.remove('fa-times');
                        }
                    }
                });
            });
            
            // Переключение темы
            const themeToggle = document.getElementById('themeToggle');
            const themeIcon = document.getElementById('themeIcon');
            let isDarkTheme = localStorage.getItem('darkTheme') === 'true';
            
            function applyTheme() {
                if (isDarkTheme) {
                    document.body.classList.add('dark-theme');
                    themeIcon.className = 'fas fa-sun';
                } else {
                    document.body.classList.remove('dark-theme');
                    themeIcon.className = 'fas fa-moon';
                }
            }
            
            function toggleTheme() {
                isDarkTheme = !isDarkTheme;
                localStorage.setItem('darkTheme', isDarkTheme);
                applyTheme();
            }
            
            if (themeToggle) {
                themeToggle.addEventListener('click', toggleTheme);
                applyTheme();
            }
            
            // Модальное окно
            const modal = document.getElementById('modal');
            const contactBtn = document.getElementById('contactBtn');
            const closeModal = document.getElementById('closeModal');
            
            function openModal() {
                if (modal) {
                    modal.classList.add('active');
                    document.body.style.overflow = 'hidden';
                }
            }
            
            function closeModalFunc() {
                if (modal) {
                    modal.classList.remove('active');
                    document.body.style.overflow = 'auto';
                }
            }
            
            if (contactBtn) {
                contactBtn.addEventListener('click', (e) => {
                    e.preventDefault();
                    openModal();
                });
            }
            
            if (closeModal) {
                closeModal.addEventListener('click', closeModalFunc);
            }
            
            // Закрытие по клику вне модального окна
            window.addEventListener('click', (e) => {
                if (e.target === modal) {
                    closeModalFunc();
                }
            });
            
            // Формы
            const contactForm = document.getElementById('contact-form');
            const quickForm = document.getElementById('quick-form');
            const notification = document.getElementById('notification');
            
            function showNotification() {
                if (notification) {
                    notification.classList.add('show');
                    setTimeout(() => {
                        notification.classList.remove('show');
                    }, 3000);
                }
            }
            
            if (contactForm) {
                contactForm.addEventListener('submit', (e) => {
                    e.preventDefault();
                    setTimeout(() => {
                        contactForm.reset();
                        showNotification();
                    }, 500);
                });
            }
            
            if (quickForm) {
                quickForm.addEventListener('submit', (e) => {
                    e.preventDefault();
                    setTimeout(() => {
                        quickForm.reset();
                        closeModalFunc();
                        showNotification();
                    }, 500);
                });
            }
            
            // Закрытие мобильного меню при ресайзе
            window.addEventListener('resize', () => {
                if (window.innerWidth > 768 && mobileNav) {
                    mobileNav.classList.remove('active');
                    mobileMenuBtn.querySelector('i').classList.add('fa-bars');
                    mobileMenuBtn.querySelector('i').classList.remove('fa-times');
                }
            });
            
            // Эффект скролла для header
            window.addEventListener('scroll', () => {
                const header = document.getElementById('header');
                if (window.scrollY > 50) {
                    header.classList.add('scrolled');
                } else {
                    header.classList.remove('scrolled');
                }
            });
        }
        
        // Инициализация при загрузке страницы
        document.addEventListener('DOMContentLoaded', () => {
            try {
                initBaseFunctionality();
                initCatalog();
                initCounters();
            } catch (error) {
                console.error('Ошибка инициализации:', error);
            }
        });
    </script>
</body>
</html>
