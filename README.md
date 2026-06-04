<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Above & Beyond Voyagers | Flight Planning Singapore</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,300;1,400;1,600&family=Cinzel:wght@400;500;600;700&family=Jost:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }

  :root {
    --navy:      #0b1a2e;
    --navy-mid:  #112240;
    --navy-lite: #1a3358;
    --gold:      #b8953f;
    --gold-b:    #d4af5a;
    --gold-pale: #e8d49a;
    --cream:     #faf8f4;
    --white:     #ffffff;
    --muted:     #7a8fa8;
    --text:      #2c3e50;
    --border:    rgba(184,149,63,0.18);
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Jost', sans-serif;
    background: var(--cream);
    color: var(--text);
    overflow-x: hidden;
  }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--navy); }
  ::-webkit-scrollbar-thumb { background: var(--gold); }

  /* ── NAV ── */
  nav {
    position: fixed; top:0; left:0; right:0; z-index:100;
    display: flex; align-items:center; justify-content:space-between;
    padding: 0 5vw;
    height: 70px;
    background: rgba(11,26,46,0.97);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    transition: all 0.3s;
  }
  .nav-brand {
    display: flex; flex-direction:column;
  }
  .nav-brand-main {
    font-family: 'Cormorant Garamond', serif;
    font-size: 18px; font-weight:600; font-style:italic;
    color: var(--cream); letter-spacing:0.5px;
  }
  .nav-brand-main span { color: var(--gold-b); }
  .nav-brand-sub {
    font-family:'Cinzel',serif; font-size:7px;
    letter-spacing:3px; color:var(--muted); text-transform:uppercase;
  }
  .nav-links {
    display:flex; gap:32px; list-style:none;
  }
  .nav-links a {
    font-family:'Cinzel',serif; font-size:9px; letter-spacing:2px;
    color:var(--muted); text-transform:uppercase; text-decoration:none;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: var(--gold-b); }
  .nav-cta {
    font-family:'Cinzel',serif; font-size:9px; letter-spacing:2px;
    color:var(--navy); background: var(--gold);
    padding: 10px 20px; text-transform:uppercase;
    text-decoration:none; transition: all 0.3s;
    border:1px solid var(--gold);
  }
  .nav-cta:hover { background:transparent; color:var(--gold); }

  .hamburger {
    display:none; flex-direction:column; gap:5px; cursor:pointer; background:none; border:none; padding:4px;
  }
  .hamburger span { width:22px; height:1.5px; background:var(--gold); display:block; transition:all 0.3s; }

  /* ── HERO ── */
  #home {
    min-height: 100vh;
    background: var(--navy);
    display: flex; align-items:center; justify-content:center;
    position: relative; overflow:hidden;
    padding: 100px 5vw 60px;
    text-align: center;
  }

  /* Star field */
  .stars {
    position:absolute; inset:0; pointer-events:none;
    background-image:
      radial-gradient(1px 1px at 15% 25%, rgba(255,255,255,0.4) 0%, transparent 100%),
      radial-gradient(1px 1px at 45% 15%, rgba(255,255,255,0.3) 0%, transparent 100%),
      radial-gradient(1px 1px at 70% 35%, rgba(255,255,255,0.35) 0%, transparent 100%),
      radial-gradient(1px 1px at 85% 60%, rgba(255,255,255,0.25) 0%, transparent 100%),
      radial-gradient(1px 1px at 30% 70%, rgba(255,255,255,0.3) 0%, transparent 100%),
      radial-gradient(1px 1px at 55% 80%, rgba(255,255,255,0.2) 0%, transparent 100%),
      radial-gradient(1px 1px at 10% 55%, rgba(255,255,255,0.25) 0%, transparent 100%),
      radial-gradient(1px 1px at 92% 20%, rgba(255,255,255,0.35) 0%, transparent 100%),
      radial-gradient(1.5px 1.5px at 60% 50%, rgba(184,149,63,0.3) 0%, transparent 100%),
      radial-gradient(1.5px 1.5px at 25% 40%, rgba(184,149,63,0.2) 0%, transparent 100%);
  }

  /* Radial glow */
  .hero-glow {
    position:absolute; top:-10%; left:50%; transform:translateX(-50%);
    width:800px; height:500px; pointer-events:none;
    background: radial-gradient(ellipse at 50% 30%, rgba(184,149,63,0.08) 0%, transparent 65%);
  }

  .hero-content { position:relative; z-index:2; max-width:780px; }

  .hero-badge {
    display:inline-block; font-family:'Cinzel',serif; font-size:9px;
    letter-spacing:4px; color:var(--gold); text-transform:uppercase;
    border:1px solid var(--border); padding:8px 20px; margin-bottom:32px;
    animation: fadeUp 0.8s ease both;
  }

  .hero-title {
    font-family:'Cormorant Garamond',serif; font-size:clamp(48px,8vw,86px);
    font-weight:300; color:var(--cream); line-height:1.0; margin-bottom:12px;
    animation: fadeUp 0.8s ease 0.15s both;
  }
  .hero-title em { font-style:normal; color:var(--gold-b); font-weight:600; }

  .hero-subtitle {
    font-family:'Cinzel',serif; font-size:clamp(10px,1.5vw,13px);
    letter-spacing:4px; color:var(--muted); text-transform:uppercase;
    margin-bottom:36px;
    animation: fadeUp 0.8s ease 0.25s both;
  }

  .hero-desc {
    font-size:16px; font-weight:300; color:rgba(255,255,255,0.6);
    line-height:1.8; max-width:560px; margin:0 auto 48px;
    animation: fadeUp 0.8s ease 0.35s both;
  }
  .hero-desc strong { color:var(--gold-b); font-weight:500; }

  .hero-divider {
    display:flex; align-items:center; gap:12px; justify-content:center;
    margin-bottom:48px;
    animation: fadeUp 0.8s ease 0.4s both;
  }
  .h-line { width:60px; height:1px; background:linear-gradient(90deg,transparent,var(--gold)); opacity:0.4; }
  .h-dia { width:5px; height:5px; background:var(--gold); transform:rotate(45deg); opacity:0.7; }

  .hero-btns {
    display:flex; gap:16px; justify-content:center; flex-wrap:wrap;
    animation: fadeUp 0.8s ease 0.5s both;
  }
  .btn-gold {
    font-family:'Cinzel',serif; font-size:10px; letter-spacing:2px;
    background:var(--gold); color:var(--navy); padding:16px 32px;
    text-decoration:none; text-transform:uppercase; transition:all 0.3s;
    border:1px solid var(--gold);
  }
  .btn-gold:hover { background:transparent; color:var(--gold); }
  .btn-outline {
    font-family:'Cinzel',serif; font-size:10px; letter-spacing:2px;
    background:transparent; color:var(--cream); padding:16px 32px;
    text-decoration:none; text-transform:uppercase; transition:all 0.3s;
    border:1px solid rgba(255,255,255,0.25);
  }
  .btn-outline:hover { border-color:var(--gold); color:var(--gold); }

  .hero-stats {
    display:flex; gap:48px; justify-content:center; margin-top:72px;
    padding-top:40px; border-top:1px solid rgba(255,255,255,0.07);
    flex-wrap:wrap;
    animation: fadeUp 0.8s ease 0.6s both;
  }
  .stat { text-align:center; }
  .stat-num {
    font-family:'Cormorant Garamond',serif; font-size:40px; font-weight:600;
    color:var(--gold-b); line-height:1;
  }
  .stat-label {
    font-family:'Cinzel',serif; font-size:8px; letter-spacing:2px;
    color:var(--muted); text-transform:uppercase; margin-top:4px;
  }

  /* ── SECTION SHARED ── */
  section { padding: 100px 5vw; }

  .section-tag {
    font-family:'Cinzel',serif; font-size:9px; letter-spacing:4px;
    color:var(--gold); text-transform:uppercase; opacity:0.8;
    display:block; margin-bottom:12px;
  }
  .section-title {
    font-family:'Cormorant Garamond',serif; font-size:clamp(32px,5vw,52px);
    font-weight:300; line-height:1.1; margin-bottom:16px;
  }
  .section-title em { font-style:italic; color:var(--gold); }
  .section-body {
    font-size:15px; font-weight:300; color:#5a6a7a; line-height:1.8;
    max-width:560px;
  }

  .divider-gold {
    display:flex; align-items:center; gap:10px; margin:20px 0;
  }
  .dg-line { flex:1; height:1px; background:linear-gradient(90deg,var(--gold),transparent); opacity:0.25; max-width:120px; }
  .dg-dia { width:4px; height:4px; background:var(--gold); transform:rotate(45deg); opacity:0.6; flex-shrink:0; }

  /* ── ABOUT ── */
  #about { background: var(--cream); }
  .about-grid {
    display:grid; grid-template-columns:1fr 1fr; gap:80px; align-items:center;
    max-width:1100px; margin:0 auto;
  }
  .about-visual {
    position:relative; height:480px;
  }
  .about-box-main {
    position:absolute; inset:0;
    background: var(--navy);
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    padding:48px 40px; text-align:center;
  }
  .about-box-main::before,
  .about-box-main::after {
    content:''; position:absolute;
    width:20px; height:20px; border-color:var(--gold); border-style:solid; opacity:0.4;
  }
  .about-box-main::before { top:14px; left:14px; border-width:1px 0 0 1px; }
  .about-box-main::after  { bottom:14px; right:14px; border-width:0 1px 1px 0; }
  .about-box-tl { position:absolute; top:14px; right:14px; width:20px; height:20px; border-top:1px solid var(--gold); border-right:1px solid var(--gold); opacity:0.4; }
  .about-box-bl { position:absolute; bottom:14px; left:14px; width:20px; height:20px; border-bottom:1px solid var(--gold); border-left:1px solid var(--gold); opacity:0.4; }
  .about-plane { font-size:64px; margin-bottom:20px; animation: float 4s ease-in-out infinite; }
  @keyframes float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-10px)} }
  .about-name {
    font-family:'Cormorant Garamond',serif; font-size:28px; font-weight:600;
    font-style:italic; color:var(--cream); margin-bottom:6px;
  }
  .about-name span { color:var(--gold-b); }
  .about-role { font-family:'Cinzel',serif; font-size:8px; letter-spacing:3px; color:var(--muted); text-transform:uppercase; margin-bottom:24px; }
  .about-quote {
    font-family:'Cormorant Garamond',serif; font-size:14px; font-style:italic;
    color:rgba(255,255,255,0.55); line-height:1.7;
  }
  .about-accent {
    position:absolute; bottom:-20px; right:-20px; width:120px; height:120px;
    background:var(--gold); opacity:0.08; z-index:-1;
  }

  .about-text { }
  .about-values { margin-top:40px; display:flex; flex-direction:column; gap:20px; }
  .value-item {
    display:flex; gap:16px; align-items:flex-start;
    padding:20px; border:1px solid rgba(184,149,63,0.12);
    background:white; transition:all 0.3s;
  }
  .value-item:hover { border-color:var(--gold); transform:translateX(4px); }
  .value-icon { font-size:22px; flex-shrink:0; }
  .value-title { font-family:'Cinzel',serif; font-size:10px; letter-spacing:1px; color:var(--navy); text-transform:uppercase; margin-bottom:4px; }
  .value-desc { font-size:13px; font-weight:300; color:#7a8a9a; line-height:1.6; }

  /* ── SERVICES / PRICING ── */
  #services { background: var(--navy); }
  #services .section-title { color:var(--cream); }
  #services .section-body  { color:var(--muted); }

  .pricing-grid {
    display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
    gap:16px; margin-top:56px; max-width:1100px; margin-left:auto; margin-right:auto;
  }
  .price-card {
    background:rgba(255,255,255,0.03); border:1px solid var(--border);
    padding:36px 28px; position:relative; overflow:hidden;
    transition:all 0.4s; cursor:default;
  }
  .price-card::before {
    content:''; position:absolute; left:0; top:0; bottom:0; width:2px;
    background:var(--gold); transform:scaleY(0); transform-origin:bottom;
    transition:transform 0.4s;
  }
  .price-card:hover { background:rgba(184,149,63,0.06); border-color:rgba(184,149,63,0.4); transform:translateY(-4px); }
  .price-card:hover::before { transform:scaleY(1); }
  .price-flag { font-size:36px; margin-bottom:16px; display:block; }
  .price-region {
    font-family:'Cinzel',serif; font-size:10px; letter-spacing:2px;
    color:var(--cream); text-transform:uppercase; margin-bottom:8px;
  }
  .price-countries { font-size:12px; color:var(--muted); font-style:italic; line-height:1.6; margin-bottom:24px; }
  .price-amount {
    font-family:'Cormorant Garamond',serif; font-size:48px; font-weight:600;
    color:var(--gold-b); line-height:1;
  }
  .price-amount small { font-family:'Cinzel',serif; font-size:12px; color:var(--muted); font-weight:300; margin-left:4px; }
  .price-book {
    display:block; margin-top:24px; font-family:'Cinzel',serif; font-size:9px;
    letter-spacing:2px; text-transform:uppercase; color:var(--gold);
    text-decoration:none; transition:color 0.3s;
  }
  .price-book:hover { color:var(--gold-pale); }

  .includes-strip {
    max-width:1100px; margin:40px auto 0;
    background:rgba(184,149,63,0.05); border:1px solid var(--border);
    padding:32px 40px;
    display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
    gap:16px;
  }
  .inc-item {
    display:flex; align-items:center; gap:10px;
    font-size:13px; color:rgba(255,255,255,0.6); font-style:italic;
  }
  .inc-check { color:var(--gold); font-size:10px; flex-shrink:0; }

  /* ── HOW IT WORKS ── */
  #how { background:var(--cream); }
  .steps {
    display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
    gap:0; margin-top:56px; max-width:1100px; margin-left:auto; margin-right:auto;
    position:relative;
  }
  .step {
    padding:40px 32px; border:1px solid rgba(184,149,63,0.15);
    background:white; position:relative; transition:all 0.3s;
  }
  .step:hover { background:var(--navy); }
  .step:hover .step-num,
  .step:hover .step-title { color:var(--gold-b); }
  .step:hover .step-desc { color:rgba(255,255,255,0.6); }
  .step-num {
    font-family:'Cormorant Garamond',serif; font-size:56px; font-weight:300;
    color:rgba(184,149,63,0.2); line-height:1; margin-bottom:16px;
    transition:color 0.3s;
  }
  .step-icon { font-size:28px; margin-bottom:12px; display:block; }
  .step-title {
    font-family:'Cinzel',serif; font-size:11px; letter-spacing:1.5px;
    color:var(--navy); text-transform:uppercase; margin-bottom:10px;
    transition:color 0.3s;
  }
  .step-desc { font-size:13px; font-weight:300; color:#7a8a9a; line-height:1.7; transition:color 0.3s; }

  /* ── TESTIMONIALS ── */
  #testimonials { background:var(--navy-mid); }
  #testimonials .section-title { color:var(--cream); }
  #testimonials .section-body { color:var(--muted); }

  .testimonials-grid {
    display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
    gap:20px; margin-top:56px; max-width:1100px; margin-left:auto; margin-right:auto;
  }
  .tcard {
    background:rgba(255,255,255,0.03); border:1px solid var(--border);
    padding:36px 32px; position:relative; transition:all 0.3s;
  }
  .tcard:hover { background:rgba(184,149,63,0.05); border-color:rgba(184,149,63,0.3); }
  .tcard-quote {
    font-family:'Cormorant Garamond',serif; font-size:48px; font-weight:300;
    color:var(--gold); opacity:0.3; line-height:0.8; margin-bottom:16px;
  }
  .tcard-text {
    font-family:'Cormorant Garamond',serif; font-size:16px; font-style:italic;
    color:rgba(255,255,255,0.75); line-height:1.8; margin-bottom:24px;
  }
  .tcard-divider { height:1px; background:var(--border); margin-bottom:20px; }
  .tcard-author { display:flex; align-items:center; gap:12px; }
  .tcard-avatar {
    width:40px; height:40px; border-radius:50%; background:var(--navy-lite);
    display:flex; align-items:center; justify-content:center;
    font-size:16px; border:1px solid var(--border);
  }
  .tcard-name { font-family:'Cinzel',serif; font-size:9px; letter-spacing:2px; color:var(--cream); text-transform:uppercase; }
  .tcard-dest { font-size:11px; color:var(--muted); font-style:italic; margin-top:2px; }
  .tcard-stars { color:var(--gold); font-size:11px; margin-top:4px; letter-spacing:2px; }

  /* ── FAQ ── */
  #faq { background:var(--cream); }
  .faq-wrap { max-width:720px; margin:56px auto 0; }
  .faq-item {
    border-bottom:1px solid rgba(184,149,63,0.15);
    overflow:hidden;
  }
  .faq-q {
    width:100%; background:none; border:none; cursor:pointer;
    display:flex; justify-content:space-between; align-items:center;
    padding:24px 0; text-align:left; gap:16px;
  }
  .faq-q-text {
    font-family:'Cinzel',serif; font-size:11px; letter-spacing:1px;
    color:var(--navy); text-transform:uppercase; line-height:1.5;
  }
  .faq-icon {
    font-size:20px; color:var(--gold); flex-shrink:0;
    transition:transform 0.3s; font-family:'Cormorant Garamond',serif;
  }
  .faq-item.open .faq-icon { transform:rotate(45deg); }
  .faq-a {
    font-size:14px; font-weight:300; color:#5a6a7a; line-height:1.8;
    max-height:0; overflow:hidden; transition:max-height 0.4s ease, padding 0.3s;
  }
  .faq-item.open .faq-a { max-height:200px; padding-bottom:24px; }

  /* ── CONTACT ── */
  #contact { background:var(--navy); }
  #contact .section-title { color:var(--cream); }
  #contact .section-body { color:var(--muted); }

  .contact-grid {
    display:grid; grid-template-columns:1fr 1fr; gap:60px;
    max-width:1100px; margin:56px auto 0; align-items:start;
  }

  .contact-info { display:flex; flex-direction:column; gap:20px; }
  .contact-card {
    background:rgba(255,255,255,0.03); border:1px solid var(--border);
    padding:28px 24px; display:flex; gap:16px; align-items:flex-start;
    text-decoration:none; transition:all 0.3s;
  }
  .contact-card:hover { background:rgba(184,149,63,0.07); border-color:rgba(184,149,63,0.4); }
  .contact-icon { font-size:24px; flex-shrink:0; }
  .contact-label { font-family:'Cinzel',serif; font-size:9px; letter-spacing:2px; color:var(--gold); text-transform:uppercase; margin-bottom:4px; }
  .contact-val { font-size:14px; color:var(--cream); font-weight:300; }
  .contact-hint { font-size:11px; color:var(--muted); margin-top:2px; font-style:italic; }

  /* Form */
  .contact-form { display:flex; flex-direction:column; gap:16px; }
  .form-row { display:grid; grid-template-columns:1fr 1fr; gap:16px; }
  .form-group { display:flex; flex-direction:column; gap:6px; }
  .form-label {
    font-family:'Cinzel',serif; font-size:8px; letter-spacing:2px;
    color:var(--muted); text-transform:uppercase;
  }
  .form-input, .form-select, .form-textarea {
    background:rgba(255,255,255,0.04); border:1px solid var(--border);
    color:var(--cream); font-family:'Jost',sans-serif; font-size:14px; font-weight:300;
    padding:14px 16px; outline:none; transition:border 0.3s;
    width:100%;
  }
  .form-input::placeholder, .form-textarea::placeholder { color:rgba(255,255,255,0.2); }
  .form-input:focus, .form-select:focus, .form-textarea:focus { border-color:var(--gold); }
  .form-select { appearance:none; cursor:pointer; }
  .form-select option { background:var(--navy); }
  .form-textarea { resize:vertical; min-height:120px; }
  .form-submit {
    font-family:'Cinzel',serif; font-size:10px; letter-spacing:2px;
    background:var(--gold); color:var(--navy); border:none; cursor:pointer;
    padding:16px 32px; text-transform:uppercase; transition:all 0.3s;
    border:1px solid var(--gold); align-self:flex-start;
  }
  .form-submit:hover { background:transparent; color:var(--gold); }
  .form-success {
    display:none; background:rgba(184,149,63,0.1); border:1px solid var(--gold);
    padding:16px 20px; font-size:13px; color:var(--gold-b); font-style:italic;
    margin-top:8px;
  }

  /* ── FOOTER ── */
  footer {
    background:var(--navy); border-top:1px solid var(--border);
    padding:40px 5vw; text-align:center;
  }
  .footer-brand {
    font-family:'Cormorant Garamond',serif; font-size:22px; font-weight:600;
    font-style:italic; color:var(--cream); margin-bottom:6px;
  }
  .footer-brand span { color:var(--gold-b); }
  .footer-tag { font-family:'Cinzel',serif; font-size:8px; letter-spacing:3px; color:var(--muted); text-transform:uppercase; margin-bottom:20px; }
  .footer-links { display:flex; gap:24px; justify-content:center; flex-wrap:wrap; margin-bottom:24px; }
  .footer-links a {
    font-family:'Cinzel',serif; font-size:8px; letter-spacing:2px;
    color:var(--muted); text-transform:uppercase; text-decoration:none; transition:color 0.3s;
  }
  .footer-links a:hover { color:var(--gold); }
  .footer-copy { font-size:11px; color:rgba(255,255,255,0.2); }

  /* ── WHATSAPP FLOAT ── */
  .wa-float {
    position:fixed; bottom:28px; right:28px; z-index:99;
    width:56px; height:56px; border-radius:50%;
    background:linear-gradient(135deg,#25d366,#128c7e);
    display:flex; align-items:center; justify-content:center;
    font-size:26px; text-decoration:none; box-shadow:0 4px 20px rgba(37,211,102,0.4);
    transition:transform 0.3s, box-shadow 0.3s;
    animation: pulse-wa 2.5s ease-in-out infinite;
  }
  .wa-float:hover { transform:scale(1.1); box-shadow:0 6px 28px rgba(37,211,102,0.6); }
  @keyframes pulse-wa {
    0%,100% { box-shadow:0 4px 20px rgba(37,211,102,0.4); }
    50%      { box-shadow:0 4px 32px rgba(37,211,102,0.7); }
  }

  /* ── MOBILE MENU ── */
  .mobile-menu {
    display:none; position:fixed; inset:0; z-index:99;
    background:rgba(11,26,46,0.98); backdrop-filter:blur(12px);
    flex-direction:column; align-items:center; justify-content:center; gap:32px;
  }
  .mobile-menu.open { display:flex; }
  .mobile-menu a {
    font-family:'Cinzel',serif; font-size:13px; letter-spacing:3px;
    color:var(--cream); text-transform:uppercase; text-decoration:none;
    transition:color 0.3s;
  }
  .mobile-menu a:hover { color:var(--gold); }
  .mobile-close {
    position:absolute; top:24px; right:5vw;
    font-size:28px; color:var(--gold); cursor:pointer; background:none; border:none;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity:0; transform:translateY(20px); }
    to   { opacity:1; transform:translateY(0); }
  }
  .reveal { opacity:0; transform:translateY(24px); transition:opacity 0.7s ease, transform 0.7s ease; }
  .reveal.visible { opacity:1; transform:translateY(0); }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    .nav-links, .nav-cta { display:none; }
    .hamburger { display:flex; }
    .about-grid { grid-template-columns:1fr; gap:40px; }
    .about-visual { height:300px; }
    .contact-grid { grid-template-columns:1fr; gap:40px; }
    .form-row { grid-template-columns:1fr; }
    .hero-stats { gap:28px; }
    section { padding:70px 5vw; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-brand">
    <div class="nav-brand-main">Above & <span>Beyond</span> Voyagers</div>
    <div class="nav-brand-sub">Flight Planning · Singapore</div>
  </div>
  <ul class="nav-links">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Pricing</a></li>
    <li><a href="#faq">FAQ</a></li>
    <li><a href="#testimonials">Reviews</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Book Now</a>
  <button class="hamburger" onclick="toggleMenu()">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mobileMenu">
  <button class="mobile-close" onclick="toggleMenu()">✕</button>
  <a href="#home" onclick="toggleMenu()">Home</a>
  <a href="#about" onclick="toggleMenu()">About</a>
  <a href="#services" onclick="toggleMenu()">Pricing</a>
  <a href="#faq" onclick="toggleMenu()">FAQ</a>
  <a href="#testimonials" onclick="toggleMenu()">Reviews</a>
  <a href="#contact" onclick="toggleMenu()">Contact</a>
</div>

<!-- HERO -->
<section id="home">
  <div class="stars"></div>
  <div class="hero-glow"></div>
  <div class="hero-content">
    <div class="hero-badge">✈ Singapore's Personal Flight Planning Service</div>
    <h1 class="hero-title">We Find Your<br>Best <em>Flight.</em><br>You Just Pack.</h1>
    <div class="hero-subtitle">Above & Beyond · Est. 2026 · 🇸🇬</div>
    <p class="hero-desc">Busy professionals deserve better than hours spent comparing flights. Tell us where you want to go — we'll deliver your <strong>top 3 flight options</strong> within <strong>24 hours.</strong> Simple, fast, affordable.</p>
    <div class="hero-divider">
      <div class="h-line"></div><div class="h-dia"></div><div class="h-line" style="background:linear-gradient(90deg,var(--gold),transparent)"></div>
    </div>
    <div class="hero-btns">
      <a href="#contact" class="btn-gold">Book a Search</a>
      <a href="#services" class="btn-outline">View Pricing</a>
    </div>
    <div class="hero-stats">
      <div class="stat"><div class="stat-num">24h</div><div class="stat-label">Delivery</div></div>
      <div class="stat"><div class="stat-num">3</div><div class="stat-label">Flight Options</div></div>
      <div class="stat"><div class="stat-num">4</div><div class="stat-label">Regions Covered</div></div>
      <div class="stat"><div class="stat-num">SGD20</div><div class="stat-label">Starting From</div></div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-grid">
    <div class="about-visual">
      <div class="about-box-main">
        <div class="about-box-tl"></div>
        <div class="about-box-bl"></div>
        <div class="about-plane">✈️</div>
        <div class="about-name">Above & <span>Beyond</span><br>Voyagers</div>
        <div class="about-role">Your Personal Flight Planner · Singapore</div>
        <div class="about-quote">"We go above & beyond so<br>you don't have to."</div>
      </div>
      <div class="about-accent"></div>
    </div>
    <div class="about-text reveal">
      <span class="section-tag">About Us</span>
      <h2 class="section-title">Your Trusted <em>Flight</em> Planning Partner</h2>
      <div class="divider-gold"><div class="dg-line"></div><div class="dg-dia"></div></div>
      <p class="section-body">We know how precious your time is. That's why Above & Beyond Voyagers was born — to take the stress of flight searching completely off your plate. Based in Singapore, we research, compare and curate the best flight deals tailored to your budget, schedule and preferences.</p>
      <div class="about-values">
        <div class="value-item">
          <div class="value-icon">🤝</div>
          <div>
            <div class="value-title">Trusted & Personal</div>
            <div class="value-desc">Like a smart friend who knows travel — we handle everything so you can focus on the excitement of your trip.</div>
          </div>
        </div>
        <div class="value-item">
          <div class="value-icon">⚡</div>
          <div>
            <div class="value-title">Fast & Reliable</div>
            <div class="value-desc">Results guaranteed within 24 hours. No waiting, no back-and-forth — just clear options delivered to you.</div>
          </div>
        </div>
        <div class="value-item">
          <div class="value-icon">💰</div>
          <div>
            <div class="value-title">More Than You Paid For</div>
            <div class="value-desc">Every search comes with our best-time-to-book tip and personalised recommendations — always over-delivering.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SERVICES / PRICING -->
<section id="services">
  <div style="max-width:1100px;margin:0 auto">
    <span class="section-tag reveal">Our Services</span>
    <h2 class="section-title reveal" style="color:var(--cream)">Simple <em>Flat-Rate</em> Pricing</h2>
    <div class="divider-gold reveal"><div class="dg-line"></div><div class="dg-dia"></div></div>
    <p class="section-body reveal">No hidden fees. No surprises. Just one simple fee based on your destination region.</p>
  </div>
  <div class="pricing-grid">
    <div class="price-card reveal">
      <span class="price-flag">🌏</span>
      <div class="price-region">Asia</div>
      <div class="price-countries">Thailand · Japan · Korea · Bali · Vietnam · Taiwan · Philippines · Hong Kong & more</div>
      <div class="price-amount">20<small>SGD</small></div>
      <a href="#contact" class="price-book">Book This Region →</a>
    </div>
    <div class="price-card reveal">
      <span class="price-flag">🦘</span>
      <div class="price-region">Pacific</div>
      <div class="price-countries">Australia · New Zealand · Fiji · Pacific Islands & more</div>
      <div class="price-amount">27<small>SGD</small></div>
      <a href="#contact" class="price-book">Book This Region →</a>
    </div>
    <div class="price-card reveal">
      <span class="price-flag">🕌</span>
      <div class="price-region">Middle East / Europe</div>
      <div class="price-countries">Dubai · London · Paris · Istanbul · Amsterdam · Rome & more</div>
      <div class="price-amount">35<small>SGD</small></div>
      <a href="#contact" class="price-book">Book This Region →</a>
    </div>
    <div class="price-card reveal">
      <span class="price-flag">🌎</span>
      <div class="price-region">Americas / Africa</div>
      <div class="price-countries">New York · Los Angeles · Toronto · Cape Town · Nairobi & more</div>
      <div class="price-amount">45<small>SGD</small></div>
      <a href="#contact" class="price-book">Book This Region →</a>
    </div>
  </div>
  <div class="includes-strip reveal">
    <div class="inc-item"><span class="inc-check">✦</span> Top 3 flight options</div>
    <div class="inc-item"><span class="inc-check">✦</span> Price comparison</div>
    <div class="inc-item"><span class="inc-check">✦</span> Best time to book tip</div>
    <div class="inc-item"><span class="inc-check">✦</span> Results in 24 hours</div>
    <div class="inc-item"><span class="inc-check">✦</span> Personalised to your budget</div>
    <div class="inc-item"><span class="inc-check">✦</span> PayNow accepted 🇸🇬</div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section id="how">
  <div style="max-width:1100px;margin:0 auto">
    <span class="section-tag reveal">Process</span>
    <h2 class="section-title reveal">How It <em>Works</em></h2>
    <div class="divider-gold reveal"><div class="dg-line"></div><div class="dg-dia"></div></div>
    <p class="section-body reveal">Getting started is effortless. Four simple steps to your perfect flight.</p>
  </div>
  <div class="steps">
    <div class="step reveal">
      <div class="step-num">01</div>
      <span class="step-icon">📋</span>
      <div class="step-title">Tell Us Your Trip</div>
      <div class="step-desc">Share your destination, travel dates, number of travelers and any budget or airline preferences via our form or WhatsApp.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">02</div>
      <span class="step-icon">💳</span>
      <div class="step-title">Make Payment</div>
      <div class="step-desc">Pay securely via PayNow based on your destination region. Simple flat rate — no hidden charges.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">03</div>
      <span class="step-icon">🔍</span>
      <div class="step-title">We Do The Research</div>
      <div class="step-desc">Our team searches across multiple platforms to find you the best available flights matching your needs.</div>
    </div>
    <div class="step reveal">
      <div class="step-num">04</div>
      <span class="step-icon">✈️</span>
      <div class="step-title">Receive & Decide</div>
      <div class="step-desc">Get your top 3 curated flight options within 24 hours. Compare and book whichever suits you best.</div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div style="max-width:1100px;margin:0 auto">
    <span class="section-tag reveal">Testimonials</span>
    <h2 class="section-title reveal" style="color:var(--cream)">What Our <em>Clients</em> Say</h2>
    <div class="divider-gold reveal"><div class="dg-line"></div><div class="dg-dia"></div></div>
    <p class="section-body reveal">Real experiences from real travelers across Singapore.</p>
  </div>
  <div class="testimonials-grid">
    <div class="tcard reveal">
      <div class="tcard-quote">"</div>
      <div class="tcard-text">I was planning a family trip to Tokyo and had no time to compare flights. Above & Beyond found me options I never would have discovered myself. Saved me hours and a good amount of money!</div>
      <div class="tcard-divider"></div>
      <div class="tcard-author">
        <div class="tcard-avatar">😊</div>
        <div>
          <div class="tcard-name">Sarah L.</div>
          <div class="tcard-dest">✈️ Singapore → Tokyo</div>
          <div class="tcard-stars">★★★★★</div>
        </div>
      </div>
    </div>
    <div class="tcard reveal">
      <div class="tcard-quote">"</div>
      <div class="tcard-text">Super fast and professional! I messaged them in the morning and by evening I already had 3 great flight options with a breakdown. Will definitely use again for my Europe trip.</div>
      <div class="tcard-divider"></div>
      <div class="tcard-author">
        <div class="tcard-avatar">🙂</div>
        <div>
          <div class="tcard-name">Marcus T.</div>
          <div class="tcard-dest">✈️ Singapore → London</div>
          <div class="tcard-stars">★★★★★</div>
        </div>
      </div>
    </div>
    <div class="tcard reveal">
      <div class="tcard-quote">"</div>
      <div class="tcard-text">Honestly worth every cent. The service is personal, fast and they really go above and beyond — gave me tips on when to book for cheaper rates too. Highly recommend to all busy parents!</div>
      <div class="tcard-divider"></div>
      <div class="tcard-author">
        <div class="tcard-avatar">😄</div>
        <div>
          <div class="tcard-name">Priya R.</div>
          <div class="tcard-dest">✈️ Singapore → Melbourne</div>
          <div class="tcard-stars">★★★★★</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FAQ -->
<section id="faq">
  <div style="max-width:720px;margin:0 auto">
    <span class="section-tag reveal">FAQ</span>
    <h2 class="section-title reveal">Frequently Asked <em>Questions</em></h2>
    <div class="divider-gold reveal"><div class="dg-line"></div><div class="dg-dia"></div></div>
  </div>
  <div class="faq-wrap">
    <div class="faq-item reveal">
      <button class="faq-q" onclick="toggleFaq(this)">
        <span class="faq-q-text">How do I make payment?</span>
        <span class="faq-icon">+</span>
      </button>
      <div class="faq-a">We accept payment via PayNow. Once you submit your request, we'll send you our PayNow details. Payment is required before we begin your flight search.</div>
    </div>
    <div class="faq-item reveal">
      <button class="faq-q" onclick="toggleFaq(this)">
        <span class="faq-q-text">How long does it take to receive my flight options?</span>
        <span class="faq-icon">+</span>
      </button>
      <div class="faq-a">We guarantee delivery within 24 hours of payment confirmation. In most cases, you'll receive your options much sooner — typically within the same day.</div>
    </div>
    <div class="faq-item reveal">
      <button class="faq-q" onclick="toggleFaq(this)">
        <span class="faq-q-text">What if my trip covers multiple regions?</span>
        <span class="faq-icon">+</span>
      </button>
      <div class="faq-a">For multi-destination trips, we charge based on the highest applicable region. For example, if your trip covers Asia and Europe, the Europe rate of SGD 35 applies.</div>
    </div>
    <div class="faq-item reveal">
      <button class="faq-q" onclick="toggleFaq(this)">
        <span class="faq-q-text">Do you book the flights for me?</span>
        <span class="faq-icon">+</span>
      </button>
      <div class="faq-a">We provide you with the best curated flight options so you can make the final decision and book directly. This keeps your payment information secure and gives you full control.</div>
    </div>
    <div class="faq-item reveal">
      <button class="faq-q" onclick="toggleFaq(this)">
        <span class="faq-q-text">What information do I need to provide?</span>
        <span class="faq-icon">+</span>
      </button>
      <div class="faq-a">We need your departure city, destination, travel dates, number of travelers (including ages of children if applicable), budget range, and any airline or stopover preferences.</div>
    </div>
    <div class="faq-item reveal">
      <button class="faq-q" onclick="toggleFaq(this)">
        <span class="faq-q-text">Can I request one-way or multi-city flights?</span>
        <span class="faq-icon">+</span>
      </button>
      <div class="faq-a">Absolutely! We handle one-way, return, and multi-city itineraries. Just let us know your travel plans when submitting your request.</div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div style="max-width:1100px;margin:0 auto">
    <span class="section-tag reveal">Get In Touch</span>
    <h2 class="section-title reveal" style="color:var(--cream)">Start Your <em>Journey</em> Today</h2>
    <div class="divider-gold reveal"><div class="dg-line"></div><div class="dg-dia"></div></div>
    <p class="section-body reveal">Fill in the form below or reach out via WhatsApp and we'll get back to you within 24 hours.</p>
  </div>
  <div class="contact-grid">
    <div class="contact-info reveal">
      <a href="https://wa.me/6500000000" target="_blank" class="contact-card">
        <div class="contact-icon">📲</div>
        <div>
          <div class="contact-label">WhatsApp</div>
          <div class="contact-val">+65 0000 0000</div>
          <div class="contact-hint">Fastest response — usually within hours</div>
        </div>
      </a>
      <a href="mailto:hello@aboveandbeyondvoyagers.com" class="contact-card">
        <div class="contact-icon">📧</div>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-val">hello@aboveandbeyondvoyagers.com</div>
          <div class="contact-hint">For detailed enquiries and requests</div>
        </div>
      </a>
      <div class="contact-card" style="cursor:default">
        <div class="contact-icon">🇸🇬</div>
        <div>
          <div class="contact-label">Based In</div>
          <div class="contact-val">Singapore</div>
          <div class="contact-hint">Serving travelers islandwide & globally</div>
        </div>
      </div>
      <div class="contact-card" style="cursor:default">
        <div class="contact-icon">⏱️</div>
        <div>
          <div class="contact-label">Response Time</div>
          <div class="contact-val">Within 24 Hours</div>
          <div class="contact-hint">Results guaranteed after payment confirmation</div>
        </div>
      </div>
    </div>

    <form class="contact-form reveal" onsubmit="submitForm(event)">
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Your Name</label>
          <input class="form-input" type="text" placeholder="e.g. Sarah Lim" required>
        </div>
        <div class="form-group">
          <label class="form-label">WhatsApp / Phone</label>
          <input class="form-input" type="tel" placeholder="+65 9000 0000" required>
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Email Address</label>
        <input class="form-input" type="email" placeholder="your@email.com" required>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Destination</label>
          <input class="form-input" type="text" placeholder="e.g. Tokyo, Japan" required>
        </div>
        <div class="form-group">
          <label class="form-label">Region</label>
          <select class="form-select form-input" required>
            <option value="" disabled selected>Select region</option>
            <option>🌏 Asia — SGD 20</option>
            <option>🦘 Pacific — SGD 27</option>
            <option>🕌 Middle East / Europe — SGD 35</option>
            <option>🌎 Americas / Africa — SGD 45</option>
          </select>
        </div>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Travel Date</label>
          <input class="form-input" type="date" required>
        </div>
        <div class="form-group">
          <label class="form-label">No. of Travelers</label>
          <input class="form-input" type="number" placeholder="e.g. 2" min="1" required>
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Additional Notes</label>
        <textarea class="form-textarea" placeholder="Budget, airline preference, one-way or return, stopovers, special requirements..."></textarea>
      </div>
      <button type="submit" class="form-submit">Submit Enquiry ✈️</button>
      <div class="form-success" id="formSuccess">
        ✦ Thank you! We've received your enquiry and will be in touch within 24 hours.
      </div>
    </form>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-brand">Above & <span>Beyond</span> Voyagers</div>
  <div class="footer-tag">Flight Planning · Singapore · Est. 2026</div>
  <div class="footer-links">
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#services">Pricing</a>
    <a href="#faq">FAQ</a>
    <a href="#testimonials">Reviews</a>
    <a href="#contact">Contact</a>
  </div>
  <div class="footer-copy">© 2026 Above & Beyond Voyagers · Singapore · We go above & beyond so you don't have to ✈️</div>
</footer>

<!-- WHATSAPP FLOAT -->
<a href="https://wa.me/6500000000" class="wa-float" target="_blank" title="Chat on WhatsApp">💬</a>

<script>
  // Mobile menu
  function toggleMenu() {
    document.getElementById('mobileMenu').classList.toggle('open');
  }

  // FAQ accordion
  function toggleFaq(btn) {
    const item = btn.closest('.faq-item');
    const isOpen = item.classList.contains('open');
    document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
    if (!isOpen) item.classList.add('open');
  }

  // Form submit
  function submitForm(e) {
    e.preventDefault();
    document.getElementById('formSuccess').style.display = 'block';
    e.target.reset();
    setTimeout(() => document.getElementById('formSuccess').style.display = 'none', 5000);
  }

  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Nav scroll effect
  window.addEventListener('scroll', () => {
    const nav = document.querySelector('nav');
    nav.style.height = window.scrollY > 60 ? '58px' : '70px';
  });
</script>
</body>
</html>
