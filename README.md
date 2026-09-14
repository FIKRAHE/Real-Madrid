<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>REAL MADRID | THE ROYAL GOLD EDITION</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #080808;
            --card-bg: #141414;
            --gold: #d4af37;
            --gold-light: #f3e5ab;
            --gold-dark: #aa8c2c;
            --text-main: #f5f5f5;
            --text-muted: #a0a0a0;
            --border-gold: rgba(212, 175, 55, 0.3);
            --danger: #e74c3c;
            --success: #2ecc71;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        header {
            text-align: center;
            padding: 30px 20px;
            background: linear-gradient(180deg, #1a1600 0%, var(--bg-color) 100%);
            border-bottom: 1px solid var(--border-gold);
        }

        header .crown-badge {
            display: inline-block;
            background: rgba(212, 175, 55, 0.15);
            color: var(--gold);
            padding: 6px 18px;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 700;
            letter-spacing: 2px;
            margin-bottom: 10px;
            border: 1px solid var(--border-gold);
        }

        header h1 {
            font-size: 2.2rem;
            font-weight: 900;
            color: var(--gold-light);
            text-shadow: 0 0 20px rgba(212, 175, 55, 0.4);
            letter-spacing: 1px;
        }

        header p {
            color: var(--text-muted);
            font-size: 1rem;
            margin-top: 5px;
        }

        .storefront-hero {
            max-width: 600px;
            margin: 30px auto;
            padding: 0 20px;
            cursor: pointer;
        }

        .compact-product-card {
            background: var(--card-bg);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid var(--border-gold);
            box-shadow: 0 10px 30px rgba(0,0,0,0.8);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }

        .compact-product-card:hover {
            transform: translateY(-5px);
            border-color: var(--gold-light);
            box-shadow: 0 15px 35px rgba(212, 175, 55, 0.2);
        }

        .compact-img-container {
            width: 100%;
            height: 380px;
            position: relative;
            overflow: hidden;
        }

        .compact-img-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .compact-info {
            padding: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: linear-gradient(180deg, #141414 0%, #1a1600 100%);
        }

        .compact-title-wrap h3 {
            font-size: 1.3rem;
            font-weight: 900;
            color: #fff;
        }

        .compact-title-wrap p {
            font-size: 0.85rem;
            color: var(--gold);
        }

        .compact-price-wrap .current-price {
            font-size: 1.8rem;
            font-weight: 900;
            color: var(--gold-light);
            display: block;
        }

        .tap-hint-bar {
            background: rgba(212, 175, 55, 0.15);
            text-align: center;
            padding: 12px;
            color: var(--gold-light);
            font-size: 0.95rem;
            font-weight: 700;
            border-top: 1px solid var(--border-gold);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            transition: background 0.3s;
        }

        .compact-product-card:hover .tap-hint-bar {
            background: rgba(212, 175, 55, 0.25);
        }

        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.88);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.35s ease;
            padding: 20px;
            overflow-y: auto;
        }

        .modal-overlay.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal-content-wrapper {
            background: var(--card-bg);
            border-radius: 24px;
            border: 1px solid var(--border-gold);
            width: 100%;
            max-width: 1050px;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            box-shadow: 0 0 50px rgba(212, 175, 55, 0.25);
            transform: translateY(20px);
            transition: transform 0.35s ease;
            display: grid;
            grid-template-columns: 1fr 1.15fr;
        }

        .modal-overlay.active .modal-content-wrapper {
            transform: translateY(0);
        }

        .modal-close-btn {
            position: absolute;
            top: 18px;
            left: 20px;
            background: rgba(255, 255, 255, 0.1);
            color: #fff;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            cursor: pointer;
            z-index: 10;
            transition: all 0.3s;
        }

        .modal-close-btn:hover {
            background: var(--danger);
            color: #fff;
        }

        @media (max-width: 900px) {
            .modal-content-wrapper {
                grid-template-columns: 1fr;
                max-height: 92vh;
            }
        }

        .modal-gallery {
            padding: 25px;
            display: flex;
            flex-direction: column;
            gap: 15px;
            border-left: 1px solid rgba(212, 175, 55, 0.15);
        }

        @media (max-width: 900px) {
            .modal-gallery {
                border-left: none;
                border-bottom: 1px solid rgba(212, 175, 55, 0.15);
            }
        }

        .main-image-container {
            width: 100%;
            height: 380px;
            border-radius: 16px;
            overflow: hidden;
            background: #111;
            border: 1px solid var(--border-gold);
            position: relative;
        }

        .main-image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .main-image-container:hover img {
            transform: scale(1.05);
        }

        .thumbnails-grid {
            display: grid;
            grid-template-columns: repeat(6, 1fr);
            gap: 8px;
        }

        .thumb {
            height: 60px;
            border-radius: 8px;
            overflow: hidden;
            cursor: pointer;
            border: 2px solid transparent;
            background: #111;
            transition: all 0.3s ease;
        }

        .thumb.active, .thumb:hover {
            border-color: var(--gold);
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.4);
        }

        .thumb img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .modal-form-area {
            padding: 25px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .epic-badge {
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            color: #000;
            font-weight: 800;
            padding: 5px 14px;
            border-radius: 6px;
            font-size: 0.8rem;
            display: inline-block;
            margin-bottom: 6px;
            width: fit-content;
        }

        .product-title {
            font-size: 1.5rem;
            font-weight: 900;
            color: #fff;
        }

        .product-desc {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        .price-box {
            display: flex;
            align-items: baseline;
            justify-content: space-between;
            background: rgba(212, 175, 55, 0.05);
            padding: 12px 16px;
            border-radius: 12px;
            border-right: 4px solid var(--gold);
        }

        .price-box .current-price {
            font-size: 1.8rem;
            font-weight: 900;
            color: var(--gold-light);
        }

        .promo-tag {
            color: var(--success);
            font-weight: 700;
            font-size: 0.85rem;
            background: rgba(46, 204, 113, 0.1);
            padding: 4px 12px;
            border-radius: 8px;
            border: 1px solid rgba(46, 204, 113, 0.2);
        }

        .option-group {
            margin-bottom: 5px;
        }

        .option-label {
            display: block;
            font-weight: 700;
            margin-bottom: 8px;
            color: var(--gold-light);
            font-size: 0.9rem;
        }

        .pills-container {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .pill-btn {
            background: #1f1f1f;
            border: 1px solid #333;
            color: #fff;
            padding: 8px 14px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.85rem;
            transition: all 0.3s;
        }

        .pill-btn.active {
            background: var(--gold);
            color: #000;
            border-color: var(--gold-light);
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.4);
        }

        .pieces-config-container {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .piece-config-block {
            background: #1a1a1a;
            border: 1px solid rgba(212, 175, 55, 0.2);
            border-radius: 12px;
            padding: 12px;
        }

        .piece-config-block .piece-title {
            font-size: 0.85rem;
            font-weight: 700;
            color: var(--gold);
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .order-form {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        @media (max-width: 600px) {
            .form-row {
                grid-template-columns: 1fr;
            }
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .form-group label {
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        .form-group input, .form-group select {
            background: #111;
            border: 1px solid #333;
            color: #fff;
            padding: 10px 12px;
            border-radius: 8px;
            font-size: 0.9rem;
            outline: none;
            transition: border-color 0.3s;
        }

        .form-group input:focus, .form-group select:focus {
            border-color: var(--gold);
        }

        .submit-btn {
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            color: #000;
            border: none;
            padding: 14px;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 800;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            margin-top: 5px;
            box-shadow: 0 5px 20px rgba(212, 175, 55, 0.4);
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(212, 175, 55, 0.6);
        }

        .memories-container {
            max-width: 1100px;
            margin: 40px auto;
            padding: 30px;
            background: var(--card-bg);
            border-radius: 20px;
            border: 1px solid var(--border-gold);
            text-align: center;
        }

        .toggle-memories-btn {
            background: transparent;
            border: 2px solid var(--gold);
            color: var(--gold-light);
            padding: 14px 30px;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .toggle-memories-btn:hover {
            background: var(--gold);
            color: #000;
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.5);
        }

        .memories-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 25px;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.6s ease-out, opacity 0.5s ease;
            opacity: 0;
        }

        .memories-grid.show {
            max-height: 3500px;
            opacity: 1;
        }

        .memory-item {
            height: 180px;
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid #333;
            cursor: pointer;
            transition: transform 0.3s, border-color 0.3s;
            background: #111;
        }

        .memory-item:hover {
            transform: scale(1.03);
            border-color: var(--gold);
            box-shadow: 0 5px 15px rgba(212, 175, 55, 0.3);
        }

        .memory-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .lightbox {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.92);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 11000;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.3s ease;
            padding: 20px;
        }

        .lightbox.active {
            opacity: 1;
            pointer-events: auto;
        }

        .lightbox img {
            max-width: 90%;
            max-height: 85vh;
            border-radius: 12px;
            border: 2px solid var(--gold);
            box-shadow: 0 0 40px rgba(212, 175, 55, 0.4);
            object-fit: contain;
        }

        .lightbox-close {
            position: absolute;
            top: 25px;
            left: 30px;
            color: #fff;
            font-size: 2.5rem;
            cursor: pointer;
            transition: color 0.3s;
        }

        .lightbox-close:hover {
            color: var(--gold);
        }

        footer {
            text-align: center;
            padding: 30px;
            color: var(--text-muted);
            font-size: 0.85rem;
            border-top: 1px solid #222;
            margin-top: 50px;
        }
    </style>
</head>
<body>

    <header>
        <span class="crown-badge"><i class="fa-solid fa-crown"></i> REAL MADRID ROYAL EDITION</span>
        <h1>HALA MADRID • الإصدار الملكي</h1>
        <p>تصميم أسود وذهبي حصري يعكس عراقة الملوك وبطولات التاريخ</p>
    </header>

    <div class="storefront-hero" onclick="openProductModal()">
        <div class="compact-product-card">
            <div class="compact-img-container">
                <img id="compactMainImg" src="https://i.ibb.co/67syX3jQ/Screenshot-20260914-201657.png" alt="Real Madrid Special Edition">
            </div>
            <div class="compact-info">
                <div class="compact-title-wrap">
                    <h3>تيشيرت ريال مدريد الملكي</h3>
                    <p>عرض خاص: 2 قطعتين بـ 5000 دج</p>
                </div>
                <div class="compact-price-wrap">
                    <span class="current-price">2700 دج</span>
                </div>
            </div>
            <div class="tap-hint-bar">
                <span>🖱️</span> اضغط هنا لعرض تفاصيل المنتج وحقول الطلب
            </div>
        </div>
    </div>

    <div class="modal-overlay" id="productModal" onclick="checkCloseModal(event)">
        <div class="modal-content-wrapper" id="modalWrapper">
            <span class="modal-close-btn" onclick="closeProductModal()">×</span>
            
            <div class="modal-gallery">
                <div class="main-image-container">
                    <img id="mainImage" src="https://i.ibb.co/67syX3jQ/Screenshot-20260914-201657.png" alt="Real Madrid Special Edition">
                </div>
                <div class="thumbnails-grid">
                    <div class="thumb active" onclick="changeImage('https://i.ibb.co/67syX3jQ/Screenshot-20260914-201657.png', this)">
                        <img src="https://i.ibb.co/67syX3jQ/Screenshot-20260914-201657.png" alt="Hero">
                    </div>
                    <div class="thumb" onclick="changeImage('https://i.ibb.co/XZ9zbZ2L/d21027a1bfb987b405be4ee78716113b.jpg', this)">
                        <img src="https://i.ibb.co/XZ9zbZ2L/d21027a1bfb987b405be4ee78716113b.jpg" alt="Detail 1">
                    </div>
                    <div class="thumb" onclick="changeImage('https://i.ibb.co/RGdV6KQJ/ee4a0785ae68a238b0fed9ceb354d855.jpg', this)">
                        <img src="https://i.ibb.co/RGdV6KQJ/ee4a0785ae68a238b0fed9ceb354d855.jpg" alt="Detail 2">
                    </div>
                    <div class="thumb" onclick="changeImage('https://i.ibb.co/v6D15YfX/8e4977d52459cd877f924fb0cfdd667d.jpg', this)">
                        <img src="https://i.ibb.co/v6D15YfX/8e4977d52459cd877f924fb0cfdd667d.jpg" alt="Detail 3">
                    </div>
                    <div class="thumb" onclick="changeImage('https://i.ibb.co/hJS4Gqgb/746c3b4b6a8c933a4e1f1fae08b66ff1.jpg', this)">
                        <img src="https://i.ibb.co/hJS4Gqgb/746c3b4b6a8c933a4e1f1fae08b66ff1.jpg" alt="Detail 4">
                    </div>
                    <div class="thumb" onclick="changeImage('https://i.ibb.co/TMggrMQj/IMG-20260914-201621.png', this)">
                        <img src="https://i.ibb.co/TMggrMQj/IMG-20260914-201621.png" alt="Detail 5">
                    </div>
                </div>
            </div>

            <div class="modal-form-area">
                <span class="epic-badge">إصدار خاص • أسود وذهبي</span>
                <h2 class="product-title">تيشيرت ريال مدريد الملكي الفاخر</h2>
                <p class="product-desc">خامة قطنية عالية الجودة بتفاصيل ذهبية أنيقة مستوحاة من عراقة النادي الملكي وبطولاته التاريخية.</p>

                <div class="price-box">
                    <div>
                        <span style="display: block; font-size: 0.75rem; color: var(--text-muted);">السعر الإجمالي:</span>
                        <span class="current-price" id="displayPrice">2700 دج</span>
                    </div>
                    <span class="promo-tag" id="promoText">قطعة واحدة</span>
                </div>

                <div class="option-group">
                    <span class="option-label">اختر الكمية:</span>
                    <div class="pills-container" id="qtyContainer">
                        <button type="button" class="pill-btn active" onclick="selectQty(1, this)">1 قطعة</button>
                        <button type="button" class="pill-btn" onclick="selectQty(2, this)">2 قطعتين (عرض خاص)</button>
                        <button type="button" class="pill-btn" onclick="selectQty(3, this)">3 قطع</button>
                        <button type="button" class="pill-btn" onclick="selectQty(4, this)">4 قطع</button>
                        <button type="button" class="pill-btn" onclick="selectQty(5, this)">5 قطع</button>
                    </div>
                </div>

                <div class="option-group">
                    <span class="option-label">تخصيص اللون والمقاس لكل قطعة:</span>
                    <div class="pieces-config-container" id="piecesConfigContainer">
                    </div>
                </div>

                <hr style="border: 0; border-top: 1px solid #333; margin: 10px 0;">

                <form class="order-form" id="orderForm" onsubmit="sendToWhatsApp(event)">
                    <span class="option-label" style="color: var(--gold);">معلومات التوصيل:</span>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label>الاسم الكامل *</label>
                            <input type="text" id="fullName" required placeholder="">
                        </div>
                        <div class="form-group">
                            <label>رقم الهاتف *</label>
                            <input type="tel" id="phone" required placeholder="">
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label>الولاية *</label>
                            <input type="text" id="wilaya" required placeholder="">
                        </div>
                        <div class="form-group">
                            <label>البلدية *</label>
                            <input type="text" id="baladiya" required placeholder="">
                        </div>
                    </div>

                    <div class="form-group">
                        <label>الحي بالضبط *</label>
                        <input type="text" id="neighborhood" required placeholder="">
                    </div>

                    <div class="form-group">
                        <label>رقم المبنى / رقم الشقة أو باب الغرفة *</label>
                        <input type="text" id="building" required placeholder="">
                    </div>

                    <button type="submit" class="submit-btn">
                        <i class="fa-brands fa-whatsapp" style="font-size: 1.3rem;"></i>
                        تأكيد الطلب وإرسال عبر واتساب
                    </button>
                </form>
            </div>
        </div>
    </div>

    <div class="memories-container">
        <button type="button" class="toggle-memories-btn" onclick="toggleMemories()">
            <i class="fa-solid fa-clock-rotate-left"></i>
            بعض من ذكريات نادي ريال مدريد
        </button>
        <div class="memories-grid" id="memoriesGrid">
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/bgYTcVVN/be3b085c0a415befcb4fc86d70c0f43c.jpg')">
                <img src="https://i.ibb.co/bgYTcVVN/be3b085c0a415befcb4fc86d70c0f43c.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/DfSf2Ggm/45491239a46148bc05b36d3205b6aaf2.jpg')">
                <img src="https://i.ibb.co/DfSf2Ggm/45491239a46148bc05b36d3205b6aaf2.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/tp54cwrS/6b9cd75912a1891a67d813b73cc2e761.jpg')">
                <img src="https://i.ibb.co/tp54cwrS/6b9cd75912a1891a67d813b73cc2e761.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/Zp15kNxv/8d68a8e35bc5aa0a88891e89596813af.jpg')">
                <img src="https://i.ibb.co/Zp15kNxv/8d68a8e35bc5aa0a88891e89596813af.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/ZRb9k0HJ/68c86d9f19d1a2ab9f4112f77eebc06c.jpg')">
                <img src="https://i.ibb.co/ZRb9k0HJ/68c86d9f19d1a2ab9f4112f77eebc06c.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/v49t6qXT/e4bf2859db9d9dcd03b46680b2d5fa10.jpg')">
                <img src="https://i.ibb.co/v49t6qXT/e4bf2859db9d9dcd03b46680b2d5fa10.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/qYyBWG1N/d5ebe386adae18ba1644190cdbf2ef42.jpg')">
                <img src="https://i.ibb.co/qYyBWG1N/d5ebe386adae18ba1644190cdbf2ef42.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/mCLr5mKs/af9b83cfd01eb8ecc9d8886e549eb89b.jpg')">
                <img src="https://i.ibb.co/mCLr5mKs/af9b83cfd01eb8ecc9d8886e549eb89b.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/x8d5bXnC/fc424a1f36e391998a9d9417604970f3.jpg')">
                <img src="https://i.ibb.co/x8d5bXnC/fc424a1f36e391998a9d9417604970f3.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/gYGpPVy/b5dff74b789ab34fff5fbe8fac5fb45b.jpg')">
                <img src="https://i.ibb.co/gYGpPVy/b5dff74b789ab34fff5fbe8fac5fb45b.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/cK9p8WpX/be0f1ca4a56427500dae438434e180e7.jpg')">
                <img src="https://i.ibb.co/cK9p8WpX/be0f1ca4a56427500dae438434e180e7.jpg" alt="Memory">
            </div>
            <div class="memory-item" onclick="openLightbox('https://i.ibb.co/Zz1cV1gs/62b521d9458b8c336b508ebde1ac69cf.jpg')">
                <img src="https://i.ibb.co/Zz1cV1gs/62b521d9458b8c336b508ebde1ac69cf.jpg" alt="Memory">
            </div>
        </div>
    </div>

    <div class="lightbox" id="lightbox" onclick="closeLightbox()">
        <span class="lightbox-close" onclick="closeLightbox()">×</span>
        <img id="lightboxImg" src="" alt="Full view">
    </div>

    <footer>
        <p>© 2026 REAL MADRID ROYAL COLLECTION • جميع الحقوق محفوظة</p>
    </footer>

    <script>
        const colors = ['أبيض', 'وردي', 'أخضر'];
        const sizes = ['S', 'M', 'L', 'XL'];
        
        let currentImgUrl = 'https://i.ibb.co/67syX3jQ/Screenshot-20260914-201657.png';
        let currentQty = 1;
        let calculatedPrice = 2700;

        function openProductModal() {
            document.getElementById('productModal').classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeProductModal() {
            document.getElementById('productModal').classList.remove('active');
            document.body.style.overflow = '';
        }

        function checkCloseModal(e) {
            if (e.target.id === 'productModal') {
                closeProductModal();
            }
        }

        function changeImage(url, element) {
            document.getElementById('mainImage').src = url;
            document.getElementById('compactMainImg').src = url;
            currentImgUrl = url;
            document.querySelectorAll('.thumb').forEach(el => el.classList.remove('active'));
            if (element) element.classList.add('active');
        }

        function calculateOrderPrice(qty) {
            if (qty === 1) return 2700;
            if (qty === 2) return 5000;
            return qty * 2700;
        }

        function renderPieceConfigs(qty) {
            const container = document.getElementById('piecesConfigContainer');
            const oldColors = [];
            const oldSizes = [];
            container.querySelectorAll('.piece-color').forEach(sel => oldColors.push(sel.value));
            container.querySelectorAll('.piece-size').forEach(sel => oldSizes.push(sel.value));

            container.innerHTML = '';
            for (let i = 1; i <= qty; i++) {
                const defaultColor = oldColors[i - 1] || 'أبيض';
                const defaultSize = oldSizes[i - 1] || 'M';

                const block = document.createElement('div');
                block.className = 'piece-config-block';
                block.innerHTML = `
                    <div class="piece-title"><i class="fa-solid fa-shirt"></i> القطعة رقم ${i}</div>
                    <div class="form-row">
                        <div class="form-group">
                            <label>اللون</label>
                            <select class="piece-color" data-piece="${i}">
                                ${colors.map(c => `<option value="${c}" ${c === defaultColor ? 'selected' : ''}>${c}</option>`).join('')}
                            </select>
                        </div>
                        <div class="form-group">
                            <label>المقاس</label>
                            <select class="piece-size" data-piece="${i}">
                                ${sizes.map(s => `<option value="${s}" ${s === defaultSize ? 'selected' : ''}>${s}</option>`).join('')}
                            </select>
                        </div>
                    </div>
                `;
                container.appendChild(block);
            }
        }

        function selectQty(qty, button) {
            document.querySelectorAll('#qtyContainer .pill-btn').forEach(btn => btn.classList.remove('active'));
            button.classList.add('active');
            currentQty = qty;
            calculatedPrice = calculateOrderPrice(qty);
            
            document.getElementById('displayPrice').innerText = calculatedPrice + ' دج';
            
            const promoEl = document.getElementById('promoText');
            if (qty === 1) {
                promoEl.innerText = 'سعر عادي';
            } else if (qty === 2) {
                promoEl.innerText = 'وفر 400 دج بالعرض الخاص';
            } else {
                promoEl.innerText = 'عرض خاص للكميات';
            }
            
            renderPieceConfigs(qty);
        }

        renderPieceConfigs(1);

        function toggleMemories() {
            const grid = document.getElementById('memoriesGrid');
            grid.classList.toggle('show');
        }

        function openLightbox(url) {
            const lb = document.getElementById('lightbox');
            const img = document.getElementById('lightboxImg');
            img.src = url;
            lb.classList.add('active');
        }

        function closeLightbox() {
            const lb = document.getElementById('lightbox');
            lb.classList.remove('active');
        }

        function sendToWhatsApp(e) {
            e.preventDefault();

            const fullName = document.getElementById('fullName').value.trim();
            const phone = document.getElementById('phone').value.trim();
            const wilaya = document.getElementById('wilaya').value.trim();
            const baladiya = document.getElementById('baladiya').value.trim();
            const neighborhood = document.getElementById('neighborhood').value.trim();
            const building = document.getElementById('building').value.trim();

            let piecesDetailsText = '';
            const colorSelects = document.querySelectorAll('.piece-color');
            const sizeSelects = document.querySelectorAll('.piece-size');
            colorSelects.forEach((sel, idx) => {
                const c = sel.value;
                const s = sizeSelects[idx].value;
                piecesDetailsText += `  ▫️ *القطعة ${idx + 1}*: لون [${c}] - مقاس [${s}]\n`;
            });

            const text = `👑 *طلب جديد - ريال مدريد (أسود وذهبي)* 👑\n\n` +
                `👤 *الاسم الكامل*: ${fullName}\n` +
                `📞 *رقم الهاتف*: ${phone}\n` +
                `📍 *الولاية*: ${wilaya}\n` +
                `🏘️ *البلدية*: ${baladiya}\n` +
                `📌 *الحي*: ${neighborhood}\n` +
                `🏢 *تفاصيل المبنى/باب الشقة*: ${building}\n\n` +
                `--------------------------\n` +
                `👕 *المنتج*: تيشيرت ريال مدريد الملكي\n` +
                `🔢 *الكمية الإجمالية*: ${currentQty} ${currentQty === 2 ? '(عرض قطعتين)' : ''}\n` +
                `🎨 *تفاصيل القطع*:\n${piecesDetailsText}` +
                `💰 *السعر الإجمالي*: ${calculatedPrice} دج\n` +
                `--------------------------\n` +
                `🖼️ *صورة المنتج المعروضة*:\n${currentImgUrl}`;

            const whatsappNumber = '213660570954';
            const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(text)}`;
            window.location.href = whatsappUrl;
        }
    </script>
</body>
</html>
