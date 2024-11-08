<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>موقع بيع الصور - Million El</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        /* إعدادات أساسية للموقع */
        body {
            font-family: Arial, sans-serif;
            background: url('nature-background.jpg') no-repeat center center fixed;
            background-size: cover;
            margin: 0;
            padding: 0;
            direction: rtl;
            color: white;
        }

        header {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 20px;
            text-align: center;
            border-bottom: 5px solid #ffffff;
        }

        #header-title {
            font-size: 2.5em;
            font-weight: bold;
        }

        /* تحسين شريط التنقل */
        nav {
            display: flex;
            justify-content: center;
            background-color: rgba(0, 0, 0, 0.7);
            padding: 15px;
            flex-wrap: wrap;
        }

        nav a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            font-size: 1em;
            font-weight: 500;
            text-transform: uppercase;
            padding: 5px 0;
        }

        nav a:hover {
            color: #f2b600;
            border-bottom: 2px solid #f2b600;
        }

        /* شريط البحث */
        .search-bar {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .search-bar input {
            padding: 10px;
            width: 80%;
            max-width: 500px;
            font-size: 1em;
            border: 2px solid #ddd;
            border-radius: 8px;
            margin-right: 10px;
        }

        .search-bar button {
            padding: 10px;
            background-color: #f2b600;
            color: white;
            font-size: 1em;
            border: none;
            border-radius: 8px;
            cursor: pointer;
        }

        .search-bar button:hover {
            background-color: #e29b00;
        }

        /* فئات الصور المميزة */
        .featured-images {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 30px;
        }

        .image-card {
            width: 90%;
            max-width: 300px;
            margin: 15px;
            background-color: rgba(255, 255, 255, 0.8);
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s;
        }

        .image-card img {
            width: 100%;
            border-radius: 8px;
        }

        .image-card:hover {
            transform: scale(1.05);
        }

        .image-card h3 {
            text-align: center;
            margin: 10px 0;
            font-size: 1.2em;
        }

        .rating {
            display: flex;
            justify-content: center;
            margin: 10px 0;
        }

        .rating span {
            margin: 0 3px;
            color: gold;
        }

        button.buy-btn {
            width: 100%;
            padding: 10px;
            background-color: #f2b600;
            border: none;
            border-radius: 8px;
            cursor: pointer;
        }

        button.buy-btn:hover {
            background-color: #e29b00;
        }

        /* نافذة منبثقة */
        .popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
        }

        .popup-content {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            text-align: center;
            color: black;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
        }

        footer {
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            text-align: center;
            padding: 15px;
            position: relative;
            bottom: 0;
            width: 100%;
        }

        /* تحسين التوافق مع الأجهزة الصغيرة */
        @media (max-width: 768px) {
            #header-title {
                font-size: 1.8em;
            }

            nav a {
                margin: 0 10px;
                font-size: 0.9em;
            }

            .image-card {
                width: 100%;
                margin: 10px 0;
            }

            .search-bar input {
                width: 100%;
                margin: 0;
                margin-bottom: 10px;
            }

            .search-bar button {
                width: 100%;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1 id="header-title">موقع Million El لبيع الصور</h1>
    </header>

    <!-- قائمة اختيار اللغة -->
    <div class="language-selector" style="text-align: center; margin-top: 20px;">
        <label for="language">اختر اللغة:</label>
        <select id="language" onchange="changeLanguage()">
            <option value="ar">العربية</option>
            <option value="en">English</option>
            <option value="es">Español</option>
            <option value="de">Deutsch</option>
            <option value="zh">中文</option>
        </select>
    </div>

    <!-- شريط التنقل -->
    <nav>
        <a href="#home" id="nav-home">الرئيسية</a>
        <a href="#shop" id="nav-shop">المنتجات</a>
        <a href="#contact" id="nav-contact">اتصل بنا</a>
        <a href="#login" id="nav-login">تسجيل الدخول</a>
        <a href="#favorites" id="nav-favorites">المفضلة</a>
    </nav>

    <!-- شريط البحث -->
    <div class="search-bar">
        <input type="text" id="search" placeholder="ابحث عن الصور..." onkeyup="searchImages()">
        <button onclick="searchImages()">🔍</button>
    </div>

    <!-- صور مميزة -->
    <section class="featured-images">
        <div class="image-card">
            <img src="image1.jpg" alt="صورة مميزة 1">
            <h3>صورة رائعة</h3>
            <div class="rating">
                <span>⭐</span><span>⭐</span><span>⭐</span><span>⭐</span><span>☆</span>
            </div>
            <button class="buy-btn">شراء الآن</button>
        </div>
        <div class="image-card">
            <img src="image2.jpg" alt="صورة مميزة 2">
            <h3>صورة ساحرة</h3>
            <div class="rating">
                <span>⭐</span><span>⭐</span><span>⭐</span><span>⭐</span><span>⭐</span>
            </div>
            <button class="buy-btn">شراء الآن</button>
        </div>
        <div class="image-card">
            <img src="image3.jpg" alt="صورة مميزة 3">
            <h3>صورة مدهشة</h3>
            <div class="rating">
                <span>⭐</span><span>⭐</span><span>⭐</span><span>☆</span><span>☆</span>
            </div>
            <button class="buy-btn">شراء الآن</button>
        </div>
    </section>

    <!-- نافذة منبثقة للترويج -->
    <div class="popup" id="promoPopup">
        <div class="popup-content">
            <h3 id="promo-message">خصم 20% على أول عملية شراء!</h3>
            <p id="promo-code">استخدم الرمز "WELCOME20" عند الشراء.</p>
            <button onclick="closePopup()">إغلاق</button>
        </div>
    </div>

    <footer>
        <p id="footer-text">© 2024 Million El. جميع الحقوق محفوظة.</p>
    </footer>

    <script>
        // وظيفة
