<!DOCTYPE html>
<html lang="am">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>Green Plant - ኢንቨስትመንት</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: #eef5e8;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding-bottom: 70px;
        }
        .app-container {
            max-width: 500px;
            margin: 0 auto;
            background: #ffffff;
            min-height: 100vh;
            box-shadow: 0 0 20px rgba(0,0,0,0.05);
            position: relative;
        }
        .auth-card {
            padding: 30px 20px;
        }
        .auth-header {
            text-align: center;
            margin-bottom: 30px;
        }
        .auth-header h1 {
            color: #2b6e3c;
            font-size: 2rem;
        }
        .toggle-buttons {
            display: flex;
            gap: 15px;
            margin-bottom: 25px;
            border-bottom: 2px solid #ddd;
        }
        .toggle-btn {
            flex: 1;
            text-align: center;
            padding: 12px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            color: #888;
        }
        .toggle-btn.active {
            color: #2b6e3c;
            border-bottom: 3px solid #2b6e3c;
        }
        .form-group {
            margin-bottom: 20px;
        }
        input {
            width: 100%;
            padding: 14px;
            border: 1px solid #ccc;
            border-radius: 60px;
            font-size: 1rem;
            outline: none;
        }
        button {
            width: 100%;
            padding: 14px;
            background: #2b6e3c;
            color: white;
            border: none;
            border-radius: 60px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
        }
        .error {
            color: #d32f2f;
            font-size: 0.8rem;
            text-align: center;
            margin-top: 8px;
        }
        .dashboard {
            display: none;
        }
        .top-bar {
            background: #2b6e3c;
            padding: 20px 16px 12px;
            color: white;
        }
        .greeting {
            font-size: 1.2rem;
            font-weight: bold;
        }
        .logout-link {
            text-align: right;
            font-size: 0.7rem;
            margin: 10px 16px;
            cursor: pointer;
            color: #b85c00;
        }
        .shortcuts {
            display: flex;
            justify-content: space-around;
            background: white;
            padding: 20px 10px;
            border-bottom: 1px solid #eee;
        }
        .shortcut-item {
            text-align: center;
            cursor: pointer;
        }
        .shortcut-icon {
            background: #f0f7ec;
            width: 55px;
            height: 55px;
            border-radius: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 8px;
            font-size: 1.8rem;
            color: #2b6e3c;
        }
        .shortcut-label {
            font-size: 0.75rem;
            font-weight: 500;
            color: #333;
        }
        .people-section {
            padding: 16px;
        }
        .section-title {
            font-size: 1rem;
            font-weight: bold;
            margin-bottom: 12px;
            color: #2b6e3c;
        }
        .people-scroll {
            display: flex;
            gap: 15px;
            overflow-x: auto;
        }
        .person-card {
            flex: 0 0 80px;
            text-align: center;
        }
        .person-avatar {
            width: 70px;
            height: 70px;
            background: #d9e6c3;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            color: #2b6e3c;
            margin-bottom: 5px;
        }
        .person-name {
            font-size: 0.7rem;
            color: #555;
        }
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            max-width: 500px;
            margin: 0 auto;
            background: white;
            display: flex;
            justify-content: space-around;
            padding: 10px 0 20px;
            border-top: 1px solid #eee;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.05);
        }
        .nav-item {
            text-align: center;
            cursor: pointer;
            flex: 1;
            color: #888;
        }
        .nav-item i {
            font-size: 1.5rem;
            display: block;
            margin-bottom: 4px;
        }
        .nav-item span {
            font-size: 0.7rem;
        }
        .nav-item.active {
            color: #2b6e3c;
        }
        .panel {
            display: none;
            padding: 16px;
        }
        .panel.active-panel {
            display: block;
        }
        .withdraw-card, .bank-card-form {
            background: #f9f9f9;
            border-radius: 28px;
            padding: 20px;
            margin-bottom: 20px;
        }
        .amount-input {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 15px 0;
        }
        .amount-input input {
            flex: 1;
        }
        .wallet-row {
            background: white;
            border-radius: 60px;
            padding: 12px 16px;
            margin: 15px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            border: 1px solid #ddd;
        }
        .bank-name-field {
            position: relative;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .bank-name-field input {
            flex: 1;
        }
        .dots-btn {
            background: #e0e0e0;
            border: none;
            width: 44px;
            border-radius: 60px;
            font-size: 1.4rem;
            cursor: pointer;
            margin-top: 0;
        }
        .bank-list {
            position: absolute;
            top: 60px;
            left: 0;
            right: 0;
            background: white;
            border-radius: 28px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
            z-index: 100;
            max-height: 250px;
            overflow-y: auto;
        }
        .bank-list div {
            padding: 12px 16px;
            border-bottom: 1px solid #eee;
            cursor: pointer;
        }
        .bank-list div:hover {
            background: #f0f7ec;
        }
        .hide {
            display: none;
        }
        .service-option {
            background: #e9f5e8;
            border-radius: 60px;
            padding: 15px;
            margin: 15px 0;
            text-align: center;
            cursor: pointer;
            font-weight: bold;
        }
        .payment-option {
            background: #f9f9f9;
            border: 1px solid #c8e6c9;
            border-radius: 60px;
            padding: 12px;
            margin: 12px 0;
            cursor: pointer;
            text-align: center;
            font-weight: bold;
        }
        .bank-detail {
            background: #fff3e0;
            border-radius: 28px;
            padding: 15px;
            margin-top: 15px;
            border-left: 5px solid #ff9800;
        }
        .deposit-form {
            margin-top: 15px;
        }
        .deposit-form input {
            margin-bottom: 12px;
        }
        hr {
            margin: 12px 0;
        }
        .copy-btn {
            background: #2b6e3c;
            padding: 4px 12px;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            display: inline-block;
            margin-left: 10px;
            font-size: 0.7rem;
        }
    </style>
</head>
<body>
<div class="app-container">
    <!-- Auth Section -->
    <div id="authSection">
        <div class="auth-card">
            <div class="auth-header"><h1>🌿 GREEN PLANT</h1><p>ትርፋማ ኢንቨስትመንት</p></div>
            <div class="toggle-buttons">
                <div id="loginTab" class="toggle-btn active">LOG IN</div>
                <div id="registerTab" class="toggle-btn">REGISTER</div>
            </div>
            <div id="loginForm">
                <div class="form-group"><input type="tel" id="loginPhone" placeholder="ስልክ ቁጥር (09XXXXXXXX)"></div>
                <div class="form-group"><input type="password" id="loginPassword" placeholder="የይለፍ ቃል"></div>
                <button id="doLoginBtn">LOG IN</button>
                <div id="loginError" class="error"></div>
            </div>
            <div id="registerForm" style="display:none;">
                <div class="form-group"><input type="tel" id="regPhone" placeholder="ስልክ ቁጥር (09XXXXXXXX)"></div>
                <div class="form-group"><input type="password" id="regPassword" placeholder="የይለፍ ቃል"></div>
                <div class="form-group"><input type="password" id="regConfirm" placeholder="የይለፍ ቃል ድገም"></div>
                <button id="doRegisterBtn">CREATE ACCOUNT</button>
                <div id="regError" class="error"></div>
            </div>
        </div>
    </div>

    <!-- Dashboard -->
    <div id="dashboard" class="dashboard">
        <div class="top-bar"><div class="greeting" id="greetingText">🌱 እንኳን ደህና መጣህ!</div></div>
        <div class="logout-link" id="logoutBtn">← ውጣ (Logout)</div>

        <div class="shortcuts">
            <div class="shortcut-item" data-action="recharge"><div class="shortcut-icon"><i class="fas fa-download"></i></div><div class="shortcut-label">Recharge</div></div>
            <div class="shortcut-item" data-action="withdraw"><div class="shortcut-icon"><i class="fas fa-upload"></i></div><div class="shortcut-label">Withdrawal</div></div>
            <div class="shortcut-item" data-action="myorder"><div class="shortcut-icon"><i class="fas fa-shopping-bag"></i></div><div class="shortcut-label">My Order</div></div>
            <div class="shortcut-item" data-action="service"><div class="shortcut-icon"><i class="fas fa-headset"></i></div><div class="shortcut-label">Service</div></div>
        </div>

        <div class="people-section">
            <div class="section-title"><i class="fas fa-users"></i> ኢንቨስተሮች</div>
            <div class="people-scroll">
                <div class="person-card"><div class="person-avatar"><i class="fas fa-user-circle"></i></div><div class="person-name">አብርሃም</div></div>
                <div class="person-card"><div class="person-avatar"><i class="fas fa-user-circle"></i></div><div class="person-name">ሰራተኛ</div></div>
                <div class="person-card"><div class="person-avatar"><i class="fas fa-user-circle"></i></div><div class="person-name">ተመዝጋቢ</div></div>
                <div class="person-card"><div class="person-avatar"><i class="fas fa-user-circle"></i></div><div class="person-name">ኢንቨስተር</div></div>
                <div class="person-card"><div class="person-avatar"><i class="fas fa-user-circle"></i></div><div class="person-name">አማካሪ</div></div>
            </div>
        </div>

        <!-- Panels -->
        <div id="homePanel" class="panel active-panel"></div>
        <div id="investPanel" class="panel"></div>
        <div id="companyPanel" class="panel"></div>
        <div id="teamPanel" class="panel"></div>
        <div id="userPanel" class="panel"></div>
        <div id="withdrawPanel" class="panel"></div>
        <div id="servicePanel" class="panel"></div>

        <div class="bottom-nav">
            <div class="nav-item" data-nav="home"><i class="fas fa-home"></i><span>Home</span></div>
            <div class="nav-item" data-nav="invest"><i class="fas fa-chart-line"></i><span>Invest</span></div>
            <div class="nav-item" data-nav="company"><i class="fas fa-building"></i><span>Company</span></div>
            <div class="nav-item" data-nav="team"><i class="fas fa-users"></i><span>Team</span></div>
            <div class="nav-item" data-nav="user"><i class="fas fa-user"></i><span>User</span></div>
        </div>
    </div>
</div>

<script>
    // ---------- Data layer (localStorage) ----------
    function getUsers() { return JSON.parse(localStorage.getItem("gp_users") || "{}"); }
    function saveUser(phone, pwd) { let u = getUsers(); u[phone] = pwd; localStorage.setItem("gp_users", JSON.stringify(u)); }
    function userExists(phone) { return getUsers().hasOwnProperty(phone); }
    function checkLogin(phone, pwd) { return getUsers()[phone] === pwd; }

    function getUserStats(phone) {
        let stats = localStorage.getItem("gp_stats_"+phone);
        return stats ? JSON.parse(stats) : { balance: 200, totalDeposit: 0, totalWithdraw: 0, totalIncome: 200, teamIncome: 0, todayIncome: 0 };
    }
    function saveUserStats(phone, stats) { localStorage.setItem("gp_stats_"+phone, JSON.stringify(stats)); }

    function getUserBankCard(phone) {
        let card = localStorage.getItem("gp_bankcard_"+phone);
        return card ? JSON.parse(card) : null;
    }
    function saveUserBankCard(phone, card) { localStorage.setItem("gp_bankcard_"+phone, JSON.stringify(card)); }

    let currentUser = null;

    // DOM
    const authDiv = document.getElementById('authSection');
    const dashboardDiv = document.getElementById('dashboard');
    const loginFormDiv = document.getElementById('loginForm');
    const registerFormDiv = document.getElementById('registerForm');
    const loginTab = document.getElementById('loginTab');
    const registerTab = document.getElementById('registerTab');
    const doLogin = document.getElementById('doLoginBtn');
    const doRegister = document.getElementById('doRegisterBtn');
    const logoutBtn = document.getElementById('logoutBtn');

    // Move shortcuts & people into homePanel
    const shortcutsDiv = document.querySelector('.shortcuts');
    const peopleDiv = document.querySelector('.people-section');
    const homePanel = document.getElementById('homePanel');
    if(shortcutsDiv && peopleDiv && homePanel) {
        homePanel.appendChild(shortcutsDiv);
        homePanel.appendChild(peopleDiv);
    }

    function showAuth() { authDiv.style.display = 'block'; dashboardDiv.style.display = 'none'; }
    function showDashboard() { authDiv.style.display = 'none'; dashboardDiv.style.display = 'block'; updateGreeting(); showPanel('home'); }
    function updateGreeting() { if(currentUser) document.getElementById('greetingText').innerHTML = `🌱 እንኳን ደህና መጣህ, ${currentUser.slice(-4)}!`; }

    function getCurrentBaseUrl() {
        let url = window.location.href;
        let base = url.split('?')[0];
        return base;
    }

    function showPanel(panelName) {
        document.querySelectorAll('.panel').forEach(p => p.classList.remove('active-panel'));
        const panel = document.getElementById(panelName+'Panel');
        if(panel) panel.classList.add('active-panel');
        document.querySelectorAll('.nav-item').forEach(nav => {
            nav.classList.remove('active');
            if(nav.getAttribute('data-nav') === panelName) nav.classList.add('active');
        });
        if(panelName === 'user') renderUserPanel();
        if(panelName === 'team') renderTeamPanel();
        if(panelName === 'company') renderCompanyPanel();
        if(panelName === 'invest') renderInvestPanel();
        if(panelName === 'withdraw') renderWithdrawPanel();
        if(panelName === 'service') renderServicePanel();
    }

    function renderUserPanel() {
        let stats = getUserStats(currentUser);
        const panel = document.getElementById('userPanel');
        panel.innerHTML = `
            <div style="background:#f9f9f9; border-radius:28px; padding:20px;">
                <h3><i class="fas fa-user"></i> ${currentUser}</h3>
                <div><span>💰 Account balance:</span> <strong>${stats.balance.toFixed(2)} ETB</strong></div>
                <hr><h4>Recharge</h4>
                <div><span>Income account:</span> <strong>${stats.totalIncome.toFixed(2)} ETB</strong></div>
                <div><span>Total income:</span> <strong>${stats.totalIncome.toFixed(2)} ETB</strong></div>
                <div><span>Team income:</span> <strong>${stats.teamIncome.toFixed(2)} ETB</strong></div>
                <hr><h4>Withdrawal</h4>
                <div><span>Today income:</span> <strong>${stats.todayIncome.toFixed(2)} ETB</strong></div>
                <div><span>Total deposit:</span> <strong>${stats.totalDeposit.toFixed(2)} ETB</strong></div>
                <div><span>Total withdraw:</span> <strong>${stats.totalWithdraw.toFixed(2)} ETB</strong></div>
                <hr><div style="display:flex; flex-wrap:wrap; gap:8px;">
                    <button class="user-action" data-act="myorder">📦 My Order</button>
                    <button class="user-action" data-act="deposits">💰 Deposits</button>
                    <button class="user-action" data-act="withdrawals">🏧 Withdrawals</button>
                    <button class="user-action" data-act="records">📋 Records</button>
                    <button class="user-action" data-act="faqs">❓ FAQs</button>
                    <button class="user-action" data-act="service">📞 Service</button>
                    <button class="user-action" data-act="bonus">🎁 Bonus</button>
                    <button class="user-action" data-act="app">📱 APP</button>
                    <button class="user-action" data-act="setting">⚙️ Setting</button>
                </div>
            </div>
        `;
        document.querySelectorAll('.user-action').forEach(btn => {
            btn.addEventListener('click', (e) => {
                let act = btn.getAttribute('data-act');
                if(act === 'myorder') alert("📦 ትዕዛዞች በቅርቡ");
                else if(act === 'deposits') alert("💰 የገንዘብ ገቢ ታሪክ");
                else if(act === 'withdrawals') alert("🏧 የወጪ ታሪክ");
                else if(act === 'records') alert("📋 መዝገቦች");
                else if(act === 'faqs') alert("❓ ተደጋጋሚ ጥያቄዎች");
                else if(act === 'service') alert("📞 ደንበኛ አገልግሎት: @GreenPlantHelp");
                else if(act === 'bonus') alert("🎁 ቦነስ ለንቃት አባላት");
                else if(act === 'app') alert("📱 መተግበሪያ በቅርቡ");
                else if(act === 'setting') alert("⚙️ ቅንብሮች");
            });
        });
    }

    function renderTeamPanel() {
        const inviteCode = "ABC123XY";
        const baseUrl = getCurrentBaseUrl();
        const inviteLink = `${baseUrl}?ref=${inviteCode}`;
        const panel = document.getElementById('teamPanel');
        panel.innerHTML = `
            <div style="background:#f9f9f9; border-radius:28px; padding:20px;">
                <div><strong>Invitation code</strong> ${inviteCode} <span class="copy-code copy-btn" data-code="${inviteCode}">Copy</span></div>
                <div><strong>Invitation link</strong> <span id="inviteLinkSpan">${inviteLink}</span> <span class="copy-link copy-btn" data-link="${inviteLink}">Copy</span></div>
                <hr><div>👥 Members: 0</div><div>✅ Active Members: 0</div>
                <table style="width:100%; margin:10px 0;"><tr><th>Members</th><th>Active</th></tr><tr><td>0</td><td>0</td></tr></table>
                <div><span>Deposit rebate rate: 10%</span> | <span>Invest rebate rate: 5%</span></div>
                <div>Deposit rebate: 0 ETB &nbsp; Invest rebate: 0 ETB</div>
                <button id="teamDetailBtn" style="background:#2b6e3c;">Team detail >></button>
            </div>
        `;
        document.querySelector('.copy-code')?.addEventListener('click', (e) => {
            let code = e.currentTarget.getAttribute('data-code');
            navigator.clipboard.writeText(code);
            alert("Copied: " + code);
        });
        document.querySelector('.copy-link')?.addEventListener('click', (e) => {
            let link = e.currentTarget.getAttribute('data-link');
            navigator.clipboard.writeText(link);
            alert("Copied: " + link);
        });
        document.getElementById('teamDetailBtn')?.addEventListener('click',()=>alert("የቡድን ዝርዝር በቅርቡ"));
    }

    function renderCompanyPanel() {
        const panel = document.getElementById('companyPanel');
        panel.innerHTML = `<div style="background:#f9f9f9; border-radius:28px; padding:20px;"><h3>🌿 Green Plant Investment</h3><p>We are Green Plant: passionate about sustainable agriculture, green investments, and empowering Ethiopian communities. We provide a platform for individuals to invest in high-yield plant-based projects, from aromatic herbs to fruit plantations. Our mission is to combine ecological responsibility with financial growth, offering daily returns and secure asset management.</p><p>With a dedicated team of agronomists and financial experts, we ensure your capital is used to expand organic farming, create jobs, and deliver consistent profits. Join us to grow your wealth while supporting a greener future.</p><p><strong>Our vision:</strong> To become Ethiopia’s leading green investment hub, fostering prosperity through nature.</p></div>`;
    }

    // Invest Panel with three options: TELE BIRR, CBE, BOA
    function renderInvestPanel() {
        const panel = document.getElementById('investPanel');
        panel.innerHTML = `
            <div class="section-title">💸 ገንዘብ አስገባ (Recharge)</div>
            <div class="payment-option" id="optTelebirr">📱 TELE BIRR</div>
            <div class="payment-option" id="optCBE">🏦 CBE</div>
            <div class="payment-option" id="optBOA">🏦 BOA</div>
            <div id="investBankDetail" class="hide"></div>
        `;
        document.getElementById('optTelebirr').addEventListener('click', ()=>showInvestBankForm('telebirr'));
        document.getElementById('optCBE').addEventListener('click', ()=>showInvestBankForm('cbe'));
        document.getElementById('optBOA').addEventListener('click', ()=>showInvestBankForm('boa'));
    }

    function showInvestBankForm(type) {
        const detailDiv = document.getElementById('investBankDetail');
        if(type === 'telebirr') {
            detailDiv.innerHTML = `
                <div class="bank-detail">
                    <strong>✅ ቴሌ ብር መረጃ</strong><br>
                    📞 አካውንት ቁጥር: <strong>0994242558</strong><br>
                    👤 ስም: <strong>Abrham</strong><br>
                    <small>ዝቅተኛ ገንዘብ ማስገቢያ: 1500 ETB</small>
                </div>
                <div class="deposit-form">
                    <input type="number" id="depositAmount" placeholder="የላኩት መጠን (ETB)" min="1500">
                    <input type="text" id="transactionId" placeholder="የግብይት መለያ (TID)">
                    <button id="submitDepositBtn">Submit Deposit Review</button>
                </div>
            `;
        } else if(type === 'cbe') {
            detailDiv.innerHTML = `
                <div class="bank-detail">
                    <strong>✅ ንግድ ባንክ መረጃ</strong><br>
                    🏦 አካውንት ቁጥር: <strong>1000529209928</strong><br>
                    👤 ስም: <strong>Abrham Ewunete Ejigalem</strong><br>
                    <small>ዝቅተኛ ገንዘብ ማስገቢያ: 1500 ETB</small>
                </div>
                <div class="deposit-form">
                    <input type="number" id="depositAmount" placeholder="የላኩት መጠን (ETB)" min="1500">
                    <input type="text" id="transactionId" placeholder="የግብይት መለያ (TID)">
                    <button id="submitDepositBtn">Submit Deposit Review</button>
                </div>
            `;
        } else { // BOA
            detailDiv.innerHTML = `
                <div class="bank-detail">
                    <strong>✅ BOA (Bank of Abyssinia) መረጃ</strong><br>
                    🏦 አካውንት ቁጥር: <strong>0923459124</strong><br>
                    👤 ስም: <strong>KERALEM</strong><br>
                    <small>ዝቅተኛ ገንዘብ ማስገቢያ: 1500 ETB</small>
                </div>
                <div class="deposit-form">
                    <input type="number" id="depositAmount" placeholder="የላኩት መጠን (ETB)" min="1500">
                    <input type="text" id="transactionId" placeholder="የግብይት መለያ (TID)">
                    <button id="submitDepositBtn">Submit Deposit Review</button>
                </div>
            `;
        }
        detailDiv.classList.remove('hide');
        document.getElementById('submitDepositBtn')?.addEventListener('click', () => {
            let amount = parseFloat(document.getElementById('depositAmount')?.value);
            let tid = document.getElementById('transactionId')?.value.trim();
            if(isNaN(amount) || amount < 1500) { alert("ትክክለኛ መጠን ያስገቡ (ዝቅተኛ 1500)"); return; }
            if(!tid) { alert("የግብይት መለያ ያስፈልጋል"); return; }
            alert(`ጥያቄዎ ተልኳል! መጠን: ${amount} ETB, TID: ${tid}\nከተረጋገጠ በኋላ ሂሳብዎ ይጨምራል።`);
        });
    }

    // Withdrawal Panel
    function renderWithdrawPanel() {
        let stats = getUserStats(currentUser);
        let bankCard = getUserBankCard(currentUser);
        let walletHtml = '';
        if(bankCard) {
            walletHtml = `<div class="wallet-row"><span>💳 ${bankCard.bankName}</span><span>${bankCard.accountNumber}</span></div>`;
        } else {
            walletHtml = `<div class="wallet-row" id="addWalletBtn">+ Add</div>`;
        }
        const panel = document.getElementById('withdrawPanel');
        panel.innerHTML = `
            <div class="withdraw-card">
                <h3>Withdrawal</h3>
                <div><strong>Available balance</strong> <span style="float:right;">ETB ${stats.balance.toFixed(2)}</span></div>
                <div class="amount-input"><span>Amount</span><input type="number" id="withdrawAmount" placeholder="ETB"></div>
                <div><strong>Wallet</strong></div>
                <div id="walletContainer">${walletHtml}</div>
                <button id="confirmWithdrawBtn">Confirm</button>
                <div class="withdraw-rules" style="margin-top:20px; font-size:0.8rem; background:#fff3e0; padding:12px; border-radius:28px;">
                    <strong>Withdrawal Rules</strong><br>
                    1. Minimum withdrawal amount: 200 ETB<br>
                    2. Funds will arrive within 1-48 hours.<br>
                    3. A 10% transaction fee will be charged for each withdrawal.
                </div>
            </div>
        `;
        if(!bankCard) {
            document.getElementById('addWalletBtn')?.addEventListener('click', showBankCardForm);
        }
        document.getElementById('confirmWithdrawBtn')?.addEventListener('click', () => {
            let amount = parseFloat(document.getElementById('withdrawAmount').value);
            if(isNaN(amount) || amount < 200) { alert("ዝቅተኛ መጠን 200 ETB ነው"); return; }
            if(!bankCard) { alert("እባክዎ መጀመሪያ የባንክ ካርድ ይጨምሩ"); return; }
            if(amount > stats.balance) { alert("በቂ ገንዘብ የለዎትም"); return; }
            let fee = amount * 0.1;
            let net = amount - fee;
            alert(`የማውጫ ጥያቄ ተልኳል!\nመጠን: ${amount} ETB\nኮሚሽን (10%): ${fee} ETB\nየሚደርስዎት: ${net} ETB`);
        });
    }

    function showBankCardForm() {
        const container = document.getElementById('walletContainer');
        container.innerHTML = `
            <div class="bank-card-form">
                <div class="bank-name-field">
                    <input type="text" id="bankNameInput" placeholder="Bank name" readonly>
                    <button class="dots-btn" id="bankDotsBtn">⋯</button>
                </div>
                <div id="bankListDropdown" class="bank-list hide"></div>
                <div class="form-group"><input type="text" id="accountNumber" placeholder="Account"></div>
                <div class="form-group"><input type="text" id="holderName" placeholder="Name"></div>
                <button id="confirmBankCardBtn">Confirm</button>
            </div>
        `;
        const bankList = [
            "CBE", "Telebirr", "Awash", "Abysinia", "Oromia Bank", 
            "M-Pesa", "Telecom", "Dashen", "Lion", "Zemen", 
            "Bunna", "Nib", "Hibret", "Enat", "Addis"
        ];
        const dropdown = document.getElementById('bankListDropdown');
        const dotsBtn = document.getElementById('bankDotsBtn');
        const bankNameInput = document.getElementById('bankNameInput');
        dotsBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            if(dropdown.classList.contains('hide')) {
                dropdown.innerHTML = bankList.map(b => `<div data-bank="${b}">${b}</div>`).join('');
                dropdown.classList.remove('hide');
            } else {
                dropdown.classList.add('hide');
            }
        });
        dropdown.addEventListener('click', (e) => {
            let target = e.target.closest('[data-bank]');
            if(target) {
                let bank = target.getAttribute('data-bank');
                bankNameInput.value = bank;
                dropdown.classList.add('hide');
            }
        });
        document.getElementById('confirmBankCardBtn').addEventListener('click', () => {
            let bank = bankNameInput.value.trim();
            let account = document.getElementById('accountNumber').value.trim();
            let name = document.getElementById('holderName').value.trim();
            if(!bank || !account || !name) { alert("ሁሉንም መረጃ ይሙሉ"); return; }
            saveUserBankCard(currentUser, { bankName: bank, accountNumber: account, holderName: name });
            renderWithdrawPanel();
        });
    }

    // Service Panel
    function renderServicePanel() {
        const panel = document.getElementById('servicePanel');
        panel.innerHTML = `
            <div style="background:#f9f9f9; border-radius:28px; padding:20px;">
                <h3>Customer support hours: 9:00 AM to 9:00 PM.</h3>
                <div class="service-option" id="customerServiceBtn">🌿 greenplant customer service</div>
                <div class="service-option" id="officialChannelBtn">📢 greenplant official channel</div>
            </div>
        `;
        document.getElementById('customerServiceBtn')?.addEventListener('click', () => {
            window.location.href = "https://t.me/GreenPlantSupport";
        });
        document.getElementById('officialChannelBtn')?.addEventListener('click', () => {
            window.location.href = "https://t.me/greenplantoffcial";
        });
    }

    // Shortcut clicks
    document.querySelectorAll('.shortcut-item').forEach(el => {
        el.addEventListener('click', () => {
            let action = el.getAttribute('data-action');
            if(action === 'recharge') showPanel('invest');
            else if(action === 'withdraw') showPanel('withdraw');
            else if(action === 'myorder') alert("📦 የእርስዎ ትዕዛዞች በቅርቡ ይታያሉ");
            else if(action === 'service') showPanel('service');
        });
    });

    // Authentication logic
    doLogin.addEventListener('click', () => {
        let phone = document.getElementById('loginPhone').value.trim();
        let pwd = document.getElementById('loginPassword').value;
        let err = document.getElementById('loginError');
        if(!phone || !pwd) { err.innerText = "ሁሉንም ይሙሉ"; return; }
        if(!userExists(phone)) { err.innerText = "አካውንት የለም"; return; }
        if(checkLogin(phone, pwd)) {
            currentUser = phone;
            localStorage.setItem("gp_logged", phone);
            showDashboard();
        } else { err.innerText = "የይለፍ ቃል ተሳስቷል"; }
    });

    doRegister.addEventListener('click', () => {
        let phone = document.getElementById('regPhone').value.trim();
        let pwd = document.getElementById('regPassword').value;
        let confirm = document.getElementById('regConfirm').value;
        let err = document.getElementById('regError');
        if(!phone || !pwd || !confirm) { err.innerText = "ሁሉንም ይሙሉ"; return; }
        if(pwd !== confirm) { err.innerText = "የይለፍ ቃል አይዛመድም"; return; }
        if(userExists(phone)) { err.innerText = "አካውንት አለ"; return; }
        saveUser(phone, pwd);
        saveUserStats(phone, { balance:200, totalDeposit:0, totalWithdraw:0, totalIncome:200, teamIncome:0, todayIncome:0 });
        currentUser = phone;
        localStorage.setItem("gp_logged", phone);
        showDashboard();
    });

    function logout() { localStorage.removeItem("gp_logged"); currentUser = null; showAuth(); }
    logoutBtn.addEventListener('click', logout);

    loginTab.addEventListener('click', () => {
        loginTab.classList.add('active'); registerTab.classList.remove('active');
        loginFormDiv.style.display = 'block'; registerFormDiv.style.display = 'none';
    });
    registerTab.addEventListener('click', () => {
        registerTab.classList.add('active'); loginTab.classList.remove('active');
        loginFormDiv.style.display = 'none'; registerFormDiv.style.display = 'block';
    });

    document.querySelectorAll('.nav-item').forEach(nav => {
        nav.addEventListener('click', () => showPanel(nav.getAttribute('data-nav')));
    });

    let saved = localStorage.getItem("gp_logged");
    if(saved && userExists(saved)) { currentUser = saved; showDashboard(); }
    else showAuth();
</script>
</body>
</html>
