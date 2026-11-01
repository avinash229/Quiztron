<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#090b18">
  <meta name="description" content="Qiztron is the ultimate IT quiz event. Think fast, test your tech knowledge, and take the top spot.">
  <title>Qiztron — The IT Quiz Event</title>
  <style>
    :root {
      color-scheme: dark;
      --bg: #090b18;
      --panel: #111426;
      --panel-light: #171a30;
      --text: #f5f6ff;
      --muted: #9da2bd;
      --purple: #a78bfa;
      --cyan: #66e4db;
      --line: rgba(191, 194, 235, .13);
      --font: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    * { box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      min-width: 320px;
      background:
        radial-gradient(ellipse at 82% 27%, rgba(108, 72, 196, .16), transparent 35rem),
        radial-gradient(ellipse at 8% 68%, rgba(46, 159, 159, .09), transparent 30rem),
        var(--bg);
      color: var(--text);
      font-family: var(--font);
      -webkit-font-smoothing: antialiased;
    }

    button { font: inherit; }
    a { color: inherit; text-decoration: none; }

    .shell { width: min(1120px, calc(100% - 48px)); margin-inline: auto; }

    .topbar {
      height: 82px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid var(--line);
    }

    .brand { display: inline-flex; align-items: center; gap: 11px; }
    .brand-mark { width: 40px; height: 40px; flex: none; }
    .brand-name { font-size: 19px; font-weight: 850; letter-spacing: .14em; }
    .brand-name span { color: var(--cyan); }

    .nav { display: flex; align-items: center; gap: 32px; color: var(--muted); font-size: 13px; }
    .nav a:hover, .nav a:focus-visible { color: var(--text); }
    .nav-cta { color: var(--text) !important; border: 1px solid var(--line); padding: 10px 15px; border-radius: 9px; }

    .hero {
      min-height: 570px;
      display: grid;
      grid-template-columns: 1.08fr .92fr;
      align-items: center;
      gap: 40px;
      padding-block: 74px 64px;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      color: var(--cyan);
      font-size: 11px;
      font-weight: 750;
      letter-spacing: .16em;
      text-transform: uppercase;
    }

    .live-dot {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: var(--cyan);
      box-shadow: 0 0 12px rgba(102, 228, 219, .8);
    }

    h1 {
      max-width: 620px;
      margin: 21px 0 18px;
      font-size: clamp(48px, 6.5vw, 78px);
      line-height: .99;
      letter-spacing: -.065em;
    }

    h1 .gradient {
      background: linear-gradient(100deg, #c2aaff 6%, #8f7af0 47%, #6ee2dc 100%);
      background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .hero-copy { max-width: 500px; color: var(--muted); font-size: 16px; line-height: 1.75; }
    .hero-actions { display: flex; align-items: center; gap: 23px; margin-top: 30px; }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      min-height: 49px;
      padding: 0 20px;
      border: 0;
      border-radius: 10px;
      background: linear-gradient(110deg, #a58af8, #8168e7);
      color: #0c0d1a;
      font-size: 13px;
      font-weight: 800;
      cursor: pointer;
      box-shadow: 0 8px 26px rgba(127, 99, 230, .23);
      transition: transform .18s ease, box-shadow .18s ease;
    }

    .button:hover { transform: translateY(-2px); box-shadow: 0 11px 30px rgba(127, 99, 230, .35); }
    .button:focus-visible, .answer:focus-visible, .nav a:focus-visible { outline: 2px solid var(--cyan); outline-offset: 4px; }
    .text-link { color: #d3d5e8; font-size: 13px; }
    .text-link span { color: var(--cyan); margin-left: 5px; }

    .visual { position: relative; display: grid; place-items: center; min-height: 390px; }
    .orbit {
      position: absolute;
      width: min(390px, 90%);
      aspect-ratio: 1;
      border: 1px solid rgba(173, 151, 255, .18);
      border-radius: 50%;
      box-shadow: 0 0 70px rgba(118, 91, 214, .09), inset 0 0 70px rgba(118, 91, 214, .05);
    }
    .orbit::before, .orbit::after {
      content: "";
      position: absolute;
      border: 1px solid rgba(102, 228, 219, .14);
      border-radius: 50%;
      inset: 30px;
    }
    .orbit::after { inset: 67px; border-color: rgba(173, 151, 255, .17); }
    .orbit-dot {
      position: absolute;
      top: 17%;
      right: 20%;
      width: 9px;
      height: 9px;
      border-radius: 50%;
      background: var(--cyan);
      box-shadow: 0 0 18px var(--cyan);
    }
    .hero-emblem { width: 185px; height: 185px; position: relative; filter: drop-shadow(0 0 32px rgba(155, 125, 255, .26)); }
    .float-card {
      position: absolute;
      display: flex;
      align-items: center;
      gap: 11px;
      padding: 13px 15px;
      border: 1px solid rgba(193, 195, 234, .15);
      border-radius: 12px;
      background: rgba(20, 23, 43, .88);
      box-shadow: 0 14px 35px rgba(0, 0, 0, .23);
      backdrop-filter: blur(12px);
    }
    .float-card.one { top: 63px; left: 3px; }
    .float-card.two { right: 0; bottom: 56px; }
    .card-icon { width: 35px; height: 35px; display: grid; place-items: center; border-radius: 9px; background: rgba(167, 139, 250, .13); color: var(--purple); font-size: 17px; }
    .float-card.two .card-icon { background: rgba(102, 228, 219, .12); color: var(--cyan); }
    .card-label { color: var(--muted); font-size: 10px; }
    .card-value { margin-top: 3px; font-size: 12px; font-weight: 750; }

    .event-strip {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      padding: 20px 0;
      border-block: 1px solid var(--line);
    }
    .event-stat { display: flex; align-items: center; justify-content: center; gap: 13px; border-right: 1px solid var(--line); }
    .event-stat:last-child { border: 0; }
    .stat-icon { color: var(--cyan); font-size: 17px; }
    .stat-label { color: var(--muted); font-size: 10px; letter-spacing: .1em; text-transform: uppercase; }
    .stat-value { margin-top: 4px; font-size: 13px; font-weight: 700; }

    .section { padding-block: 83px 76px; }
    .section-heading { display: flex; justify-content: space-between; align-items: end; gap: 24px; margin-bottom: 28px; }
    .section-kicker { color: var(--purple); font-size: 10px; font-weight: 800; letter-spacing: .15em; text-transform: uppercase; }
    h2 { margin: 9px 0 0; font-size: clamp(26px, 3vw, 34px); letter-spacing: -.04em; }
    .section-note { max-width: 330px; margin: 0; color: var(--muted); font-size: 12px; line-height: 1.7; }

    .topics { display: grid; grid-template-columns: repeat(4, 1fr); gap: 13px; }
    .topic {
      min-height: 148px;
      padding: 21px;
      border: 1px solid var(--line);
      border-radius: 13px;
      background: linear-gradient(145deg, rgba(24, 27, 49, .85), rgba(15, 17, 33, .85));
    }
    .topic-symbol { display: inline-grid; place-items: center; width: 36px; height: 36px; margin-bottom: 20px; border-radius: 10px; background: rgba(167, 139, 250, .12); color: #c0aaff; font-size: 16px; }
    .topic:nth-child(2) .topic-symbol { background: rgba(102, 228, 219, .1); color: var(--cyan); }
    .topic:nth-child(3) .topic-symbol { background: rgba(246, 190, 110, .1); color: #f6be6e; }
    .topic:nth-child(4) .topic-symbol { background: rgba(244, 129, 173, .1); color: #f481ad; }
    .topic h3 { margin: 0 0 6px; font-size: 13px; }
    .topic p { margin: 0; color: var(--muted); font-size: 11px; line-height: 1.5; }

    .bottom-cta {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
      margin-bottom: 75px;
      padding: 28px 32px;
      border: 1px solid rgba(167, 139, 250, .2);
      border-radius: 16px;
      background: linear-gradient(110deg, rgba(100, 76, 171, .18), rgba(26, 105, 109, .1));
    }
    .bottom-cta h2 { font-size: 21px; }
    .bottom-cta p { margin: 7px 0 0; color: var(--muted); font-size: 12px; }
    footer { display: flex; justify-content: space-between; align-items: center; gap: 18px; padding: 20px 0 25px; border-top: 1px solid var(--line); color: var(--muted); font-size: 10px; }
    footer .brand-name { color: var(--text); font-size: 14px; }
    footer .brand-mark { width: 30px; height: 30px; }

    .quiz-overlay {
      position: fixed;
      z-index: 5;
      inset: 0;
      display: none;
      place-items: center;
      padding: 20px;
      background: rgba(5, 6, 14, .82);
      backdrop-filter: blur(10px);
    }
    .quiz-overlay.open { display: grid; }
    .quiz-dialog {
      width: min(540px, 100%);
      padding: 29px;
      border: 1px solid rgba(194, 170, 255, .22);
      border-radius: 18px;
      background: #111426;
      box-shadow: 0 25px 90px rgba(0, 0, 0, .5);
    }
    .quiz-top { display: flex; justify-content: space-between; align-items: center; gap: 12px; }
    .quiz-brand { color: var(--cyan); font-size: 10px; font-weight: 800; letter-spacing: .15em; }
    .close-quiz { border: 0; padding: 6px 9px; background: transparent; color: var(--muted); font-size: 21px; cursor: pointer; }
    .progress-track { height: 4px; margin: 21px 0 26px; border-radius: 9px; background: #292b40; overflow: hidden; }
    .progress-bar { width: 20%; height: 100%; border-radius: inherit; background: linear-gradient(90deg, var(--purple), var(--cyan)); transition: width .25s ease; }
    .question-count { color: var(--muted); font-size: 11px; }
    .quiz-dialog h2 { margin: 12px 0 22px; font-size: 22px; line-height: 1.35; letter-spacing: -.025em; }
    .answers { display: grid; gap: 9px; }
    .answer {
      width: 100%;
      padding: 13px 14px;
      border: 1px solid var(--line);
      border-radius: 9px;
      background: #171a2c;
      color: var(--text);
      text-align: left;
      font-size: 12px;
      cursor: pointer;
      transition: border-color .15s, background .15s;
    }
    .answer:hover:not(:disabled) { border-color: rgba(167, 139, 250, .7); background: #1d2037; }
    .answer:disabled { cursor: default; }
    .answer.correct { border-color: #4fc4a7; background: rgba(54, 158, 132, .13); }
    .answer.incorrect { border-color: #e87979; background: rgba(196, 74, 74, .13); }
    .quiz-feedback { min-height: 22px; margin: 14px 0 4px; color: var(--muted); font-size: 11px; }
    .quiz-next { width: 100%; margin-top: 8px; }
    .quiz-result { padding-block: 24px 12px; text-align: center; }
    .result-icon { font-size: 40px; }
    .quiz-result h2 { margin-bottom: 10px; }
    .quiz-result p { margin: 0 0 22px; color: var(--muted); font-size: 13px; line-height: 1.7; }

    @media (max-width: 760px) {
      .shell { width: min(100% - 36px, 560px); }
      .topbar { height: 70px; }
      .nav { gap: 17px; }
      .nav a:not(.nav-cta) { display: none; }
      .hero { min-height: 0; grid-template-columns: 1fr; gap: 4px; padding-block: 60px 40px; }
      .visual { min-height: 330px; }
      .orbit { width: 310px; }
      .hero-emblem { width: 150px; height: 150px; }
      .float-card.one { left: 4%; top: 38px; }
      .float-card.two { right: 2%; bottom: 30px; }
      .topics { grid-template-columns: repeat(2, 1fr); }
      .section { padding-block: 60px 54px; }
      .bottom-cta { margin-bottom: 55px; }
    }

    @media (max-width: 480px) {
      .shell { width: calc(100% - 32px); }
      .brand-name { font-size: 16px; }
      .brand-mark { width: 35px; height: 35px; }
      .nav-cta { padding: 9px 11px; font-size: 11px; }
      .hero { padding-top: 49px; }
      h1 { font-size: 51px; }
      .hero-copy { font-size: 14px; }
      .hero-actions { gap: 16px; }
      .button { padding-inline: 15px; font-size: 12px; }
      .text-link { font-size: 11px; }
      .visual { min-height: 290px; }
      .orbit { width: 265px; }
      .hero-emblem { width: 122px; height: 122px; }
      .float-card { padding: 10px 11px; }
      .float-card.one { left: 0; }
      .float-card.two { right: 0; }
      .event-strip { grid-template-columns: 1fr; gap: 15px; padding: 19px 0; }
      .event-stat { justify-content: flex-start; padding-left: 18%; border: 0; }
      .section-heading { align-items: flex-start; flex-direction: column; gap: 12px; }
      .topics { gap: 9px; }
      .topic { min-height: 140px; padding: 15px; }
      .topic-symbol { margin-bottom: 14px; }
      .bottom-cta { align-items: flex-start; flex-direction: column; padding: 22px; }
      footer { align-items: flex-start; flex-direction: column; }
      .quiz-dialog { padding: 22px 18px; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { scroll-behavior: auto !important; transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <header class="shell topbar">
    <a class="brand" href="#" aria-label="Qiztron home">
      <svg class="brand-mark" viewBox="0 0 48 48" role="img" aria-label="Qiztron logo">
        <defs>
          <linearGradient id="logo-gradient" x1="0" y1="0" x2="1" y2="1">
            <stop offset="0" stop-color="#b99cff"/>
            <stop offset="1" stop-color="#62e2d9"/>
          </linearGradient>
        </defs>
        <path d="M24 3.5 42 13.8v20.4L24 44.5 6 34.2V13.8L24 3.5Z" fill="none" stroke="url(#logo-gradient)" stroke-width="2.4"/>
        <path d="M30.6 19.2a8.6 8.6 0 1 0-2.1 11.6l5.2 4.1" fill="none" stroke="url(#logo-gradient)" stroke-linecap="round" stroke-width="4"/>
        <path d="m23.1 21.3 2.7 2.7-2.7 2.7" fill="none" stroke="#f5f6ff" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.7"/>
      </svg>
      <span class="brand-name">QIZ<span>TRON</span></span>
    </a>
    <nav class="nav" aria-label="Main navigation">
      <a href="#about">The event</a>
      <a href="#topics">Topics</a>
      <a class="nav-cta" href="#challenge" data-start-quiz>Join the quiz <span aria-hidden="true">↗</span></a>
    </nav>
  </header>

  <main>
    <section class="shell hero" id="about">
      <div class="hero-content">
        <div class="eyebrow"><span class="live-dot"></span> The ultimate IT quiz event</div>
        <h1>Think tech.<br><span class="gradient">Play smart.</span></h1>
        <p class="hero-copy">One stage. A whole world of technology. Put your IT instincts to the test and find out if you have what it takes to top the Qiztron leaderboard.</p>
        <div class="hero-actions">
          <button class="button" type="button" data-start-quiz>Start the challenge <span aria-hidden="true">→</span></button>
          <a class="text-link" href="#topics">Explore the topics <span aria-hidden="true">↓</span></a>
        </div>
      </div>

      <div class="visual" aria-hidden="true">
        <div class="orbit"><span class="orbit-dot"></span></div>
        <svg class="hero-emblem" viewBox="0 0 200 200">
          <defs>
            <linearGradient id="hero-gradient" x1="0" y1="0" x2="1" y2="1">
              <stop offset="0" stop-color="#c5aaff"/>
              <stop offset="1" stop-color="#68e2db"/>
            </linearGradient>
          </defs>
          <path d="M100 8 179.7 54v92L100 192 20.3 146V54L100 8Z" fill="rgba(21,24,46,.78)" stroke="url(#hero-gradient)" stroke-width="2"/>
          <path d="M125 71a37 37 0 1 0-6 55l20 16" fill="none" stroke="url(#hero-gradient)" stroke-linecap="round" stroke-width="12"/>
          <path d="m88 84 17 16-17 16" fill="none" stroke="#f6f5ff" stroke-linecap="round" stroke-linejoin="round" stroke-width="5"/>
          <circle cx="100" cy="100" r="58" fill="none" stroke="rgba(176,159,255,.17)" stroke-width="1"/>
        </svg>
        <div class="float-card one">
          <span class="card-icon" aria-hidden="true">⌘</span>
          <span><span class="card-label">YOUR BRAIN, BUT</span><br><span class="card-value">In tech mode</span></span>
        </div>
        <div class="float-card two">
          <span class="card-icon" aria-hidden="true">✦</span>
          <span><span class="card-label">READY, SET,</span><br><span class="card-value">Outsmart</span></span>
        </div>
      </div>
    </section>

    <section class="shell event-strip" aria-label="Event highlights">
      <div class="event-stat"><span class="stat-icon" aria-hidden="true">◷</span><span><span class="stat-label">Format</span><br><span class="stat-value">Fast-paced rounds</span></span></div>
      <div class="event-stat"><span class="stat-icon" aria-hidden="true">◇</span><span><span class="stat-label">Challenge</span><br><span class="stat-value">All things IT</span></span></div>
      <div class="event-stat"><span class="stat-icon" aria-hidden="true">⌁</span><span><span class="stat-label">Your mission</span><br><span class="stat-value">Claim the top spot</span></span></div>
    </section>

    <section class="shell section" id="topics">
      <div class="section-heading">
        <div><div class="section-kicker">A little bit of everything</div><h2>What do you know about tech?</h2></div>
        <p class="section-note">From the code behind your favorite apps to the networks that connect us all—bring your curiosity.</p>
      </div>
      <div class="topics">
        <article class="topic"><span class="topic-symbol" aria-hidden="true">&lt;/&gt;</span><h3>Code &amp; logic</h3><p>Think in algorithms. Crack the patterns.</p></article>
        <article class="topic"><span class="topic-symbol" aria-hidden="true">⌘</span><h3>AI &amp; the future</h3><p>Explore the tech changing everything.</p></article>
        <article class="topic"><span class="topic-symbol" aria-hidden="true">◈</span><h3>Cybersecurity</h3><p>Spot the threats. Protect the data.</p></article>
        <article class="topic"><span class="topic-symbol" aria-hidden="true">⌁</span><h3>Web &amp; networks</h3><p>Know what keeps the internet moving.</p></article>
      </div>
    </section>

    <section class="shell bottom-cta" id="challenge">
      <div><h2>Your next great answer starts here.</h2><p>Jump in, test your tech knowledge, and have some fun.</p></div>
      <button class="button" type="button" data-start-quiz>Take the quiz <span aria-hidden="true">→</span></button>
    </section>
  </main>

  <footer class="shell">
    <a class="brand" href="#" aria-label="Qiztron home">
      <svg class="brand-mark" viewBox="0 0 48 48" aria-hidden="true">
        <path d="M24 3.5 42 13.8v20.4L24 44.5 6 34.2V13.8L24 3.5Z" fill="none" stroke="#9e8af1" stroke-width="2.4"/>
        <path d="M30.6 19.2a8.6 8.6 0 1 0-2.1 11.6l5.2 4.1" fill="none" stroke="#67e1da" stroke-linecap="round" stroke-width="4"/>
      </svg>
      <span class="brand-name">QIZTRON</span>
    </a>
    <span>Curiosity looks good on you. © <span id="year"></span> Qiztron</span>
  </footer>

  <div class="quiz-overlay" id="quiz-overlay" role="dialog" aria-modal="true" aria-labelledby="quiz-title" aria-hidden="true">
    <div class="quiz-dialog">
      <div class="quiz-top"><span class="quiz-brand">QIZTRON · QUICK ROUND</span><button class="close-quiz" type="button" aria-label="Close quiz">×</button></div>
      <div class="progress-track" aria-hidden="true"><div class="progress-bar" id="progress-bar"></div></div>
      <div id="quiz-content" aria-live="polite"></div>
    </div>
  </div>

  <script>
    (() => {
      const questionBank = [
        {
          question: "Which language is most commonly used to add interactivity to web pages?",
          answers: ["Python", "JavaScript", "C++", "SQL"],
          correct: 1
        },
        {
          question: "What does 'HTTP' stand for?",
          answers: ["Hypertext Transfer Protocol", "High-speed Text Transmission Process", "Host Transfer Technology Program", "Hyperlink Text Tracking Protocol"],
          correct: 0
        },
        {
          question: "Which of these is an example of two-factor authentication?",
          answers: ["Using a longer password", "Changing your password monthly", "Password plus a one-time phone code", "Using the same password on two sites"],
          correct: 2
        },
        {
          question: "What is the main purpose of DNS?",
          answers: ["Encrypt files on your computer", "Translate domain names into IP addresses", "Back up your browser history", "Compress images for websites"],
          correct: 1
        },
        {
          question: "In AI, what does 'training data' refer to?",
          answers: ["The computer's hardware manual", "Examples used to teach a model patterns", "A list of saved passwords", "The model's source code"],
          correct: 1
        },
        {
          question: "Which data structure follows the last-in, first-out principle?",
          answers: ["Queue", "Stack", "Tree", "Graph"],
          correct: 1
        },
        {
          question: "What does RAM provide to a computer?",
          answers: ["Long-term file storage", "Temporary working memory", "A connection to Wi-Fi", "Power to the processor"],
          correct: 1
        },
        {
          question: "Which Git command creates a copy of a remote repository on your computer?",
          answers: ["git push", "git merge", "git clone", "git status"],
          correct: 2
        },
        {
          question: "What is the primary purpose of an operating system?",
          answers: ["Manage hardware and provide services for applications", "Design websites automatically", "Replace a computer's processor", "Connect every device directly to the internet"],
          correct: 0
        },
        {
          question: "Which number system uses only 0 and 1?",
          answers: ["Decimal", "Hexadecimal", "Binary", "Octal"],
          correct: 2
        },
        {
          question: "What does an SQL JOIN do?",
          answers: ["Combines related rows from tables", "Deletes a database", "Encrypts a network connection", "Sorts files on a computer"],
          correct: 0
        },
        {
          question: "Which protocol is commonly used to securely browse websites?",
          answers: ["FTP", "HTTPS", "SMTP", "DHCP"],
          correct: 1
        },
        {
          question: "What is an API primarily used for?",
          answers: ["Letting software systems communicate", "Increasing a monitor's resolution", "Removing viruses from a computer", "Compressing a hard drive"],
          correct: 0
        },
        {
          question: "Which practice helps protect an account from password guessing?",
          answers: ["Using a short, memorable password", "Reusing a password across sites", "Using a unique, long password", "Sharing your password with a friend"],
          correct: 2
        },
        {
          question: "In cloud computing, what does scalability mean?",
          answers: ["Changing the color of a website", "Adjusting resources to meet changing demand", "Moving files to a USB drive", "Running software without an operating system"],
          correct: 1
        },
        {
          question: "What is the main role of a firewall?",
          answers: ["Filter network traffic based on security rules", "Speed up typing", "Create backups of photos", "Translate code into machine language"],
          correct: 0
        },
        {
          question: "Which CSS property changes the text color?",
          answers: ["font-style", "background", "color", "display"],
          correct: 2
        },
        {
          question: "What does 'open source' software generally mean?",
          answers: ["Its source code is available to inspect and use under a license", "It can only run while online", "It has no source code", "It is always made by one company"],
          correct: 0
        },
        {
          question: "What is the purpose of a cache?",
          answers: ["Temporarily store data for faster access", "Permanently erase old files", "Block all internet traffic", "Create a new user account"],
          correct: 0
        }
      ];

      const QUESTION_COUNT = 10;
      const overlay = document.getElementById("quiz-overlay");
      const content = document.getElementById("quiz-content");
      const progress = document.getElementById("progress-bar");
      let roundQuestions = [];
      let previousRoundQuestionSet = null;
      let current = 0;
      let score = 0;
      let answered = false;
      let previousFocus = null;

      function shuffle(items) {
        for (let index = items.length - 1; index > 0; index--) {
          const swapIndex = Math.floor(Math.random() * (index + 1));
          [items[index], items[swapIndex]] = [items[swapIndex], items[index]];
        }
        return items;
      }

      function createRound() {
        const shuffledQuestions = shuffle([...questionBank]);
        const selectedQuestions = shuffledQuestions.slice(0, QUESTION_COUNT);
        if (previousRoundQuestionSet && selectedQuestions.every(item => previousRoundQuestionSet.has(item.question))) {
          selectedQuestions[QUESTION_COUNT - 1] = shuffledQuestions[QUESTION_COUNT];
        }
        roundQuestions = shuffle(selectedQuestions);
        previousRoundQuestionSet = new Set(roundQuestions.map(item => item.question));
      }

      function renderQuestion() {
        answered = false;
        const item = roundQuestions[current];
        progress.style.width = `${(current / QUESTION_COUNT) * 100}%`;
        content.innerHTML = `
          <div class="question-count">QUESTION ${current + 1} OF ${QUESTION_COUNT}</div>
          <h2 id="quiz-title">${item.question}</h2>
          <div class="answers">${item.answers.map((answer, index) =>
            `<button class="answer" type="button" data-answer="${index}">${answer}</button>`
          ).join("")}</div>
          <p class="quiz-feedback" id="quiz-feedback" role="status"></p>
          <button class="button quiz-next" id="quiz-next" type="button" hidden>${current === QUESTION_COUNT - 1 ? "See my score" : "Next question"} <span aria-hidden="true">→</span></button>
        `;
        content.querySelectorAll(".answer").forEach(button => {
          button.addEventListener("click", () => selectAnswer(Number(button.dataset.answer)));
        });
        document.getElementById("quiz-next").addEventListener("click", nextQuestion);
      }

      function selectAnswer(choice) {
        if (answered) return;
        answered = true;
        const correct = choice === roundQuestions[current].correct;
        if (correct) score++;
        content.querySelectorAll(".answer").forEach((button, index) => {
          button.disabled = true;
          if (index === roundQuestions[current].correct) button.classList.add("correct");
          else if (index === choice) button.classList.add("incorrect");
        });
        document.getElementById("quiz-feedback").textContent = correct
          ? "That's right! Nice one."
          : `Not quite — the answer is ${roundQuestions[current].answers[roundQuestions[current].correct]}.`;
        document.getElementById("quiz-next").hidden = false;
        document.getElementById("quiz-next").focus();
      }

      function nextQuestion() {
        current++;
        if (current < QUESTION_COUNT) {
          renderQuestion();
          content.querySelector(".answer").focus();
          return;
        }
        progress.style.width = "100%";
        const message = score === QUESTION_COUNT
          ? "A perfect round. The Qiztron leaderboard has your name written all over it."
          : score >= 6
            ? "Solid tech instincts. You're definitely in the running for the top spot."
            : "Every great tech mind starts with curiosity. Give it another go and beat your score.";
        content.innerHTML = `
          <div class="quiz-result">
            <div class="result-icon" aria-hidden="true">${score === QUESTION_COUNT ? "✦" : "⌁"}</div>
            <h2 id="quiz-title">You scored ${score} out of ${QUESTION_COUNT}</h2>
            <p>${message}</p>
            <button class="button quiz-next" id="quiz-restart" type="button">Play again <span aria-hidden="true">↻</span></button>
          </div>
        `;
        document.getElementById("quiz-restart").addEventListener("click", startQuiz);
        document.getElementById("quiz-restart").focus();
      }

      function startQuiz() {
        createRound();
        current = 0;
        score = 0;
        overlay.classList.add("open");
        overlay.setAttribute("aria-hidden", "false");
        document.body.style.overflow = "hidden";
        renderQuestion();
        content.querySelector(".answer").focus();
      }

      function closeQuiz() {
        overlay.classList.remove("open");
        overlay.setAttribute("aria-hidden", "true");
        document.body.style.overflow = "";
        if (previousFocus) previousFocus.focus();
      }

      document.querySelectorAll("[data-start-quiz]").forEach(button => {
        button.addEventListener("click", event => {
          event.preventDefault();
          previousFocus = button;
          startQuiz();
        });
      });
      document.querySelector(".close-quiz").addEventListener("click", closeQuiz);
      overlay.addEventListener("click", event => {
        if (event.target === overlay) closeQuiz();
      });
      document.addEventListener("keydown", event => {
        if (event.key === "Escape" && overlay.classList.contains("open")) closeQuiz();
      });
      document.getElementById("year").textContent = new Date().getFullYear();
    })();
  </script>
</body>
</html>
