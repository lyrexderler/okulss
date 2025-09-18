<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yapım Aşamasında</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
        }
        
        .container {
            max-width: 600px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .construction-icon {
            font-size: 5rem;
            margin: 30px 0;
            color: #FFD700;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        .instagram-container {
            background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
            padding: 20px;
            border-radius: 15px;
            margin: 30px 0;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .instagram-text {
            font-size: 1.8rem;
            font-weight: bold;
            margin-bottom: 10px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
        }
        
        .username {
            font-size: 2.5rem;
            font-weight: bold;
            letter-spacing: 1px;
            background: white;
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            text-shadow: 0px 2px 3px rgba(255, 255, 255, 0.3);
        }
        
        .message {
            font-size: 1.2rem;
            margin-top: 30px;
            line-height: 1.6;
            opacity: 0.9;
        }
        
        .social-links {
            margin-top: 30px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }
        
        .social-link {
            display: inline-block;
            width: 50px;
            height: 50px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
            transition: all 0.3s ease;
            text-decoration: none;
        }
        
        .social-link:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.2);
        }
        
        .footer {
            margin-top: 40px;
            font-size: 0.9rem;
            opacity: 0.7;
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2.2rem;
            }
            
            .username {
                font-size: 2rem;
            }
            
            .container {
                padding: 30px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Yapım Aşamasında</h1>
        
        <div class="construction-icon">
            <i class="fas fa-tools"></i>
        </div>
        
        <div class="instagram-container">
            <div class="instagram-text">Instagram:</div>
            <div class="username">@yusuf_svp13</div>
        </div>
        
        <div class="message">
            <p>Web sitem yakında hizmetinizde olacak!</p>
            <p>Şu anda yoğun bir şekilde çalışmalar devam ediyor.</p>
        </div>
        
        <div class="social-links">
            <a href="https://instagram.com/yusuf_svp13" class="social-link" target="_blank">
                <i class="fab fa-instagram"></i>
            </a>
            <a href="#" class="social-link">
                <i class="fab fa-twitter"></i>
            </a>
            <a href="#" class="social-link">
                <i class="fab fa-facebook-f"></i>
            </a>
        </div>
        
        <div class="footer">
            <p>© 2023 Yusuf SVP. Tüm hakları saklıdır.</p>
        </div>
    </div>

    <script>
        // Basit bir animasyon efekti
        document.addEventListener('DOMContentLoaded', function() {
            const elements = document.querySelectorAll('h1, .construction-icon, .instagram-container, .message, .social-links');
            
            elements.forEach((element, index) => {
                element.style.opacity = 0;
                element.style.transform = 'translateY(20px)';
                
                setTimeout(() => {
                    element.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
                    element.style.opacity = 1;
                    element.style.transform = 'translateY(0)';
                }, 200 * index);
            });
        });
    </script>
</body>
</html>
