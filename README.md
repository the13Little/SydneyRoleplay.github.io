<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sydney RP — Community Portal</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --brand: #0861fa;
  --brand-dark: #0448c4;
  --brand-glow: rgba(8,97,250,0.18);
  --bg: #060b14;
  --bg2: #0b1220;
  --bg3: #111827;
  --surface: #141e2e;
  --surface2: #1a2640;
  --border: rgba(8,97,250,0.2);
  --border2: rgba(255,255,255,0.07);
  --text: #eef2ff;
  --muted: #7b8fb0;
  --accent: #38bdf8;
  --danger: #f87171;
  --success: #4ade80;
  --warn: #fbbf24;
  --r: 10px;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: 'DM Sans', sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ─── NAV ─── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 2.5rem; height: 64px;
  background: rgba(6,11,20,0.85);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
}
.nav-logo {
  font-family: 'Bebas Neue', sans-serif;
  font-size: 28px; letter-spacing: 2px;
  color: var(--brand);
}
.nav-logo span { color: var(--text); }
.nav-links { display: flex; gap: 2rem; align-items: center; }
.nav-links a {
  color: var(--muted); text-decoration: none; font-size: 14px; font-weight: 500;
  letter-spacing: 0.5px; transition: color .2s;
}
.nav-links a:hover { color: var(--text); }
.nav-btn {
  background: var(--brand); color: #fff; border: none; border-radius: 8px;
  padding: 8px 18px; font-size: 14px; font-weight: 600; cursor: pointer;
  transition: background .2s, transform .1s;
}
.nav-btn:hover { background: var(--brand-dark); }
.hamburger { display: none; cursor: pointer; flex-direction: column; gap: 5px; }
.hamburger span { width: 22px; height: 2px; background: var(--text); border-radius: 2px; transition: .3s; }

/* ─── PAGES ─── */
.page { display: none; min-height: 100vh; padding-top: 64px; }
.page.active { display: block; }

/* ─── HERO ─── */
#home {
  position: relative; overflow: hidden;
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  min-height: 100vh; text-align: center; padding: 80px 2rem 60px;
}
.hero-grid {
  position: absolute; inset: 0; opacity: 0.06;
  background-image: linear-gradient(var(--brand) 1px, transparent 1px),
    linear-gradient(90deg, var(--brand) 1px, transparent 1px);
  background-size: 60px 60px;
}
.hero-glow {
  position: absolute; top: 10%; left: 50%; transform: translateX(-50%);
  width: 700px; height: 400px;
  background: radial-gradient(ellipse, rgba(8,97,250,0.15) 0%, transparent 70%);
  pointer-events: none;
}
.hero-badge {
  display: inline-flex; align-items: center; gap: 8px;
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 100px; padding: 6px 16px; font-size: 12px;
  color: var(--accent); font-weight: 500; letter-spacing: 0.5px; margin-bottom: 24px;
}
.badge-dot { width: 6px; height: 6px; background: var(--success); border-radius: 50%; animation: pulse 2s infinite; }
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }
.hero h1 {
  font-family: 'Bebas Neue', sans-serif;
  font-size: clamp(56px, 10vw, 120px);
  line-height: 0.9; letter-spacing: 4px;
  margin-bottom: 20px;
}
.hero h1 .blue { color: var(--brand); }
.hero p {
  font-size: 18px; color: var(--muted); max-width: 520px; margin: 0 auto 36px;
  line-height: 1.7;
}
.hero-btns { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
.btn-primary {
  background: var(--brand); color: #fff; border: none; border-radius: var(--r);
  padding: 14px 28px; font-size: 15px; font-weight: 600; cursor: pointer; transition: .2s;
}
.btn-primary:hover { background: var(--brand-dark); transform: translateY(-1px); }
.btn-outline {
  background: transparent; color: var(--text);
  border: 1px solid var(--border2); border-radius: var(--r);
  padding: 14px 28px; font-size: 15px; font-weight: 500; cursor: pointer; transition: .2s;
}
.btn-outline:hover { border-color: var(--brand); color: var(--brand); }

/* ─── STATS STRIP ─── */
.stats-strip {
  display: flex; justify-content: center; gap: 0; flex-wrap: wrap;
  margin: 56px 0 0; border-top: 1px solid var(--border2);
  border-bottom: 1px solid var(--border2); width: 100%;
}
.stat-item {
  flex: 1; min-width: 140px; max-width: 200px;
  text-align: center; padding: 28px 16px;
  border-right: 1px solid var(--border2);
}
.stat-item:last-child { border-right: none; }
.stat-num { font-family: 'Bebas Neue', sans-serif; font-size: 42px; color: var(--brand); }
.stat-label { font-size: 12px; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; margin-top: 4px; }

/* ─── SECTIONS ─── */
.section { padding: 80px 2rem; max-width: 1100px; margin: 0 auto; }
.section-title {
  font-family: 'Bebas Neue', sans-serif;
  font-size: 48px; letter-spacing: 2px; margin-bottom: 8px;
}
.section-title .blue { color: var(--brand); }
.section-sub { color: var(--muted); font-size: 16px; margin-bottom: 44px; }
.divider { border: none; border-top: 1px solid var(--border2); margin: 0; }

/* ─── SERVER STATUS ─── */
.status-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 16px; }
.status-card {
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: var(--r); padding: 20px 22px;
  transition: border-color .2s;
}
.status-card:hover { border-color: var(--border); }
.sc-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
.sc-name { font-weight: 600; font-size: 15px; }
.status-pill {
  font-size: 11px; font-weight: 600; padding: 3px 10px; border-radius: 100px;
  text-transform: uppercase; letter-spacing: 0.5px;
}
.online { background: rgba(74,222,128,0.15); color: var(--success); }
.offline { background: rgba(248,113,113,0.15); color: var(--danger); }
.maintenance { background: rgba(251,191,36,0.15); color: var(--warn); }
.sc-detail { font-size: 13px; color: var(--muted); margin-top: 6px; }
.sc-num { font-family: 'DM Mono', monospace; font-size: 28px; font-weight: 500; color: var(--text); }

/* ─── DEPT CARDS ─── */
.dept-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 16px; }
.dept-card {
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: var(--r); padding: 24px; cursor: pointer;
  transition: border-color .2s, transform .2s;
  text-decoration: none; color: inherit;
  display: block;
}
.dept-card:hover { border-color: var(--brand); transform: translateY(-3px); }
.dept-icon {
  width: 44px; height: 44px; border-radius: 10px;
  background: var(--brand-glow); border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  font-size: 22px; margin-bottom: 14px;
}
.dept-name { font-weight: 600; font-size: 16px; margin-bottom: 6px; }
.dept-desc { font-size: 13px; color: var(--muted); line-height: 1.6; margin-bottom: 14px; }
.dept-link {
  font-size: 13px; color: var(--brand); font-weight: 500;
  display: inline-flex; align-items: center; gap: 4px;
}

/* ─── FORMS ─── */
.form-container {
  max-width: 680px; margin: 0 auto;
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: 14px; padding: 36px 40px;
}
.form-tabs { display: flex; gap: 4px; margin-bottom: 32px; background: var(--bg2); border-radius: 10px; padding: 4px; }
.ftab {
  flex: 1; padding: 10px; text-align: center; border-radius: 8px;
  cursor: pointer; font-size: 14px; font-weight: 500; color: var(--muted); transition: .2s;
}
.ftab.active { background: var(--brand); color: #fff; }
.form-section { display: none; }
.form-section.active { display: block; }
.form-group { margin-bottom: 20px; }
.form-label { display: block; font-size: 13px; font-weight: 500; color: var(--muted); margin-bottom: 8px; text-transform: uppercase; letter-spacing: 0.5px; }
.form-input, .form-select, .form-textarea {
  width: 100%; background: var(--bg2); border: 1px solid var(--border2);
  border-radius: 8px; color: var(--text); font-family: inherit;
  font-size: 14px; padding: 11px 14px; outline: none; transition: border-color .2s;
  appearance: none;
}
.form-input:focus, .form-select:focus, .form-textarea:focus { border-color: var(--brand); }
.form-textarea { resize: vertical; min-height: 110px; line-height: 1.6; }
.form-select { cursor: pointer; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.form-submit {
  width: 100%; padding: 14px; border: none; border-radius: var(--r);
  background: var(--brand); color: #fff; font-size: 15px; font-weight: 600;
  cursor: pointer; transition: .2s; margin-top: 8px;
}
.form-submit:hover { background: var(--brand-dark); }
.form-note { font-size: 12px; color: var(--muted); margin-top: 12px; text-align: center; }
.success-msg {
  display: none; background: rgba(74,222,128,0.1); border: 1px solid rgba(74,222,128,0.3);
  border-radius: var(--r); padding: 16px; text-align: center; color: var(--success);
  font-size: 14px; font-weight: 500; margin-top: 12px;
}

/* ─── INFO PAGE ─── */
.info-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.info-card {
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: var(--r); padding: 24px;
}
.info-card h3 { font-size: 16px; font-weight: 600; margin-bottom: 12px; color: var(--text); }
.info-card p { font-size: 14px; color: var(--muted); line-height: 1.7; }
.rule-list { list-style: none; }
.rule-list li { font-size: 14px; color: var(--muted); padding: 8px 0; border-bottom: 1px solid var(--border2); display: flex; gap: 10px; }
.rule-list li:last-child { border-bottom: none; }
.rule-num { color: var(--brand); font-family: 'DM Mono', monospace; font-size: 13px; font-weight: 500; min-width: 24px; }

/* ─── LOGIN / PORTAL ─── */
.login-wrap {
  min-height: calc(100vh - 64px); display: flex; align-items: center;
  justify-content: center; padding: 40px 2rem;
}
.login-box {
  width: 100%; max-width: 420px;
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: 16px; padding: 40px;
}
.login-logo {
  text-align: center; margin-bottom: 28px;
}
.login-logo .title { font-family: 'Bebas Neue', sans-serif; font-size: 32px; color: var(--brand); letter-spacing: 3px; }
.login-logo .sub { font-size: 13px; color: var(--muted); margin-top: 4px; }
.login-role-select { display: flex; gap: 8px; margin-bottom: 24px; }
.role-btn {
  flex: 1; padding: 9px; border: 1px solid var(--border2); border-radius: 8px;
  background: transparent; color: var(--muted); font-size: 13px; font-weight: 500;
  cursor: pointer; transition: .2s;
}
.role-btn.active { border-color: var(--brand); color: var(--brand); background: var(--brand-glow); }
.login-form-group { margin-bottom: 16px; }
.login-label { display: block; font-size: 12px; font-weight: 500; color: var(--muted); text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 7px; }
.login-input {
  width: 100%; background: var(--bg2); border: 1px solid var(--border2);
  border-radius: 8px; color: var(--text); font-family: inherit;
  font-size: 14px; padding: 11px 14px; outline: none; transition: border-color .2s;
}
.login-input:focus { border-color: var(--brand); }
.login-btn {
  width: 100%; padding: 13px; border: none; border-radius: var(--r);
  background: var(--brand); color: #fff; font-size: 15px; font-weight: 600;
  cursor: pointer; margin-top: 8px; transition: .2s;
}
.login-btn:hover { background: var(--brand-dark); }
.login-error {
  display: none; background: rgba(248,113,113,0.1); border: 1px solid rgba(248,113,113,0.3);
  border-radius: 8px; padding: 12px; text-align: center;
  color: var(--danger); font-size: 13px; margin-top: 12px;
}

/* ─── ADMIN PANEL ─── */
.admin-layout { display: grid; grid-template-columns: 230px 1fr; min-height: calc(100vh - 64px); }
.admin-sidebar {
  background: var(--bg2); border-right: 1px solid var(--border2);
  padding: 24px 0;
}
.sidebar-label { font-size: 10px; text-transform: uppercase; letter-spacing: 1px; color: var(--muted); padding: 0 20px; margin-bottom: 8px; margin-top: 20px; }
.sidebar-label:first-child { margin-top: 0; }
.sidebar-item {
  display: flex; align-items: center; gap: 10px;
  padding: 10px 20px; cursor: pointer; font-size: 14px;
  color: var(--muted); transition: .15s; border-left: 2px solid transparent;
}
.sidebar-item:hover { color: var(--text); background: rgba(255,255,255,0.03); }
.sidebar-item.active { color: var(--brand); border-left-color: var(--brand); background: var(--brand-glow); }
.sidebar-icon { font-size: 18px; }
.admin-main { padding: 36px; overflow-y: auto; }
.admin-header { margin-bottom: 28px; }
.admin-header h2 { font-family: 'Bebas Neue', sans-serif; font-size: 36px; letter-spacing: 2px; }
.admin-header p { color: var(--muted); font-size: 14px; }
.admin-cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 14px; margin-bottom: 32px; }
.admin-card {
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: var(--r); padding: 18px 20px;
}
.admin-card .ac-num { font-family: 'Bebas Neue', sans-serif; font-size: 36px; color: var(--brand); }
.admin-card .ac-label { font-size: 12px; color: var(--muted); text-transform: uppercase; letter-spacing: 0.5px; margin-top: 2px; }
.data-table { width: 100%; border-collapse: collapse; }
.data-table th {
  text-align: left; font-size: 11px; text-transform: uppercase;
  letter-spacing: 0.5px; color: var(--muted); padding: 10px 14px;
  border-bottom: 1px solid var(--border2);
}
.data-table td { padding: 12px 14px; font-size: 14px; border-bottom: 1px solid rgba(255,255,255,0.04); }
.data-table tr:last-child td { border-bottom: none; }
.data-table tr:hover td { background: rgba(255,255,255,0.02); }
.badge {
  font-size: 11px; padding: 3px 9px; border-radius: 100px; font-weight: 600;
}
.badge-blue { background: rgba(8,97,250,0.15); color: var(--brand); }
.badge-green { background: rgba(74,222,128,0.15); color: var(--success); }
.badge-red { background: rgba(248,113,113,0.15); color: var(--danger); }
.badge-yellow { background: rgba(251,191,36,0.15); color: var(--warn); }
.badge-gray { background: rgba(255,255,255,0.08); color: var(--muted); }
.action-btn {
  background: transparent; border: 1px solid var(--border2); color: var(--muted);
  border-radius: 6px; padding: 5px 12px; font-size: 12px; cursor: pointer; transition: .15s;
}
.action-btn:hover { border-color: var(--brand); color: var(--brand); }
.action-btn.danger:hover { border-color: var(--danger); color: var(--danger); }
.modal-overlay {
  display: none; position: fixed; inset: 0; z-index: 200;
  background: rgba(0,0,0,0.6); align-items: center; justify-content: center;
}
.modal-overlay.open { display: flex; }
.modal-box {
  background: var(--surface); border: 1px solid var(--border2);
  border-radius: 16px; padding: 32px; width: 100%; max-width: 480px;
  max-height: 90vh; overflow-y: auto;
}
.modal-title { font-size: 20px; font-weight: 600; margin-bottom: 20px; }
.modal-close { float: right; background: none; border: none; color: var(--muted); font-size: 20px; cursor: pointer; margin-top: -4px; }
.table-wrap { background: var(--surface); border: 1px solid var(--border2); border-radius: var(--r); overflow: hidden; }
.table-header { padding: 16px 20px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--border2); }
.table-title { font-weight: 600; font-size: 15px; }

/* ─── DISCORD BTN ─── */
.discord-btn {
  display: inline-flex; align-items: center; gap: 8px;
  background: #5865F2; color: #fff; border: none; border-radius: var(--r);
  padding: 12px 22px; font-size: 14px; font-weight: 600; cursor: pointer;
  text-decoration: none; transition: .2s;
}
.discord-btn:hover { background: #4752c4; }
.discord-logo { width: 20px; height: 20px; fill: currentColor; }

/* ─── FOOTER ─── */
footer {
  background: var(--bg2); border-top: 1px solid var(--border2);
  padding: 40px 2rem; text-align: center;
}
footer .f-logo { font-family: 'Bebas Neue', sans-serif; font-size: 24px; color: var(--brand); letter-spacing: 2px; margin-bottom: 8px; }
footer p { color: var(--muted); font-size: 13px; }

/* ─── MOBILE ─── */
@media (max-width: 768px) {
  .nav-links { display: none; }
  .hamburger { display: flex; }
  .nav-links.open { display: flex; flex-direction: column; position: fixed; top: 64px; left: 0; right: 0; background: var(--bg2); padding: 20px; gap: 16px; border-bottom: 1px solid var(--border2); }
  .form-row { grid-template-columns: 1fr; }
  .info-grid { grid-template-columns: 1fr; }
  .admin-layout { grid-template-columns: 1fr; }
  .admin-sidebar { display: none; }
  .form-container { padding: 24px 20px; }
  .login-box { padding: 28px 24px; }
}

/* ─── ANIMATIONS ─── */
@keyframes fadeUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
.fade-up { animation: fadeUp .5s ease forwards; }

/* ─── CHAT ─── */
.chat-msg { display: flex; flex-direction: column; gap: 3px; }
.chat-name { font-size: 13px; font-weight: 600; color: var(--text); }
.chat-time { font-size: 11px; color: var(--muted); margin-left: 8px; }
.chat-text { font-size: 14px; color: var(--muted); line-height: 1.6; background: var(--surface); border-radius: 0 8px 8px 8px; padding: 8px 12px; display: inline-block; max-width: 90%; }

/* ─── GALLERY ─── */
.gallery-item { position: relative; border-radius: var(--r); overflow: hidden; border: 1px solid var(--border2); aspect-ratio: 16/9; background: var(--surface); cursor: pointer; transition: border-color .2s; }
.gallery-item:hover { border-color: var(--brand); }
.gallery-item img, .gallery-item video { width: 100%; height: 100%; object-fit: cover; }
.gallery-badge { position: absolute; top: 8px; right: 8px; font-size: 10px; padding: 2px 8px; border-radius: 100px; font-weight: 600; }
.gallery-label { position: absolute; bottom: 0; left: 0; right: 0; padding: 6px 10px; background: rgba(6,11,20,0.85); font-size: 12px; color: var(--text); }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">SYDNEY<span>RP</span></div>
  <div class="nav-links" id="navLinks">
    <a href="#" onclick="showPage('home')">Home</a>
    <a href="#" onclick="showPage('status')">Server Status</a>
    <a href="#" onclick="showPage('departments')">Departments</a>
    <a href="#" onclick="showPage('apply')">Apply</a>
    <a href="#" onclick="showPage('info')">Info</a>
  </div>
  <div style="display:flex;gap:10px;align-items:center">
    <button class="nav-btn" onclick="showPage('login')">Staff Portal</button>
    <div class="hamburger" onclick="toggleMenu()" id="hamburger">
      <span></span><span></span><span></span>
    </div>
  </div>
</nav>

<!-- ═══════════ HOME ═══════════ -->
<div id="home" class="page active">
  <section style="position:relative;overflow:hidden;display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:100vh;text-align:center;padding:80px 2rem 60px">
    <div class="hero-grid"></div>
    <div class="hero-glow"></div>
    <div style="position:relative;z-index:1">
      <div class="hero-badge">
        <div class="badge-dot"></div>
        Servers Online — Join Now
      </div>
      <h1 class="hero" style="font-family:'Bebas Neue',sans-serif;font-size:clamp(56px,10vw,120px);line-height:0.9;letter-spacing:4px;margin-bottom:20px">
        <span style="color:#fff">SYDNEY</span><br>
        <span style="color:var(--brand)">ROLEPLAY</span>
      </h1>
      <p style="font-size:18px;color:var(--muted);max-width:520px;margin:0 auto 36px;line-height:1.7">
        Sydney's premier ERLC roleplay community. Experience realistic Australian emergency services, law enforcement, and civilian roleplay on Roblox.
      </p>
      <div style="display:flex;gap:12px;justify-content:center;flex-wrap:wrap">
        <button class="btn-primary" onclick="showPage('apply')">Apply Now</button>
        <a class="discord-btn" href="https://discord.gg/sydneyrp" target="_blank">
          <svg class="discord-logo" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
          Join Discord
        </a>
      </div>
      <div class="stats-strip">
        <div class="stat-item"><div class="stat-num" id="memberCount">2,841</div><div class="stat-label">Members</div></div>
        <div class="stat-item"><div class="stat-num">3</div><div class="stat-label">Active Servers</div></div>
        <div class="stat-item"><div class="stat-num">12</div><div class="stat-label">Departments</div></div>
        <div class="stat-item"><div class="stat-num">24/7</div><div class="stat-label">Uptime</div></div>
      </div>
    </div>
  </section>

  <!-- QUICK LINKS -->
  <section class="section">
    <h2 class="section-title">QUICK <span class="blue">ACCESS</span></h2>
    <p class="section-sub">Everything you need in one place.</p>
    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:14px">
      <div class="dept-card" onclick="showPage('status')">
        <div class="dept-icon">📡</div>
        <div class="dept-name">Server Status</div>
        <div class="dept-desc">Live ERLC server uptime and player counts.</div>
        <div class="dept-link">Check status →</div>
      </div>
      <div class="dept-card" onclick="showPage('departments')">
        <div class="dept-icon">🏛️</div>
        <div class="dept-name">Departments</div>
        <div class="dept-desc">Browse all community departments and join a team.</div>
        <div class="dept-link">View departments →</div>
      </div>
      <div class="dept-card" onclick="showPage('apply')">
        <div class="dept-icon">📋</div>
        <div class="dept-name">Applications</div>
        <div class="dept-desc">Apply for staff, departments, or appeal a ban.</div>
        <div class="dept-link">Apply now →</div>
      </div>
      <div class="dept-card" onclick="showPage('info')">
        <div class="dept-icon">📖</div>
        <div class="dept-name">Community Info</div>
        <div class="dept-desc">Rules, guidelines, and general information.</div>
        <div class="dept-link">Read more →</div>
      </div>
    </div>
  </section>
  <hr class="divider">
  <footer>
    <div class="f-logo">SYDNEY RP</div>
    <p>© 2025 Sydney RP — An ERLC Roblox Roleplay Community</p>
  </footer>
</div>

<!-- ═══════════ SERVER STATUS ═══════════ -->
<div id="status" class="page">
  <section class="section">
    <h2 class="section-title">SERVER <span class="blue">STATUS</span></h2>
    <p class="section-sub">Live ERLC server uptime and information. Last updated: <span id="lastUpdated">just now</span></p>
    <div class="status-grid" id="serverGrid">
      <!-- Populated by JS -->
    </div>
    <div style="margin-top:32px;display:flex;gap:12px;flex-wrap:wrap;align-items:center">
      <button class="btn-primary" onclick="refreshStatus()">↻ Refresh Status</button>
      <a class="discord-btn" href="https://discord.gg/sydneyrp" target="_blank">
        <svg class="discord-logo" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
        Server Notifications
      </a>
    </div>
  </section>
  <hr class="divider">
  <footer><div class="f-logo">SYDNEY RP</div><p>© 2025 Sydney RP</p></footer>
</div>

<!-- ═══════════ DEPARTMENTS ═══════════ -->
<div id="departments" class="page">
  <section class="section">
    <h2 class="section-title">COMMUNITY <span class="blue">DEPARTMENTS</span></h2>
    <p class="section-sub">Join a department to participate in structured Sydney RP roleplay.</p>
    <div class="dept-grid">
      <div class="dept-card">
        <div class="dept-icon">🚔</div>
        <div class="dept-name">NSW Police Force</div>
        <div class="dept-desc">Patrol the streets of Sydney, respond to incidents, and enforce the law in our main law enforcement department.</div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center">
          <button class="btn-primary" style="padding:8px 16px;font-size:13px" onclick="showPage('apply');setTab('dept')">Apply Now</button>
          <a class="discord-btn" style="padding:8px 14px;font-size:13px" href="https://discord.gg/sydneyrp" target="_blank">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
            Discord
          </a>
        </div>
      </div>
      <div class="dept-card">
        <div class="dept-icon">🚑</div>
        <div class="dept-name">NSW Ambulance</div>
        <div class="dept-desc">Save lives as a paramedic, respond to medical emergencies, and keep the community healthy.</div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center">
          <button class="btn-primary" style="padding:8px 16px;font-size:13px" onclick="showPage('apply');setTab('dept')">Apply Now</button>
          <a class="discord-btn" style="padding:8px 14px;font-size:13px" href="https://discord.gg/sydneyrp" target="_blank">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
            Discord
          </a>
        </div>
      </div>
      <div class="dept-card">
        <div class="dept-icon">🚒</div>
        <div class="dept-name">Fire & Rescue NSW</div>
        <div class="dept-desc">Battle blazes, perform rescues, and keep Sydney safe as a firefighter in our fire department.</div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center">
          <button class="btn-primary" style="padding:8px 16px;font-size:13px" onclick="showPage('apply');setTab('dept')">Apply Now</button>
          <a class="discord-btn" style="padding:8px 14px;font-size:13px" href="https://discord.gg/sydneyrp" target="_blank">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
            Discord
          </a>
        </div>
      </div>
      <div class="dept-card">
        <div class="dept-icon">⚖️</div>
        <div class="dept-name">Department of Justice</div>
        <div class="dept-desc">Preside over court cases, serve as a judge or lawyer, and maintain the legal system in Sydney RP.</div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center">
          <button class="btn-primary" style="padding:8px 16px;font-size:13px" onclick="showPage('apply');setTab('dept')">Apply Now</button>
          <a class="discord-btn" style="padding:8px 14px;font-size:13px" href="https://discord.gg/sydneyrp" target="_blank">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.030z"/></svg>
            Discord
          </a>
        </div>
      </div>
      <div class="dept-card">
        <div class="dept-icon">🚢</div>
        <div class="dept-name">NSW Transport</div>
        <div class="dept-desc">Operate public transport, manage logistics, and keep Sydney's infrastructure running smoothly.</div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center">
          <button class="btn-primary" style="padding:8px 16px;font-size:13px" onclick="showPage('apply');setTab('dept')">Apply Now</button>
          <a class="discord-btn" style="padding:8px 14px;font-size:13px" href="https://discord.gg/sydneyrp" target="_blank">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
            Discord
          </a>
        </div>
      </div>
      <div class="dept-card">
        <div class="dept-icon">🏙️</div>
        <div class="dept-name">Government & Media</div>
        <div class="dept-desc">Run the city government, manage public relations, or work in Sydney RP's media and communications team.</div>
        <div style="display:flex;gap:10px;flex-wrap:wrap;align-items:center">
          <button class="btn-primary" style="padding:8px 16px;font-size:13px" onclick="showPage('apply');setTab('dept')">Apply Now</button>
          <a class="discord-btn" style="padding:8px 14px;font-size:13px" href="https://discord.gg/sydneyrp" target="_blank">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
            Discord
          </a>
        </div>
      </div>
    </div>
  </section>
  <hr class="divider">
  <footer><div class="f-logo">SYDNEY RP</div><p>© 2025 Sydney RP</p></footer>
</div>

<!-- ═══════════ APPLY ═══════════ -->
<div id="apply" class="page">
  <section class="section">
    <h2 class="section-title">APPLICATIONS <span class="blue">& APPEALS</span></h2>
    <p class="section-sub">All submissions are reviewed within 48–72 hours.</p>
    <div class="form-container">
      <div class="form-tabs">
        <div class="ftab active" onclick="setTab('staff')">Staff Application</div>
        <div class="ftab" onclick="setTab('dept')">Department App</div>
        <div class="ftab" onclick="setTab('appeal')">Ban Appeal</div>
      </div>

      <!-- STAFF APPLICATION -->
      <div class="form-section active" id="form-staff">
        <div class="form-group">
          <label class="form-label">Roblox Username</label>
          <input class="form-input" type="text" placeholder="Your Roblox username">
        </div>
        <div class="form-group">
          <label class="form-label">Discord Username</label>
          <input class="form-input" type="text" placeholder="username#0000 or username">
        </div>
        <div class="form-row">
          <div class="form-group">
            <label class="form-label">Age</label>
            <input class="form-input" type="number" placeholder="Your age" min="13">
          </div>
          <div class="form-group">
            <label class="form-label">Timezone</label>
            <select class="form-select">
              <option value="">Select timezone</option>
              <option>AEST (UTC+10)</option>
              <option>AEDT (UTC+11)</option>
              <option>AWST (UTC+8)</option>
              <option>NZST (UTC+12)</option>
              <option>Other</option>
            </select>
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Position Applying For</label>
          <select class="form-select">
            <option value="">Select a role</option>
            <option>Moderator</option>
            <option>Administrator</option>
            <option>Event Host</option>
            <option>Support Staff</option>
            <option>Media Team</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Previous Experience</label>
          <textarea class="form-textarea" placeholder="Describe any previous staff/moderation experience in other communities..."></textarea>
        </div>
        <div class="form-group">
          <label class="form-label">Why do you want to be staff?</label>
          <textarea class="form-textarea" placeholder="Tell us why you want to join the Sydney RP staff team and what you can bring to the community..."></textarea>
        </div>
        <div class="form-group">
          <label class="form-label">How many hours per week can you dedicate?</label>
          <select class="form-select">
            <option value="">Select hours</option>
            <option>Less than 5 hours</option>
            <option>5–10 hours</option>
            <option>10–20 hours</option>
            <option>20+ hours</option>
          </select>
        </div>
        <button class="form-submit" onclick="submitForm('staff')">Submit Staff Application</button>
        <div class="success-msg" id="success-staff">✓ Application submitted! We'll review it within 48–72 hours and contact you via Discord.</div>
        <p class="form-note">By submitting, you agree to our community guidelines and terms of service.</p>
      </div>

      <!-- DEPT APPLICATION -->
      <div class="form-section" id="form-dept">
        <div class="form-group">
          <label class="form-label">Roblox Username</label>
          <input class="form-input" type="text" placeholder="Your Roblox username">
        </div>
        <div class="form-group">
          <label class="form-label">Discord Username</label>
          <input class="form-input" type="text" placeholder="username#0000 or username">
        </div>
        <div class="form-group">
          <label class="form-label">Department</label>
          <select class="form-select">
            <option value="">Select department</option>
            <option>NSW Police Force</option>
            <option>NSW Ambulance</option>
            <option>Fire & Rescue NSW</option>
            <option>Department of Justice</option>
            <option>NSW Transport</option>
            <option>Government & Media</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">ERLC Experience Level</label>
          <select class="form-select">
            <option value="">Select experience</option>
            <option>New to ERLC</option>
            <option>Some experience (< 6 months)</option>
            <option>Experienced (6–12 months)</option>
            <option>Veteran (1+ year)</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Why do you want to join this department?</label>
          <textarea class="form-textarea" placeholder="Explain your interest in this department and what you hope to contribute..."></textarea>
        </div>
        <div class="form-group">
          <label class="form-label">Any previous department experience?</label>
          <textarea class="form-textarea" placeholder="List any departments you've previously been in, within Sydney RP or other communities..."></textarea>
        </div>
        <button class="form-submit" onclick="submitForm('dept')">Submit Department Application</button>
        <div class="success-msg" id="success-dept">✓ Application submitted! Our department heads will review your application and be in touch.</div>
        <p class="form-note">Department applications are reviewed by the relevant department leadership.</p>
      </div>

      <!-- BAN APPEAL -->
      <div class="form-section" id="form-appeal">
        <div style="background:rgba(251,191,36,0.08);border:1px solid rgba(251,191,36,0.25);border-radius:8px;padding:14px 16px;margin-bottom:20px;font-size:13px;color:var(--warn)">
          ⚠️ Submitting false information in a ban appeal may result in a permanent ban. Be honest and accurate.
        </div>
        <div class="form-group">
          <label class="form-label">Roblox Username</label>
          <input class="form-input" type="text" placeholder="Your Roblox username">
        </div>
        <div class="form-group">
          <label class="form-label">Discord Username</label>
          <input class="form-input" type="text" placeholder="username#0000 or username">
        </div>
        <div class="form-row">
          <div class="form-group">
            <label class="form-label">Ban Type</label>
            <select class="form-select">
              <option value="">Select type</option>
              <option>Discord Ban</option>
              <option>ERLC Server Ban</option>
              <option>Both</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Ban Date (approx.)</label>
            <input class="form-input" type="date">
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Reason Given for Ban</label>
          <input class="form-input" type="text" placeholder="What reason were you given, if any?">
        </div>
        <div class="form-group">
          <label class="form-label">Why were you banned? (Your account)</label>
          <textarea class="form-textarea" placeholder="Explain in your own words what happened and why you were banned. Be honest."></textarea>
        </div>
        <div class="form-group">
          <label class="form-label">Why should your ban be lifted?</label>
          <textarea class="form-textarea" placeholder="Explain why you believe your ban should be lifted and how you've changed or why it was unjust..."></textarea>
        </div>
        <div class="form-group">
          <label class="form-label">Any supporting evidence? (Screenshots, links)</label>
          <input class="form-input" type="text" placeholder="Paste any image/screenshot URLs here">
        </div>
        <button class="form-submit" onclick="submitForm('appeal')">Submit Ban Appeal</button>
        <div class="success-msg" id="success-appeal">✓ Appeal submitted! Our moderation team will review it within 72 hours.</div>
        <p class="form-note">Ban appeals are handled by senior moderation staff and are final unless new evidence emerges.</p>
      </div>
    </div>
  </section>
  <hr class="divider">
  <footer><div class="f-logo">SYDNEY RP</div><p>© 2025 Sydney RP</p></footer>
</div>

<!-- ═══════════ INFO ═══════════ -->
<div id="info" class="page">
  <section class="section">
    <h2 class="section-title">COMMUNITY <span class="blue">INFO</span></h2>
    <p class="section-sub">Everything you need to know about Sydney RP.</p>
    <div class="info-grid" style="margin-bottom:24px">
      <div class="info-card">
        <h3>🗺️ About Sydney RP</h3>
        <p>Sydney RP is an Australian-themed ERLC (Emergency Response: Liberty County) Roblox roleplay community. We aim to provide a realistic, fun, and structured environment for players who love Australian emergency services and law enforcement roleplay.</p>
      </div>
      <div class="info-card">
        <h3>🎮 The Game</h3>
        <p>We operate private ERLC servers on Roblox. ERLC is a popular emergency services roleplay game where players take on roles as police, paramedics, firefighters, and civilians in a realistic open-world environment.</p>
      </div>
      <div class="info-card">
        <h3>💬 Discord Server</h3>
        <p>Our main hub is on Discord. All department communications, announcements, applications, and community events are coordinated there. Join via the button below to stay connected.</p>
        <div style="margin-top:14px">
          <a class="discord-btn" href="https://discord.gg/sydneyrp" target="_blank" style="font-size:13px;padding:9px 16px">
            <svg class="discord-logo" style="width:16px;height:16px" viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.032.05a19.9 19.9 0 0 0 5.993 3.03.077.077 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03z"/></svg>
            Join Discord
          </a>
        </div>
      </div>
      <div class="info-card">
        <h3>📅 Events</h3>
        <p>We run regular community events including hosted patrol sessions, department training, roleplay scenarios, and community meetings. Check the Discord events channel for the latest schedule.</p>
      </div>
    </div>
    <div class="info-card" style="margin-bottom:24px">
      <h3>📜 Community Rules</h3>
      <ul class="rule-list">
        <li><span class="rule-num">01</span>Respect all community members — harassment, discrimination, and toxic behaviour will not be tolerated.</li>
        <li><span class="rule-num">02</span>No metagaming — do not use out-of-game information in roleplay situations.</li>
        <li><span class="rule-num">03</span>No RDM (Random Deathmatch) — you must have valid roleplay reasons for any aggressive actions.</li>
        <li><span class="rule-num">04</span>Follow chain of command within your department at all times.</li>
        <li><span class="rule-num">05</span>No exploiting, hacking, or using unauthorised scripts in ERLC servers.</li>
        <li><span class="rule-num">06</span>All communications must remain SFW and appropriate for all ages.</li>
        <li><span class="rule-num">07</span>Staff decisions are final — if you disagree, use the proper appeal process.</li>
        <li><span class="rule-num">08</span>Impersonating staff or department leaders is a bannable offence.</li>
        <li><span class="rule-num">09</span>Advertising other communities without permission is not allowed.</li>
        <li><span class="rule-num">10</span>Have fun and contribute positively to the Sydney RP community!</li>
      </ul>
    </div>
    <div class="info-card">
      <h3>🏆 Staff Hierarchy</h3>
      <div style="display:flex;flex-direction:column;gap:10px;margin-top:8px">
        <div style="display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--bg2);border-radius:8px;border:1px solid rgba(8,97,250,0.3)">
          <span style="font-size:20px">👑</span>
          <div><div style="font-weight:600;font-size:14px;color:var(--brand)">Founder</div><div style="font-size:12px;color:var(--muted)">Full server ownership and control</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--bg2);border-radius:8px">
          <span style="font-size:20px">⭐</span>
          <div><div style="font-weight:600;font-size:14px">Senior Administrator</div><div style="font-size:12px;color:var(--muted)">Oversees staff team and major decisions</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--bg2);border-radius:8px">
          <span style="font-size:20px">🛡️</span>
          <div><div style="font-weight:600;font-size:14px">Administrator</div><div style="font-size:12px;color:var(--muted)">Manages moderation and community events</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--bg2);border-radius:8px">
          <span style="font-size:20px">🔧</span>
          <div><div style="font-weight:600;font-size:14px">Moderator</div><div style="font-size:12px;color:var(--muted)">Enforces rules and handles reports</div></div>
        </div>
        <div style="display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--bg2);border-radius:8px">
          <span style="font-size:20px">🎗️</span>
          <div><div style="font-weight:600;font-size:14px">Support Staff</div><div style="font-size:12px;color:var(--muted)">Assists members with questions and issues</div></div>
        </div>
      </div>
    </div>
  </section>
  <hr class="divider">
  <footer><div class="f-logo">SYDNEY RP</div><p>© 2025 Sydney RP</p></footer>
</div>

<!-- ═══════════ LOGIN ═══════════ -->
<div id="login" class="page">
  <div class="login-wrap" id="loginWrap">
    <div class="login-box">
      <div class="login-logo">
        <div class="title">SYDNEY RP</div>
        <div class="sub">Staff Portal Login</div>
      </div>
      <div class="login-form-group">
        <label class="login-label">Username</label>
        <input class="login-input" type="text" id="loginUser" placeholder="Enter username">
      </div>
      <div class="login-form-group">
        <label class="login-label">Password</label>
        <input class="login-input" type="password" id="loginPass" placeholder="Enter password" onkeydown="if(event.key==='Enter')doLogin()">
      </div>
      <button class="login-btn" onclick="doLogin()">Login</button>
      <div class="login-error" id="loginError">Incorrect username or password.</div>
      <p style="font-size:12px;color:var(--muted);text-align:center;margin-top:16px">
        Staff accounts are created by the Owner. Contact leadership if you need access.
      </p>
    </div>
  </div>
</div>

<!-- ═══════════ ADMIN PANEL (MASTER) ═══════════ -->
<div id="adminPanel" class="page">
  <div class="admin-layout">
    <div class="admin-sidebar">
      <div class="sidebar-label">Overview</div>
      <div class="sidebar-item active" onclick="adminTab('dashboard',this)">
        <span class="sidebar-icon">📊</span> Dashboard
      </div>
      <div class="sidebar-label">Management</div>
      <div class="sidebar-item" onclick="adminTab('accounts',this)">
        <span class="sidebar-icon">👥</span> Staff Accounts
      </div>
      <div class="sidebar-item" onclick="adminTab('applications',this)">
        <span class="sidebar-icon">📋</span> Applications
      </div>
      <div class="sidebar-item" onclick="adminTab('appeals',this)">
        <span class="sidebar-icon">⚖️</span> Ban Appeals
      </div>
      <div class="sidebar-label">Server</div>
      <div class="sidebar-item" onclick="adminTab('servers',this)">
        <span class="sidebar-icon">🖥️</span> Server Status
      </div>
      <div class="sidebar-item" onclick="adminTab('announcements',this)">
        <span class="sidebar-icon">📢</span> Announcements
      </div>
      <div class="sidebar-label">Departments</div>
      <div class="sidebar-item" onclick="adminTab('media',this)">
        <span class="sidebar-icon">🎬</span> Media Team
      </div>
      <div class="sidebar-item" onclick="adminTab('roster',this)">
        <span class="sidebar-icon">📅</span> Staff Roster
      </div>
      <div class="sidebar-item" onclick="adminTab('messages',this)">
        <span class="sidebar-icon">✉️</span> Messages
      </div>
      <div class="sidebar-label">Account</div>
      <div class="sidebar-item" onclick="logout()">
        <span class="sidebar-icon">🚪</span> Log Out
      </div>
    </div>
    <div class="admin-main">

      <!-- DASHBOARD -->
      <div id="tab-dashboard">
        <div class="admin-header">
          <h2>DASHBOARD</h2>
          <p>Welcome back, Founder. Here's an overview.</p>
        </div>
        <div class="admin-cards">
          <div class="admin-card"><div class="ac-num">8</div><div class="ac-label">Staff Members</div></div>
          <div class="admin-card"><div class="ac-num">3</div><div class="ac-label">Pending Apps</div></div>
          <div class="admin-card"><div class="ac-num">1</div><div class="ac-label">Open Appeals</div></div>
          <div class="admin-card"><div class="ac-num">3</div><div class="ac-label">Servers Online</div></div>
        </div>
        <div class="table-wrap">
          <div class="table-header">
            <div class="table-title">Recent Activity</div>
          </div>
          <table class="data-table">
            <thead><tr><th>Action</th><th>User</th><th>Time</th></tr></thead>
            <tbody>
              <tr><td>Staff application submitted</td><td>xSydney_Cop</td><td style="color:var(--muted);font-size:13px">2h ago</td></tr>
              <tr><td>Ban appeal opened</td><td>robloxguy123</td><td style="color:var(--muted);font-size:13px">5h ago</td></tr>
              <tr><td>Department app (Police)</td><td>AussiePatrol</td><td style="color:var(--muted);font-size:13px">1d ago</td></tr>
              <tr><td>Staff login</td><td>Mod_Jake</td><td style="color:var(--muted);font-size:13px">1d ago</td></tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- ACCOUNTS -->
      <div id="tab-accounts" style="display:none">
        <div class="admin-header">
          <h2>STAFF ACCOUNTS</h2>
          <p>Manage staff logins and permissions.</p>
        </div>
        <div class="table-wrap">
          <div class="table-header">
            <div class="table-title">Staff Members</div>
            <button class="btn-primary" style="font-size:13px;padding:8px 16px" onclick="document.getElementById('newAccountModal').classList.add('open')">+ New Account</button>
          </div>
          <table class="data-table">
            <thead><tr><th>Username</th><th>Role</th><th>Status</th><th>Actions</th></tr></thead>
            <tbody id="accountsTable">
              <tr><td><strong>Founder</strong></td><td><span class="badge badge-blue">Founder</span></td><td><span class="badge badge-green">Active</span></td><td><button class="action-btn">Edit</button></td></tr>
              <tr><td>SeniorAdmin_Jake</td><td><span class="badge badge-blue">Sr. Admin</span></td><td><span class="badge badge-green">Active</span></td><td><button class="action-btn">Edit</button> <button class="action-btn danger" onclick="removeAccount(this)">Remove</button></td></tr>
              <tr><td>Admin_Sarah</td><td><span class="badge badge-gray">Admin</span></td><td><span class="badge badge-green">Active</span></td><td><button class="action-btn">Edit</button> <button class="action-btn danger" onclick="removeAccount(this)">Remove</button></td></tr>
              <tr><td>Mod_Tom</td><td><span class="badge badge-gray">Moderator</span></td><td><span class="badge badge-yellow">Away</span></td><td><button class="action-btn">Edit</button> <button class="action-btn danger" onclick="removeAccount(this)">Remove</button></td></tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- APPLICATIONS -->
      <div id="tab-applications" style="display:none">
        <div class="admin-header">
          <h2>APPLICATIONS</h2>
          <p>Review pending staff and department applications.</p>
        </div>
        <div class="table-wrap">
          <div class="table-header"><div class="table-title">Pending Applications</div></div>
          <table class="data-table">
            <thead><tr><th>Applicant</th><th>Type</th><th>Position</th><th>Submitted</th><th>Actions</th></tr></thead>
            <tbody>
              <tr>
                <td>xSydney_Cop</td>
                <td><span class="badge badge-blue">Staff</span></td>
                <td>Moderator</td>
                <td style="color:var(--muted);font-size:13px">2h ago</td>
                <td>
                  <button class="action-btn" onclick="this.closest('tr').cells[3].textContent='Accepted';this.closest('tr').cells[3].style.color='var(--success)';this.closest('tr').cells[4].innerHTML='<span class=\'badge badge-green\'>Accepted</span>'">Accept</button>
                  <button class="action-btn danger" onclick="this.closest('tr').cells[4].innerHTML='<span class=\'badge badge-red\'>Denied</span>'">Deny</button>
                </td>
              </tr>
              <tr>
                <td>AussiePatrol</td>
                <td><span class="badge badge-gray">Department</span></td>
                <td>NSW Police</td>
                <td style="color:var(--muted);font-size:13px">1d ago</td>
                <td>
                  <button class="action-btn" onclick="this.closest('tr').cells[4].innerHTML='<span class=\'badge badge-green\'>Accepted</span>'">Accept</button>
                  <button class="action-btn danger" onclick="this.closest('tr').cells[4].innerHTML='<span class=\'badge badge-red\'>Denied</span>'">Deny</button>
                </td>
              </tr>
              <tr>
                <td>FireFighter99</td>
                <td><span class="badge badge-gray">Department</span></td>
                <td>Fire & Rescue</td>
                <td style="color:var(--muted);font-size:13px">2d ago</td>
                <td>
                  <button class="action-btn" onclick="this.closest('tr').cells[4].innerHTML='<span class=\'badge badge-green\'>Accepted</span>'">Accept</button>
                  <button class="action-btn danger" onclick="this.closest('tr').cells[4].innerHTML='<span class=\'badge badge-red\'>Denied</span>'">Deny</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- APPEALS -->
      <div id="tab-appeals" style="display:none">
        <div class="admin-header">
          <h2>BAN APPEALS</h2>
          <p>Review and action ban appeals from community members.</p>
        </div>
        <div class="table-wrap">
          <div class="table-header"><div class="table-title">Open Appeals</div></div>
          <table class="data-table">
            <thead><tr><th>Username</th><th>Ban Type</th><th>Submitted</th><th>Status</th><th>Actions</th></tr></thead>
            <tbody>
              <tr>
                <td>robloxguy123</td>
                <td>Discord Ban</td>
                <td style="color:var(--muted);font-size:13px">5h ago</td>
                <td><span class="badge badge-yellow">Pending</span></td>
                <td>
                  <button class="action-btn" onclick="this.closest('tr').cells[3].innerHTML='<span class=\'badge badge-green\'>Lifted</span>'">Lift Ban</button>
                  <button class="action-btn danger" onclick="this.closest('tr').cells[3].innerHTML='<span class=\'badge badge-red\'>Denied</span>'">Deny</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <!-- SERVERS -->
      <div id="tab-servers" style="display:none">
        <div class="admin-header">
          <h2>SERVER STATUS</h2>
          <p>Monitor ERLC server uptime and manage server settings.</p>
        </div>
        <div class="status-grid" id="adminServerGrid"></div>
      </div>

      <!-- ANNOUNCEMENTS -->
      <div id="tab-announcements" style="display:none">
        <div class="admin-header">
          <h2>ANNOUNCEMENTS</h2>
          <p>Post a new community announcement.</p>
        </div>
        <div class="form-container" style="max-width:100%">
          <div class="form-group">
            <label class="form-label">Announcement Title</label>
            <input class="form-input" type="text" placeholder="e.g. Server Maintenance Tonight">
          </div>
          <div class="form-group">
            <label class="form-label">Target Channel</label>
            <select class="form-select">
              <option>📢 #announcements</option>
              <option>📋 #department-news</option>
              <option>🎮 #server-updates</option>
              <option>⚖️ #moderation-notices</option>
            </select>
          </div>
          <div class="form-group">
            <label class="form-label">Message</label>
            <textarea class="form-textarea" style="min-height:160px" placeholder="Write your announcement here..."></textarea>
          </div>
          <div style="display:flex;gap:10px;flex-wrap:wrap">
            <button class="form-submit" style="max-width:200px" onclick="this.textContent='✓ Posted!';this.style.background='var(--success)'">Post Announcement</button>
            <button class="btn-outline" style="padding:14px 24px;font-size:15px">Preview</button>
          </div>
        </div>
      </div>

      <!-- MEDIA TEAM -->
      <div id="tab-media" style="display:none">
        <div class="admin-header">
          <h2>MEDIA <span style="color:var(--brand)">TEAM</span></h2>
          <p>Manage media assets, templates, team chat and Discord channels.</p>
        </div>

        <!-- Media sub-tabs -->
        <div style="display:flex;gap:4px;margin-bottom:28px;background:var(--bg2);border-radius:10px;padding:4px;max-width:560px">
          <div class="ftab active" id="mtab-channels" onclick="mediaTab('channels')">📡 Channels</div>
          <div class="ftab" id="mtab-templates" onclick="mediaTab('templates')">📄 Templates</div>
          <div class="ftab" id="mtab-chat" onclick="mediaTab('chat')">💬 Team Chat</div>
          <div class="ftab" id="mtab-gallery" onclick="mediaTab('gallery')">🖼️ Media Gallery</div>
        </div>

        <!-- CHANNELS -->
        <div id="msec-channels">
          <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px">
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none">
              <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                <span style="font-size:18px;color:var(--muted)">#</span>
                <span style="font-weight:600;font-size:15px">media-announcements</span>
                <span class="badge badge-blue" style="margin-left:auto">Announce</span>
              </div>
              <div style="font-size:13px;color:var(--muted)">Official media team announcements and updates posted here.</div>
              <div class="dept-link" style="margin-top:10px">Open in Discord →</div>
            </a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none">
              <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                <span style="font-size:18px;color:var(--muted)">#</span>
                <span style="font-weight:600;font-size:15px">media-submissions</span>
                <span class="badge badge-green" style="margin-left:auto">Submit</span>
              </div>
              <div style="font-size:13px;color:var(--muted)">Submit screenshots, clips, and graphics for review and publishing.</div>
              <div class="dept-link" style="margin-top:10px">Open in Discord →</div>
            </a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none">
              <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                <span style="font-size:18px;color:var(--muted)">#</span>
                <span style="font-weight:600;font-size:15px">media-general</span>
                <span class="badge badge-gray" style="margin-left:auto">Chat</span>
              </div>
              <div style="font-size:13px;color:var(--muted)">General media team discussion, ideas, and brainstorming.</div>
              <div class="dept-link" style="margin-top:10px">Open in Discord →</div>
            </a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none">
              <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                <span style="font-size:18px;color:var(--muted)">#</span>
                <span style="font-weight:600;font-size:15px">published-content</span>
                <span class="badge badge-yellow" style="margin-left:auto">Archive</span>
              </div>
              <div style="font-size:13px;color:var(--muted)">All approved and published media content is archived here.</div>
              <div class="dept-link" style="margin-top:10px">Open in Discord →</div>
            </a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none">
              <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                <span style="font-size:18px;color:var(--muted)">#</span>
                <span style="font-weight:600;font-size:15px">media-staff-only</span>
                <span class="badge badge-red" style="margin-left:auto">Restricted</span>
              </div>
              <div style="font-size:13px;color:var(--muted)">Private channel for media team leadership and internal discussions.</div>
              <div class="dept-link" style="margin-top:10px">Open in Discord →</div>
            </a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none">
              <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
                <span style="font-size:18px;color:var(--muted)">#</span>
                <span style="font-weight:600;font-size:15px">video-editing</span>
                <span class="badge badge-gray" style="margin-left:auto">Video</span>
              </div>
              <div style="font-size:13px;color:var(--muted)">Coordination channel for video editors and clip requests.</div>
              <div class="dept-link" style="margin-top:10px">Open in Discord →</div>
            </a>
          </div>
        </div>

        <!-- TEMPLATES -->
        <div id="msec-templates" style="display:none">
          <div style="display:flex;gap:8px;margin-bottom:20px;flex-wrap:wrap">
            <button class="ftab active" id="tmptab-text" onclick="tmplTab('text')" style="flex:unset;padding:8px 16px">Text Templates</button>
            <button class="ftab" id="tmptab-image" onclick="tmplTab('image')" style="flex:unset;padding:8px 16px">Image Templates</button>
          </div>

          <!-- Text templates -->
          <div id="tmpl-text">
            <div style="display:flex;flex-direction:column;gap:14px">

              <div class="table-wrap">
                <div class="table-header">
                  <div class="table-title">📢 Server Announcement</div>
                  <button class="action-btn" onclick="copyTemplate('tmpl1')">Copy</button>
                </div>
                <pre id="tmpl1" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">@everyone

📣 **[ANNOUNCEMENT TITLE]**

[Write your announcement here. Keep it clear, concise, and professional.]

━━━━━━━━━━━━━━━━━━━━━━
🎮 **Sydney RP** | erlc.sydneyrp.com
📅 Posted by: [Your Name] | [Date]</pre>
              </div>

              <div class="table-wrap">
                <div class="table-header">
                  <div class="table-title">🎉 Event Announcement</div>
                  <button class="action-btn" onclick="copyTemplate('tmpl2')">Copy</button>
                </div>
                <pre id="tmpl2" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">@everyone 🎉

**━━━ SYDNEY RP EVENT ━━━**

📅 **Date:** [Day, DD Month YYYY]
🕐 **Time:** [HH:MM AEST]
🎮 **Server:** [SYD-MAIN / SYD-EVT]
📌 **Type:** [Patrol / Training / Special Event]

**About this event:**
[Describe the event here. What's happening, who can join, any requirements.]

React with ✅ if you're attending!

━━━━━━━━━━━━━━━━━━━━━━
Hosted by: [Host Name] | Sydney RP Events Team</pre>
              </div>

              <div class="table-wrap">
                <div class="table-header">
                  <div class="table-title">🚨 Moderation Notice</div>
                  <button class="action-btn" onclick="copyTemplate('tmpl3')">Copy</button>
                </div>
                <pre id="tmpl3" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">🚨 **MODERATION NOTICE**

**Action Taken:** [Ban / Kick / Warning / Mute]
**User:** [Username]
**Reason:** [Brief reason]
**Duration:** [Permanent / X days / Temporary]

If you believe this action was made in error, please submit a ban appeal at our community portal.

━━━━━━━━━━━━━━━━━━━━━━
Sydney RP Moderation Team</pre>
              </div>

              <div class="table-wrap">
                <div class="table-header">
                  <div class="table-title">📋 Department Update</div>
                  <button class="action-btn" onclick="copyTemplate('tmpl4')">Copy</button>
                </div>
                <pre id="tmpl4" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">**━━━ [DEPARTMENT NAME] UPDATE ━━━**

Hello [Department Name] members,

[Write your department update here. Include any roster changes, policy updates, upcoming training, or other relevant news.]

**Key Points:**
• [Point 1]
• [Point 2]
• [Point 3]

Any questions? Reach out to leadership in [#channel-name].

— [Your Name], [Your Rank]
[Department Name] | Sydney RP</pre>
              </div>

              <div class="table-wrap">
                <div class="table-header">
                  <div class="table-title">🎬 Media Call-to-Action</div>
                  <button class="action-btn" onclick="copyTemplate('tmpl5')">Copy</button>
                </div>
                <pre id="tmpl5" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">📸 **GOT GREAT FOOTAGE?**

We're always looking for awesome screenshots and clips from inside our ERLC servers!

**We want:**
🖼️ High quality screenshots
🎥 Patrol / event video clips
✂️ Edited highlights and montages

**How to submit:**
Drop your media in #media-submissions and our team will review it for publishing on our socials and server.

Keep making Sydney RP look incredible! 🔵
— Sydney RP Media Team</pre>
              </div>

            </div>
          </div>

          <!-- Image templates -->
          <div id="tmpl-image" style="display:none">
            <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px">

              <div class="status-card" style="cursor:pointer" onclick="dlTemplate('Announcement Banner')">
                <div style="width:100%;height:110px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#0448c4,#0861fa);border:1px solid var(--border)">
                  <div style="text-align:center">
                    <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;letter-spacing:2px;color:#fff">SYDNEY RP</div>
                    <div style="font-size:11px;color:rgba(255,255,255,0.7);margin-top:2px">ANNOUNCEMENT</div>
                  </div>
                </div>
                <div style="font-weight:600;font-size:14px;margin-bottom:4px">Announcement Banner</div>
                <div style="font-size:12px;color:var(--muted);margin-bottom:10px">1920×600px — Discord banner format</div>
                <button class="action-btn" style="width:100%">⬇ Download Template</button>
              </div>

              <div class="status-card" style="cursor:pointer" onclick="dlTemplate('Event Poster')">
                <div style="width:100%;height:110px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(160deg,#060b14,#111827);border:1px solid var(--border)">
                  <div style="text-align:center">
                    <div style="font-size:28px">🎉</div>
                    <div style="font-family:'Bebas Neue',sans-serif;font-size:16px;letter-spacing:2px;color:var(--brand);margin-top:4px">EVENT POSTER</div>
                  </div>
                </div>
                <div style="font-weight:600;font-size:14px;margin-bottom:4px">Event Poster</div>
                <div style="font-size:12px;color:var(--muted);margin-bottom:10px">1080×1080px — Square social format</div>
                <button class="action-btn" style="width:100%">⬇ Download Template</button>
              </div>

              <div class="status-card" style="cursor:pointer" onclick="dlTemplate('Recruitment Graphic')">
                <div style="width:100%;height:110px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#0b1220,#1a2640);border:1px solid var(--border)">
                  <div style="text-align:center">
                    <div style="font-size:24px">👮</div>
                    <div style="font-family:'Bebas Neue',sans-serif;font-size:14px;letter-spacing:2px;color:#fff;margin-top:4px">NOW RECRUITING</div>
                  </div>
                </div>
                <div style="font-weight:600;font-size:14px;margin-bottom:4px">Recruitment Graphic</div>
                <div style="font-size:12px;color:var(--muted);margin-bottom:10px">1200×628px — Link preview / banner</div>
                <button class="action-btn" style="width:100%">⬇ Download Template</button>
              </div>

              <div class="status-card" style="cursor:pointer" onclick="dlTemplate('Department Logo')">
                <div style="width:100%;height:110px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:var(--bg2);border:1px solid var(--border)">
                  <div style="text-align:center">
                    <div style="width:50px;height:50px;border-radius:50%;background:var(--brand-glow);border:2px solid var(--brand);margin:0 auto;display:flex;align-items:center;justify-content:center">
                      <span style="font-family:'Bebas Neue',sans-serif;font-size:18px;color:var(--brand)">SRP</span>
                    </div>
                  </div>
                </div>
                <div style="font-weight:600;font-size:14px;margin-bottom:4px">Department Logo Pack</div>
                <div style="font-size:12px;color:var(--muted);margin-bottom:10px">512×512px — All departments included</div>
                <button class="action-btn" style="width:100%">⬇ Download Template</button>
              </div>

              <div class="status-card" style="cursor:pointer" onclick="dlTemplate('Patrol Thumbnail')">
                <div style="width:100%;height:110px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#111827,#1a2640);border:1px solid var(--border)">
                  <div style="text-align:center">
                    <div style="font-size:26px">🎥</div>
                    <div style="font-family:'Bebas Neue',sans-serif;font-size:14px;letter-spacing:1px;color:var(--muted);margin-top:4px">PATROL CLIP</div>
                  </div>
                </div>
                <div style="font-weight:600;font-size:14px;margin-bottom:4px">Video Thumbnail</div>
                <div style="font-size:12px;color:var(--muted);margin-bottom:10px">1280×720px — YouTube / social video</div>
                <button class="action-btn" style="width:100%">⬇ Download Template</button>
              </div>

              <div class="status-card" style="cursor:pointer" onclick="dlTemplate('Discord Profile Banner')">
                <div style="width:100%;height:110px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(90deg,#0448c4,#38bdf8);border:1px solid var(--border)">
                  <div style="font-family:'Bebas Neue',sans-serif;font-size:20px;letter-spacing:3px;color:#fff">SYDNEY RP STAFF</div>
                </div>
                <div style="font-weight:600;font-size:14px;margin-bottom:4px">Discord Profile Banner</div>
                <div style="font-size:12px;color:var(--muted);margin-bottom:10px">960×480px — Discord profile banner</div>
                <button class="action-btn" style="width:100%">⬇ Download Template</button>
              </div>

            </div>
            <div style="margin-top:16px;padding:14px 16px;background:rgba(8,97,250,0.08);border:1px solid rgba(8,97,250,0.2);border-radius:8px;font-size:13px;color:var(--muted)">
              💡 Templates are provided as editable files. Upload your completed graphics to <strong style="color:var(--text)">#media-submissions</strong> for approval before publishing.
            </div>
          </div>
        </div>

        <!-- TEAM CHAT -->
        <div id="msec-chat" style="display:none">
          <div style="display:grid;grid-template-columns:1fr 280px;gap:16px;height:520px">
            <div style="display:flex;flex-direction:column;background:var(--bg2);border:1px solid var(--border2);border-radius:var(--r);overflow:hidden">
              <div style="padding:14px 18px;border-bottom:1px solid var(--border2);font-weight:600;font-size:14px;display:flex;align-items:center;gap:8px">
                <span style="color:var(--brand)">●</span> Media Team Chat
                <span style="font-size:12px;color:var(--muted);font-weight:400;margin-left:auto">5 online</span>
              </div>
              <div id="chatMessages" style="flex:1;overflow-y:auto;padding:16px;display:flex;flex-direction:column;gap:14px">
                <div class="chat-msg"><span class="chat-name" style="color:var(--brand)">Founder</span><span class="chat-time">Yesterday 9:14 AM</span><div class="chat-text">Hey team, remember to get the patrol montage submitted by Friday for the weekly post 📹</div></div>
                <div class="chat-msg"><span class="chat-name">Admin_Sarah</span><span class="chat-time">Yesterday 10:02 AM</span><div class="chat-text">On it! Got about 3 clips from last night's patrol session, editing now</div></div>
                <div class="chat-msg"><span class="chat-name">MediaMike</span><span class="chat-time">Yesterday 2:45 PM</span><div class="chat-text">Just uploaded the recruitment graphic to #media-submissions — can someone approve?</div></div>
                <div class="chat-msg"><span class="chat-name" style="color:var(--brand)">Founder</span><span class="chat-time">Today 8:30 AM</span><div class="chat-text">Approved and published! Looks great 🔥 We also need a new event poster for Friday's hosted patrol</div></div>
                <div class="chat-msg"><span class="chat-name">Admin_Sarah</span><span class="chat-time">Today 9:15 AM</span><div class="chat-text">I can do the poster, give me a couple hours</div></div>
              </div>
              <div style="padding:12px 16px;border-top:1px solid var(--border2);display:flex;gap:10px">
                <input class="form-input" id="chatInput" type="text" placeholder="Message the media team..." style="flex:1" onkeydown="if(event.key==='Enter')sendChatMsg()">
                <button class="btn-primary" style="padding:10px 18px;font-size:14px" onclick="sendChatMsg()">Send</button>
              </div>
            </div>
            <div style="background:var(--bg2);border:1px solid var(--border2);border-radius:var(--r);overflow:hidden">
              <div style="padding:14px 18px;border-bottom:1px solid var(--border2);font-weight:600;font-size:14px">Team Members</div>
              <div style="padding:12px 16px;display:flex;flex-direction:column;gap:10px">
                <div style="display:flex;align-items:center;gap:10px"><div style="width:8px;height:8px;border-radius:50%;background:var(--success)"></div><div><div style="font-size:14px;font-weight:500">Founder</div><div style="font-size:11px;color:var(--brand)">Media Lead</div></div></div>
                <div style="display:flex;align-items:center;gap:10px"><div style="width:8px;height:8px;border-radius:50%;background:var(--success)"></div><div><div style="font-size:14px;font-weight:500">Admin_Sarah</div><div style="font-size:11px;color:var(--muted)">Editor</div></div></div>
                <div style="display:flex;align-items:center;gap:10px"><div style="width:8px;height:8px;border-radius:50%;background:var(--success)"></div><div><div style="font-size:14px;font-weight:500">MediaMike</div><div style="font-size:11px;color:var(--muted)">Graphic Designer</div></div></div>
                <div style="display:flex;align-items:center;gap:10px"><div style="width:8px;height:8px;border-radius:50%;background:var(--warn)"></div><div><div style="font-size:14px;font-weight:500">ClipMaster99</div><div style="font-size:11px;color:var(--muted)">Video Editor</div></div></div>
                <div style="display:flex;align-items:center;gap:10px"><div style="width:8px;height:8px;border-radius:50%;background:var(--muted)"></div><div><div style="font-size:14px;font-weight:500">Mod_Tom</div><div style="font-size:11px;color:var(--muted)">Photographer</div></div></div>
              </div>
            </div>
          </div>
        </div>

        <!-- MEDIA GALLERY -->
        <div id="msec-gallery" style="display:none">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;flex-wrap:wrap;gap:10px">
            <div style="display:flex;gap:8px">
              <button class="ftab active" id="gtab-all" onclick="galleryFilter('all')" style="flex:unset;padding:7px 14px;font-size:13px">All</button>
              <button class="ftab" id="gtab-images" onclick="galleryFilter('images')" style="flex:unset;padding:7px 14px;font-size:13px">🖼️ Images</button>
              <button class="ftab" id="gtab-videos" onclick="galleryFilter('videos')" style="flex:unset;padding:7px 14px;font-size:13px">🎥 Videos</button>
            </div>
            <label style="cursor:pointer">
              <input type="file" accept="image/*,video/*" style="display:none" onchange="handleUpload(event)">
              <div class="btn-primary" style="padding:9px 18px;font-size:13px">+ Upload Media</div>
            </label>
          </div>
          <div id="galleryGrid" style="display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:12px">
            <!-- Populated by JS -->
          </div>
          <div id="noMedia" style="display:none;text-align:center;padding:60px 20px;color:var(--muted);font-size:14px">No media uploaded yet. Click "Upload Media" to add images or videos.</div>
        </div>

      </div>

      <!-- STAFF ROSTER (ADMIN EDITOR) -->
      <div id="tab-roster" style="display:none">
        <div class="admin-header" style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:12px">
          <div>
            <h2>STAFF <span style="color:var(--brand)">ROSTER</span></h2>
            <p>Assign staff and supervisors to each session. Update each session in its own box.</p>
          </div>
          <div style="display:flex;gap:10px">
            <button class="btn-primary" onclick="saveRoster()">Update Roster</button>
            <button class="btn-outline" style="padding:12px 20px;font-size:14px" onclick="resetRoster()">Reset Roster</button>
          </div>
        </div>
        <div id="rosterEditorGrid" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:14px;margin-top:8px">
          <!-- Populated by JS -->
        </div>
        <div style="margin-top:20px;padding:12px 16px;background:rgba(8,97,250,0.07);border:1px solid rgba(8,97,250,0.18);border-radius:8px;font-size:13px;color:var(--muted)">
          💡 Tip: Mark a session as <strong style="color:var(--text)">Closed</strong> to lock it — it will appear greyed out on the public roster view.
        </div>
      </div>

      <!-- MESSAGES & NOTICES (ADMIN) -->
      <div id="tab-messages" style="display:none">
        <div class="admin-header">
          <h2>MESSAGES <span style="color:var(--brand)">&amp; NOTICES</span></h2>
          <p>Send direct notices to staff members.</p>
        </div>
        <div class="table-wrap" style="margin-bottom:20px">
          <div class="table-header"><div class="table-title">Send a Message</div></div>
          <div style="padding:20px 24px;display:grid;grid-template-columns:200px 1fr auto;gap:16px;align-items:start">
            <div>
              <label class="form-label" style="margin-bottom:8px;display:block">Send To</label>
              <select class="form-select" id="msgRecipient">
                <option>Founder (Owner)</option>
                <option>SeniorAdmin_Jake</option>
                <option>Admin_Sarah</option>
                <option>Mod_Tom</option>
                <option>All Staff</option>
              </select>
            </div>
            <div>
              <label class="form-label" style="margin-bottom:8px;display:block">Message</label>
              <textarea class="form-textarea" id="msgBody" style="min-height:80px" placeholder="Write your message or notice here..."></textarea>
            </div>
            <div style="padding-top:28px">
              <button class="btn-primary" style="white-space:nowrap" onclick="sendNotice()">Send Message</button>
            </div>
          </div>
        </div>
        <div class="table-wrap">
          <div class="table-header"><div class="table-title">Message Log</div></div>
          <div id="noticeLog" style="padding:16px 20px">
            <p style="font-size:14px;color:var(--muted)">No messages yet.</p>
          </div>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- STAFF PANEL (non-master) -->
<div id="staffPanel" class="page">
  <div class="admin-layout">
    <div class="admin-sidebar">
      <div class="sidebar-label">Portal</div>
      <div class="sidebar-item active" onclick="staffTab('sdash',this)">
        <span class="sidebar-icon">📊</span> Overview
      </div>
      <div class="sidebar-item" onclick="staffTab('sapps',this)">
        <span class="sidebar-icon">📋</span> Applications
      </div>
      <div class="sidebar-item" onclick="staffTab('sappeals',this)">
        <span class="sidebar-icon">⚖️</span> Appeals
      </div>
      <div class="sidebar-label">Departments</div>
      <div class="sidebar-item" onclick="staffTab('smedia',this)">
        <span class="sidebar-icon">🎬</span> Media Team
      </div>
      <div class="sidebar-item" onclick="staffTab('sroster',this)">
        <span class="sidebar-icon">📅</span> Roster View
      </div>
      <div class="sidebar-label">Account</div>
      <div class="sidebar-item" onclick="logout()">
        <span class="sidebar-icon">🚪</span> Log Out
      </div>
    </div>
    <div class="admin-main">
      <div id="tab-sdash">
        <div class="admin-header">
          <h2>STAFF OVERVIEW</h2>
          <p id="staffWelcome">Welcome back.</p>
        </div>
        <div class="admin-cards">
          <div class="admin-card"><div class="ac-num">3</div><div class="ac-label">Pending Apps</div></div>
          <div class="admin-card"><div class="ac-num">1</div><div class="ac-label">Open Appeals</div></div>
        </div>
        <div class="table-wrap">
          <div class="table-header"><div class="table-title">Your Recent Actions</div></div>
          <table class="data-table">
            <thead><tr><th>Action</th><th>Time</th></tr></thead>
            <tbody>
              <tr><td>Reviewed application from AussiePatrol</td><td style="color:var(--muted);font-size:13px">1d ago</td></tr>
              <tr><td>Logged in to Staff Portal</td><td style="color:var(--muted);font-size:13px">Now</td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <div id="tab-sapps" style="display:none">
        <div class="admin-header"><h2>APPLICATIONS</h2><p>Applications assigned to your review queue.</p></div>
        <div class="table-wrap">
          <div class="table-header"><div class="table-title">Review Queue</div></div>
          <table class="data-table">
            <thead><tr><th>Applicant</th><th>Type</th><th>Position</th><th>Actions</th></tr></thead>
            <tbody>
              <tr><td>xSydney_Cop</td><td><span class="badge badge-blue">Staff</span></td><td>Moderator</td>
                <td><button class="action-btn" onclick="this.closest('tr').cells[3].innerHTML='<span class=\'badge badge-green\'>Reviewed</span>'">Review</button></td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <div id="tab-sappeals" style="display:none">
        <div class="admin-header"><h2>BAN APPEALS</h2><p>Appeals in your review queue.</p></div>
        <div class="table-wrap">
          <div class="table-header"><div class="table-title">Appeals Queue</div></div>
          <table class="data-table">
            <thead><tr><th>Username</th><th>Ban Type</th><th>Status</th><th>Actions</th></tr></thead>
            <tbody>
              <tr><td>robloxguy123</td><td>Discord Ban</td><td><span class="badge badge-yellow">Pending</span></td>
                <td><button class="action-btn" onclick="this.closest('tr').cells[2].innerHTML='<span class=\'badge badge-blue\'>Escalated</span>'">Escalate to Admin</button></td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <div id="tab-smedia" style="display:none">
        <div class="admin-header"><h2>MEDIA <span style="color:var(--brand)">TEAM</span></h2><p>Team channels, templates, chat and media gallery.</p></div>
        <div style="display:flex;gap:4px;margin-bottom:28px;background:var(--bg2);border-radius:10px;padding:4px;max-width:560px">
          <div class="ftab active" id="smtab-channels" onclick="smediaTab('channels')">📡 Channels</div>
          <div class="ftab" id="smtab-templates" onclick="smediaTab('templates')">📄 Templates</div>
          <div class="ftab" id="smtab-chat" onclick="smediaTab('chat')">💬 Team Chat</div>
          <div class="ftab" id="smtab-gallery" onclick="smediaTab('gallery')">🖼️ Media Gallery</div>
        </div>
        <div id="smsec-channels">
          <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px">
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none"><div style="display:flex;align-items:center;gap:10px;margin-bottom:8px"><span style="font-size:18px;color:var(--muted)">#</span><span style="font-weight:600;font-size:15px">media-announcements</span><span class="badge badge-blue" style="margin-left:auto">Announce</span></div><div style="font-size:13px;color:var(--muted)">Official media team announcements and updates.</div><div class="dept-link" style="margin-top:10px">Open in Discord →</div></a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none"><div style="display:flex;align-items:center;gap:10px;margin-bottom:8px"><span style="font-size:18px;color:var(--muted)">#</span><span style="font-weight:600;font-size:15px">media-submissions</span><span class="badge badge-green" style="margin-left:auto">Submit</span></div><div style="font-size:13px;color:var(--muted)">Submit screenshots and clips for review.</div><div class="dept-link" style="margin-top:10px">Open in Discord →</div></a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none"><div style="display:flex;align-items:center;gap:10px;margin-bottom:8px"><span style="font-size:18px;color:var(--muted)">#</span><span style="font-weight:600;font-size:15px">media-general</span><span class="badge badge-gray" style="margin-left:auto">Chat</span></div><div style="font-size:13px;color:var(--muted)">General media team discussion and brainstorming.</div><div class="dept-link" style="margin-top:10px">Open in Discord →</div></a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none"><div style="display:flex;align-items:center;gap:10px;margin-bottom:8px"><span style="font-size:18px;color:var(--muted)">#</span><span style="font-weight:600;font-size:15px">published-content</span><span class="badge badge-yellow" style="margin-left:auto">Archive</span></div><div style="font-size:13px;color:var(--muted)">Archive of all approved published media.</div><div class="dept-link" style="margin-top:10px">Open in Discord →</div></a>
            <a href="https://discord.gg/sydneyrp" target="_blank" class="dept-card" style="text-decoration:none"><div style="display:flex;align-items:center;gap:10px;margin-bottom:8px"><span style="font-size:18px;color:var(--muted)">#</span><span style="font-weight:600;font-size:15px">video-editing</span><span class="badge badge-gray" style="margin-left:auto">Video</span></div><div style="font-size:13px;color:var(--muted)">Coordination for video editors and clip requests.</div><div class="dept-link" style="margin-top:10px">Open in Discord →</div></a>
          </div>
        </div>
        <div id="smsec-templates" style="display:none">
          <div style="display:flex;gap:8px;margin-bottom:20px;flex-wrap:wrap">
            <button class="ftab active" id="stmptab-text" onclick="stmplTab('text')" style="flex:unset;padding:8px 16px">Text Templates</button>
            <button class="ftab" id="stmptab-image" onclick="stmplTab('image')" style="flex:unset;padding:8px 16px">Image Templates</button>
          </div>
          <div id="stmpl-text">
            <div style="display:flex;flex-direction:column;gap:14px">
              <div class="table-wrap"><div class="table-header"><div class="table-title">📢 Server Announcement</div><button class="action-btn" onclick="copyTemplate('tmpl1')">Copy</button></div><pre id="stmpl1" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">@everyone&#10;&#10;📣 **[ANNOUNCEMENT TITLE]**&#10;&#10;[Write your announcement here. Keep it clear, concise, and professional.]&#10;&#10;━━━━━━━━━━━━━━━━━━━━━━&#10;🎮 **Sydney RP** | erlc.sydneyrp.com&#10;📅 Posted by: [Your Name] | [Date]</pre></div>
              <div class="table-wrap"><div class="table-header"><div class="table-title">🎉 Event Announcement</div><button class="action-btn" onclick="copyTemplate('stmpl2')">Copy</button></div><pre id="stmpl2" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">@everyone 🎉&#10;&#10;**━━━ SYDNEY RP EVENT ━━━**&#10;&#10;📅 **Date:** [Day, DD Month YYYY]&#10;🕐 **Time:** [HH:MM AEST]&#10;🎮 **Server:** [SYD-MAIN / SYD-EVT]&#10;📌 **Type:** [Patrol / Training / Special Event]&#10;&#10;**About this event:**&#10;[Describe the event here.]&#10;&#10;React with ✅ if attending!&#10;&#10;━━━━━━━━━━━━━━━━━━━━━━&#10;Hosted by: [Host Name] | Sydney RP Events Team</pre></div>
              <div class="table-wrap"><div class="table-header"><div class="table-title">🎬 Media Call-to-Action</div><button class="action-btn" onclick="copyTemplate('stmpl3')">Copy</button></div><pre id="stmpl3" style="padding:16px 20px;font-family:'DM Mono',monospace;font-size:13px;color:var(--muted);white-space:pre-wrap;line-height:1.7">📸 **GOT GREAT FOOTAGE?**&#10;&#10;We're always looking for screenshots and clips!&#10;&#10;**We want:**&#10;🖼️ High quality screenshots&#10;🎥 Patrol / event video clips&#10;✂️ Edited highlights and montages&#10;&#10;Drop your media in #media-submissions 🔵&#10;— Sydney RP Media Team</pre></div>
            </div>
          </div>
          <div id="stmpl-image" style="display:none">
            <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px">
              <div class="status-card"><div style="width:100%;height:100px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#0448c4,#0861fa);border:1px solid var(--border)"><div style="text-align:center"><div style="font-family:'Bebas Neue',sans-serif;font-size:20px;letter-spacing:2px;color:#fff">SYDNEY RP</div><div style="font-size:10px;color:rgba(255,255,255,0.7)">ANNOUNCEMENT</div></div></div><div style="font-weight:600;font-size:14px;margin-bottom:4px">Announcement Banner</div><div style="font-size:12px;color:var(--muted);margin-bottom:10px">1920×600px</div><button class="action-btn" style="width:100%" onclick="dlTemplate('Announcement Banner')">⬇ Download</button></div>
              <div class="status-card"><div style="width:100%;height:100px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(160deg,#060b14,#111827);border:1px solid var(--border)"><div style="text-align:center"><div style="font-size:26px">🎉</div><div style="font-family:'Bebas Neue',sans-serif;font-size:14px;color:var(--brand)">EVENT POSTER</div></div></div><div style="font-weight:600;font-size:14px;margin-bottom:4px">Event Poster</div><div style="font-size:12px;color:var(--muted);margin-bottom:10px">1080×1080px</div><button class="action-btn" style="width:100%" onclick="dlTemplate('Event Poster')">⬇ Download</button></div>
              <div class="status-card"><div style="width:100%;height:100px;border-radius:8px;margin-bottom:12px;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,#0b1220,#1a2640);border:1px solid var(--border)"><div style="text-align:center"><div style="font-size:22px">👮</div><div style="font-family:'Bebas Neue',sans-serif;font-size:13px;color:#fff">NOW RECRUITING</div></div></div><div style="font-weight:600;font-size:14px;margin-bottom:4px">Recruitment Graphic</div><div style="font-size:12px;color:var(--muted);margin-bottom:10px">1200×628px</div><button class="action-btn" style="width:100%" onclick="dlTemplate('Recruitment Graphic')">⬇ Download</button></div>
            </div>
          </div>
        </div>
        <div id="smsec-chat" style="display:none">
          <div style="display:flex;flex-direction:column;background:var(--bg2);border:1px solid var(--border2);border-radius:var(--r);overflow:hidden;height:460px">
            <div style="padding:14px 18px;border-bottom:1px solid var(--border2);font-weight:600;font-size:14px;display:flex;align-items:center;gap:8px"><span style="color:var(--brand)">●</span> Media Team Chat <span style="font-size:12px;color:var(--muted);font-weight:400;margin-left:auto">5 online</span></div>
            <div id="schatMessages" style="flex:1;overflow-y:auto;padding:16px;display:flex;flex-direction:column;gap:14px">
              <div class="chat-msg"><span class="chat-name" style="color:var(--brand)">Founder</span><span class="chat-time">Yesterday 9:14 AM</span><div class="chat-text">Hey team, remember to get the patrol montage submitted by Friday 📹</div></div>
              <div class="chat-msg"><span class="chat-name">Admin_Sarah</span><span class="chat-time">Yesterday 10:02 AM</span><div class="chat-text">On it! Got about 3 clips from last night's patrol, editing now</div></div>
              <div class="chat-msg"><span class="chat-name">MediaMike</span><span class="chat-time">Today 8:30 AM</span><div class="chat-text">Uploaded the recruitment graphic — can someone approve?</div></div>
            </div>
            <div style="padding:12px 16px;border-top:1px solid var(--border2);display:flex;gap:10px">
              <input class="form-input" id="schatInput" type="text" placeholder="Message the media team..." style="flex:1" onkeydown="if(event.key==='Enter')sendSChatMsg()">
              <button class="btn-primary" style="padding:10px 18px;font-size:14px" onclick="sendSChatMsg()">Send</button>
            </div>
          </div>
        </div>
        <div id="smsec-gallery" style="display:none">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;flex-wrap:wrap;gap:10px">
            <div style="display:flex;gap:8px">
              <button class="ftab active" id="sgtab-all" onclick="sgalleryFilter('all')" style="flex:unset;padding:7px 14px;font-size:13px">All</button>
              <button class="ftab" id="sgtab-images" onclick="sgalleryFilter('images')" style="flex:unset;padding:7px 14px;font-size:13px">🖼️ Images</button>
              <button class="ftab" id="sgtab-videos" onclick="sgalleryFilter('videos')" style="flex:unset;padding:7px 14px;font-size:13px">🎥 Videos</button>
            </div>
            <label style="cursor:pointer"><input type="file" accept="image/*,video/*" style="display:none" onchange="handleUpload(event)"><div class="btn-primary" style="padding:9px 18px;font-size:13px">+ Upload Media</div></label>
          </div>
          <div id="sgalleryGrid" style="display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:12px"></div>
          <div id="snoMedia" style="display:none;text-align:center;padding:60px 20px;color:var(--muted);font-size:14px">No media uploaded yet.</div>
        </div>
      </div>

      <!-- ROSTER VIEW (STAFF READ-ONLY) -->
      <div id="tab-sroster" style="display:none">
        <div class="admin-header">
          <h2>ROSTER <span style="color:var(--brand)">VIEW</span></h2>
          <p>Current session roster. Contact the Owner to make changes.</p>
        </div>
        <div id="rosterViewGrid" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:14px"></div>
      </div>

    </div>
  </div>
</div>

<!-- NEW ACCOUNT MODAL -->
<div class="modal-overlay" id="newAccountModal">
  <div class="modal-box">
    <button class="modal-close" onclick="document.getElementById('newAccountModal').classList.remove('open')">✕</button>
    <div class="modal-title">Create Staff Account</div>
    <div class="form-group">
      <label class="form-label">Username</label>
      <input class="form-input" type="text" id="newUser" placeholder="Staff username">
    </div>
    <div class="form-group">
      <label class="form-label">Password</label>
      <input class="form-input" type="password" id="newPass" placeholder="Set a password">
    </div>
    <div class="form-group">
      <label class="form-label">Role</label>
      <select class="form-select" id="newRole">
        <option>Moderator</option>
        <option>Administrator</option>
        <option>Senior Administrator</option>
        <option>Support Staff</option>
      </select>
    </div>
    <button class="form-submit" onclick="createAccount()">Create Account</button>
    <div class="success-msg" id="accountCreated" style="display:none">✓ Account created successfully.</div>
  </div>
</div>

<script>
const MASTER_USER = 'founder';
const MASTER_PASS = 'SydneyRP2025!';
let staffAccounts = [
  {user:'mod_jake',pass:'jake123',role:'Moderator'},
  {user:'admin_sarah',pass:'sarah123',role:'Administrator'}
];

const servers = [
  {name:'Sydney RP — Main',status:'online',players:28,max:50,uptime:'99.8%',code:'SYD-MAIN'},
  {name:'Sydney RP — Training',status:'online',players:9,max:30,uptime:'97.2%',code:'SYD-TRN'},
  {name:'Sydney RP — Events',status:'maintenance',players:0,max:50,uptime:'—',code:'SYD-EVT'},
  {name:'Sydney RP — Backup',status:'offline',players:0,max:50,uptime:'—',code:'SYD-BCK'},
];

function renderServers(containerId) {
  const c = document.getElementById(containerId);
  if (!c) return;
  c.innerHTML = servers.map(s => `
    <div class="status-card">
      <div class="sc-header">
        <div class="sc-name">${s.name}</div>
        <div class="status-pill ${s.status}">${s.status}</div>
      </div>
      <div class="sc-num">${s.status==='online'?s.players:0}<span style="font-size:14px;color:var(--muted)">/${s.max} players</span></div>
      <div class="sc-detail">Server Code: <span style="font-family:'DM Mono',monospace;color:var(--brand)">${s.code}</span></div>
      <div class="sc-detail">Uptime: ${s.uptime}</div>
    </div>
  `).join('');
}

function refreshStatus() {
  document.getElementById('lastUpdated').textContent = 'just now';
  renderServers('serverGrid');
}

function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  const el = document.getElementById(id);
  if (el) { el.classList.add('active'); window.scrollTo(0,0); }
  if (id === 'status') renderServers('serverGrid');
  if (id === 'adminPanel') renderServers('adminServerGrid');
  document.getElementById('navLinks').classList.remove('open');
}

function setTab(t, el) {
  document.querySelectorAll('.form-section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.ftab').forEach(b => b.classList.remove('active'));
  const sec = document.getElementById('form-' + t);
  if (sec) sec.classList.add('active');
  if (el) el.classList.add('active');
  else {
    const tabs = document.querySelectorAll('.ftab');
    const map = {staff:0,dept:1,appeal:2};
    if (map[t] !== undefined) tabs[map[t]].classList.add('active');
  }
}

function submitForm(type) {
  const msg = document.getElementById('success-' + type);
  msg.style.display = 'block';
  setTimeout(() => msg.style.display = 'none', 5000);
}

let currentRole = 'staff';
function setRole(r, el) {
  currentRole = r;
  document.querySelectorAll('.role-btn').forEach(b => b.classList.remove('active'));
  el.classList.add('active');
}

function doLogin() {
  const u = document.getElementById('loginUser').value.trim().toLowerCase();
  const p = document.getElementById('loginPass').value;
  document.getElementById('loginError').style.display = 'none';
  if (u === MASTER_USER && p === MASTER_PASS) {
    showPage('adminPanel'); buildRosterEditor(); return;
  }
  const found = staffAccounts.find(a => a.user === u && a.pass === p);
  if (found) {
    document.getElementById('staffWelcome').textContent = `Welcome back, ${found.user}. Role: ${found.role}`;
    showPage('staffPanel'); return;
  }
  document.getElementById('loginError').style.display = 'block';
}

function logout() {
  document.getElementById('loginUser').value = '';
  document.getElementById('loginPass').value = '';
  showPage('login');
}

function adminTab(tab, el) {
  document.querySelectorAll('#adminPanel .admin-main > div').forEach(d => d.style.display = 'none');
  document.getElementById('tab-' + tab).style.display = 'block';
  document.querySelectorAll('#adminPanel .admin-sidebar .sidebar-item').forEach(i => i.classList.remove('active'));
  el.classList.add('active');
  if (tab === 'servers') renderServers('adminServerGrid');
  if (tab === 'roster') buildRosterEditor();
}

function createAccount() {
  const u = document.getElementById('newUser').value.trim().toLowerCase();
  const p = document.getElementById('newPass').value;
  const r = document.getElementById('newRole').value;
  if (!u || !p) return;
  staffAccounts.push({user:u, pass:p, role:r});
  const tbody = document.getElementById('accountsTable');
  const row = document.createElement('tr');
  row.innerHTML = `<td>${u}</td><td><span class="badge badge-gray">${r}</span></td><td><span class="badge badge-green">Active</span></td><td><button class="action-btn">Edit</button> <button class="action-btn danger" onclick="removeAccount(this)">Remove</button></td>`;
  tbody.appendChild(row);
  document.getElementById('accountCreated').style.display = 'block';
  document.getElementById('newUser').value = '';
  document.getElementById('newPass').value = '';
  setTimeout(() => {
    document.getElementById('accountCreated').style.display = 'none';
    document.getElementById('newAccountModal').classList.remove('open');
  }, 2000);
}

function removeAccount(btn) {
  if (confirm('Remove this staff account?')) btn.closest('tr').remove();
}

function toggleMenu() {
  document.getElementById('navLinks').classList.toggle('open');
}

// ─── MEDIA TEAM ───
function mediaTab(tab) {
  ['channels','templates','chat','gallery'].forEach(t => {
    document.getElementById('msec-'+t).style.display = 'none';
    document.getElementById('mtab-'+t).classList.remove('active');
  });
  document.getElementById('msec-'+tab).style.display = 'block';
  document.getElementById('mtab-'+tab).classList.add('active');
  if (tab === 'gallery') renderGallery();
}

function smediaTab(tab) {
  ['channels','templates','chat','gallery'].forEach(t => {
    document.getElementById('smsec-'+t).style.display = 'none';
    document.getElementById('smtab-'+t).classList.remove('active');
  });
  document.getElementById('smsec-'+tab).style.display = 'block';
  document.getElementById('smtab-'+tab).classList.add('active');
  if (tab === 'gallery') renderSGallery();
}

function tmplTab(t) {
  document.getElementById('tmpl-text').style.display = t==='text'?'block':'none';
  document.getElementById('tmpl-image').style.display = t==='image'?'block':'none';
  document.getElementById('tmptab-text').classList.toggle('active', t==='text');
  document.getElementById('tmptab-image').classList.toggle('active', t==='image');
}

function stmplTab(t) {
  document.getElementById('stmpl-text').style.display = t==='text'?'block':'none';
  document.getElementById('stmpl-image').style.display = t==='image'?'block':'none';
  document.getElementById('stmptab-text').classList.toggle('active', t==='text');
  document.getElementById('stmptab-image').classList.toggle('active', t==='image');
}

function copyTemplate(id) {
  const el = document.getElementById(id);
  if (!el) return;
  navigator.clipboard.writeText(el.textContent).then(() => {
    const btns = document.querySelectorAll('.action-btn');
    btns.forEach(b => { if (b.getAttribute('onclick') && b.getAttribute('onclick').includes(id)) { const orig = b.textContent; b.textContent = '✓ Copied!'; b.style.color = 'var(--success)'; setTimeout(() => { b.textContent = orig; b.style.color = ''; }, 2000); }});
  });
}

function dlTemplate(name) {
  alert('Template "' + name + '" would download here.\n\nConnect your file storage to enable actual downloads.');
}

// ─── CHAT ───
let chatLog = [];
function sendChatMsg() {
  const inp = document.getElementById('chatInput');
  const msg = inp.value.trim();
  if (!msg) return;
  const now = new Date();
  const time = 'Today ' + now.getHours().toString().padStart(2,'0') + ':' + now.getMinutes().toString().padStart(2,'0');
  const div = document.createElement('div');
  div.className = 'chat-msg';
  div.innerHTML = `<div><span class="chat-name" style="color:var(--brand)">Founder</span><span class="chat-time">${time}</span></div><div class="chat-text">${msg}</div>`;
  document.getElementById('chatMessages').appendChild(div);
  document.getElementById('chatMessages').scrollTop = 9999;
  inp.value = '';
}

function sendSChatMsg() {
  const inp = document.getElementById('schatInput');
  const msg = inp.value.trim();
  if (!msg) return;
  const now = new Date();
  const time = 'Today ' + now.getHours().toString().padStart(2,'0') + ':' + now.getMinutes().toString().padStart(2,'0');
  const div = document.createElement('div');
  div.className = 'chat-msg';
  div.innerHTML = `<div><span class="chat-name" style="color:var(--brand)">You</span><span class="chat-time">${time}</span></div><div class="chat-text">${msg}</div>`;
  document.getElementById('schatMessages').appendChild(div);
  document.getElementById('schatMessages').scrollTop = 9999;
  inp.value = '';
}

// ─── GALLERY ───
let mediaItems = [];
let galleryFilterActive = 'all';
let sgalleryFilterActive = 'all';

function handleUpload(event) {
  const files = event.target.files;
  for (const file of files) {
    const url = URL.createObjectURL(file);
    const type = file.type.startsWith('video') ? 'video' : 'image';
    mediaItems.push({ url, type, name: file.name, time: new Date().toLocaleDateString() });
  }
  renderGallery();
  renderSGallery();
  event.target.value = '';
}

function renderGallery() {
  const grid = document.getElementById('galleryGrid');
  const none = document.getElementById('noMedia');
  if (!grid) return;
  const filtered = galleryFilterActive === 'all' ? mediaItems : mediaItems.filter(i => (galleryFilterActive === 'images' ? i.type === 'image' : i.type === 'video'));
  if (filtered.length === 0) { grid.innerHTML = ''; if(none) none.style.display = 'block'; return; }
  if(none) none.style.display = 'none';
  grid.innerHTML = filtered.map(item => `
    <div class="gallery-item">
      ${item.type === 'video'
        ? `<video src="${item.url}" muted></video>`
        : `<img src="${item.url}" alt="${item.name}">`}
      <div class="gallery-badge ${item.type === 'video' ? 'badge-blue' : 'badge-green'}">${item.type === 'video' ? '🎥 Video' : '🖼️ Image'}</div>
      <div class="gallery-label">${item.name.length > 20 ? item.name.slice(0,20)+'…' : item.name}</div>
    </div>
  `).join('');
}

function renderSGallery() {
  const grid = document.getElementById('sgalleryGrid');
  const none = document.getElementById('snoMedia');
  if (!grid) return;
  const filtered = sgalleryFilterActive === 'all' ? mediaItems : mediaItems.filter(i => (sgalleryFilterActive === 'images' ? i.type === 'image' : i.type === 'video'));
  if (filtered.length === 0) { grid.innerHTML = ''; if(none) none.style.display = 'block'; return; }
  if(none) none.style.display = 'none';
  grid.innerHTML = filtered.map(item => `
    <div class="gallery-item">
      ${item.type === 'video'
        ? `<video src="${item.url}" muted></video>`
        : `<img src="${item.url}" alt="${item.name}">`}
      <div class="gallery-badge ${item.type === 'video' ? 'badge-blue' : 'badge-green'}">${item.type === 'video' ? '🎥 Video' : '🖼️ Image'}</div>
      <div class="gallery-label">${item.name.length > 20 ? item.name.slice(0,20)+'…' : item.name}</div>
    </div>
  `).join('');
}

function galleryFilter(f) {
  galleryFilterActive = f;
  ['all','images','videos'].forEach(t => document.getElementById('gtab-'+t).classList.toggle('active', t===f));
  renderGallery();
}

function sgalleryFilter(f) {
  sgalleryFilterActive = f;
  ['all','images','videos'].forEach(t => document.getElementById('sgtab-'+t).classList.toggle('active', t===f));
  renderSGallery();
}

// ─── ROSTER DATA ───
const allStaff = ['Founder','SeniorAdmin_Jake','Admin_Sarah','Mod_Tom','MediaMike','ClipMaster99'];
const allSupervisors = ['Founder','SeniorAdmin_Jake','Admin_Sarah'];
const NUM_SESSIONS = 7;
let rosterData = Array.from({length: NUM_SESSIONS}, (_, i) => ({session:i+1, closed:false, staff:[], supervisors:[]}));

function buildRosterEditor() {
  const grid = document.getElementById('rosterEditorGrid');
  if (!grid) return;
  grid.innerHTML = rosterData.map((s, idx) => `
    <div class="table-wrap" style="padding:18px 20px">
      <div style="font-weight:700;font-size:15px;margin-bottom:12px">Session ${s.session}</div>
      <label style="display:flex;align-items:center;gap:8px;font-size:13px;cursor:pointer;margin-bottom:14px">
        <input type="checkbox" ${s.closed?'checked':''} onchange="rosterData[${idx}].closed=this.checked;buildRosterEditor()">
        <span style="color:var(--text)">Closed</span>
      </label>
      ${s.closed ? '<div style="font-size:13px;color:var(--muted);margin-bottom:10px">This session is marked as closed.</div>' : `
      <div style="margin-bottom:12px">
        <div style="font-size:12px;font-weight:500;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;margin-bottom:8px">Select staff to be rostered on</div>
        <div style="display:flex;flex-direction:column;gap:6px;background:var(--bg2);border:1px solid var(--border2);border-radius:8px;padding:10px">
          ${allStaff.map(name => `<label style="display:flex;align-items:center;gap:8px;font-size:13px;cursor:pointer"><input type="checkbox" ${s.staff.includes(name)?'checked':''} onchange="toggleRosterMember(${idx},'staff','${name}',this.checked)"> ${name}</label>`).join('')}
        </div>
        ${s.staff.length ? '<div style="margin-top:6px;font-size:12px;color:var(--brand)">'+s.staff.length+' selected</div>' : ''}
      </div>
      <div style="margin-bottom:12px">
        <div style="font-size:12px;font-weight:500;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;margin-bottom:8px">Select a supervisor to be rostered on</div>
        <div style="display:flex;flex-direction:column;gap:6px;background:var(--bg2);border:1px solid var(--border2);border-radius:8px;padding:10px">
          ${allSupervisors.map(name => `<label style="display:flex;align-items:center;gap:8px;font-size:13px;cursor:pointer"><input type="checkbox" ${s.supervisors.includes(name)?'checked':''} onchange="toggleRosterMember(${idx},'supervisors','${name}',this.checked)"> ${name}</label>`).join('')}
        </div>
        ${s.supervisors.length ? '<div style="margin-top:6px;font-size:12px;color:var(--brand)">'+s.supervisors.length+' selected</div>' : ''}
      </div>`}
      <button class="btn-primary" style="width:100%;padding:10px;font-size:13px;margin-top:4px" onclick="saveSession(${idx})">Update</button>
    </div>
  `).join('');
}

function toggleRosterMember(idx, field, name, checked) {
  if (checked) { if (!rosterData[idx][field].includes(name)) rosterData[idx][field].push(name); }
  else { rosterData[idx][field] = rosterData[idx][field].filter(n => n !== name); }
}

function saveSession(idx) {
  const btn = event.target;
  btn.textContent = '✓ Updated!'; btn.style.background = 'var(--success)';
  setTimeout(() => { btn.textContent = 'Update'; btn.style.background = ''; }, 2000);
  renderRosterView('rosterViewGrid');
}

function saveRoster() {
  const btn = event.target;
  btn.textContent = '✓ Roster Saved!'; btn.style.background = 'var(--success)';
  setTimeout(() => { btn.textContent = 'Update Roster'; btn.style.background = ''; }, 2000);
  renderRosterView('rosterViewGrid');
}

function resetRoster() {
  if (!confirm('Reset all roster assignments? This cannot be undone.')) return;
  rosterData.forEach(s => { s.closed = false; s.staff = []; s.supervisors = []; });
  buildRosterEditor(); renderRosterView('rosterViewGrid');
}

function renderRosterView(containerId) {
  const grid = document.getElementById(containerId);
  if (!grid) return;
  grid.innerHTML = rosterData.map(s => `
    <div class="table-wrap" style="padding:18px 20px;${s.closed?'opacity:.45':''}">
      <div style="font-weight:700;font-size:15px;margin-bottom:10px">Session ${s.session}</div>
      ${s.closed
        ? '<div style="font-size:13px;color:var(--muted)">Closed</div>'
        : `<div style="margin-bottom:10px">
            <div style="font-weight:600;font-size:13px;margin-bottom:6px">Staff</div>
            ${s.staff.length ? s.staff.map(n=>`<div style="display:inline-flex;align-items:center;gap:6px;background:var(--brand-glow);border:1px solid var(--border);border-radius:100px;padding:3px 12px;font-size:12px;margin:2px">${n}</div>`).join('') : '<div style="font-size:13px;color:var(--muted)">No staff assigned.</div>'}
          </div>
          <div>
            <div style="font-weight:600;font-size:13px;margin-bottom:6px">Supervisors</div>
            ${s.supervisors.length ? s.supervisors.map(n=>`<div style="display:inline-flex;align-items:center;gap:6px;background:rgba(255,255,255,0.05);border:1px solid var(--border2);border-radius:100px;padding:3px 12px;font-size:12px;margin:2px">${n}</div>`).join('') : '<div style="font-size:13px;color:var(--muted)">No supervisors assigned.</div>'}
          </div>`}
    </div>
  `).join('');
}

// ─── MESSAGES ───
let noticeMessages = [];
function sendNotice() {
  const to = document.getElementById('msgRecipient').value;
  const body = document.getElementById('msgBody').value.trim();
  if (!body) return;
  const now = new Date();
  noticeMessages.unshift({ to, body, time: now.toLocaleTimeString([],{hour:'2-digit',minute:'2-digit'})+' '+now.toLocaleDateString() });
  renderNotices();
  document.getElementById('msgBody').value = '';
}

function renderNotices() {
  const log = document.getElementById('noticeLog');
  if (!log) return;
  if (!noticeMessages.length) { log.innerHTML = '<p style="font-size:14px;color:var(--muted)">No messages yet.</p>'; return; }
  log.innerHTML = noticeMessages.map(m => `
    <div style="padding:12px 0;border-bottom:1px solid var(--border2)">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:4px">
        <span style="font-size:13px;font-weight:600">To: <span style="color:var(--brand)">${m.to}</span></span>
        <span style="font-size:11px;color:var(--muted)">${m.time}</span>
      </div>
      <div style="font-size:14px;color:var(--muted);line-height:1.6">${m.body}</div>
    </div>
  `).join('');
}

// ─── STAFF TAB ───
function staffTab(tab, el) {
  ['sdash','sapps','sappeals','smedia','sroster'].forEach(t => {
    const el2 = document.getElementById('tab-' + t);
    if (el2) el2.style.display = 'none';
  });
  document.getElementById('tab-' + tab).style.display = 'block';
  document.querySelectorAll('#staffPanel .sidebar-item').forEach(i => i.classList.remove('active'));
  el.classList.add('active');
  if (tab === 'sroster') renderRosterView('rosterViewGrid');
}

renderServers('serverGrid');
buildRosterEditor();
</script>
</body>
</html>
