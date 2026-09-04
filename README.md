<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Tokyo Reign</title>

    <style>
        * {
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            margin: 0;
            font-family: Arial, Helvetica, sans-serif;
            background:
                radial-gradient(circle at top, #2b050b 0%, #100103 35%, #070707 70%);
            color: white;
            min-height: 100vh;
        }

        button,
        input {
            font-family: inherit;
        }

        header {
            height: 75px;
            padding: 0 45px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: rgba(8, 8, 8, 0.94);
            border-bottom: 1px solid #3b0b12;
            position: sticky;
            top: 0;
            z-index: 100;
            backdrop-filter: blur(12px);
        }

        .logo {
            font-size: 26px;
            font-weight: 900;
            letter-spacing: 5px;
            cursor: pointer;
        }

        .logo span {
            color: #b4162c;
        }

        nav {
            display: flex;
            gap: 28px;
        }

        nav a {
            color: #a9a9a9;
            text-decoration: none;
            font-size: 14px;
            transition: 0.2s;
        }

        nav a:hover {
            color: white;
        }

        .header-user {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .mini-avatar {
            width: 38px;
            height: 38px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #8d1525;
        }

        .auth-btn {
            border: 1px solid #781321;
            background: #151515;
            color: white;
            padding: 10px 18px;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.2s;
        }

        .auth-btn:hover {
            background: #8f1426;
        }

        main {
            width: min(1100px, calc(100% - 30px));
            margin: auto;
        }

        .hero {
            min-height: calc(100vh - 75px);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
            padding: 80px 20px;
        }

        .tag {
            color: #c62b41;
            letter-spacing: 5px;
            font-size: 13px;
            font-weight: bold;
        }

        h1 {
            font-size: clamp(55px, 10vw, 120px);
            line-height: 0.9;
            margin: 20px 0;
            letter-spacing: -5px;
        }

        h1 span {
            color: #a51026;
        }

        .hero p {
            max-width: 650px;
            color: #999;
            line-height: 1.8;
            font-size: 17px;
        }

        .hero-buttons {
            display: flex;
            gap: 15px;
            margin-top: 25px;
            flex-wrap: wrap;
        }

        .primary {
            border: none;
            background: #a51026;
            color: white;
            padding: 14px 25px;
            border-radius: 9px;
            cursor: pointer;
            font-size: 15px;
            transition: 0.2s;
        }

        .primary:hover {
            background: #c21935;
            transform: translateY(-2px);
        }

        .secondary {
            border: 1px solid #333;
            background: #111;
            color: white;
            padding: 14px 25px;
            border-radius: 9px;
            cursor: pointer;
            transition: 0.2s;
        }

        .secondary:hover {
            border-color: #8a1626;
            background: #171717;
        }

        .section {
            padding: 90px 0;
            scroll-margin-top: 95px;
        }

        .section-title {
            margin-bottom: 30px;
        }

        .section-title h2 {
            font-size: 38px;
            margin: 10px 0;
        }

        .section-title p {
            color: #777;
        }

        .about-text {
            max-width: 900px;
            background: linear-gradient(145deg, #111111, #090909);
            border: 1px solid #2b2022;
            border-left: 3px solid #a51026;
            border-radius: 16px;
            padding: 35px 40px;
        }

        .about-text p {
            color: #aaa;
            font-size: 16px;
            line-height: 1.9;
            margin-bottom: 25px;
        }

        .about-text strong {
            color: white;
        }

        .about-text h3 {
            font-size: 22px;
            margin-top: 35px;
            margin-bottom: 12px;
            color: white;
        }

        .about-text h3::before {
            content: "— ";
            color: #b4162c;
        }

        .about-final {
            margin-top: 40px;
            padding: 25px;
            background: #160307;
            border: 1px solid #49101a;
            border-radius: 12px;
            font-size: 18px;
            line-height: 1.7;
            color: #aaa;
        }

        .about-final span {
            color: #d51e39;
            font-size: 21px;
            font-weight: bold;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .card {
            background: linear-gradient(145deg, #121212, #0b0b0b);
            border: 1px solid #262626;
            border-radius: 16px;
            padding: 25px;
            min-height: 170px;
            transition: 0.2s;
        }

        .card:hover {
            transform: translateY(-4px);
            border-color: #53101a;
        }

        .card h3 {
            margin-top: 0;
        }

        .card p {
            color: #888;
            line-height: 1.6;
        }

        .profile-page {
            display: none;
            padding: 65px 0;
        }

        .profile-card {
            max-width: 700px;
            margin: auto;
            background: #0e0e0e;
            border: 1px solid #292929;
            border-radius: 22px;
            overflow: hidden;
        }

        .profile-banner {
            height: 170px;
            background:
                linear-gradient(120deg, rgba(160, 10, 35, .8), rgba(25, 0, 5, .9)),
                repeating-linear-gradient(
                    45deg,
                    transparent,
                    transparent 15px,
                    rgba(255,255,255,.02) 15px,
                    rgba(255,255,255,.02) 30px
                );
        }

        .profile-content {
            padding: 0 35px 35px;
        }

        .profile-avatar {
            width: 130px;
            height: 130px;
            border-radius: 50%;
            object-fit: cover;
            border: 6px solid #0e0e0e;
            margin-top: -65px;
            background: #222;
        }

        .profile-name {
            font-size: 30px;
            margin: 15px 0 5px;
        }

        .profile-id {
            color: #686868;
            font-size: 14px;
        }

        .profile-settings {
            margin-top: 30px;
            padding-top: 25px;
            border-top: 1px solid #252525;
        }

        .form-group {
            margin-bottom: 18px;
        }

        label {
            display: block;
            font-size: 13px;
            color: #a5a5a5;
            margin-bottom: 8px;
        }

        input {
            width: 100%;
            background: #181818;
            border: 1px solid #303030;
            color: white;
            padding: 13px 14px;
            border-radius: 8px;
            outline: none;
        }

        input:focus {
            border-color: #8e1627;
        }

        .logout {
            margin-top: 20px;
            background: transparent;
            border: 1px solid #5a1822;
            color: #d35a6c;
            padding: 12px 18px;
            border-radius: 8px;
            cursor: pointer;
        }

        .modal-bg {
            display: none;
            position: fixed;
            inset: 0;
            z-index: 1000;
            background: rgba(0, 0, 0, 0.78);
            backdrop-filter: blur(8px);
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .modal {
            width: 100%;
            max-width: 430px;
            background: #101010;
            border: 1px solid #292929;
            border-radius: 18px;
            padding: 30px;
            box-shadow: 0 25px 80px rgba(0,0,0,.7);
        }

        .modal h2 {
            margin-top: 0;
        }

        .modal p {
            color: #777;
            font-size: 14px;
        }

        .switch {
            color: #c32b40;
            cursor: pointer;
        }

        .error {
            color: #ff5b6f;
            font-size: 13px;
            min-height: 18px;
        }

        .close {
            float: right;
            font-size: 25px;
            color: #777;
            cursor: pointer;
        }

        .avatar-upload {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .avatar-preview {
            width: 85px;
            height: 85px;
            border-radius: 50%;
            object-fit: cover;
            background: #222;
        }

        footer {
            border-top: 1px solid #1f1f1f;
            color: #555;
            padding: 30px 0;
            margin-top: 80px;
        }

        @media (max-width: 800px) {
            header {
                padding: 0 18px;
            }

            nav {
                display: none;
            }

            .cards {
                grid-template-columns: 1fr;
            }

            h1 {
                letter-spacing: -2px;
            }

            .profile-content {
                padding-left: 20px;
                padding-right: 20px;
            }

            .about-text {
                padding: 25px 22px;
            }
        }
    </style>
</head>

<body>

<header>

    <div class="logo" onclick="openHome()">
        TOKYO <span>REIGN</span>
    </div>

    <nav>
        <a href="#" onclick="goToSection('top')">Главная</a>
        <a href="#about" onclick="goToSection('about')">О проекте</a>
        <a href="#gangs" onclick="goToSection('gangs')">Группировки</a>
        <a href="#news" onclick="goToSection('news')">Новости</a>
    </nav>

    <div id="headerAuth"></div>

</header>


<main id="top">

    <div id="homePage">

        <section class="hero">

            <div class="tag">
                TOKYO • 2000s • ROLEPLAY
            </div>

            <h1>
                TOKYO<br>
                <span>REIGN</span>
            </h1>

            <p>
                Город, где имя может значить больше закона.
                Создавай персонажа, вступай в группировки,
                участвуй в конфликтах и формируй собственную историю.
            </p>

            <div class="hero-buttons">

                <button class="primary" onclick="profileAction()">
                    Начать игру
                </button>

                <button class="secondary" onclick="goToSection('about')">
                    Узнать больше
                </button>

            </div>

        </section>


        <section class="section" id="about">

            <div class="section-title">

                <div class="tag">ABOUT • TOKYO REIGN</div>

                <h2>О проекте</h2>

                <p>
                    Мир, где история создаётся самими игроками.
                </p>

            </div>

            <div class="about-text">

                <p>
                    <strong>Tokyo Reign</strong> — RolePlay-проект, вдохновлённый атмосферой
                    Японии 2000-х, уличными группировками и миром Tokyo Revengers.
                </p>

                <p>
                    Здесь история строится не вокруг заранее написанного сюжета,
                    а вокруг самих игроков. Ты создаёшь собственного персонажа,
                    выбираешь его характер, цели и окружение, а дальнейшая судьба
                    зависит от твоих решений и событий внутри проекта.
                </p>

                <h3>Живой город</h3>

                <p>
                    Tokyo Reign — это не только школа. Улицы, переулки, районы и
                    другие места города становятся частью RP. Здесь проходят встречи,
                    конфликты, тренировки, мероприятия и обычная жизнь персонажей.
                </p>

                <h3>Группировки и территории</h3>

                <p>
                    Игроки могут вступать в существующие группировки или развивать
                    собственные. У каждой могут быть своя история, символика,
                    иерархия, союзники и противники.
                </p>

                <p>
                    Группировки способны бороться за территории и влияние на город.
                    Победы и поражения меняют положение сил внутри проекта.
                </p>

                <h3>Твой персонаж — твоя история</h3>

                <p>
                    В Tokyo Reign необязательно становиться частью банды.
                    Можно быть обычным учеником, спортсменом, участником клуба
                    или просто человеком, который оказался втянут в происходящее.
                </p>

                <p>
                    Знакомства могут перерасти в дружбу или соперничество,
                    небольшая ссора — в серьёзный конфликт, а действия одного
                    персонажа способны повлиять на истории других игроков.
                </p>

                <h3>Мир, который меняют игроки</h3>

                <p>
                    События проекта становятся частью общей истории Tokyo Reign.
                    Появляются новые лидеры и группировки, заключаются союзы,
                    меняются территории и отношения между персонажами.
                </p>

                <div class="about-final">
                    Здесь нет одной главной истории.<br>
                    <span>Историю Tokyo Reign создают сами игроки.</span>
                </div>

            </div>

        </section>


        <section class="section" id="gangs">

            <div class="section-title">

                <div class="tag">FACTIONS • TOKYO</div>

                <h2>Группировки</h2>

                <p>
                    Основные направления жизни внутри проекта.
                </p>

            </div>

            <div class="cards">

                <div class="card">
                    <h3>Уличные группировки</h3>
                    <p>
                        Создавай собственную команду или присоединяйся к уже существующей.
                        У каждой группировки может быть своя территория, стиль и история.
                    </p>
                </div>

                <div class="card">
                    <h3>Клубы</h3>
                    <p>
                        Не все объединения существуют ради конфликтов.
                        Создавай спортивные, творческие и школьные клубы.
                    </p>
                </div>

                <div class="card">
                    <h3>Одиночки</h3>
                    <p>
                        Не хочешь вступать никуда? Создавай самостоятельного персонажа
                        и развивай собственные связи внутри города.
                    </p>
                </div>

            </div>

        </section>


        <section class="section" id="news">

            <div class="section-title">

                <div class="tag">NEWS • CITY FEED</div>

                <h2>Новости</h2>

                <p>
                    Позже здесь можно будет публиковать события проекта.
                </p>

            </div>

            <div class="cards">

                <div class="card">
                    <h3>Tokyo Reign открыт</h3>
                    <p>
                        Здесь будут появляться важные события, изменения территорий,
                        результаты конфликтов и объявления администрации.
                    </p>
                </div>

                <div class="card">
                    <h3>Новые группировки</h3>
                    <p>
                        В будущем здесь можно вывести список новых банд
                        и важных изменений в их составе.
                    </p>
                </div>

                <div class="card">
                    <h3>Городская хроника</h3>
                    <p>
                        RP-события игроков могут становиться частью официальной
                        истории Tokyo Reign.
                    </p>
                </div>

            </div>

        </section>

    </div>


    <section class="profile-page" id="profilePage">

        <div class="profile-card">

            <div class="profile-banner"></div>

            <div class="profile-content">

                <img
                    id="profileAvatar"
                    class="profile-avatar"
                    src=""
                    alt="Аватар"
                >

                <div
                    class="profile-name"
                    id="profileName">
                </div>

                <div
                    class="profile-id"
                    id="profileEmail">
                </div>


                <div class="profile-settings">

                    <h3>Настройка профиля</h3>


                    <div class="form-group">

                        <label>Ник</label>

                        <input
                            id="nicknameInput"
                            maxlength="25"
                            placeholder="Введите ник"
                        >

                    </div>


                    <div class="form-group">

                        <label>Аватарка</label>

                        <div class="avatar-upload">

                            <img
                                id="avatarPreview"
                                class="avatar-preview"
                                src=""
                                alt="Предпросмотр аватара"
                            >

                            <input
                                type="file"
                                id="avatarInput"
                                accept="image/*"
                            >

                        </div>

                    </div>


                    <button
                        class="primary"
                        onclick="saveProfile()">

                        Сохранить профиль

                    </button>

                    <br>

                    <button
                        class="logout"
                        onclick="logout()">

                        Выйти из аккаунта

                    </button>

                </div>

            </div>

        </div>

    </section>


    <footer>
        TOKYO REIGN © 2026
    </footer>

</main>


<div class="modal-bg" id="authModal">

    <div class="modal">

        <span class="close" onclick="closeModal()">×</span>

        <div id="loginForm">

            <h2>Вход</h2>

            <p>
                Войди в аккаунт Tokyo Reign.
            </p>

            <div class="form-group">

                <label>Email</label>

                <input
                    type="email"
                    id="loginEmail"
                    placeholder="example@email.com"
                >

            </div>

            <div class="form-group">

                <label>Пароль</label>

                <input
                    type="password"
                    id="loginPassword"
                    placeholder="Пароль"
                >

            </div>

            <div class="error" id="loginError"></div>

            <button
                class="primary"
                onclick="login()">

                Войти

            </button>

            <p>
                Нет аккаунта?
                <span
                    class="switch"
                    onclick="showRegister()">
                    Создать аккаунт
                </span>
            </p>

        </div>


        <div id="registerForm" style="display:none;">

            <h2>Регистрация</h2>

            <p>
                Создай аккаунт Tokyo Reign.
            </p>


            <div class="form-group">

                <label>Email</label>

                <input
                    type="email"
                    id="registerEmail"
                    placeholder="example@email.com"
                >

            </div>


            <div class="form-group">

                <label>Пароль</label>

                <input
                    type="password"
                    id="registerPassword"
                    placeholder="Минимум 4 символа"
                >

            </div>


            <div class="form-group">

                <label>Ник</label>

                <input
                    id="registerNickname"
                    maxlength="25"
                    placeholder="Например: Senju Ferrari"
                >

            </div>

            <div class="error" id="registerError"></div>


            <button
                class="primary"
                onclick="register()">

                Создать аккаунт

            </button>

            <p>
                Уже есть аккаунт?
                <span
                    class="switch"
                    onclick="showLogin()">
                    Войти
                </span>
            </p>

        </div>

    </div>

</div>


<script>

const DEFAULT_AVATAR =
    "data:image/svg+xml;charset=UTF-8," +
    encodeURIComponent(`
        <svg xmlns="http://www.w3.org/2000/svg" width="300" height="300">
            <rect width="100%" height="100%" fill="#1b1b1b"/>
            <circle cx="150" cy="115" r="55" fill="#555"/>
            <circle cx="150" cy="290" r="100" fill="#555"/>
        </svg>
    `);


function getUsers() {
    return JSON.parse(
        localStorage.getItem("tokyoReignUsers") || "{}"
    );
}


function saveUsers(users) {
    localStorage.setItem(
        "tokyoReignUsers",
        JSON.stringify(users)
    );
}


function getCurrentEmail() {
    return localStorage.getItem(
        "tokyoReignCurrentUser"
    );
}


function getCurrentUser() {
    const email = getCurrentEmail();

    if (!email) return null;

    const users = getUsers();

    return users[email] || null;
}


function register() {

    const email =
        document
        .getElementById("registerEmail")
        .value
        .trim()
        .toLowerCase();

    const password =
        document
        .getElementById("registerPassword")
        .value;

    const nickname =
        document
        .getElementById("registerNickname")
        .value
        .trim();

    const error =
        document
        .getElementById("registerError");


    error.innerText = "";


    if (!email.includes("@")) {
        error.innerText = "Введите нормальный email.";
        return;
    }


    if (password.length < 4) {
        error.innerText =
            "Пароль должен содержать минимум 4 символа.";
        return;
    }


    if (nickname.length < 2) {
        error.innerText = "Введите ник.";
        return;
    }


    const users = getUsers();


    if (users[email]) {
        error.innerText =
            "Аккаунт с таким email уже существует.";
        return;
    }


    users[email] = {
        email: email,
        password: password,
        nickname: nickname,
        avatar: DEFAULT_AVATAR
    };


    saveUsers(users);


    localStorage.setItem(
        "tokyoReignCurrentUser",
        email
    );


    closeModal();
    updateHeader();
    openProfile();
}


function login() {

    const email =
        document
        .getElementById("loginEmail")
        .value
        .trim()
        .toLowerCase();

    const password =
        document
        .getElementById("loginPassword")
        .value;

    const users = getUsers();

    const error =
        document
        .getElementById("loginError");


    error.innerText = "";


    if (!users[email]) {
        error.innerText =
            "Такого аккаунта нет.";
        return;
    }


    if (users[email].password !== password) {
        error.innerText =
            "Неверный пароль.";
        return;
    }


    localStorage.setItem(
        "tokyoReignCurrentUser",
        email
    );


    closeModal();
    updateHeader();
    openProfile();
}


function logout() {

    localStorage.removeItem(
        "tokyoReignCurrentUser"
    );

    updateHeader();
    openHome();
}


function openModal() {

    document
        .getElementById("authModal")
        .style.display = "flex";
}


function closeModal() {

    document
        .getElementById("authModal")
        .style.display = "none";
}


function showRegister() {

    document
        .getElementById("loginForm")
        .style.display = "none";

    document
        .getElementById("registerForm")
        .style.display = "block";
}


function showLogin() {

    document
        .getElementById("registerForm")
        .style.display = "none";

    document
        .getElementById("loginForm")
        .style.display = "block";
}


function updateHeader() {

    const container =
        document
        .getElementById("headerAuth");

    const user = getCurrentUser();


    if (!user) {

        container.innerHTML = `
            <button
                class="auth-btn"
                onclick="openModal()">
                Войти
            </button>
        `;

        return;
    }


    container.innerHTML = `
        <div
            class="header-user"
            onclick="openProfile()"
            style="cursor:pointer"
        >
            <img
                class="mini-avatar"
                src="${user.avatar || DEFAULT_AVATAR}"
            >

            <span>
                ${escapeHTML(user.nickname)}
            </span>
        </div>
    `;
}


function profileAction() {

    if (getCurrentUser()) {
        openProfile();
    } else {
        openModal();
    }
}


function openHome() {

    document
        .getElementById("homePage")
        .style.display = "block";

    document
        .getElementById("profilePage")
        .style.display = "none";

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


function goToSection(sectionId) {

    document
        .getElementById("homePage")
        .style.display = "block";

    document
        .getElementById("profilePage")
        .style.display = "none";


    setTimeout(() => {

        const section =
            document.getElementById(sectionId);

        if (section) {
            section.scrollIntoView({
                behavior: "smooth",
                block: "start"
            });
        }

    }, 50);
}


function openProfile() {

    const user = getCurrentUser();

    if (!user) {
        openModal();
        return;
    }


    document
        .getElementById("homePage")
        .style.display = "none";

    document
        .getElementById("profilePage")
        .style.display = "block";


    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });


    document
        .getElementById("profileName")
        .innerText = user.nickname;


    document
        .getElementById("profileEmail")
        .innerText = user.email;


    document
        .getElementById("nicknameInput")
        .value = user.nickname;


    document
        .getElementById("profileAvatar")
        .src = user.avatar || DEFAULT_AVATAR;


    document
        .getElementById("avatarPreview")
        .src = user.avatar || DEFAULT_AVATAR;
}


let pendingAvatar = null;


document
    .getElementById("avatarInput")
    .addEventListener(
        "change",
        function(event) {

            const file =
                event.target.files[0];

            if (!file) return;


            const reader =
                new FileReader();


            reader.onload =
                function(e) {

                    pendingAvatar =
                        e.target.result;

                    document
                        .getElementById("avatarPreview")
                        .src = pendingAvatar;

                };


            reader.readAsDataURL(file);

        }
    );


function saveProfile() {

    const email =
        getCurrentEmail();

    if (!email) return;


    const users =
        getUsers();


    const nickname =
        document
        .getElementById("nicknameInput")
        .value
        .trim();


    if (nickname.length < 2) {

        alert("Ник слишком короткий.");

        return;
    }


    users[email].nickname =
        nickname;


    if (pendingAvatar) {

        users[email].avatar =
            pendingAvatar;

    }


    saveUsers(users);


    pendingAvatar = null;


    updateHeader();
    openProfile();


    alert("Профиль сохранён.");
}


function escapeHTML(text) {

    return text
        .replaceAll("&", "&amp;")
        .replaceAll("<", "&lt;")
        .replaceAll(">", "&gt;")
        .replaceAll('"', "&quot;")
        .replaceAll("'", "&#039;");
}


window.onclick =
    function(event) {

        const modal =
            document
            .getElementById("authModal");

        if (event.target === modal) {
            closeModal();
        }

    };


updateHeader();

</script>

</body>
</html>
