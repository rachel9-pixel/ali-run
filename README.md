# ali-run[index.html.html](https://github.com/user-attachments/files/33141783/index.html.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ali-Run — Move. Relax. Progress.</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Outfit:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
<link href="https://api.mapbox.com/mapbox-gl-js/v3.3.0/mapbox-gl.css" rel="stylesheet">
<script src="https://api.mapbox.com/mapbox-gl-js/v3.3.0/mapbox-gl.js"></script>
<style>
/* ═══════════════════════════════════════════
   RESET & TOKENS
═══════════════════════════════════════════ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  /* Colors */
  --c-bg:         #070710;
  --c-surface:    #0F0F1A;
  --c-surface2:   #161624;
  --c-surface3:   #1E1E30;
  --c-border:     rgba(255,255,255,0.07);
  --c-border2:    rgba(255,255,255,0.12);
  --c-blue:       #2563EB;
  --c-blue-l:     #3B82F6;
  --c-blue-xl:    #60A5FA;
  --c-blue-glow:  rgba(37,99,235,0.25);
  --c-beige:      #D4C5A9;
  --c-beige-l:    #EDE3D0;
  --c-green:      #10B981;
  --c-green-l:    #34D399;
  --c-amber:      #F59E0B;
  --c-red:        #EF4444;
  --c-txt:        #F1F1F8;
  --c-txt2:       #9898B8;
  --c-txt3:       #52526A;
  /* Typography */
  --f-display:   'Bebas Neue', sans-serif;
  --f-body:      'Outfit', sans-serif;
  --f-mono:      'JetBrains Mono', monospace;
  /* Spacing */
  --sp-xs: 4px; --sp-sm: 8px; --sp-md: 16px;
  --sp-lg: 24px; --sp-xl: 32px; --sp-2xl: 48px;
  /* Radius */
  --r-sm: 8px; --r-md: 12px; --r-lg: 16px; --r-xl: 24px;
  /* Motion */
  --ease: cubic-bezier(0.16,1,0.3,1);
  --dur: 0.3s;
  /* Sidebar */
  --sidebar-w: 240px;
  --topbar-h: 64px;
}
html{height:100%;scroll-behavior:smooth}
body{
  height:100%;font-family:var(--f-body);
  background:var(--c-bg);color:var(--c-txt);
  overflow:hidden;line-height:1.5;
  -webkit-font-smoothing:antialiased;
}
button{font-family:inherit;cursor:pointer;border:none;outline:none;background:none}
input,textarea,select{font-family:inherit;outline:none;border:none;background:none}
a{color:inherit;text-decoration:none}
img{display:block;max-width:100%}

/* ═══════════════════════════════════════════
   SCROLLBAR
═══════════════════════════════════════════ */
::-webkit-scrollbar{width:4px;height:4px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--c-border2);border-radius:2px}

/* ═══════════════════════════════════════════
   UTILITY
═══════════════════════════════════════════ */
.hidden{display:none!important}
.flex{display:flex}.flex-col{flex-direction:column}
.items-center{align-items:center}.justify-between{justify-content:space-between}
.justify-center{justify-content:center}.gap-sm{gap:var(--sp-sm)}
.gap-md{gap:var(--sp-md)}.gap-lg{gap:var(--sp-lg)}
.w-full{width:100%}.h-full{height:100%}
.text-center{text-align:center}
.text-muted{color:var(--c-txt2)}
.text-xs{font-size:12px}.text-sm{font-size:13px}.text-base{font-size:15px}
.text-blue{color:var(--c-blue-l)}.text-green{color:var(--c-green-l)}
.text-amber{color:var(--c-amber)}.text-red{color:var(--c-red)}
.fw-500{font-weight:500}.fw-600{font-weight:600}
.mono{font-family:var(--f-mono)}
.badge{
  display:inline-flex;align-items:center;gap:4px;
  font-size:11px;font-weight:600;letter-spacing:0.04em;text-transform:uppercase;
  padding:3px 8px;border-radius:20px;
}
.badge-blue{background:rgba(37,99,235,0.18);color:var(--c-blue-xl)}
.badge-green{background:rgba(16,185,129,0.15);color:var(--c-green-l)}
.badge-amber{background:rgba(245,158,11,0.15);color:var(--c-amber)}
.badge-beige{background:rgba(212,197,169,0.12);color:var(--c-beige-l)}

/* ═══════════════════════════════════════════
   CARD
═══════════════════════════════════════════ */
.card{
  background:var(--c-surface);border:1px solid var(--c-border);
  border-radius:var(--r-lg);padding:var(--sp-lg);
  transition:border-color var(--dur) var(--ease), transform var(--dur) var(--ease);
}
.card:hover{border-color:var(--c-border2)}
.card-interactive{cursor:pointer}
.card-interactive:hover{transform:translateY(-2px);border-color:rgba(37,99,235,0.3)}

/* ═══════════════════════════════════════════
   AUTH SCREEN
═══════════════════════════════════════════ */
#auth-screen{
  position:fixed;inset:0;z-index:1000;
  display:flex;align-items:center;justify-content:center;
  background:var(--c-bg);
  overflow:hidden;
}
.auth-bg{
  position:absolute;inset:0;overflow:hidden;pointer-events:none;
}
.auth-bg-glow{
  position:absolute;width:600px;height:600px;border-radius:50%;
  filter:blur(120px);opacity:0.15;
}
.auth-bg-glow.g1{background:var(--c-blue);top:-20%;left:-10%;animation:glow-drift 8s ease-in-out infinite alternate}
.auth-bg-glow.g2{background:var(--c-beige);bottom:-20%;right:-10%;animation:glow-drift 10s ease-in-out infinite alternate-reverse}
@keyframes glow-drift{0%{transform:translate(0,0)}100%{transform:translate(40px,30px)}}
.auth-grid{
  position:absolute;inset:0;
  background-image:linear-gradient(rgba(37,99,235,0.05) 1px,transparent 1px),linear-gradient(90deg,rgba(37,99,235,0.05) 1px,transparent 1px);
  background-size:48px 48px;
}
.auth-container{
  position:relative;z-index:1;
  width:100%;max-width:420px;padding:var(--sp-md);
}
.auth-logo{
  text-align:center;margin-bottom:var(--sp-2xl);
}
.auth-logo-text{
  font-family:var(--f-display);font-size:3rem;letter-spacing:0.06em;
  color:var(--c-txt);
}
.auth-logo-text span{color:var(--c-blue-l)}
.auth-logo-sub{font-size:13px;color:var(--c-txt2);margin-top:4px;letter-spacing:0.08em;text-transform:uppercase}

.auth-card{
  background:var(--c-surface);border:1px solid var(--c-border2);
  border-radius:var(--r-xl);padding:var(--sp-xl);
  box-shadow:0 32px 64px rgba(0,0,0,0.5),0 0 0 1px rgba(255,255,255,0.03);
}
.auth-tabs{
  display:flex;background:var(--c-surface2);border-radius:var(--r-md);padding:4px;
  margin-bottom:var(--sp-xl);gap:4px;
}
.auth-tab{
  flex:1;text-align:center;padding:10px;border-radius:10px;
  font-size:14px;font-weight:500;color:var(--c-txt2);
  cursor:pointer;transition:all var(--dur) var(--ease);
}
.auth-tab.active{background:var(--c-surface3);color:var(--c-txt);box-shadow:0 1px 4px rgba(0,0,0,0.3)}

.auth-panel{display:none;flex-direction:column;gap:var(--sp-md)}
.auth-panel.active{display:flex}

.form-group{display:flex;flex-direction:column;gap:6px}
.form-label{font-size:13px;font-weight:500;color:var(--c-txt2)}
.form-input{
  background:var(--c-surface2);border:1.5px solid var(--c-border);
  border-radius:var(--r-md);padding:12px 16px;
  color:var(--c-txt);font-size:15px;
  transition:border-color var(--dur) var(--ease),box-shadow var(--dur) var(--ease);
}
.form-input::placeholder{color:var(--c-txt3)}
.form-input:focus{border-color:var(--c-blue);box-shadow:0 0 0 3px var(--c-blue-glow)}
.form-input.error{border-color:var(--c-red);box-shadow:0 0 0 3px rgba(239,68,68,0.15)}
.form-error{font-size:12px;color:var(--c-red);display:flex;align-items:center;gap:4px;min-height:16px}

.password-wrap{position:relative}
.password-wrap .form-input{padding-right:48px;width:100%}
.pwd-toggle{
  position:absolute;right:14px;top:50%;transform:translateY(-50%);
  color:var(--c-txt3);font-size:16px;cursor:pointer;transition:color .2s;
  background:none;border:none;padding:0;line-height:1;
}
.pwd-toggle:hover{color:var(--c-txt2)}

.input-hint{
  font-size:11px;color:var(--c-txt3);margin-top:4px;
}
.strength-bar{display:flex;gap:3px;margin-top:6px}
.strength-seg{height:3px;flex:1;border-radius:2px;background:var(--c-border2);transition:background .3s}
.strength-seg.weak{background:var(--c-red)}
.strength-seg.medium{background:var(--c-amber)}
.strength-seg.strong{background:var(--c-green)}

.btn{
  display:flex;align-items:center;justify-content:center;gap:8px;
  border-radius:var(--r-md);font-size:15px;font-weight:600;
  padding:13px 20px;transition:all var(--dur) var(--ease);cursor:pointer;
}
.btn:active{transform:scale(0.98)}
.btn-primary{
  background:var(--c-blue);color:#fff;border:none;
  box-shadow:0 4px 20px rgba(37,99,235,0.35);
}
.btn-primary:hover{background:var(--c-blue-l);box-shadow:0 4px 24px rgba(37,99,235,0.5);transform:translateY(-1px)}
.btn-secondary{
  background:var(--c-surface2);color:var(--c-txt);
  border:1.5px solid var(--c-border2);
}
.btn-secondary:hover{background:var(--c-surface3);border-color:var(--c-border2)}
.btn-social{
  background:var(--c-surface2);border:1.5px solid var(--c-border);
  color:var(--c-txt);padding:11px 16px;border-radius:var(--r-md);
  font-size:14px;font-weight:500;
  display:flex;align-items:center;justify-content:center;gap:10px;
  cursor:pointer;transition:all var(--dur) var(--ease);
}
.btn-social:hover{background:var(--c-surface3);border-color:var(--c-border2)}
.btn-social .social-icon{width:20px;height:20px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:13px}

.divider{display:flex;align-items:center;gap:var(--sp-md);color:var(--c-txt3);font-size:12px}
.divider::before,.divider::after{content:'';flex:1;height:1px;background:var(--c-border)}

.social-row{display:grid;grid-template-columns:1fr 1fr 1fr;gap:var(--sp-sm)}

.forgot-link{font-size:13px;color:var(--c-blue-l);cursor:pointer;text-align:right;margin-top:-8px;transition:color .2s}
.forgot-link:hover{color:var(--c-blue-xl)}

/* ═══════════════════════════════════════════
   ONBOARDING
═══════════════════════════════════════════ */
#onboarding-screen{
  position:fixed;inset:0;z-index:900;
  display:flex;align-items:center;justify-content:center;
  background:var(--c-bg);overflow-y:auto;
}
.onboarding-container{
  width:100%;max-width:600px;padding:var(--sp-xl) var(--sp-md);
  min-height:100vh;display:flex;flex-direction:column;justify-content:center;
}
.onb-step{display:none;flex-direction:column;gap:var(--sp-xl);animation:fadeUp .5s var(--ease)}
.onb-step.active{display:flex}
@keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none}}

.onb-progress{display:flex;gap:6px;justify-content:center;margin-bottom:var(--sp-lg)}
.onb-dot{width:8px;height:8px;border-radius:4px;background:var(--c-surface3);transition:all .4s var(--ease)}
.onb-dot.active{width:24px;background:var(--c-blue)}
.onb-dot.done{background:var(--c-green)}

.onb-header{text-align:center}
.onb-eyebrow{font-size:12px;font-weight:600;letter-spacing:0.12em;text-transform:uppercase;color:var(--c-blue-l);margin-bottom:12px}
.onb-title{font-family:var(--f-display);font-size:clamp(2.5rem,5vw,3.5rem);letter-spacing:0.02em;line-height:0.95}
.onb-subtitle{font-size:15px;color:var(--c-txt2);margin-top:12px}

.onb-choices{display:grid;gap:var(--sp-md)}
.onb-choice{
  background:var(--c-surface);border:2px solid var(--c-border);
  border-radius:var(--r-lg);padding:var(--sp-lg);
  cursor:pointer;transition:all var(--dur) var(--ease);
  display:flex;align-items:center;gap:var(--sp-md);
}
.onb-choice:hover{border-color:var(--c-blue);background:rgba(37,99,235,0.05)}
.onb-choice.selected{border-color:var(--c-blue);background:rgba(37,99,235,0.08);box-shadow:0 0 0 1px var(--c-blue)}
.onb-choice-icon{
  width:52px;height:52px;border-radius:14px;
  display:flex;align-items:center;justify-content:center;font-size:1.6rem;flex-shrink:0;
  background:var(--c-surface2);
}
.onb-choice.selected .onb-choice-icon{background:var(--c-blue-glow)}
.onb-choice-label{font-size:16px;font-weight:600}
.onb-choice-desc{font-size:13px;color:var(--c-txt2);margin-top:2px}
.onb-check{margin-left:auto;width:22px;height:22px;border-radius:50%;border:2px solid var(--c-border);display:flex;align-items:center;justify-content:center;font-size:11px;transition:all .25s}
.onb-choice.selected .onb-check{background:var(--c-blue);border-color:var(--c-blue);color:#fff}

.onb-levels{display:grid;grid-template-columns:repeat(3,1fr);gap:var(--sp-md)}
.onb-level{
  background:var(--c-surface);border:2px solid var(--c-border);
  border-radius:var(--r-lg);padding:var(--sp-lg);text-align:center;
  cursor:pointer;transition:all var(--dur) var(--ease);
}
.onb-level:hover{border-color:rgba(37,99,235,0.5)}
.onb-level.selected{border-color:var(--c-blue);background:rgba(37,99,235,0.07)}
.onb-level-icon{font-size:2rem;margin-bottom:8px}
.onb-level-name{font-size:15px;font-weight:600}
.onb-level-sub{font-size:12px;color:var(--c-txt2);margin-top:4px}

/* ═══════════════════════════════════════════
   APP SHELL
═══════════════════════════════════════════ */
#app-shell{
  position:fixed;inset:0;
  display:none;
  background:var(--c-bg);
}
#app-shell.active{display:flex}

/* ─ SIDEBAR ─ */
.sidebar{
  width:var(--sidebar-w);flex-shrink:0;
  background:var(--c-surface);border-right:1px solid var(--c-border);
  display:flex;flex-direction:column;
  padding:var(--sp-lg) 0;
  transition:transform var(--dur) var(--ease);
  z-index:50;
}
.sidebar-logo{
  padding:0 var(--sp-lg) var(--sp-xl);
  border-bottom:1px solid var(--c-border);
  margin-bottom:var(--sp-lg);
}
.sidebar-logo-text{
  font-family:var(--f-display);font-size:1.8rem;letter-spacing:0.06em;
}
.sidebar-logo-text span{color:var(--c-blue-l)}
.sidebar-logo-sub{font-size:11px;color:var(--c-txt3);letter-spacing:0.1em;text-transform:uppercase;margin-top:2px}

.sidebar-nav{display:flex;flex-direction:column;gap:2px;padding:0 var(--sp-md);flex:1}
.nav-item{
  display:flex;align-items:center;gap:12px;
  padding:11px var(--sp-md);border-radius:var(--r-md);
  font-size:14px;font-weight:500;color:var(--c-txt2);
  cursor:pointer;transition:all var(--dur) var(--ease);position:relative;
}
.nav-item:hover{color:var(--c-txt);background:rgba(255,255,255,0.04)}
.nav-item.active{color:var(--c-txt);background:rgba(37,99,235,0.12)}
.nav-item.active::before{
  content:'';position:absolute;left:0;top:50%;transform:translateY(-50%);
  width:3px;height:60%;background:var(--c-blue-l);border-radius:0 2px 2px 0;
}
.nav-item-icon{
  width:36px;height:36px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:1rem;flex-shrink:0;background:transparent;
  transition:background var(--dur) var(--ease);
}
.nav-item.active .nav-item-icon{background:rgba(37,99,235,0.18)}
.nav-item-badge{
  margin-left:auto;font-size:10px;font-weight:700;
  background:var(--c-blue);color:#fff;
  border-radius:10px;padding:1px 6px;min-width:18px;text-align:center;
}

.sidebar-section{
  font-size:10px;font-weight:700;letter-spacing:0.12em;text-transform:uppercase;
  color:var(--c-txt3);padding:var(--sp-sm) var(--sp-lg) 4px;margin-top:var(--sp-md);
}

.sidebar-footer{
  padding:var(--sp-md) var(--sp-md) 0;
  border-top:1px solid var(--c-border);margin-top:auto;
  padding-top:var(--sp-md);
}
.user-compact{
  display:flex;align-items:center;gap:12px;padding:10px var(--sp-md);
  border-radius:var(--r-md);cursor:pointer;
  transition:background var(--dur) var(--ease);
}
.user-compact:hover{background:rgba(255,255,255,0.04)}
.user-avatar-sm{
  width:36px;height:36px;border-radius:10px;
  background:linear-gradient(135deg,var(--c-blue) 0%,var(--c-blue-xl) 100%);
  display:flex;align-items:center;justify-content:center;
  font-size:14px;font-weight:700;color:#fff;flex-shrink:0;
}
.user-compact-name{font-size:13px;font-weight:600}
.user-compact-role{font-size:11px;color:var(--c-txt3)}
.user-compact-more{margin-left:auto;color:var(--c-txt3);font-size:14px}

/* ─ MAIN ─ */
.main-area{
  flex:1;display:flex;flex-direction:column;overflow:hidden;
  min-width:0;
}

/* ─ TOPBAR ─ */
.topbar{
  height:var(--topbar-h);flex-shrink:0;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 var(--sp-xl);
  background:rgba(7,7,16,0.85);backdrop-filter:blur(12px);
  border-bottom:1px solid var(--c-border);
  z-index:40;position:sticky;top:0;
}
.topbar-left{display:flex;align-items:center;gap:var(--sp-md)}
.topbar-title{font-size:18px;font-weight:600}
.topbar-subtitle{font-size:13px;color:var(--c-txt2)}
.topbar-right{display:flex;align-items:center;gap:12px}
.topbar-btn{
  width:38px;height:38px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  background:var(--c-surface2);border:1px solid var(--c-border);
  color:var(--c-txt2);font-size:16px;cursor:pointer;
  transition:all var(--dur) var(--ease);position:relative;
}
.topbar-btn:hover{color:var(--c-txt);border-color:var(--c-border2);background:var(--c-surface3)}
.notif-dot{
  position:absolute;top:7px;right:7px;width:7px;height:7px;
  border-radius:50%;background:var(--c-blue);
  border:2px solid var(--c-bg);
}
.topbar-user{
  display:flex;align-items:center;gap:10px;padding:6px 12px 6px 6px;
  border:1px solid var(--c-border);border-radius:var(--r-xl);
  cursor:pointer;transition:all var(--dur) var(--ease);
}
.topbar-user:hover{border-color:var(--c-border2);background:var(--c-surface2)}
.topbar-avatar{
  width:30px;height:30px;border-radius:8px;
  background:linear-gradient(135deg,var(--c-blue) 0%,var(--c-blue-xl) 100%);
  display:flex;align-items:center;justify-content:center;
  font-size:12px;font-weight:700;color:#fff;
}
.topbar-user-name{font-size:13px;font-weight:600}

/* Hamburger mobile */
.mobile-menu-btn{
  display:none;width:38px;height:38px;
  align-items:center;justify-content:center;
  background:var(--c-surface2);border:1px solid var(--c-border);
  border-radius:var(--r-sm);color:var(--c-txt2);font-size:18px;cursor:pointer;
}

/* ─ PAGE CONTENT ─ */
.pages{flex:1;overflow:hidden;position:relative}
.page{
  position:absolute;inset:0;overflow-y:auto;
  padding:var(--sp-xl);display:none;
}
.page.active{display:block;animation:pageFade .35s var(--ease)}
@keyframes pageFade{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}

/* ═══════════════════════════════════════════
   DASHBOARD PAGE
═══════════════════════════════════════════ */
.dashboard-grid{
  display:grid;
  grid-template-columns:1fr 1fr 1fr;
  grid-template-rows:auto;
  gap:var(--sp-lg);
}
/* Big welcome card */
.welcome-card{
  grid-column:1 / -1;
  background:linear-gradient(135deg,var(--c-blue-dark,#1e3a8a) 0%,var(--c-blue) 60%,var(--c-blue-l) 100%);
  border-radius:var(--r-xl);padding:var(--sp-xl);
  position:relative;overflow:hidden;border:none;
}
.welcome-card-bg{
  position:absolute;inset:0;pointer-events:none;
  background:radial-gradient(ellipse at 80% 50%,rgba(255,255,255,0.07) 0%,transparent 60%);
}
.welcome-card-grid{
  position:absolute;inset:0;pointer-events:none;
  background-image:linear-gradient(rgba(255,255,255,0.04) 1px,transparent 1px),linear-gradient(90deg,rgba(255,255,255,0.04) 1px,transparent 1px);
  background-size:28px 28px;
}
.welcome-greeting{font-size:14px;color:rgba(255,255,255,0.65);margin-bottom:6px;position:relative}
.welcome-name{
  font-family:var(--f-display);font-size:2.6rem;letter-spacing:0.03em;
  line-height:1;position:relative;
}
.welcome-tagline{font-size:14px;color:rgba(255,255,255,0.65);margin-top:8px;position:relative}
.welcome-stats{
  display:flex;gap:var(--sp-xl);margin-top:var(--sp-xl);position:relative;
}
.welcome-stat-item{}
.welcome-stat-val{font-family:var(--f-mono);font-size:1.8rem;font-weight:600;line-height:1}
.welcome-stat-label{font-size:12px;color:rgba(255,255,255,0.6);margin-top:4px}
.welcome-streak{
  margin-left:auto;display:flex;flex-direction:column;align-items:center;justify-content:center;
  background:rgba(255,255,255,0.1);border-radius:var(--r-lg);
  padding:var(--sp-md) var(--sp-xl);gap:4px;
}
.welcome-streak-num{font-family:var(--f-display);font-size:3rem;line-height:1}
.welcome-streak-label{font-size:12px;color:rgba(255,255,255,0.65)}

/* Quick stats */
.quick-stat-card{
  background:var(--c-surface);border:1px solid var(--c-border);
  border-radius:var(--r-lg);padding:var(--sp-lg);
}
.qs-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:var(--sp-md)}
.qs-icon{
  width:40px;height:40px;border-radius:12px;
  display:flex;align-items:center;justify-content:center;font-size:1.1rem;
}
.qs-icon-blue{background:rgba(37,99,235,0.15)}
.qs-icon-green{background:rgba(16,185,129,0.15)}
.qs-icon-amber{background:rgba(245,158,11,0.15)}
.qs-val{font-family:var(--f-mono);font-size:1.8rem;font-weight:600;line-height:1}
.qs-unit{font-size:14px;color:var(--c-txt2);font-weight:400}
.qs-label{font-size:13px;color:var(--c-txt2);margin-top:4px}
.qs-trend{display:flex;align-items:center;gap:4px;font-size:12px;margin-top:var(--sp-sm)}
.trend-up{color:var(--c-green-l)}.trend-down{color:var(--c-red)}

/* Weekly goals */
.goals-card{grid-column:1/3}
.goal-row{display:flex;align-items:center;gap:var(--sp-md);padding:var(--sp-md) 0;border-bottom:1px solid var(--c-border)}
.goal-row:last-child{border-bottom:none;padding-bottom:0}
.goal-icon{width:38px;height:38px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1rem;flex-shrink:0}
.goal-info{flex:1}
.goal-name{font-size:14px;font-weight:500}
.goal-progress-row{display:flex;align-items:center;gap:var(--sp-sm);margin-top:6px}
.goal-bar{flex:1;height:5px;background:var(--c-surface3);border-radius:3px;overflow:hidden}
.goal-bar-fill{height:100%;border-radius:3px;transition:width 1s var(--ease)}
.goal-pct{font-size:12px;font-family:var(--f-mono);color:var(--c-txt2);min-width:32px;text-align:right}

/* Recent sessions */
.sessions-card{grid-column:3/4}
.session-item{
  display:flex;align-items:center;gap:12px;
  padding:10px 0;border-bottom:1px solid var(--c-border);
}
.session-item:last-child{border-bottom:none;padding-bottom:0}
.session-type-icon{
  width:36px;height:36px;border-radius:10px;
  display:flex;align-items:center;justify-content:center;font-size:1rem;flex-shrink:0;
}
.session-info{flex:1}
.session-name{font-size:13px;font-weight:500}
.session-meta{font-size:11px;color:var(--c-txt3);margin-top:2px}
.session-val{font-family:var(--f-mono);font-size:13px;font-weight:600;color:var(--c-blue-xl)}

/* Activity chart */
.chart-card{grid-column:1/3}
.chart-bars{
  display:flex;align-items:flex-end;gap:8px;height:100px;
  margin-top:var(--sp-lg);
}
.chart-bar-wrap{flex:1;display:flex;flex-direction:column;align-items:center;gap:4px}
.chart-bar{
  width:100%;border-radius:4px 4px 0 0;
  background:var(--c-surface3);
  transition:height .8s var(--ease),background .3s;
  cursor:pointer;
}
.chart-bar:hover{background:var(--c-blue)}
.chart-bar.active{background:var(--c-blue-l)}
.chart-day{font-size:10px;color:var(--c-txt3);font-family:var(--f-mono)}

/* ═══════════════════════════════════════════
   RUN PAGE
═══════════════════════════════════════════ */
.run-layout{display:grid;grid-template-columns:1fr 340px;gap:var(--sp-lg)}

.gps-card{
  background:var(--c-surface);border:1px solid var(--c-border);
  border-radius:var(--r-xl);overflow:hidden;
}
.gps-map{
  height:280px;background:var(--c-surface2);position:relative;overflow:hidden;
}
#mapbox-container{width:100%;height:100%}
.mapboxgl-ctrl-logo{display:none!important}

.map-label{
  position:absolute;top:var(--sp-md);left:var(--sp-md);
  background:rgba(7,7,16,0.85);backdrop-filter:blur(8px);
  border:1px solid var(--c-border2);border-radius:var(--r-sm);
  padding:6px 12px;font-size:12px;font-weight:500;color:var(--c-blue-xl);
  display:flex;align-items:center;gap:6px;
}
.gps-dot{width:7px;height:7px;border-radius:50%;background:var(--c-blue-l);animation:gps-blink 1.5s infinite}
@keyframes gps-blink{0%,100%{opacity:1;box-shadow:0 0 0 3px rgba(37,99,235,0.3)}50%{opacity:.6;box-shadow:none}}

.run-stats-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  gap:1px;background:var(--c-border);
}
.run-stat{
  background:var(--c-surface);padding:var(--sp-lg);text-align:center;
}
.run-stat-val{font-family:var(--f-mono);font-size:2rem;font-weight:600;line-height:1}
.run-stat-unit{font-size:12px;color:var(--c-txt2);margin-top:4px}
.run-stat-label{font-size:11px;color:var(--c-txt3);margin-top:2px;text-transform:uppercase;letter-spacing:.08em}

.run-controls{
  padding:var(--sp-lg);
  display:flex;align-items:center;justify-content:center;gap:var(--sp-md);
}
.run-btn{
  width:60px;height:60px;border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  font-size:1.4rem;cursor:pointer;transition:all .25s var(--ease);border:none;
}
.run-btn-main{
  width:76px;height:76px;font-size:1.8rem;
  background:var(--c-blue);color:#fff;
  box-shadow:0 0 0 8px rgba(37,99,235,0.15),0 4px 20px rgba(37,99,235,0.4);
}
.run-btn-main:hover{box-shadow:0 0 0 12px rgba(37,99,235,0.12),0 6px 24px rgba(37,99,235,0.5)}
.run-btn-main.running{background:var(--c-amber)}
.run-btn-main.running:hover{box-shadow:0 0 0 12px rgba(245,158,11,0.12),0 6px 24px rgba(245,158,11,0.4)}
.run-btn-sec{background:var(--c-surface2);color:var(--c-txt2);border:1px solid var(--c-border2)}
.run-btn-sec:hover{background:var(--c-surface3);color:var(--c-txt)}
.run-btn-stop{background:rgba(239,68,68,0.12);color:var(--c-red);border:1px solid rgba(239,68,68,0.2)}
.run-btn-stop:hover{background:rgba(239,68,68,0.2)}

.run-sidebar{display:flex;flex-direction:column;gap:var(--sp-lg)}

.pace-card{}
.pace-display{
  font-family:var(--f-mono);font-size:3rem;font-weight:600;
  line-height:1;margin:var(--sp-md) 0;
}
.pace-unit{font-size:14px;color:var(--c-txt2)}
.pace-zone{
  display:flex;gap:4px;margin-top:var(--sp-md);
}
.zone-seg{flex:1;height:6px;border-radius:3px;background:var(--c-surface3)}
.zone-seg.z1{background:#10B981}.zone-seg.z2{background:#3B82F6}.zone-seg.z3{background:#F59E0B}.zone-seg.z4{background:#EF4444}

.audio-coach{
  background:linear-gradient(135deg,rgba(37,99,235,0.12),rgba(37,99,235,0.04));
  border:1px solid rgba(37,99,235,0.2);
  border-radius:var(--r-lg);padding:var(--sp-lg);
}
.audio-wave{display:flex;align-items:center;gap:3px;height:30px;margin:var(--sp-md) 0}
.audio-bar{width:3px;border-radius:2px;background:var(--c-blue-l);animation:wave-anim 1.2s ease-in-out infinite}
.audio-bar:nth-child(2){animation-delay:.1s;height:40%}
.audio-bar:nth-child(3){animation-delay:.2s;height:80%}
.audio-bar:nth-child(4){animation-delay:.3s;height:60%}
.audio-bar:nth-child(5){animation-delay:.4s;height:100%}
.audio-bar:nth-child(6){animation-delay:.5s;height:70%}
.audio-bar:nth-child(7){animation-delay:.6s;height:45%}
.audio-bar:nth-child(8){animation-delay:.3s;height:85%}
.audio-bar:nth-child(9){animation-delay:.1s;height:50%}
@keyframes wave-anim{0%,100%{transform:scaleY(0.5);opacity:.6}50%{transform:scaleY(1);opacity:1}}

.coach-msg{font-size:14px;color:var(--c-txt2);line-height:1.6}

.run-history-list{display:flex;flex-direction:column;gap:8px}
.run-hist-item{
  display:flex;align-items:center;gap:12px;
  background:var(--c-surface2);border-radius:var(--r-md);padding:12px 14px;
  transition:background .2s;cursor:pointer;
}
.run-hist-item:hover{background:var(--c-surface3)}
.run-hist-info{flex:1}
.run-hist-name{font-size:13px;font-weight:500}
.run-hist-meta{font-size:11px;color:var(--c-txt3);margin-top:2px}
.run-hist-dist{font-family:var(--f-mono);font-size:14px;font-weight:600;color:var(--c-blue-xl)}

/* ═══════════════════════════════════════════
   YOGA PAGE
═══════════════════════════════════════════ */
.yoga-header{
  background:linear-gradient(135deg,rgba(212,197,169,0.12),rgba(212,197,169,0.04));
  border:1px solid rgba(212,197,169,0.15);
  border-radius:var(--r-xl);padding:var(--sp-xl);
  display:flex;align-items:center;justify-content:space-between;
  margin-bottom:var(--sp-lg);
}
.yoga-cat-tabs{
  display:flex;gap:6px;flex-wrap:wrap;margin-bottom:var(--sp-lg);
}
.yoga-cat-tab{
  padding:8px 18px;border-radius:20px;font-size:13px;font-weight:500;
  background:var(--c-surface2);color:var(--c-txt2);
  border:1px solid var(--c-border);cursor:pointer;transition:all .2s;
}
.yoga-cat-tab:hover{color:var(--c-txt);border-color:var(--c-border2)}
.yoga-cat-tab.active{background:rgba(212,197,169,0.12);color:var(--c-beige);border-color:rgba(212,197,169,0.3)}

.yoga-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:var(--sp-lg)}
.yoga-card{
  background:var(--c-surface);border:1px solid var(--c-border);
  border-radius:var(--r-lg);overflow:hidden;cursor:pointer;
  transition:all var(--dur) var(--ease);
}
.yoga-card:hover{transform:translateY(-3px);border-color:rgba(212,197,169,0.25);box-shadow:0 8px 32px rgba(0,0,0,0.3)}
.yoga-thumb{
  height:140px;display:flex;align-items:center;justify-content:center;
  font-size:3.5rem;position:relative;overflow:hidden;
}
.yoga-thumb-overlay{
  position:absolute;inset:0;display:flex;align-items:center;justify-content:center;
  background:rgba(37,99,235,0.15);opacity:0;transition:opacity .3s;font-size:1.5rem;
}
.yoga-card:hover .yoga-thumb-overlay{opacity:1}
.yoga-card-body{padding:var(--sp-md)}
.yoga-card-name{font-size:15px;font-weight:600;margin-bottom:6px}
.yoga-card-meta{display:flex;align-items:center;gap:var(--sp-md)}
.yoga-card-tag{font-size:11px;color:var(--c-txt3)}

/* Yoga player modal */
.yoga-modal-overlay{
  position:fixed;inset:0;z-index:200;
  background:rgba(0,0,0,0.8);backdrop-filter:blur(8px);
  display:none;align-items:center;justify-content:center;
}
.yoga-modal-overlay.open{display:flex;animation:fadeIn .3s var(--ease)}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
.yoga-modal{
  background:var(--c-surface);border:1px solid var(--c-border2);
  border-radius:var(--r-xl);width:min(540px,95vw);padding:var(--sp-xl);
  position:relative;animation:scaleIn .35s var(--ease);
}
@keyframes scaleIn{from{opacity:0;transform:scale(0.95)}to{opacity:1;transform:none}}
.yoga-modal-close{
  position:absolute;top:var(--sp-md);right:var(--sp-md);
  width:32px;height:32px;border-radius:8px;background:var(--c-surface2);
  border:1px solid var(--c-border);color:var(--c-txt2);font-size:16px;
  display:flex;align-items:center;justify-content:center;cursor:pointer;
}
.yoga-modal-close:hover{background:var(--c-surface3);color:var(--c-txt)}
.yoga-player-header{text-align:center;margin-bottom:var(--sp-xl)}
.yoga-player-icon{font-size:4rem;margin-bottom:var(--sp-md);display:block}
.yoga-timer{
  font-family:var(--f-mono);font-size:3.5rem;font-weight:600;
  text-align:center;margin:var(--sp-lg) 0;letter-spacing:.05em;
}
.yoga-progress-ring{
  display:flex;justify-content:center;margin:var(--sp-lg) 0;
}
.yoga-player-controls{display:flex;align-items:center;justify-content:center;gap:var(--sp-lg)}

/* ═══════════════════════════════════════════
   PROGRESS PAGE
═══════════════════════════════════════════ */
.progress-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:var(--sp-lg)}
.progress-big{grid-column:1/3}

.weight-input-row{
  display:flex;align-items:center;gap:var(--sp-sm);margin-top:var(--sp-md);
}
.weight-input{
  background:var(--c-surface2);border:1.5px solid var(--c-border);
  border-radius:var(--r-md);padding:10px 14px;color:var(--c-txt);
  font-size:16px;font-family:var(--f-mono);font-weight:600;width:100px;
  text-align:center;transition:border-color .2s;
}
.weight-input:focus{border-color:var(--c-blue)}
.btn-sm{padding:9px 16px;font-size:13px;border-radius:var(--r-sm)}

/* Chart SVG */
.chart-svg-wrap{margin-top:var(--sp-lg);overflow:hidden}

/* Achievements */
.achievements-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:var(--sp-md)}
.achievement{
  background:var(--c-surface2);border-radius:var(--r-lg);padding:var(--sp-md);
  text-align:center;cursor:pointer;transition:all .25s var(--ease);
  border:2px solid transparent;
}
.achievement:hover{background:var(--c-surface3);transform:translateY(-2px)}
.achievement.unlocked{border-color:rgba(245,158,11,0.3);background:rgba(245,158,11,0.06)}
.achievement-icon{font-size:2rem;margin-bottom:8px;display:block;opacity:.4}
.achievement.unlocked .achievement-icon{opacity:1}
.achievement-name{font-size:12px;font-weight:600;color:var(--c-txt2)}
.achievement.unlocked .achievement-name{color:var(--c-txt)}
.achievement-desc{font-size:10px;color:var(--c-txt3);margin-top:3px}

/* XP bar */
.xp-bar-wrap{background:var(--c-surface2);border-radius:var(--r-xl);padding:var(--sp-lg)}
.xp-header{display:flex;justify-content:space-between;margin-bottom:var(--sp-md);align-items:center}
.xp-level{font-family:var(--f-display);font-size:1.5rem;letter-spacing:.04em}
.xp-bar{height:8px;background:var(--c-surface3);border-radius:4px;overflow:hidden}
.xp-bar-fill{height:100%;background:linear-gradient(90deg,var(--c-blue),var(--c-blue-xl));border-radius:4px;transition:width 1.2s var(--ease)}

/* ═══════════════════════════════════════════
   PROFILE PAGE
═══════════════════════════════════════════ */
.profile-hero{
  background:var(--c-surface);border:1px solid var(--c-border);
  border-radius:var(--r-xl);padding:var(--sp-xl);
  display:flex;align-items:center;gap:var(--sp-xl);
  margin-bottom:var(--sp-lg);
}
.profile-avatar{
  width:80px;height:80px;border-radius:20px;
  background:linear-gradient(135deg,var(--c-blue) 0%,var(--c-blue-xl) 100%);
  display:flex;align-items:center;justify-content:center;
  font-family:var(--f-display);font-size:2rem;color:#fff;flex-shrink:0;
}
.profile-name{font-family:var(--f-display);font-size:2rem;letter-spacing:.03em;line-height:1}
.profile-email{font-size:14px;color:var(--c-txt2);margin-top:4px}
.profile-tags{display:flex;gap:8px;margin-top:var(--sp-md)}

.settings-sections{display:grid;grid-template-columns:1fr 1fr;gap:var(--sp-lg)}
.settings-group{background:var(--c-surface);border:1px solid var(--c-border);border-radius:var(--r-lg);overflow:hidden}
.settings-group-title{
  font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;
  color:var(--c-txt3);padding:var(--sp-md) var(--sp-lg);
  border-bottom:1px solid var(--c-border);
}
.settings-item{
  display:flex;align-items:center;gap:var(--sp-md);padding:14px var(--sp-lg);
  border-bottom:1px solid var(--c-border);cursor:pointer;
  transition:background .2s;
}
.settings-item:last-child{border-bottom:none}
.settings-item:hover{background:rgba(255,255,255,0.03)}
.settings-item-icon{width:34px;height:34px;border-radius:8px;background:var(--c-surface2);display:flex;align-items:center;justify-content:center;font-size:.9rem;flex-shrink:0}
.settings-item-info{flex:1}
.settings-item-label{font-size:14px;font-weight:500}
.settings-item-sub{font-size:12px;color:var(--c-txt3);margin-top:2px}
.settings-item-arrow{color:var(--c-txt3);font-size:12px}

.toggle{
  position:relative;width:44px;height:24px;
}
.toggle input{opacity:0;width:0;height:0;position:absolute}
.toggle-slider{
  position:absolute;inset:0;border-radius:12px;
  background:var(--c-surface3);cursor:pointer;transition:background .25s;
}
.toggle-slider::before{
  content:'';position:absolute;
  width:18px;height:18px;border-radius:50%;
  left:3px;top:3px;background:var(--c-txt3);
  transition:transform .25s var(--ease),background .25s;
}
.toggle input:checked + .toggle-slider{background:var(--c-blue)}
.toggle input:checked + .toggle-slider::before{transform:translateX(20px);background:#fff}

.logout-btn{
  display:flex;align-items:center;gap:12px;
  background:rgba(239,68,68,0.06);border:1px solid rgba(239,68,68,0.15);
  border-radius:var(--r-lg);padding:14px var(--sp-lg);
  color:var(--c-red);font-size:15px;font-weight:500;
  cursor:pointer;transition:all .2s;margin-top:var(--sp-lg);width:100%;
}
.logout-btn:hover{background:rgba(239,68,68,0.12);border-color:rgba(239,68,68,0.3)}

/* ═══════════════════════════════════════════
   TOAST
═══════════════════════════════════════════ */
#toast-container{
  position:fixed;bottom:var(--sp-xl);right:var(--sp-xl);
  z-index:9999;display:flex;flex-direction:column;gap:8px;pointer-events:none;
}
.toast{
  background:var(--c-surface2);border:1px solid var(--c-border2);
  border-radius:var(--r-md);padding:12px 16px;
  display:flex;align-items:center;gap:10px;
  font-size:14px;pointer-events:all;min-width:260px;
  box-shadow:0 8px 32px rgba(0,0,0,0.4);
  animation:toastIn .35s var(--ease);
}
.toast.removing{animation:toastOut .3s var(--ease) forwards}
@keyframes toastIn{from{opacity:0;transform:translateX(20px)}to{opacity:1;transform:none}}
@keyframes toastOut{to{opacity:0;transform:translateX(20px)}}
.toast-success{border-left:3px solid var(--c-green)}
.toast-error{border-left:3px solid var(--c-red)}
.toast-info{border-left:3px solid var(--c-blue-l)}
.toast-icon{font-size:16px}

/* ═══════════════════════════════════════════
   NOTIFICATIONS DROPDOWN
═══════════════════════════════════════════ */
.notif-dropdown{
  position:absolute;top:calc(100% + 8px);right:0;
  width:320px;background:var(--c-surface);border:1px solid var(--c-border2);
  border-radius:var(--r-lg);box-shadow:0 16px 48px rgba(0,0,0,0.5);
  z-index:100;overflow:hidden;
  display:none;animation:scaleIn .25s var(--ease);
  transform-origin:top right;
}
.notif-dropdown.open{display:block}
.notif-dd-header{
  padding:var(--sp-md) var(--sp-lg);border-bottom:1px solid var(--c-border);
  display:flex;justify-content:space-between;align-items:center;
}
.notif-dd-title{font-size:15px;font-weight:600}
.notif-dd-clear{font-size:12px;color:var(--c-blue-l);cursor:pointer}
.notif-item{
  padding:12px var(--sp-lg);border-bottom:1px solid var(--c-border);
  display:flex;gap:12px;cursor:pointer;transition:background .2s;
}
.notif-item:last-child{border-bottom:none}
.notif-item:hover{background:rgba(255,255,255,0.03)}
.notif-item-dot{
  width:8px;height:8px;border-radius:50%;background:var(--c-blue);
  flex-shrink:0;margin-top:4px;
}
.notif-item-dot.read{background:transparent;border:1px solid var(--c-border2)}
.notif-item-text{font-size:13px;line-height:1.5;color:var(--c-txt2)}
.notif-item-time{font-size:11px;color:var(--c-txt3);margin-top:3px}

/* ═══════════════════════════════════════════
   LOADING OVERLAY
═══════════════════════════════════════════ */
.loading-overlay{
  position:fixed;inset:0;z-index:9999;
  background:var(--c-bg);
  display:flex;align-items:center;justify-content:center;
  flex-direction:column;gap:var(--sp-lg);
  transition:opacity .5s;
}
.loading-logo{
  font-family:var(--f-display);font-size:3.5rem;letter-spacing:.06em;
}
.loading-logo span{color:var(--c-blue-l)}
.loading-bar{width:200px;height:3px;background:var(--c-surface3);border-radius:2px;overflow:hidden}
.loading-bar-fill{height:100%;background:var(--c-blue-l);border-radius:2px;animation:loading 1.5s var(--ease) forwards}
@keyframes loading{from{width:0}to{width:100%}}

/* ═══════════════════════════════════════════
   RESPONSIVE
═══════════════════════════════════════════ */
@media(max-width:1024px){
  .dashboard-grid{grid-template-columns:1fr 1fr}
  .goals-card{grid-column:1/-1}
  .sessions-card{grid-column:1/-1}
  .chart-card{grid-column:1/-1}
  .progress-grid{grid-template-columns:1fr 1fr}
  .progress-big{grid-column:1/-1}
  .settings-sections{grid-template-columns:1fr}
  .run-layout{grid-template-columns:1fr}
  .yoga-grid{grid-template-columns:repeat(2,1fr)}
  .achievements-grid{grid-template-columns:repeat(3,1fr)}
}
@media(max-width:768px){
  :root{--sidebar-w:0px}
  .sidebar{
    position:fixed;left:-260px;top:0;bottom:0;width:260px;
    z-index:60;box-shadow:4px 0 20px rgba(0,0,0,0.5);
    transition:left var(--dur) var(--ease);
  }
  .sidebar.open{left:0}
  .mobile-menu-btn{display:flex}
  .topbar-right .topbar-user span{display:none}
  .dashboard-grid{grid-template-columns:1fr}
  .yoga-grid{grid-template-columns:1fr}
  .achievements-grid{grid-template-columns:repeat(2,1fr)}
  .page{padding:var(--sp-md)}
  .onb-levels{grid-template-columns:1fr}
  .social-row{grid-template-columns:1fr}
  .profile-hero{flex-direction:column;text-align:center}
  .settings-sections{grid-template-columns:1fr}
}
@media(max-width:480px){
  .welcome-stats{flex-wrap:wrap}
  .run-stats-grid{grid-template-columns:1fr 1fr}
}
</style>
</head>
<body>

<!-- ════════════════════════════════════════
     LOADING SCREEN
════════════════════════════════════════ -->
<div class="loading-overlay" id="loading">
  <div class="loading-logo">ALI<span>-</span>RUN</div>
  <div class="loading-bar"><div class="loading-bar-fill"></div></div>
</div>

<!-- ════════════════════════════════════════
     AUTH SCREEN
════════════════════════════════════════ -->
<div id="auth-screen">
  <div class="auth-bg">
    <div class="auth-bg-glow g1"></div>
    <div class="auth-bg-glow g2"></div>
    <div class="auth-grid"></div>
  </div>
  <div class="auth-container">
    <div class="auth-logo">
      <div class="auth-logo-text">ALI<span>-</span>RUN</div>
      <div class="auth-logo-sub">Move · Relax · Progress</div>
    </div>
    <div class="auth-card">
      <!-- Tabs -->
      <div class="auth-tabs">
        <div class="auth-tab active" data-tab="login">Connexion</div>
        <div class="auth-tab" data-tab="signup">Inscription</div>
      </div>

      <!-- LOGIN PANEL -->
      <div class="auth-panel active" id="panel-login">
        <div class="form-group">
          <label class="form-label">Adresse e-mail</label>
          <input type="email" id="login-email" class="form-input" placeholder="vous@exemple.com">
          <div class="form-error" id="login-email-err"></div>
        </div>
        <div class="form-group">
          <label class="form-label">Mot de passe</label>
          <div class="password-wrap">
            <input type="password" id="login-pwd" class="form-input" placeholder="••••••••">
            <button class="pwd-toggle" data-target="login-pwd">👁</button>
          </div>
          <div class="form-error" id="login-pwd-err"></div>
        </div>
        <div class="forgot-link" onclick="showForgot()">Mot de passe oublié ?</div>
        <button class="btn btn-primary w-full" id="btn-login" onclick="doLogin()">
          <span>Se connecter</span>
        </button>
        <div class="divider">ou continuer avec</div>
        <div class="social-row">
          <button class="btn-social" onclick="socialLogin('Google')">
            <span style="font-size:16px">G</span>
            <span>Google</span>
          </button>
          <button class="btn-social" onclick="socialLogin('Facebook')">
            <span style="color:#1877F2;font-weight:700;font-size:16px">f</span>
            <span>Facebook</span>
          </button>
          <button class="btn-social" onclick="socialLogin('Apple')">
            <span style="font-size:16px">🍎</span>
            <span>Apple</span>
          </button>
        </div>
      </div>

      <!-- SIGNUP PANEL -->
      <div class="auth-panel" id="panel-signup">
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:var(--sp-sm);width:100%;min-width:0">
          <div class="form-group" style="min-width:0;overflow:hidden">
            <label class="form-label">Prénom</label>
            <input type="text" id="signup-fname" class="form-input" placeholder="Prénom" style="width:100%;min-width:0">
            <div class="form-error" id="signup-fname-err"></div>
          </div>
          <div class="form-group" style="min-width:0;overflow:hidden">
            <label class="form-label">Nom</label>
            <input type="text" id="signup-lname" class="form-input" placeholder="Nom" style="width:100%;min-width:0">
          </div>
        </div>
        <div class="form-group">
          <label class="form-label">Adresse e-mail</label>
          <input type="email" id="signup-email" class="form-input" placeholder="vous@exemple.com">
          <div class="form-error" id="signup-email-err"></div>
        </div>
        <div class="form-group">
          <label class="form-label">Mot de passe</label>
          <div class="password-wrap">
            <input type="password" id="signup-pwd" class="form-input" placeholder="Min. 8 caractères" oninput="checkStrength(this.value)">
            <button class="pwd-toggle" data-target="signup-pwd">👁</button>
          </div>
          <div class="strength-bar" id="strength-bar">
            <div class="strength-seg" id="s1"></div>
            <div class="strength-seg" id="s2"></div>
            <div class="strength-seg" id="s3"></div>
            <div class="strength-seg" id="s4"></div>
          </div>
          <div class="input-hint" id="strength-label">Entrez un mot de passe</div>
          <div class="form-error" id="signup-pwd-err"></div>
        </div>
        <button class="btn btn-primary w-full" onclick="doSignup()">Créer mon compte</button>
        <div class="divider">ou s'inscrire avec</div>
        <div class="social-row">
          <button class="btn-social" onclick="socialLogin('Google')">
            <span style="font-size:16px">G</span>
            <span>Google</span>
          </button>
          <button class="btn-social" onclick="socialLogin('Facebook')">
            <span style="color:#1877F2;font-weight:700;font-size:16px">f</span>
            <span>Facebook</span>
          </button>
          <button class="btn-social" onclick="socialLogin('Apple')">
            <span style="font-size:16px">🍎</span>
            <span>Apple</span>
          </button>
        </div>
        <p style="font-size:12px;color:var(--c-txt3);text-align:center;line-height:1.6">
          En vous inscrivant, vous acceptez nos <span style="color:var(--c-blue-l);cursor:pointer">CGU</span> et notre <span style="color:var(--c-blue-l);cursor:pointer">Politique de confidentialité</span>.
        </p>
      </div>
    </div>
  </div>
</div>

<!-- ════════════════════════════════════════
     ONBOARDING
════════════════════════════════════════ -->
<div id="onboarding-screen" class="hidden">
  <div class="onboarding-container">
    <div class="onb-progress">
      <div class="onb-dot active" id="onb-dot-0"></div>
      <div class="onb-dot" id="onb-dot-1"></div>
      <div class="onb-dot" id="onb-dot-2"></div>
    </div>

    <!-- Step 1: Objectif -->
    <div class="onb-step active" id="onb-step-0">
      <div class="onb-header">
        <div class="onb-eyebrow">Étape 1 sur 3</div>
        <h1 class="onb-title">QUEL EST<br>VOTRE OBJECTIF ?</h1>
        <p class="onb-subtitle">Nous personnaliserons votre programme en fonction de vos ambitions.</p>
      </div>
      <div class="onb-choices">
        <div class="onb-choice" data-val="weight" onclick="selectOnb(this,'goal')">
          <div class="onb-choice-icon">⚡</div>
          <div>
            <div class="onb-choice-label">Perte de poids</div>
            <div class="onb-choice-desc">Brûler des calories, affiner la silhouette</div>
          </div>
          <div class="onb-check">✓</div>
        </div>
        <div class="onb-choice" data-val="perf" onclick="selectOnb(this,'goal')">
          <div class="onb-choice-icon">🏆</div>
          <div>
            <div class="onb-choice-label">Performance sportive</div>
            <div class="onb-choice-desc">Améliorer endurance, vitesse, records</div>
          </div>
          <div class="onb-check">✓</div>
        </div>
        <div class="onb-choice" data-val="wellness" onclick="selectOnb(this,'goal')">
          <div class="onb-choice-icon">🧘</div>
          <div>
            <div class="onb-choice-label">Bien-être & Équilibre</div>
            <div class="onb-choice-desc">Détente, flexibilité, qualité de vie</div>
          </div>
          <div class="onb-check">✓</div>
        </div>
      </div>
      <button class="btn btn-primary" onclick="nextOnbStep(1)" id="onb-next-0" style="opacity:.4;pointer-events:none">Continuer →</button>
    </div>

    <!-- Step 2: Niveau -->
    <div class="onb-step" id="onb-step-1">
      <div class="onb-header">
        <div class="onb-eyebrow">Étape 2 sur 3</div>
        <h1 class="onb-title">VOTRE<br>NIVEAU ?</h1>
        <p class="onb-subtitle">Soyez honnête — nous adapterons l'intensité à vous.</p>
      </div>
      <div class="onb-levels">
        <div class="onb-level" data-val="beginner" onclick="selectOnb(this,'level')">
          <div class="onb-level-icon">🌱</div>
          <div class="onb-level-name">Débutant</div>
          <div class="onb-level-sub">Moins de 3 mois de pratique</div>
        </div>
        <div class="onb-level" data-val="intermediate" onclick="selectOnb(this,'level')">
          <div class="onb-level-icon">⚡</div>
          <div class="onb-level-name">Intermédiaire</div>
          <div class="onb-level-sub">Quelques mois de pratique régulière</div>
        </div>
        <div class="onb-level" data-val="advanced" onclick="selectOnb(this,'level')">
          <div class="onb-level-icon">🔥</div>
          <div class="onb-level-name">Avancé</div>
          <div class="onb-level-sub">Pratique intensive depuis plus d'un an</div>
        </div>
      </div>
      <div style="display:flex;gap:var(--sp-md)">
        <button class="btn btn-secondary" onclick="prevOnbStep(0)" style="flex:0 0 auto">← Retour</button>
        <button class="btn btn-primary w-full" onclick="nextOnbStep(2)" id="onb-next-1" style="opacity:.4;pointer-events:none">Continuer →</button>
      </div>
    </div>

    <!-- Step 3: Prénom -->
    <div class="onb-step" id="onb-step-2">
      <div class="onb-header">
        <div class="onb-eyebrow">Étape 3 sur 3</div>
        <h1 class="onb-title">COMMENT<br>VOUS APPELER ?</h1>
        <p class="onb-subtitle">Votre coach virtuel utilisera ce prénom pour vous motiver.</p>
      </div>
      <div class="form-group">
        <label class="form-label">Votre prénom</label>
        <input type="text" id="onb-name" class="form-input" placeholder="Ex: Ali" oninput="onbNameInput(this.value)" style="font-size:1.2rem;padding:16px 20px">
      </div>
      <div style="display:flex;gap:var(--sp-md)">
        <button class="btn btn-secondary" onclick="prevOnbStep(1)" style="flex:0 0 auto">← Retour</button>
        <button class="btn btn-primary w-full" onclick="finishOnboarding()" id="onb-next-2" style="opacity:.4;pointer-events:none">🚀 Lancer Ali-Run</button>
      </div>
    </div>
  </div>
</div>

<!-- ════════════════════════════════════════
     APP SHELL
════════════════════════════════════════ -->
<div id="app-shell">

  <!-- SIDEBAR -->
  <aside class="sidebar" id="sidebar">
    <div class="sidebar-logo">
      <div class="sidebar-logo-text">ALI<span>-</span>RUN</div>
      <div class="sidebar-logo-sub">Move · Relax · Progress</div>
    </div>

    <nav class="sidebar-nav">
      <div class="sidebar-section">Principal</div>
      <div class="nav-item active" data-page="dashboard" onclick="navigate('dashboard',this)">
        <div class="nav-item-icon">🏠</div>
        <span>Dashboard</span>
      </div>
      <div class="nav-item" data-page="run" onclick="navigate('run',this)">
        <div class="nav-item-icon">🏃</div>
        <span>Course</span>
        <span class="nav-item-badge">GPS</span>
      </div>
      <div class="nav-item" data-page="yoga" onclick="navigate('yoga',this)">
        <div class="nav-item-icon">🧘</div>
        <span>Yoga</span>
      </div>

      <div class="sidebar-section">Suivi</div>
      <div class="nav-item" data-page="progress" onclick="navigate('progress',this)">
        <div class="nav-item-icon">📊</div>
        <span>Progression</span>
      </div>
      <div class="nav-item" data-page="profile" onclick="navigate('profile',this)">
        <div class="nav-item-icon">👤</div>
        <span>Profil</span>
      </div>
    </nav>

    <div class="sidebar-footer">
      <div class="user-compact" onclick="navigate('profile',null)">
        <div class="user-avatar-sm" id="sidebar-avatar">A</div>
        <div>
          <div class="user-compact-name" id="sidebar-name">Utilisateur</div>
          <div class="user-compact-role" id="sidebar-level">Débutant · Lv.7</div>
        </div>
        <div class="user-compact-more">⋯</div>
      </div>
    </div>
  </aside>

  <!-- MAIN -->
  <div class="main-area">

    <!-- TOPBAR -->
    <header class="topbar">
      <div class="topbar-left">
        <button class="mobile-menu-btn" onclick="toggleSidebar()">☰</button>
        <div>
          <div class="topbar-title" id="topbar-title">Dashboard</div>
          <div class="topbar-subtitle" id="topbar-subtitle">Bienvenue sur Ali-Run</div>
        </div>
      </div>
      <div class="topbar-right">
        <div style="position:relative">
          <button class="topbar-btn" id="notif-btn" onclick="toggleNotif()">
            🔔
            <div class="notif-dot" id="notif-dot"></div>
          </button>
          <div class="notif-dropdown" id="notif-dropdown">
            <div class="notif-dd-header">
              <span class="notif-dd-title">Notifications</span>
              <span class="notif-dd-clear" onclick="clearNotifs()">Tout lire</span>
            </div>
            <div class="notif-item" onclick="closeNotif()">
              <div class="notif-item-dot"></div>
              <div>
                <div class="notif-item-text">🏆 Nouveau badge débloqué : <strong>Premier 5km</strong></div>
                <div class="notif-item-time">Il y a 2 min</div>
              </div>
            </div>
            <div class="notif-item" onclick="closeNotif()">
              <div class="notif-item-dot"></div>
              <div>
                <div class="notif-item-text">👥 Sofia R. vous a lancé un défi de course</div>
                <div class="notif-item-time">Il y a 1 heure</div>
              </div>
            </div>
            <div class="notif-item" onclick="closeNotif()">
              <div class="notif-item-dot read"></div>
              <div>
                <div class="notif-item-text">🧘 Votre séance yoga du soir commence dans 30 min</div>
                <div class="notif-item-time">Hier, 19:30</div>
              </div>
            </div>
            <div class="notif-item" onclick="closeNotif()">
              <div class="notif-item-dot read"></div>
              <div>
                <div class="notif-item-text">⚡ Vous avez gagné 250 XP cette semaine !</div>
                <div class="notif-item-time">Hier, 12:00</div>
              </div>
            </div>
          </div>
        </div>
        <div class="topbar-user" onclick="navigate('profile',null)">
          <div class="topbar-avatar" id="topbar-avatar">A</div>
          <span class="topbar-user-name" id="topbar-name">Ali</span>
        </div>
      </div>
    </header>

    <!-- PAGES -->
    <div class="pages">

      <!-- ─ DASHBOARD ─ -->
      <div class="page active" id="page-dashboard">
        <div class="dashboard-grid">

          <!-- Welcome card -->
          <div class="welcome-card card">
            <div class="welcome-card-bg"></div>
            <div class="welcome-card-grid"></div>
            <div class="welcome-greeting">Bonjour 👋</div>
            <div class="welcome-name" id="welcome-name">Ali</div>
            <div class="welcome-tagline">Vous êtes à <strong>3 séances</strong> de votre record personnel ce mois-ci !</div>
            <div class="welcome-stats">
              <div class="welcome-stat-item">
                <div class="welcome-stat-val" id="dash-dist">24.7</div>
                <div class="welcome-stat-label">km ce mois</div>
              </div>
              <div class="welcome-stat-item">
                <div class="welcome-stat-val" id="dash-cal">3,840</div>
                <div class="welcome-stat-label">kcal brûlées</div>
              </div>
              <div class="welcome-stat-item">
                <div class="welcome-stat-val" id="dash-sessions">12</div>
                <div class="welcome-stat-label">séances</div>
              </div>
              <div class="welcome-streak">
                <div class="welcome-streak-num">7</div>
                <div class="welcome-streak-label">🔥 jours streak</div>
              </div>
            </div>
          </div>

          <!-- Quick stats -->
          <div class="quick-stat-card card">
            <div class="qs-header">
              <div class="qs-icon qs-icon-blue">🏃</div>
              <span class="badge badge-green">+12%</span>
            </div>
            <div class="qs-val">5.4 <span class="qs-unit">km</span></div>
            <div class="qs-label">Distance moyenne / run</div>
            <div class="qs-trend trend-up">↑ vs semaine dernière</div>
          </div>

          <div class="quick-stat-card card">
            <div class="qs-header">
              <div class="qs-icon qs-icon-green">⚡</div>
              <span class="badge badge-amber">3 450</span>
            </div>
            <div class="qs-val">Nv. <span class="qs-unit">7</span></div>
            <div class="qs-label">Niveau actuel</div>
            <div class="qs-trend">
              <div style="flex:1;height:4px;background:var(--c-surface3);border-radius:2px;overflow:hidden">
                <div style="width:72%;height:100%;background:var(--c-blue-l);border-radius:2px"></div>
              </div>
              <span style="font-size:11px;color:var(--c-txt3)">72%</span>
            </div>
          </div>

          <div class="quick-stat-card card">
            <div class="qs-header">
              <div class="qs-icon qs-icon-amber">🧘</div>
              <span class="badge badge-blue">Ce mois</span>
            </div>
            <div class="qs-val">8 <span class="qs-unit">séances</span></div>
            <div class="qs-label">Yoga complétées</div>
            <div class="qs-trend trend-up">↑ +3 vs mois dernier</div>
          </div>

          <!-- Weekly goals -->
          <div class="goals-card card">
            <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:var(--sp-md)">
              <h3 style="font-size:16px;font-weight:600">Objectifs de la semaine</h3>
              <span class="badge badge-blue">Lun — Dim</span>
            </div>
            <div class="goal-row">
              <div class="goal-icon" style="background:rgba(37,99,235,0.12)">🏃</div>
              <div class="goal-info">
                <div class="goal-name">Distance de course</div>
                <div class="goal-progress-row">
                  <div class="goal-bar"><div class="goal-bar-fill" style="width:68%;background:var(--c-blue-l)"></div></div>
                  <span class="goal-pct">68%</span>
                </div>
              </div>
              <div style="font-family:var(--f-mono);font-size:13px;color:var(--c-txt2)">17 / 25 km</div>
            </div>
            <div class="goal-row">
              <div class="goal-icon" style="background:rgba(16,185,129,0.12)">🔥</div>
              <div class="goal-info">
                <div class="goal-name">Calories brûlées</div>
                <div class="goal-progress-row">
                  <div class="goal-bar"><div class="goal-bar-fill" style="width:85%;background:var(--c-green)"></div></div>
                  <span class="goal-pct">85%</span>
                </div>
              </div>
              <div style="font-family:var(--f-mono);font-size:13px;color:var(--c-txt2)">1,700 / 2,000</div>
            </div>
            <div class="goal-row">
              <div class="goal-icon" style="background:rgba(212,197,169,0.12)">🧘</div>
              <div class="goal-info">
                <div class="goal-name">Minutes de yoga</div>
                <div class="goal-progress-row">
                  <div class="goal-bar"><div class="goal-bar-fill" style="width:40%;background:var(--c-beige)"></div></div>
                  <span class="goal-pct">40%</span>
                </div>
              </div>
              <div style="font-family:var(--f-mono);font-size:13px;color:var(--c-txt2)">80 / 200 min</div>
            </div>
            <div class="goal-row" style="border-bottom:none">
              <div class="goal-icon" style="background:rgba(245,158,11,0.12)">⚡</div>
              <div class="goal-info">
                <div class="goal-name">Séances totales</div>
                <div class="goal-progress-row">
                  <div class="goal-bar"><div class="goal-bar-fill" style="width:60%;background:var(--c-amber)"></div></div>
                  <span class="goal-pct">60%</span>
                </div>
              </div>
              <div style="font-family:var(--f-mono);font-size:13px;color:var(--c-txt2)">3 / 5 séances</div>
            </div>
          </div>

          <!-- Recent sessions -->
          <div class="sessions-card card">
            <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:var(--sp-md)">
              <h3 style="font-size:16px;font-weight:600">Sessions récentes</h3>
              <span style="font-size:12px;color:var(--c-blue-l);cursor:pointer" onclick="navigate('run',null)">Voir tout →</span>
            </div>
            <div class="session-item">
              <div class="session-type-icon" style="background:rgba(37,99,235,0.12)">🏃</div>
              <div class="session-info">
                <div class="session-name">Run du matin</div>
                <div class="session-meta">Aujourd'hui · 06:45 · 28 min</div>
              </div>
              <div class="session-val">5.2 km</div>
            </div>
            <div class="session-item">
              <div class="session-type-icon" style="background:rgba(212,197,169,0.12)">🧘</div>
              <div class="session-info">
                <div class="session-name">Yoga Récupération</div>
                <div class="session-meta">Hier · 20:15 · 20 min</div>
              </div>
              <div class="session-val">200 kcal</div>
            </div>
            <div class="session-item">
              <div class="session-type-icon" style="background:rgba(37,99,235,0.12)">🏃</div>
              <div class="session-info">
                <div class="session-name">Interval training</div>
                <div class="session-meta">Lundi · 07:00 · 35 min</div>
              </div>
              <div class="session-val">6.4 km</div>
            </div>
            <div class="session-item">
              <div class="session-type-icon" style="background:rgba(16,185,129,0.12)">💪</div>
              <div class="session-info">
                <div class="session-name">Yoga Renforcement</div>
                <div class="session-meta">Dimanche · 18:00 · 30 min</div>
              </div>
              <div class="session-val">310 kcal</div>
            </div>
          </div>

          <!-- Activity chart -->
          <div class="chart-card card">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <h3 style="font-size:16px;font-weight:600">Activité hebdomadaire</h3>
              <div style="display:flex;gap:6px">
                <button class="badge badge-blue" onclick="setChartMode('km',this)" style="cursor:pointer">km</button>
                <button class="badge" onclick="setChartMode('kcal',this)" style="cursor:pointer;background:var(--c-surface2);color:var(--c-txt2)">kcal</button>
                <button class="badge" onclick="setChartMode('min',this)" style="cursor:pointer;background:var(--c-surface2);color:var(--c-txt2)">min</button>
              </div>
            </div>
            <div class="chart-bars" id="week-chart"></div>
          </div>
        </div>
      </div>

      <!-- ─ RUN PAGE ─ -->
      <div class="page" id="page-run">
        <div class="run-layout">
          <div style="display:flex;flex-direction:column;gap:var(--sp-lg)">
            <div class="gps-card">
              <div class="gps-map">
                <div id="mapbox-container"></div>
                <div class="map-label"><div class="gps-dot"></div><span id="gps-status">GPS en attente...</span></div>
                <div style="position:absolute;bottom:var(--sp-md);right:var(--sp-md);display:flex;gap:6px">
                  <div style="background:rgba(7,7,16,0.85);border:1px solid var(--c-border2);border-radius:var(--r-sm);padding:5px 10px;font-size:11px;color:var(--c-txt2)" id="gps-coords">📍 Localisation...</div>
                </div>
              </div>
              <div class="run-stats-grid">
                <div class="run-stat">
                  <div class="run-stat-val" id="run-dist">4.20</div>
                  <div class="run-stat-unit">km</div>
                  <div class="run-stat-label">Distance</div>
                </div>
                <div class="run-stat">
                  <div class="run-stat-val" id="run-time">24:06</div>
                  <div class="run-stat-unit">mm:ss</div>
                  <div class="run-stat-label">Temps</div>
                </div>
                <div class="run-stat">
                  <div class="run-stat-val" id="run-cal">287</div>
                  <div class="run-stat-unit">kcal</div>
                  <div class="run-stat-label">Calories</div>
                </div>
              </div>
              <div class="run-controls">
                <button class="run-btn run-btn-sec" onclick="showToast('Musique','🎵 Playlist activée','info')" title="Musique">🎵</button>
                <button class="run-btn run-btn-main" id="run-play-btn" onclick="toggleRun()">▶</button>
                <button class="run-btn run-btn-stop" onclick="stopRun()" title="Arrêter">⏹</button>
              </div>
            </div>

            <!-- Run history -->
            <div class="card">
              <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:var(--sp-lg)">
                <h3 style="font-size:16px;font-weight:600">Historique des courses</h3>
                <span class="badge badge-beige">Ce mois</span>
              </div>
              <div class="run-history-list">
                <div class="run-hist-item"><div style="width:34px;height:34px;border-radius:10px;background:rgba(37,99,235,0.12);display:flex;align-items:center;justify-content:center;font-size:1rem">🏃</div><div class="run-hist-info"><div class="run-hist-name">Run du matin</div><div class="run-hist-meta">Aujourd'hui · 06:45 · Pace 5:32/km</div></div><div class="run-hist-dist">5.2 km</div></div>
                <div class="run-hist-item"><div style="width:34px;height:34px;border-radius:10px;background:rgba(37,99,235,0.12);display:flex;align-items:center;justify-content:center;font-size:1rem">⚡</div><div class="run-hist-info"><div class="run-hist-name">Interval training</div><div class="run-hist-meta">Lundi · 07:00 · Pace 5:12/km</div></div><div class="run-hist-dist">6.4 km</div></div>
                <div class="run-hist-item"><div style="width:34px;height:34px;border-radius:10px;background:rgba(37,99,235,0.12);display:flex;align-items:center;justify-content:center;font-size:1rem">🌅</div><div class="run-hist-info"><div class="run-hist-name">Course longue</div><div class="run-hist-meta">Samedi · 08:30 · Pace 5:48/km</div></div><div class="run-hist-dist">12.1 km</div></div>
                <div class="run-hist-item"><div style="width:34px;height:34px;border-radius:10px;background:rgba(37,99,235,0.12);display:flex;align-items:center;justify-content:center;font-size:1rem">🏃</div><div class="run-hist-info"><div class="run-hist-name">Run récupération</div><div class="run-hist-meta">Vendredi · 18:00 · Pace 6:15/km</div></div><div class="run-hist-dist">3.8 km</div></div>
              </div>
            </div>
          </div>

          <!-- Run sidebar -->
          <div class="run-sidebar">
            <div class="card">
              <div style="font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--c-txt3);margin-bottom:var(--sp-md)">Allure actuelle</div>
              <div class="pace-display">5:42 <span class="pace-unit">/km</span></div>
              <div style="font-size:13px;color:var(--c-txt2)">Zone d'intensité</div>
              <div class="pace-zone">
                <div class="zone-seg z1"></div>
                <div class="zone-seg z2"></div>
                <div class="zone-seg" style="background:var(--c-surface3)"></div>
                <div class="zone-seg" style="background:var(--c-surface3)"></div>
              </div>
              <div style="display:flex;justify-content:space-between;margin-top:6px;font-size:11px;color:var(--c-txt3)">
                <span>Facile</span><span>Zone 2</span><span>Intensif</span>
              </div>
            </div>

            <div class="audio-coach card">
              <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px">
                <div style="font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--c-txt3)">Coach audio</div>
                <div class="badge badge-green">Actif</div>
              </div>
              <div class="audio-wave">
                <div class="audio-bar" style="height:50%"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
                <div class="audio-bar"></div>
              </div>
              <div class="coach-msg">"Super rythme ! Maintenez cette allure encore 800m, vous êtes dans votre zone optimale."</div>
            </div>

            <div class="card">
              <div style="font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--c-txt3);margin-bottom:var(--sp-md)">Objectif course</div>
              <div style="display:flex;flex-direction:column;gap:12px">
                <div>
                  <div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:6px"><span>Distance</span><span class="mono">4.2 / 5 km</span></div>
                  <div style="height:5px;background:var(--c-surface3);border-radius:3px;overflow:hidden"><div style="width:84%;height:100%;background:var(--c-blue-l);border-radius:3px"></div></div>
                </div>
                <div>
                  <div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:6px"><span>Temps estimé restant</span><span class="mono">~4:45</span></div>
                  <div style="height:5px;background:var(--c-surface3);border-radius:3px;overflow:hidden"><div style="width:84%;height:100%;background:var(--c-green);border-radius:3px"></div></div>
                </div>
              </div>
            </div>

            <div class="card">
              <div style="font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--c-txt3);margin-bottom:var(--sp-md)">Fréquence cardiaque</div>
              <div style="display:flex;align-items:baseline;gap:8px;margin-bottom:var(--sp-md)">
                <span style="font-family:var(--f-mono);font-size:2.5rem;font-weight:600">156</span>
                <span style="color:var(--c-txt2);font-size:14px">bpm</span>
                <span class="badge badge-green" style="margin-left:auto">Zone 2</span>
              </div>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
                <div style="background:var(--c-surface2);border-radius:8px;padding:10px;text-align:center"><div style="font-family:var(--f-mono);font-size:1.1rem;font-weight:600">142</div><div style="font-size:10px;color:var(--c-txt3);margin-top:2px">Min</div></div>
                <div style="background:var(--c-surface2);border-radius:8px;padding:10px;text-align:center"><div style="font-family:var(--f-mono);font-size:1.1rem;font-weight:600">168</div><div style="font-size:10px;color:var(--c-txt3);margin-top:2px">Max</div></div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- ─ YOGA PAGE ─ -->
      <div class="page" id="page-yoga">
        <div class="yoga-header">
          <div>
            <div style="font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--c-beige);margin-bottom:6px">Votre programme yoga</div>
            <div style="font-family:var(--f-display);font-size:2.2rem;letter-spacing:.02em;line-height:1">DÉTENTE & RENFORCEMENT</div>
            <div style="font-size:14px;color:var(--c-txt2);margin-top:8px">8 séances recommandées cette semaine · 3 complétées</div>
          </div>
          <div style="text-align:center;background:rgba(212,197,169,0.1);border:1px solid rgba(212,197,169,0.2);border-radius:var(--r-lg);padding:var(--sp-lg) var(--sp-xl)">
            <div style="font-family:var(--f-mono);font-size:2rem;font-weight:600;color:var(--c-beige)">240</div>
            <div style="font-size:12px;color:var(--c-txt2)">minutes ce mois</div>
          </div>
        </div>

        <div class="yoga-cat-tabs">
          <div class="yoga-cat-tab active" onclick="filterYoga('all',this)">Toutes</div>
          <div class="yoga-cat-tab" onclick="filterYoga('relaxation',this)">🌙 Relaxation</div>
          <div class="yoga-cat-tab" onclick="filterYoga('recovery',this)">🔄 Récupération</div>
          <div class="yoga-cat-tab" onclick="filterYoga('strength',this)">💪 Renforcement</div>
          <div class="yoga-cat-tab" onclick="filterYoga('balance',this)">⚖️ Équilibre</div>
          <div class="yoga-cat-tab" onclick="filterYoga('morning',this)">☀️ Matin</div>
        </div>

        <div class="yoga-grid" id="yoga-grid"></div>
      </div>

      <!-- ─ PROGRESS PAGE ─ -->
      <div class="page" id="page-progress">
        <div class="progress-grid">

          <!-- Weight chart -->
          <div class="progress-big card">
            <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:var(--sp-md)">
              <div>
                <h3 style="font-size:16px;font-weight:600">Évolution du poids</h3>
                <div style="font-size:13px;color:var(--c-txt2);margin-top:3px">Objectif : 72 kg (-3 kg)</div>
              </div>
              <div style="display:flex;align-items:center;gap:var(--sp-sm)">
                <input type="number" id="weight-in" class="weight-input" placeholder="75.0" step="0.1">
                <span style="font-size:14px;color:var(--c-txt2)">kg</span>
                <button class="btn btn-primary btn-sm" onclick="addWeight()">+ Ajouter</button>
              </div>
            </div>
            <div class="chart-svg-wrap" id="weight-chart-wrap">
              <svg id="weight-chart" viewBox="0 0 600 160" xmlns="http://www.w3.org/2000/svg" width="100%" height="160">
                <defs>
                  <linearGradient id="weightGrad" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stop-color="#3B82F6" stop-opacity="0.25"/>
                    <stop offset="100%" stop-color="#3B82F6" stop-opacity="0"/>
                  </linearGradient>
                </defs>
                <path id="weight-area" fill="url(#weightGrad)"/>
                <path id="weight-line" fill="none" stroke="#3B82F6" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
                <line x1="0" y1="130" x2="600" y2="130" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="0" y1="95" x2="600" y2="95" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="0" y1="60" x2="600" y2="60" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <line x1="0" y1="25" x2="600" y2="25" stroke="rgba(255,255,255,0.04)" stroke-width="1"/>
                <!-- Target line -->
                <line x1="0" y1="110" x2="600" y2="110" stroke="rgba(16,185,129,0.3)" stroke-width="1.5" stroke-dasharray="6,4"/>
                <text x="5" y="107" fill="rgba(16,185,129,0.6)" font-size="10" font-family="JetBrains Mono, monospace">72 kg</text>
              </svg>
            </div>
            <div style="display:flex;gap:var(--sp-lg);margin-top:var(--sp-md)">
              <div><div style="font-family:var(--f-mono);font-size:1.3rem;font-weight:600">75.2</div><div style="font-size:12px;color:var(--c-txt2)">Poids actuel</div></div>
              <div><div style="font-family:var(--f-mono);font-size:1.3rem;font-weight:600;color:var(--c-green-l)">-1.8 kg</div><div style="font-size:12px;color:var(--c-txt2)">Perte totale</div></div>
              <div><div style="font-family:var(--f-mono);font-size:1.3rem;font-weight:600;color:var(--c-blue-xl)">-3.0 kg</div><div style="font-size:12px;color:var(--c-txt2)">Objectif restant</div></div>
            </div>
          </div>

          <!-- XP & Level -->
          <div class="card" style="display:flex;flex-direction:column;gap:var(--sp-lg)">
            <h3 style="font-size:16px;font-weight:600">Niveau & XP</h3>
            <div class="xp-bar-wrap" style="background:var(--c-surface2)">
              <div class="xp-header">
                <div>
                  <div class="xp-level">NIVEAU 7</div>
                  <div style="font-size:12px;color:var(--c-txt2)">Coureur Régulier</div>
                </div>
                <div style="text-align:right">
                  <div style="font-family:var(--f-mono);font-size:1rem;font-weight:600">3,450 / 4,800 XP</div>
                  <div style="font-size:11px;color:var(--c-txt3)">Prochain niveau</div>
                </div>
              </div>
              <div class="xp-bar"><div class="xp-bar-fill" style="width:72%"></div></div>
              <div style="font-size:12px;color:var(--c-txt3);margin-top:8px">1,350 XP pour le niveau 8</div>
            </div>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
              <div style="background:var(--c-surface2);border-radius:10px;padding:12px;text-align:center">
                <div style="font-family:var(--f-mono);font-size:1.5rem;font-weight:600;color:var(--c-blue-xl)">12</div>
                <div style="font-size:11px;color:var(--c-txt3);margin-top:3px">Séances ce mois</div>
              </div>
              <div style="background:var(--c-surface2);border-radius:10px;padding:12px;text-align:center">
                <div style="font-family:var(--f-mono);font-size:1.5rem;font-weight:600;color:var(--c-amber)">7 🔥</div>
                <div style="font-size:11px;color:var(--c-txt3);margin-top:3px">Jours consécutifs</div>
              </div>
              <div style="background:var(--c-surface2);border-radius:10px;padding:12px;text-align:center">
                <div style="font-family:var(--f-mono);font-size:1.5rem;font-weight:600;color:var(--c-green-l)">24.7</div>
                <div style="font-size:11px;color:var(--c-txt3);margin-top:3px">km totaux</div>
              </div>
              <div style="background:var(--c-surface2);border-radius:10px;padding:12px;text-align:center">
                <div style="font-family:var(--f-mono);font-size:1.5rem;font-weight:600;color:var(--c-beige)">6</div>
                <div style="font-size:11px;color:var(--c-txt3);margin-top:3px">Badges obtenus</div>
              </div>
            </div>
          </div>

          <!-- Achievements -->
          <div class="card" style="grid-column:1/-1">
            <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:var(--sp-lg)">
              <h3 style="font-size:16px;font-weight:600">Badges & Récompenses</h3>
              <span class="badge badge-amber">6 / 20 obtenus</span>
            </div>
            <div class="achievements-grid" id="achievements-grid"></div>
          </div>

          <!-- Monthly stats table -->
          <div class="card" style="grid-column:1/-1">
            <h3 style="font-size:16px;font-weight:600;margin-bottom:var(--sp-lg)">Statistiques mensuelles</h3>
            <div style="overflow-x:auto">
              <table style="width:100%;border-collapse:collapse;font-size:14px">
                <thead>
                  <tr style="border-bottom:1px solid var(--c-border)">
                    <th style="text-align:left;padding:10px 12px;color:var(--c-txt3);font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em">Mois</th>
                    <th style="text-align:right;padding:10px 12px;color:var(--c-txt3);font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em">Distance</th>
                    <th style="text-align:right;padding:10px 12px;color:var(--c-txt3);font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em">Calories</th>
                    <th style="text-align:right;padding:10px 12px;color:var(--c-txt3);font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em">Séances</th>
                    <th style="text-align:right;padding:10px 12px;color:var(--c-txt3);font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em">Yoga</th>
                    <th style="text-align:right;padding:10px 12px;color:var(--c-txt3);font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.08em">XP gagnés</th>
                  </tr>
                </thead>
                <tbody id="stats-table"></tbody>
              </table>
            </div>
          </div>
        </div>
      </div>

      <!-- ─ PROFILE PAGE ─ -->
      <div class="page" id="page-profile">
        <div class="profile-hero">
          <div class="profile-avatar" id="profile-avatar-big">A</div>
          <div>
            <div class="profile-name" id="profile-name-big">Ali</div>
            <div class="profile-email" id="profile-email-big">ali@alirun.app</div>
            <div class="profile-tags">
              <span class="badge badge-blue" id="profile-obj-badge">Bien-être</span>
              <span class="badge badge-beige" id="profile-level-badge">Débutant</span>
              <span class="badge badge-green">Niveau 7</span>
              <span class="badge badge-amber">🔥 7 jours</span>
            </div>
          </div>
          <div style="margin-left:auto;display:flex;flex-direction:column;gap:8px">
            <button class="btn btn-secondary btn-sm" onclick="showToast('Profil','✏️ Modification en cours...','info')">Modifier le profil</button>
            <button class="btn btn-secondary btn-sm" onclick="showToast('Photo','📷 Sélection photo...','info')">Changer la photo</button>
          </div>
        </div>

        <div class="settings-sections">
          <div class="settings-group">
            <div class="settings-group-title">Compte</div>
            <div class="settings-item" onclick="showToast('Profil','👤 Informations personnelles','info')">
              <div class="settings-item-icon">👤</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Informations personnelles</div>
                <div class="settings-item-sub">Nom, prénom, date de naissance</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
            <div class="settings-item" onclick="showToast('Email','📧 Modifier votre e-mail','info')">
              <div class="settings-item-icon">📧</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Adresse e-mail</div>
                <div class="settings-item-sub" id="settings-email">ali@alirun.app</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
            <div class="settings-item" onclick="showToast('Sécurité','🔑 Modification du mot de passe','info')">
              <div class="settings-item-icon">🔑</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Mot de passe</div>
                <div class="settings-item-sub">Dernière modification il y a 30 jours</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
          </div>

          <div class="settings-group">
            <div class="settings-group-title">Préférences</div>
            <div class="settings-item">
              <div class="settings-item-icon">🌍</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Langue</div>
                <div class="settings-item-sub">Français</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
            <div class="settings-item">
              <div class="settings-item-icon">🔔</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Notifications push</div>
                <div class="settings-item-sub">Rappels, défis, streaks</div>
              </div>
              <label class="toggle"><input type="checkbox" checked><div class="toggle-slider"></div></label>
            </div>
            <div class="settings-item">
              <div class="settings-item-icon">🎵</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Coaching audio</div>
                <div class="settings-item-sub">Conseils vocaux pendant la course</div>
              </div>
              <label class="toggle"><input type="checkbox" checked><div class="toggle-slider"></div></label>
            </div>
          </div>

          <div class="settings-group">
            <div class="settings-group-title">Sport & Santé</div>
            <div class="settings-item" onclick="showToast('Objectifs','🎯 Modifier vos objectifs','info')">
              <div class="settings-item-icon">🎯</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Mes objectifs</div>
                <div class="settings-item-sub" id="settings-goal">Bien-être & Équilibre</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
            <div class="settings-item" onclick="showToast('Niveau','⚡ Modifier votre niveau','info')">
              <div class="settings-item-icon">⚡</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Niveau sportif</div>
                <div class="settings-item-sub" id="settings-level">Débutant</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
            <div class="settings-item" onclick="showToast('Santé','💓 Données de santé','info')">
              <div class="settings-item-icon">💓</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Données physiologiques</div>
                <div class="settings-item-sub">Poids, taille, âge, FC max</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
          </div>

          <div class="settings-group">
            <div class="settings-group-title">Confidentialité</div>
            <div class="settings-item">
              <div class="settings-item-icon">👁</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Profil public</div>
                <div class="settings-item-sub">Visible dans les classements</div>
              </div>
              <label class="toggle"><input type="checkbox" checked><div class="toggle-slider"></div></label>
            </div>
            <div class="settings-item">
              <div class="settings-item-icon">📍</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Partage de localisation</div>
                <div class="settings-item-sub">Utilisé uniquement en course</div>
              </div>
              <label class="toggle"><input type="checkbox" checked><div class="toggle-slider"></div></label>
            </div>
            <div class="settings-item" onclick="showToast('Données','📥 Export en cours...','info')">
              <div class="settings-item-icon">📥</div>
              <div class="settings-item-info">
                <div class="settings-item-label">Exporter mes données</div>
                <div class="settings-item-sub">Format JSON ou CSV</div>
              </div>
              <div class="settings-item-arrow">›</div>
            </div>
          </div>
        </div>

        <button class="logout-btn" onclick="doLogout()">
          <span>🚪</span> Se déconnecter de Ali-Run
        </button>
      </div>

    </div><!-- /pages -->
  </div><!-- /main-area -->
</div><!-- /app-shell -->

<!-- Yoga modal -->
<div class="yoga-modal-overlay" id="yoga-modal-overlay" onclick="closeYogaModal(event)">
  <div class="yoga-modal">
    <button class="yoga-modal-close" onclick="closeYogaModal()">✕</button>
    <div class="yoga-player-header">
      <span class="yoga-player-icon" id="modal-icon">🧘</span>
      <h2 style="font-family:var(--f-display);font-size:1.8rem;letter-spacing:.03em" id="modal-title">Relaxation du soir</h2>
      <p style="font-size:14px;color:var(--c-txt2);margin-top:6px" id="modal-meta">20 min · Débutant · Relaxation</p>
    </div>
    <div class="yoga-progress-ring">
      <svg width="120" height="120" viewBox="0 0 120 120">
        <circle cx="60" cy="60" r="52" fill="none" stroke="rgba(255,255,255,0.06)" stroke-width="6"/>
        <circle id="yoga-ring" cx="60" cy="60" r="52" fill="none" stroke="#3B82F6" stroke-width="6"
          stroke-dasharray="326.7" stroke-dashoffset="326.7"
          stroke-linecap="round" transform="rotate(-90 60 60)"
          style="transition:stroke-dashoffset .5s ease"/>
        <text id="yoga-ring-label" x="50%" y="54%" text-anchor="middle" dominant-baseline="middle"
          fill="white" font-family="JetBrains Mono" font-size="18" font-weight="600">0%</text>
      </svg>
    </div>
    <div class="yoga-timer" id="yoga-timer">20:00</div>
    <div class="yoga-player-controls">
      <button class="run-btn run-btn-sec" onclick="showToast('Yoga','⏮ Séquence précédente','info')">⏮</button>
      <button class="run-btn run-btn-main" id="yoga-play-btn" onclick="toggleYoga()">▶</button>
      <button class="run-btn run-btn-sec" onclick="showToast('Yoga','⏭ Séquence suivante','info')">⏭</button>
    </div>
    <div style="text-align:center;margin-top:var(--sp-lg);font-size:13px;color:var(--c-txt2)">
      Pose actuelle : <strong style="color:var(--c-txt)" id="modal-pose">Posture de l'enfant (Balasana)</strong>
    </div>
  </div>
</div>

<!-- Toast container -->
<div id="toast-container"></div>

<!-- ════════════════════════════════════════
     JAVASCRIPT
════════════════════════════════════════ -->
<script>
/* ═══ STATE ═══ */
window.state = {
  user: null,
  onb: { goal: null, level: null, name: '' },
  runActive: false, runTimer: null, runSeconds: 1446,
  yogaActive: false, yogaTimer: null, yogaTotalSec: 1200, yogaElapsed: 0,
  chartMode: 'km',
  weightData: [77.0, 76.5, 76.2, 75.8, 75.6, 75.2, 75.0, 75.2],
};

const DAYS = ['Lun','Mar','Mer','Jeu','Ven','Sam','Dim'];
const CHART_DATA = {
  km:   [0, 5.2, 0, 6.4, 3.1, 12.1, 5.8],
  kcal: [0, 380, 0, 460, 240, 830, 420],
  min:  [0, 28, 0, 35, 20, 72, 32],
};

/* ═══ LOADING ═══ */
window.addEventListener('load', () => {
  setTimeout(() => {
    const ld = document.getElementById('loading');
    ld.style.opacity = '0';
    setTimeout(() => ld.style.display = 'none', 500);
  }, 1600);
});

/* ═══ TOAST ═══ */
function showToast(title, msg, type = 'info') {
  const icons = { success:'✅', error:'❌', info:'💬' };
  const tc = document.getElementById('toast-container');
  const t = document.createElement('div');
  t.className = `toast toast-${type}`;
  t.innerHTML = `<span class="toast-icon">${icons[type]||'💬'}</span><div><div style="font-weight:600;font-size:13px">${title}</div><div style="color:var(--c-txt2);font-size:12px;margin-top:2px">${msg}</div></div>`;
  tc.appendChild(t);
  setTimeout(() => { t.classList.add('removing'); setTimeout(() => t.remove(), 300); }, 3500);
}

/* ═══ AUTH TABS ═══ */
document.querySelectorAll('.auth-tab').forEach(tab => {
  tab.addEventListener('click', () => {
    const id = tab.dataset.tab;
    document.querySelectorAll('.auth-tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.auth-panel').forEach(p => p.classList.remove('active'));
    tab.classList.add('active');
    document.getElementById(`panel-${id}`).classList.add('active');
  });
});

/* ═══ PASSWORD TOGGLE ═══ */
document.querySelectorAll('.pwd-toggle').forEach(btn => {
  btn.addEventListener('click', () => {
    const inp = document.getElementById(btn.dataset.target);
    inp.type = inp.type === 'password' ? 'text' : 'password';
    btn.textContent = inp.type === 'password' ? '👁' : '🙈';
  });
});

/* ═══ PASSWORD STRENGTH ═══ */
function checkStrength(val) {
  const segs = [document.getElementById('s1'), document.getElementById('s2'), document.getElementById('s3'), document.getElementById('s4')];
  const lbl = document.getElementById('strength-label');
  segs.forEach(s => { s.className = 'strength-seg'; });
  if (!val) { lbl.textContent = 'Entrez un mot de passe'; lbl.style.color = 'var(--c-txt3)'; return; }
  let score = 0;
  if (val.length >= 8) score++;
  if (/[A-Z]/.test(val)) score++;
  if (/[0-9]/.test(val)) score++;
  if (/[^a-zA-Z0-9]/.test(val)) score++;
  const labels = ['','Faible','Moyen','Fort','Excellent'];
  const colors = ['','var(--c-red)','var(--c-amber)','var(--c-green)','var(--c-green)'];
  const cls = ['','weak','medium','strong','strong'];
  for (let i = 0; i < score; i++) segs[i].classList.add(cls[score]);
  lbl.textContent = labels[score] || '';
  lbl.style.color = colors[score] || 'var(--c-txt3)';
}

/* ═══ VALIDATION ═══ */
function validateEmail(e) { return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(e); }
function setErr(id, msg) {
  const el = document.getElementById(id);
  if (!el) return;
  el.textContent = msg ? `⚠ ${msg}` : '';
  const inp = el.previousElementSibling?.querySelector?.('input') || el.previousElementSibling;
  if (inp && inp.classList) { msg ? inp.classList.add('error') : inp.classList.remove('error'); }
}

/* ═══ LOGIN ═══ */
function doLogin() {
  const email = document.getElementById('login-email').value.trim();
  const pwd = document.getElementById('login-pwd').value;
  let ok = true;
  setErr('login-email-err',''); setErr('login-pwd-err','');
  if (!validateEmail(email)) { setErr('login-email-err','Adresse e-mail invalide'); ok = false; }
  if (pwd.length < 6) { setErr('login-pwd-err','Mot de passe trop court'); ok = false; }
  if (!ok) return;
  const btn = document.getElementById('btn-login');
  btn.innerHTML = '<span style="display:inline-block;width:16px;height:16px;border:2px solid rgba(255,255,255,0.3);border-top-color:#fff;border-radius:50%;animation:spin .7s linear infinite"></span> Connexion...';
  btn.disabled = true;
  document.head.insertAdjacentHTML('beforeend','<style>@keyframes spin{to{transform:rotate(360deg)}}</style>');
  setTimeout(() => {
    state.user = { name: email.split('@')[0].charAt(0).toUpperCase()+email.split('@')[0].slice(1), email, goal:'wellness', level:'beginner' };
    enterApp();
  }, 1200);
}

/* ═══ SIGNUP ═══ */
function doSignup() {
  const fname = document.getElementById('signup-fname').value.trim();
  const email = document.getElementById('signup-email').value.trim();
  const pwd = document.getElementById('signup-pwd').value;
  let ok = true;
  setErr('signup-fname-err',''); setErr('signup-email-err',''); setErr('signup-pwd-err','');
  if (!fname) { setErr('signup-fname-err','Prénom requis'); ok = false; }
  if (!validateEmail(email)) { setErr('signup-email-err','E-mail invalide'); ok = false; }
  if (pwd.length < 8) { setErr('signup-pwd-err','Min. 8 caractères requis'); ok = false; }
  if (!ok) return;
  state.user = { name: fname, email, goal: null, level: null };
  document.getElementById('auth-screen').classList.add('hidden');
  document.getElementById('onboarding-screen').classList.remove('hidden');
}

function showForgot() { showToast('Mot de passe', '📧 Un lien de réinitialisation a été envoyé à votre e-mail.', 'success'); }

/* ═══ SOCIAL LOGIN ═══ */
function socialLogin(provider) {
  showToast(provider, `🔄 Connexion via ${provider}...`, 'info');
  setTimeout(() => {
    state.user = { name: provider + '_User', email: `user@${provider.toLowerCase()}.com`, goal: null, level: null };
    document.getElementById('auth-screen').classList.add('hidden');
    document.getElementById('onboarding-screen').classList.remove('hidden');
  }, 1000);
}

/* ═══ ONBOARDING ═══ */
function selectOnb(el, type) {
  const siblings = el.parentElement.querySelectorAll('.onb-choice, .onb-level');
  siblings.forEach(s => s.classList.remove('selected'));
  el.classList.add('selected');
  state.onb[type] = el.dataset.val;
  const stepMap = { goal: 0, level: 1 };
  const nextBtn = document.getElementById(`onb-next-${stepMap[type]}`);
  nextBtn.style.opacity = '1'; nextBtn.style.pointerEvents = 'auto';
}
function onbNameInput(v) {
  state.onb.name = v;
  const btn = document.getElementById('onb-next-2');
  btn.style.opacity = v.trim() ? '1' : '0.4';
  btn.style.pointerEvents = v.trim() ? 'auto' : 'none';
}
function nextOnbStep(step) {
  document.querySelectorAll('.onb-step').forEach(s => s.classList.remove('active'));
  document.getElementById(`onb-step-${step}`).classList.add('active');
  document.querySelectorAll('.onb-dot').forEach((d,i) => {
    d.classList.remove('active','done');
    if (i < step) d.classList.add('done');
    else if (i === step) d.classList.add('active');
  });
}
function prevOnbStep(step) { nextOnbStep(step); }

function finishOnboarding() {
  const name = state.onb.name || state.user?.name || 'Ali';
  state.user = { ...state.user, name, goal: state.onb.goal || 'wellness', level: state.onb.level || 'beginner' };
  document.getElementById('onboarding-screen').classList.add('hidden');
  enterApp();
}

/* ═══ ENTER APP ═══ */
window.enterApp = function enterApp() {
  const u = state.user || { name:'Ali', email:'ali@alirun.app', goal:'wellness', level:'beginner' };
  const initials = u.name.slice(0,2).toUpperCase();
  document.getElementById('sidebar-avatar').textContent = initials;
  document.getElementById('topbar-avatar').textContent = initials;
  document.getElementById('sidebar-name').textContent = u.name;
  document.getElementById('topbar-name').textContent = u.name;
  document.getElementById('welcome-name').textContent = u.name.toUpperCase() + ' !';
  document.getElementById('profile-avatar-big').textContent = initials;
  document.getElementById('profile-name-big').textContent = u.name;
  document.getElementById('profile-email-big').textContent = u.email || 'ali@alirun.app';
  document.getElementById('settings-email').textContent = u.email || 'ali@alirun.app';
  const goalLabels = { weight:'Perte de poids', perf:'Performance', wellness:'Bien-être', null:'Bien-être' };
  const levelLabels = { beginner:'Débutant', intermediate:'Intermédiaire', advanced:'Avancé', null:'Débutant' };
  document.getElementById('profile-obj-badge').textContent = goalLabels[u.goal] || 'Bien-être';
  document.getElementById('profile-level-badge').textContent = levelLabels[u.level] || 'Débutant';
  document.getElementById('settings-goal').textContent = goalLabels[u.goal] || 'Bien-être & Équilibre';
  document.getElementById('settings-level').textContent = levelLabels[u.level] || 'Débutant';
  document.getElementById('sidebar-level').textContent = (levelLabels[u.level]||'Débutant') + ' · Lv.7';
  document.getElementById('auth-screen').classList.add('hidden');
  document.getElementById('app-shell').classList.add('active');
  initDashboard();
  initProgress();
  initYoga();
  showToast('Bienvenue', `👋 Content de vous revoir, ${u.name} !`, 'success');
}

/* ═══ NAVIGATION ═══ */
const pageTitles = {
  dashboard: ['Dashboard','Bienvenue sur Ali-Run'],
  run: ['Course GPS','Suivez vos performances en temps réel'],
  yoga: ['Yoga','Séances guidées à domicile'],
  progress: ['Progression','Vos statistiques et objectifs'],
  profile: ['Profil','Paramètres et compte'],
};
function navigate(page, navItem) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById(`page-${page}`).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  if (navItem) navItem.classList.add('active');
  else {
    const match = document.querySelector(`[data-page="${page}"]`);
    if (match) match.classList.add('active');
  }
  const [title, sub] = pageTitles[page] || [page,''];
  document.getElementById('topbar-title').textContent = title;
  document.getElementById('topbar-subtitle').textContent = sub;
  if (page === 'run') setTimeout(initMap, 100);
  if (window.innerWidth < 768) closeSidebar();
}

/* ═══ MOBILE SIDEBAR ═══ */
function toggleSidebar() { document.getElementById('sidebar').classList.toggle('open'); }
function closeSidebar() { document.getElementById('sidebar').classList.remove('open'); }

/* ═══ NOTIFICATIONS ═══ */
function toggleNotif() {
  const dd = document.getElementById('notif-dropdown');
  dd.classList.toggle('open');
  if (dd.classList.contains('open')) {
    document.getElementById('notif-dot').style.display = 'none';
  }
}
function closeNotif() { document.getElementById('notif-dropdown').classList.remove('open'); }
function clearNotifs() {
  document.querySelectorAll('.notif-item-dot').forEach(d => { d.classList.add('read'); });
  showToast('Notifications','✅ Toutes les notifications lues','success');
  closeNotif();
}
document.addEventListener('click', e => {
  if (!e.target.closest('#notif-btn') && !e.target.closest('#notif-dropdown')) closeNotif();
});

/* ═══ DASHBOARD ═══ */
function initDashboard() { renderWeekChart(); }

function renderWeekChart() {
  const data = CHART_DATA[state.chartMode];
  const max = Math.max(...data) || 1;
  const wrap = document.getElementById('week-chart');
  wrap.innerHTML = '';
  const units = { km:'km', kcal:'kcal', min:'min' };
  data.forEach((v, i) => {
    const pct = (v / max) * 100;
    const div = document.createElement('div');
    div.className = 'chart-bar-wrap';
    div.innerHTML = `
      <div class="chart-bar ${v > 0 ? '' : ''}" style="height:${pct || 4}%;min-height:4px;background:${v===Math.max(...data)?'var(--c-blue-l)':'var(--c-surface3)'}"
        title="${v} ${units[state.chartMode]}" onclick="showToast('${DAYS[i]}','${v} ${units[state.chartMode]}','info')">
      </div>
      <div class="chart-day">${DAYS[i]}</div>`;
    wrap.appendChild(div);
  });
  setTimeout(() => {
    wrap.querySelectorAll('.chart-bar').forEach((b, i) => {
      b.style.transition = `height .8s ${i*0.07}s cubic-bezier(0.16,1,0.3,1)`;
    });
  }, 50);
}
function setChartMode(mode, btn) {
  state.chartMode = mode;
  document.querySelectorAll('.chart-card .badge').forEach(b => {
    b.className = 'badge';
    b.style.background = 'var(--c-surface2)'; b.style.color = 'var(--c-txt2)';
  });
  btn.className = 'badge badge-blue';
  btn.style.background = ''; btn.style.color = '';
  renderWeekChart();
}

/* ═══ RUN ═══ */
function toggleRun() {
  state.runActive = !state.runActive;
  const btn = document.getElementById('run-play-btn');
  if (state.runActive) {
    btn.textContent = '⏸'; btn.classList.add('running');
    state.runTimer = setInterval(updateRunTimer, 1000);
    showToast('Course','🏃 Course démarrée ! Bonne chance !','success');
  } else {
    btn.textContent = '▶'; btn.classList.remove('running');
    clearInterval(state.runTimer);
    showToast('Course','⏸ Course mise en pause','info');
  }
}
function updateRunTimer() {
  state.runSeconds++;
  const m = Math.floor(state.runSeconds / 60).toString().padStart(2,'0');
  const s = (state.runSeconds % 60).toString().padStart(2,'0');
  document.getElementById('run-time').textContent = `${m}:${s}`;
  const dist = (state.runSeconds / 342).toFixed(2);
  document.getElementById('run-dist').textContent = dist;
  document.getElementById('run-cal').textContent = Math.round(state.runSeconds * 0.2);
}
function stopRun() {
  if (state.runActive) toggleRun();
  const dist = document.getElementById('run-dist').textContent;
  showToast('Course terminée', `🏁 ${dist} km complétés ! +${Math.round(parseFloat(dist)*80)} XP`, 'success');
  state.runSeconds = 0;
  document.getElementById('run-dist').textContent = '0.00';
  document.getElementById('run-time').textContent = '00:00';
  document.getElementById('run-cal').textContent = '0';
  resetRoute();
}

/* ═══ YOGA ═══ */
const yogaSessions = [
  { id:1, icon:'🌙', name:'Relaxation du soir', meta:'20 min · Débutant', cat:'relaxation', bg:'rgba(99,79,129,0.15)', done:true, pose:'Posture de l\'enfant (Balasana)' },
  { id:2, icon:'🔄', name:'Récupération post-run', meta:'15 min · Débutant', cat:'recovery', bg:'rgba(16,185,129,0.1)', done:true, pose:'Étirement du piriforme' },
  { id:3, icon:'💪', name:'Renforcement du core', meta:'30 min · Intermédiaire', cat:'strength', bg:'rgba(37,99,235,0.12)', done:false, pose:'Planche (Phalakasana)' },
  { id:4, icon:'⚖️', name:'Équilibre & Focus', meta:'25 min · Intermédiaire', cat:'balance', bg:'rgba(245,158,11,0.1)', done:false, pose:'Arbre (Vrksasana)' },
  { id:5, icon:'☀️', name:'Salutation au soleil', meta:'20 min · Débutant', cat:'morning', bg:'rgba(245,158,11,0.12)', done:true, pose:'Chien tête en bas' },
  { id:6, icon:'🫁', name:'Respiration profonde', meta:'10 min · Débutant', cat:'relaxation', bg:'rgba(212,197,169,0.08)', done:false, pose:'Posture du cadavre (Savasana)' },
  { id:7, icon:'🏋️', name:'Yoga Power', meta:'40 min · Avancé', cat:'strength', bg:'rgba(239,68,68,0.08)', done:false, pose:'Guerrier III (Virabhadrasana III)' },
  { id:8, icon:'🌊', name:'Flow dynamique', meta:'35 min · Avancé', cat:'balance', bg:'rgba(37,99,235,0.1)', done:false, pose:'Demi-lune (Ardha Chandrasana)' },
  { id:9, icon:'😴', name:'Yoga Nidra', meta:'30 min · Débutant', cat:'relaxation', bg:'rgba(99,79,129,0.1)', done:false, pose:'Relaxation guidée' },
];
function initYoga() { renderYoga('all'); }
function filterYoga(cat, btn) {
  document.querySelectorAll('.yoga-cat-tab').forEach(t => t.classList.remove('active'));
  btn.classList.add('active');
  renderYoga(cat);
}
function renderYoga(cat) {
  const grid = document.getElementById('yoga-grid');
  const sessions = cat === 'all' ? yogaSessions : yogaSessions.filter(s => s.cat === cat);
  grid.innerHTML = sessions.map(s => `
    <div class="yoga-card" onclick="openYoga(${s.id})">
      <div class="yoga-thumb" style="background:${s.bg}">
        <span style="font-size:3.5rem">${s.icon}</span>
        ${s.done ? '<div style="position:absolute;top:10px;right:10px"><span class="badge badge-green">✓ Fait</span></div>' : ''}
        <div class="yoga-thumb-overlay">▶</div>
      </div>
      <div class="yoga-card-body">
        <div class="yoga-card-name">${s.name}</div>
        <div class="yoga-card-meta">
          <span class="yoga-card-tag">⏱ ${s.meta}</span>
        </div>
      </div>
    </div>`).join('');
}
let currentYogaSession = null;
function openYoga(id) {
  const s = yogaSessions.find(x => x.id === id);
  if (!s) return;
  currentYogaSession = s;
  const mins = parseInt(s.meta);
  state.yogaTotalSec = mins * 60; state.yogaElapsed = 0;
  document.getElementById('modal-icon').textContent = s.icon;
  document.getElementById('modal-title').textContent = s.name;
  document.getElementById('modal-meta').textContent = s.meta;
  document.getElementById('modal-pose').textContent = s.pose;
  document.getElementById('yoga-timer').textContent = `${String(mins).padStart(2,'0')}:00`;
  document.getElementById('yoga-ring').style.strokeDashoffset = '326.7';
  document.getElementById('yoga-ring-label').textContent = '0%';
  document.getElementById('yoga-play-btn').textContent = '▶';
  document.getElementById('yoga-modal-overlay').classList.add('open');
  if (state.yogaActive) { clearInterval(state.yogaTimer); state.yogaActive = false; }
}
function closeYogaModal(e) {
  if (e && e.target !== document.getElementById('yoga-modal-overlay') && !e.target.classList.contains('yoga-modal-close')) return;
  if (!e || e.target === document.getElementById('yoga-modal-overlay') || e.target.classList.contains('yoga-modal-close')) {
    document.getElementById('yoga-modal-overlay').classList.remove('open');
    if (state.yogaActive) { clearInterval(state.yogaTimer); state.yogaActive = false; }
  }
}
function toggleYoga() {
  state.yogaActive = !state.yogaActive;
  const btn = document.getElementById('yoga-play-btn');
  if (state.yogaActive) {
    btn.textContent = '⏸'; btn.classList.add('running');
    state.yogaTimer = setInterval(updateYogaTimer, 1000);
  } else {
    btn.textContent = '▶'; btn.classList.remove('running');
    clearInterval(state.yogaTimer);
  }
}
function updateYogaTimer() {
  state.yogaElapsed++;
  const rem = state.yogaTotalSec - state.yogaElapsed;
  if (rem <= 0) {
    clearInterval(state.yogaTimer); state.yogaActive = false;
    document.getElementById('yoga-timer').textContent = '00:00';
    document.getElementById('yoga-play-btn').textContent = '▶';
    document.getElementById('yoga-ring-label').textContent = '100%';
    document.getElementById('yoga-ring').style.strokeDashoffset = '0';
    showToast('Yoga terminé', `🧘 Super ! Séance "${currentYogaSession?.name}" complétée !`, 'success');
    document.getElementById('yoga-modal-overlay').classList.remove('open');
    return;
  }
  const m = Math.floor(rem/60).toString().padStart(2,'0');
  const s = (rem%60).toString().padStart(2,'0');
  document.getElementById('yoga-timer').textContent = `${m}:${s}`;
  const pct = Math.round((state.yogaElapsed/state.yogaTotalSec)*100);
  document.getElementById('yoga-ring').style.strokeDashoffset = 326.7 * (1 - pct/100);
  document.getElementById('yoga-ring-label').textContent = `${pct}%`;
}

/* ═══ PROGRESS ═══ */
function initProgress() {
  renderWeightChart();
  renderAchievements();
  renderStatsTable();
}
function renderWeightChart() {
  const data = state.weightData;
  const n = data.length;
  const min = Math.min(...data) - 1;
  const max = Math.max(...data) + 0.5;
  const W = 600, H = 140, pad = 15;
  const xs = data.map((_,i) => pad + (i/(n-1))*(W-2*pad));
  const ys = data.map(v => H - pad - ((v-min)/(max-min))*(H-2*pad));
  const linePts = xs.map((x,i) => `${x},${ys[i]}`).join(' ');
  const areaPts = `${xs[0]},${H} ` + xs.map((x,i) => `${x},${ys[i]}`).join(' ') + ` ${xs[n-1]},${H}`;
  document.getElementById('weight-line').setAttribute('d','M '+xs.map((x,i)=>`${x} ${ys[i]}`).join(' L '));
  document.getElementById('weight-area').setAttribute('d','M '+xs[0]+' '+H+' L '+xs.map((x,i)=>`${x} ${ys[i]}`).join(' L ')+' L '+xs[n-1]+' '+H+' Z');
}
function addWeight() {
  const v = parseFloat(document.getElementById('weight-in').value);
  if (isNaN(v) || v < 30 || v > 200) { showToast('Erreur','⚠ Valeur invalide (30-200 kg)','error'); return; }
  state.weightData.push(v);
  if (state.weightData.length > 12) state.weightData.shift();
  renderWeightChart();
  document.getElementById('weight-in').value = '';
  showToast('Poids enregistré',`⚖ ${v} kg ajouté à votre historique`,'success');
}

const achievements = [
  { icon:'🏃', name:'Premier Run', desc:'Complétez votre 1ère course', unlocked:true },
  { icon:'⭐', name:'5 km', desc:'Courez 5 km sans pause', unlocked:true },
  { icon:'🔥', name:'7 jours', desc:'7 jours consécutifs', unlocked:true },
  { icon:'🧘', name:'Zen', desc:'10 séances yoga', unlocked:true },
  { icon:'⚡', name:'Niveau 5', desc:'Atteignez le niveau 5', unlocked:true },
  { icon:'🏆', name:'10 km', desc:'Courez 10 km d\'un coup', unlocked:true },
  { icon:'💪', name:'Force', desc:'20 séances de renforcement', unlocked:false },
  { icon:'🌅', name:'Lève-tôt', desc:'10 runs avant 7h00', unlocked:false },
  { icon:'🚀', name:'Niveau 10', desc:'Atteignez le niveau 10', unlocked:false },
  { icon:'🎯', name:'Objectif', desc:'Atteindre votre objectif poids', unlocked:false },
  { icon:'👥', name:'Social', desc:'Inviter 3 amis', unlocked:false },
  { icon:'🌍', name:'50 km', desc:'50 km cumulés', unlocked:false },
];
function renderAchievements() {
  document.getElementById('achievements-grid').innerHTML = achievements.map(a => `
    <div class="achievement ${a.unlocked?'unlocked':''}" title="${a.desc}" onclick="showToast('${a.name}','${a.desc}','${a.unlocked?'success':'info'}')">
      <span class="achievement-icon">${a.icon}</span>
      <div class="achievement-name">${a.name}</div>
      <div class="achievement-desc">${a.desc}</div>
    </div>`).join('');
}

const monthlyStats = [
  { m:'Avril 2025', km:'24.7', kcal:'3,840', sessions:'12', yoga:'8', xp:'3,450' },
  { m:'Mars 2025',  km:'31.2', kcal:'4,620', sessions:'15', yoga:'10', xp:'4,210' },
  { m:'Fév. 2025',  km:'18.5', kcal:'2,890', sessions:'9',  yoga:'6',  xp:'2,780' },
  { m:'Janv. 2025', km:'12.0', kcal:'1,950', sessions:'6',  yoga:'3',  xp:'1,540' },
];
function renderStatsTable() {
  document.getElementById('stats-table').innerHTML = monthlyStats.map((r,i) => `
    <tr style="border-bottom:1px solid var(--c-border);${i===0?'background:rgba(37,99,235,0.04)':''}">
      <td style="padding:12px;font-weight:${i===0?'600':'400'};font-size:14px">${r.m}${i===0?' <span class="badge badge-blue" style="font-size:10px">actuel</span>':''}</td>
      <td style="padding:12px;text-align:right;font-family:var(--f-mono);font-size:13px">${r.km} km</td>
      <td style="padding:12px;text-align:right;font-family:var(--f-mono);font-size:13px">${r.kcal}</td>
      <td style="padding:12px;text-align:right;font-family:var(--f-mono);font-size:13px">${r.sessions}</td>
      <td style="padding:12px;text-align:right;font-family:var(--f-mono);font-size:13px">${r.yoga}</td>
      <td style="padding:12px;text-align:right;font-family:var(--f-mono);font-size:13px;color:var(--c-blue-xl)">${r.xp}</td>
    </tr>`).join('');
}

/* ═══ LOGOUT ═══ */
function doLogout() {
  if (state.runActive) { clearInterval(state.runTimer); state.runActive = false; }
  if (state.yogaActive) { clearInterval(state.yogaTimer); state.yogaActive = false; }
  document.getElementById('app-shell').classList.remove('active');
  document.getElementById('auth-screen').classList.remove('hidden');
  document.getElementById('panel-login').classList.add('active');
  document.getElementById('panel-signup').classList.remove('active');
  document.querySelectorAll('.auth-tab').forEach((t,i) => { i===0?t.classList.add('active'):t.classList.remove('active'); });
  document.getElementById('login-email').value = '';
  document.getElementById('login-pwd').value = '';
  document.getElementById('btn-login').innerHTML = '<span>Se connecter</span>';
  document.getElementById('btn-login').disabled = false;
  state.user = null;
  navigate('dashboard', document.querySelector('[data-page="dashboard"]'));
  showToast('Déconnexion','👋 À bientôt sur Ali-Run !','info');
}

/* ═══ MAPBOX GPS ═══ */
const MAPBOX_TOKEN = 'pk.eyJ1IjoibmF0YWNoYTE2NyIsImEiOiJjbXVkcHdrcTUyYmk3MnhzNzBod2xjYTI4In0.RxwYGQS7o-zYKk_zX3V_KA';
let map = null;
let gpsWatcher = null;
let routeCoords = [];
let userMarker = null;

function initMap() {
  if (map) return;
  mapboxgl.accessToken = MAPBOX_TOKEN;
  map = new mapboxgl.Map({
    container: 'mapbox-container',
    style: 'mapbox://styles/mapbox/dark-v11',
    zoom: 15,
    center: [55.4513, -20.8823]
  });
  map.addControl(new mapboxgl.NavigationControl(), 'top-right');
  map.on('load', () => {
    map.addSource('route', {
      type: 'geojson',
      data: { type: 'Feature', properties: {}, geometry: { type: 'LineString', coordinates: [] } }
    });
    map.addLayer({
      id: 'route-line',
      type: 'line',
      source: 'route',
      paint: { 'line-color': '#3B82F6', 'line-width': 4, 'line-opacity': 0.9 }
    });
  });
  startGPS();
}

function startGPS() {
  if (!navigator.geolocation) {
    document.getElementById('gps-status').textContent = 'GPS non supporté';
    return;
  }
  document.getElementById('gps-status').textContent = 'Recherche GPS...';
  gpsWatcher = navigator.geolocation.watchPosition(
    (pos) => {
      const { latitude: lat, longitude: lng, accuracy } = pos.coords;
      document.getElementById('gps-status').textContent = `GPS Actif · Précision ${Math.round(accuracy)}m`;
      document.getElementById('gps-coords').textContent = `📍 ${lat.toFixed(5)}, ${lng.toFixed(5)}`;
      map.setCenter([lng, lat]);
      if (userMarker) userMarker.remove();
      const el = document.createElement('div');
      el.style.cssText = 'width:16px;height:16px;border-radius:50%;background:#3B82F6;border:3px solid white;box-shadow:0 0 10px rgba(59,130,246,0.6)';
      userMarker = new mapboxgl.Marker(el).setLngLat([lng, lat]).addTo(map);
      if (window.state.runActive) {
        routeCoords.push([lng, lat]);
        if (map.getSource('route')) {
          map.getSource('route').setData({
            type: 'Feature', properties: {},
            geometry: { type: 'LineString', coordinates: routeCoords }
          });
        }
      }
    },
    (err) => {
      document.getElementById('gps-status').textContent = 'GPS indisponible';
      console.warn('GPS error:', err);
    },
    { enableHighAccuracy: true, maximumAge: 3000, timeout: 10000 }
  );
}

function stopGPS() {
  if (gpsWatcher) { navigator.geolocation.clearWatch(gpsWatcher); gpsWatcher = null; }
}

function resetRoute() {
  routeCoords = [];
  if (map && map.getSource('route')) {
    map.getSource('route').setData({ type:'Feature', properties:{}, geometry:{ type:'LineString', coordinates:[] } });
  }
}

async function doLogin() {
  const email = document.getElementById('login-email').value.trim();
  const pwd = document.getElementById('login-pwd').value;
  let ok = true;
  setErr('login-email-err',''); setErr('login-pwd-err','');
  if (!validateEmail(email)) { setErr('login-email-err','Adresse e-mail invalide'); ok = false; }
  if (pwd.length < 6) { setErr('login-pwd-err','Mot de passe trop court'); ok = false; }
  if (!ok) return;
  const btn = document.getElementById('btn-login');
  btn.innerHTML = '<span style="display:inline-block;width:16px;height:16px;border:2px solid rgba(255,255,255,0.3);border-top-color:#fff;border-radius:50%;animation:spin .7s linear infinite"></span> Connexion...';
  btn.disabled = true;
  document.head.insertAdjacentHTML('beforeend','<style>@keyframes spin{to{transform:rotate(360deg)}}</style>');
  try {
    if (!window._fbFns || !window._fbAuth) {
      showToast('Erreur', '⏳ Firebase pas encore chargé, réessayez dans 2 secondes...', 'error');
      btn.innerHTML = '<span>Se connecter</span>'; btn.disabled = false; return;
    }
    const { signInWithEmailAndPassword } = window._fbFns;
    const cred = await signInWithEmailAndPassword(window._fbAuth, email, pwd);
    const { doc, getDoc } = window._fbFns;
    const docSnap = await getDoc(doc(window._fbDb, 'users', cred.user.uid));
    if (docSnap.exists()) {
      const data = docSnap.data();
      state.user = { name: data.name, email, goal: data.goal, level: data.level, uid: cred.user.uid };
      enterApp();
      showToast('Connexion','✅ Bienvenue ' + data.name + ' !','success');
    }
  } catch(e) {
    btn.innerHTML = '<span>Se connecter</span>';
    btn.disabled = false;
    const msgs = { 'auth/user-not-found':'Aucun compte avec cet email', 'auth/wrong-password':'Mot de passe incorrect', 'auth/invalid-credential':'Email ou mot de passe incorrect' };
    setErr('login-pwd-err', msgs[e.code] || 'Erreur de connexion');
  }
}

async function doSignup() {
  const fname = document.getElementById('signup-fname').value.trim();
  const email = document.getElementById('signup-email').value.trim();
  const pwd = document.getElementById('signup-pwd').value;
  let ok = true;
  setErr('signup-fname-err',''); setErr('signup-email-err',''); setErr('signup-pwd-err','');
  if (!fname) { setErr('signup-fname-err','Prénom requis'); ok = false; }
  if (!validateEmail(email)) { setErr('signup-email-err','E-mail invalide'); ok = false; }
  if (pwd.length < 8) { setErr('signup-pwd-err','Min. 8 caractères requis'); ok = false; }
  if (!ok) return;
  try {
    const { createUserWithEmailAndPassword, updateProfile } = window._fbFns;
    const cred = await createUserWithEmailAndPassword(window._fbAuth, email, pwd);
    await updateProfile(cred.user, { displayName: fname });
    state.user = { name: fname, email, goal: null, level: null, uid: cred.user.uid };
    document.getElementById('auth-screen').classList.add('hidden');
    document.getElementById('onboarding-screen').classList.remove('hidden');
  } catch(e) {
    const msgs = { 'auth/email-already-in-use':'Cet email est déjà utilisé', 'auth/weak-password':'Mot de passe trop faible' };
    setErr('signup-pwd-err', msgs[e.code] || 'Erreur inscription');
  }
}

async function socialLogin(provider) {
  try {
    showToast(provider, '🔄 Connexion via ' + provider + '...', 'info');
    if (!window._fbFns || !window._fbAuth) {
      showToast('Erreur', '⏳ Firebase pas encore chargé, réessayez dans 2 secondes...', 'error');
      return;
    }
    const { GoogleAuthProvider, signInWithPopup, doc, getDoc, setDoc, serverTimestamp } = window._fbFns;
    const prov = new GoogleAuthProvider();
    const cred = await signInWithPopup(window._fbAuth, prov);
    const user = cred.user;
    const docRef = doc(window._fbDb, 'users', user.uid);
    const docSnap = await getDoc(docRef);
    if (!docSnap.exists()) {
      state.user = { name: user.displayName || 'Utilisateur', email: user.email, goal: null, level: null, uid: user.uid };
      document.getElementById('auth-screen').classList.add('hidden');
      document.getElementById('onboarding-screen').classList.remove('hidden');
    } else {
      const data = docSnap.data();
      state.user = { name: data.name, email: user.email, goal: data.goal, level: data.level, uid: user.uid };
      enterApp();
    }
  } catch(e) {
    showToast('Erreur', '❌ Connexion échouée : ' + (e.message || e.code), 'error');
  }
}

async function finishOnboarding() {
  const name = document.getElementById('onb-name').value.trim() || state.user?.name || 'Ali';
  state.user = { ...state.user, name, goal: state.onb.goal || 'wellness', level: state.onb.level || 'beginner' };
  try {
    if (state.user.uid && window._fbDb) {
      const { doc, setDoc, serverTimestamp } = window._fbFns;
      await setDoc(doc(window._fbDb, 'users', state.user.uid), {
        name, email: state.user.email,
        goal: state.user.goal, level: state.user.level,
        onboarded: true, createdAt: serverTimestamp(),
        xp: 0, level_num: 1, streak: 0
      });
    }
  } catch(e) { console.error(e); }
  document.getElementById('onboarding-screen').classList.add('hidden');
  enterApp();
}

async function doLogout() {
  if (state.runActive) { clearInterval(state.runTimer); state.runActive = false; }
  if (state.yogaActive) { clearInterval(state.yogaTimer); state.yogaActive = false; }
  try {
    if (window._fbAuth) { const { signOut } = window._fbFns; await signOut(window._fbAuth); }
  } catch(e) {}
  document.getElementById('app-shell').classList.remove('active');
  document.getElementById('auth-screen').classList.remove('hidden');
  document.getElementById('panel-login').classList.add('active');
  document.getElementById('panel-signup').classList.remove('active');
  document.querySelectorAll('.auth-tab').forEach((t,i) => { i===0?t.classList.add('active'):t.classList.remove('active'); });
  document.getElementById('login-email').value = '';
  document.getElementById('login-pwd').value = '';
  document.getElementById('btn-login').innerHTML = '<span>Se connecter</span>';
  document.getElementById('btn-login').disabled = false;
  state.user = null;
  navigate('dashboard', document.querySelector('[data-page="dashboard"]'));
  showToast('Déconnexion','👋 À bientôt sur Ali-Run !','info');
}


</script>

<!-- Firebase via module script -->
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/12.19.0/firebase-app.js";
import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged, GoogleAuthProvider, signInWithPopup, updateProfile } from "https://www.gstatic.com/firebasejs/12.19.0/firebase-auth.js";
import { getFirestore, doc, setDoc, getDoc, serverTimestamp } from "https://www.gstatic.com/firebasejs/12.19.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyCMLcRqiLNJpMaLRq4Tk7ikoVI-v8ZRDlQ",
  authDomain: "ali-run.firebaseapp.com",
  projectId: "ali-run",
  storageBucket: "ali-run.firebasestorage.app",
  messagingSenderId: "637499642436",
  appId: "1:637499642436:web:9808293e3b5f54f95d2211"
};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);

window._fbAuth = auth;
window._fbDb = db;
window._fbFns = {
  createUserWithEmailAndPassword, signInWithEmailAndPassword,
  signOut, GoogleAuthProvider, signInWithPopup, updateProfile,
  doc, setDoc, getDoc, serverTimestamp
};

onAuthStateChanged(auth, async (user) => {
  if (user) {
    try {
      const docSnap = await getDoc(doc(db, 'users', user.uid));
      if (docSnap.exists()) {
        const data = docSnap.data();
        window.state.user = {
          name: data.name || user.displayName || 'Utilisateur',
          email: user.email,
          goal: data.goal || 'wellness',
          level: data.level || 'beginner',
          uid: user.uid
        };
        if (data.onboarded) {
          document.getElementById('onboarding-screen').classList.add('hidden');
          document.getElementById('auth-screen').classList.add('hidden');
          window.enterApp();
        } else {
          document.getElementById('auth-screen').classList.add('hidden');
          document.getElementById('onboarding-screen').classList.remove('hidden');
        }
      }
    } catch(e) { console.error(e); }
  }
});

console.log('✅ Firebase connecté !');
</script>
</body>
</html>
