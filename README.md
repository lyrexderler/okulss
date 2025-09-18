
[deepseek_html_20250918_0bf936 (1).html](https://github.com/user-attachments/files/22414702/deepseek_html_20250918_0bf936.1.html)
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Key-Value Okul Sohbeti</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #4e73df;
            --secondary-color: #f8f9fc;
            --accent-color: #36b9cc;
            --text-color: #5a5c69;
            --light-color: #fff;
            --dark-color: #2e59d9;
            --success-color: #1cc88a;
            --danger-color: #e74a3b;
            --warning-color: #f6c23e;
            --dark-bg: #2e3440;
            --darker-bg: #242831;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--dark-bg);
            color: #d8dee9;
            height: 100vh;
            display: flex;
            flex-direction: column;
        }

        .container {
            display: flex;
            flex: 1;
            overflow: hidden;
        }

        /* Giriş Ekranı */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #2e3440 0%, #3b4252 100%);
        }

        .auth-tabs {
            display: flex;
            margin-bottom: 1rem;
            border-radius: 5px 5px 0 0;
            overflow: hidden;
        }

        .auth-tab {
            flex: 1;
            padding: 1rem;
            text-align: center;
            background-color: #3b4252;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .auth-tab.active {
            background-color: var(--primary-color);
            font-weight: bold;
        }

        .auth-form {
            background: var(--darker-bg);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
            width: 100%;
            max-width: 400px;
            border: 1px solid #4c566a;
        }

        .auth-form h2 {
            text-align: center;
            margin-bottom: 1.5rem;
            color: var(--primary-color);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #eceff4;
        }

        .form-group input {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #4c566a;
            border-radius: 5px;
            font-size: 1rem;
            background-color: #3b4252;
            color: #eceff4;
        }

        .btn {
            display: block;
            width: 100%;
            padding: 0.75rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: var(--dark-color);
        }

        /* Ana Uygulama */
        .app {
            display: none;
            flex-direction: column;
            height: 100vh;
            width: 100%;
        }

        /* Header */
        .header {
            background-color: var(--darker-bg);
            color: var(--light-color);
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            border-bottom: 1px solid #4c566a;
        }

        .header h1 {
            font-size: 1.5rem;
            color: #88c0d0;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .user-info span {
            font-weight: 600;
            color: #81a1c1;
        }

        /* Sidebar */
        .sidebar {
            width: 250px;
            background-color: var(--darker-bg);
            padding: 1rem;
            border-right: 1px solid #4c566a;
            overflow-y: auto;
        }

        .sidebar h3 {
            margin-bottom: 1rem;
            color: var(--primary-color);
            border-bottom: 1px solid #4c566a;
            padding-bottom: 0.5rem;
        }

        .online-users {
            list-style: none;
        }

        .online-users li {
            padding: 0.5rem;
            margin-bottom: 0.5rem;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: background-color 0.3s;
        }

        .online-users li:hover {
            background-color: #3b4252;
        }

        .user-status {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: var(--success-color);
        }

        /* Chat Area */
        .chat-area {
            flex: 1;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-messages {
            flex: 1;
            padding: 1rem;
            overflow-y: auto;
            background-color: #2e3440;
        }

        .message {
            margin-bottom: 1rem;
            padding: 0.75rem;
            border-radius: 10px;
            max-width: 70%;
            position: relative;
            animation: fadeIn 0.3s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .message.sent {
            background-color: #5e81ac;
            color: white;
            margin-left: auto;
        }

        .message.received {
            background-color: #434c5e;
            border: 1px solid #4c566a;
        }

        .message-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
        }

        .message.sent .message-header {
            color: #d8dee9;
        }

        .message.received .message-header {
            color: var(--primary-color);
        }

        .message-content {
            word-wrap: break-word;
        }

        .mentioned {
            background-color: #4c566a;
            border: 1px solid #5e81ac;
        }

        .mention {
            color: #88c0d0;
            font-weight: 600;
        }

        .system-message {
            text-align: center;
            color: #a3be8c;
            font-style: italic;
            margin: 10px 0;
        }

        /* Chat Input */
        .chat-input {
            padding: 1rem;
            background-color: var(--darker-bg);
            border-top: 1px solid #4c566a;
            display: flex;
            gap: 10px;
        }

        .chat-input input {
            flex: 1;
            padding: 0.75rem;
            border: 1px solid #4c566a;
            border-radius: 5px;
            font-size: 1rem;
            background-color: #3b4252;
            color: #eceff4;
        }

        .chat-input button {
            padding: 0.75rem 1.5rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .chat-input button:hover {
            background-color: var(--dark-color);
        }

        /* Sesli Sohbet */
        .voice-chat {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 0.5rem 1rem;
            background-color: #3b4252;
            border-top: 1px solid #4c566a;
        }

        .voice-btn {
            padding: 0.5rem;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: var(--primary-color);
            color: white;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .voice-btn:hover {
            background-color: var(--dark-color);
        }

        .voice-btn.muted {
            background-color: var(--danger-color);
        }

        /* Admin Panel */
        .admin-panel {
            display: none;
            position: fixed;
            top: 0;
            right: 0;
            width: 300px;
            height: 100%;
            background-color: var(--darker-bg);
            box-shadow: -2px 0 10px rgba(0, 0, 0, 0.3);
            padding: 1rem;
            overflow-y: auto;
            z-index: 1000;
            border-left: 1px solid #4c566a;
        }

        .admin-panel h2 {
            color: var(--primary-color);
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid #4c566a;
        }

        .admin-section {
            margin-bottom: 1.5rem;
            padding: 1rem;
            background-color: #3b4252;
            border-radius: 5px;
        }

        .admin-section h3 {
            margin-bottom: 0.5rem;
            color: #88c0d0;
        }

        .admin-btn {
            padding: 0.5rem;
            margin: 0.25rem;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .btn-danger {
            background-color: var(--danger-color);
            color: white;
        }

        .btn-danger:hover {
            background-color: #c53030;
        }

        .btn-warning {
            background-color: var(--warning-color);
            color: black;
        }

        .btn-warning:hover {
            background-color: #ecc94b;
        }

        .admin-close {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #eceff4;
        }

        /* Bot Koruması Uyarıları */
        .bot-warning {
            padding: 0.5rem;
            margin: 0.5rem 0;
            background-color: rgba(229, 62, 62, 0.1);
            border-left: 3px solid var(--danger-color);
            border-radius: 3px;
            font-size: 0.9rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .sidebar {
                width: 200px;
            }

            .message {
                max-width: 85%;
            }
        }

        @media (max-width: 576px) {
            .container {
                flex-direction: column;
            }

            .sidebar {
                width: 100%;
                height: 150px;
                border-right: none;
                border-bottom: 1px solid #4c566a;
            }

            .message {
                max-width: 90%;
            }
            
            .admin-panel {
                width: 100%;
            }
        }

        /* Özel Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: #3b4252;
        }

        ::-webkit-scrollbar-thumb {
            background: #4c566a;
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: #434c5e;
        }
    </style>
</head>
<body>
    <!-- Giriş/Kayıt Ekranı -->
    <div class="auth-container" id="authContainer">
        <div class="auth-form">
            <div class="auth-tabs">
                <div class="auth-tab active" id="loginTab">Giriş Yap</div>
                <div class="auth-tab" id="registerTab">Kayıt Ol</div>
            </div>
            
            <div id="loginForm">
                <h2>Giriş Yap</h2>
                <div class="form-group">
                    <label for="loginUsername">Kullanıcı Adı</label>
                    <input type="text" id="loginUsername" placeholder="Kullanıcı adınız" required>
                </div>
                <div class="form-group">
                    <label for="loginPassword">Şifre</label>
                    <input type="password" id="loginPassword" placeholder="Şifreniz" required>
                </div>
                <button class="btn" id="loginBtn">Giriş Yap</button>
            </div>
            
            <div id="registerForm" style="display: none;">
                <h2>Kayıt Ol</h2>
                <div class="form-group">
                    <label for="registerUsername">Kullanıcı Adı</label>
                    <input type="text" id="registerUsername" placeholder="Soyad kullanmadan" required>
                </div>
                <div class="form-group">
                    <label for="registerPassword">Şifre</label>
                    <input type="password" id="registerPassword" placeholder="Şifreniz (en az 6 karakter)" required>
                </div>
                <div class="form-group">
                    <label for="registerPasswordConfirm">Şifre Tekrar</label>
                    <input type="password" id="registerPasswordConfirm" placeholder="Şifrenizi tekrar girin" required>
                </div>
                <button class="btn" id="registerBtn">Kayıt Ol</button>
            </div>
            
            <p style="margin-top: 1rem; text-align: center;">
                Kurucular: <strong>Lyrex</strong> ve <strong>Vaynes</strong>
            </p>
        </div>
    </div>

    <!-- Ana Uygulama -->
    <div class="app" id="app">
        <!-- Header -->
        <div class="header">
            <h1><i class="fas fa-school"></i> Key-Value Sohbet</h1>
            <div class="user-info">
                <span id="currentUsername">Kullanıcı</span>
                <button class="btn" id="adminToggle" style="padding: 0.5rem; display: none;">Yönetici</button>
                <button class="btn" id="shareBtn" style="padding: 0.5rem; background-color: var(--accent-color);">Paylaş</button>
                <button class="btn" id="logoutBtn" style="padding: 0.5rem; background-color: var(--danger-color);">Çıkış</button>
            </div>
        </div>

        <div class="container">
            <!-- Sidebar - Online Kullanıcılar -->
            <div class="sidebar">
                <h3><i class="fas fa-users"></i> Çevrimiçi Kullanıcılar</h3>
                <ul class="online-users" id="onlineUsers">
                    <!-- Kullanıcılar JavaScript ile eklenecek -->
                </ul>
                
                <h3><i class="fas fa-shield-alt"></i> Güvenlik Durumu</h3>
                <div class="bot-warning">
                    <i class="fas fa-check-circle"></i> Key-Value DB: Aktif
                </div>
                <div class="bot-warning">
                    <i class="fas fa-check-circle"></i> Kötü dil filtresi: Aktif
                </div>
                <div class="bot-warning">
                    <i class="fas fa-check-circle"></i> Spam koruması: Aktif
                </div>
            </div>

            <!-- Sohbet Alanı -->
            <div class="chat-area">
                <div class="chat-messages" id="chatMessages">
                    <!-- Mesajlar JavaScript ile eklenecek -->
                </div>

                <!-- Mesaj Girişi -->
                <div class="chat-input">
                    <input type="text" id="messageInput" placeholder="Mesajınızı yazın...">
                    <button id="sendMessageBtn"><i class="fas fa-paper-plane"></i> Gönder</button>
                </div>
            </div>
        </div>

        <!-- Admin Panel -->
        <div class="admin-panel" id="adminPanel">
            <button class="admin-close" id="adminClose">&times;</button>
            <h2><i class="fas fa-crown"></i> Yönetici Paneli</h2>
            
            <div class="admin-section">
                <h3><i class="fas fa-bullhorn"></i> Duyuru Yap</h3>
                <input type="text" id="announcementInput" placeholder="Duyuru metni" style="width: 100%; padding: 0.5rem; margin-bottom: 0.5rem; background: #2e3440; color: #eceff4; border: 1px solid #4c566a; border-radius: 4px;">
                <button class="btn" id="sendAnnouncementBtn">Duyuru Gönder</button>
            </div>
            
            <div class="admin-section">
                <h3><i class="fas fa-user-cog"></i> Kullanıcı İşlemleri</h3>
                <select id="userSelect" style="width: 100%; padding: 0.5rem; margin-bottom: 0.5rem; background: #2e3440; color: #eceff4; border: 1px solid #4c566a; border-radius: 4px;">
                    <!-- Kullanıcılar JavaScript ile eklenecek -->
                </select>
                <button class="admin-btn btn-danger" id="banUserBtn"><i class="fas fa-ban"></i> Banla</button>
                <button class="admin-btn btn-warning" id="muteUserBtn"><i class="fas fa-volume-mute"></i> Sustur</button>
            </div>
            
            <div class="admin-section">
                <h3><i class="fas fa-database"></i> Key-Value Veritabanı</h3>
                <button class="btn" id="viewDatabaseBtn">Veritabanını Görüntüle</button>
                <div id="databaseContainer" style="margin-top: 0.5rem; display: none;"></div>
            </div>
            
            <div class="admin-section">
                <h3><i class="fas fa-info-circle"></i> Sistem Bilgisi</h3>
                <p>Kurucular: Lyrex ve Vaynes</p>
                <p>Kullanıcı Sayısı: <span id="userCount">0</span></p>
                <p>Aktif Sohbetler: <span id="activeChats">0</span></p>
                <p>Toplam Mesaj: <span id="totalMessages">0</span></p>
            </div>
        </div>
    </div>

    <script>
        // Key-Value Veritabanı Benzetimi
        const Database = {
            // Kullanıcıları saklamak için users key'i
            users: JSON.parse(localStorage.getItem('chatUsers')) || [],
            
            // Mesajları saklamak için messages key'i
            messages: JSON.parse(localStorage.getItem('chatMessages')) || [],
            
            // Sistem ayarları için settings key'i
            settings: JSON.parse(localStorage.getItem('chatSettings')) || {
                badWords: ["küfür", "argo", "hakaret", "kötükelime"],
                maxMessageLength: 500,
                spamProtection: true,
                allowRegistration: true
            },
            
            // Key'e göre değer getirme
            get: function(key) {
                return this[key];
            },
            
            // Key'e değer atama
            set: function(key, value) {
                this[key] = value;
                localStorage.setItem(`chat${key.charAt(0).toUpperCase() + key.slice(1)}`, JSON.stringify(value));
            },
            
            // Key'e öğe ekleme
            add: function(key, item) {
                if (!this[key]) this[key] = [];
                this[key].push(item);
                this.set(key, this[key]);
            },
            
            // Key'den öğe kaldırma
            remove: function(key, predicate) {
                if (!this[key]) return;
                const index = this[key].findIndex(predicate);
                if (index !== -1) {
                    this[key].splice(index, 1);
                    this.set(key, this[key]);
                }
            },
            
            // Key'de öğe arama
            find: function(key, predicate) {
                if (!this[key]) return null;
                return this[key].find(predicate);
            },
            
            // Key'de filtreleme
            filter: function(key, predicate) {
                if (!this[key]) return [];
                return this[key].filter(predicate);
            }
        };

        document.addEventListener('DOMContentLoaded', function() {
            // DOM Elements
            const authContainer = document.getElementById('authContainer');
            const app = document.getElementById('app');
            const loginTab = document.getElementById('loginTab');
            const registerTab = document.getElementById('registerTab');
            const loginForm = document.getElementById('loginForm');
            const registerForm = document.getElementById('registerForm');
            const loginBtn = document.getElementById('loginBtn');
            const registerBtn = document.getElementById('registerBtn');
            const logoutBtn = document.getElementById('logoutBtn');
            const shareBtn = document.getElementById('shareBtn');
            const loginUsername = document.getElementById('loginUsername');
            const loginPassword = document.getElementById('loginPassword');
            const registerUsername = document.getElementById('registerUsername');
            const registerPassword = document.getElementById('registerPassword');
            const registerPasswordConfirm = document.getElementById('registerPasswordConfirm');
            const currentUsername = document.getElementById('currentUsername');
            const messageInput = document.getElementById('messageInput');
            const sendMessageBtn = document.getElementById('sendMessageBtn');
            const chatMessages = document.getElementById('chatMessages');
            const onlineUsers = document.getElementById('onlineUsers');
            const adminToggle = document.getElementById('adminToggle');
            const adminPanel = document.getElementById('adminPanel');
            const adminClose = document.getElementById('adminClose');
            const sendAnnouncementBtn = document.getElementById('sendAnnouncementBtn');
            const announcementInput = document.getElementById('announcementInput');
            const viewDatabaseBtn = document.getElementById('viewDatabaseBtn');
            const databaseContainer = document.getElementById('databaseContainer');
            const userSelect = document.getElementById('userSelect');
            const banUserBtn = document.getElementById('banUserBtn');
            const muteUserBtn = document.getElementById('muteUserBtn');
            const userCount = document.getElementById('userCount');
            const activeChats = document.getElementById('activeChats');
            const totalMessages = document.getElementById('totalMessages');
            
            let currentUser = null;
            let isAdminPanelOpen = false;
            let lastMessageTime = 0;
            let messageCount = Database.get('messages').length;
            
            // Tab değiştirme
            loginTab.addEventListener('click', function() {
                loginTab.classList.add('active');
                registerTab.classList.remove('active');
                loginForm.style.display = 'block';
                registerForm.style.display = 'none';
            });
            
            registerTab.addEventListener('click', function() {
                registerTab.classList.add('active');
                loginTab.classList.remove('active');
                registerForm.style.display = 'block';
                loginForm.style.display = 'none';
            });
            
            // Kayıt ol butonu
            registerBtn.addEventListener('click', function() {
                const username = registerUsername.value.trim();
                const password = registerPassword.value.trim();
                const passwordConfirm = registerPasswordConfirm.value.trim();
                
                if (!username || !password || !passwordConfirm) {
                    alert('Lütfen tüm alanları doldurunuz.');
                    return;
                }
                
                if (password.length < 6) {
                    alert('Şifre en az 6 karakter olmalıdır!');
                    return;
                }
                
                if (password !== passwordConfirm) {
                    alert('Şifreler eşleşmiyor!');
                    return;
                }
                
                // Kullanıcı adı kontrolü - Key-Value kullanımı
                if (Database.find('users', user => user.username === username)) {
                    alert('Bu kullanıcı adı zaten alınmış!');
                    return;
                }
                
                // Yeni kullanıcı oluştur - Key-Value kullanımı
                const newUser = {
                    id: Date.now().toString(),
                    username,
                    password,
                    isOnline: true,
                    isAdmin: (username === 'Lyrex' || username === 'Vaynes'),
                    isMuted: false,
                    joinDate: new Date().toISOString()
                };
                
                Database.add('users', newUser);
                
                currentUser = newUser;
                currentUsername.textContent = currentUser.username;
                authContainer.style.display = 'none';
                app.style.display = 'flex';
                
                // Admin kontrolü
                if (currentUser.isAdmin) {
                    adminToggle.style.display = 'block';
                }
                
                // Hoş geldin mesajı - Key-Value kullanımı
                addMessage('Sistem', `${currentUser.username} sohbete katıldı!`, false);
                updateOnlineUsers();
            });
            
            // Giriş yap butonu
            loginBtn.addEventListener('click', function() {
                const username = loginUsername.value.trim();
                const password = loginPassword.value.trim();
                
                if (!username || !password) {
                    alert('Lütfen kullanıcı adı ve şifre giriniz.');
                    return;
                }
                
                // Kullanıcıyı kontrol et - Key-Value kullanımı
                const user = Database.find('users', u => u.username === username && u.password === password);
                
                if (user) {
                    if (user.isMuted) {
                        alert('Hesabınız susturulmuş. Mesaj gönderemezsiniz.');
                    }
                    
                    // Giriş başarılı
                    currentUser = user;
                    currentUser.isOnline = true;
                    Database.set('users', Database.get('users').map(u => 
                        u.id === user.id ? {...u, isOnline: true} : u
                    ));
                    
                    currentUsername.textContent = currentUser.username;
                    authContainer.style.display = 'none';
                    app.style.display = 'flex';
                    
                    // Admin kontrolü
                    if (currentUser.isAdmin) {
                        adminToggle.style.display = 'block';
                    }
                    
                    // Hoş geldin mesajı - Key-Value kullanımı
                    addMessage('Sistem', `${currentUser.username} sohbete tekrar katıldı!`, false);
                    updateOnlineUsers();
                } else {
                    alert('Kullanıcı adı veya şifre hatalı!');
                }
            });
            
            // Çıkış butonu
            logoutBtn.addEventListener('click', function() {
                if (currentUser) {
                    // Kullanıcı durumunu güncelle - Key-Value kullanımı
                    Database.set('users', Database.get('users').map(u => 
                        u.id === currentUser.id ? {...u, isOnline: false} : u
                    ));
                }
                
                authContainer.style.display = 'flex';
                app.style.display = 'none';
                currentUser = null;
                updateOnlineUsers();
            });
            
            // Paylaş butonu
            shareBtn.addEventListener('click', function() {
                // Mevcut URL'yi kopyala
                const url = window.location.href;
                
                // Panoya kopyala
                navigator.clipboard.writeText(url).then(() => {
                    alert('Bağlantı panoya kopyalandı! Arkadaşlarınıza gönderebilirsiniz: ' + url);
                }).catch(err => {
                    alert('Bağlantıyı kopyalama hatası: ' + err);
                });
            });
            
            // Mesaj gönderme
            sendMessageBtn.addEventListener('click', function() {
                sendMessage();
            });
            
            messageInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    sendMessage();
                }
            });
            
            function sendMessage() {
                const messageText = messageInput.value.trim();
                
                if (!messageText || !currentUser) return;
                
                // Susturulma kontrolü
                if (currentUser.isMuted) {
                    alert('Susturulmuş kullanıcılar mesaj gönderemez!');
                    return;
                }
                
                // Spam koruması
                const now = Date.now();
                if (now - lastMessageTime < 1000) {
                    alert('Çok hızlı mesaj gönderiyorsunuz. Lütfen bekleyin.');
                    return;
                }
                
                // Kötü dil filtresi - Key-Value kullanımı
                const badWords = Database.get('settings').badWords;
                if (containsBadWords(messageText, badWords)) {
                    alert('Mesajınız uygun olmayan içerik içeriyor!');
                    return;
                }
                
                lastMessageTime = now;
                messageCount++;
                
                // Etiket kontrolü
                let formattedMessage = messageText;
                if (messageText.includes('@')) {
                    formattedMessage = formatMentions(messageText);
                }
                
                // Mesajı ekrana ekle
                addMessage(currentUser.username, formattedMessage, true);
                
                // Mesajı veritabanına kaydet - Key-Value kullanımı
                Database.add('messages', {
                    id: Date.now().toString(),
                    sender: currentUser.username,
                    content: messageText,
                    timestamp: new Date().toISOString(),
                    isSystem: false
                });
                
                // Input'u temizle
                messageInput.value = '';
                
                // Bot yanıtı simülasyonu
                if (messageCount % 5 === 0) {
                    setTimeout(() => {
                        addMessage('Sohbet Botu', 'Key-Value veritabanı ile güvenli sohbet!', false);
                        
                        // Sistem mesajını da veritabanına kaydet
                        Database.add('messages', {
                            id: Date.now().toString(),
                            sender: 'Sohbet Botu',
                            content: 'Key-Value veritabanı ile güvenli sohbet!',
                            timestamp: new Date().toISOString(),
                            isSystem: true
                        });
                    }, 1000);
                }
            }
            
            function containsBadWords(text, badWordsList) {
                const lowerText = text.toLowerCase();
                return badWordsList.some(word => lowerText.includes(word));
            }
            
            function addMessage(sender, message, isSent) {
                const messageEl = document.createElement('div');
                messageEl.classList.add('message');
                messageEl.classList.add(isSent ? 'sent' : 'received');
                
                // Eğer mesajda etiket varsa, özel stil uygula
                if (message.includes('mention')) {
                    messageEl.classList.add('mentioned');
                }
                
                // Sistem mesajı kontrolü
                if (sender === 'Sistem' || sender === 'Sohbet Botu') {
                    messageEl.classList.add('system-message');
                    messageEl.classList.remove('sent', 'received');
                }
                
                const now = new Date();
                const time = `${now.getHours().toString().padStart(2, '0')}:${now.getMinutes().toString().padStart(2, '0')}`;
                
                messageEl.innerHTML = `
                    <div class="message-header">
                        <span class="sender">${sender}</span>
                        <span class="time">${time}</span>
                    </div>
                    <div class="message-content">${message}</div>
                `;
                
                chatMessages.appendChild(messageEl);
                chatMessages.scrollTop = chatMessages.scrollHeight;
            }
            
            function formatMentions(text) {
                return text.replace(/@(\w+)/g, '<span class="mention">@$1</span>');
            }
            
            function updateOnlineUsers() {
                onlineUsers.innerHTML = '';
                userSelect.innerHTML = '';
                
                // Çevrimiçi kullanıcıları al - Key-Value kullanımı
                const onlineUsersList = Database.filter('users', user => user.isOnline);
                userCount.textContent = Database.get('users').length;
                activeChats.textContent = onlineUsersList.length;
                totalMessages.textContent = Database.get('messages').length;
                
                onlineUsersList.forEach(user => {
                    const li = document.createElement('li');
                    li.innerHTML = `<div class="user-status"></div> ${user.username} ${user.isAdmin ? '<i class="fas fa-crown" style="color: #f6c23e;"></i>' : ''}`;
                    onlineUsers.appendChild(li);
                    
                    const option = document.createElement('option');
                    option.value = user.username;
                    option.textContent = user.username;
                    userSelect.appendChild(option);
                });
            }
            
            // Admin paneli kontrolü
            adminToggle.addEventListener('click', function() {
                isAdminPanelOpen = !isAdminPanelOpen;
                adminPanel.style.display = isAdminPanelOpen ? 'block' : 'none';
            });
            
            adminClose.addEventListener('click', function() {
                adminPanel.style.display = 'none';
                isAdminPanelOpen = false;
            });
            
            // Duyuru gönderme
            sendAnnouncementBtn.addEventListener('click', function() {
                const announcement = announcementInput.value.trim();
                
                if (!announcement) return;
                
                addMessage('Sistem', `<strong>DUYURU: ${announcement}</strong>`, false);
                
                // Duyuruyu veritabanına kaydet - Key-Value kullanımı
                Database.add('messages', {
                    id: Date.now().toString(),
                    sender: 'Sistem',
                    content: `DUYURU: ${announcement}`,
                    timestamp: new Date().toISOString(),
                    isSystem: true
                });
                
                announcementInput.value = '';
            });
            
            // Veritabanını görüntüleme
            viewDatabaseBtn.addEventListener('click', function() {
                if (databaseContainer.style.display === 'none') {
                    let dbHTML = `
                        <h4>Kullanıcılar (${Database.get('users').length})</h4>
                        <pre>${JSON.stringify(Database.get('users'), null, 2)}</pre>
                        <h4>Mesajlar (${Database.get('messages').length})</h4>
                        <pre>${JSON.stringify(Database.get('messages').slice(-5), null, 2)}</pre>
                        <h4>Ayarlar</h4>
                        <pre>${JSON.stringify(Database.get('settings'), null, 2)}</pre>
                    `;
                    
                    databaseContainer.innerHTML = dbHTML;
                    databaseContainer.style.display = 'block';
                    viewDatabaseBtn.textContent = 'Veritabanını Gizle';
                } else {
                    databaseContainer.style.display = 'none';
                    viewDatabaseBtn.textContent = 'Veritabanını Görüntüle';
                }
            });
            
            // Kullanıcı banlama
            banUserBtn.addEventListener('click', function() {
                const selectedUser = userSelect.value;
                if (selectedUser && confirm(`${selectedUser} kullanıcısını banlamak istediğinize emin misiniz?`)) {
                    // Kullanıcıyı veritabanından kaldır - Key-Value kullanımı
                    Database.remove('users', user => user.username === selectedUser);
                    
                    updateOnlineUsers();
                    addMessage('Sistem', `${selectedUser} kullanıcısı banlandı!`, false);
                    
                    // Sisteme mesaj ekle
                    Database.add('messages', {
                        id: Date.now().toString(),
                        sender: 'Sistem',
                        content: `${selectedUser} kullanıcısı banlandı!`,
                        timestamp: new Date().toISOString(),
                        isSystem: true
                    });
                }
            });
            
            // Kullanıcı susturma
            muteUserBtn.addEventListener('click', function() {
                const selectedUser = userSelect.value;
                if (selectedUser) {
                    const user = Database.find('users', u => u.username === selectedUser);
                    if (user) {
                        // Kullanıcı susturma durumunu güncelle - Key-Value kullanımı
                        Database.set('users', Database.get('users').map(u => 
                            u.id === user.id ? {...u, isMuted: !u.isMuted} : u
                        ));
                        
                        addMessage('Sistem', `${selectedUser} kullanıcısı ${user.isMuted ? 'susturuldu' : 'susturması kaldırıldı'}!`, false);
                        
                        // Sisteme mesaj ekle
                        Database.add('messages', {
                            id: Date.now().toString(),
                            sender: 'Sistem',
                            content: `${selectedUser} kullanıcısı ${user.isMuted ? 'susturuldu' : 'susturması kaldırıldı'}!`,
                            timestamp: new Date().toISOString(),
                            isSystem: true
                        });
                    }
                }
            });
            
            // Örnek mesajlar ekle
            setTimeout(() => {
                addMessage('Sistem', 'Key-Value veritabanı ile gelişmiş sohbet uygulamasına hoşgeldiniz!', false);
                addMessage('Sistem', 'Bot koruması aktif! Kötü dil ve spam otomatik olarak filtrelenir.', false);
                addMessage('Sohbet Botu', 'Key-Value sistemi sayesinde tüm veriler güvende!', false);
                
                // Örnek mesajları veritabanına ekle
                Database.add('messages', {
                    id: Date.now().toString(),
                    sender: 'Sistem',
                    content: 'Key-Value veritabanı ile gelişmiş sohbet uygulamasına hoşgeldiniz!',
                    timestamp: new Date().toISOString(),
                    isSystem: true
                });
                
                Database.add('messages', {
                    id: Date.now().toString(),
                    sender: 'Sistem',
                    content: 'Bot koruması aktif! Kötü dil ve spam otomatik olarak filtrelenir.',
                    timestamp: new Date().toISOString(),
                    isSystem: true
                });
                
                Database.add('messages', {
                    id: Date.now().toString(),
                    sender: 'Sohbet Botu',
                    content: 'Key-Value sistemi sayesinde tüm veriler güvende!',
                    timestamp: new Date().toISOString(),
                    isSystem: true
                });
            }, 500);
            
            // İlk yüklemede çevrimiçi kullanıcıları güncelle
            updateOnlineUsers();
            
            // Mevcut mesajları yükle
            Database.get('messages').forEach(msg => {
                addMessage(msg.sender, msg.content, msg.sender === currentUser?.username);
            });
        });
    </script>
</body>
</html>
