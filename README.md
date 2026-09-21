<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="color-scheme" content="dark">
<title>Hariharan P — Full Stack Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Geist:wght@300;400;500;600&family=Geist+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    color-scheme: dark;
    --sky: #04050b;
    --card: rgba(18, 20, 30, .62);
    --inner: rgba(255, 255, 255, .055);
    --chip: rgba(255, 255, 255, .08);
    --line: rgba(255, 255, 255, .09);
    --text: #f1f2f6;
    --body: #cfd2dc;
    --muted: #8d92a3;
    --accent: #7aa2ff;
    --sans: "Geist", ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
    --mono: "Geist Mono", ui-monospace, "SF Mono", Menlo, Consolas, monospace;
    box-sizing: border-box;
    padding-top: env(safe-area-inset-top, 0px);
    padding-bottom: env(safe-area-inset-bottom, 0px);
  }
  *, *::before, *::after { box-sizing: border-box; }
  html { background: var(--sky); scroll-padding-top: calc(env(safe-area-inset-top, 0px) + 24px); }
  body {
    margin: 0; min-height: 100vh; color: var(--text); font-family: var(--sans);
    -webkit-font-smoothing: antialiased; background: transparent;
  }
  a { color: inherit; }

  /* ---------- sky ---------- */
  .sky {
    position: fixed; inset: 0; z-index: 0; pointer-events: none;
    background:
      radial-gradient(60% 45% at 12% -5%, rgba(64, 96, 214, .28), transparent 62%),
      radial-gradient(45% 40% at 95% 25%, rgba(122, 72, 206, .20), transparent 62%),
      radial-gradient(55% 40% at 50% 115%, rgba(30, 110, 170, .18), transparent 60%),
      var(--sky);
  }
  #stars { position: fixed; inset: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; }

  /* ---------- layout ---------- */
  .page { position: relative; z-index: 1; max-width: 1180px; margin: 0 auto; padding: clamp(20px, 5vw, 64px) clamp(14px, 4vw, 40px) 72px; display: grid; gap: 20px; }

  .card {
    background: var(--card);
    -webkit-backdrop-filter: blur(16px) saturate(1.1); backdrop-filter: blur(16px) saturate(1.1);
    border: 1px solid var(--line);
    border-radius: 28px; padding: 36px;
  }
  .card h2 { margin: 0; font-size: 22px; font-weight: 500; letter-spacing: -0.015em; }
  .card-head { display: flex; align-items: baseline; justify-content: space-between; gap: 16px; margin-bottom: 26px; }

  .hero { display: grid; grid-template-columns: minmax(0, 340px) minmax(0, 1fr); gap: 20px; }
  .portrait {
    padding: 0; aspect-ratio: 1 / 1; display: grid; place-items: center; overflow: hidden; position: relative;
    background:
      radial-gradient(90% 70% at 25% 10%, rgba(122, 162, 255, .28), transparent 60%),
      radial-gradient(80% 80% at 90% 100%, rgba(150, 100, 255, .22), transparent 60%),
      var(--card);
  }
  .portrait span { font-size: clamp(88px, 12vw, 150px); font-weight: 300; letter-spacing: -0.06em; line-height: 1; color: #fff; }

  .intro { display: flex; flex-direction: column; justify-content: center; }
  .crumb { font-family: var(--mono); font-size: 13px; color: var(--muted); margin: 0 0 22px; }
  .intro h1 { margin: 0; font-size: clamp(40px, 6vw, 66px); font-weight: 500; letter-spacing: -0.035em; line-height: 1.02; }
  .role { margin: 10px 0 26px; font-size: 20px; color: var(--muted); }
  .intro p.about { margin: 0 0 14px; font-size: 17px; line-height: 1.65; color: var(--body); max-width: 60ch; }
  .intro p.about b { color: #fff; font-weight: 500; }
  .cta { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 18px; }
  .btn {
    display: inline-flex; align-items: center; gap: 10px; padding: 13px 22px; border-radius: 14px;
    font-size: 16px; text-decoration: none; border: 1px solid rgba(255, 255, 255, .28); color: #fff;
    transition: background .15s, color .15s, border-color .15s;
  }
  .btn:hover { background: #f2f2f2; color: #0a0a0a; border-color: #f2f2f2; }
  .btn.solid { background: #f2f2f2; color: #0a0a0a; border-color: #f2f2f2; }
  .btn.solid:hover { background: #fff; }
  .btn:focus-visible { outline: 2px solid var(--accent); outline-offset: 3px; }
  svg.ic { width: 18px; height: 18px; stroke: currentColor; fill: none; stroke-width: 1.7; stroke-linecap: round; stroke-linejoin: round; flex: none; }

  .groups { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 14px; }
  @media (max-width: 720px) { .groups { grid-template-columns: 1fr; } }
  .group { background: var(--inner); border: 1px solid var(--line); border-radius: 20px; padding: 22px; }
  .group h3 { margin: 0 0 16px; font-size: 16px; font-weight: 500; color: #fff; }
  .chips { display: flex; flex-wrap: wrap; gap: 8px; }
  .chip { display: inline-flex; align-items: center; gap: 9px; background: var(--chip); color: var(--body); font-size: 14px; padding: 7px 14px 7px 9px; border-radius: 999px; line-height: 1.2; }
  .chip img, .chip svg.g { width: 20px; height: 20px; flex: none; display: block; }

  .tools { display: grid; grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 14px; }
  .tool { background: var(--inner); border: 1px solid var(--line); border-radius: 20px; padding: 24px; display: flex; flex-direction: column; gap: 20px; }
  .ticon { width: 64px; height: 64px; border-radius: 16px; background: rgba(255, 255, 255, .08); display: grid; place-items: center; margin: 0; }
  .ticon img { width: 40px; height: 40px; object-fit: contain; display: block; }
  .tool.aws .ticon { width: 88px; }
  .tool.aws .ticon img { width: 64px; }
  .tool strong { display: block; font-size: 18px; font-weight: 500; color: #fff; }
  .tool span { display: block; font-size: 14px; color: var(--muted); margin-top: 4px; }

  @media (max-width: 960px) { .tools { grid-template-columns: repeat(2, minmax(0, 1fr)); } }
  @media (max-width: 820px) {
    .hero { grid-template-columns: 1fr; }
    .portrait { aspect-ratio: 16 / 9; }
    .card { padding: 26px; border-radius: 24px; }
  }
  @media (max-width: 420px) { .tools { grid-template-columns: 1fr; } }
</style>
</head>
<body>
<div class="sky" aria-hidden="true"></div>
<canvas id="stars" aria-hidden="true"></canvas>

<div class="page">

  <section class="hero">
    <div class="card portrait" aria-hidden="true"><span>HP</span></div>

    <div class="card intro">
      <p class="crumb">hariharan / README.md</p>
      <h1>Hariharan P</h1>
      <p class="role">Full Stack Developer</p>
      <p class="about">I have <b>2+ years</b> of experience building and deploying production web applications with React.js, Node.js and Python.</p>
      <p class="about">I own features end to end: API design, database architecture, responsive frontends and AWS deployment. Most recently I shipped a production AI feature using <b>RAG with the Gemini API</b>.</p>
      <div class="cta">
        <a class="btn solid" href="mailto:hariharan23kph@gmail.com">
          <svg class="ic" viewBox="0 0 24 24"><rect x="3" y="5" width="18" height="14" rx="2.5"/><path d="M3.5 7l8.5 6 8.5-6"/></svg>
          Say hello
        </a>
        <a class="btn" href="https://linkedin.com/in/hariharan504047306" target="_blank" rel="noopener">
          <svg class="ic" viewBox="0 0 24 24"><path d="M10 14a4 4 0 0 0 5.7 0l3-3a4 4 0 0 0-5.7-5.7l-1 1"/><path d="M14 10a4 4 0 0 0-5.7 0l-3 3a4 4 0 0 0 5.7 5.7l1-1"/></svg>
          LinkedIn
        </a>
      </div>
    </div>
  </section>

  <section class="card" id="skills">
        <div class="card-head"><h2>Skills</h2></div>
        <div class="groups">
<div class="group"><h3>Frontend</h3><div class="chips"><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" alt="" width="20" height="20">JavaScript</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg" alt="" width="20" height="20">TypeScript</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/react/react-original.svg" alt="" width="20" height="20">React.js</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nextjs/nextjs-original.svg" alt="" width="20" height="20">Next.js</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/redux/redux-original.svg" alt="" width="20" height="20">Redux</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" alt="" width="20" height="20">HTML5</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" alt="" width="20" height="20">CSS3</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/tailwindcss/tailwindcss-original.svg" alt="" width="20" height="20">Tailwind CSS</span></div></div>
<div class="group"><h3>Backend</h3><div class="chips"><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/nodejs/nodejs-original.svg" alt="" width="20" height="20">Node.js</span><span class="chip"><img src="data:image/svg+xml;base64,PHN2ZyBmaWxsPSIjZjVmNWY1IiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxMjggMTI4Ij48cGF0aCBkPSJNMTI2LjY3IDk4LjQ0Yy00LjU2IDEuMTYtNy4zOC4wNS05LjkxLTMuNzUtNS42OC04LjUxLTExLjk1LTE2LjYzLTE4LTI0LjktLjc4LTEuMDctMS41OS0yLjEyLTIuNi0zLjQ1Qzg5IDc2IDgxLjg1IDg1LjIgNzUuMTQgOTQuNzdjLTIuNCAzLjQyLTQuOTIgNC45MS05LjQgMy43bDI2LjkyLTM2LjEzTDY3LjYgMjkuNzFjNC4zMS0uODQgNy4yOS0uNDEgOS45MyAzLjQ1IDUuODMgOC41MiAxMi4yNiAxNi42MyAxOC42NyAyNS4yMSA2LjQ1LTguNTUgMTIuOC0xNi42NyAxOC44LTI1LjExIDIuNDEtMy40MiA1LTQuNzIgOS4zMy0zLjQ2LTMuMjggNC4zNS02LjQ5IDguNjMtOS43MiAxMi44OC00LjM2IDUuNzMtOC42NCAxMS41My0xMy4xNiAxNy4xNC0xLjYxIDItMS4zNSAzLjMuMDkgNS4xOUMxMDkuOSA3NiAxMTguMTYgODcuMSAxMjYuNjcgOTguNDR6TTEuMzMgNjEuNzRjLjcyLTMuNjEgMS4yLTcuMjkgMi4yLTEwLjgzIDYtMjEuNDMgMzAuNi0zMC4zNCA0Ny41LTE3LjA2QzYwLjkzIDQxLjY0IDYzLjM5IDUyLjYyIDYyLjkgNjVINy4xYy0uODQgMjIuMjEgMTUuMTUgMzUuNjIgMzUuNTMgMjguNzggNy4xNS0yLjQgMTEuMzYtOCAxMy40Ny0xNSAxLjA3LTMuNTEgMi44NC00LjA2IDYuMTQtMy4wNi0xLjY5IDguNzYtNS41MiAxNi4wOC0xMy41MiAyMC42Ni0xMiA2Ljg2LTI5LjEzIDQuNjQtMzguMTQtNC44OUM1LjI2IDg1Ljg5IDMgNzguOTIgMiA3MS4zOWMtLjE1LTEuMi0uNDYtMi4zOC0uNy0zLjU3cS4wMy0zLjA0LjAzLTYuMDh6bTUuODctMS40OWg1MC40M2MtLjMzLTE2LjA2LTEwLjMzLTI3LjQ3LTI0LTI3LjU3LTE1LS4xMi0yNS43OCAxMS4wMi0yNi40MyAyNy41N3oiLz48L3N2Zz4=" alt="" width="20" height="20">Express.js</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" alt="" width="20" height="20">Python</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/fastapi/fastapi-original.svg" alt="" width="20" height="20">FastAPI</span><span class="chip"><img src="data:image/svg+xml;base64,PHN2ZyB2ZXJzaW9uPSIxLjAiIHZpZXdCb3g9IjAgMCAxMjggMTI4IiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGZpbGw9IiM0NGI3OGIiPjxwYXRoIGQ9Ik01OS40NDggMGgyMC45M3Y5Ni44OGMtMTAuNzM3IDIuMDQtMTguNjIgMi44NTUtMjcuMTgxIDIuODU1LTI1LjU1MS0uMDAxLTM4Ljg3LTExLjU1MS0zOC44Ny0zMy43MDUgMC0yMS4zMzggMTQuMTM1LTM1LjIgMzYuMDE1LTM1LjIgMy4zOTggMCA1Ljk4LjI3MiA5LjEwNiAxLjA4N3ptMCA0OC43NjVjLTIuNDQ2LS44MTUtNC40ODUtMS4wODYtNy4wNjctMS4wODYtMTAuNiAwLTE2LjcxNyA2LjUyMy0xNi43MTcgMTcuOTM5IDAgMTEuMTQ1IDUuODQ1IDE3LjI2IDE2LjU4MiAxNy4yNiAyLjMwOSAwIDQuMjEyLS4xMzYgNy4yMDItLjU0MnoiLz48cGF0aCBkPSJNMTEzLjY3MiAzMi4zMjFWODAuODRjMCAxNi43MTctMS4yMjQgMjQuNzM1LTQuODkzIDMxLjY2Ni0zLjM5OCA2LjY2MS03Ljg4MyAxMC44NzMtMTcuMTI0IDE1LjQ5NGwtMTkuNDM1LTkuMjQxYzkuMjQyLTQuMzUgMTMuNzI2LTguMTUzIDE2LjU4LTE0IDIuOTktNS45NzkgMy45NDMtMTIuOTEgMy45NDMtMzEuMTIyVjMyLjMyMXpNOTIuNzQyLjExMWgyMC45M3YyMS40NzRoLTIwLjkzeiIvPjwvc3ZnPgo=" alt="" width="20" height="20">Django</span><span class="chip"><svg class="g" viewBox="0 0 24 24" fill="none" stroke="#9ca3af" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M8 7l-5 5 5 5M16 7l5 5-5 5"/><path d="M13.5 5l-3 14"/></svg>REST APIs</span><span class="chip"><img src="https://cdn.simpleicons.org/jsonwebtokens/d63aff" alt="" width="20" height="20">JWT Authentication</span></div></div>
<div class="group"><h3>Database</h3><div class="chips"><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mongodb/mongodb-original.svg" alt="" width="20" height="20">MongoDB</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-original.svg" alt="" width="20" height="20">PostgreSQL</span><span class="chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/redis/redis-original.svg" alt="" width="20" height="20">Redis</span></div></div>
<div class="group"><h3>AI</h3><div class="chips"><span class="chip"><img src="https://cdn.simpleicons.org/googlegemini/8e75b2" alt="" width="20" height="20">Gemini API</span><span class="chip"><svg class="g" viewBox="0 0 24 24" fill="none" stroke="#9ca3af" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><ellipse cx="12" cy="6" rx="7" ry="3"/><path d="M5 6v6c0 1.7 3.1 3 7 3s7-1.3 7-3V6"/><path d="M5 12v6c0 1.7 3.1 3 7 3s7-1.3 7-3v-6"/></svg>RAG Architecture</span><span class="chip"><svg class="g" viewBox="0 0 24 24" fill="none" stroke="#9ca3af" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="12" cy="12" r="3"/><path d="M12 3v3M12 18v3M3 12h3M18 12h3M5.6 5.6l2.1 2.1M16.3 16.3l2.1 2.1M18.4 5.6l-2.1 2.1M7.7 16.3l-2.1 2.1"/></svg>LLM Integration</span></div></div>
</div>
      </section>

  <section class="card" id="tools">
        <div class="card-head"><h2>Tools</h2></div>
        <div class="tools">
<div class="tool "><span class="ticon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg" alt="" ></span><div><strong>Git</strong><span>Version control</span></div></div>
<div class="tool "><span class="ticon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original.svg" alt="" ></span><div><strong>Docker</strong><span>Containers</span></div></div>
<div class="tool "><span class="ticon"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/jenkins/jenkins-original.svg" alt="" ></span><div><strong>Jenkins</strong><span>CI/CD pipelines</span></div></div>
<div class="tool aws"><span class="ticon"><img src="data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTI4IDEyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxwYXRoIGZpbGw9IiNmNWY1ZjUiIGQ9Ik0zNi4zNzkgNTMuNjRjMCAxLjU2LjE2OCAyLjgyNS40NjUgMy43NS4zMzYuOTI2Ljc1OCAxLjkzOCAxLjM0NyAzLjAzMi4yMDcuMzM2LjI5My42NzIuMjkzLjk2OSAwIC40MTgtLjI1NC44NC0uOCAxLjI2MWwtMi42NTMgMS43N2MtLjM3OS4yNS0uNzU4LjM3OS0xLjA5My4zNzktLjQyMiAwLS44NDQtLjIxMS0xLjI2Ni0uNTlhMTMuMjggMTMuMjggMCAwIDEtMS41MTYtMS45OCAzNC4xNTMgMzQuMTUzIDAgMCAxLTEuMzA0LTIuNDg1Yy0zLjI4MiAzLjg3NS03LjQxIDUuODEzLTEyLjM4IDUuODEzLTMuNTM1IDAtNi4zNTUtMS4wMTItOC40MjEtMy4wMzItMi4wNjMtMi4wMjMtMy4xMTQtNC43MTgtMy4xMTQtOC4wODYgMC0zLjU3OCAxLjI2Mi02LjQ4NCAzLjgzMy04LjY3MSAyLjU2Ni0yLjE5MiA1Ljk3Ni0zLjI4NiAxMC4zMTYtMy4yODYgMS40MyAwIDIuOTAyLjEyNSA0LjQ2LjMzNiAxLjU2LjIxMSAzLjE2MS41NDcgNC44NDUuOTI2di0zLjA3NGMwLTMuMi0uNjc2LTUuNDMtMS45OC02LjczNEMyNi4wNjEgMzIuNjMzIDIzLjc4OCAzMiAyMC41NDYgMzJjLTEuNDczIDAtMi45ODguMTY4LTQuNTQ3LjU0N2EzMy40MTYgMzMuNDE2IDAgMCAwLTQuNTQ3IDEuNDMzYy0uNjc2LjI5My0xLjE4LjQ2MS0xLjQ3My41NDctLjI5Ni4wODItLjUwNy4xMjUtLjY3NS4xMjUtLjU5IDAtLjg4My0uNDIyLS44ODMtMS4zMDR2LTIuMDYzYzAtLjY3Ni4wODItMS4xOC4yOTMtMS40NzYuMjEtLjI5My41OS0uNTg2IDEuMTgtLjg4MyAxLjQ3Mi0uNzU4IDMuMjQyLTEuMzkgNS4zMDQtMS44OTUgMi4wNjMtLjU0NyA0LjI1NC0uOCA2LjU3LS44IDUuMDA4IDAgOC42NzIgMS4xMzYgMTEuMDMyIDMuNDEgMi4zMTYgMi4yNzMgMy40OTIgNS43MjYgMy40OTIgMTAuMzU5djEzLjY0Wm0tMTcuMDk0IDYuNDAzYzEuMzg3IDAgMi44Mi0uMjU0IDQuMzM2LS43NTggMS41MTYtLjUwOCAyLjg2My0xLjQzMyA0LTIuNjk1LjY3Mi0uOCAxLjE4LTEuNjg0IDEuNDMtMi42OTUuMjU0LTEuMDEyLjQyMi0yLjIzLjQyMi0zLjY2NXYtMS43NjVhMzQuNDAxIDM0LjQwMSAwIDAgMC0zLjg3MS0uNzE5IDMxLjgxNiAzMS44MTYgMCAwIDAtMy45NjEtLjI1Yy0yLjgyIDAtNC44ODMuNTQ3LTYuMjc0IDEuNjg0LTEuMzg3IDEuMTM2LTIuMDYyIDIuNzM0LTIuMDYyIDQuODQgMCAxLjk4LjUwNCAzLjQ1MyAxLjU1OCA0LjQ2NCAxLjAxMiAxLjA1MSAyLjQ4NSAxLjU1OSA0LjQyMiAxLjU1OVptMzMuODA5IDQuNTQ3Yy0uNzU4IDAtMS4yNjItLjEyNS0xLjU5OC0uNDIyLS4zNC0uMjU0LS42MzMtLjg0LS44ODctMS42NEw0MC43MTUgMjkuOThjLS4yNS0uODQzLS4zOC0xLjM5LS4zOC0xLjY4NyAwLS42NzIuMzM3LTEuMDUgMS4wMTMtMS4wNWg0LjEyNWMuOCAwIDEuMzQ3LjEyNCAxLjY0NC40MjEuMzM2LjI1LjU5Ljg0Ljg0IDEuNjRsNy4wNzQgMjcuODc2IDYuNTctMjcuODc1Yy4yMDgtLjg0LjQ2Mi0xLjM5Ljc5Ny0xLjY0LjM0LS4yNTUuOTMtLjQyMyAxLjY4OC0uNDIzaDMuMzY3Yy44IDAgMS4zNDguMTI1IDEuNjg0LjQyMi4zMzYuMjUuNjMzLjg0LjggMS42NGw2LjY1MyAyOC4yMTIgNy4yODUtMjguMjExYy4yNS0uODQuNTQ3LTEuMzkuODQtMS42NC4zMzYtLjI1NS44ODctLjQyMyAxLjY0NC0uNDIzaDMuOTE0Yy42NzYgMCAxLjA1NS4zMzYgMS4wNTUgMS4wNTEgMCAuMjEtLjA0My40MjItLjA4Ni42NzYtLjA0My4yNTQtLjEyNS41OS0uMjkzIDEuMDVMODAuODAxIDYyLjU3Yy0uMjU0Ljg0LS41NDcgMS4zODctLjg4NyAxLjY0LS4zMzYuMjU1LS44ODMuNDIzLTEuNTk4LjQyM2gtMy42MmMtLjgwMSAwLTEuMzQ4LS4xMy0xLjY4NC0uNDIyLS4zNC0uMjk3LS42MzMtLjg0NC0uODAxLTEuNjg0bC02LjUyNy0yNy4xNi02LjQ4NSAyNy4xMTdjLS4yMS44NDQtLjQ2IDEuMzkxLS44IDEuNjg0LS4zMzcuMjk3LS45MjYuNDIyLTEuNjg0LjQyMlptNTQuMTA1IDEuMTM3Yy0yLjE4NyAwLTQuMzc5LS4yNTQtNi40ODQtLjc1OC0yLjEwNi0uNTA0LTMuNzQ2LTEuMDU1LTQuODQtMS42ODQtLjY3Ni0uMzc5LTEuMTM3LS44LTEuMzA1LTEuMThhMi45MTkgMi45MTkgMCAwIDEtLjI1NC0xLjE4di0yLjE0OGMwLS44ODIuMzM2LTEuMzA0Ljk3LTEuMzA0LjI1IDAgLjUwMy4wNDMuNzU3LjEyOS4yNS4wODIuNjI5LjI1IDEuMDUuNDE4YTIzLjEwMiAyMy4xMDIgMCAwIDAgNC42MzQgMS40NzZjMS42ODMuMzM2IDMuMzI0LjUwNCA1LjAxMS41MDQgMi42NTMgMCA0LjcxNS0uNDY1IDYuMTQ1LTEuMzkgMS40MzMtLjkyNiAyLjE5MS0yLjI3NCAyLjE5MS00IDAtMS4xOC0uMzc5LTIuMTQ1LTEuMTM2LTIuOTQ2LS43NTgtLjgtMi4xOTItMS41MTYtNC4yNTQtMi4xOTFsLTYuMTA2LTEuODk1Yy0zLjA3NC0uOTY5LTUuMzQ4LTIuMzk4LTYuNzM0LTQuMjkzLTEuMzktMS44NTUtMi4xMDYtMy45MTgtMi4xMDYtNi4xMDUgMC0xLjc3LjM4LTMuMzI4IDEuMTM3LTQuNjc2YTEwLjgyOSAxMC44MjkgMCAwIDEgMy4wMzEtMy40NTNjMS4yNjItLjk2NSAyLjY5Ni0xLjY4NCA0LjM4LTIuMTg4IDEuNjgzLS41MDQgMy40NTItLjcxNSA1LjMwNC0uNzE1LjkyNiAwIDEuODk0LjA0MyAyLjgyLjE2OC45NjkuMTI1IDEuODUyLjI5MyAyLjczOC40NjEuODQuMjExIDEuNjQxLjQyMiAyLjM5OS42NzYuNzU4LjI1NCAxLjM0OC41MDQgMS43Ny43NTguNTkuMzM2IDEuMDExLjY3MiAxLjI2MSAxLjA1LjI1NC4zNC4zNzkuODAyLjM3OSAxLjM5MXYxLjk4YzAgLjg4NC0uMzM2IDEuMzQ4LS45NjkgMS4zNDgtLjMzNiAwLS44ODMtLjE3MS0xLjU5Ny0uNTA3LTIuNDAzLTEuMDk0LTUuMDk4LTEuNjQxLTguMDg2LTEuNjQxLTIuMzk5IDAtNC4yOTMuMzc5LTUuNTk4IDEuMTgtMS4zMDkuNzk3LTEuOTggMi4wMi0xLjk4IDMuNzQ2IDAgMS4xOC40MjEgMi4xOTEgMS4yNjEgMi45ODguODQ0LjggMi40MDMgMS42MDIgNC42MzMgMi4zMTZsNS45OCAxLjg5NWMzLjAzMi45NjkgNS4yMiAyLjMxNiA2LjUyNCA0LjA0MyAxLjMwNSAxLjcyNyAxLjkzOCAzLjcwNyAxLjkzOCA1Ljg5NSAwIDEuODEyLS4zOCAzLjQ1My0xLjA5NCA0Ljg4Mi0uNzU4IDEuNDM0LTEuNzcgMi42OTYtMy4wNzQgMy43MDctMS4zMDUgMS4wNTEtMi44NjQgMS44MDktNC42NzIgMi4zNi0xLjg5NS41ODYtMy44NzUuODgzLTYuMDI0Ljg4M1ptMCAwIi8+Cgk8cGF0aCBmaWxsPSIjZjkwIiBkPSJNMTE4IDczLjM0OGMtNC40MzIuMDYzLTkuNjY0IDEuMDUyLTEzLjYyMSAzLjgzMi0xLjIyMy44ODMtMS4wMTIgMi4wNjIuMzM2IDEuODk0IDQuNTA4LS41NDcgMTQuNDQtMS43MjYgMTYuMjEuNTQ3IDEuNzcgMi4yMy0xLjk3NiAxMS42Mi0zLjY2MyAxNS43OS0uNTA0IDEuMjYuNTkgMS43NjkgMS43MjYuOCA3LjQxLTYuMjMxIDkuMzQ4LTE5LjI0MiA3LjgzMi0yMS4xMzctLjc1Ny0uOTI1LTQuMzg4LTEuNzktOC44Mi0xLjcyNnpNMS42MyA3NS44NTljLS45MjcuMTE2LTEuMzQ3IDEuMjM2LS4zNjggMi4xMjEgMTYuNTA4IDE0LjkwMiAzOC4zNTkgMjMuODcyIDYyLjYxMyAyMy44NzIgMTcuMzA1IDAgMzcuNDMtNS40MyA1MS4yODEtMTUuNjYgMi4yNzMtMS42ODguMjk3LTQuMjU0LTIuMDItMy4yMDQtMTUuNTM0IDYuNTctMzIuNDIxIDkuNzctNDcuNzg4IDkuNzctMjIuNzc4IDAtNDQuOC02LjI3My02Mi42NTMtMTYuNjMzLS4zOS0uMjMxLS43NTUtLjMwNC0xLjA2NC0uMjY2eiIvPgo8L3N2Zz4=" alt="" ></span><div><strong>AWS</strong><span>EC2 · S3 · Lambda · Cognito · WAF</span></div></div>
</div>
      </section>

</div>

<script>
(function () {
  var canvas = document.getElementById('stars');
  var ctx = canvas.getContext('2d');
  var reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  var W = 0, H = 0, stars = [], shoot = null, nextShoot = 0;
  var mx = 0, my = 0, tx = 0, ty = 0, scrollY = 0;
  var tints = [[255,255,255],[255,255,255],[255,255,255],[170,200,255],[200,180,255],[255,226,190]];

  function resize() {
    var dpr = Math.min(window.devicePixelRatio || 1, 2);
    W = window.innerWidth; H = window.innerHeight;
    canvas.width = W * dpr; canvas.height = H * dpr;
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
    var n = Math.min(420, Math.round(W * H / 5200));
    stars = [];
    for (var i = 0; i < n; i++) {
      var z = Math.random();
      stars.push({
        x: Math.random() * W, y: Math.random() * H, z: z,
        r: 0.35 + z * 1.15, a: 0.35 + Math.random() * 0.65,
        s: 0.6 + Math.random() * 2.2, p: Math.random() * 6.283,
        c: tints[Math.floor(Math.random() * tints.length)]
      });
    }
    draw(performance.now());
  }

  function wrap(v, m) { return ((v % m) + m) % m; }

  function draw(t) {
    ctx.clearRect(0, 0, W, H);
    tx += (mx - tx) * 0.04; ty += (my - ty) * 0.04;
    for (var i = 0; i < stars.length; i++) {
      var s = stars[i];
      var tw = reduce ? 0.8 : 0.5 + 0.5 * Math.sin(t * 0.001 * s.s + s.p);
      var alpha = s.a * (0.3 + 0.7 * tw);
      var x = wrap(s.x + tx * s.z * 18, W);
      var y = wrap(s.y - (reduce ? 0 : t * 0.004) * (0.15 + s.z) - scrollY * s.z * 0.22 + ty * s.z * 12, H);
      var c = s.c;
      if (s.r > 1.05) {
        ctx.fillStyle = 'rgba(' + c[0] + ',' + c[1] + ',' + c[2] + ',' + (alpha * 0.12) + ')';
        ctx.beginPath(); ctx.arc(x, y, s.r * 3.2, 0, 6.283); ctx.fill();
      }
      ctx.fillStyle = 'rgba(' + c[0] + ',' + c[1] + ',' + c[2] + ',' + alpha + ')';
      ctx.beginPath(); ctx.arc(x, y, s.r, 0, 6.283); ctx.fill();
    }
    if (!reduce) {
      if (!shoot && t > nextShoot) {
        var ang = 0.5 + Math.random() * 0.35;
        shoot = { x: Math.random() * W * 0.8, y: Math.random() * H * 0.4, vx: Math.cos(ang) * 11, vy: Math.sin(ang) * 11, life: 0 };
      }
      if (shoot) {
        shoot.x += shoot.vx; shoot.y += shoot.vy; shoot.life++;
        var k = Math.max(0, 1 - shoot.life / 55);
        var g = ctx.createLinearGradient(shoot.x, shoot.y, shoot.x - shoot.vx * 9, shoot.y - shoot.vy * 9);
        g.addColorStop(0, 'rgba(255,255,255,' + (0.9 * k) + ')');
        g.addColorStop(1, 'rgba(255,255,255,0)');
        ctx.strokeStyle = g; ctx.lineWidth = 1.6; ctx.lineCap = 'round';
        ctx.beginPath(); ctx.moveTo(shoot.x, shoot.y); ctx.lineTo(shoot.x - shoot.vx * 9, shoot.y - shoot.vy * 9); ctx.stroke();
        if (shoot.life > 55) { shoot = null; nextShoot = t + 5000 + Math.random() * 6000; }
      }
    }
  }

  function loop(t) { draw(t); requestAnimationFrame(loop); }

  window.addEventListener('resize', resize);
  window.addEventListener('scroll', function () { scrollY = window.scrollY || 0; if (reduce) draw(0); }, { passive: true });
  window.addEventListener('pointermove', function (e) {
    mx = (e.clientX / W - 0.5) * 2; my = (e.clientY / H - 0.5) * 2;
  }, { passive: true });

  resize();
  nextShoot = performance.now() + 2500;
  if (!reduce) requestAnimationFrame(loop);
})();
</script>
</body>
</html>
