<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GrantWatch Kenya — Find Grants. Apply Smarter.</title>
<style>
/* ── TOKENS ─────────────────────────────────────────────────────────────── */
:root {
  --navy:   #0A3D5C;
  --teal:   #0D7C8C;
  --gold:   #E8A020;
  --white:  #FFFFFF;
  --offwhite: #F4F8FB;
  --light:  #E8F4F8;
  --text:   #1E293B;
  --muted:  #64748B;
  --border: #CBD5E1;
  --green:  #16A34A;
  --red:    #DC2626;
  --yellow: #D97706;
  --font-display: 'Georgia', serif;
  --font-body: 'Segoe UI', Arial, sans-serif;
  --radius: 10px;
  --shadow: 0 2px 12px rgba(0,0,0,0.09);
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: var(--font-body); background: var(--offwhite); color: var(--text); }
a { color: inherit; text-decoration: none; }
img { max-width: 100%; }

/* ── NAVIGATION ──────────────────────────────────────────────────────────── */
nav {
  background: var(--navy);
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 32px; height: 62px; position: sticky; top: 0; z-index: 100;
  box-shadow: 0 2px 8px rgba(0,0,0,0.18);
}
.nav-logo {
  font-family: var(--font-display);
  font-size: 1.25rem; font-weight: 700; color: var(--white);
  display: flex; align-items: center; gap: 10px;
}
.nav-logo span { color: var(--gold); }
.nav-links { display: flex; gap: 6px; }
.nav-links a {
  color: rgba(255,255,255,0.78); font-size: 0.88rem; font-weight: 500;
  padding: 7px 14px; border-radius: 6px; transition: all .2s; cursor: pointer;
}
.nav-links a:hover, .nav-links a.active {
  background: rgba(255,255,255,0.1); color: var(--white);
}
.nav-cta {
  background: var(--gold); color: var(--navy) !important;
  font-weight: 700 !important; padding: 8px 18px !important;
  border-radius: 6px !important;
}
.nav-cta:hover { background: #f0b030 !important; }

/* ── PAGE SECTIONS ───────────────────────────────────────────────────────── */
.page { display: none; }
.page.active { display: block; }

/* ── HERO ────────────────────────────────────────────────────────────────── */
.hero {
  background: linear-gradient(135deg, var(--navy) 0%, #0D5C7A 60%, var(--teal) 100%);
  padding: 80px 32px 64px; text-align: center; color: var(--white);
  position: relative; overflow: hidden;
}
.hero::before {
  content: ""; position: absolute; top: -60px; right: -60px;
  width: 320px; height: 320px; border-radius: 50%;
  background: rgba(232,160,32,0.1);
}
.hero::after {
  content: ""; position: absolute; bottom: -80px; left: -40px;
  width: 260px; height: 260px; border-radius: 50%;
  background: rgba(13,124,140,0.2);
}
.hero-tag {
  display: inline-block; background: rgba(232,160,32,0.2);
  border: 1px solid var(--gold); color: var(--gold);
  font-size: 0.78rem; font-weight: 700; letter-spacing: 2px;
  padding: 5px 16px; border-radius: 20px; margin-bottom: 20px;
}
.hero h1 {
  font-family: var(--font-display); font-size: 2.8rem;
  font-weight: 700; line-height: 1.2; margin-bottom: 18px;
  max-width: 720px; margin-left: auto; margin-right: auto;
}
.hero h1 em { color: var(--gold); font-style: normal; }
.hero p {
  font-size: 1.05rem; color: rgba(255,255,255,0.82);
  max-width: 560px; margin: 0 auto 32px; line-height: 1.7;
}
.hero-btns { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }
.btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 13px 26px; border-radius: 8px; font-size: 0.95rem;
  font-weight: 600; cursor: pointer; transition: all .2s; border: none;
}
.btn-gold { background: var(--gold); color: var(--navy); }
.btn-gold:hover { background: #f0b030; transform: translateY(-1px); }
.btn-outline {
  background: transparent; color: var(--white);
  border: 2px solid rgba(255,255,255,0.45);
}
.btn-outline:hover { border-color: var(--white); background: rgba(255,255,255,0.08); }
.btn-primary { background: var(--teal); color: var(--white); }
.btn-primary:hover { background: #0a6575; }
.btn-sm { padding: 8px 16px; font-size: 0.84rem; }

/* Stats bar */
.stats-bar {
  background: var(--white); border-bottom: 1px solid var(--border);
  display: flex; justify-content: center; gap: 0;
}
.stat-item {
  padding: 18px 36px; text-align: center; border-right: 1px solid var(--border);
}
.stat-item:last-child { border-right: none; }
.stat-item strong { display: block; font-size: 1.5rem; font-weight: 800; color: var(--navy); }
.stat-item span { font-size: 0.8rem; color: var(--muted); }

/* ── SECTION WRAPPER ─────────────────────────────────────────────────────── */
.section { padding: 52px 32px; max-width: 1100px; margin: 0 auto; }
.section-title {
  font-family: var(--font-display); font-size: 1.65rem;
  font-weight: 700; color: var(--navy); margin-bottom: 6px;
}
.section-sub { color: var(--muted); font-size: 0.95rem; margin-bottom: 32px; }

/* ── SEARCH & FILTER ─────────────────────────────────────────────────────── */
.search-bar {
  background: var(--white); border-radius: var(--radius);
  box-shadow: var(--shadow); padding: 20px 24px;
  display: flex; gap: 12px; flex-wrap: wrap; align-items: center;
  margin-bottom: 24px;
}
.search-bar input, .search-bar select {
  flex: 1; min-width: 160px; padding: 10px 14px;
  border: 1.5px solid var(--border); border-radius: 7px;
  font-size: 0.9rem; font-family: var(--font-body);
  outline: none; transition: border .2s;
}
.search-bar input:focus, .search-bar select:focus { border-color: var(--teal); }
.search-bar button { flex-shrink: 0; }

/* ── GRANT CARDS ─────────────────────────────────────────────────────────── */
.grants-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 20px;
}
.grant-card {
  background: var(--white); border-radius: var(--radius);
  box-shadow: var(--shadow); overflow: hidden;
  border: 1px solid var(--border); transition: transform .2s, box-shadow .2s;
  display: flex; flex-direction: column;
}
.grant-card:hover { transform: translateY(-3px); box-shadow: 0 6px 24px rgba(0,0,0,0.12); }
.card-top {
  padding: 18px 20px 14px;
  border-bottom: 1px solid var(--border);
}
.card-sector {
  display: inline-block; font-size: 0.72rem; font-weight: 700;
  letter-spacing: 1px; padding: 3px 10px; border-radius: 20px;
  margin-bottom: 10px; text-transform: uppercase;
}
.sector-tech { background: #DBEAFE; color: #1E40AF; }
.sector-agri { background: #DCFCE7; color: #166534; }
.sector-community { background: #FEF3C7; color: #92400E; }
.sector-health { background: #FCE7F3; color: #9D174D; }
.sector-all { background: var(--light); color: var(--navy); }
.sector-climate { background: #D1FAE5; color: #065F46; }
.sector-women { background: #FDE8F4; color: #831843; }
.card-title {
  font-size: 0.97rem; font-weight: 700; color: var(--navy);
  line-height: 1.4; margin-bottom: 6px;
}
.card-org { font-size: 0.83rem; color: var(--muted); }
.card-body { padding: 14px 20px; flex: 1; }
.card-amount {
  font-size: 1.1rem; font-weight: 800; color: var(--teal);
  margin-bottom: 10px;
}
.card-meta {
  display: flex; flex-direction: column; gap: 5px;
  font-size: 0.82rem; color: var(--muted);
}
.card-meta span { display: flex; align-items: center; gap: 6px; }
.deadline-badge {
  display: inline-block; font-size: 0.75rem; font-weight: 700;
  padding: 3px 10px; border-radius: 20px; margin-top: 6px;
}
.deadline-urgent { background: #FEE2E2; color: var(--red); }
.deadline-soon { background: #FEF3C7; color: var(--yellow); }
.deadline-ok { background: #DCFCE7; color: var(--green); }
.deadline-rolling { background: var(--light); color: var(--navy); }
.card-footer {
  padding: 12px 20px; border-top: 1px solid var(--border);
  display: flex; gap: 8px;
}
.card-footer button {
  flex: 1; padding: 9px; border: none; border-radius: 6px;
  font-size: 0.84rem; font-weight: 600; cursor: pointer; transition: all .2s;
}
.btn-apply { background: var(--teal); color: var(--white); }
.btn-apply:hover { background: #0a6575; }
.btn-save { background: var(--light); color: var(--navy); }
.btn-save:hover { background: #d0e8f0; }

/* ── MODAL ───────────────────────────────────────────────────────────────── */
.modal-overlay {
  display: none; position: fixed; inset: 0;
  background: rgba(10,61,92,0.55); z-index: 999;
  align-items: center; justify-content: center; padding: 20px;
}
.modal-overlay.open { display: flex; }
.modal {
  background: var(--white); border-radius: 14px;
  max-width: 620px; width: 100%; max-height: 88vh;
  overflow-y: auto; box-shadow: 0 20px 60px rgba(0,0,0,0.25);
}
.modal-header {
  padding: 24px 28px 16px;
  border-bottom: 1px solid var(--border);
  display: flex; justify-content: space-between; align-items: flex-start;
}
.modal-header h2 { font-size: 1.1rem; font-weight: 700; color: var(--navy); }
.modal-close {
  width: 32px; height: 32px; border: none; background: var(--offwhite);
  border-radius: 50%; font-size: 1.1rem; cursor: pointer; color: var(--muted);
  display: flex; align-items: center; justify-content: center;
}
.modal-body { padding: 20px 28px 28px; }
.modal-field { margin-bottom: 16px; }
.modal-field label {
  display: block; font-size: 0.85rem; font-weight: 600;
  color: var(--navy); margin-bottom: 6px;
}
.modal-field input, .modal-field select, .modal-field textarea {
  width: 100%; padding: 10px 13px; border: 1.5px solid var(--border);
  border-radius: 7px; font-size: 0.9rem; font-family: var(--font-body);
  outline: none; transition: border .2s;
}
.modal-field input:focus, .modal-field select:focus, .modal-field textarea:focus {
  border-color: var(--teal);
}
.modal-field textarea { resize: vertical; min-height: 80px; }
.modal-section-title {
  font-size: 0.8rem; font-weight: 700; color: var(--muted);
  letter-spacing: 1px; text-transform: uppercase;
  margin: 20px 0 12px; padding-bottom: 6px;
  border-bottom: 1px solid var(--border);
}
.checkbox-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
.checkbox-item {
  display: flex; align-items: center; gap: 8px;
  font-size: 0.87rem; cursor: pointer;
}
.checkbox-item input { accent-color: var(--teal); width: 15px; height: 15px; }
.form-success {
  display: none; text-align: center; padding: 30px 20px;
}
.form-success .check-icon {
  width: 60px; height: 60px; border-radius: 50%;
  background: #DCFCE7; color: var(--green);
  font-size: 1.8rem; display: flex; align-items: center;
  justify-content: center; margin: 0 auto 16px;
}
.form-success h3 { color: var(--navy); margin-bottom: 8px; }
.form-success p { color: var(--muted); font-size: 0.9rem; }

/* ── ADMIN PANEL ─────────────────────────────────────────────────────────── */
.admin-grid { display: grid; grid-template-columns: 240px 1fr; gap: 24px; }
.admin-sidebar {
  background: var(--white); border-radius: var(--radius);
  box-shadow: var(--shadow); padding: 20px; height: fit-content;
}
.admin-sidebar h3 {
  font-size: 0.8rem; font-weight: 700; color: var(--muted);
  letter-spacing: 1px; text-transform: uppercase; margin-bottom: 12px;
}
.admin-nav-item {
  display: flex; align-items: center; gap: 10px;
  padding: 10px 12px; border-radius: 7px; font-size: 0.88rem;
  cursor: pointer; color: var(--text); transition: all .2s; margin-bottom: 3px;
}
.admin-nav-item:hover { background: var(--light); }
.admin-nav-item.active { background: var(--light); color: var(--navy); font-weight: 600; }
.admin-nav-item .dot { width: 8px; height: 8px; border-radius: 50%; background: var(--teal); }

.admin-main { display: flex; flex-direction: column; gap: 20px; }
.admin-card {
  background: var(--white); border-radius: var(--radius);
  box-shadow: var(--shadow); padding: 22px 24px;
}
.admin-card h3 {
  font-size: 1rem; font-weight: 700; color: var(--navy); margin-bottom: 16px;
  padding-bottom: 10px; border-bottom: 1px solid var(--border);
}

.kpi-row { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px; margin-bottom: 20px; }
.kpi {
  background: var(--white); border-radius: var(--radius);
  box-shadow: var(--shadow); padding: 18px 20px;
  border-left: 4px solid var(--teal);
}
.kpi.gold { border-left-color: var(--gold); }
.kpi.green { border-left-color: var(--green); }
.kpi.red { border-left-color: var(--red); }
.kpi .kpi-val { font-size: 1.7rem; font-weight: 800; color: var(--navy); }
.kpi .kpi-lbl { font-size: 0.78rem; color: var(--muted); margin-top: 2px; }

/* Table */
.data-table { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
.data-table th {
  text-align: left; padding: 10px 12px; background: var(--offwhite);
  font-size: 0.78rem; font-weight: 700; color: var(--muted);
  text-transform: uppercase; letter-spacing: 0.5px;
  border-bottom: 2px solid var(--border);
}
.data-table td {
  padding: 12px 12px; border-bottom: 1px solid var(--border);
  vertical-align: middle;
}
.data-table tr:last-child td { border-bottom: none; }
.data-table tr:hover td { background: var(--offwhite); }
.status-pill {
  display: inline-block; padding: 3px 10px; border-radius: 20px;
  font-size: 0.75rem; font-weight: 700;
}
.pill-active { background: #DCFCE7; color: var(--green); }
.pill-pending { background: #FEF3C7; color: var(--yellow); }
.pill-expired { background: #FEE2E2; color: var(--red); }
.pill-rolling { background: var(--light); color: var(--navy); }

/* ── ABOUT / HOW IT WORKS ────────────────────────────────────────────────── */
.how-steps {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px; margin-top: 16px;
}
.how-step {
  background: var(--white); border-radius: var(--radius);
  padding: 24px 20px; box-shadow: var(--shadow); text-align: center;
  border-top: 4px solid var(--teal); position: relative;
}
.how-step .step-num {
  width: 40px; height: 40px; border-radius: 50%;
  background: var(--teal); color: var(--white);
  font-size: 1rem; font-weight: 800;
  display: flex; align-items: center; justify-content: center;
  margin: 0 auto 14px;
}
.how-step h4 { font-size: 0.95rem; font-weight: 700; color: var(--navy); margin-bottom: 8px; }
.how-step p { font-size: 0.84rem; color: var(--muted); line-height: 1.6; }
.arrow-right {
  display: flex; align-items: center; justify-content: center;
  font-size: 1.5rem; color: var(--gold); margin-top: 50px;
}

.tools-row {
  display: flex; gap: 16px; flex-wrap: wrap; margin-top: 20px;
}
.tool-chip {
  background: var(--white); border: 1.5px solid var(--border);
  border-radius: 8px; padding: 12px 18px;
  display: flex; align-items: center; gap: 10px;
  font-size: 0.88rem; font-weight: 600; color: var(--navy);
  box-shadow: var(--shadow);
}
.tool-chip .tool-icon { font-size: 1.3rem; }

/* ── FOOTER ──────────────────────────────────────────────────────────────── */
footer {
  background: var(--navy); color: rgba(255,255,255,0.7);
  text-align: center; padding: 28px 32px; font-size: 0.84rem; margin-top: 40px;
}
footer strong { color: var(--gold); }
footer p { margin-bottom: 6px; }

/* ── TABS ────────────────────────────────────────────────────────────────── */
.tab-bar {
  display: flex; gap: 0; border-bottom: 2px solid var(--border);
  margin-bottom: 24px;
}
.tab-btn {
  padding: 10px 20px; font-size: 0.88rem; font-weight: 600;
  color: var(--muted); cursor: pointer; border-bottom: 3px solid transparent;
  margin-bottom: -2px; transition: all .2s; background: none; border-top: none;
  border-left: none; border-right: none;
}
.tab-btn.active { color: var(--teal); border-bottom-color: var(--teal); }

/* ── ALERT BANNER ────────────────────────────────────────────────────────── */
.alert {
  border-radius: 8px; padding: 12px 16px; margin-bottom: 16px;
  font-size: 0.87rem; display: flex; align-items: center; gap: 10px;
}
.alert-info { background: var(--light); color: var(--navy); border-left: 4px solid var(--teal); }
.alert-warn { background: #FEF3C7; color: #78350F; border-left: 4px solid var(--gold); }

/* ── FORM PAGE ───────────────────────────────────────────────────────────── */
.register-wrap {
  max-width: 620px; margin: 0 auto;
  background: var(--white); border-radius: var(--radius);
  box-shadow: var(--shadow); overflow: hidden;
}
.register-header {
  background: linear-gradient(135deg, var(--navy), var(--teal));
  padding: 32px 32px 24px; color: var(--white);
}
.register-header h2 { font-family: var(--font-display); font-size: 1.4rem; margin-bottom: 8px; }
.register-header p { font-size: 0.9rem; opacity: 0.85; }
.register-body { padding: 28px 32px; }
.field-group { margin-bottom: 18px; }
.field-group label {
  display: block; font-size: 0.85rem; font-weight: 600;
  color: var(--navy); margin-bottom: 7px;
}
.field-group input, .field-group select {
  width: 100%; padding: 11px 14px; border: 1.5px solid var(--border);
  border-radius: 7px; font-size: 0.9rem; font-family: var(--font-body); outline: none;
  transition: border .2s;
}
.field-group input:focus, .field-group select:focus { border-color: var(--teal); }
.interest-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
.interest-item {
  display: flex; align-items: center; gap: 9px;
  padding: 10px 12px; border: 1.5px solid var(--border);
  border-radius: 8px; cursor: pointer; transition: all .2s; font-size: 0.87rem;
}
.interest-item:hover { border-color: var(--teal); background: var(--light); }
.interest-item.selected { border-color: var(--teal); background: var(--light); color: var(--navy); font-weight: 600; }
.interest-item input { display: none; }
.interest-icon { font-size: 1.1rem; }
.submit-btn {
  width: 100%; padding: 14px; background: var(--teal); color: var(--white);
  border: none; border-radius: 8px; font-size: 1rem; font-weight: 700;
  cursor: pointer; transition: all .2s; margin-top: 8px;
}
.submit-btn:hover { background: #0a6575; }
.success-banner {
  display: none; background: #DCFCE7; border-radius: 10px;
  padding: 28px; text-align: center; margin: 20px 0;
}
.success-banner h3 { color: var(--green); font-size: 1.1rem; margin-bottom: 8px; }
.success-banner p { color: #166534; font-size: 0.9rem; }

/* ── RESPONSIVE ──────────────────────────────────────────────────────────── */
@media(max-width:768px){
  nav { padding: 0 16px; }
  .nav-links { display: none; }
  .hero h1 { font-size: 1.9rem; }
  .stats-bar { flex-wrap: wrap; }
  .stat-item { flex: 1; min-width: 120px; }
  .section { padding: 32px 16px; }
  .admin-grid { grid-template-columns: 1fr; }
  .kpi-row { grid-template-columns: 1fr 1fr; }
  .register-body { padding: 20px; }
  .interest-grid { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<!-- ── NAVIGATION ──────────────────────────────────────────────────────────── -->
<nav>
  <div class="nav-logo">🌍 Grant<span>Watch</span> Kenya</div>
  <div class="nav-links">
    <a onclick="showPage('home')" class="active" id="nav-home">Home</a>
    <a onclick="showPage('grants')" id="nav-grants">Browse Grants</a>
    <a onclick="showPage('register')" id="nav-register">Register</a>
    <a onclick="showPage('about')" id="nav-about">How It Works</a>
    <a onclick="showPage('admin')" id="nav-admin">Admin Panel</a>
    <a onclick="showPage('register')" class="nav-cta">Get Alerts →</a>
  </div>
</nav>

<!-- ══════════════════════════════════════════════════════════════════════════ -->
<!-- HOME PAGE -->
<!-- ══════════════════════════════════════════════════════════════════════════ -->
<div id="page-home" class="page active">
  <div class="hero">
    <div class="hero-tag">AI-POWERED GRANT FINDER — KENYA</div>
    <h1>Stop Missing Grants.<br>Start <em>Getting Funded.</em></h1>
    <p>We automatically find active grants in Kenya, track their deadlines, and send you alerts before they close — matched to your sector and organization type.</p>
    <div class="hero-btns">
      <button class="btn btn-gold" onclick="showPage('grants')">Browse Active Grants →</button>
      <button class="btn btn-outline" onclick="showPage('register')">Get Email Alerts</button>
    </div>
  </div>

  <div class="stats-bar">
    <div class="stat-item"><strong id="stat-total">15</strong><span>Active Grants</span></div>
    <div class="stat-item"><strong>KSh 50K–6.5M</strong><span>Funding Range</span></div>
    <div class="stat-item"><strong id="stat-urgent">3</strong><span>Closing This Month</span></div>
    <div class="stat-item"><strong id="stat-clients">0</strong><span>Registered Users</span></div>
    <div class="stat-item"><strong>7</strong><span>Sectors Covered</span></div>
  </div>

  <!-- Urgent alerts -->
  <div class="section">
    <div class="alert alert-warn">
      ⚠️ <strong>3 grants close within 30 days.</strong> Register now to get deadline reminders before they expire.
    </div>
    <div class="alert alert-info">
      🤖 <strong>Powered by Manus AI + Google Sheets.</strong> Grant data is updated weekly. Expired grants are automatically hidden.
    </div>

    <div style="display:flex; justify-content:space-between; align-items:flex-end; margin-bottom:24px; margin-top:24px; flex-wrap:wrap; gap:12px;">
      <div>
        <div class="section-title">Featured Grants This Week</div>
        <div class="section-sub">Top opportunities matched across all sectors in Kenya</div>
      </div>
      <button class="btn btn-primary btn-sm" onclick="showPage('grants')">View All Grants</button>
    </div>
    <div class="grants-grid" id="featured-grants"></div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════════════════════════════ -->
<!-- GRANTS PAGE -->
<!-- ══════════════════════════════════════════════════════════════════════════ -->
<div id="page-grants" class="page">
  <div class="section">
    <div class="section-title">Browse Active Grants — Kenya</div>
    <div class="section-sub">All amounts in Kenyan Shillings (KSh). Expired grants are automatically hidden.</div>

    <div class="search-bar">
      <input type="text" id="search-input" placeholder="🔍  Search by name or organization..." oninput="filterGrants()">
      <select id="filter-sector" onchange="filterGrants()">
        <option value="">All Sectors</option>
        <option value="Technology">Technology</option>
        <option value="Agriculture">Agriculture</option>
        <option value="Community">Community Development</option>
        <option value="Climate">Climate / Environment</option>
        <option value="Women">Women-Led</option>
        <option value="Health">Health</option>
        <option value="All sectors">All Sectors</option>
      </select>
      <select id="filter-priority" onchange="filterGrants()">
        <option value="">All Priorities</option>
        <option value="HIGH">High Priority</option>
        <option value="MEDIUM">Medium Priority</option>
        <option value="LOW">Low Priority</option>
      </select>
      <select id="filter-status" onchange="filterGrants()">
        <option value="">All Deadlines</option>
        <option value="urgent">Closing Soon (&lt;30 days)</option>
        <option value="rolling">Rolling / Ongoing</option>
        <option value="open">Open (30+ days)</option>
      </select>
      <button class="btn btn-primary btn-sm" onclick="filterGrants()">Search</button>
    </div>

    <div id="grants-count" style="font-size:0.85rem; color:var(--muted); margin-bottom:16px;"></div>
    <div class="grants-grid" id="all-grants"></div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════════════════════════════ -->
<!-- REGISTER PAGE -->
<!-- ══════════════════════════════════════════════════════════════════════════ -->
<div id="page-register" class="page">
  <div class="section" style="max-width:700px; margin:0 auto;">
    <div class="register-wrap">
      <div class="register-header">
        <div style="font-size:0.78rem; letter-spacing:2px; opacity:0.7; margin-bottom:10px;">CLIENT REGISTRATION</div>
        <h2>Get Matched to Grants That Fit You</h2>
        <p>Register once. We'll send you alerts for grants that match your sector — 60 days and 30 days before each deadline.</p>
      </div>
      <div class="register-body">
        <div id="reg-form">
          <div class="field-group">
            <label>Full Name *</label>
            <input type="text" id="reg-name" placeholder="e.g. Rachel Mugisha">
          </div>
          <div class="field-group">
            <label>Email Address *</label>
            <input type="email" id="reg-email" placeholder="your@email.com">
          </div>
          <div class="field-group">
            <label>Phone Number (for SMS alerts)</label>
            <input type="tel" id="reg-phone" placeholder="+254 700 000 000">
          </div>
          <div class="field-group">
            <label>Organization Name</label>
            <input type="text" id="reg-org" placeholder="Your startup, NGO, or group name">
          </div>
          <div class="field-group">
            <label>Organization Type *</label>
            <select id="reg-type">
              <option value="">Select type...</option>
              <option>Individual Entrepreneur</option>
              <option>Youth Group</option>
              <option>NGO / CBO</option>
              <option>Social Enterprise</option>
              <option>SME / Startup</option>
              <option>Women-Led Organization</option>
              <option>Faith-Based Organization</option>
              <option>School / STEM Group</option>
            </select>
          </div>
          <div class="field-group">
            <label>County (Kenya)</label>
            <select id="reg-county">
              <option value="">Select county...</option>
              <option>Nairobi</option><option>Mombasa</option><option>Kisumu</option>
              <option>Nakuru</option><option>Eldoret / Uasin Gishu</option>
              <option>Kiambu</option><option>Machakos</option><option>Meru</option>
              <option>Kilifi</option><option>Kisii</option><option>Bungoma</option>
              <option>Other / Nationwide</option>
            </select>
          </div>
          <div class="field-group">
            <label>Select Your Sectors of Interest * (choose all that apply)</label>
            <div class="interest-grid">
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">💻</span><span>Technology / Digital</span>
                <input type="checkbox" value="Technology">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">🌾</span><span>Agriculture / Agribusiness</span>
                <input type="checkbox" value="Agriculture">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">🤝</span><span>Community Development</span>
                <input type="checkbox" value="Community">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">🌍</span><span>Climate / Environment</span>
                <input type="checkbox" value="Climate">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">👩‍💼</span><span>Women Empowerment</span>
                <input type="checkbox" value="Women">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">🏥</span><span>Health / Nutrition</span>
                <input type="checkbox" value="Health">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">📚</span><span>Education / STEM</span>
                <input type="checkbox" value="Education">
              </div>
              <div class="interest-item" onclick="toggleInterest(this)">
                <span class="interest-icon">💰</span><span>All Grants (any sector)</span>
                <input type="checkbox" value="All">
              </div>
            </div>
          </div>
          <button class="submit-btn" onclick="submitRegistration()">Register & Get Alerts →</button>
          <p style="font-size:0.78rem; color:var(--muted); margin-top:10px; text-align:center;">
            No spam. You'll only receive emails matching your selected sectors.
          </p>
        </div>
        <div class="success-banner" id="reg-success">
          <div style="font-size:2.5rem; margin-bottom:12px;">✅</div>
          <h3>You're registered!</h3>
          <p>You'll receive grant alerts matching your sectors — 60 days and 30 days before each deadline.<br><br>
          Check the <strong>Admin Panel</strong> to see your registration in the client database.</p>
          <button class="btn btn-primary btn-sm" style="margin-top:16px;" onclick="showPage('grants')">Browse Grants Now</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════════════════════════════ -->
<!-- HOW IT WORKS PAGE -->
<!-- ══════════════════════════════════════════════════════════════════════════ -->
<div id="page-about" class="page">
  <div class="section">
    <div class="section-title">How GrantWatch Kenya Works</div>
    <div class="section-sub">A fully automated pipeline — from grant discovery to personalized email alerts</div>

    <div class="how-steps">
      <div class="how-step">
        <div class="step-num">1</div>
        <h4>Manus AI Searches</h4>
        <p>Manus AI scans grant databases, NGO portals, and funding websites weekly — finding active Kenya grants and structuring the results.</p>
      </div>
      <div class="how-step">
        <div class="step-num">2</div>
        <h4>Google Sheets Updated</h4>
        <p>Scraped data is summarized by the LLM and entered into the central Google Sheet — the master database for the whole system.</p>
      </div>
      <div class="how-step">
        <div class="step-num">3</div>
        <h4>Website Pulls Live Data</h4>
        <p>This website reads directly from the Google Sheet. Expired grants are automatically hidden. Fresh grants appear without manual updates.</p>
      </div>
      <div class="how-step">
        <div class="step-num">4</div>
        <h4>Clients Register by Sector</h4>
        <p>Users register their interests (Agriculture, Tech, NGO, STEM, etc.) via the registration form, stored in the Client Management System.</p>
      </div>
      <div class="how-step">
        <div class="step-num">5</div>
        <h4>Targeted Email Alerts</h4>
        <p>Apps Script matches client sectors to relevant grants and sends personalized email reminders at 60 days and 30 days before each deadline.</p>
      </div>
    </div>

    <div style="margin-top:40px;">
      <div class="section-title" style="font-size:1.2rem;">Tools Powering This System</div>
      <div class="tools-row">
        <div class="tool-chip"><span class="tool-icon">🤖</span> Manus AI — Grant Discovery</div>
        <div class="tool-chip"><span class="tool-icon">📊</span> Google Sheets — Central Database</div>
        <div class="tool-chip"><span class="tool-icon">⚙️</span> Apps Script — Automation & Alerts</div>
        <div class="tool-chip"><span class="tool-icon">📧</span> Gmail / Mailchimp — Email Delivery</div>
        <div class="tool-chip"><span class="tool-icon">🧠</span> LLM (Claude/Gemini) — Summarization</div>
        <div class="tool-chip"><span class="tool-icon">🐍</span> Python — Web Scraping</div>
      </div>
    </div>

    <div style="margin-top:36px; background:var(--white); border-radius:var(--radius); padding:24px; box-shadow:var(--shadow);">
      <div class="section-title" style="font-size:1.1rem; margin-bottom:16px;">Data Flow</div>
      <div style="font-size:0.9rem; line-height:2; color:var(--text);">
        <div>🐍 <strong>Python scraper</strong> collects grants from Funds for NGOs, Fuzu, JobWeb, Remotivate</div>
        <div style="padding-left:24px; color:var(--muted);">↓</div>
        <div>🧠 <strong>Gemini / Claude</strong> summarizes and formats each grant into the correct column structure</div>
        <div style="padding-left:24px; color:var(--muted);">↓</div>
        <div>📊 <strong>Google Sheet</strong> receives the structured data — master database updated</div>
        <div style="padding-left:24px; color:var(--muted);">↓</div>
        <div>⚙️ <strong>Apps Script</strong> hides expired grants, checks deadlines daily, fires Gmail alerts</div>
        <div style="padding-left:24px; color:var(--muted);">↓</div>
        <div>🌐 <strong>Website</strong> pulls live data — users always see current, active opportunities</div>
        <div style="padding-left:24px; color:var(--muted);">↓</div>
        <div>📧 <strong>Personalized emails</strong> sent to matched clients at 60 days and 30 days before deadline</div>
      </div>
    </div>

    <div style="margin-top:32px; background:var(--light); border-radius:var(--radius); padding:24px;">
      <div class="section-title" style="font-size:1.1rem; margin-bottom:12px;">Cost & Sustainability</div>
      <div style="display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:14px;">
        <div style="text-align:center;"><strong style="font-size:1.4rem; color:var(--navy);">~KSh 1,000</strong><div style="font-size:0.8rem; color:var(--muted);">per month (Gemini API)</div></div>
        <div style="text-align:center;"><strong style="font-size:1.4rem; color:var(--navy);">Free</strong><div style="font-size:0.8rem; color:var(--muted);">Google Sheets, Forms, Script</div></div>
        <div style="text-align:center;"><strong style="font-size:1.4rem; color:var(--navy);">Free</strong><div style="font-size:0.8rem; color:var(--muted);">Gmail up to 500 emails/day</div></div>
        <div style="text-align:center;"><strong style="font-size:1.4rem; color:var(--navy);">Weekly</strong><div style="font-size:0.8rem; color:var(--muted);">Automatic grant updates</div></div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════════════════════════════ -->
<!-- ADMIN PANEL -->
<!-- ══════════════════════════════════════════════════════════════════════════ -->
<div id="page-admin" class="page">
  <div class="section" style="max-width:1100px;">
    <div class="section-title">Admin Panel</div>
    <div class="section-sub">Grant Management System + Client Management System</div>

    <div class="kpi-row">
      <div class="kpi"><div class="kpi-val" id="kpi-grants">15</div><div class="kpi-lbl">Active Grants</div></div>
      <div class="kpi gold"><div class="kpi-val" id="kpi-urgent-admin">3</div><div class="kpi-lbl">Closing &lt;30 Days</div></div>
      <div class="kpi green"><div class="kpi-val" id="kpi-clients-admin">0</div><div class="kpi-lbl">Registered Clients</div></div>
      <div class="kpi red"><div class="kpi-val" id="kpi-expired">0</div><div class="kpi-lbl">Hidden (Expired)</div></div>
    </div>

    <div class="tab-bar">
      <button class="tab-btn active" onclick="adminTab('grants-tab',this)">📋 Grant Management</button>
      <button class="tab-btn" onclick="adminTab('clients-tab',this)">👥 Client Management</button>
      <button class="tab-btn" onclick="adminTab('alerts-tab',this)">📧 Email Alerts</button>
      <button class="tab-btn" onclick="adminTab('script-tab',this)">⚙️ Apps Script Code</button>
    </div>

    <!-- GRANTS TAB -->
    <div id="grants-tab" class="admin-tab">
      <div class="admin-card">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:16px;">
          <h3 style="border:none; padding:0; margin:0;">All Grants in System</h3>
          <button class="btn btn-primary btn-sm" onclick="openAddGrant()">+ Add New Grant</button>
        </div>
        <div style="overflow-x:auto;">
          <table class="data-table" id="admin-grants-table">
            <thead>
              <tr>
                <th>#</th><th>Grant Name</th><th>Organization</th>
                <th>Amount (KSh)</th><th>Deadline</th><th>Sector</th>
                <th>Days Left</th><th>Priority</th><th>Status</th><th>Action</th>
              </tr>
            </thead>
            <tbody id="admin-grants-body"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- CLIENTS TAB -->
    <div id="clients-tab" class="admin-tab" style="display:none;">
      <div class="admin-card">
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:16px;">
          <h3 style="border:none; padding:0; margin:0;">Registered Clients</h3>
          <div style="font-size:0.83rem; color:var(--muted);" id="client-count-label">0 clients registered</div>
        </div>
        <div id="no-clients" style="text-align:center; padding:40px; color:var(--muted);">
          <div style="font-size:2.5rem; margin-bottom:12px;">👥</div>
          <p>No clients registered yet.</p>
          <p style="font-size:0.85rem; margin-top:6px;">Share the registration link to start building your client database.</p>
          <button class="btn btn-primary btn-sm" style="margin-top:14px;" onclick="showPage('register')">Go to Registration Form</button>
        </div>
        <div style="overflow-x:auto; display:none;" id="clients-table-wrap">
          <table class="data-table">
            <thead>
              <tr><th>#</th><th>Name</th><th>Email</th><th>Org Type</th><th>County</th><th>Sectors</th><th>Registered</th></tr>
            </thead>
            <tbody id="clients-body"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ALERTS TAB -->
    <div id="alerts-tab" class="admin-tab" style="display:none;">
      <div class="admin-card">
        <h3>Email Alert Logic</h3>
        <div class="alert alert-info" style="margin-bottom:20px;">
          ℹ️ Alerts are sent automatically by Google Apps Script. The logic below shows how clients are matched to grants.
        </div>
        <div style="background:var(--offwhite); border-radius:8px; padding:20px; font-size:0.88rem; line-height:2;">
          <div><strong>Trigger:</strong> Script runs daily at 8:00 AM (East Africa Time)</div>
          <div><strong>Alert 1:</strong> Sent when a grant is exactly 60 days from deadline</div>
          <div><strong>Alert 2:</strong> Sent when a grant is exactly 30 days from deadline</div>
          <div><strong>Matching logic:</strong> Client sector interests (from registration) matched against grant sector column</div>
          <div><strong>Email content:</strong> Grant name, amount, deadline, eligibility summary, direct application link</div>
          <div><strong>Rolling grants:</strong> Alert sent once per month for rolling-deadline grants</div>
          <div><strong>Expired grants:</strong> Automatically hidden from website — no alerts sent</div>
        </div>

        <div style="margin-top:24px;">
          <div style="font-weight:700; color:var(--navy); margin-bottom:12px;">Simulate Alert Preview</div>
          <div style="background:var(--white); border:1.5px solid var(--border); border-radius:8px; padding:20px; font-size:0.87rem; font-family:monospace; line-height:1.8;">
            <div style="color:var(--muted);">From: grantwatch.kenya@gmail.com</div>
            <div style="color:var(--muted);">To: client@email.com</div>
            <div style="color:var(--muted);">Subject: ⏰ Grant Alert: Safaricom Spark — 30 Days Left</div>
            <div style="border-top:1px solid var(--border); margin:10px 0; padding-top:10px;">
              Hi Rachel,<br><br>
              A grant matching your <strong>Technology</strong> interest is closing in <strong>30 days.</strong><br><br>
              🏆 <strong>Safaricom Spark Accelerator</strong><br>
              💰 Up to KSh 3,900,000<br>
              📅 Deadline: 15 July 2026<br>
              ✅ Eligibility: Kenyan tech startups, mobile-first, 18–35 yrs<br><br>
              👉 Apply here: safaricom.co.ke/spark<br><br>
              — GrantWatch Kenya Team
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- SCRIPT TAB -->
    <div id="script-tab" class="admin-tab" style="display:none;">
      <div class="admin-card">
        <h3>Google Apps Script — Full Code</h3>
        <div class="alert alert-info" style="margin-bottom:16px;">
          📋 Copy this code into your Google Sheet → Extensions → Apps Script → Paste → Save → Run
        </div>
        <pre style="background:#1E293B; color:#E2E8F0; border-radius:8px; padding:20px; font-size:0.78rem; line-height:1.7; overflow-x:auto; white-space:pre-wrap;"><code>// ─── GrantWatch Kenya — Google Apps Script ─────────────────────────────────
// Paste this in: Google Sheet → Extensions → Apps Script
// Set a daily trigger on checkDeadlinesAndAlert()

const SHEET_NAME = "Grant Tracker";
const CLIENT_SHEET = "Client Database";
const SENDER_EMAIL = "grantwatch.kenya@gmail.com";

// ── 1. HIDE EXPIRED GRANTS ──────────────────────────────────────────────────
function hideExpiredGrants() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const ws = ss.getSheetByName(SHEET_NAME);
  const data = ws.getDataRange().getValues();
  const today = new Date();
  today.setHours(0, 0, 0, 0);

  for (let i = 1; i < data.length; i++) {
    const deadline = data[i][4]; // Column E = Deadline
    if (deadline instanceof Date && deadline < today) {
      ws.hideRows(i + 1); // Hide the row
      ws.getRange(i + 1, 12).setValue("Expired"); // Update Status column
    } else if (typeof deadline === "string" &&
               !deadline.toLowerCase().includes("rolling")) {
      const parsed = new Date(deadline);
      if (!isNaN(parsed) && parsed < today) {
        ws.hideRows(i + 1);
        ws.getRange(i + 1, 12).setValue("Expired");
      }
    }
  }
  Logger.log("Expired grants hidden successfully.");
}

// ── 2. CALCULATE DAYS UNTIL DEADLINE ───────────────────────────────────────
function updateDaysLeft() {
  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const ws = ss.getSheetByName(SHEET_NAME);
  const data = ws.getDataRange().getValues();
  const today = new Date();
  today.setHours(0, 0, 0, 0);

  for (let i = 1; i < data.length; i++) {
    const deadline = data[i][4];
    if (typeof deadline === "string" &&
        deadline.toLowerCase().includes("rolling")) {
      ws.getRange(i + 1, 10).setValue("Rolling");
    } else {
      const dl = new Date(deadline);
      if (!isNaN(dl)) {
        const diff = Math.ceil((dl - today) / (1000 * 60 * 60 * 24));
        ws.getRange(i + 1, 10).setValue(diff > 0 ? diff : "Expired");
      }
    }
  }
}

// ── 3. SEND DEADLINE ALERT EMAILS ──────────────────────────────────────────
function checkDeadlinesAndAlert() {
  hideExpiredGrants();
  updateDaysLeft();

  const ss = SpreadsheetApp.getActiveSpreadsheet();
  const grantWs = ss.getSheetByName(SHEET_NAME);
  const clientWs = ss.getSheetByName(CLIENT_SHEET);

  const grants = grantWs.getDataRange().getValues().slice(1);
  const clients = clientWs.getDataRange().getValues().slice(1);
  const today = new Date();
  today.setHours(0, 0, 0, 0);

  grants.forEach(grant => {
    const [, name, org, amount, deadline, eligibility, sector,
           region, link, daysLeft, priority, status] = grant;

    if (status === "Expired" || !daysLeft) return;

    const alertDays = [60, 30];
    if (!alertDays.includes(Number(daysLeft)) &&
        !(typeof deadline === "string" &&
          deadline.toLowerCase().includes("rolling"))) return;

    // Match clients by sector
    clients.forEach(client => {
      const [, cName, cEmail, , cType, cCounty, cSectors] = client;
      if (!cEmail) return;

      const clientSectors = String(cSectors).toLowerCase();
      const grantSector = String(sector).toLowerCase();
      const isMatch = clientSectors.includes("all") ||
                      clientSectors.includes(grantSector.split("/")[0].trim()) ||
                      grantSector.includes("all");

      if (!isMatch) return;

      const deadlineStr = typeof deadline === "string" ? deadline :
        new Date(deadline).toLocaleDateString("en-KE",
          {day:"2-digit", month:"short", year:"numeric"});

      const subject = `⏰ Grant Alert: ${name} — ${
        typeof daysLeft === "number" ? daysLeft + " Days Left" : "Rolling Deadline"
      }`;

      const body = `
Hi ${cName},

A grant matching your ${cSectors} interest is closing soon.

────────────────────────────────
🏆 ${name}
🏢 ${org}
💰 ${amount}
📅 Deadline: ${deadlineStr}
✅ Eligibility: ${eligibility}
🌍 Region: ${region}
────────────────────────────────

👉 Apply here: ${link}

Need help writing your application? Reply to this email.

— GrantWatch Kenya Team
grantwatch.kenya@gmail.com

To unsubscribe, reply with "UNSUBSCRIBE".
      `.trim();

      GmailApp.sendEmail(cEmail, subject, body);
      Logger.log(`Alert sent to ${cEmail} for grant: ${name}`);
    });
  });
}

// ── 4. WEEKLY GRANT REFRESH REMINDER ───────────────────────────────────────
function weeklyRefreshReminder() {
  const admin = "your-admin@gmail.com"; // Change this
  GmailApp.sendEmail(
    admin,
    "📋 GrantWatch: Time to Run Weekly Grant Search",
    "It's time to run your weekly Manus AI grant search and update the tracker.\n\n" +
    "1. Open Manus AI\n2. Run search: active Kenya grants\n3. Clean results\n4. Paste to Grant Tracker sheet\n\n" +
    "The Apps Script will automatically hide expired grants and send client alerts."
  );
}

// ── 5. SET UP ALL TRIGGERS ──────────────────────────────────────────────────
function setUpTriggers() {
  ScriptApp.newTrigger("checkDeadlinesAndAlert")
    .timeBased().everyDays(1).atHour(8).create();

  ScriptApp.newTrigger("weeklyRefreshReminder")
    .timeBased().everyWeeks(1).onWeekDay(ScriptApp.WeekDay.MONDAY)
    .atHour(7).create();

  Logger.log("All triggers set up successfully.");
}
// ─── END OF SCRIPT ──────────────────────────────────────────────────────────</code></pre>
        <button class="btn btn-primary btn-sm" style="margin-top:14px;"
          onclick="copyScript()">📋 Copy Script</button>
        <span id="copy-confirm" style="font-size:0.83rem; color:var(--green); margin-left:10px; display:none;">✅ Copied!</span>
      </div>
    </div>
  </div>
</div>

<!-- ── ADD GRANT MODAL ────────────────────────────────────────────────────── -->
<div class="modal-overlay" id="add-grant-modal">
  <div class="modal">
    <div class="modal-header">
      <h2>Add New Grant</h2>
      <button class="modal-close" onclick="closeModal('add-grant-modal')">✕</button>
    </div>
    <div class="modal-body">
      <div id="modal-form-body">
        <div class="modal-section-title">Grant Details</div>
        <div class="modal-field"><label>Grant Name *</label>
          <input id="m-name" placeholder="Full official grant name"></div>
        <div class="modal-field"><label>Funding Organization *</label>
          <input id="m-org" placeholder="e.g. Safaricom PLC"></div>
        <div class="modal-field"><label>Maximum Amount (KSh) *</label>
          <input id="m-amount" placeholder="e.g. KSh 500,000 – 1,500,000"></div>
        <div class="modal-field"><label>Application Deadline *</label>
          <input id="m-deadline" type="date"></div>
        <div class="modal-field"><label>Sector</label>
          <select id="m-sector">
            <option>Technology</option><option>Agriculture</option>
            <option>Community Development</option><option>Climate</option>
            <option>Women-Led</option><option>Health</option>
            <option>All sectors</option>
          </select></div>
        <div class="modal-field"><label>Eligibility</label>
          <textarea id="m-eligibility" placeholder="Who qualifies for this grant?"></textarea></div>
        <div class="modal-field"><label>Region (Kenya)</label>
          <input id="m-region" placeholder="e.g. Nationwide or Nairobi"></div>
        <div class="modal-field"><label>Application Link *</label>
          <input id="m-link" placeholder="https://..."></div>
        <div class="modal-field"><label>Priority</label>
          <select id="m-priority"><option>HIGH</option><option>MEDIUM</option><option>LOW</option></select></div>
        <button class="btn btn-primary" style="width:100%; margin-top:8px;" onclick="saveGrant()">Add Grant to System</button>
      </div>
      <div id="modal-success" class="form-success">
        <div class="check-icon">✓</div>
        <h3>Grant Added!</h3>
        <p>The grant has been added to the system and will appear on the website immediately.</p>
        <button class="btn btn-primary btn-sm" style="margin-top:12px;" onclick="closeModal('add-grant-modal')">Done</button>
      </div>
    </div>
  </div>
</div>

<!-- ── GRANT DETAIL MODAL ─────────────────────────────────────────────────── -->
<div class="modal-overlay" id="grant-detail-modal">
  <div class="modal">
    <div class="modal-header">
      <div>
        <div id="modal-sector-tag" class="card-sector" style="margin-bottom:8px;"></div>
        <h2 id="modal-title"></h2>
        <div id="modal-org" style="font-size:0.85rem; color:var(--muted); margin-top:4px;"></div>
      </div>
      <button class="modal-close" onclick="closeModal('grant-detail-modal')">✕</button>
    </div>
    <div class="modal-body">
      <div id="modal-amount" style="font-size:1.3rem; font-weight:800; color:var(--teal); margin-bottom:16px;"></div>
      <div class="modal-section-title">Grant Details</div>
      <table style="width:100%; font-size:0.88rem; border-collapse:collapse;">
        <tr><td style="padding:8px 0; color:var(--muted); width:140px;">Deadline</td><td id="modal-deadline" style="font-weight:600;"></td></tr>
        <tr><td style="padding:8px 0; color:var(--muted);">Days Remaining</td><td id="modal-days" style="font-weight:600;"></td></tr>
        <tr><td style="padding:8px 0; color:var(--muted);">Region</td><td id="modal-region"></td></tr>
        <tr><td style="padding:8px 0; color:var(--muted);">Priority</td><td id="modal-priority"></td></tr>
      </table>
      <div class="modal-section-title" style="margin-top:16px;">Eligibility Requirements</div>
      <div id="modal-eligibility" style="font-size:0.88rem; line-height:1.7; color:var(--text);"></div>
      <div style="display:flex; gap:10px; margin-top:20px;">
        <a id="modal-link" href="#" target="_blank" class="btn btn-primary" style="flex:1; text-align:center; justify-content:center;">Apply Now →</a>
        <button class="btn btn-outline" style="flex:1; border-color:var(--border); color:var(--navy);" onclick="showPage('register')">Get Alerts for This Grant</button>
      </div>
    </div>
  </div>
</div>

<footer>
  <p><strong>GrantWatch Kenya</strong> — AI-Powered Grant Discovery & Alerts</p>
  <p>Powered by Manus AI · Google Sheets · Google Apps Script · LLM</p>
  <p style="margin-top:8px; font-size:0.78rem;">AI Project Challenge 2026 · Rachel Mugisha · office@heri.mr.com</p>
</footer>

<script>
// ── DATA ─────────────────────────────────────────────────────────────────────
const GRANTS = [
  {id:1, name:"Uwezo Fund — Youth, Women & PWDs Enterprise Grant", org:"Uwezo Fund (Government of Kenya)", amount:"KSh 50,000 – 500,000", deadline:"Rolling", sector:"All sectors", region:"All 47 Counties", eligibility:"Youth, women & persons with disabilities; group or individual; Kenyan citizen; any sector", link:"https://www.uwezo.go.ke", priority:"HIGH", status:"Active", days:"Rolling"},
  {id:2, name:"Youth Enterprise Development Fund (YEDF)", org:"YEDF — Ministry of Public Service", amount:"KSh 50,000 – 500,000", deadline:"Rolling (quarterly)", sector:"All sectors", region:"All 47 Counties", eligibility:"Kenyan youth aged 18–35; registered business (6+ months operation)", link:"https://www.youthfund.go.ke", priority:"HIGH", status:"Active", days:"Rolling"},
  {id:3, name:"Kenya Climate Innovation Centre (KCIC) — Startup Grant", org:"KCIC / World Bank InfoDev", amount:"KSh 500,000 – 1,500,000", deadline:"30 Aug 2026", sector:"Climate", region:"Nationwide (8 counties priority)", eligibility:"Kenyan entrepreneurs with climate-smart, clean energy or agribusiness solutions", link:"https://www.kenyacic.org", priority:"HIGH", status:"Active", days:85},
  {id:4, name:"Safaricom Spark Accelerator Programme", org:"Safaricom PLC / iHub", amount:"KSh 1,300,000 – 3,900,000", deadline:"15 Jul 2026", sector:"Technology", region:"Nairobi & major counties", eligibility:"Kenyan tech startups; early-stage; mobile-first or digital solutions; 18–35 yrs", link:"https://www.safaricom.co.ke/spark", priority:"HIGH", status:"Active", days:38},
  {id:5, name:"KCIC Agribiz Programme — Women & Youth", org:"KCIC / County Governments", amount:"KSh 200,000 – 800,000", deadline:"01 Sep 2026", sector:"Agriculture", region:"Bungoma, Meru, Kiambu, Machakos, Kisii", eligibility:"Women entrepreneurs & youth in agribusiness; 51% women ownership preferred", link:"https://www.kenyacic.org/agribiz", priority:"HIGH", status:"Active", days:87},
  {id:6, name:"Youth Empowerment Fund (YEF) — SDG Youth Grant", org:"Youth Empowerment Fund International", amount:"KSh 75,000 – 225,000", deadline:"31 Aug 2026", sector:"Community", region:"Nationwide", eligibility:"Kenyan youth aged 18–35; projects addressing SDGs; under-represented communities", link:"https://www.youthempowermentfund.org", priority:"MEDIUM", status:"Active", days:86},
  {id:7, name:"Orange Corners Kenya Innovation Fund", org:"Orange Corners / Dutch Embassy", amount:"KSh 1,550,000", deadline:"20 Aug 2026", sector:"All sectors", region:"Nairobi", eligibility:"Kenyan young entrepreneurs aged 18–35 with a scalable business idea", link:"https://orangecorners.com/kenya", priority:"MEDIUM", status:"Active", days:75},
  {id:8, name:"WIDU Africa — Diaspora-Supported Business Grant", org:"WIDU / GIZ / EU", amount:"KSh 390,000 – 650,000", deadline:"Rolling", sector:"All sectors", region:"Nationwide", eligibility:"Kenyan entrepreneurs supported by a relative in an EU/Swiss/Norwegian country", link:"https://widu.africa/kenya", priority:"MEDIUM", status:"Active", days:"Rolling"},
  {id:9, name:"KIRDI/KIEP — SME Innovation & Incubation Grant", org:"KIRDI / Kenya Industry & Entrepreneurship Project", amount:"KSh 300,000 – 1,200,000", deadline:"01 Oct 2026", sector:"Technology", region:"Nairobi, Kisumu, Migori, Kisii, Uasin Gishu, Bungoma, Garissa, Kilifi", eligibility:"Kenyan MSMEs in manufacturing, ICT, agro-processing, energy or textile sectors", link:"https://www.kiep.go.ke", priority:"MEDIUM", status:"Active", days:116},
  {id:10, name:"Women Enterprise Fund (WEF)", org:"Women Enterprise Fund (Government of Kenya)", amount:"KSh 50,000 – 500,000", deadline:"Rolling", sector:"Women", region:"All 47 Counties", eligibility:"Women entrepreneurs in Kenya; group or individual; any sector", link:"https://www.wef.co.ke", priority:"HIGH", status:"Active", days:"Rolling"},
  {id:11, name:"Humanity Calls International — Individual Grant", org:"Humanity Calls International", amount:"KSh 65,000 – 2,600,000", deadline:"Rolling", sector:"Community", region:"Nationwide", eligibility:"Individuals, CBOs, NGOs, faith-based organizations; community development focus", link:"https://humanitycallsinternational.org/grants-in-kenya", priority:"MEDIUM", status:"Active", days:"Rolling"},
  {id:12, name:"Mastercard Foundation — Young Africa Works Kenya", org:"Mastercard Foundation", amount:"KSh 3,900,000 – 6,500,000", deadline:"30 Sep 2026", sector:"Community", region:"Nationwide (priority: rural counties)", eligibility:"Organizations enabling dignified work for young Kenyans; NGOs, social enterprises", link:"https://mastercardfdn.org", priority:"MEDIUM", status:"Active", days:115},
  {id:13, name:"Public Diplomacy Small Grants — Kenya", org:"U.S. Embassy Nairobi", amount:"KSh 5,200,000", deadline:"31 Jul 2026", sector:"Community", region:"Nationwide", eligibility:"Kenyan organizations promoting education, civic engagement, and entrepreneurship", link:"https://ke.usembassy.gov/grants", priority:"LOW", status:"Active", days:54},
  {id:14, name:"Tony Elumelu Foundation Entrepreneurship Programme", org:"Tony Elumelu Foundation", amount:"KSh 650,000", deadline:"31 Mar 2027", sector:"All sectors", region:"Nationwide (Pan-Africa)", eligibility:"African entrepreneurs incl. Kenyans; 18–35 yrs; early-stage startup", link:"https://www.tonyelumelufoundation.org/teep", priority:"MEDIUM", status:"Active", days:297},
  {id:15, name:"iHub Nairobi — Tech Startup Seed Grant", org:"iHub Nairobi", amount:"KSh 260,000 – 1,300,000", deadline:"01 Aug 2026", sector:"Technology", region:"Nairobi", eligibility:"Early-stage Kenyan tech startups; prototype or MVP stage; Nairobi-based preferred", link:"https://www.ihub.co.ke", priority:"HIGH", status:"Active", days:55},
];

let clients = [];
let grantList = [...GRANTS];

// ── PAGE NAVIGATION ───────────────────────────────────────────────────────────
function showPage(id) {
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-links a').forEach(a=>a.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  const navEl = document.getElementById('nav-'+id);
  if(navEl) navEl.classList.add('active');
  window.scrollTo(0,0);
  if(id==='grants') renderAllGrants();
  if(id==='admin') renderAdmin();
}

// ── SECTOR COLOR ─────────────────────────────────────────────────────────────
function sectorClass(s) {
  const m = {'Technology':'sector-tech','Agriculture':'sector-agri',
    'Community':'sector-community','Climate':'sector-climate',
    'Women':'sector-women','Health':'sector-health','All sectors':'sector-all'};
  for(const k in m) if(s.includes(k)) return m[k];
  return 'sector-all';
}

// ── DEADLINE BADGE ────────────────────────────────────────────────────────────
function deadlineBadge(days, deadline) {
  if(days==='Rolling'||String(deadline).toLowerCase().includes('rolling'))
    return `<span class="deadline-badge deadline-rolling">🔄 Rolling</span>`;
  if(typeof days==='number'){
    if(days<=30) return `<span class="deadline-badge deadline-urgent">🔴 ${days} days left</span>`;
    if(days<=60) return `<span class="deadline-badge deadline-soon">🟡 ${days} days left</span>`;
    return `<span class="deadline-badge deadline-ok">🟢 ${days} days left</span>`;
  }
  return `<span class="deadline-badge deadline-rolling">${deadline}</span>`;
}

// ── RENDER GRANT CARD ─────────────────────────────────────────────────────────
function grantCard(g) {
  return `
  <div class="grant-card">
    <div class="card-top">
      <div class="card-sector ${sectorClass(g.sector)}">${g.sector}</div>
      <div class="card-title">${g.name}</div>
      <div class="card-org">${g.org}</div>
    </div>
    <div class="card-body">
      <div class="card-amount">${g.amount}</div>
      <div class="card-meta">
        <span>📅 ${g.deadline}</span>
        <span>📍 ${g.region}</span>
        ${deadlineBadge(g.days, g.deadline)}
      </div>
    </div>
    <div class="card-footer">
      <button class="btn-apply" onclick='openGrantDetail(${JSON.stringify(g).replace(/'/g,"&#39;")})'>View & Apply</button>
      <button class="btn-save" onclick="showPage('register')">Get Alerts</button>
    </div>
  </div>`;
}

// ── FEATURED GRANTS ───────────────────────────────────────────────────────────
function renderFeatured() {
  const featured = grantList.filter(g=>g.priority==='HIGH').slice(0,6);
  document.getElementById('featured-grants').innerHTML = featured.map(grantCard).join('');
}

// ── ALL GRANTS ────────────────────────────────────────────────────────────────
function renderAllGrants(list=null) {
  const data = list || grantList;
  document.getElementById('all-grants').innerHTML = data.map(grantCard).join('');
  document.getElementById('grants-count').textContent =
    `Showing ${data.length} of ${grantList.length} grants`;
}

function filterGrants() {
  const q = document.getElementById('search-input').value.toLowerCase();
  const sec = document.getElementById('filter-sector').value;
  const pri = document.getElementById('filter-priority').value;
  const sta = document.getElementById('filter-status').value;
  const res = grantList.filter(g=>{
    const matchQ = !q || g.name.toLowerCase().includes(q) || g.org.toLowerCase().includes(q);
    const matchS = !sec || g.sector.includes(sec);
    const matchP = !pri || g.priority===pri;
    let matchSt = true;
    if(sta==='urgent') matchSt = typeof g.days==='number' && g.days<=30;
    else if(sta==='rolling') matchSt = g.days==='Rolling';
    else if(sta==='open') matchSt = typeof g.days==='number' && g.days>30;
    return matchQ&&matchS&&matchP&&matchSt;
  });
  renderAllGrants(res);
}

// ── GRANT DETAIL MODAL ────────────────────────────────────────────────────────
function openGrantDetail(g) {
  document.getElementById('modal-title').textContent = g.name;
  document.getElementById('modal-org').textContent = g.org;
  document.getElementById('modal-amount').textContent = g.amount;
  document.getElementById('modal-deadline').textContent = g.deadline;
  document.getElementById('modal-days').innerHTML = deadlineBadge(g.days, g.deadline);
  document.getElementById('modal-region').textContent = g.region;
  document.getElementById('modal-priority').textContent = g.priority;
  document.getElementById('modal-eligibility').textContent = g.eligibility;
  document.getElementById('modal-link').href = g.link;
  const tag = document.getElementById('modal-sector-tag');
  tag.textContent = g.sector;
  tag.className = 'card-sector ' + sectorClass(g.sector);
  document.getElementById('grant-detail-modal').classList.add('open');
}

// ── ADD GRANT ─────────────────────────────────────────────────────────────────
function openAddGrant() {
  document.getElementById('modal-form-body').style.display='block';
  document.getElementById('modal-success').style.display='none';
  document.getElementById('add-grant-modal').classList.add('open');
}

function saveGrant() {
  const name = document.getElementById('m-name').value;
  const org = document.getElementById('m-org').value;
  const amount = document.getElementById('m-amount').value;
  const deadline = document.getElementById('m-deadline').value;
  const sector = document.getElementById('m-sector').value;
  const eligibility = document.getElementById('m-eligibility').value;
  const region = document.getElementById('m-region').value;
  const link = document.getElementById('m-link').value;
  const priority = document.getElementById('m-priority').value;
  if(!name||!org||!amount||!deadline||!link){
    alert('Please fill in all required fields.'); return;
  }
  const today = new Date(); today.setHours(0,0,0,0);
  const dl = new Date(deadline);
  const days = Math.ceil((dl-today)/(1000*60*60*24));
  const dlStr = dl.toLocaleDateString('en-GB',{day:'2-digit',month:'short',year:'numeric'});
  const newGrant = {id:grantList.length+1,name,org,amount,deadline:dlStr,
    sector,region,eligibility,link,priority,status:'Active',days};
  grantList.push(newGrant);
  document.getElementById('modal-form-body').style.display='none';
  document.getElementById('modal-success').style.display='block';
  document.getElementById('kpi-grants').textContent = grantList.length;
  document.getElementById('stat-total').textContent = grantList.length;
  renderAdmin();
}

// ── MODALS ────────────────────────────────────────────────────────────────────
function closeModal(id) {
  document.getElementById(id).classList.remove('open');
}
document.querySelectorAll('.modal-overlay').forEach(m=>{
  m.addEventListener('click', e=>{ if(e.target===m) m.classList.remove('open'); });
});

// ── REGISTRATION ──────────────────────────────────────────────────────────────
function toggleInterest(el) {
  el.classList.toggle('selected');
  el.querySelector('input').checked = el.classList.contains('selected');
}

function submitRegistration() {
  const name = document.getElementById('reg-name').value;
  const email = document.getElementById('reg-email').value;
  const phone = document.getElementById('reg-phone').value;
  const org = document.getElementById('reg-org').value;
  const type = document.getElementById('reg-type').value;
  const county = document.getElementById('reg-county').value;
  const interests = [...document.querySelectorAll('.interest-item.selected')]
    .map(el=>el.querySelector('input').value).join(', ');

  if(!name||!email||!type) { alert('Please fill in Name, Email, and Organization Type.'); return; }
  if(!interests) { alert('Please select at least one sector of interest.'); return; }

  clients.push({name,email,phone,org,type,county,sectors:interests,
    date:new Date().toLocaleDateString('en-GB')});

  document.getElementById('reg-form').style.display='none';
  document.getElementById('reg-success').style.display='block';
  document.getElementById('stat-clients').textContent = clients.length;
  document.getElementById('kpi-clients-admin').textContent = clients.length;
  renderClientsTable();
}

// ── ADMIN ─────────────────────────────────────────────────────────────────────
function adminTab(id, btn) {
  document.querySelectorAll('.admin-tab').forEach(t=>t.style.display='none');
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById(id).style.display='block';
  btn.classList.add('active');
}

function renderAdmin() {
  const tbody = document.getElementById('admin-grants-body');
  const urgent = grantList.filter(g=>typeof g.days==='number'&&g.days<=30).length;
  document.getElementById('kpi-urgent-admin').textContent = urgent;
  document.getElementById('stat-urgent').textContent = urgent;

  tbody.innerHTML = grantList.map((g,i)=>`
    <tr>
      <td>${g.id}</td>
      <td style="font-weight:600; max-width:200px;">${g.name}</td>
      <td>${g.org}</td>
      <td style="font-weight:700; color:var(--teal);">${g.amount}</td>
      <td>${g.deadline}</td>
      <td><span class="card-sector ${sectorClass(g.sector)}" style="display:inline-block;padding:2px 8px;font-size:0.72rem;border-radius:20px;">${g.sector}</span></td>
      <td style="font-weight:700; color:${typeof g.days==='number'&&g.days<=30?'var(--red)':typeof g.days==='number'&&g.days<=60?'var(--yellow)':'var(--green)'};">
        ${g.days}</td>
      <td><span class="status-pill ${g.priority==='HIGH'?'pill-active':g.priority==='LOW'?'pill-expired':'pill-pending'}">${g.priority}</span></td>
      <td><span class="status-pill pill-active">Active</span></td>
      <td><button class="btn btn-sm" style="background:var(--light);color:var(--navy);border:none;cursor:pointer;border-radius:5px;padding:5px 10px;" onclick='openGrantDetail(${JSON.stringify(g)})'>View</button></td>
    </tr>`).join('');
}

function renderClientsTable() {
  const wrap = document.getElementById('clients-table-wrap');
  const noClients = document.getElementById('no-clients');
  const label = document.getElementById('client-count-label');
  label.textContent = `${clients.length} client${clients.length!==1?'s':''} registered`;

  if(clients.length===0){ noClients.style.display='block'; wrap.style.display='none'; return; }
  noClients.style.display='none'; wrap.style.display='block';

  document.getElementById('clients-body').innerHTML = clients.map((c,i)=>`
    <tr>
      <td>${i+1}</td>
      <td style="font-weight:600;">${c.name}</td>
      <td><a href="mailto:${c.email}" style="color:var(--teal);">${c.email}</a></td>
      <td>${c.type}</td>
      <td>${c.county||'—'}</td>
      <td style="max-width:180px; font-size:0.82rem;">${c.sectors}</td>
      <td style="color:var(--muted); font-size:0.82rem;">${c.date}</td>
    </tr>`).join('');
}

// ── COPY SCRIPT ───────────────────────────────────────────────────────────────
function copyScript() {
  const code = document.querySelector('#script-tab code').textContent;
  navigator.clipboard.writeText(code).then(()=>{
    const el = document.getElementById('copy-confirm');
    el.style.display='inline'; setTimeout(()=>el.style.display='none', 2500);
  });
}

// ── INIT ──────────────────────────────────────────────────────────────────────
renderFeatured();
renderAllGrants();
renderAdmin();
</script>
</body>
</html>
