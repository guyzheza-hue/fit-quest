[index.html](https://github.com/user-attachments/files/30342373/index.html)
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="theme-color" content="#EDE8DF">
<title>FitQuest</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent;-webkit-font-smoothing:antialiased}
:root{
  --bg:#EDE8DF;--s1:#F5F2EC;--s2:#FAF8F5;
  --line:rgba(0,0,0,.08);--line2:rgba(0,0,0,.05);
  --lime:#3D5240;--red:#C05050;--blue:#4D72A8;--grn:#5E8B60;
  --text:#252420;--t2:#8A857C;--t3:#C0BAB2;
  --st:env(safe-area-inset-top,20px);--sb:env(safe-area-inset-bottom,20px);
}
body{font-family:-apple-system,'Helvetica Neue',sans-serif;background:var(--bg);color:var(--text);min-height:100dvh;max-width:430px;margin:0 auto;overflow-x:hidden}
.screen{display:none;min-height:100dvh;padding-bottom:calc(58px + var(--sb))}
.screen.active{display:block}

/* ── NAV ───────────────────────────────────────── */
.bnav{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:100%;max-width:430px;height:calc(52px + var(--sb));padding-bottom:var(--sb);background:var(--s1);border-top:1px solid var(--line);display:flex;align-items:stretch;justify-content:stretch;z-index:100}
.nb{flex:1;display:flex;align-items:center;justify-content:center;background:none;border:none;color:var(--t2);font-size:12px;font-weight:600;cursor:pointer;position:relative;letter-spacing:.2px;padding-top:2px}
.nb.on{color:var(--lime)}
.nb.on::after{content:'';position:absolute;bottom:0;left:20%;right:20%;height:2px;background:var(--lime);border-radius:2px 2px 0 0}

/* ── SECTION ───────────────────────────────────── */
.sec{border-top:1px solid var(--line);padding:16px}
.sec:first-child{border-top:none}
.sec-lbl{font-size:14px;font-style:italic;font-family:Georgia,'Times New Roman',serif;color:var(--text);margin-bottom:12px;font-weight:normal;display:flex;justify-content:space-between;align-items:center}

/* ── PROFILE SELECT ────────────────────────────── */
#profileSelect{min-height:100dvh;display:flex;flex-direction:column;padding:calc(var(--st)+40px) 20px calc(32px+var(--sb))}
.ps-logo{margin-bottom:40px}
.ps-logo-title{font-size:36px;font-weight:900;letter-spacing:-1px;color:var(--lime);font-family:Georgia,'Times New Roman',serif;font-style:italic}
.ps-logo-sub{font-size:11px;color:var(--t2);margin-top:4px;letter-spacing:.8px;text-transform:uppercase}
.profile-card{border:1px solid var(--line);border-radius:14px;padding:14px 16px;display:flex;align-items:center;gap:14px;cursor:pointer;margin-bottom:8px;transition:all .15s;background:var(--s1)}
.profile-card:active{border-color:var(--lime);transform:scale(.99)}
.pc-avatar{font-size:22px;width:36px;text-align:center;flex-shrink:0}
.pc-info{flex:1}
.pc-name{font-size:16px;font-weight:700;letter-spacing:-.3px}
.pc-sub{font-size:11px;color:var(--t2);margin-top:2px}
.pc-badge{font-size:10px;font-weight:800;color:var(--lime);letter-spacing:.3px}
.add-profile-btn{display:flex;align-items:center;justify-content:center;gap:8px;border:1.5px dashed var(--t3);border-radius:14px;padding:14px;color:var(--t2);font-size:14px;cursor:pointer;margin-top:4px;font-weight:600}

/* ── SETUP ─────────────────────────────────────── */
#setup{min-height:100dvh;display:flex;flex-direction:column;padding:calc(var(--st)+16px) 20px calc(28px+var(--sb))}
.setup-back{background:none;border:none;color:var(--t2);font-size:20px;cursor:pointer;padding:0;margin-bottom:16px;align-self:flex-start}
.setup-prog{display:flex;gap:4px;margin-bottom:28px}
.sp-dot{height:3px;flex:1;background:var(--line);border-radius:2px;transition:background .3s}
.sp-dot.on{background:var(--lime)}
.setup-title{font-size:26px;font-weight:900;letter-spacing:-.5px;margin-bottom:4px;font-family:Georgia,'Times New Roman',serif;font-style:italic}
.setup-sub{font-size:13px;color:var(--t2);margin-bottom:22px;line-height:1.5}
.s-opts{display:flex;flex-direction:column;gap:8px;margin-bottom:20px}
.s-opt{background:var(--s1);border:1.5px solid var(--line);border-radius:14px;padding:12px 14px;cursor:pointer;display:flex;align-items:center;gap:12px;transition:all .15s}
.s-opt.on{border-color:var(--lime);background:rgba(61,82,64,.06)}
.s-opt-icon{font-size:22px;width:28px;text-align:center}
.s-opt-title{font-size:14px;font-weight:700}
.s-opt-sub{font-size:11px;color:var(--t2);margin-top:2px}

/* ── BUTTONS ───────────────────────────────────── */
.btn{border:none;border-radius:12px;padding:14px;font-size:15px;font-weight:700;cursor:pointer;width:100%;transition:opacity .15s;letter-spacing:.2px}
.btn:active{opacity:.7}
.btn-lime{background:var(--lime);color:#fff}
.btn-outline{background:transparent;border:1.5px solid var(--line);color:var(--text)}
.btn-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:10px}
.btn-sm{border:none;border-radius:10px;padding:8px 14px;font-size:12px;font-weight:700;cursor:pointer;letter-spacing:.3px;transition:opacity .15s}
.btn-sm:active{opacity:.7}

/* ── FORM ──────────────────────────────────────── */
.form-group{margin-bottom:12px}
.form-lbl{font-size:9px;font-weight:700;color:var(--t2);margin-bottom:5px;display:block;letter-spacing:1px;text-transform:uppercase}
.form-input{width:100%;background:var(--s2);border:1.5px solid var(--line);border-radius:12px;padding:11px 13px;color:var(--text);font-size:16px;outline:none;-webkit-appearance:none}
.form-input:focus{border-color:var(--lime)}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.form-row3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px}
select.form-input{color:var(--text)}
select.form-input option{background:var(--s2)}

/* ── HOME HERO ─────────────────────────────────── */
.home-top{background:var(--lime);color:#fff;padding:calc(var(--st)+18px) 20px 18px;border-bottom:none}
.ht-greeting{font-size:12px;color:rgba(255,255,255,.6);margin-bottom:3px;font-weight:500}
.ht-name{font-size:26px;font-weight:900;letter-spacing:-.5px;margin-bottom:18px;color:#fff;font-family:Georgia,'Times New Roman',serif;font-style:italic}
.ht-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:0}
.hts-cell{text-align:center;padding:10px 0}
.hts-cell+.hts-cell{border-left:1px solid rgba(255,255,255,.2)}
.hts-val{font-size:28px;font-weight:900;letter-spacing:-1px;line-height:1;color:#fff}
.hts-lbl{font-size:9px;font-weight:700;letter-spacing:1px;text-transform:uppercase;color:rgba(255,255,255,.55);margin-top:4px}
.hts-lime{color:#fff}

/* ── XP BAR ────────────────────────────────────── */
.xp-row{display:flex;justify-content:space-between;align-items:baseline;margin-bottom:6px}
.xp-level{font-size:11px;font-weight:800;color:var(--lime);letter-spacing:.5px}
.xp-nums{font-size:10px;color:var(--t2);font-weight:600}
.xp-track{height:4px;background:var(--line);border-radius:2px;overflow:hidden}
.xp-fill{height:100%;background:var(--lime);border-radius:2px;transition:width .5s}

/* ── CALENDAR ──────────────────────────────────── */
.cal-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.cal-month{font-size:14px;font-style:italic;font-family:Georgia,'Times New Roman',serif;color:var(--text)}
.cal-streak{font-size:11px;color:var(--lime);font-weight:700}
.cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:3px}
.cal-dn{font-size:9px;color:var(--t3);text-align:center;padding:2px 0;font-weight:700;letter-spacing:.3px;text-transform:uppercase}
.cal-d{aspect-ratio:1;display:flex;align-items:center;justify-content:center;font-size:10px;color:var(--t2);border-radius:50%}
.cal-d.chk{background:var(--lime);color:#fff;font-weight:700}
.cal-d.tod{outline:2px solid var(--lime);outline-offset:-1px;color:var(--lime);font-weight:800}
.cal-d.chk.tod{background:var(--lime);color:#fff}

/* ── DEFICIT ───────────────────────────────────── */
.deficit-num-row{display:flex;align-items:baseline;gap:6px;margin-bottom:4px}
.deficit-big{font-size:48px;font-weight:900;letter-spacing:-2px;line-height:1}
.deficit-unit{font-size:13px;color:var(--t2);font-weight:600}
.deficit-sub{font-size:11px;color:var(--t2);margin-bottom:10px}
.deficit-track{height:4px;background:var(--line);border-radius:2px;overflow:hidden;margin-bottom:12px}
.deficit-fill{height:100%;border-radius:2px;transition:width .4s}
.deficit-trio{display:grid;grid-template-columns:repeat(3,1fr);gap:0;border-top:1px solid var(--line)}
.dt-cell{padding:10px 0;text-align:center}
.dt-cell+.dt-cell{border-left:1px solid var(--line)}
.dt-val{font-size:17px;font-weight:900;line-height:1}
.dt-lbl{font-size:9px;color:var(--t2);margin-top:3px;letter-spacing:.5px;text-transform:uppercase}
.dt-note{font-size:11px;color:var(--t2);padding:10px 0 0;line-height:1.5}

/* ── CHECKIN ───────────────────────────────────── */
.ex-row{display:flex;align-items:center;gap:12px;padding:12px 0;cursor:pointer;border-bottom:1px solid var(--line)}
.ex-row:last-of-type{border-bottom:none}
.ex-row:active{opacity:.7}
.ex-icon{font-size:20px;width:32px;text-align:center;flex-shrink:0}
.ex-info{flex:1}
.ex-name{font-size:15px;font-weight:700;letter-spacing:-.2px}
.ex-sub{font-size:11px;color:var(--t2);margin-top:2px}
.ex-badge{width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:800;flex-shrink:0}
.ex-badge.done-lime{background:var(--lime);color:#fff}
.ex-badge.done-blue{background:var(--blue);color:#fff}
.ex-badge.todo{border:1.5px solid var(--t3);color:var(--t3)}
.water-row{display:flex;align-items:center;gap:12px;padding:12px 0;cursor:pointer}
.water-row:active{opacity:.7}

/* ── YESTERDAY ─────────────────────────────────── */
.yday-item{display:flex;align-items:flex-start;gap:8px;padding:5px 0}
.yday-ico{font-size:13px;width:20px;flex-shrink:0;margin-top:1px}
.yday-msg{flex:1;font-size:12px;line-height:1.5;color:var(--text)}
.yday-fix{font-size:10px;color:var(--t2)}

/* ── FOOD ──────────────────────────────────────── */
.food-top{padding:calc(var(--st)+16px) 20px 14px;border-bottom:1px solid var(--line);display:flex;justify-content:space-between;align-items:center}
.date-nav{display:flex;align-items:center;gap:4px;padding:12px 20px;border-bottom:1px solid var(--line);background:var(--bg)}
.dnav-btn{background:none;border:none;color:var(--t2);font-size:20px;cursor:pointer;padding:0 8px;line-height:1;transition:color .15s}
.dnav-btn:active{color:var(--lime)}
.dnav-label{flex:1;text-align:center;font-size:13px;font-weight:700;color:var(--text);letter-spacing:-.2px}
.dnav-today{font-size:11px;font-weight:700;color:var(--lime);padding:3px 10px;border:1.5px solid var(--lime);border-radius:20px;cursor:pointer;letter-spacing:.3px;white-space:nowrap;background:rgba(61,82,64,.07)}
.fsearch-wrap{position:relative;padding:12px 20px;border-bottom:1px solid var(--line)}
.fsearch{width:100%;background:var(--s1);border:1.5px solid var(--line);border-radius:12px;padding:10px 13px;color:var(--text);font-size:15px;outline:none;-webkit-appearance:none}
.fsearch:focus{border-color:var(--lime)}
.fsearch::placeholder{color:var(--t2)}
.sr-dropdown{position:absolute;top:calc(100% - 2px);left:20px;right:20px;background:var(--s1);border:1px solid var(--line);border-radius:14px;z-index:200;max-height:240px;overflow-y:auto;display:none;box-shadow:0 8px 24px rgba(0,0,0,.12)}
.sr-item{padding:10px 13px;border-bottom:1px solid var(--line);cursor:pointer;display:flex;justify-content:space-between;align-items:center}
.sr-item:last-child{border-bottom:none}
.sr-item:active{background:var(--s2)}
.sr-name{font-size:14px;font-weight:600}
.sr-unit{font-size:10px;color:var(--t2);margin-top:1px}
.sr-kcal{font-size:13px;font-weight:900;color:var(--lime)}
.macro-sec{padding:16px 20px;border-bottom:1px solid var(--line);display:flex;gap:16px;align-items:center}
.kcal-ring{width:72px;height:72px;position:relative;flex-shrink:0}
.kcal-ring svg{width:72px;height:72px}
.kcal-txt{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);text-align:center}
.kcal-num{font-size:17px;font-weight:900;color:var(--lime);line-height:1}
.kcal-lbl{font-size:8px;color:var(--t2);line-height:1.3;margin-top:1px}
.macro-bars{flex:1;display:flex;flex-direction:column;gap:8px}
.mb-row{display:flex;flex-direction:column;gap:3px}
.mb-lbl{display:flex;justify-content:space-between;font-size:10px;font-weight:600}
.mb-lbl span:last-child{color:var(--t2);font-weight:500}
.mb-bar{height:4px;background:var(--line);border-radius:2px;overflow:hidden}
.mb-fill{height:100%;border-radius:2px;transition:width .4s}
.fill-c{background:var(--lime)}.fill-p{background:var(--blue)}.fill-f{background:var(--red)}
.food-log-sec{padding:0 20px}
.food-log-item{display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid var(--line)}
.food-log-item:last-child{border-bottom:none}
.fli-info{flex:1;min-width:0}
.fli-name{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.fli-macros{font-size:10px;color:var(--t2);margin-top:2px}
.fli-kcal{font-size:13px;font-weight:900;color:var(--lime);white-space:nowrap}
.fli-del{background:none;border:none;color:var(--t2);width:28px;height:28px;cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:15px;flex-shrink:0}
.fli-edit{background:none;border:none;color:var(--t2);width:28px;height:28px;cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0}
.meal-tag{display:inline-block;font-size:9px;font-weight:800;padding:3px 10px;border-radius:20px;margin:10px 0 6px;letter-spacing:.8px;text-transform:uppercase}
.mt-breakfast{background:rgba(61,82,64,.1);color:var(--lime)}
.mt-lunch{background:rgba(94,139,96,.1);color:var(--grn)}
.mt-dinner{background:rgba(77,114,168,.1);color:var(--blue)}
.mt-snack{background:rgba(192,80,80,.1);color:var(--red)}

/* ── PROGRESS ──────────────────────────────────── */
.stat-grid{display:grid;grid-template-columns:1fr 1fr;gap:0;border:1px solid var(--line);border-radius:14px;overflow:hidden;margin-bottom:16px;background:var(--s1)}
.sg-cell{padding:16px;text-align:center}
.sg-cell+.sg-cell{border-left:1px solid var(--line)}
.sg-cell:nth-child(3),.sg-cell:nth-child(4){border-top:1px solid var(--line)}
.sg-val{font-size:26px;font-weight:900;letter-spacing:-1px;line-height:1;color:var(--lime)}
.sg-lbl{font-size:9px;font-weight:700;letter-spacing:1px;text-transform:uppercase;color:var(--t2);margin-top:4px}
.sg-full{grid-column:span 2;border-left:none!important}
.week-row{display:grid;grid-template-columns:repeat(7,1fr);gap:6px}
.wday{display:flex;flex-direction:column;align-items:center;gap:4px}
.wday-lbl{font-size:9px;color:var(--t2);font-weight:700;letter-spacing:.3px;text-transform:uppercase}
.wday-dot{width:34px;height:34px;border-radius:50%;background:var(--s1);border:1.5px solid var(--line);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;transition:all .3s;color:var(--t3)}
.wday-dot.done{background:var(--lime);border-color:var(--lime);color:#fff}
.wday-dot.today{border-color:var(--lime);color:var(--lime)}

/* ── PROFILE TAB ───────────────────────────────── */
.prof-hero{padding:20px;text-align:center;border-bottom:1px solid var(--line)}
.prof-emoji{font-size:40px;margin-bottom:8px}
.prof-name{font-size:22px;font-weight:900;letter-spacing:-.5px;font-family:Georgia,'Times New Roman',serif;font-style:italic}
.prof-goal-badge{display:inline-block;margin-top:6px;padding:4px 14px;border-radius:20px;font-size:11px;font-weight:700;letter-spacing:.3px}
.prof-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:0;border-top:1px solid var(--line);margin-top:16px}
.ps-cell{padding:12px 0;text-align:center}
.ps-cell+.ps-cell{border-left:1px solid var(--line)}
.ps-val{font-size:18px;font-weight:900;color:var(--lime)}
.ps-lbl{font-size:9px;color:var(--t2);font-weight:700;letter-spacing:.5px;text-transform:uppercase;margin-top:3px}
.targets-grid{display:grid;grid-template-columns:1fr 1fr;gap:0;border:1px solid var(--line);border-radius:14px;overflow:hidden;background:var(--s1)}
.tg-cell{padding:14px;text-align:center}
.tg-cell+.tg-cell{border-left:1px solid var(--line)}
.tg-cell:nth-child(3),.tg-cell:nth-child(4){border-top:1px solid var(--line)}
.tg-val{font-size:20px;font-weight:900;line-height:1}
.tg-lbl{font-size:9px;font-weight:700;letter-spacing:.8px;text-transform:uppercase;color:var(--t2);margin-top:3px}
.gtarget-row{display:grid;grid-template-columns:repeat(3,1fr);gap:0;border:1px solid var(--line);border-radius:14px;overflow:hidden;margin-bottom:12px;background:var(--s1)}
.gt-cell{padding:12px;text-align:center}
.gt-cell+.gt-cell{border-left:1px solid var(--line)}

/* ── GITHUB SYNC ───────────────────────────────── */
.sync-row{display:flex;align-items:center;gap:8px;margin-bottom:10px}
.sync-dot{width:7px;height:7px;border-radius:50%;background:var(--t3);flex-shrink:0;transition:background .3s}
.sync-dot.on{background:var(--grn)}.sync-dot.err{background:var(--red)}.sync-dot.spin{background:var(--grn);animation:pulse 1s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}
.sync-text{font-size:11px;font-weight:600;color:var(--t2);flex:1}

/* ── MODAL ─────────────────────────────────────── */
.modal{position:fixed;inset:0;background:rgba(0,0,0,.3);z-index:300;display:none;align-items:flex-end;justify-content:center}
.modal.show{display:flex}
.modal-sheet{background:var(--s1);border-radius:20px 20px 0 0;padding:14px 18px calc(18px+var(--sb));width:100%;max-width:430px;max-height:88dvh;overflow-y:auto}
.modal-handle{width:36px;height:4px;background:var(--t3);border-radius:2px;margin:0 auto 16px}
.modal-title{font-size:18px;font-weight:900;margin-bottom:14px;font-family:Georgia,'Times New Roman',serif;font-style:italic;color:var(--text)}

/* ── DURATION PICKER ───────────────────────────── */
.dur-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin-bottom:12px}
.dur-opt{background:var(--s2);border:1.5px solid var(--line);border-radius:12px;padding:11px 8px;text-align:center;cursor:pointer;font-size:14px;font-weight:700;transition:all .15s;color:var(--t2)}
.dur-opt:active{opacity:.7}
.dur-opt.on{border-color:var(--lime);color:var(--lime);background:rgba(61,82,64,.07)}
.dur-preview{background:var(--s2);border-radius:12px;padding:10px 13px;margin-bottom:12px;display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;text-align:center;border:1px solid var(--line)}
.dp-val{font-size:15px;font-weight:900}
.dp-lbl{font-size:9px;color:var(--t2);margin-top:2px;letter-spacing:.5px;text-transform:uppercase}

/* ── TOAST ─────────────────────────────────────── */
.toast{position:fixed;top:calc(var(--st)+12px);left:50%;transform:translateX(-50%) translateY(-70px);background:var(--lime);color:#fff;font-size:13px;font-weight:700;padding:10px 22px;border-radius:12px;z-index:999;transition:transform .3s cubic-bezier(.175,.885,.32,1.275);white-space:nowrap;pointer-events:none;letter-spacing:.2px}
.toast.show{transform:translateX(-50%) translateY(0)}
::-webkit-scrollbar{width:0;height:0}
</style>
</head>
<body>

<!-- PROFILE SELECT -->
<div id="profileSelect">
  <div class="ps-logo">
    <div class="ps-logo-title">FitQuest</div>
    <div class="ps-logo-sub">Fitness RPG Tracker</div>
  </div>
  <div id="profileList"></div>
  <div class="add-profile-btn" onclick="startSetup()">＋ สร้างโปรไฟล์ใหม่</div>
</div>

<!-- SETUP -->
<div id="setup" style="display:none">
  <button class="setup-back" onclick="backSetup()">←</button>
  <div class="setup-prog" id="setupProg"></div>
  <div id="setupContent"></div>
</div>

<!-- MAIN APP -->
<div id="app" style="display:none">

  <!-- GITHUB BANNER -->
  <div id="ghBanner" style="display:none;background:rgba(61,82,64,.07);border-bottom:1px solid rgba(61,82,64,.18);padding:10px 16px;display:none;align-items:center;gap:10px">
    <div style="flex:1;font-size:12px;color:var(--lime);font-weight:600">🔗 วาง Token เพื่อโหลดข้อมูล</div>
    <button class="btn-sm btn-lime" style="padding:6px 14px;font-size:12px;white-space:nowrap" onclick="openGitHubSetup()">Connect</button>
  </div>

  <!-- HOME -->
  <div id="screenHome" class="screen active">
    <div class="home-top">
      <div class="ht-greeting" id="homeDate"></div>
      <div class="ht-name" id="homeGreet">สวัสดี</div>
      <div class="ht-stats">
        <div class="hts-cell">
          <div class="hts-val hts-lime">Lv.<span id="homeLv">1</span></div>
          <div class="hts-lbl">Level</div>
        </div>
        <div class="hts-cell">
          <div class="hts-val" id="streakVal">0</div>
          <div class="hts-lbl">วันติด</div>
        </div>
        <div class="hts-cell">
          <div class="hts-val hts-lime" id="coinVal">0</div>
          <div class="hts-lbl">เหรียญ</div>
        </div>
      </div>
    </div>

    <div class="sec">
      <div class="xp-row">
        <span class="xp-level">XP</span>
        <span class="xp-nums" id="xpText"></span>
      </div>
      <div class="xp-track"><div class="xp-fill" id="xpFill" style="width:0%"></div></div>
    </div>

    <!-- MONTHLY CALENDAR -->
    <div class="sec">
      <div class="cal-hdr">
        <div class="cal-month" id="calMonthLbl"></div>
        <div class="cal-streak" id="calStreakLbl"></div>
      </div>
      <div class="cal-grid" id="calGrid"></div>
    </div>

    <!-- AUTO DEFICIT CARD -->
    <div class="sec" id="deficitCard">
      <div class="sec-lbl">TDEE · แคลวันนี้ · <span id="dcTdeeLabel"></span></div>
      <div class="deficit-num-row">
        <div class="deficit-big" id="dcEaten">0</div>
        <div class="deficit-unit">/ <span id="dcTarget">–</span> kcal</div>
      </div>
      <div class="deficit-sub" id="dcNote"></div>
      <div class="deficit-track"><div class="deficit-fill" id="dcBar" style="width:0%"></div></div>
      <div class="deficit-trio">
        <div class="dt-cell">
          <div class="dt-val hts-lime" id="dcDeficit">–</div>
          <div class="dt-lbl" id="dcDeficitLbl">ขาดแคล</div>
        </div>
        <div class="dt-cell">
          <div class="dt-val" id="dcProjCoins" style="color:var(--lime)">–</div>
          <div class="dt-lbl">เหรียญคืนนี้</div>
        </div>
        <div class="dt-cell">
          <div class="dt-val" id="dcDays" style="color:var(--t2)">–</div>
          <div class="dt-lbl">วันถึงเป้า</div>
        </div>
      </div>
    </div>

    <div id="ydayCard"></div>

    <!-- CHECK-IN -->
    <div class="sec">
      <div class="sec-lbl">เช็คอินวันนี้ · <span id="checkinCount">0/3</span></div>
      <div class="ex-row" id="tileWeight" onclick="openExercise('weight')">
        <div class="ex-icon">🏋️</div>
        <div class="ex-info">
          <div class="ex-name">เวท</div>
          <div class="ex-sub" id="weightSub">แตะเพื่อบันทึก</div>
        </div>
        <div class="ex-badge todo" id="weightBadge">+</div>
      </div>
      <div class="ex-row" id="tileCardio" onclick="openExercise('cardio')">
        <div class="ex-icon">🏃</div>
        <div class="ex-info">
          <div class="ex-name">คาร์ดิโอ</div>
          <div class="ex-sub" id="cardioSub">แตะเพื่อบันทึก</div>
        </div>
        <div class="ex-badge todo" id="cardioBadge">+</div>
      </div>
      <div class="water-row" id="waterCheckin" onclick="toggleWater()">
        <div class="ex-icon">💧</div>
        <div class="ex-info">
          <div class="ex-name">ดื่มน้ำเพียงพอ</div>
          <div class="ex-sub" id="waterSub">แตะเมื่อดื่มน้ำครบแล้ว</div>
        </div>
        <div class="ex-badge todo" id="waterCheck">+</div>
      </div>
    </div>
  </div>

  <!-- FOOD -->
  <div id="screenFood" class="screen">
    <div class="food-top">
      <div style="font-size:20px;font-weight:900;letter-spacing:-.5px">บันทึกอาหาร</div>
      <button class="btn-sm btn-lime" onclick="openManualFood()">+ กรอกเอง</button>
    </div>
    <div class="date-nav">
      <button class="dnav-btn" onclick="shiftDate(-1)">←</button>
      <div class="dnav-label" id="foodDate"></div>
      <button class="dnav-today" id="btnToday" onclick="jumpToday()" style="display:none">วันนี้</button>
      <button class="dnav-btn" id="dnext" onclick="shiftDate(1)">→</button>
    </div>
    <div class="fsearch-wrap">
      <input class="fsearch" id="foodSearch" placeholder="ค้นหาอาหาร เช่น ข้าวมันไก่..." oninput="onFoodSearch(this.value)" autocomplete="off" autocorrect="off" spellcheck="false">
      <div class="sr-dropdown" id="srDropdown"></div>
    </div>
    <div class="macro-sec">
      <div class="kcal-ring">
        <svg viewBox="0 0 72 72"><circle cx="36" cy="36" r="30" fill="none" stroke="var(--line2)" stroke-width="5"/><circle id="kcalArc" cx="36" cy="36" r="30" fill="none" stroke="var(--lime)" stroke-width="5" stroke-linecap="round" stroke-dasharray="188" stroke-dashoffset="188" transform="rotate(-90 36 36)" style="transition:stroke-dashoffset .5s"/></svg>
        <div class="kcal-txt"><div class="kcal-num" id="kcalEaten">0</div><div class="kcal-lbl">/ <span id="kcalTarget">-</span><br>kcal</div></div>
      </div>
      <div class="macro-bars">
        <div class="mb-row"><div class="mb-lbl"><span>คาร์บ</span><span id="carbVal">0g</span></div><div class="mb-bar"><div class="mb-fill fill-c" id="carbBar" style="width:0%"></div></div></div>
        <div class="mb-row"><div class="mb-lbl"><span>โปรตีน</span><span id="proteinVal">0g</span></div><div class="mb-bar"><div class="mb-fill fill-p" id="proteinBar" style="width:0%"></div></div></div>
        <div class="mb-row"><div class="mb-lbl"><span>ไขมัน</span><span id="fatVal">0g</span></div><div class="mb-bar"><div class="mb-fill fill-f" id="fatBar" style="width:0%"></div></div></div>
      </div>
    </div>
    <div class="food-log-sec"><div id="foodLogList"><div style="text-align:center;color:var(--t2);padding:24px 0;font-size:13px">ยังไม่มีรายการอาหาร</div></div></div>
  </div>

  <!-- PROGRESS -->
  <div id="screenProgress" class="screen">
    <div class="sec" style="padding-top:calc(var(--st)+16px)">
      <div style="font-size:20px;font-weight:900;letter-spacing:-.5px;margin-bottom:16px">สถิติ</div>
      <div class="stat-grid">
        <div class="sg-cell"><div class="sg-val" id="statLevel">1</div><div class="sg-lbl">Level</div></div>
        <div class="sg-cell"><div class="sg-val" style="color:var(--grn)" id="statStreak">0</div><div class="sg-lbl">วันติด</div></div>
        <div class="sg-cell"><div class="sg-val" style="color:var(--t2)" id="statTotalXP">0</div><div class="sg-lbl">XP รวม</div></div>
        <div class="sg-cell"><div class="sg-val" style="color:var(--t2)" id="statCheckin">0</div><div class="sg-lbl">วันเช็คอิน</div></div>
        <div class="sg-cell sg-full"><div class="sg-val" id="statCoins">0</div><div class="sg-lbl">เหรียญสะสม</div></div>
      </div>
      <div class="sec-lbl" style="margin-bottom:10px">7 วันล่าสุด</div>
      <div class="week-row" id="weekGrid"></div>
    </div>
  </div>

  <!-- PROFILE -->
  <div id="screenProfile" class="screen">
    <div class="prof-hero">
      <div class="prof-emoji" id="profileAvatarBig"></div>
      <div class="prof-name" id="profileName"></div>
      <div class="prof-goal-badge" id="profileGoalBadge"></div>
      <div class="prof-stats" id="profileStats"></div>
    </div>
    <div class="sec" id="goalTargetCard" style="display:none">
      <div class="sec-lbl">เป้าหมาย</div>
      <div class="gtarget-row" id="goalTargets"></div>
    </div>
    <div class="sec">
      <div class="sec-lbl">เป้าประจำวัน</div>
      <div id="dailyTargets"></div>
    </div>
    <div class="sec">
      <div class="sec-lbl">GitHub Auto-Sync</div>
      <div class="sync-row">
        <div class="sync-dot" id="syncDot"></div>
        <div class="sync-text" id="syncText">ไม่ได้เชื่อมต่อ</div>
        <button class="btn-sm" id="syncDisconnectBtn" style="display:none;background:rgba(255,80,80,.1);color:var(--red);border:1px solid rgba(255,80,80,.2);font-size:11px;padding:5px 10px" onclick="ghDisconnect()">ยกเลิก</button>
      </div>
      <div id="ghConnectWrap">
        <p style="font-size:12px;color:var(--t2);margin-bottom:10px;line-height:1.6">เชื่อม GitHub Gist เพื่อ auto-save ข้อมูลทุก 30 วิ — ใช้ได้ทั้งใน artifact และไฟล์ desktop</p>
        <button class="btn btn-lime" style="font-size:13px;padding:11px" onclick="openGitHubSetup()">เชื่อมต่อ GitHub</button>
      </div>
      <div id="ghSyncWrap" style="display:none">
        <button class="btn btn-outline" style="font-size:13px;padding:11px" onclick="ghSave()">Sync ตอนนี้</button>
      </div>
    </div>
    <div class="sec">
      <div class="sec-lbl">สำรองข้อมูล (Manual)</div>
      <div style="display:flex;gap:8px">
        <button class="btn btn-outline" style="font-size:13px;padding:11px" onclick="exportData()">📋 Copy</button>
        <button class="btn btn-outline" style="font-size:13px;padding:11px" onclick="openImport()">📥 Paste</button>
      </div>
    </div>
    <div class="sec" style="display:flex;flex-direction:column;gap:8px">
      <button class="btn btn-outline" onclick="switchProfile()">เปลี่ยนโปรไฟล์</button>
      <button class="btn" style="background:rgba(255,80,80,.1);color:var(--red);border:1px solid rgba(255,80,80,.2)" onclick="deleteProfile()">ลบโปรไฟล์</button>
    </div>
    <div style="height:18px"></div>
  </div>

  <div class="bnav">
    <button class="nb on" onclick="showTab('Home')">หน้าหลัก</button>
    <button class="nb" onclick="showTab('Food')">อาหาร</button>
    <button class="nb" onclick="showTab('Progress')">สถิติ</button>
    <button class="nb" onclick="showTab('Profile')">โปรไฟล์</button>
  </div>
</div>

<!-- MODAL: EXERCISE -->
<div class="modal" id="modalExercise">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title" id="exModalTitle">เวท</div>
    <div style="font-size:12px;color:var(--t2);margin-bottom:10px">เลือกหรือกรอกจำนวนนาที</div>
    <div class="dur-grid" id="durGrid"></div>
    <div class="form-group">
      <label class="form-lbl">กรอกเอง (นาที)</label>
      <input class="form-input" id="customMins" type="number" placeholder="เช่น 75" min="1" max="300" oninput="selectDur(null,this.value)">
    </div>
    <div class="dur-preview" id="durPreview">
      <div><div class="dp-val" style="color:var(--lime)" id="prevXP">–</div><div class="dp-lbl">XP</div></div>
      <div><div class="dp-val" style="color:var(--lime)" id="prevCoins">–</div><div class="dp-lbl">เหรียญ</div></div>
      <div><div class="dp-val" style="color:var(--red)" id="prevBurn">–</div><div class="dp-lbl">kcal เผา</div></div>
    </div>
    <div class="form-group" style="margin-bottom:12px">
      <label class="form-lbl">แคลจริงจากเครื่อง (ไม่บังคับ)</label>
      <input class="form-input" id="exKcalOverride" type="number" placeholder="เช่น 380 — กรอกเพื่อใช้แทนค่าคำนวณ" oninput="onKcalOverride()">
    </div>
    <div class="btn-row">
      <button class="btn btn-outline" onclick="closeModal('modalExercise')">ยกเลิก</button>
      <button class="btn btn-lime" onclick="confirmExercise()">บันทึก ✓</button>
    </div>
  </div>
</div>

<!-- MODAL: FOOD SEARCH -->
<div class="modal" id="modalFoodMeal">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title" id="modalFoodTitle">เพิ่มอาหาร</div>
    <div class="form-group"><label class="form-lbl">มื้อ</label>
      <select class="form-input" id="srMeal">
        <option value="breakfast">🌅 เช้า</option><option value="lunch">☀️ กลางวัน</option>
        <option value="dinner">🌙 เย็น</option><option value="snack">🍪 ของว่าง</option>
      </select>
    </div>
    <div class="form-group"><label class="form-lbl">จำนวน</label>
      <div style="display:flex;gap:8px;align-items:center">
        <input class="form-input" id="srQty" type="number" value="1" min="0.25" step="0.25" style="width:75px;flex-shrink:0">
        <span id="srUnitLabel" style="color:var(--t2);font-size:13px"></span>
      </div>
    </div>
    <div id="srPreviewMacros" style="background:var(--s2);border-radius:4px;padding:10px;margin-bottom:13px;display:grid;grid-template-columns:repeat(4,1fr);gap:8px;text-align:center;border:1px solid var(--line)"></div>
    <div class="btn-row">
      <button class="btn btn-outline" onclick="closeModal('modalFoodMeal')">ยกเลิก</button>
      <button class="btn btn-lime" onclick="confirmAddFood()">เพิ่ม</button>
    </div>
  </div>
</div>

<!-- MODAL: EDIT FOOD -->
<div class="modal" id="modalEditFood">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title">แก้ไขรายการอาหาร</div>
    <div class="form-group"><label class="form-lbl">ชื่ออาหาร</label><input class="form-input" id="efName" placeholder="ชื่ออาหาร"></div>
    <div class="form-group"><label class="form-lbl">แคลอรี่ (kcal)</label><input class="form-input" id="efKcal" type="number"></div>
    <div class="form-row3">
      <div class="form-group"><label class="form-lbl">คาร์บ (g)</label><input class="form-input" id="efCarb" type="number"></div>
      <div class="form-group"><label class="form-lbl">โปรตีน (g)</label><input class="form-input" id="efProtein" type="number"></div>
      <div class="form-group"><label class="form-lbl">ไขมัน (g)</label><input class="form-input" id="efFat" type="number"></div>
    </div>
    <div class="btn-row">
      <button class="btn btn-outline" onclick="closeModal('modalEditFood')">ยกเลิก</button>
      <button class="btn btn-lime" onclick="saveEditFood()">บันทึก ✓</button>
    </div>
  </div>
</div>

<!-- MODAL: MANUAL FOOD -->
<div class="modal" id="modalManualFood">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title">กรอกอาหาร</div>
    <div class="form-group"><label class="form-lbl">ชื่ออาหาร</label><input class="form-input" id="mfName" placeholder="ชื่ออาหาร"></div>
    <div class="form-group"><label class="form-lbl">มื้อ</label>
      <select class="form-input" id="mfMeal">
        <option value="breakfast">🌅 เช้า</option><option value="lunch">☀️ กลางวัน</option>
        <option value="dinner">🌙 เย็น</option><option value="snack">🍪 ของว่าง</option>
      </select>
    </div>
    <div class="form-group"><label class="form-lbl">แคลอรี่ (kcal)</label><input class="form-input" id="mfKcal" type="number" placeholder="เช่น 350"></div>
    <div class="form-row3">
      <div class="form-group"><label class="form-lbl">คาร์บ (g)</label><input class="form-input" id="mfCarb" type="number" placeholder="0"></div>
      <div class="form-group"><label class="form-lbl">โปรตีน (g)</label><input class="form-input" id="mfProtein" type="number" placeholder="0"></div>
      <div class="form-group"><label class="form-lbl">ไขมัน (g)</label><input class="form-input" id="mfFat" type="number" placeholder="0"></div>
    </div>
    <div class="btn-row">
      <button class="btn btn-outline" onclick="closeModal('modalManualFood')">ยกเลิก</button>
      <button class="btn btn-lime" onclick="saveManualFood()">บันทึก</button>
    </div>
  </div>
</div>

<!-- MODAL: GITHUB SETUP -->
<div class="modal" id="modalGitHub">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title">เชื่อมต่อ GitHub</div>
    <p style="font-size:12px;color:var(--t2);margin-bottom:14px;line-height:1.7">
      1. ไปที่ <strong style="color:var(--text)">github.com → Settings → Developer settings<br>→ Personal access tokens → Tokens (classic)</strong><br>
      2. กด Generate → เลือก scope: <strong style="color:var(--lime)">gist</strong> เท่านั้น<br>
      3. Copy token มาวางด้านล่าง — แอพจะหา Gist เดิมให้เอง
    </p>
    <div class="form-group">
      <label class="form-lbl">GitHub Personal Access Token</label>
      <input class="form-input" id="ghToken" type="password" placeholder="ghp_xxxxxxxxxxxx" autocomplete="off">
    </div>
    <div class="btn-row">
      <button class="btn btn-outline" onclick="closeModal('modalGitHub')">ยกเลิก</button>
      <button class="btn btn-lime" onclick="ghConnect()">เชื่อมต่อ ✓</button>
    </div>
  </div>
</div>

<!-- MODAL: IMPORT DATA -->
<div class="modal" id="modalImport">
  <div class="modal-sheet">
    <div class="modal-handle"></div>
    <div class="modal-title">โหลดข้อมูล</div>
    <p style="font-size:12px;color:var(--t2);margin-bottom:10px;line-height:1.6">วาง (Paste) โค้ดที่คัดลอกไว้จากครั้งก่อนลงช่องด้านล่าง</p>
    <textarea id="importJson" style="width:100%;height:130px;background:var(--s2);border:1px solid var(--line);border-radius:4px;padding:10px;color:var(--text);font-size:13px;resize:none;outline:none;font-family:monospace" placeholder="วาง JSON ที่คัดลอกมา..."></textarea>
    <div class="btn-row" style="margin-top:10px">
      <button class="btn btn-outline" onclick="closeModal('modalImport')">ยกเลิก</button>
      <button class="btn btn-lime" onclick="importData()">โหลดข้อมูล ✓</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
const K={profiles:'fq_profiles2',current:'fq_current2'};
const fmtDate=(d)=>`${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;
const today=()=>fmtDate(new Date());
const yesterday=()=>{const d=new Date();d.setDate(d.getDate()-1);return fmtDate(d);};

/* storage with localStorage → sessionStorage → memory fallback */
const _mem={};
const _store={
  get(k){try{return localStorage.getItem(k);}catch(e){try{return sessionStorage.getItem(k);}catch(e2){return _mem[k]??null;}}},
  set(k,v){try{localStorage.setItem(k,v);}catch(e){try{sessionStorage.setItem(k,v);}catch(e2){_mem[k]=v;}}},
  del(k){try{localStorage.removeItem(k);}catch(e){try{sessionStorage.removeItem(k);}catch(e2){delete _mem[k];}}}
};

const gp=()=>JSON.parse(_store.get(K.profiles)||'[]');
const sp=(d)=>_store.set(K.profiles,JSON.stringify(d));
const gcid=()=>_store.get(K.current);
const scid=(id)=>_store.set(K.current,id);
const getProfile=(id)=>gp().find(p=>p.id===id);
const curProfile=()=>getProfile(gcid());
let viewDate=today();
function getViewData(p,date){
  if(!p.days)p.days={};
  if(!p.days[date]){
    if(date===today()){
      p.days[date]={weight:{done:false,mins:0},cardio:{done:false,mins:0},water:false,food:[],xpEarned:0,coinsEarned:0};
    }else{
      return{weight:{done:false,mins:0},cardio:{done:false,mins:0},water:false,food:[]};
    }
  }
  return p.days[date];
}
function shiftDate(n){
  const d=new Date(viewDate+'T12:00:00');d.setDate(d.getDate()+n);
  const nd=d.toISOString().slice(0,10);
  if(nd>today())return;
  viewDate=nd;
  renderFood();
}
function jumpToday(){viewDate=today();renderFood();}

const FOOD_DB=[
  {name:'ข้าวสวย',unit:'ทัพพี',kcal:90,c:20,p:2,f:0},
  {name:'ข้าวเหนียว',unit:'ทัพพี',kcal:100,c:22,p:2,f:0},
  {name:'ข้าวต้ม',unit:'ชาม',kcal:180,c:38,p:4,f:1},
  {name:'ข้าวผัด',unit:'จาน',kcal:450,c:65,p:15,f:14},
  {name:'ข้าวมันไก่',unit:'จาน',kcal:480,c:60,p:28,f:12},
  {name:'ผัดกะเพราไก่ข้าว',unit:'จาน',kcal:520,c:65,p:28,f:14},
  {name:'ผัดกะเพราหมูข้าว',unit:'จาน',kcal:540,c:64,p:24,f:16},
  {name:'ก๋วยเตี๋ยวหมู',unit:'ชาม',kcal:320,c:45,p:18,f:8},
  {name:'ก๋วยเตี๋ยวเนื้อ',unit:'ชาม',kcal:350,c:45,p:22,f:9},
  {name:'ต้มยำกุ้ง',unit:'ชาม',kcal:150,c:8,p:18,f:5},
  {name:'ต้มข่าไก่',unit:'ชาม',kcal:250,c:8,p:20,f:16},
  {name:'แกงเขียวหวานไก่',unit:'ถ้วย',kcal:280,c:12,p:22,f:16},
  {name:'แกงจืด',unit:'ชาม',kcal:100,c:8,p:10,f:3},
  {name:'ส้มตำ',unit:'จาน',kcal:120,c:18,p:4,f:3},
  {name:'ลาบหมู',unit:'จาน',kcal:280,c:10,p:30,f:12},
  {name:'ผัดผักรวม',unit:'จาน',kcal:120,c:10,p:5,f:7},
  {name:'ไก่ย่าง',unit:'ชิ้น',kcal:200,c:2,p:28,f:9},
  {name:'หมูย่าง',unit:'ชิ้น',kcal:220,c:1,p:24,f:13},
  {name:'ปลาทู',unit:'ตัว',kcal:130,c:0,p:20,f:5},
  {name:'อกไก่ต้ม',unit:'100g',kcal:165,c:0,p:31,f:4},
  {name:'ไข่ดาว',unit:'ฟอง',kcal:90,c:0,p:6,f:7},
  {name:'ไข่ต้ม',unit:'ฟอง',kcal:78,c:1,p:6,f:5},
  {name:'ไข่เจียว',unit:'ฟอง',kcal:110,c:1,p:7,f:9},
  {name:'เต้าหู้',unit:'ก้อน',kcal:80,c:2,p:9,f:4},
  {name:'มาม่า',unit:'ซอง',kcal:360,c:52,p:8,f:13},
  {name:'ขนมปัง',unit:'แผ่น',kcal:80,c:15,p:3,f:1},
  {name:'ข้าวโอ๊ต',unit:'ถ้วย',kcal:300,c:54,p:10,f:5},
  {name:'ซีเรียล',unit:'ถ้วย',kcal:200,c:44,p:4,f:2},
  {name:'กล้วยน้ำว้า',unit:'ลูก',kcal:90,c:23,p:1,f:0},
  {name:'มะม่วง',unit:'ลูก',kcal:100,c:25,p:1,f:1},
  {name:'ฝรั่ง',unit:'ลูก',kcal:68,c:14,p:3,f:1},
  {name:'มะละกอ',unit:'ถ้วย',kcal:55,c:14,p:1,f:0},
  {name:'แอปเปิ้ล',unit:'ลูก',kcal:80,c:21,p:0,f:0},
  {name:'นมวัว',unit:'แก้ว (250ml)',kcal:150,c:12,p:8,f:8},
  {name:'นมถั่วเหลือง',unit:'แก้ว (250ml)',kcal:100,c:10,p:7,f:3},
  {name:'น้ำเต้าหู้',unit:'แก้ว (300ml)',kcal:110,c:11,p:9,f:3},
  {name:'โยเกิร์ต',unit:'ถ้วย (150g)',kcal:100,c:14,p:6,f:2},
  {name:'กาแฟดำ',unit:'แก้ว',kcal:5,c:0,p:0,f:0},
  {name:'กาแฟนม',unit:'แก้ว',kcal:60,c:6,p:3,f:2},
  {name:'ชาไทย',unit:'แก้ว',kcal:150,c:28,p:2,f:4},
  {name:'น้ำอัดลม',unit:'กระป๋อง',kcal:140,c:38,p:0,f:0},
  {name:'น้ำผลไม้',unit:'แก้ว',kcal:110,c:26,p:1,f:1},
  {name:'โปรตีนเชค',unit:'ช้อน (30g)',kcal:120,c:5,p:24,f:2},
  {name:'อัลมอนด์',unit:'30g',kcal:174,c:6,p:6,f:15},
  {name:'ถั่วลิสง',unit:'30g',kcal:170,c:5,p:7,f:14},
  {name:'แฮมเบอร์เกอร์',unit:'ชิ้น',kcal:450,c:40,p:25,f:20},
  {name:'พิซซ่า',unit:'ชิ้น',kcal:285,c:36,p:12,f:10},
  {name:'เฟรนช์ฟราย',unit:'กล่องกลาง',kcal:320,c:42,p:4,f:15},
  {name:'สเต็กเนื้อ',unit:'150g',kcal:330,c:0,p:36,f:20},
  {name:'สลัดผัก',unit:'จาน',kcal:50,c:8,p:2,f:1},
  {name:'ช็อกโกแลต',unit:'แท่ง (40g)',kcal:210,c:24,p:3,f:12},
  {name:'ผักบุ้งผัดน้ำมันหอย',unit:'จาน',kcal:110,c:8,p:4,f:7},
  {name:'บร็อคโคลี่ต้ม',unit:'ถ้วย',kcal:55,c:11,p:4,f:1},
  {name:'แกงส้ม',unit:'ชาม',kcal:180,c:15,p:18,f:5},
  {name:'ข้าวหน้าเป็ด',unit:'จาน',kcal:500,c:62,p:30,f:14},
  {name:'ขนมจีน',unit:'จาน',kcal:350,c:60,p:12,f:6},
];

const EX_RATES={weight:{xpPerMin:3,burnPerMin:4},cardio:{xpPerMin:2.5,burnPerMin:7}};
const DUR_OPTIONS=[15,20,30,45,60,90];

function calcBMR(p){
  return p.gender==='male'?10*p.weight+6.25*p.height-5*p.age+5:10*p.weight+6.25*p.height-5*p.age-161;
}
function calcTDEE(p){
  const f={sedentary:1.2,light:1.375,moderate:1.55,active:1.725,very_active:1.9};
  return Math.round(calcBMR(p)*(f[p.activity]||1.55));
}
function calcTargets(p){
  const tdee=calcTDEE(p);
  let kcal=tdee+(p.goal==='muscle_gain'?300:p.goal==='fat_loss'?-500:0);
  const protein=Math.round(p.weight*(p.goal==='fat_loss'?2:1.8));
  const fat=Math.round(kcal*0.25/9);
  const carb=Math.round((kcal-protein*4-fat*9)/4);
  return{kcal:Math.max(1200,kcal),protein,carb,fat,tdee};
}
function getLevelFromXP(xp){
  let level=1,needed=0;
  while(xp>=needed+level*150){needed+=level*150;level++;}
  return{level,xpIn:xp-needed,xpNext:level*150};
}
function goalEmoji(g){return g==='fat_loss'?'🔥':g==='muscle_gain'?'💪':'⚖️';}
function goalLabel(g){return g==='fat_loss'?'ลดไขมัน':g==='muscle_gain'?'เพิ่มกล้าม':'คงสภาพ';}

function getTodayData(p){
  const d=today();
  if(!p.days)p.days={};
  if(!p.days[d])p.days[d]={weight:{done:false,mins:0},cardio:{done:false,mins:0},water:false,food:[],xpEarned:0,coinsEarned:0};
  return p.days[d];
}
function dayCheckinCount(dayData){
  let n=0;
  if(dayData.weight&&dayData.weight.done)n++;
  if(dayData.cardio&&dayData.cardio.done)n++;
  if(dayData.water)n++;
  return n;
}
function dayHasCheckin(dayData){return dayCheckinCount(dayData)>0;}

function saveProfileData(p){
  const all=gp();const idx=all.findIndex(x=>x.id===p.id);
  if(idx>=0){all[idx]=p;sp(all);}
  // debounced GitHub sync — don't hammer API on rapid changes
  if(GH.token&&GH.gistId){
    clearTimeout(GH._debounce);
    GH._debounce=setTimeout(()=>GH.save(),5000);
  }
}

let toastTimer;
function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer=setTimeout(()=>t.classList.remove('show'),2200);
}

function processYesterday(p){
  const yd=yesterday();
  if(!p.days||!p.days[yd])return;
  const ydata=p.days[yd];
  if(ydata.deficitProcessed)return;
  const targets=calcTargets(p);
  const eaten=ydata.food.reduce((s,f)=>s+f.kcal,0);
  if(eaten>=1200){
    const deficit=targets.kcal-eaten;
    if(deficit>0){
      const coins=Math.floor(deficit/2);
      p.coins=(p.coins||0)+coins;
      ydata.deficitCoins=coins;
    }
  }
  ydata.deficitProcessed=true;
  saveProfileData(p);
}

const STREAK_MILESTONES={3:20,7:50,14:100,30:250};
function checkStreak(p){
  const d=today();
  if(!p.lastActive){p.lastActive=d;p.streak=1;}
  else{
    const diff=(new Date(d)-new Date(p.lastActive))/(1000*60*60*24);
    if(diff>=1&&diff<2){
      p.streak=(p.streak||0)+1;
      if(STREAK_MILESTONES[p.streak]){
        p.coins=(p.coins||0)+STREAK_MILESTONES[p.streak];
        setTimeout(()=>showToast(`Streak ${p.streak} วัน! +${STREAK_MILESTONES[p.streak]} เหรียญ`),500);
      }
    }else if(diff>=2){p.streak=1;}
    p.lastActive=d;
  }
  saveProfileData(p);
}

function renderProfileSelect(){
  document.getElementById('profileSelect').style.display='flex';
  document.getElementById('setup').style.display='none';
  document.getElementById('app').style.display='none';
  const profiles=gp();
  document.getElementById('profileList').innerHTML=profiles.map(p=>{
    const{level}=getLevelFromXP(p.xp||0);
    return`<div class="profile-card" onclick="selectProfile('${p.id}')">
      <div class="pc-avatar">${goalEmoji(p.goal)}</div>
      <div class="pc-info">
        <div class="pc-name">${p.name}</div>
        <div class="pc-sub">${goalLabel(p.goal)} · ${(p.coins||0).toLocaleString()} เหรียญ · Lv.${level}</div>
      </div>
      <div class="pc-badge">LV.${level}</div>
    </div>`;
  }).join('');
}

function selectProfile(id){
  scid(id);
  const p=getProfile(id);
  processYesterday(p);
  checkStreak(p);
  renderApp();
}

let setupData={};let setupStep=0;
const setupSteps=['gender','goal','targets','activity','info'];

function startSetup(){
  setupData={};setupStep=0;
  document.getElementById('profileSelect').style.display='none';
  document.getElementById('setup').style.display='flex';
  renderSetupStep();
}
function backSetup(){if(setupStep===0)renderProfileSelect();else{setupStep--;renderSetupStep();}}
function renderSetupStep(){
  document.getElementById('setupProg').innerHTML=setupSteps.map((_,i)=>`<div class="sp-dot${i<=setupStep?' on':''}"></div>`).join('');
  const c=document.getElementById('setupContent');
  const step=setupSteps[setupStep];
  if(step==='gender'){
    c.innerHTML=`<div class="setup-title">เพศ</div>
    <div class="setup-sub">ใช้คำนวณแคลอรี่ที่เหมาะสม</div>
    <div class="s-opts">
      <div class="s-opt${setupData.gender==='male'?' on':''}" onclick="setSetup('gender','male');renderSetupStep()">
        <div class="s-opt-icon">♂️</div><div><div class="s-opt-title">ผู้ชาย</div></div>
      </div>
      <div class="s-opt${setupData.gender==='female'?' on':''}" onclick="setSetup('gender','female');renderSetupStep()">
        <div class="s-opt-icon">♀️</div><div><div class="s-opt-title">ผู้หญิง</div></div>
      </div>
    </div>
    <button class="btn btn-lime" onclick="nextSetup()" ${!setupData.gender?'disabled style="opacity:.4"':''}>ถัดไป →</button>`;
  }else if(step==='goal'){
    const opts=[
      {v:'fat_loss',icon:'🔥',t:'ลดไขมัน / ลดน้ำหนัก',s:'แคลต่ำกว่า TDEE'},
      {v:'muscle_gain',icon:'💪',t:'เพิ่มกล้ามเนื้อ',s:'แคลสูงกว่า TDEE + เน้นโปรตีน'},
      {v:'maintenance',icon:'⚖️',t:'คงรูปร่าง',s:'สมดุล'},
    ];
    c.innerHTML=`<div class="setup-title">เป้าหมาย</div>
    <div class="setup-sub">เพื่อคำนวณแคลอรี่และ Quest</div>
    <div class="s-opts">${opts.map(o=>`<div class="s-opt${setupData.goal===o.v?' on':''}" onclick="setSetup('goal','${o.v}');renderSetupStep()">
      <div class="s-opt-icon">${o.icon}</div>
      <div><div class="s-opt-title">${o.t}</div><div class="s-opt-sub">${o.s}</div></div>
    </div>`).join('')}</div>
    <button class="btn btn-lime" onclick="nextSetup()" ${!setupData.goal?'disabled style="opacity:.4"':''}>ถัดไป →</button>`;
  }else if(step==='targets'){
    c.innerHTML=`<div class="setup-title">ตั้งเป้าหมาย</div>
    <div class="setup-sub">ใช้คำนวณ "ถึงเป้าเร็วขึ้นกี่วัน" (ไม่บังคับ)</div>
    ${setupData.goal!=='maintenance'?`<div class="form-group"><label class="form-lbl">น้ำหนักเป้าหมาย (kg)</label><input class="form-input" id="st_weight" type="number" placeholder="เช่น 65" value="${setupData.targetWeight||''}"></div>`:''}
    <div class="form-group"><label class="form-lbl">ไขมันเป้าหมาย (%)</label><input class="form-input" id="st_fat" type="number" placeholder="เช่น 15" value="${setupData.targetFat||''}"></div>
    <div class="form-group"><label class="form-lbl">ระยะเวลา (สัปดาห์)</label><input class="form-input" id="st_weeks" type="number" placeholder="เช่น 12" value="${setupData.timeline||''}"></div>
    <div class="btn-row">
      <button class="btn btn-outline" onclick="nextSetup()">ข้ามขั้นนี้</button>
      <button class="btn btn-lime" onclick="saveTargets()">ถัดไป →</button>
    </div>`;
  }else if(step==='activity'){
    const opts=[
      {v:'sedentary',icon:'🛋️',t:'นั่งส่วนใหญ่',s:'ออฟฟิศ'},
      {v:'light',icon:'🚶',t:'เบา',s:'ออก 1-3 วัน/สัปดาห์'},
      {v:'moderate',icon:'🏃',t:'ปานกลาง',s:'ออก 3-5 วัน/สัปดาห์'},
      {v:'active',icon:'🏋️',t:'หนัก',s:'ออก 6-7 วัน'},
    ];
    c.innerHTML=`<div class="setup-title">ระดับกิจกรรม</div>
    <div class="setup-sub">ใช้คำนวณ TDEE</div>
    <div class="s-opts">${opts.map(o=>`<div class="s-opt${setupData.activity===o.v?' on':''}" onclick="setSetup('activity','${o.v}');renderSetupStep()">
      <div class="s-opt-icon">${o.icon}</div>
      <div><div class="s-opt-title">${o.t}</div><div class="s-opt-sub">${o.s}</div></div>
    </div>`).join('')}</div>
    <button class="btn btn-lime" onclick="nextSetup()" ${!setupData.activity?'disabled style="opacity:.4"':''}>ถัดไป →</button>`;
  }else if(step==='info'){
    c.innerHTML=`<div class="setup-title">ข้อมูลส่วนตัว</div>
    <div class="setup-sub">ใช้คำนวณแคลอรี่</div>
    <div class="form-group"><label class="form-lbl">ชื่อ</label><input class="form-input" id="si_name" placeholder="ชื่อของคุณ" value="${setupData.name||''}"></div>
    <div class="form-row">
      <div class="form-group"><label class="form-lbl">น้ำหนัก (kg)</label><input class="form-input" id="si_weight" type="number" placeholder="70" value="${setupData.weight||''}"></div>
      <div class="form-group"><label class="form-lbl">ส่วนสูง (cm)</label><input class="form-input" id="si_height" type="number" placeholder="170" value="${setupData.height||''}"></div>
    </div>
    <div class="form-group"><label class="form-lbl">อายุ</label><input class="form-input" id="si_age" type="number" placeholder="25" value="${setupData.age||''}"></div>
    <button class="btn btn-lime" onclick="finishSetup()" style="margin-top:8px">เริ่มเลย!</button>`;
  }
}
function setSetup(k,v){setupData[k]=v;}
function nextSetup(){setupStep++;renderSetupStep();}
function saveTargets(){
  const wEl=document.getElementById('st_weight');
  const fEl=document.getElementById('st_fat');
  const wkEl=document.getElementById('st_weeks');
  if(wEl&&wEl.value)setupData.targetWeight=parseFloat(wEl.value);
  if(fEl&&fEl.value)setupData.targetFat=parseFloat(fEl.value);
  if(wkEl&&wkEl.value)setupData.timeline=parseInt(wkEl.value);
  nextSetup();
}
function finishSetup(){
  const name=document.getElementById('si_name').value.trim();
  const weight=parseFloat(document.getElementById('si_weight').value);
  const height=parseFloat(document.getElementById('si_height').value);
  const age=parseInt(document.getElementById('si_age').value);
  if(!name||!weight||!height||!age){showToast('กรุณากรอกข้อมูลให้ครบ');return;}
  const id='p_'+Date.now();
  const p={id,...setupData,name,weight,height,age,xp:0,coins:0,streak:1,lastActive:today(),totalCheckins:0,days:{}};
  const all=gp();all.push(p);sp(all);
  selectProfile(id);
}

function renderApp(){
  document.getElementById('profileSelect').style.display='none';
  document.getElementById('setup').style.display='none';
  document.getElementById('app').style.display='block';
  showTab('Home');
}
function showTab(tab){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.querySelectorAll('.nb').forEach(b=>b.classList.remove('on'));
  document.getElementById('screen'+tab).classList.add('active');
  document.querySelectorAll('.nb')[['Home','Food','Progress','Profile'].indexOf(tab)].classList.add('on');
  if(tab==='Home')renderHome();
  else if(tab==='Food'){viewDate=today();renderFood();}
  else if(tab==='Progress')renderProgress();
  else if(tab==='Profile')renderProfileTab();
}

function renderHome(){
  const p=curProfile();if(!p)return;
  const d=getTodayData(p);
  const{level,xpIn,xpNext}=getLevelFromXP(p.xp||0);
  const pct=Math.min(100,Math.round(xpIn/xpNext*100));
  const hours=new Date().getHours();
  const greet=hours<12?'อรุณสวัสดิ์':hours<18?'สวัสดี':'ตอนเย็นสวัสดิ์';
  document.getElementById('homeGreet').textContent=`${greet}, ${p.name}`;
  document.getElementById('homeDate').textContent=new Date().toLocaleDateString('th-TH',{weekday:'long',day:'numeric',month:'long'});
  document.getElementById('homeLv').textContent=level;
  document.getElementById('xpFill').style.width=pct+'%';
  document.getElementById('xpText').textContent=`${xpIn}/${xpNext} XP`;
  document.getElementById('streakVal').textContent=p.streak||1;
  document.getElementById('coinVal').textContent=(p.coins||0).toLocaleString();
  document.getElementById('checkinCount').textContent=`${dayCheckinCount(d)}/3`;
  renderMonthCalendar(p);
  renderDeficitCard(p,d);
  renderYesterdayCard(p);
  renderCheckinTiles(d);
}

function renderMonthCalendar(p){
  const now=new Date();
  const year=now.getFullYear();
  const month=now.getMonth();
  const todayStr=today();
  const monthNames=['ม.ค.','ก.พ.','มี.ค.','เม.ย.','พ.ค.','มิ.ย.','ก.ค.','ส.ค.','ก.ย.','ต.ค.','พ.ย.','ธ.ค.'];
  document.getElementById('calMonthLbl').textContent=`${monthNames[month]} ${year+543}`;
  const streak=p.streak||1;
  document.getElementById('calStreakLbl').textContent=`${streak} วันติด`;
  const firstDay=new Date(year,month,1).getDay();
  const daysInMonth=new Date(year,month+1,0).getDate();
  const dayNames=['อา','จ','อ','พ','พฤ','ศ','ส'];
  let html=dayNames.map(d=>`<div class="cal-dn">${d}</div>`).join('');
  for(let i=0;i<firstDay;i++)html+=`<div class="cal-d"></div>`;
  for(let day=1;day<=daysInMonth;day++){
    const dateStr=`${year}-${String(month+1).padStart(2,'0')}-${String(day).padStart(2,'0')}`;
    const isToday=dateStr===todayStr;
    const hasCheckin=p.days&&p.days[dateStr]&&dayHasCheckin(p.days[dateStr]);
    const cls=['cal-d','in',isToday?'tod':'',hasCheckin?'chk':''].filter(Boolean).join(' ');
    html+=`<div class="${cls}">${day}</div>`;
  }
  document.getElementById('calGrid').innerHTML=html;
}

function renderDeficitCard(p,d){
  const targets=calcTargets(p);
  const eaten=d.food.reduce((s,f)=>s+f.kcal,0);
  const goalKcal=targets.kcal;
  const deficit=goalKcal-eaten;
  const pct=Math.min(100,Math.round(eaten/goalKcal*100));
  const barColor=pct>100?'var(--red)':pct>80?'var(--lime)':'var(--grn)';
  document.getElementById('dcTdeeLabel').textContent=`TDEE ${targets.tdee}`;
  document.getElementById('dcBar').style.width=pct+'%';
  document.getElementById('dcBar').style.background=barColor;
  document.getElementById('dcEaten').textContent=eaten;
  document.getElementById('dcTarget').textContent=goalKcal;
  if(deficit>0){
    document.getElementById('dcDeficit').textContent=deficit+' kcal';
    document.getElementById('dcDeficit').style.color='var(--grn)';
    document.getElementById('dcDeficitLbl').textContent='ขาดแคล';
    document.getElementById('dcProjCoins').textContent='+'+Math.floor(deficit/2);
    let daysNote='–';
    if(p.targetWeight&&p.weight>p.targetWeight){
      const days=Math.round((p.weight-p.targetWeight)*7700/deficit);
      daysNote=days>365?Math.round(days/30)+'mo':days+'d';
    }
    document.getElementById('dcDays').textContent=daysNote;
    document.getElementById('dcNote').textContent=`ขาดแคลอีก ${deficit} kcal ← ดี ลดไขมัน −${Math.round(deficit/7.7)}g วันนี้`;
  }else if(deficit<0){
    document.getElementById('dcDeficit').textContent=Math.abs(deficit)+' kcal';
    document.getElementById('dcDeficit').style.color='var(--red)';
    document.getElementById('dcDeficitLbl').textContent='เกินเป้า';
    document.getElementById('dcProjCoins').textContent='0';
    document.getElementById('dcDays').textContent='–';
    document.getElementById('dcNote').textContent=`กินเกิน ${Math.abs(deficit)} kcal จากเป้าวันนี้`;
  }else{
    document.getElementById('dcDeficit').textContent='ตรงเป้า';
    document.getElementById('dcDeficit').style.color='var(--t2)';
    document.getElementById('dcDeficitLbl').textContent='สถานะ';
    document.getElementById('dcProjCoins').textContent='0';
    document.getElementById('dcDays').textContent='–';
    document.getElementById('dcNote').textContent='กินตรงเป้าพอดี';
  }
}

function renderCheckinTiles(d){
  const tw=document.getElementById('tileWeight');
  const ws=document.getElementById('weightSub');
  const wb=document.getElementById('weightBadge');
  if(d.weight&&d.weight.done){
    tw.classList.add('done-weight');
    ws.textContent=`${d.weight.mins} นาที · +${Math.round(d.weight.mins*EX_RATES.weight.xpPerMin)} XP`;
    wb.className='ex-badge done-blue';wb.textContent='✓';
  }else{tw.classList.remove('done-weight');ws.textContent='แตะเพื่อบันทึก';wb.className='ex-badge todo';wb.textContent='+';}
  const tc=document.getElementById('tileCardio');
  const cs=document.getElementById('cardioSub');
  const cb=document.getElementById('cardioBadge');
  if(d.cardio&&d.cardio.done){
    tc.classList.add('done');
    cs.textContent=`${d.cardio.mins} นาที · +${Math.round(d.cardio.mins*EX_RATES.cardio.xpPerMin)} XP`;
    cb.className='ex-badge done-lime';cb.textContent='✓';
  }else{tc.classList.remove('done');cs.textContent='แตะเพื่อบันทึก';cb.className='ex-badge todo';cb.textContent='+';}
  const wc=document.getElementById('waterCheckin');
  const wck=document.getElementById('waterCheck');
  const wst=document.getElementById('waterSub');
  if(d.water){
    wc.style.opacity='1';
    wck.className='ex-badge done-blue';wck.textContent='✓';
    wst.textContent='ดื่มน้ำครบแล้ว';
  }else{
    wck.className='ex-badge todo';wck.textContent='+';
    wst.textContent='แตะเมื่อดื่มน้ำครบแล้ว';
  }
}

function renderYesterdayCard(p){
  const el=document.getElementById('ydayCard');
  const yd=yesterday();
  if(!p.days||!p.days[yd]){el.innerHTML='';return;}
  const ydata=p.days[yd];
  const targets=calcTargets(p);
  const eaten=ydata.food.reduce((s,f)=>s+f.kcal,0);
  const items=[];
  if(!dayHasCheckin(ydata)){
    items.push({ico:'—',msg:'ไม่มีการเช็คอินเลยเมื่อวาน',fix:'วันนี้ทำอย่างน้อย 1 ข้อนะ'});
  }else{
    if(ydata.weight&&ydata.weight.done)items.push({ico:'🏋️',msg:`เวท ${ydata.weight.mins} นาที ✓`,fix:''});
    if(ydata.cardio&&ydata.cardio.done)items.push({ico:'🏃',msg:`คาร์ดิโอ ${ydata.cardio.mins} นาที ✓`,fix:''});
    if(ydata.water)items.push({ico:'💧',msg:'ดื่มน้ำครบ ✓',fix:''});
  }
  if(eaten>0){
    const deficit=targets.kcal-eaten;
    if(deficit>100&&ydata.deficitCoins)items.push({ico:'🪙',msg:`ขาดแคล ${deficit} kcal → +${ydata.deficitCoins} เหรียญ!`,fix:''});
    else if(deficit<-300)items.push({ico:'!',msg:`กินเกินเป้า ${Math.abs(deficit)} kcal`,fix:'วันนี้ลองควบคุมดูนะ'});
  }
  if(!items.length){el.innerHTML='';return;}
  const ydStr=new Date(yd).toLocaleDateString('th-TH',{day:'numeric',month:'short'});
  el.innerHTML=`<div class="sec">
    <div class="sec-lbl">เมื่อวาน ${ydStr}</div>
    ${items.map(it=>`<div class="yday-item">
      <div class="yday-ico">${it.ico}</div>
      <div class="yday-msg">${it.msg}${it.fix?`<div class="yday-fix">${it.fix}</div>`:''}</div>
    </div>`).join('')}
  </div>`;
}

let currentExType=null;let selectedMins=30;

function openExercise(type){
  currentExType=type;selectedMins=30;
  document.getElementById('exModalTitle').textContent=type==='weight'?'🏋️ เวท':'🏃 คาร์ดิโอ';
  document.getElementById('customMins').value='';
  document.getElementById('exKcalOverride').value='';
  renderDurGrid(30);
  document.getElementById('modalExercise').classList.add('show');
}
function onKcalOverride(){
  const val=parseInt(document.getElementById('exKcalOverride').value)||0;
  if(val>0){
    document.getElementById('prevCoins').textContent='+'+Math.floor(val/5);
    document.getElementById('prevBurn').textContent=val+' kcal';
  }else{
    updateDurPreview(selectedMins,EX_RATES[currentExType]);
  }
}
function renderDurGrid(selected){
  const rates=EX_RATES[currentExType];
  document.getElementById('durGrid').innerHTML=DUR_OPTIONS.map(m=>`
    <div class="dur-opt${m===selected?' on':''}" onclick="selectDur(${m},null)">${m} นาที</div>`).join('');
  updateDurPreview(selected,rates);
}
function selectDur(mins,raw){
  const m=mins!==null?mins:(parseInt(raw)||0);
  if(m<=0)return;
  selectedMins=m;
  const rates=EX_RATES[currentExType];
  document.getElementById('durGrid').querySelectorAll('.dur-opt').forEach(el=>{
    el.classList.toggle('on',parseInt(el.textContent)===m);
  });
  updateDurPreview(m,rates);
}
function updateDurPreview(mins,rates){
  if(!mins||mins<=0){
    ['prevXP','prevCoins','prevBurn'].forEach(id=>document.getElementById(id).textContent='–');return;
  }
  const xp=Math.round(mins*rates.xpPerMin);
  const burn=Math.round(mins*rates.burnPerMin);
  const coins=Math.floor(burn/5);
  document.getElementById('prevXP').textContent='+'+xp;
  document.getElementById('prevCoins').textContent='+'+coins;
  document.getElementById('prevBurn').textContent=burn+' kcal';
}
function confirmExercise(){
  const mins=selectedMins;
  if(!mins||mins<=0){showToast('เลือกจำนวนนาทีก่อน');return;}
  const p=curProfile();const d=getTodayData(p);
  const rates=EX_RATES[currentExType];
  const mult=p.streak>=7?1.5:p.streak>=3?1.2:1;
  const xp=Math.round(mins*rates.xpPerMin*mult);
  const kcalOverride=parseInt(document.getElementById('exKcalOverride').value)||0;
  const burn=kcalOverride>0?kcalOverride:Math.round(mins*rates.burnPerMin);
  const coins=Math.floor(burn/5);
  const wasFirst=!dayHasCheckin(d);
  d[currentExType]={done:true,mins};
  p.xp=(p.xp||0)+xp;
  p.coins=(p.coins||0)+coins;
  if(wasFirst&&dayHasCheckin(d))p.totalCheckins=(p.totalCheckins||0)+1;
  const oldLevel=getLevelFromXP((p.xp||0)-xp).level;
  const newLevel=getLevelFromXP(p.xp).level;
  saveProfileData(p);
  closeModal('modalExercise');
  showToast(`${currentExType==='weight'?'🏋️':'🏃'} ${mins} นาที! +${xp} XP +${coins} เหรียญ`);
  if(newLevel>oldLevel)setTimeout(()=>showToast(`LEVEL UP! → Lv.${newLevel}`),2400);
  renderHome();
}

function toggleWater(){
  const p=curProfile();const d=getTodayData(p);
  const wasFirst=!dayHasCheckin(d);
  d.water=!d.water;
  if(d.water){
    const mult=p.streak>=7?1.5:p.streak>=3?1.2:1;
    const xp=Math.round(30*mult);
    p.xp=(p.xp||0)+xp;
    if(wasFirst)p.totalCheckins=(p.totalCheckins||0)+1;
    saveProfileData(p);
    showToast(`💧 ดื่มน้ำครบ! +${xp} XP`);
  }else{saveProfileData(p);}
  renderHome();
}

let pendingFood=null;
function renderFood(){
  const p=curProfile();if(!p)return;
  viewDate=viewDate||today();
  const isToday=viewDate===today();
  const d=isToday?getTodayData(p):getViewData(p,viewDate);
  const targets=calcTargets(p);
  const dn=document.getElementById('dnext');
  const btnToday=document.getElementById('btnToday');
  if(dn)dn.style.opacity=isToday?'.25':'1';
  if(btnToday)btnToday.style.display=isToday?'none':'block';
  const dt=new Date(viewDate+'T12:00:00');
  const label=isToday?`วันนี้ · ${dt.toLocaleDateString('th-TH',{day:'numeric',month:'short'})}`:dt.toLocaleDateString('th-TH',{weekday:'short',day:'numeric',month:'long',year:'numeric'});
  document.getElementById('foodDate').textContent=label;
  document.getElementById('kcalTarget').textContent=targets.kcal;
  updateMacroDisplay(d.food,targets);
  renderFoodLog(d.food,!isToday);
}
function updateMacroDisplay(foods,targets){
  const tot={kcal:0,c:0,p:0,f:0};
  foods.forEach(f=>{tot.kcal+=f.kcal;tot.c+=f.c;tot.p+=f.p;tot.f+=f.f;});
  document.getElementById('kcalEaten').textContent=Math.round(tot.kcal);
  const pct=Math.min(188,Math.round(tot.kcal/targets.kcal*188));
  document.getElementById('kcalArc').style.strokeDashoffset=188-pct;
  document.getElementById('carbVal').textContent=Math.round(tot.c)+'g';
  document.getElementById('proteinVal').textContent=Math.round(tot.p)+'g';
  document.getElementById('fatVal').textContent=Math.round(tot.f)+'g';
  document.getElementById('carbBar').style.width=Math.min(100,tot.c/targets.carb*100)+'%';
  document.getElementById('proteinBar').style.width=Math.min(100,tot.p/targets.protein*100)+'%';
  document.getElementById('fatBar').style.width=Math.min(100,tot.f/targets.fat*100)+'%';
}
const mealLabel={breakfast:'เช้า',lunch:'กลางวัน',dinner:'เย็น',snack:'ของว่าง'};
const mealClass={breakfast:'mt-breakfast',lunch:'mt-lunch',dinner:'mt-dinner',snack:'mt-snack'};
function renderFoodLog(foods,readonly){
  const el=document.getElementById('foodLogList');
  if(!foods.length){el.innerHTML=`<div style="text-align:center;color:var(--t2);padding:24px 0;font-size:13px">${readonly?'ไม่มีรายการวันนี้':'ยังไม่มีรายการ'}</div>`;return;}
  const byMeal={};
  foods.forEach((f,i)=>{if(!byMeal[f.meal])byMeal[f.meal]=[];byMeal[f.meal].push({...f,_i:i});});
  el.innerHTML=['breakfast','lunch','dinner','snack'].filter(m=>byMeal[m]).map(m=>`
    <div class="meal-tag ${mealClass[m]}">${mealLabel[m]}</div>
    ${byMeal[m].map(f=>`<div class="food-log-item">
      <div class="fli-info">
        <div class="fli-name">${f.name}${f.qty&&f.qty!==1?` ×${f.qty}`:''}${f.unit?' ('+f.unit+')':''}</div>
        <div class="fli-macros">C:${Math.round(f.c)}g P:${Math.round(f.p)}g F:${Math.round(f.f)}g</div>
      </div>
      <div class="fli-kcal">${Math.round(f.kcal)}</div>
      ${readonly?'':`<button class="fli-edit" onclick="openEditFood(${f._i})">✎</button>
      <button class="fli-del" onclick="deleteFood(${f._i})">×</button>`}
    </div>`).join('')}`).join('');
}
function deleteFood(idx){
  const p=curProfile();const d=getTodayData(p);
  d.food.splice(idx,1);saveProfileData(p);
  const targets=calcTargets(p);updateMacroDisplay(d.food,targets);renderFoodLog(d.food,false);
  renderDeficitCard(p,getTodayData(p));
}
let editFoodIdx=-1;
function openEditFood(idx){
  editFoodIdx=idx;
  const p=curProfile();const d=viewDate===today()?getTodayData(p):getViewData(p,viewDate);
  const f=d.food[idx];
  document.getElementById('efName').value=f.name||'';
  document.getElementById('efKcal').value=Math.round(f.kcal)||0;
  document.getElementById('efCarb').value=Math.round(f.c)||0;
  document.getElementById('efProtein').value=Math.round(f.p)||0;
  document.getElementById('efFat').value=Math.round(f.f)||0;
  document.getElementById('modalEditFood').classList.add('show');
}
function saveEditFood(){
  const name=document.getElementById('efName').value.trim();
  const kcal=parseFloat(document.getElementById('efKcal').value)||0;
  const c=parseFloat(document.getElementById('efCarb').value)||0;
  const pr=parseFloat(document.getElementById('efProtein').value)||0;
  const f2=parseFloat(document.getElementById('efFat').value)||0;
  if(!name||!kcal){showToast('กรอกชื่อและแคลอรี่ด้วย');return;}
  const p=curProfile();const d=viewDate===today()?getTodayData(p):getViewData(p,viewDate);
  d.food[editFoodIdx]={...d.food[editFoodIdx],name,kcal,c,p:pr,f:f2};
  saveProfileData(p);
  const targets=calcTargets(p);updateMacroDisplay(d.food,targets);renderFoodLog(d.food,viewDate!==today());
  if(viewDate===today())renderDeficitCard(p,getTodayData(p));
  closeModal('modalEditFood');
  showToast('แก้ไขแล้ว ✓');
}
function onFoodSearch(q){
  const dr=document.getElementById('srDropdown');
  if(!q.trim()){dr.style.display='none';return;}
  const res=FOOD_DB.filter(f=>f.name.includes(q)||q.split('').some(c=>f.name.includes(c))).slice(0,8);
  if(!res.length){dr.style.display='none';return;}
  dr.style.display='block';
  dr.innerHTML=res.map(f=>`<div class="sr-item" onclick="selectFood(${FOOD_DB.indexOf(f)})">
    <div><div class="sr-name">${f.name}</div><div class="sr-unit">ต่อ 1 ${f.unit}</div></div>
    <div class="sr-kcal">${f.kcal}</div>
  </div>`).join('');
}
function selectFood(idx){
  const f=FOOD_DB[idx];pendingFood=f;
  document.getElementById('srDropdown').style.display='none';
  document.getElementById('foodSearch').value='';
  document.getElementById('modalFoodTitle').textContent='เพิ่ม: '+f.name;
  document.getElementById('srUnitLabel').textContent=f.unit;
  document.getElementById('srQty').value=1;
  updateFoodPreview(f,1);
  document.getElementById('srQty').oninput=function(){updateFoodPreview(f,parseFloat(this.value)||1);};
  document.getElementById('modalFoodMeal').classList.add('show');
}
function updateFoodPreview(f,qty){
  document.getElementById('srPreviewMacros').innerHTML=`
    <div><div style="font-size:15px;font-weight:900;color:var(--lime)">${Math.round(f.kcal*qty)}</div><div style="font-size:10px;color:var(--t2)">kcal</div></div>
    <div><div style="font-size:15px;font-weight:900;color:var(--lime)">${Math.round(f.c*qty)}g</div><div style="font-size:10px;color:var(--t2)">คาร์บ</div></div>
    <div><div style="font-size:15px;font-weight:900;color:var(--blue)">${Math.round(f.p*qty)}g</div><div style="font-size:10px;color:var(--t2)">โปรตีน</div></div>
    <div><div style="font-size:15px;font-weight:900;color:var(--red)">${Math.round(f.f*qty)}g</div><div style="font-size:10px;color:var(--t2)">ไขมัน</div></div>`;
}
function confirmAddFood(){
  const qty=parseFloat(document.getElementById('srQty').value)||1;
  const meal=document.getElementById('srMeal').value;
  const f=pendingFood;
  addFoodEntry({name:f.name,unit:f.unit,qty,meal,kcal:f.kcal*qty,c:f.c*qty,p:f.p*qty,f:f.f*qty});
  closeModal('modalFoodMeal');
}
function openManualFood(){document.getElementById('modalManualFood').classList.add('show');}
function saveManualFood(){
  const name=document.getElementById('mfName').value.trim();
  const kcal=parseFloat(document.getElementById('mfKcal').value)||0;
  const c=parseFloat(document.getElementById('mfCarb').value)||0;
  const p2=parseFloat(document.getElementById('mfProtein').value)||0;
  const f2=parseFloat(document.getElementById('mfFat').value)||0;
  const meal=document.getElementById('mfMeal').value;
  if(!name||!kcal){showToast('กรอกชื่อและแคลอรี่ด้วย');return;}
  addFoodEntry({name,meal,kcal,c,p:p2,f:f2});
  closeModal('modalManualFood');
  ['mfName','mfKcal','mfCarb','mfProtein','mfFat'].forEach(id=>document.getElementById(id).value='');
}
function addFoodEntry(entry){
  const p=curProfile();const d=viewDate===today()?getTodayData(p):getViewData(p,viewDate);
  d.food.push(entry);saveProfileData(p);
  const targets=calcTargets(p);updateMacroDisplay(d.food,targets);renderFoodLog(d.food);
  showToast('บันทึกอาหารแล้ว ✓');
}

function renderProgress(){
  const p=curProfile();if(!p)return;
  const{level}=getLevelFromXP(p.xp||0);
  document.getElementById('statLevel').textContent=level;
  document.getElementById('statStreak').textContent=p.streak||1;
  document.getElementById('statTotalXP').textContent=p.xp||0;
  document.getElementById('statCheckin').textContent=p.totalCheckins||0;
  document.getElementById('statCoins').textContent=(p.coins||0).toLocaleString();
  const wg=document.getElementById('weekGrid');
  const days=['อา','จ','อ','พ','พฤ','ศ','ส'];
  const now=new Date();
  wg.innerHTML=Array.from({length:7},(_,i)=>{
    const d=new Date(now);d.setDate(now.getDate()-6+i);
    const key=d.toISOString().slice(0,10);
    const isToday=key===today();
    const data=p.days&&p.days[key];
    const has=data&&dayHasCheckin(data);
    return`<div class="wday"><div class="wday-lbl">${days[d.getDay()]}</div>
      <div class="wday-dot${has?' done':''}${isToday?' today':''}">${has?'✓':isToday?'·':''}</div>
    </div>`;
  }).join('');
}

function renderProfileTab(){
  const p=curProfile();if(!p)return;
  GH.updateUI();
  const{level}=getLevelFromXP(p.xp||0);
  const targets=calcTargets(p);
  const goalColors={fat_loss:'rgba(255,80,80,.15)',muscle_gain:'rgba(85,153,255,.15)',maintenance:'rgba(68,221,119,.15)'};
  const goalTexts={fat_loss:'ลดไขมัน',muscle_gain:'เพิ่มกล้าม',maintenance:'คงสภาพ'};
  const goalTextColors={fat_loss:'var(--red)',muscle_gain:'var(--blue)',maintenance:'var(--grn)'};
  document.getElementById('profileAvatarBig').textContent=goalEmoji(p.goal);
  document.getElementById('profileName').textContent=p.name;
  const gb=document.getElementById('profileGoalBadge');
  gb.textContent=goalTexts[p.goal];
  gb.style.background=goalColors[p.goal];
  gb.style.color=goalTextColors[p.goal];
  document.getElementById('profileStats').innerHTML=`
    <div class="ps-cell"><div class="ps-val">${p.weight}kg</div><div class="ps-lbl">น้ำหนัก</div></div>
    <div class="ps-cell"><div class="ps-val">${p.height}cm</div><div class="ps-lbl">ส่วนสูง</div></div>
    <div class="ps-cell"><div class="ps-val">${p.age}ปี</div><div class="ps-lbl">อายุ</div></div>`;
  const gtCard=document.getElementById('goalTargetCard');
  const hasGoalTargets=p.targetWeight||p.targetFat||p.timeline;
  if(hasGoalTargets){
    gtCard.style.display='block';
    document.getElementById('goalTargets').innerHTML=`
      ${p.targetWeight?`<div class="gt-cell"><div style="font-size:17px;font-weight:900;color:var(--lime)">${p.targetWeight}kg</div><div style="font-size:9px;color:var(--t2);margin-top:3px;letter-spacing:.5px;text-transform:uppercase">เป้าน้ำหนัก</div></div>`:''}
      ${p.targetFat?`<div class="gt-cell"><div style="font-size:17px;font-weight:900;color:var(--blue)">${p.targetFat}%</div><div style="font-size:9px;color:var(--t2);margin-top:3px;letter-spacing:.5px;text-transform:uppercase">เป้าไขมัน</div></div>`:''}
      ${p.timeline?`<div class="gt-cell"><div style="font-size:17px;font-weight:900;color:var(--grn)">${p.timeline}wk</div><div style="font-size:9px;color:var(--t2);margin-top:3px;letter-spacing:.5px;text-transform:uppercase">ระยะเวลา</div></div>`:''}`;
  }else gtCard.style.display='none';
  document.getElementById('dailyTargets').innerHTML=`
    <div class="targets-grid">
      <div class="tg-cell"><div class="tg-val" style="color:var(--lime)">${targets.kcal}</div><div class="tg-lbl">kcal/วัน</div></div>
      <div class="tg-cell"><div class="tg-val" style="color:var(--blue)">${targets.protein}g</div><div class="tg-lbl">โปรตีน</div></div>
      <div class="tg-cell"><div class="tg-val" style="color:var(--lime)">${targets.carb}g</div><div class="tg-lbl">คาร์บ</div></div>
      <div class="tg-cell"><div class="tg-val" style="color:var(--red)">${targets.fat}g</div><div class="tg-lbl">ไขมัน</div></div>
    </div>`;
}

// ── GITHUB GIST SYNC ─────────────────────────────
const GH={
  token:null,gistId:null,timer:null,_debounce:null,
  init(){
    this.token=_store.get('fq_gh_token');
    this.gistId=_store.get('fq_gh_gist');
    if(this.token&&this.gistId){this.startTimer();this.load();}
    else this.showBanner(true);
    this.updateUI();
  },
  showBanner(show){
    const b=document.getElementById('ghBanner');
    if(b)b.style.display=show?'flex':'none';
  },
  setSyncUI(dot,text){
    const d=document.getElementById('syncDot');
    const t=document.getElementById('syncText');
    if(d)d.className='sync-dot'+(dot?' '+dot:'');
    if(t)t.textContent=text;
  },
  updateUI(){
    const connected=!!(this.token&&this.gistId);
    const cw=document.getElementById('ghConnectWrap');
    const sw=document.getElementById('ghSyncWrap');
    const db=document.getElementById('syncDisconnectBtn');
    if(cw)cw.style.display=connected?'none':'block';
    if(sw)sw.style.display=connected?'block':'none';
    if(db)db.style.display=connected?'inline-block':'none';
    if(!connected)this.setSyncUI('','ไม่ได้เชื่อมต่อ');
    this.showBanner(!connected);
  },
  startTimer(){
    if(this.timer)clearInterval(this.timer);
    this.timer=setInterval(()=>this.save(),30000);
  },
  async save(){
    if(!this.token||!this.gistId)return;
    this.setSyncUI('spin','กำลัง sync...');
    try{
      const data=JSON.stringify({profiles:gp(),current:gcid()});
      const r=await fetch(`https://api.github.com/gists/${this.gistId}`,{
        method:'PATCH',
        headers:{Authorization:`Bearer ${this.token}`,'Content-Type':'application/json'},
        body:JSON.stringify({files:{'fitquest-data.json':{content:data}}})
      });
      if(!r.ok)throw new Error(r.status);
      const now=new Date().toLocaleTimeString('th-TH',{hour:'2-digit',minute:'2-digit',second:'2-digit'});
      this.setSyncUI('on',`Synced ${now}`);
    }catch(e){this.setSyncUI('err',`Error ${e.message}`);}
  },
  async load(){
    if(!this.token||!this.gistId)return false;
    this.setSyncUI('spin','กำลังโหลดจาก GitHub...');
    try{
      const r=await fetch(`https://api.github.com/gists/${this.gistId}`,{
        headers:{Authorization:`Bearer ${this.token}`}
      });
      if(!r.ok)throw new Error(r.status);
      const gist=await r.json();
      const content=gist.files['fitquest-data.json']?.content;
      if(!content)throw new Error('no data');
      const obj=JSON.parse(content);
      if(obj.profiles)sp(obj.profiles);
      if(obj.current)scid(obj.current);
      const now=new Date().toLocaleTimeString('th-TH',{hour:'2-digit',minute:'2-digit',second:'2-digit'});
      this.setSyncUI('on',`Loaded ${now}`);
      this.showBanner(false);
      const id=gcid();
      if(id&&getProfile(id)){const p=getProfile(id);processYesterday(p);checkStreak(p);renderApp();}
      else renderProfileSelect();
      return true;
    }catch(e){this.setSyncUI('err',`Load error ${e.message}`);return false;}
  },
  async connect(token){
    this.setSyncUI('spin','กำลังเชื่อมต่อ...');
    const headers={Authorization:`Bearer ${token}`,'Content-Type':'application/json'};
    const uRes=await fetch('https://api.github.com/user',{headers});
    if(!uRes.ok)throw new Error('Token ไม่ถูกต้อง หรือไม่มีสิทธิ์ gist');
    // ค้นหา Gist เดิมจากชื่อไฟล์
    let gistId=null;
    const listRes=await fetch('https://api.github.com/gists?per_page=100',{headers});
    if(listRes.ok){
      const list=await listRes.json();
      const found=list.find(g=>g.files&&g.files['fitquest-data.json']);
      if(found)gistId=found.id;
    }
    if(!gistId){
      // สร้างใหม่
      const cRes=await fetch('https://api.github.com/gists',{
        method:'POST',headers,
        body:JSON.stringify({description:'FitQuest App Data',public:false,files:{'fitquest-data.json':{content:JSON.stringify({profiles:gp(),current:gcid()})}}})
      });
      if(!cRes.ok)throw new Error('สร้าง Gist ไม่ได้ — ต้องมี scope: gist');
      gistId=(await cRes.json()).id;
    }
    this.token=token;this.gistId=gistId;
    _store.set('fq_gh_token',token);
    _store.set('fq_gh_gist',gistId);
    this.startTimer();
    this.updateUI();
    await this.load();
  },
  disconnect(){
    if(this.timer)clearInterval(this.timer);
    if(this._debounce)clearTimeout(this._debounce);
    this.token=null;this.gistId=null;
    _store.del('fq_gh_token');_store.del('fq_gh_gist');
    this.updateUI();
    showToast('ยกเลิกการเชื่อมต่อแล้ว');
  }
};

function openGitHubSetup(){
  document.getElementById('ghToken').value='';
  document.getElementById('modalGitHub').classList.add('show');
}
async function ghConnect(){
  const token=document.getElementById('ghToken').value.trim();
  if(!token){showToast('กรุณากรอก Token');return;}
  try{
    closeModal('modalGitHub');
    showToast('กำลังเชื่อมต่อ...');
    await GH.connect(token);
    showToast('เชื่อมต่อ GitHub แล้ว ✓');
    renderProfileTab();
  }catch(e){showToast('❌ '+e.message);}
}
async function ghSave(){await GH.save();showToast('Sync แล้ว ✓');}
function ghDisconnect(){GH.disconnect();renderProfileTab();}

function exportData(){
  const data=JSON.stringify({profiles:gp(),current:gcid()});
  if(navigator.clipboard&&navigator.clipboard.writeText){
    navigator.clipboard.writeText(data).then(()=>showToast('คัดลอกแล้ว ✓ เก็บไว้วาง paste ครั้งหน้า')).catch(()=>fallbackCopy(data));
  }else{fallbackCopy(data);}
}
function fallbackCopy(text){
  const ta=document.createElement('textarea');ta.value=text;ta.style.position='fixed';ta.style.opacity='0';document.body.appendChild(ta);ta.select();document.execCommand('copy');document.body.removeChild(ta);showToast('คัดลอกแล้ว ✓');
}
function openImport(){document.getElementById('importJson').value='';document.getElementById('modalImport').classList.add('show');}
function importData(){
  try{
    const raw=document.getElementById('importJson').value.trim();
    const obj=JSON.parse(raw);
    if(!obj.profiles||!Array.isArray(obj.profiles))throw new Error('invalid');
    sp(obj.profiles);
    if(obj.current)scid(obj.current);
    closeModal('modalImport');
    showToast('โหลดข้อมูลแล้ว ✓');
    const id=gcid();
    if(id&&getProfile(id)){const p=getProfile(id);processYesterday(p);checkStreak(p);renderApp();}
    else renderProfileSelect();
  }catch(e){showToast('ข้อมูลไม่ถูกต้อง ลองคัดลอกใหม่');}
}
function switchProfile(){renderProfileSelect();}
function deleteProfile(){
  if(!confirm('ลบโปรไฟล์นี้?'))return;
  const id=gcid();const all=gp().filter(p=>p.id!==id);sp(all);
  _store.del(K.current);renderProfileSelect();
}

function closeModal(id){document.getElementById(id).classList.remove('show');}
document.addEventListener('DOMContentLoaded',()=>{document.querySelectorAll('.modal').forEach(m=>{m.addEventListener('click',e=>{if(e.target===m)m.classList.remove('show');});});});
document.querySelectorAll('.modal').forEach(m=>{m.addEventListener('click',e=>{if(e.target===m)m.classList.remove('show');});});

(function init(){
  GH.init();
  const id=gcid();
  if(id&&getProfile(id)){
    const p=getProfile(id);processYesterday(p);checkStreak(p);renderApp();
  }else renderProfileSelect();
})();
</script>
</body>
</html>
