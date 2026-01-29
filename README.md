<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مشاهدتي - تطبيق المشاهدة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }
        
        body {
            background-color: #0f0f1a;
            color: #fff;
            direction: rtl;
            overflow-x: hidden;
            padding-bottom: 80px;
        }
        
        /* الشريط العلوي */
        .top-bar {
            background-color: #1a1a2e;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 20px;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            height: 70px;
            border-bottom: 1px solid #2d2d4a;
        }
        
        .logo {
            font-size: 24px;
            font-weight: 700;
            color: #ff4081;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-left: 10px;
            font-size: 26px;
        }
        
        .user-actions {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-actions i {
            font-size: 22px;
            color: #aaa;
            cursor: pointer;
            transition: color 0.3s;
        }
        
        .user-actions i:hover {
            color: #ff4081;
        }
        
        .balance-info {
            background-color: #ff4081;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        /* محتوى الصفحة */
        .main-container {
            margin-top: 70px;
            padding: 20px;
        }
        
        /* العنوان الرئيسي */
        .main-title {
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 10px;
            color: white;
        }
        
        /* قسم VIP مع الرصيد */
        .vip-balance-section {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }
        
        .balance-large {
            background-color: #ff4081;
            color: white;
            padding: 12px 25px;
            border-radius: 30px;
            font-weight: 700;
            font-size: 24px;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 5px 15px rgba(255, 64, 129, 0.3);
        }
        
        /* ميزات VIP */
        .features-section {
            margin-bottom: 40px;
        }
        
        .section-title {
            font-size: 22px;
            font-weight: 600;
            color: #ddd;
            margin-bottom: 20px;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .feature-card {
            background-color: #1a1a2e;
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: transform 0.3s, box-shadow 0.3s;
            border: 1px solid #2d2d4a;
            cursor: pointer;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(255, 64, 129, 0.2);
            border-color: #ff4081;
        }
        
        .feature-icon {
            font-size: 40px;
            color: #ff4081;
            margin-bottom: 15px;
        }
        
        .feature-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 10px;
            color: white;
        }
        
        .feature-desc {
            font-size: 14px;
            color: #aaa;
            line-height: 1.5;
        }
        
        /* باقات VIP */
        .plans-section {
            margin-bottom: 40px;
        }
        
        .plans-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
        }
        
        .plan-card {
            background-color: #1a1a2e;
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            border: 2px solid #2d2d4a;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }
        
        .plan-card:hover {
            border-color: #ff4081;
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(255, 64, 129, 0.2);
        }
        
        .plan-card.popular {
            border-color: #ff4081;
            background: linear-gradient(145deg, #1a1a2e, #252541);
        }
        
        .popular-badge {
            position: absolute;
            top: 15px;
            left: 15px;
            background-color: #ff4081;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .plan-name {
            font-size: 22px;
            font-weight: 700;
            margin-bottom: 10px;
            color: white;
        }
        
        .plan-price {
            font-size: 36px;
            font-weight: 700;
            color: #ff4081;
            margin-bottom: 15px;
        }
        
        .plan-period {
            font-size: 16px;
            color: #aaa;
            margin-bottom: 25px;
        }
        
        .plan-features {
            list-style: none;
            margin-bottom: 25px;
            text-align: right;
        }
        
        .plan-features li {
            padding: 8px 0;
            color: #ddd;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .plan-features li i {
            color: #4CAF50;
            font-size: 18px;
        }
        
        .subscribe-btn {
            background-color: #ff4081;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 30px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }
        
        .subscribe-btn:hover {
            background-color: #ff2a6d;
        }
        
        .subscribe-btn.secondary {
            background-color: transparent;
            border: 2px solid #ff4081;
            color: #ff4081;
        }
        
        .subscribe-btn.secondary:hover {
            background-color: rgba(255, 64, 129, 0.1);
        }
        
        /* صفحة الاستكشاف */
        .explore-page {
            display: none;
            padding: 20px;
            background-color: #0f0f1a;
            position: fixed;
            top: 70px;
            left: 0;
            right: 0;
            bottom: 80px;
            overflow-y: auto;
            z-index: 1500;
        }
        
        .explore-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 20px;
        }
        
        .explore-card {
            background-color: #1a1a2e;
            border-radius: 15px;
            overflow: hidden;
            cursor: pointer;
            transition: transform 0.3s;
            border: 1px solid #2d2d4a;
        }
        
        .explore-card:hover {
            transform: translateY(-5px);
            border-color: #ff4081;
        }
        
        .explore-card img {
            width: 100%;
            height: 120px;
            object-fit: cover;
        }
        
        .explore-card h3 {
            padding: 15px;
            font-size: 16px;
            color: white;
            text-align: center;
        }
        
        /* صفحة التحميلات */
        .downloads-page {
            display: none;
            padding: 20px;
            background-color: #0f0f1a;
            position: fixed;
            top: 70px;
            left: 0;
            right: 0;
            bottom: 80px;
            overflow-y: auto;
            z-index: 1500;
        }
        
        .downloads-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .download-item {
            background-color: #1a1a2e;
            border-radius: 15px;
            padding: 20px;
            display: flex;
            align-items: center;
            gap: 20px;
            border: 1px solid #2d2d4a;
        }
        
        .download-item img {
            width: 80px;
            height: 80px;
            border-radius: 10px;
            object-fit: cover;
        }
        
        .download-info {
            flex: 1;
        }
        
        .download-name {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 5px;
            color: white;
        }
        
        .download-size {
            font-size: 14px;
            color: #aaa;
            margin-bottom: 10px;
        }
        
        .download-progress {
            width: 100%;
            height: 8px;
            background-color: #2d2d4a;
            border-radius: 4px;
            overflow: hidden;
            margin-bottom: 10px;
        }
        
        .progress-bar {
            height: 100%;
            background-color: #ff4081;
            border-radius: 4px;
        }
        
        .download-actions {
            display: flex;
            gap: 10px;
        }
        
        .download-btn {
            background-color: transparent;
            color: #aaa;
            border: 1px solid #555;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 14px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: all 0.3s;
        }
        
        .download-btn:hover {
            border-color: #ff4081;
            color: #ff4081;
        }
        
        /* صفحة الحساب */
        .account-page {
            display: none;
            padding: 20px;
            background-color: #0f0f1a;
            position: fixed;
            top: 70px;
            left: 0;
            right: 0;
            bottom: 80px;
            overflow-y: auto;
            z-index: 1500;
        }
        
        .profile-header {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 30px;
            background-color: #1a1a2e;
            border-radius: 20px;
            padding: 25px;
        }
        
        .profile-pic {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid #ff4081;
        }
        
        .profile-info h2 {
            font-size: 24px;
            margin-bottom: 5px;
            color: white;
        }
        
        .profile-info p {
            color: #aaa;
        }
        
        .account-stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background-color: #1a1a2e;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            transition: transform 0.3s;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            border: 1px solid #ff4081;
        }
        
        .stat-value {
            font-size: 24px;
            font-weight: 700;
            color: #ff4081;
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 14px;
            color: #aaa;
        }
        
        /* شريط التنقل السفلي */
        .bottom-nav {
            background-color: #1a1a2e;
            display: flex;
            justify-content: space-around;
            align-items: center;
            padding: 15px 0;
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            height: 80px;
            border-top: 1px solid #2d2d4a;
            z-index: 1000;
        }
        
        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: #aaa;
            cursor: pointer;
            transition: color 0.3s;
            width: 70px;
            text-align: center;
        }
        
        .nav-item:hover, .nav-item.active {
            color: #ff4081;
        }
        
        .nav-item i {
            font-size: 22px;
            margin-bottom: 5px;
        }
        
        .nav-item span {
            font-size: 14px;
            font-weight: 500;
        }
        
        /* صفحات إضافية */
        .home-page {
            display: block;
        }
        
        .vip-page {
            display: none;
        }
        
        /* صفحة الفيديو */
        .video-page {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #000;
            z-index: 2000;
            flex-direction: column;
        }
        
        .video-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.8);
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            z-index: 10;
        }
        
        .video-title {
            font-size: 18px;
            font-weight: 600;
            color: white;
        }
        
        .close-video {
            background: none;
            border: none;
            color: white;
            font-size: 24px;
            cursor: pointer;
        }
        
        .video-player {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
        }
        
        .video-placeholder {
            width: 100%;
            height: 100%;
            background-color: #000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 24px;
        }
        
        .video-placeholder i {
            font-size: 60px;
            margin-bottom: 20px;
            color: #ff4081;
        }
        
        /* التكيف مع الشاشات الصغيرة */
        @media (max-width: 768px) {
            .main-title {
                font-size: 24px;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
            }
            
            .plans-grid {
                grid-template-columns: 1fr;
            }
            
            .explore-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .account-stats {
                grid-template-columns: 1fr;
            }
            
            .download-item {
                flex-direction: column;
                text-align: center;
                gap: 15px;
            }
            
            .download-actions {
                justify-content: center;
                width: 100%;
            }
        }
        
        @media (max-width: 480px) {
            .logo {
                font-size: 20px;
            }
            
            .balance-info {
                font-size: 12px;
                padding: 5px 10px;
            }
            
            .main-container {
                padding: 15px;
            }
            
            .nav-item span {
                font-size: 12px;
            }
            
            .balance-large {
                font-size: 20px;
                padding: 10px 20px;
            }
        }
    </style>
</head>
<body>
    <!-- الشريط العلوي -->
    <div class="top-bar">
        <div class="logo">
            <i class="fas fa-play-circle"></i>
            <span>مشاهدتي</span>
        </div>
        
        <div class="user-actions">
            <i class="fas fa-search" id="searchBtn"></i>
            <i class="fas fa-bell" id="notificationsBtn"></i>
            <i class="fas fa-user-circle" id="accountBtn"></i>
            <div class="balance-info">
                <i class="fas fa-coins"></i>
                <span id="userBalance">765+</span>
            </div>
        </div>
    </div>
    
    <!-- الصفحة الرئيسية (VIP) -->
    <div class="main-container vip-page" id="vipPageMain">
        <h1 class="main-title">مشاهدتي</h1>
        
        <div class="vip-balance-section">
            <div class="balance-large">
                <i class="fas fa-crown"></i>
                <span>+765</span>
            </div>
        </div>
        
        <!-- ميزات VIP -->
        <div class="features-section">
            <h2 class="section-title">مميزات الاشتراك VIP</h2>
            <div class="features-grid" id="vipFeatures">
                <!-- سيتم ملؤها بميزات VIP -->
            </div>
        </div>
        
        <!-- باقات VIP -->
        <div class="plans-section">
            <h2 class="section-title">باقات الاشتراك</h2>
            <div class="plans-grid" id="vipPlans">
                <!-- سيتم ملؤها بباقات VIP -->
            </div>
        </div>
    </div>
    
    <!-- صفحة الاستكشاف -->
    <div class="explore-page" id="explorePage">
        <h2 class="main-title">استكشاف</h2>
        
        <div class="section-title" style="margin-top: 20px;">التصنيفات الشائعة</div>
        <div class="explore-grid" id="categoriesGrid">
            <!-- سيتم ملؤها بالتصنيفات -->
        </div>
        
        <div class="section-title" style="margin-top: 30px;">المسلسلات الجديدة</div>
        <div class="explore-grid" id="newShowsGrid">
            <!-- سيتم ملؤها بالمسلسلات الجديدة -->
        </div>
    </div>
    
    <!-- صفحة التحميلات -->
    <div class="downloads-page" id="downloadsPage">
        <h2 class="main-title">تحميلاتي</h2>
        
        <div class="downloads-list" id="downloadsList">
            <!-- سيتم ملؤها بالتحميلات -->
        </div>
        
        <div style="text-align: center; margin-top: 30px;">
            <button class="subscribe-btn" id="manageDownloadsBtn" style="width: auto; padding: 12px 30px;">
                إدارة التحميلات
            </button>
        </div>
    </div>
    
    <!-- صفحة الحساب -->
    <div class="account-page" id="accountPage">
        <div class="profile-header">
            <img src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=500&q=80" alt="الصورة الشخصية" class="profile-pic">
            <div class="profile-info">
                <h2>عمر أحمد</h2>
                <p>عضو VIP منذ: يناير 2024</p>
            </div>
        </div>
        
        <div class="account-stats">
            <div class="stat-card">
                <div class="stat-value">+765</div>
                <div class="stat-label">نقاط المكافآت</div>
            </div>
            <div class="stat-card">
              
