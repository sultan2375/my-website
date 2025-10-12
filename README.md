# my-website<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Earn & Reward App</title>
    
    <!-- Google Fonts (Nunito) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700&display=swap" rel="stylesheet">
    
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css" />

    <!-- Internal CSS -->
    <style>
        /* Google Font Import */
        @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700&display=swap');

        /* CSS Variables for Theming */
        :root {
            --font-family: 'Nunito', sans-serif;
            --bg-color-light: #f4f4f9;
            --secondary-bg-light: #ffffff;
            --text-color-light: #1c1c1e;
            --subtle-text-light: #6d6d72;
            --primary-color-light: #007aff;
            --border-color-light: #e0e0e0;
            --bg-color-dark: #121212;
            --secondary-bg-dark: #1c1c1e;
            --text-color-dark: #ffffff;
            --subtle-text-dark: #8e8e93;
            --primary-color-dark: #0a84ff;
            --border-color-dark: #38383a;
        }

        /* Base Styles */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: var(--font-family);
            transition: background-color 0.3s, color 0.3s;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* Theme Styles */
        body.light-theme { background-color: var(--bg-color-light); color: var(--text-color-light); }
        body.dark-theme { background-color: var(--bg-color-dark); color: var(--text-color-dark); }
        #app { max-width: 500px; margin: 0 auto; padding-bottom: 70px; }

        /* Profile Header */
        .profile-header { padding: 20px 15px; display: flex; align-items: center; border-bottom: 1px solid; }
        .light-theme .profile-header { border-bottom-color: var(--border-color-light); }
        .dark-theme .profile-header { border-bottom-color: var(--border-color-dark); }
        .profile-info { display: flex; align-items: center; gap: 15px; }
        #user-photo { width: 60px; height: 60px; border-radius: 50%; object-fit: cover; border: 2px solid; }
        .light-theme #user-photo { border-color: var(--primary-color-light); }
        .dark-theme #user-photo { border-color: var(--primary-color-dark); }
        .user-details h1 { font-size: 1.2rem; font-weight: 700; }
        .verified-icon { font-size: 1rem; margin-left: 5px; }
        .light-theme .verified-icon { color: var(--primary-color-light); }
        .dark-theme .verified-icon { color: var(--primary-color-dark); }
        .user-details p { font-size: 0.9rem; font-weight: 600; }
        .light-theme .user-details p { color: var(--subtle-text-light); }
        .dark-theme .user-details p { color: var(--subtle-text-dark); }

        /* Main Content & Pages */
        main { padding: 15px; }
        .page { display: none; }
        .page.active { display: block; animation: fadeIn 0.3s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        h2 { font-size: 1.5rem; margin-bottom: 15px; }

        /* Home Page Stats & Referral */
        .stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-top: 20px; }
        .stat-card { padding: 20px; border-radius: 12px; text-align: center; }
        .light-theme .stat-card { background-color: var(--secondary-bg-light); border: 1px solid var(--border-color-light); }
        .dark-theme .stat-card { background-color: var(--secondary-bg-dark); border: 1px solid var(--border-color-dark); }
        .stat-card h3 { font-size: 0.9rem; margin-bottom: 10px; }
        .light-theme .stat-card h3 { color: var(--subtle-text-light); }
        .dark-theme .stat-card h3 { color: var(--subtle-text-dark); }
        .stat-card p { font-size: 1.5rem; font-weight: 700; }
        .light-theme .stat-card p { color: var(--primary-color-light); }
        .dark-theme .stat-card p { color: var(--primary-color-dark); }
        .referral-section { margin-top: 30px; padding: 20px; border-radius: 12px; }
        .light-theme .referral-section { background-color: var(--secondary-bg-light); border: 1px solid var(--border-color-light); }
        .dark-theme .referral-section { background-color: var(--secondary-bg-dark); border: 1px solid var(--border-color-dark); }
        .referral-section h3 { text-align: center; }
        #referral-link { width: 100%; padding: 10px; text-align: center; border: 1px dashed; border-radius: 8px; margin: 10px 0; font-size: 0.9rem; }
        .light-theme #referral-link { border-color: var(--primary-color-light); background-color: var(--bg-color-light); color: var(--text-color-light); }
        .dark-theme #referral-link { border-color: var(--primary-color-dark); background-color: var(--bg-color-dark); color: var(--text-color-dark); }
        #copy-ref-link-btn { width: 100%; padding: 12px; border: none; border-radius: 8px; color: #fff; cursor: pointer; font-weight: 600; }
        .light-theme #copy-ref-link-btn { background-color: var(--primary-color-light); }
        .dark-theme #copy-ref-link-btn { background-color: var(--primary-color-dark); }
        
        /* Task/Bonus Container */
        .task-container { padding: 20px; border-radius: 12px; text-align: center; margin-bottom: 20px; }
        .task-container:last-child { margin-bottom: 0; }
        .light-theme .task-container { background-color: var(--secondary-bg-light); border: 1px solid var(--border-color-light); }
        .dark-theme .task-container { background-color: var(--secondary-bg-dark); border: 1px solid var(--border-color-dark); }
        .task-icon { font-size: 3rem; margin-bottom: 15px; }
        .light-theme .task-icon { color: var(--primary-color-light); }
        .dark-theme .task-icon { color: var(--primary-color-dark); }
        .task-container h3 { font-size: 1.2rem; margin-bottom: 5px; }
        .task-container p { font-size: 0.9rem; margin-bottom: 20px; }
        .light-theme .task-container p { color: var(--subtle-text-light); }
        .dark-theme .task-container p { color: var(--subtle-text-dark); }

        /* Action Button */
        .action-btn { width: 100%; padding: 15px; font-size: 1rem; font-weight: 700; color: #fff; border: none; border-radius: 10px; cursor: pointer; transition: background-color 0.2s, opacity 0.2s; position: relative; display: flex; justify-content: center; align-items: center; }
        .light-theme .action-btn { background-color: var(--primary-color-light); }
        .dark-theme .action-btn { background-color: var(--primary-color-dark); }
        .action-btn:disabled { opacity: 0.6; cursor: not-allowed; }
        .btn-loader { width: 20px; height: 20px; border: 3px solid rgba(255, 255, 255, 0.4); border-top-color: #fff; border-radius: 50%; animation: spin 1s linear infinite; display: none; }
        .action-btn.loading .btn-text { visibility: hidden; }
        .action-btn.loading .btn-loader { display: block; position: absolute; }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        /* Form Styles */
        #withdraw-form .form-group { margin-bottom: 15px; }
        #withdraw-form label { display: block; margin-bottom: 5px; font-weight: 600; }
        #withdraw-form input, #withdraw-form select { width: 100%; padding: 12px; border-radius: 8px; font-family: var(--font-family); font-size: 1rem; transition: border-color 0.2s, box-shadow 0.2s; }
        .light-theme #withdraw-form input, .light-theme #withdraw-form select { background-color: var(--bg-color-light); border: 1px solid var(--border-color-light); color: var(--text-color-light); }
        .dark-theme #withdraw-form input, .dark-theme #withdraw-form select { background-color: var(--secondary-bg-dark); border: 1px solid var(--border-color-dark); color: var(--text-color-dark); }
        .light-theme input:focus, .light-theme select:focus { outline: none; border-color: var(--primary-color-light); box-shadow: 0 0 0 3px rgba(0, 122, 255, 0.15); }
        .dark-theme input:focus, .dark-theme select:focus { outline: none; border-color: var(--primary-color-dark); box-shadow: 0 0 0 3px rgba(10, 132, 255, 0.2); }
        
        /* Bottom Navigation */
        .bottom-nav { position: fixed; bottom: 0; left: 0; right: 0; max-width: 500px; margin: 0 auto; display: flex; justify-content: space-around; padding: 5px 0; border-top: 1px solid; z-index: 1000; }
        .light-theme .bottom-nav { background-color: var(--secondary-bg-light); border-top-color: var(--border-color-light); }
        .dark-theme .bottom-nav { background-color: var(--secondary-bg-dark); border-top-color: var(--border-color-dark); }
        .nav-btn { background: none; border: none; cursor: pointer; display: flex; flex-direction: column; align-items: center; padding: 5px 10px; font-family: var(--font-family); font-size: 0.7rem; transition: color 0.2s; flex-grow: 1; }
        .light-theme .nav-btn { color: var(--subtle-text-light); }
        .dark-theme .nav-btn { color: var(--subtle-text-dark); }
        .nav-btn i { font-size: 1.4rem; margin-bottom: 3px; }
        .nav-btn.active { font-weight: 700; }
        .light-theme .nav-btn.active { color: var(--primary-color-light); }
        .dark-theme .nav-btn.active { color: var(--primary-color-dark); }

        /* Modal Styles */
        .modal { display: none; position: fixed; z-index: 2000; left: 0; top: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.6); justify-content: center; align-items: center; }
        .modal-content { padding: 30px; border-radius: 15px; text-align: center; }
        .light-theme .modal-content { background-color: var(--secondary-bg-light); }
        .dark-theme .modal-content { background-color: var(--secondary-bg-dark); }
        .loader { border: 5px solid #f3f3f3; border-radius: 50%; border-top: 5px solid; width: 40px; height: 40px; animation: spin 1s linear infinite; margin: 0 auto 15px; }
        .light-theme .loader { border-top-color: var(--primary-color-light); }
        .dark-theme .loader { border-top-color: var(--primary-color-dark); }
    </style>
</head>
<body>

    <div id="app">
        <header class="profile-header">
            <div class="profile-info">
                <img id="user-photo" src="" alt="User Photo">
                <div class="user-details">
                    <h1 id="user-name">Loading... <i class="fas fa-check-circle verified-icon"></i></h1>
                    <p>Balince: $<span id="user-BDT">0</span>BDT</p>
                </div>
            </div>
        </header>

        <main id="main-content">
            <!-- Home Page -->
            <div id="home-page" class="page active">
                <h2>Dashboard</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <h3>Daily Ads Watched</h3>
                        <p><span id="daily-ads-watched">00</span> /  10</p>
                    </div>
                    <div class="stat-card">
                        <h3>Total Referrals</h3>
                        <p id="referral-count">00</p>
                    </div>
                </div>
                <div class="referral-section">
                    <h3>Refer & Earn More!</h3>
                    <p>Share your link to get bonus BDT.</p>
                    <input type="text" id="referral-link" readonly>
                    <button id="copy-ref-link-btn">Copy Referral Link</button>
                </div>
            </div>

            <!-- Tasks Page -->
            <div id="tasks-page" class="page">
                <h2>Complete Tasks</h2>
                <div class="task-container">
                    <i class="fas fa-video task-icon"></i>
                    <h3>Watch a Rewarded Ad</h3>
                    <p>Earn 2 BDT for every ad.</p>
                    <button id="watch-ad-btn" class="action-btn">Watch Ad</button>
                </div>
                <div class="task-container">
                    <i class="fab fa-telegram task-icon"></i>
                    <h3>Join Our Channel</h3>
                    <p>Get 5.00 bonus BDT.</p>
                    <button id="join-channel-btn" class="action-btn">Join & Claim Bonus</button>
                </div>
                <div class="task-container">
                    <i class="fas fa-users task-icon"></i>
                    <h3>Join Our Channel</h3>
                    <p>Get 5.00 bonus BDT.</p>
                    <button id="join-group-btn" class="action-btn">Join & Claim Bonus</button>
                </div>
            </div>
            
            <!-- Withdraw Page -->
            <div id="withdraw-page" class="page">
                <h2>Withdraw BDT</h2>
                <p>Minimum 50 BDT 5 Refer required to withdraw.</p>
                <form id="withdraw-form">
                    <div class="form-group">
                        <label for="withdraw-method">Method:</label>
                        <select id="withdraw-method" required>
                            <option value="Bkash">Bkash</option>
                            <option value="Nagad">Nagad</option>
                     </select>
                    </div>
                    <div class="form-group">
                        <label for="account-number">Account Number/ID:</label>
                        <input type="text" id="account-number" placeholder="       " required>
                    </div>
                    <div class="form-group">
                        <label for="amount">BDT to Withdraw:</label>
                        <input type="number" id="amount" placeholder="    " required>
                    </div>
                    <button type="submit" id="withdraw-submit-btn" class="action-btn">
                        <span class="btn-text">Submit Request</span>
                        <span class="btn-loader"></span>
                    </button>
                </form>
            </div>
        </main>

        <nav class="bottom-nav">
            <button class="nav-btn active" data-page="home-page"><i class="fas fa-home"></i><span>Home</span></button>
            <button class="nav-btn" data-page="tasks-page"><i class="fas fa-tasks"></i><span>Tasks</span></button>
            <button class="nav-btn" data-page="withdraw-page"><i class="fas fa-wallet"></i><span>Withdraw</span></button>
        </nav>
    </div>

    <div id="loading-modal" class="modal">
        <div class="modal-content"><div class="loader"></div><p>Loading Ad...</p></div>
    </div>
    
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <script type='text/javascript' src='//pl27826491.effectivegatecpm.com/32/7b/b3/327bb3662572d7ae69a34c0aeb78a858.js'></script>
    
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const tg = window.Telegram.WebApp;

            // --- Configuration ---
            const BOT_TOKEN = "8306356638:AAGklBM06-dyd9i_Cp3ZM2Y3BInGoulQ2_Y";
            const BOT_USERNAME = "http://t.me/cashmate112_bot"; // Your bot's username
            const ADMIN_CHAT_ID = "6203336796";
            const UPDATE_CHANNEL_ = "https://t.me/crypto2211866";
            const CHANNEL_LINK = "https://t.me/clickadsbd11";
            const DAILY_AD_LIMIT = 10;
            const BDT_PER_AD = 2.00;
            const CHANNEL_JOIN_BONUS = 5.00;
            const GROUP_JOIN_BONUS = 5.00;
            const MIN_WITHDRAW_BDT = 50;
           
            // --- DOM Elements ---
            const userPhotoElem = document.getElementById('user-photo');
            const userNameElem = document.getElementById('user-name');
            const userBDTElem = document.getElementById('user-BDT');
            const dailyAdsWatchedElem = document.getElementById('daily-ads-watched');
            const referralCountElem = document.getElementById('referral-count');
            const watchAdBtn = document.getElementById('watch-ad-btn');
            const joinChannelBtn = document.getElementById('join-channel-btn');
            const joinGroupBtn = document.getElementById('join-group-btn');
            const withdrawForm = document.getElementById('withdraw-form');
            const withdrawSubmitBtn = document.getElementById('withdraw-submit-btn');
            const referralLinkElem = document.getElementById('referral-link');
            const copyRefLinkBtn = document.getElementById('copy-ref-link-btn');
            const loadingModal = document.getElementById('loading-modal');

            // --- State Management ---
            let userState = {
                BDT: 0,
                dailyAdWatchCount: 0,
                lastAdWatchDate: null,
                referrals: [],
                hasJoinedChannel: false,
                hasJoinedGroup: false, // New state for group join
                userId: null
            };

            const saveState = () => {
                if(userState.userId) {
                    localStorage.setItem(`userState_${userState.userId}`, JSON.stringify(userState));
                }
            };

            const loadState = (userId) => {
                const savedState = localStorage.getItem(`userState_${userId}`);
                if (savedState) {
                    userState = JSON.parse(savedState);
                    // Ensure new state properties exist
                    if (userState.hasJoinedGroup === undefined) userState.hasJoinedGroup = false;
                }
            };
            
            // --- Core Functions ---
            const initApp = () => {
                tg.ready();
                tg.expand();
                document.body.className = `${tg.colorScheme}-theme`;

                const user = tg.initDataUnsafe.user;
                if (!user || !user.id) {
                    tg.showAlert("Could not verify user. Please open this app through Telegram.", () => tg.close());
                    return;
                }
                
                userState.userId = user.id;
                loadState(user.id);
                
                const today = new Date().toISOString().slice(0, 10);
                if (userState.lastAdWatchDate !== today) {
                    userState.dailyAdWatchCount = 0;
                    userState.lastAdWatchDate = today;
                }
                
                updateUI();
                setupNavigation();
                setupEventListeners();
                saveState();
            };
            
            const updateUI = () => {
                const user = tg.initDataUnsafe.user;
                if (user) {
                    userPhotoElem.src = user.photo_url || 'https://i.imgur.com/placeholder.png';
                    userNameElem.innerHTML = `${user.first_name || ''} ${user.last_name || ''} <i class="fas fa-check-circle verified-icon"></i>`;
                }
                
                userBDTElem.textContent = userState.BDT;
                dailyAdsWatchedElem.textContent = userState.dailyAdWatchCount;
                referralCountElem.textContent = userState.referrals.length;

                referralLinkElem.value = `https://t.me/${BOT_USERNAME}?start=ref_${userState.userId}`;

                // Update task button states
                if (userState.hasJoinedChannel) {
                    joinChannelBtn.textContent = 'Bonus Claimed';
                    joinChannelBtn.disabled = true;
                }
                if (userState.h
