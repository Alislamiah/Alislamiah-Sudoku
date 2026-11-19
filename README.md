<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#070d1b">

<title>Sudoku | Alislamiah AATB Games</title>
<link rel="icon" href="icon.png">

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Inter,sans-serif;
    background:#070d1b;
    color:#fff;
    min-height:100vh;
}

.splash{
    position:fixed;
    inset:0;
    z-index:1000;
    background:#070d1b;
    display:flex;
    align-items:center;
    justify-content:center;
    transition:opacity .7s ease,visibility .7s;
}

.splash img{
    width:100%;
    height:100%;
    object-fit:cover;
}

.splash.hide{
    opacity:0;
    visibility:hidden;
}

.app{
    min-height:100vh;
    background:
    radial-gradient(ellipse at 50% 0%,rgba(41,102,255,.16),transparent 48%),
    #070d1b;
    opacity:0;
    transition:opacity .7s ease;
}

.app.show{
    opacity:1;
}

header{
    padding:24px 6%;
    display:flex;
    align-items:center;
    justify-content:space-between;
    border-bottom:1px solid rgba(255,255,255,.06);
}

.brand{
    display:flex;
    align-items:center;
    gap:13px;
}

.brand img{
    width:49px;
    height:49px;
    border-radius:14px;
    object-fit:cover;
}

.brand-info h2{
    font-size:19px;
    font-weight:900;
    letter-spacing:-.5px;
}

.brand-info p{
    font-size:10px;
    color:#7587a8;
    margin-top:5px;
    letter-spacing:1.2px;
}

.header-right{
    display:flex;
    align-items:center;
    gap:12px;
}

.header-tag{
    font-size:10px;
    font-weight:800;
    color:#65a2ff;
    background:rgba(49,112,255,.12);
    padding:9px 13px;
    border-radius:30px;
    border:1px solid rgba(75,130,255,.2);
}

.user-pill{
    display:none;
    align-items:center;
    gap:10px;
    background:rgba(49,112,255,.12);
    border:1px solid rgba(75,130,255,.25);
    border-radius:30px;
    padding:6px 12px 6px 6px;
}

.user-pill.show{display:flex}

.user-avatar{
    width:32px;
    height:32px;
    border-radius:50%;
    background:#183d68;
    color:#8ec5ff;
    display:grid;
    place-items:center;
    font-weight:800;
    font-size:13px;
    overflow:hidden;
    flex-shrink:0;
}

.user-avatar img{
    width:100%;
    height:100%;
    object-fit:cover;
}

.user-name{
    font-size:12px;
    font-weight:700;
    color:#d7e6ff;
    max-width:120px;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

.login-header-btn{
    display:none;
    border:none;
    border-radius:30px;
    padding:9px 14px;
    background:linear-gradient(110deg,#3475ff,#2860dc);
    color:#fff;
    font-size:11px;
    font-weight:800;
    cursor:pointer;
}

.login-header-btn.show{display:inline-flex;align-items:center;gap:8px}

main{
    width:100%;
    max-width:950px;
    padding:65px 22px 50px;
    margin:auto;
}

/* شاشة تسجيل الدخول داخل الرئيسية */
.auth-gate{
    display:none;
    max-width:460px;
    margin:0 auto 40px;
    text-align:center;
    background:linear-gradient(145deg,rgba(24,38,68,.83),rgba(12,21,40,.94));
    border:1px solid rgba(115,153,220,.17);
    border-radius:23px;
    padding:28px 24px;
    box-shadow:0 20px 65px rgba(0,0,0,.25);
}

.auth-gate.show{display:block !important}

.auth-gate h3{
    font-size:18px;
    font-weight:900;
    margin-bottom:10px;
}

.auth-gate p{
    color:#91a5bd;
    font-size:13px;
    line-height:1.7;
    margin-bottom:20px;
}

.continue-btn{
    width:100%;
    min-height:54px;
    border:none;
    border-radius:14px;
    background:linear-gradient(110deg,#3475ff,#2860dc);
    color:white;
    font-size:14px;
    font-weight:800;
    cursor:pointer;
    display:flex;
    align-items:center;
    justify-content:center;
    gap:12px;
    box-shadow:0 8px 25px rgba(47,107,255,.25);
}

.continue-btn img{
    width:24px;
    height:24px;
    border-radius:6px;
    background:#fff;
    object-fit:cover;
}

.auth-status{
    display:none;
    margin-top:14px;
    color:#8dbaff;
    font-size:12px;
}

.auth-status.show{display:block}

.welcome{
    text-align:center;
    margin-bottom:43px;
}

.welcome .small{
    color:#5998ff;
    font-size:11px;
    font-weight:800;
    letter-spacing:3px;
    margin-bottom:15px;
}

.welcome h1{
    font-size:clamp(29px,6vw,43px);
    font-weight:900;
    letter-spacing:-1.5px;
}

.welcome h1 span{
    color:#5897ff;
}

.welcome p{
    color:#8190aa;
    font-size:13px;
    margin-top:13px;
    line-height:1.8;
}

.learn-card{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:15px;
    max-width:650px;
    margin:0 auto 48px;
    padding:21px 23px;
    background:linear-gradient(110deg,#14284b,#101b32);
    border:1px solid rgba(83,145,255,.23);
    border-radius:19px;
    text-decoration:none;
    color:white;
    transition:.25s;
}

.learn-card:hover{
    border-color:#4389ff;
    transform:translateY(-3px);
}

.learn-left{
    display:flex;
    align-items:center;
    gap:15px;
}

.learn-icon{
    width:47px;
    height:47px;
    flex-shrink:0;
    display:flex;
    align-items:center;
    justify-content:center;
    border-radius:14px;
    background:rgba(61,125,255,.17);
    font-size:23px;
}

.learn-text h3{
    font-size:14px;
    font-weight:800;
}

.learn-text p{
    font-size:11px;
    color:#8297b8;
    margin-top:6px;
}

.arrow{
    font-size:23px;
    color:#6ba4ff;
}

.section-title{
    text-align:center;
    margin-bottom:23px;
}

.section-title h2{
    font-size:22px;
    font-weight:900;
}

.section-title p{
    color:#7788a6;
    font-size:12px;
    margin-top:9px;
}

.levels{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:17px;
}

.level{
    position:relative;
    overflow:hidden;
    min-height:185px;
    padding:24px 17px;
    text-align:center;
    border:1px solid rgba(255,255,255,.09);
    border-radius:21px;
    background:linear-gradient(145deg,#14213a,#0d172b);
    cursor:pointer;
    transition:.25s;
    color:white;
    font-family:inherit;
}

.level:hover{
    transform:translateY(-6px);
    border-color:rgba(84,147,255,.65);
    box-shadow:0 15px 35px rgba(0,0,0,.25);
}

.level-icon{
    width:52px;
    height:52px;
    margin:0 auto 16px;
    border-radius:16px;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:25px;
}

.easy .level-icon{background:rgba(44,210,145,.13)}
.medium .level-icon{background:rgba(255,179,58,.13)}
.hard .level-icon{background:rgba(255,82,99,.13)}

.level h3{font-size:17px;font-weight:900}
.level p{color:#8191ac;font-size:11px;margin-top:8px}

.easy h3{color:#5cdeb0}
.medium h3{color:#ffc16b}
.hard h3{color:#ff7887}

footer{
    text-align:center;
    padding:30px 15px;
    color:#53627c;
    font-size:10px;
    line-height:2;
}

footer span{color:#8297b8}

@media(max-width:600px){
    header{padding:19px 17px}
    .brand img{width:43px;height:43px}
    .brand-info h2{font-size:16px}
    .header-tag{font-size:8px;padding:8px 9px}
    main{padding:55px 17px 35px}
    .levels{grid-template-columns:1fr;gap:13px}
    .level{
        min-height:125px;
        display:flex;
        align-items:center;
        text-align:left;
        gap:17px;
        padding:20px;
    }
    .level-icon{margin:0;flex-shrink:0}
    .level-info{flex:1}
    .level h3{font-size:17px}
    .learn-card{padding:18px}
}
</style>
</head>

<body>

<div class="splash" id="splash">
    <img src="splash.png" alt="Sudoku Welcome">
</div>

<div class="app" id="app">

<header>
    <div class="brand">
        <img src="icon.png" alt="Sudoku">
        <div class="brand-info">
            <h2>Sudoku</h2>
            <p>ALISLAMIAH AATB GAMES</p>
        </div>
    </div>

    <div class="header-right">
        <div class="header-tag">BRAIN GAMES</div>

        <!-- يظهر عند تسجيل الدخول -->
        <div class="user-pill" id="userPill">
            <div class="user-avatar" id="userAvatar">U</div>
            <span class="user-name" id="userName">User</span>
        </div>

        <!-- يظهر إذا غير مسجل -->
        <button class="login-header-btn" id="headerLoginBtn">
            <img src="https://alislamiah.github.io/Alislamiah-AI/icon.png" width="16" height="16" style="border-radius:4px;background:#fff">
            Sign in
        </button>
    </div>
</header>

<main>

    <!-- بوابة تسجيل الدخول (تظهر فقط لغير المسجلين) -->
    <div class="auth-gate" id="authGate">
        <h3>سجّل دخولك أولاً</h3>
        <p>للمتابعة، سجّل الدخول عبر حساب Alislamiah AI</p>
        <button class="continue-btn" id="mainLoginBtn">
            <img src="https://alislamiah.github.io/Alislamiah-AI/icon.png" alt="Alislamiah AI">
            <span>Continue with Alislamiah AI</span>
        </button>
        <div class="auth-status" id="authStatus">Opening Alislamiah AI...</div>
    </div>

    <section class="welcome">
        <div class="small">WELCOME TO SUDOKU</div>
        <h1>
            Challenge Your<br>
            <span>Mind.</span>
        </h1>
        <p>
            Train your brain, improve your logic<br>
            and become a Sudoku master.
        </p>
    </section>

    <a href="learn.html" class="learn-card">
        <div class="learn-left">
            <div class="learn-icon">📘</div>
            <div class="learn-text">
                <h3>You're beginner? Learn Sudoku ♂️</h3>
                <p>Learn the rules and start your journey</p>
            </div>
        </div>
        <div class="arrow">›</div>
    </a>

    <section>
        <div class="section-title">
            <h2>Play as</h2>
            <p>Choose your difficulty level</p>
        </div>

        <div class="levels">
            <button class="level easy" onclick="startGame('easy')">
                <div class="level-icon">🌱</div>
                <div class="level-info">
                    <h3>Easy</h3>
                    <p>Perfect for beginners</p>
                </div>
            </button>

            <button class="level medium" onclick="startGame('medium')">
                <div class="level-icon">⚡</div>
                <div class="level-info">
                    <h3>Medium</h3>
                    <p>Test your logic skills</p>
                </div>
            </button>

            <button class="level hard" onclick="startGame('hard')">
                <div class="level-icon">🔥</div>
                <div class="level-info">
                    <h3>Hard</h3>
                    <p>For Sudoku experts</p>
                </div>
            </button>
        </div>
    </section>

</main>

<footer>
    Powered by <span>Alislamiah AATB Games</span><br>
    © 2026 All rights reserved.
</footer>

</div>

<script>
const AI_URL = "https://alislamiah.github.io/Alislamiah-AI/continue.html";

const authGate = document.getElementById("authGate");
const userPill = document.getElementById("userPill");
const userAvatar = document.getElementById("userAvatar");
const userName = document.getElementById("userName");
const headerLoginBtn = document.getElementById("headerLoginBtn");
const mainLoginBtn = document.getElementById("mainLoginBtn");
const authStatus = document.getElementById("authStatus");

let authWindow = null;
let waitingForAuth = false;

function getSession() {
    try {
        const raw = localStorage.getItem("aatb_games_session");
        if (!raw) return null;
        const session = JSON.parse(raw);
        if (session && session.uid && session.accessToken) return session;
        return null;
    } catch (e) {
        return null;
    }
}

function setLoggedInUI(session) {
    // المستخدم مسجّل → لا تطلب منه تسجيل الدخول أبدًا
    authGate.classList.remove("show");
    authGate.style.display = "none";
    headerLoginBtn.classList.remove("show");
    headerLoginBtn.style.display = "none";
    userPill.classList.add("show");
    userPill.style.display = "flex";

    const name = session.displayName || session.email || "User";
    userName.textContent = name;

    if (session.photoURL) {
        userAvatar.innerHTML = `<img src="${session.photoURL}" alt="">`;
    } else {
        userAvatar.textContent = name.charAt(0).toUpperCase();
    }

    authStatus.classList.remove("show");
    waitingForAuth = false;
}

function setLoggedOutUI() {
    authGate.classList.add("show");
    authGate.style.display = "block";
    headerLoginBtn.classList.add("show");
    headerLoginBtn.style.display = "inline-flex";
    userPill.classList.remove("show");
    userPill.style.display = "none";
}

function updateUI() {
    const session = getSession();
    if (session) {
        setLoggedInUI(session);
    } else {
        setLoggedOutUI();
    }
}

function openLogin() {
    // إذا مسجّل مسبقًا لا تفتح تسجيل الدخول
    const session = getSession();
    if (session) {
        setLoggedInUI(session);
        return;
    }

    waitingForAuth = true;
    authStatus.textContent = "Opening Alislamiah AI account selection...";
    authStatus.classList.add("show");

    const url = AI_URL + "?provider=alislamiah&app_id=aatb-games";

    authWindow = window.open(
        url,
        "AlislamiahAuthentication",
        "width=520,height=720,left=200,top=80"
    );

    if (!authWindow) {
        waitingForAuth = false;
        authStatus.textContent = "Please allow popups to continue.";
        return;
    }

    const popupWatcher = setInterval(() => {
        if (!authWindow || authWindow.closed) {
            clearInterval(popupWatcher);
            if (waitingForAuth) {
                updateUI();
                if (getSession()) {
                    authStatus.textContent = "Signed in successfully!";
                    authStatus.classList.add("show");
                }
                waitingForAuth = false;
            }
        }
    }, 400);
}

function startGame(level) {
    const session = getSession();
    if (!session) {
        openLogin();
        return;
    }
    localStorage.setItem("sudoku_difficulty", level);
    window.location.href = "game.html";
}

headerLoginBtn.addEventListener("click", openLogin);
mainLoginBtn.addEventListener("click", openLogin);

window.addEventListener("focus", () => {
    updateUI();
    if (waitingForAuth && getSession()) {
        authStatus.textContent = "Signed in successfully!";
        authStatus.classList.add("show");
        waitingForAuth = false;
    }
});

document.addEventListener("visibilitychange", () => {
    if (document.visibilityState === "visible") {
        updateUI();
        if (waitingForAuth && getSession()) {
            authStatus.textContent = "Signed in successfully!";
            authStatus.classList.add("show");
            waitingForAuth = false;
        }
    }
});

window.addEventListener("message", (event) => {
    if (event.origin !== "https://alislamiah.github.io") return;

    const data = event.data;
    if (!data || data.status !== "SUCCESS") return;
    if (!data.accessToken || !data.user || !data.user.uid) return;

    const session = {
        uid: data.user.uid,
        email: data.user.email || "",
        displayName: data.user.displayName || "",
        photoURL: data.user.photoURL || "",
        providerUsed: data.user.providerUsed || "alislamiah",
        accessToken: data.accessToken,
        loginTime: Date.now()
    };

    localStorage.setItem("aatb_games_session", JSON.stringify(session));

    if (authWindow && !authWindow.closed) {
        try { authWindow.close(); } catch (e) {}
    }

    waitingForAuth = false;
    setLoggedInUI(session);
    authStatus.textContent = "Signed in successfully!";
    authStatus.classList.add("show");
});

const splash = document.getElementById("splash");
const app = document.getElementById("app");

setTimeout(() => {
    splash.classList.add("hide");
    app.classList.add("show");
    setTimeout(() => { splash.style.display = "none"; }, 750);
}, 5000);

// مهم: فحص فوري قبل أي عرض
updateUI();
</script>

</body>
</html>
