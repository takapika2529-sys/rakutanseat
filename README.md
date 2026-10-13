# raku```html
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>楽単シート for web</title>
<style>
:root{--bg:#f6f7fb;--card:#fff;--text:#1d2433;--sub:#667085;--pri:#4f46e5;--priT:#fff;--ok:#16a34a;--ng:#dc2626;--bd:#e3e6ee;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#12141c;--card:#1b1f2b;--text:#e8eaf2;--sub:#98a2b3;--pri:#818cf8;--priT:#12141c;--bd:#2c3242}}
:root[data-theme="dark"]{--bg:#12141c;--card:#1b1f2b;--text:#e8eaf2;--sub:#98a2b3;--pri:#818cf8;--priT:#12141c;--bd:#2c3242}
*{box-sizing:border-box}
html,body{margin:0;min-height:100%}
body{background:var(--bg);color:var(--text);font-family:system-ui,-apple-system,"Hiragino Sans","Noto Sans JP",sans-serif;line-height:1.5}
.wrap{width:100%;max-width:560px;margin:0 auto;padding:16px;container-type:inline-size;container-name:main}
h1{font-size:20px;margin:4px 0 12px}
.card{background:var(--card);border:1px solid var(--bd);border-radius:16px;padding:20px}
.fc{min-height:200px;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;cursor:pointer;user-select:none}
.fc .w{font-size:34px;font-weight:700;word-break:break-word}
.fc .m{font-size:22px}
.hint{color:var(--sub);font-size:13px;margin-top:10px}
.row{display:flex;gap:8px;margin-top:12px}
.btn{flex:1;padding:12px;border:1px solid var(--bd);background:var(--card);color:var(--text);border-radius:10px;font-size:15px;cursor:pointer}
.btn.pri{background:var(--pri);color:var(--priT);border-color:var(--pri);font-weight:600}
.btn.ok{background:var(--ok);color:#fff;border-color:var(--ok)}
.btn.ng{background:var(--ng);color:#fff;border-color:var(--ng)}
.opt.right{border-color:var(--ok);background:color-mix(in srgb,var(--ok) 15%,var(--card))}
.opt.wrong{border-color:var(--ng);background:color-mix(in srgb,var(--ng) 15%,var(--card))}
.opts{display:grid;gap:8px;margin-top:14px}
.opt{text-align:left}
.q{font-size:30px;font-weight:700;text-align:center;margin:8px 0}
.box{font-size:12px;color:var(--sub)}
input{width:100%;padding:11px;border:1px solid var(--bd);border-radius:10px;background:var(--bg);color:var(--text);font-size:15px;margin-top:8px}
ul{list-style:none;padding:0;margin:14px 0 0}
li{display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid var(--bd)}
li div{flex:1;min-width:0}
li b{display:block}
li span{color:var(--sub);font-size:14px}
.del{background:none;border:none;color:var(--ng);font-size:13px;cursor:pointer}
.bar{display:flex;align-items:center;gap:10px;margin:10px 0;font-size:14px}
.bar i{display:block;height:14px;border-radius:7px;background:var(--pri);min-width:2px}
.bar .t{flex:1;background:var(--bd);border-radius:7px;height:14px}
.bar .l{width:92px;color:var(--sub)}
.big{font-size:36px;font-weight:700}
.res,.dex{display:grid;grid-template-columns:repeat(auto-fill,minmax(105px,1fr));gap:8px;margin-top:12px}
.g{border:2px solid var(--bd);border-radius:12px;padding:8px;font-size:13px;display:flex;flex-direction:column;word-break:break-word}
.g b{font-size:15px}.g span{color:var(--sub);font-size:12px}
.g i{font-style:normal;font-size:11px;font-weight:700;margin-top:2px}
.g.N{border-color:#94a3b8}.g.R{border-color:#3b82f6}
.g.S{border-color:#f59e0b;background:color-mix(in srgb,#f59e0b 14%,var(--card))}
.chips{display:flex;flex-wrap:wrap;gap:6px;margin-top:10px}
.chip{padding:8px 12px;border:1px solid var(--bd);background:var(--bg);color:var(--sub);border-radius:20px;font-size:13px;cursor:pointer}
textarea{font-family:inherit;resize:vertical}
details summary{cursor:pointer;padding:6px 0}
.shop{display:flex;gap:10px;align-items:center;padding:12px 0;border-bottom:1px solid var(--bd)}
.shop .si{flex:1;min-width:0}
.chip.pre{border-color:#f59e0b}
.ttl{position:fixed;inset:0;z-index:10;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:24px;padding-top:calc(24px + env(safe-area-inset-top,0px));padding-bottom:calc(24px + env(safe-area-inset-bottom,0px));background:linear-gradient(160deg,var(--bg),color-mix(in srgb,var(--pri) 28%,var(--bg)))}
.ttl .logo{font-size:72px;animation:bob 2.4s ease-in-out infinite}
.ttl h2{font-size:clamp(44px,10vw,60px);line-height:1.15;margin:8px 0 0;letter-spacing:.06em;font-weight:850}
.ttl .sub{display:none}
.ttl .tstat{margin-top:30px;font-size:19px;background:var(--card);border:1px solid var(--bd);border-radius:22px;padding:10px 20px}
.ttl .btn{flex:none;width:100%;max-width:320px;margin-top:30px;padding:19px;font-size:22px;border-radius:14px}
@keyframes bob{50%{transform:translateY(-10px)}}
@media (prefers-reduced-motion:reduce){.ttl .logo{animation:none}}
.stile{display:grid;grid-template-columns:repeat(2,1fr);gap:8px;margin-top:10px}
.stile div{background:var(--bg);border-radius:10px;padding:10px;text-align:center}
.stile b{font-size:22px;display:block}
.stile span{font-size:12px;color:var(--sub)}
.chip.on{background:var(--pri);color:var(--priT);border-color:var(--pri);font-weight:600}
.hud{display:flex;align-items:center;gap:10px;margin-bottom:14px;font-size:14px}
.hud .lv{background:var(--pri);color:var(--priT);border-radius:10px;padding:4px 10px;font-weight:700}
.hud .xp{flex:1}
.hud .t{height:10px;background:var(--bd);border-radius:5px;overflow:hidden}
.hud .t i{display:block;height:100%;background:var(--pri);transition:width .3s}
.hud small{color:var(--sub);font-size:11px}
.toast{margin-top:12px;padding:10px;border-radius:10px;background:color-mix(in srgb,var(--ok) 15%,var(--card));text-align:center;font-weight:600;font-size:14px}
.chk{display:flex;gap:10px;align-items:center}
.chk input{width:auto;margin:0}
textarea,select{width:100%;padding:11px;border:1px solid var(--bd);border-radius:10px;background:var(--bg);color:var(--text);font-size:15px;margin-top:10px}
.top{display:flex;align-items:center;gap:10px;margin:4px 0 12px}
.top h1{margin:0}
.menu{flex:none;width:40px;height:40px;border:1px solid var(--bd);background:var(--card);color:var(--text);border-radius:10px;font-size:20px;cursor:pointer;line-height:1;padding:0}
#sb{position:fixed;top:0;left:0;bottom:0;width:240px;max-width:80vw;z-index:6;background:var(--card);border-right:1px solid var(--bd);display:flex;flex-direction:column;padding:calc(16px + env(safe-area-inset-top,0px)) 12px calc(16px + env(safe-area-inset-bottom,0px));transform:translateX(-102%);transition:transform .25s ease;overflow-y:auto}
#sb.open{transform:none;box-shadow:4px 0 24px rgba(0,0,0,.25)}
#ov{position:fixed;inset:0;z-index:5;background:rgba(0,0,0,.4);opacity:0;pointer-events:none;transition:opacity .25s}
#ov.open{opacity:1;pointer-events:auto}
.sbt{font-size:18px;font-weight:700;padding:4px 8px 12px}
#nav{display:flex;flex-direction:column;gap:4px}
#nav button{display:flex;align-items:center;gap:10px;width:100%;padding:12px;border:none;background:none;color:var(--text);border-radius:10px;font-size:15px;text-align:left;cursor:pointer}
#nav button.on{background:var(--pri);color:var(--priT);font-weight:600}
#sbf{margin-top:auto;padding:12px 8px 0;font-size:12px;color:var(--sub)}
@media (min-width:600px) and (max-width:899px){.wrap{max-width:900px;padding:22px}}
@media (min-width:900px){#sb{transform:none;box-shadow:none}#ov{display:none}.menu{display:none}body{padding-left:240px}.wrap{max-width:1080px;padding:24px}}
@media (prefers-reduced-motion:reduce){#sb,#ov{transition:none}}

/* Home dashboard, separate from the sidebar navigation */
.home-head{display:flex;align-items:center;justify-content:space-between;gap:12px;margin:8px 0 16px}
.home-head h2{font-size:28px;line-height:1.2;margin:0;font-weight:850;letter-spacing:.01em}
.home-stats{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px;margin:12px 0}
.home-stat{background:var(--bg);border:1px solid var(--bd);border-radius:13px;padding:12px 8px;text-align:center;min-width:0}
.home-stat .hs-icon{display:block;margin-bottom:4px;color:var(--pri)}
.home-stat b{display:block;font-size:23px;line-height:1.2}
.home-stat span{display:block;color:var(--sub);font-size:11px;margin-top:4px}
.calendar-card{padding:16px}
.cal-top{display:flex;align-items:center;justify-content:space-between;gap:8px;margin-bottom:12px}
.cal-top strong{font-size:17px}
.cal-nav{display:flex;gap:6px}
.cal-nav button{width:36px;height:36px;border:1px solid var(--bd);border-radius:9px;background:var(--card);color:var(--text);font-size:18px;cursor:pointer}
.cal-grid{display:grid;grid-template-columns:repeat(7,minmax(0,1fr));gap:5px;text-align:center}
.cal-week{font-size:11px;color:var(--sub);padding:4px 0}
.cal-day{min-height:36px;display:flex;align-items:center;justify-content:center;border-radius:10px;font-size:13px;position:relative}
.cal-day.empty{visibility:hidden}
.cal-day.visited{background:color-mix(in srgb,var(--pri) 13%,var(--card));font-weight:700;border:1px solid color-mix(in srgb,var(--pri) 45%,var(--bd))}
.cal-day.studied:after{content:"";position:absolute;bottom:3px;width:4px;height:4px;border-radius:50%;background:var(--ok)}
.cal-legend{display:flex;gap:12px;flex-wrap:wrap;color:var(--sub);font-size:11px;margin-top:10px}
.cal-dot{display:inline-block;width:8px;height:8px;border-radius:50%;background:var(--pri);margin-right:5px}
.home-section-title{font-size:17px;font-weight:750;margin:20px 0 10px;display:flex;align-items:center;gap:8px}
.home-actions{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}
.home-action{display:flex;align-items:center;gap:10px;text-align:left;padding:14px 12px;border:1px solid var(--bd);border-radius:14px;background:var(--card);color:var(--text);min-width:0;min-height:68px;cursor:pointer;transition:transform .15s,border-color .15s}
.home-action:active{transform:scale(.98)}
.home-action .ha-icon{width:40px;height:40px;display:flex;align-items:center;justify-content:center;border-radius:12px;background:color-mix(in srgb,var(--pri) 12%,var(--card));color:var(--pri);flex:none}
.home-action b{display:block;font-size:14px;line-height:1.3;overflow-wrap:anywhere}
.home-action.primary{border-color:color-mix(in srgb,var(--pri) 55%,var(--bd));background:color-mix(in srgb,var(--pri) 5%,var(--card))}
.home-shortcut{flex:none;width:40px;height:40px;display:flex;align-items:center;justify-content:center;border:1px solid var(--bd);border-radius:10px;background:var(--card);color:var(--text);cursor:pointer}
@container main (min-width:560px){
 .home-actions{grid-template-columns:repeat(3,minmax(0,1fr));gap:12px}
 .home-action{flex-direction:column;justify-content:center;text-align:center;gap:8px;min-height:100px;padding:12px 8px}
 .home-action .ha-icon{width:44px;height:44px}
 .home-action b{font-size:14px}
 .home-stats{gap:10px}
 .home-stat{padding:14px 8px}
 .calendar-card{padding:20px}
 .cal-grid{gap:7px}
 .cal-day{min-height:40px}
}
@container main (min-width:640px){
 #app.home-dashboard{display:grid;grid-template-columns:minmax(0,1.2fr) minmax(220px,.8fr);column-gap:18px;align-items:start}
 #app.home-dashboard>.home-head,#app.home-dashboard>.home-section-title,#app.home-dashboard>.home-actions{grid-column:1/-1}
 #app.home-dashboard>.home-head{grid-row:1}
 #app.home-dashboard>.calendar-card{grid-column:1;grid-row:2}
 #app.home-dashboard>.home-stats{grid-column:2;grid-row:2;grid-template-columns:minmax(0,1fr);align-content:start;margin:0}
 #app.home-dashboard>.home-section-title{grid-row:3;margin-top:22px}
 #app.home-dashboard>.home-actions{grid-row:4}
 .home-stat{display:grid;grid-template-columns:30px minmax(0,1fr);grid-template-rows:auto auto;align-items:center;column-gap:8px;text-align:left;padding:14px 12px}
 .home-stat .hs-icon{grid-row:1/3;margin:0;align-self:center}
 .home-stat b{font-size:24px}
 .home-stat span:last-child{margin:3px 0 0}
}
@container main (min-width:880px){#app.home-dashboard>.home-actions{grid-template-columns:repeat(4,minmax(0,1fr))}}
@media(max-width:420px){.home-head h2{font-size:25px}.home-stats{gap:5px}.home-stat{padding:10px 4px}.home-stat b{font-size:20px}.home-action{gap:8px;padding:11px 8px;min-height:62px}.home-action .ha-icon{width:34px;height:34px}.cal-grid{gap:2px}.cal-day{min-height:31px;font-size:12px;border-radius:7px}.cal-legend{gap:8px}}
@media(orientation:landscape) and (max-height:520px){.wrap{max-width:900px;padding:10px 16px}.top{margin-bottom:6px}.hud{margin-bottom:8px}.calendar-card{padding:10px}.cal-grid{gap:2px}.cal-day{min-height:26px}.cal-week{padding:1px 0}.cal-legend{margin-top:4px}.home-head{margin:4px 0 8px}.home-section-title{margin-top:12px}.home-actions{gap:7px}.home-action{min-height:58px;padding:8px}.home-action .ha-icon{width:32px;height:32px}}


.sw{position:relative;display:block;flex:none;width:44px;height:26px}
.sw input{position:absolute;inset:0;width:100%;height:100%;margin:0;padding:0;border:none;opacity:0;cursor:pointer;z-index:1}
.sw i{position:absolute;inset:0;display:block;background:var(--bd);border-radius:13px;transition:background .2s}
.sw i::after{content:"";position:absolute;top:3px;left:3px;width:20px;height:20px;border-radius:50%;background:#fff;transition:transform .2s;box-shadow:0 1px 3px rgba(0,0,0,.3)}
.sw input:checked+i{background:var(--pri)}
.sw input:checked+i::after{transform:translateX(18px)}
li.off div{opacity:.45}

.listtools{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:10px}
.listtools input,.listtools select{margin:0;min-width:0}
.challengeQ{font-size:28px;font-weight:700;text-align:center;margin:16px 0}
.timerbar{height:12px;background:var(--bd);border-radius:8px;overflow:hidden;margin:8px 0}
.timerbar i{display:block;height:100%;background:var(--pri)}
.mission{padding:10px 0;border-bottom:1px solid var(--bd)}
.mission:last-child{border-bottom:0}
.achievement-list{display:grid;grid-template-columns:1fr;gap:8px;margin-top:10px}
.achievement-row{display:grid;grid-template-columns:28px 1fr;gap:8px;align-items:start;padding:11px;border:1px solid var(--bd);border-radius:12px;background:var(--card)}
.achievement-row.unlocked{border-color:color-mix(in srgb,var(--ok) 60%,var(--bd));background:color-mix(in srgb,var(--ok) 6%,var(--card))}
.achievement-icon{font-size:20px;line-height:1.3;text-align:center}
.achievement-title{font-weight:700}
.achievement-desc{color:var(--sub);font-size:13px;margin-top:3px}
.achievement-reward{font-size:12px;font-weight:600;margin-top:6px}
.achToast{position:fixed;left:50%;bottom:calc(18px + env(safe-area-inset-bottom,0px));transform:translate(-50%,18px);z-index:20;width:min(92vw,480px);padding:12px 16px;border:1px solid var(--bd);border-radius:13px;background:var(--card);color:var(--text);box-shadow:0 8px 30px rgba(0,0,0,.2);font-size:14px;text-align:center;font-weight:650;opacity:0;pointer-events:none;transition:opacity .2s,transform .2s}
.achToast.show{opacity:1;transform:translate(-50%,0)}

.line-icon{display:inline-block;flex:none;width:var(--icon-size,1.2em);height:var(--icon-size,1.2em);vertical-align:-.22em;fill:none;stroke:currentColor;stroke-width:1.8;stroke-linecap:round;stroke-linejoin:round}
.nav-icon{width:20px;height:20px;opacity:.92}
.coin-mark{color:#c58a12;width:1.15em;height:1.15em}
.inline-icon{margin:0 .14em}
.icon-label{display:inline-flex;align-items:center;justify-content:center;gap:6px}
.menu .line-icon{width:22px;height:22px;vertical-align:middle}
.achievement-icon .line-icon{width:22px;height:22px}
#nav button .nav-icon{transition:transform .15s ease}
#nav button:hover .nav-icon{transform:translateX(2px)}
@media (prefers-reduced-motion:reduce){#nav button .nav-icon{transition:none}}


/* Shop UI and purchasable themes */
:root[data-theme="ocean"]{--bg:#eff8ff;--card:#ffffff;--text:#17324a;--sub:#527188;--pri:#1677b9;--priT:#ffffff;--ok:#14805e;--ng:#c33d54;--bd:#d6e7f3}
:root[data-theme="forest"]{--bg:#f1f7f0;--card:#ffffff;--text:#1d382b;--sub:#5e7869;--pri:#2e7d50;--priT:#ffffff;--ok:#26784a;--ng:#bd4040;--bd:#d9e8da}
:root[data-theme="violet"]{--bg:#f7f3ff;--card:#ffffff;--text:#30254a;--sub:#78698e;--pri:#8055c7;--priT:#ffffff;--ok:#24845b;--ng:#c23b61;--bd:#e5daf5}
:root[data-theme="sunset"]{--bg:#fff6ef;--card:#ffffff;--text:#472b25;--sub:#8a675e;--pri:#d45f3b;--priT:#ffffff;--ok:#27825d;--ng:#bd3c45;--bd:#f0ddd3}
:root[data-theme="rose"]{--bg:#fff2f6;--card:#ffffff;--text:#4b2535;--sub:#936a7a;--pri:#c44579;--priT:#ffffff;--ok:#25825f;--ng:#b82d52;--bd:#f0d6e1}
:root[data-theme="aurora"]{--bg:#101b2d;--card:#17263b;--text:#e6f2ff;--sub:#a2b7d1;--pri:#61a7e8;--priT:#0b1725;--ok:#51c49b;--ng:#ff7b89;--bd:#2a3c55}
:root[data-theme="paper"]{--bg:#f4f0e6;--card:#fffcf4;--text:#35342d;--sub:#747166;--pri:#796b4b;--priT:#fffdf6;--ok:#3e8258;--ng:#b8463b;--bd:#ddd6c4}
.shop-tabs{display:flex;gap:6px;overflow-x:auto;padding:2px 0 8px;margin:0 0 8px;scrollbar-width:thin}
.shop-tabs .chip{white-space:nowrap;flex:none}
.shop-balance{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:10px;padding:10px 12px;border:1px solid var(--bd);border-radius:12px;background:var(--bg)}
.shop-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px;margin-top:12px}
.shop-product{min-width:0;border:1px solid var(--bd);border-radius:14px;padding:13px;background:var(--card);display:flex;flex-direction:column;gap:8px}
.shop-product .sp-icon{width:40px;height:40px;border-radius:12px;background:color-mix(in srgb,var(--pri) 12%,var(--card));display:flex;align-items:center;justify-content:center;color:var(--pri)}
.shop-product h3{font-size:15px;margin:0;line-height:1.35}
.shop-product p{font-size:12px;color:var(--sub);margin:0;min-height:34px}
.shop-product .sp-price{font-weight:750;font-size:14px;margin-top:auto}
.shop-product .btn{width:100%;flex:none;padding:10px 8px;font-size:13px}
.shop-product .owned-label{font-size:12px;color:var(--ok);font-weight:700}
.shop-note{font-size:12px;color:var(--sub);margin-top:8px}
.shop-section-head{display:flex;align-items:center;justify-content:space-between;gap:8px;margin:4px 0 8px}
.inventory-count{font-weight:750;font-variant-numeric:tabular-nums}
.theme-swatch{height:8px;border-radius:99px;background:linear-gradient(90deg,var(--sw1),var(--sw2));margin:2px 0}
@media(max-width:380px){.shop-grid{grid-template-columns:1fr}.shop-product p{min-height:0}}
@media (min-width:700px){.shop-grid{grid-template-columns:repeat(3,minmax(0,1fr))}}


.analytics-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px;margin-top:12px}.analytics-tile{border:1px solid var(--bd);border-radius:12px;padding:12px}.analytics-tile b{display:block;font-size:23px}.analytics-tile span{font-size:12px;color:var(--sub)}.settings-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}.settings-grid label{display:flex;flex-direction:column;gap:6px;font-size:13px}.settings-grid select{width:100%;min-width:0}.mode-row{display:flex;gap:8px;flex-wrap:wrap;margin-top:10px}
@media(min-width:700px){.analytics-grid{grid-template-columns:repeat(4,minmax(0,1fr))}.settings-grid{grid-template-columns:repeat(3,minmax(0,1fr))}}
</style>
</head>
<body>
<div class="ttl" id="ttl"></div>
<aside id="sb" aria-label="メニュー"><div class="sbt">メニュー</div><nav id="nav"></nav><div id="sbf"></div></aside>
<div id="ov" onclick="closeSb()"></div>
<div id="achToast" class="achToast" role="status" aria-live="polite"></div>
<div class="wrap">
<div class="top"><button class="menu" onclick="toggleSb()" aria-label="メニューを開く"><svg class="line-icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M4 6h16M4 12h16M4 18h16"/></svg></button><h1 style="flex:1">楽単シート <small style="font-size:13px;color:var(--sub);font-weight:400">for web</small></h1><button class="home-shortcut" onclick="setTab('home')" aria-label="ホームへ戻る" title="ホーム"><svg class="line-icon" viewBox="0 0 24 24" aria-hidden="true"><path d="m3 10 9-7 9 7M5 9v12h14V9M9 21v-7h6v7"/></svg></button></div>
<div class="hud" id="hud"></div>
<div id="app"></div>
</div>
<script>
const K="vocab_v2";
const UR=[[["settler","入植者","名詞","N","","1.1"],["incredible","信じられない","形容詞","R","","1.1"],["extinct","絶滅した","形容詞","N","","1.1"],["claw","かぎづめ","名詞","N","","1.1"],["ratite","平胸類の","形容詞","N","","1.1"],["wing","翼","名詞","N","","1.1"],["flightless","飛べない","形容詞","R","","1.1"],["kiwi","キーウィ (鳥)","名詞","N","","1.1"],["emu","エミュー(鳥)","名詞","N","","1.1"],["be in for~","(ショックなど)を受けることになる","熟語","R","","1.1"],["in contrast","対照的に","熟語","R","","1.1"],["arrival","到着","名詞","N","","1.2"],["Polynesia","ポリネシア","名詞","R","","1.2"],["carnivore","肉食動物","名詞","R","","1.2"],["predator","捕食動物","名詞","R","","1.2"],["herbivore","草食動物","名詞","R","","1.2"],["variety","いろいろ、多様","名詞","N","a (wide) variety of~･･･いろいろな〜","1.2"],["dune","砂丘","名詞","N","","1.2"],["shrubland","低木地","名詞","R","","1.2"],["berry","ベリー (果実)","名詞","N","","1.2"],["make use of","･･･を利用する、活用する","熟語","R","","1.2"],["hunt","･･･を狩る","動詞","N","","1.3"],["incubate","･･･を孵化する","動詞","R","","1.3"],["forage","食物を探す","動詞","N","","1.3"],["underground","地下の","形容詞","S","","1.3"],["extinction","絶滅","名詞","R","","1.3,3.1"],["lay","･･･を置く、･･･を産む","動詞","N","過去・過去分詞:laid","1.3"],["breeding","繁殖","名詞","R","breeding season･･･繁殖期","1.3"],["chick","ひな","名詞","N","","1.3"],["rapid","速い、急な、急速な","形容詞","N","","1.3"],["come across","･･･に出くわす","熟語","R","","1.3"],["for good","永遠に","熟語","R","","1.3"]],[["advent","出現、到来","名詞","N","","2.1"],["streaming","(インターネット上の) ストリーミング","名詞","R","","2.1"],["attract","･･･を引き付ける","動詞","N","","2.1"],["spectator","観客","名詞","R","","2.1"],["arena","競技場","名詞","N","","2.1"],["gamer","ゲーマー","名詞","N","","2.1"],["compete","競争する、競い合う","動詞","N","","2.1"],["network","ネットワーク","名詞","N","","2.1"],["content","内容、コンテンツ","名詞","N","","2.1"],["limit","限界、制限","名詞","N","the sky is the limit ･･･「空が限界である」 = 限界がない","2.1"],["competitor","参加者,競技者","名詞","R","","2.1"],["electronic","電子の","形容詞","R","","2.1"],["involve","･･･を含む","動詞","N","","2.1"],["highly","非常に、大いに","副詞","N","","2.1"],["competitive","競争の、競争心の強い","形容詞","S","","2.1"],["strictly","厳密に","副詞","R","","2.1"],["regulate","･･･を規制する","動詞","R","","2.1"],["obvious","明白な","形容詞","N","","2.2"],["teamwork","チームワーク","名詞","R","","2.2"],["normally","通常は","副詞","R","","2.2"],["isolate","･･･を孤立させる","動詞","N","","2.2"],["socialize","社交的に交際する","動詞","R","","2.2"],["peer","仲間","名詞","N","","2.2"],["immerse","･･･を浸す","動詞","N","","2.2"],["growth","増加","名詞","N","","2.2"],["scholarship","奨学金","名詞","S","","2.2"],["engineering","工学(技術)","名詞","S","","2.2"],["management","経営,運営,管理","名詞","R","","2.2"],["designer","デザイナー、設計者","名詞","R","","2.2"],["go into doing","･･･するために費やされる","熟語","R","","2.2"],["absolutely","(全く) そのとおり","副詞","R","","2.3"],["traditional","伝統的な、昔ながらの","形容詞","S","","2.3"],["require","･･･を必要とする","動詞","N","","2.3"],["discipline","訓練,規律","名詞","R","","2.3"],["collaboration","協力,共同制作","名詞","S","","2.3"],["strategy","戦略、戦術","名詞","R","","2.3"],["defeat","･･･を打ち負かす","動詞","N","","2.3"],["viewership","視聴者数","名詞","R","","2.3"],["component","部分","名詞","R","","2.3"],["characteristic","特徴","名詞","S","","2.3"],["be regarded as ...","･･･とみなされる","熟語","S","","2.3"]],[["editorial","(新聞などの) 社説","名詞","R","","3.1"],["climate","気候","名詞","N","","3.1"],["extreme","極端な","形容詞","N","","3.1"],["drought","干ばつ","名詞","N","","3.1"],["mass","大量の、大規模な","形容詞","N","","3.1"],["catastrophe","大災害","名詞","S","","3.1"],["helpless","無力な、どうすることもできない","形容詞","R","","3.1"],["diet","(日常的な) 食べ物、常食","名詞","N","","3.1"],["total","全体の、全部の、総計の","形容詞","N","","3.1"],["greenhouse gas","温室効果ガス","名詞","S","","3.1"],["emission","排出","名詞","R","","3.1"],["transportation","交通機関","名詞","S","","3.1"],["combined","合計の、合算した","形容詞","R","","3.1"],["carbon","炭素","名詞","N","","3.1"],["dramatically","劇的に","副詞","S","","3.1"],["according to~","〜によれば","熟語","R","","3.1"],["account for~","〜を占める、~を構成する","熟語","R","","3.1"],["animal welfare","動物福祉","名詞","S","","3.2"],["behind~","~の背後に、~の後ろの","前置詞","N","","3.2"],["tiny","とても小さな","形容詞","N","","3.2"],["room","余地","名詞","N","","3.2"],["overcrowding","過密(状態)","名詞","S","","3.2"],["factory-farmed","工場方式で飼育された","形容詞","S","","3.2"],["dose","(1回分の)服用量","名詞","N","","3.2"],["antibiotic","抗生物質","名詞","R","通例複数形 antibioticsで","3.2"],["antibiotic-resistant","耐抗生物質の","形容詞","S","","3.2"],["bacteria","バクテリア、細菌","名詞","R","","3.2"],["infection","感染(症)","名詞","R","","3.2,4.1"],["consumption","消費 [摂取] 量","名詞","S","","3.3"],["affect","~に影響を与える","動詞","N","","3.3"],["illness","病気","名詞","N","","3.3"],["cancer","癌","名詞","N","","3.3"],["consume","~を消費 [摂取] する","動詞","N","","3.3"],["processed","加工された","形容詞","R","","3.3"],["given~","~を考慮すれば","熟語","R","","3.3"],["as a whole","全体として","熟語","R","","3.3"],["switch to~","~へ切り替える、転換する","熟語","R","","3.3"],["central","中心の","形容詞","N","","3.4"],["altogether","完全に","副詞","R","","3.4"],["misguided","見当違いの","形容詞","R","","3.4"],["livestock","家畜(類)","名詞","R","","3.4"],["contribute","(･･･の)一因となる","動詞","R","","3.4"],["completely","完全に","副詞","R","","3.4"],["agriculture","農業","名詞","S","","3.4"],["intensively","集中的に","副詞","S","","3.4"],["fertilizer","肥料","名詞","R","","3.4"],["agricultural","農業の","形容詞","S","","3.4"],["irrigation","灌漑","名詞","R","","3.4"],["take issue with~","〜に異議を唱える、~に反対する","熟語","S","","3.4"],["be true of~","〜にも当てはまる","熟語","R","","3.4"],["in short","要するに、手短に言えば","熟語","R","","3.4"],["explosion","爆発的増加","名詞","R","","3.5"],["organic","有機栽培 [肥料] による","形容詞","N","","3.5"],["free-range","放し飼いの","形容詞","R","","3.5"],["obviously","明らかに","副詞","R","","3.5"],["non-intensive","非集約的な","形容詞","S","","3.5"],["neither","･･･もまた〜しない","副詞","N","","3.5"],["evolve","進化する","動詞","N","","3.5"],["omnivore","雑食(性)動物","名詞","R","","3.5"],["nutrition","栄養(になるもの)","名詞","R","","3.5"],["flexitarian","フレキシタリアン (柔軟な菜食主義者) ／ フレキタリアンの","名詞/形容詞","S","","3.5"],["realistic","現実的な、実際的な","形容詞","R","","3.5"],["vegetarianism","菜食主義","名詞","S","","3.5"],["overall","全体の","形容詞","N","","3.5"],["promote","~を促進する","動詞","N","","3.5"],["long-term","長期にわたる","形容詞","R","","3.5"],["refer to~","〜に言及する","熟語","R","","3.5"]],[["founding father","創始者","名詞","S","","4.1"],["Scottish","スコットランド(人)の","形容詞","R","","4.1"],["discovery","発見","名詞","R","","4.1"],["penicillin","ペニシリン (抗生物質の一種)","名詞","R","","4.1"],["revolutionize","･･･に革命をもたらす","動詞","S","","4.1"],["cure","･･･を治療する","動詞","N","","4.1"],["infect","･･･を感染させる","動詞","N","","4.1"],["large-scale","大規模な","形容詞","S","","4.1"],["humble","身分が低い、恵まれない","形容詞","N","humble beginnings=庶民の出、恵まれない生い立ち","4.1"],["desire","願望","名詞","N","","4.1"],["wound","傷 ／ ~を負傷させる","名詞/動詞","N","","4.1,4.3"],["injury","負傷","名詞","N","","4.1"],["by accident","偶然に","熟語","R","","4.1"],["break out","起こる、勃発する、発生する","熟語","R","","4.1"],["not~but...","〜ではなく･･･","熟語","R","","4.1"],["accidental","偶然の","形容詞","R","","4.2"],["lucky break","けがの功名","熟語","R","","4.2"],["laboratory","研究所","名詞","R","","4.2"],["Petri dish","ペトリ皿、シャーレ","名詞","R","","4.2"],["cultivate","･･･を培養する","動詞","R","","4.2"],["contaminated","汚染された","形容詞","S","","4.2"],["mold","かび","名詞","N","","4.2"],["penicillium notatum","ペニシリウム・ノタツム (アオカビ)","名詞","S","","4.2"],["obtain","･･･を得る","動詞","N","","4.2"],["bacteria-killing","バクテリア [細菌] を殺す","形容詞","S","","4.2"],["ingredient","材料、成分、要素","名詞","R","","4.2"],["convince","~を納得させる、確信させる","動詞","R","be convinced (that)~=~と確信している","4.2"],["skin","皮膚","名詞","N","","4.2"],["pneumonia","肺炎","名詞","R","","4.2"],["deadly","致命的な","形容詞","N","","4.2"],["respiratory","呼吸(器)の","形容詞","S","","4.2"],["available","利用できる、入手できる","形容詞","R","","4.2"],["retirement","退職","名詞","R","","4.3"],["achievement","功績","名詞","S","","4.3"],["substance","物質","名詞","R","","4.3"],["microorganism","微生物","名詞","S","","4.3"],["antibiosis","抗生作用","名詞","R","","4.3"],["bacterial","バクテリア [細菌] の","形容詞","R","","4.3"],["multiply","増殖する","動詞","R","","4.3"],["Egyptian","エジプト人","名詞","R","","4.3"],["moldy","かびの生えた","形容詞","N","","4.3"],["in time","間に合うように","熟語","R","in time for~=~ に間に合うように","4.3"]],[["rise","台頭、興隆、隆盛","名詞","N","on the rise･･･増加中で、上昇中で","5.1"],["exhausted","疲れ果てた","形容詞","R","","5.1"],["stress","(精神的)緊張、ストレス","名詞","N","","5.1"],["increasingly","ますます","副詞","S","","5.1"],["trend","傾向、動向","名詞","N","","5.1"],["encourage","~を励ます、勇気づける","動詞","R","encourage O to do~･･･ を~するよう励ます、奨励する","5.1"],["maturity","(身体・精神の) 成熟","名詞","R","","5.1"],["despite","~にも関わらず (=in","前置詞","N","spite of~)","5.1"],["catch on","流行する","熟語","R","","5.1"],["expectation","期待、予期、見込み","名詞","S","","5.2"],["applicant","志願者,応募者","名詞","R","","5.2"],["likewise","同様に","副詞","R","","5.2"],["abound","たくさんある、豊富である","動詞","N","","5.2"],["noticeably","際立って","副詞","R","","5.2"],["elite","えり抜きの、エリートの","形容詞","N","the elite･･･エリート","5.2"],["youngster","若者","名詞","R","","5.2"],["sun","~を日光に当てる","動詞","N","sun oneself･･･ 日なたぼっこをする","5.2"],["champion","擁護者","名詞","R","","5.2"],["renewed","新たな、よみがえった","形容詞","N","","5.2"],["refreshment","元気回復、気分爽快","名詞","S","","5.2"],["demotivate","･･･のやる気をなくさせる","動詞","R","","5.2"],["full-time","フルタイムで","副詞","R","","5.2"],["broaden","~を広くする、広げる","動詞","N","","5.2"],["horizon","地平線、[通例~s] 視野、範囲","名詞","N","broaden one's horizons･･･~の視野を広げる","5.2"],["step-up","増加,向上","名詞","N","","5.2"],["build... into ~","･･･を〜に組み込む","熟語","S","","5.2"],["settle into~","〜に慣れる","熟語","R","","5.2"],["pay one's way","経済的に自立する","熟語","R","","5.2"],["bring~down","〜をがっかりさせる、落ち込ませる","熟語","R","","5.2"],["a new lease on life","復活、再出発、新たな人生","熟語","S","","5.2"],["go on to say","続けて･･･と言う","熟語","R","","5.2"],["burn-out","(心身の) 極度の疲労、燃え尽き","名詞","R","","5.3"],["luxury","ぜいたく","名詞","N","","5.3"],["afford","･･･を持つ (買う) 余裕がある","動詞","N","","5.3"],["remote","人里離れた、へんぴな、遠い","形容詞","N","","5.3"],["isolation","孤独感","名詞","R","","5.3"],["struggle","(･･･しようと) 努力する、もがく","動詞","R","","5.3"],["afterward","後で","副詞","R","","5.3"],["push","~に強いる","動詞","N","push O to do~･･･ に~するよう強いる","5.3"],["end up~ing","結局は〜することになる","熟語","R","","5.3"],["get to 人","人の心に影響を及ぼす、人をいらいらさせる","熟語","R","","5.3"],["not all it's cracked up to be","評判ほどではない","熟語","S","","5.3"],["take into account ...","･･･を考慮する","熟語","S","","5.3"],["take up...","･･･を取り入れる","熟語","R","","5.3"]]];
const UNITS=UR.map((l,i)=>({u:i+1,list:l.map(([w,m,p,r,n,s])=>({w,m,p,r,n,s,u:i+1}))}));
const START=()=>UNITS[0].list.map(x=>({w:x.w,m:x.m,p:x.p,n:x.n,u:1,box:1}));
const nk=w=>String(w).toLowerCase().replace(/[~\s]+$/,"");
const UNITW=new Map(UNITS.flatMap(U=>U.list).map(x=>[nk(x.w),x]));
const mkWord=(w,m)=>{const U=UNITW.get(nk(w));return{w,m,p:U?U.p:"",n:U?U.n:"",u:U?U.u:0,g:U?undefined:nextG(),box:1}};
const GN="vocab_gnames_v1";
let gnames=(()=>{try{const g=JSON.parse(localStorage.getItem(GN));if(g&&typeof g==="object")return g}catch(e){}return{}})(),openG=null;
const gnm=g=>gnames[g]||`取り込み単語 ${g+1}`;
function saveGn(){try{localStorage.setItem(GN,JSON.stringify(gnames))}catch(e){}}
function nextG(){const c=words.filter(x=>!x.u&&x.g!==undefined);if(!c.length)return 0;const mx=Math.max(...c.map(x=>x.g));return c.filter(x=>x.g===mx).length>=100?mx+1:mx}
let words=load(),tab="study",cur=null,flip=false,quiz=null,score={c:0,t:0},gain="",cands=[],scanMsg="",scanLvl="all";
const REVIEW_KEY="vocab_review_meta_v1", SETTINGS_KEY="vocab_learning_settings_v1";
let reviewMeta=(()=>{try{return JSON.parse(localStorage.getItem(REVIEW_KEY))||{}}catch(e){return {}}})();
let learningSettings=(()=>{try{return {...{direction:"en2ja",count:10,scope:"all"},...(JSON.parse(localStorage.getItem(SETTINGS_KEY))||{})}}catch(e){return {direction:"en2ja",count:10,scope:"all"}}})();
let activeStudyMode="all",sessionAnswered=0,sessionCorrect=0,sessionFinished=false;
function saveReviewMeta(){try{localStorage.setItem(REVIEW_KEY,JSON.stringify(reviewMeta))}catch(e){}}
function saveLearningSettings(){try{localStorage.setItem(SETTINGS_KEY,JSON.stringify(learningSettings))}catch(e){}}
function wordKey(w){return String(w.w||"").toLowerCase()}
function reviewDue(w){const m=reviewMeta[wordKey(w)];return !!m&&(!m.nextReview||new Date(m.nextReview)<=new Date())}
function isWeak(w){const m=reviewMeta[wordKey(w)];return (!!m&&((Number(m.wrong)||0)>=(Number(m.correct)||0)))||(Number(w.box)||1)<=2}
function candidatesForMode(){return words.map((w,i)=>({w,i})).filter(({w})=>!w.off&&(activeStudyMode==="weak"?isWeak(w):activeStudyMode==="review"?reviewDue(w):true));}
function recordReview(w,ok){const k=wordKey(w),m=reviewMeta[k]||{correct:0,wrong:0};if(ok){m.correct++;const days=[1,3,7,14,30];m.intervalIndex=Math.min(4,(m.intervalIndex||0));m.interval=days[m.intervalIndex];m.intervalIndex=Math.min(4,m.intervalIndex+1);m.nextReview=new Date(Date.now()+m.interval*86400000).toISOString()}else{m.wrong++;m.interval=1;m.intervalIndex=0;m.nextReview=new Date(Date.now()+86400000).toISOString()}m.lastSeen=new Date().toISOString();reviewMeta[k]=m;saveReviewMeta()}

let listSearch="",listSort="default";
const DK="vocab_daily_v1",AK="vocab_achievements_v1",TK="vocab_timer_v1",RAK="vocab_achievement_rewards_v1";
const todayKey=()=>{const d=new Date();return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,"0")}-${String(d.getDate()).padStart(2,"0")}`};
let daily=(()=>{try{return JSON.parse(localStorage.getItem(DK))||{}}catch(e){return {}}})();
const VK="vocab_visit_days_v1";
let visitDays=(()=>{try{const v=JSON.parse(localStorage.getItem(VK));return Array.isArray(v)?v:[]}catch(e){return []}})();
// Browser-local visit tracking: one login/visit day per calendar date.
if(!visitDays.includes(todayKey())){visitDays.push(todayKey());try{localStorage.setItem(VK,JSON.stringify(visitDays))}catch(e){}}
let calendarCursor=new Date(new Date().getFullYear(),new Date().getMonth(),1);
let achievements=(()=>{try{const a=JSON.parse(localStorage.getItem(AK));return Array.isArray(a)?a:[]}catch(e){return []}})();
let rewardedAchievements=(()=>{try{const a=JSON.parse(localStorage.getItem(RAK));return Array.isArray(a)?a:[]}catch(e){return []}})();
let challenge={active:false,left:60,score:0,question:null,interval:null};
let timerData=(()=>{try{const d=JSON.parse(localStorage.getItem(TK));return {best:Number(d&&d.best)||0}}catch(e){return {best:0}}})();
const MK="vocab_marathon_v1";
let marathonData=(()=>{try{const d=JSON.parse(localStorage.getItem(MK))||{};return {best:Number(d.best)||0,runs:Number(d.runs)||0,totalCorrect:Number(d.totalCorrect)||0}}catch(e){return {best:0,runs:0,totalCorrect:0}}})();
let marathon={active:false,score:0,question:null,recent:[],last:null};
let achievementToastTimer=null,achievementPage=1;
function saveDaily(){try{localStorage.setItem(DK,JSON.stringify(daily))}catch(e){}}
function markStudy(){const d=todayKey();if(!daily[d])daily[d]=0;daily[d]++;saveDaily();if(shopData&&shopData.reviewRemaining>0){shopData.reviewRemaining--;saveShopData()}checkAchievements()}
function streak(){let n=0,d=new Date();if(!daily[todayKey()])d.setDate(d.getDate()-1);while(daily[`${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,"0")}-${String(d.getDate()).padStart(2,"0")}`]){n++;d.setDate(d.getDate()-1)}return n}
function todayCount(){return daily[todayKey()]||0}
function totalStudyCount(){return Object.values(daily).reduce((a,b)=>a+(Number(b)||0),0)}
function masteredCount(){return words.filter(w=>w.box>=5).length}
function achievementDefs(){return [
 // 基本実績：既存IDを維持しているため、これまでの達成状況は引き継がれます
 {id:"first",title:"学習1回",desc:"学習を1回記録する",test:()=>totalStudyCount()>=1,xp:20,coins:10},
 {id:"ten",title:"学習10回",desc:"累計10回学習する",test:()=>totalStudyCount()>=10,xp:35,coins:20},
 {id:"study50",title:"学習50回",desc:"累計50回学習する",test:()=>totalStudyCount()>=50,xp:70,coins:40},
 {id:"study100",title:"学習100回",desc:"累計100回学習する",test:()=>totalStudyCount()>=100,xp:140,coins:80},
 {id:"streak3",title:"連続学習3日",desc:"3日連続で学習する",test:()=>streak()>=3,xp:50,coins:30},
 {id:"streak7",title:"連続学習7日",desc:"7日連続で学習する",test:()=>streak()>=7,xp:130,coins:75},
 {id:"level3",title:"レベル3",desc:"プレイヤーレベル3になる",test:()=>lvOf(prof.xp)>=3,xp:40,coins:20},
 {id:"level5",title:"レベル5",desc:"プレイヤーレベル5になる",test:()=>lvOf(prof.xp)>=5,xp:80,coins:45},
 {id:"level10",title:"レベル10",desc:"プレイヤーレベル10になる",test:()=>lvOf(prof.xp)>=10,xp:180,coins:100},
 {id:"level20",title:"レベル20",desc:"プレイヤーレベル20になる",test:()=>lvOf(prof.xp)>=20,xp:400,coins:250},
 {id:"words40",title:"単語数40",desc:"単語帳に40語登録する",test:()=>words.length>=40,xp:25,coins:15},
 {id:"words60",title:"単語数60",desc:"単語帳に60語登録する",test:()=>words.length>=60,xp:50,coins:30},
 {id:"words100",title:"単語数100",desc:"単語帳に100語登録する",test:()=>words.length>=100,xp:100,coins:70},
 {id:"words150",title:"単語数150",desc:"単語帳に150語登録する",test:()=>words.length>=150,xp:200,coins:140},
 {id:"words200",title:"単語数200",desc:"単語帳に200語登録する",test:()=>words.length>=200,xp:350,coins:240},
 {id:"master10",title:"定着単語10語",desc:"レベル5に定着した単語を10語にする",test:()=>masteredCount()>=10,xp:80,coins:50},
 {id:"master30",title:"定着単語30語",desc:"レベル5に定着した単語を30語にする",test:()=>masteredCount()>=30,xp:180,coins:110},
 {id:"combo5",title:"5コンボ",desc:"5コンボを達成する",test:()=>prof.combo>=5,xp:45,coins:25},
 {id:"unit2",title:"Unit 2開放",desc:"Unit 2の単語を1語以上開放する",test:()=>words.some(w=>w.u===2),xp:35,coins:20},
 // 60秒チャレンジ：条件の順に番号を付け、名前をシンプルに統一
 {id:"timer5",title:"60秒チャレンジ1",desc:"60秒チャレンジで5問以上正解する",test:()=>timerData.best>=5,xp:30,coins:15},
 {id:"challenge10",title:"60秒チャレンジ2",desc:"60秒チャレンジで10問以上正解する",test:()=>timerData.best>=10,xp:100,coins:60},
 {id:"timer15",title:"60秒チャレンジ3",desc:"60秒チャレンジで15問以上正解する",test:()=>timerData.best>=15,xp:80,coins:45},
 {id:"timer20",title:"60秒チャレンジ4",desc:"60秒チャレンジで20問以上正解する",test:()=>timerData.best>=20,xp:130,coins:80},
 {id:"timer25",title:"60秒チャレンジ5",desc:"60秒チャレンジで25問以上正解する",test:()=>timerData.best>=25,xp:180,coins:110},
 {id:"timer30",title:"60秒チャレンジ6",desc:"60秒チャレンジで30問以上正解する",test:()=>timerData.best>=30,xp:250,coins:160},
 {id:"timer35",title:"60秒チャレンジ7",desc:"60秒チャレンジで35問以上正解する",test:()=>timerData.best>=35,xp:300,coins:190},
 {id:"timer40",title:"60秒チャレンジ8",desc:"60秒チャレンジで40問以上正解する",test:()=>timerData.best>=40,xp:350,coins:230},
 {id:"timer45",title:"60秒チャレンジ9",desc:"60秒チャレンジで45問以上正解する",test:()=>timerData.best>=45,xp:420,coins:270},
 {id:"timer50",title:"60秒チャレンジ10",desc:"60秒チャレンジで50問以上正解する",test:()=>timerData.best>=50,xp:500,coins:320},
 {id:"timer55",title:"60秒チャレンジ11",desc:"60秒チャレンジで55問以上正解する",test:()=>timerData.best>=55,xp:580,coins:380},
 {id:"timer60",title:"60秒チャレンジ12",desc:"60秒チャレンジで60問以上正解する",test:()=>timerData.best>=60,xp:680,coins:450},
 {id:"timer65",title:"60秒チャレンジ13",desc:"60秒チャレンジで65問以上正解する",test:()=>timerData.best>=65,xp:800,coins:530},
 {id:"timer70",title:"60秒チャレンジ14",desc:"60秒チャレンジで70問以上正解する",test:()=>timerData.best>=70,xp:950,coins:620},
 {id:"timer75",title:"60秒チャレンジ15",desc:"60秒チャレンジで75問以上正解する",test:()=>timerData.best>=75,xp:1100,coins:720},
 {id:"timer80",title:"60秒チャレンジ16",desc:"60秒チャレンジで80問以上正解する",test:()=>timerData.best>=80,xp:1300,coins:850},
 // マラソンモード：既存の5段階に10段階を追加
 {id:"marathon10",title:"マラソンモード1",desc:"マラソンモードで10問連続正解する",test:()=>marathonData.best>=10,xp:50,coins:25},
 {id:"marathon25",title:"マラソンモード2",desc:"マラソンモードで25問連続正解する",test:()=>marathonData.best>=25,xp:100,coins:60},
 {id:"marathon50",title:"マラソンモード3",desc:"マラソンモードで50問連続正解する",test:()=>marathonData.best>=50,xp:200,coins:120},
 {id:"marathon100",title:"マラソンモード4",desc:"マラソンモードで100問連続正解する",test:()=>marathonData.best>=100,xp:350,coins:220},
 {id:"marathon200",title:"マラソンモード5",desc:"マラソンモードで200問連続正解する",test:()=>marathonData.best>=200,xp:700,coins:450},
 {id:"marathon250",title:"マラソンモード6",desc:"マラソンモードで250問連続正解する",test:()=>marathonData.best>=250,xp:800,coins:500},
 {id:"marathon300",title:"マラソンモード7",desc:"マラソンモードで300問連続正解する",test:()=>marathonData.best>=300,xp:900,coins:600},
 {id:"marathon400",title:"マラソンモード8",desc:"マラソンモードで400問連続正解する",test:()=>marathonData.best>=400,xp:1100,coins:700},
 {id:"marathon500",title:"マラソンモード9",desc:"マラソンモードで500問連続正解する",test:()=>marathonData.best>=500,xp:1300,coins:850},
 {id:"marathon750",title:"マラソンモード10",desc:"マラソンモードで750問連続正解する",test:()=>marathonData.best>=750,xp:1700,coins:1100},
 {id:"marathon1000",title:"マラソンモード11",desc:"マラソンモードで1000問連続正解する",test:()=>marathonData.best>=1000,xp:2200,coins:1500},
 {id:"marathon1250",title:"マラソンモード12",desc:"マラソンモードで1250問連続正解する",test:()=>marathonData.best>=1250,xp:2700,coins:1800},
 {id:"marathon1500",title:"マラソンモード13",desc:"マラソンモードで1500問連続正解する",test:()=>marathonData.best>=1500,xp:3200,coins:2200},
 {id:"marathon2000",title:"マラソンモード14",desc:"マラソンモードで2000問連続正解する",test:()=>marathonData.best>=2000,xp:4000,coins:2800},
 {id:"marathon3000",title:"マラソンモード15",desc:"マラソンモードで3000問連続正解する",test:()=>marathonData.best>=3000,xp:5500,coins:3800}
]}
function showAchievementToast(items,xp,coins){const el=$("achToast");if(!el)return;const names=items.slice(0,3).map(a=>a.title).join("・")+(items.length>3?` ほか${items.length-3}件`:"");el.innerHTML=`${ico("trophy",18)} 実績報酬：${names}　+${xp} XP / +${ico("coins",16,"coin-mark")} ${coins}`;el.classList.add("show");if(achievementToastTimer)clearTimeout(achievementToastTimer);achievementToastTimer=setTimeout(()=>el.classList.remove("show"),4800)}
function checkAchievements(){
 let changed=false,again=true,guard=0,totalXP=0,totalCoins=0;const rewardBatch=[];
 while(again&&guard++<25){again=false;
  for(const a of achievementDefs()){
   if(!a.test())continue;
   if(!achievements.includes(a.id)){achievements.push(a.id);changed=true;again=true}
   if(!rewardedAchievements.includes(a.id)){rewardedAchievements.push(a.id);prof.xp+=a.xp;prof.coins+=a.coins;totalXP+=a.xp;totalCoins+=a.coins;rewardBatch.push(a);changed=true;again=true}
  }
 }
 if(changed){try{localStorage.setItem(AK,JSON.stringify(achievements));localStorage.setItem(RAK,JSON.stringify(rewardedAchievements))}catch(e){}saveProf();hud()}
 if(rewardBatch.length)showAchievementToast(rewardBatch,totalXP,totalCoins);
}

words.filter(x=>!x.u&&x.g===undefined).forEach(x=>{x.g=nextG()});
const PK="vocab_profile_v1";
let prof=(()=>{try{const p=JSON.parse(localStorage.getItem(PK));if(p&&typeof p.xp==="number")return p}catch(e){}return{xp:0,coins:0,combo:0}})();
function saveProf(){try{localStorage.setItem(PK,JSON.stringify(prof))}catch(e){}}
const SHK="vocab_shop_v1";
const SHOP_DEFAULTS={inventory:{hintTicket:0,reviewTicket:0,xpBoost:0,coinBoost:0},ownedThemes:["default"],theme:"default",reviewRemaining:0,xpBoostRemaining:0,coinBoostRemaining:0,medalsSpent:0,dailyBought:{}};
function loadShopData(){
 try{const d=JSON.parse(localStorage.getItem(SHK))||{};return {...SHOP_DEFAULTS,...d,inventory:{...SHOP_DEFAULTS.inventory,...(d.inventory||{})},ownedThemes:Array.isArray(d.ownedThemes)?[...new Set(["default",...d.ownedThemes])]:["default"],dailyBought:d.dailyBought&&typeof d.dailyBought==="object"?d.dailyBought:{}}}catch(e){return JSON.parse(JSON.stringify(SHOP_DEFAULTS))}
}
let shopData=loadShopData();
function saveShopData(){try{localStorage.setItem(SHK,JSON.stringify(shopData))}catch(e){}applyShopTheme()}
function applyShopTheme(){const root=document.documentElement;if(!shopData||!shopData.theme||shopData.theme==="default")root.removeAttribute("data-theme");else root.setAttribute("data-theme",shopData.theme)}
applyShopTheme();
const lvOf=x=>Math.floor(Math.sqrt(x/40))+1;
const U=id=>(prof.up&&prof.up[id])||0;
const GK="vocab_gacha_v2",REF={N:3,R:8,S:20};
const POOL=UNITS.slice(1).flatMap(U=>U.list);
let gcat=2;
const gpool=()=>gcat==="pre"?POOL.filter(p=>p.r!=="N"):POOL.filter(p=>p.u===gcat);
const RT={coin:1.12,xp:1.12,combo:1.2,lvb:1.15,disc:.96},mu=id=>Math.pow(RT[id],U(id)),pc=(id,l)=>Math.round((Math.pow(RT[id],l)-1)*100);
const costOf=n=>Math.max(1,Math.round((gcat==="pre"?(n===1?80:720):(n===1?20:180))*mu("disc")));
const gname=()=>gcat==="pre"?"プレミアム":"Unit "+gcat;
let gz=(()=>{try{const g=JSON.parse(localStorage.getItem(GK));if(g&&Array.isArray(g.owned))return g}catch(e){}return{owned:[],pulls:0}})(),pulled=[],dexMsg="";
let sfxOn=(()=>{try{return localStorage.getItem("vocab_sfx")!=="0"}catch(e){return true}})(),AC=null;
function tone(f,t,d,type="sine",v=.15){
  if(!sfxOn)return;
  try{AC=AC||new(window.AudioContext||window.webkitAudioContext)();if(AC.state==="suspended")AC.resume();
    const o=AC.createOscillator(),g=AC.createGain(),s=AC.currentTime+t;
    o.type=type;o.frequency.value=f;g.gain.setValueAtTime(v,s);g.gain.exponentialRampToValueAtTime(.001,s+d);
    o.connect(g);g.connect(AC.destination);o.start(s);o.stop(s+d)}catch(e){}
}
const SFX={
  ok:()=>{tone(660,0,.12);tone(880,.1,.2)},
  ng:()=>{tone(220,0,.18,"sawtooth",.08);tone(165,.15,.25,"sawtooth",.08)},
  flip:()=>tone(500,0,.07,"triangle",.1),
  up:()=>[523,659,784,1047].forEach((f,i)=>tone(f,i*.1,.3,"triangle")),
  N:()=>tone(440,0,.15),
  R:()=>{tone(523,0,.12);tone(784,.1,.25)},
  S:()=>[523,659,784,1047,1319].forEach((f,i)=>tone(f,i*.09,.4,"triangle",.18))
};
function sfx(n){SFX[n]&&SFX[n]()}
function toggleSfx(){sfxOn=!sfxOn;try{localStorage.setItem("vocab_sfx",sfxOn?"1":"0")}catch(e){}sfx("flip");hud()}
function showTitle(){
  const L=lvOf(prof.xp),t=$("ttl");t.style.display="flex";
  t.innerHTML=`<h2>楽単シート</h2><div class="tstat">Lv ${L}　<span class="icon-label">${ico("coins",17,"coin-mark")} ${prof.coins}</span>　<span class="icon-label">${ico("book",17)} ${words.length}語</span></div><button class="btn pri" onclick="startApp()">${prof.xp||gz.pulls?"つづきから":"はじめる"} ${ico("arrow",18)}</button>`;
}
function startApp(){sfx("ok");$("ttl").style.display="none";setTab("home")}
function saveGz(){try{localStorage.setItem(GK,JSON.stringify(gz))}catch(e){}}
function pullOne(fs){
  const x=Math.random(),pr=gcat==="pre",r=fs?"S":pr?(x<.3?"S":"R"):x<.05?"S":x<.30?"R":"N",has=p=>gz.owned.includes(p.w);
  const cp=gpool(),tier=cp.filter(p=>p.r===r);
  let c=tier.filter(p=>!has(p));
  if(!c.length)c=cp.filter(p=>!has(p));
  if(!c.length)c=tier.length?tier:cp;
  const p=c[Math.floor(Math.random()*c.length)],isNew=!has(p);
  if(isNew){gz.owned.push(p.w);if(!words.some(y=>y.w.toLowerCase()===p.w))words.push({w:p.w,m:p.m,p:p.p,n:p.n,u:p.u,box:1})}else prof.coins+=REF[p.r];
  return{...p,isNew};
}
function draw(n){
  const cost=costOf(n);if(prof.coins<cost)return;
  prof.coins-=cost;pulled=[];dexMsg="";
  for(let i=0;i<n;i++)pulled.push(pullOne(gcat==="pre"&&n===10&&i===9&&!pulled.some(q=>q.r==="S")));
  gz.pulls+=n;sfx(pulled.some(p=>p.r==="S")?"S":pulled.some(p=>p.r==="R")?"R":"N");
  gz.cd=gz.cd||{};if(gpool().every(p=>gz.owned.includes(p.w))&&!gz.cd[gcat]){gz.cd[gcat]=1;const bn=gcat==="pre"?300:100;prof.coins+=bn;dexMsg="「"+gname()+"」コンプリート！ボーナス "+ico("coins",16,"coin-mark")+" "+bn}
  save();saveGz();saveProf();hud();rShop();
}
function hud(){const L=lvOf(prof.xp),a=40*(L-1)**2,b=40*L*L;
  $("hud").innerHTML=`<span class="lv">Lv ${L}</span><div class="xp"><div class="t"><i style="width:${(prof.xp-a)/(b-a)*100}%"></i></div><small>${prof.xp-a} / ${b-a} XP</small></div><span class="icon-label" title="所持コイン">${ico("coins",17,"coin-mark")} ${prof.coins}</span><button class="del icon-label" style="color:var(--text);font-size:13px" onclick="toggleSfx()" aria-label="効果音の切り替え">${ico(sfxOn?"volume":"volumeOff",17)} ${sfxOn?"音ON":"音OFF"}</button>`}
function load(){try{const s=localStorage.getItem(K);if(s){const a=JSON.parse(s);if(Array.isArray(a)&&a.length)return a}}catch(e){}return START()}
function save(){try{localStorage.setItem(K,JSON.stringify(words))}catch(e){}sbInfo();checkAchievements()}
function sbInfo(){const e=$("sbf");if(e){const m=words.filter(x=>!x.off).length;e.textContent="出題中 "+m+" / "+words.length+"語"}}
function toggleSb(){$("sb").classList.toggle("open");$("ov").classList.toggle("open")}
function closeSb(){$("sb").classList.remove("open");$("ov").classList.remove("open")}
document.addEventListener("keydown",e=>{if(e.key==="Escape")closeSb()});
const esc=s=>String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const $=id=>document.getElementById(id);
// Inline SVG line icons: embedded in this file, so no network or icon font is required.
const ICONS={
 home:'<path d="m3 10 9-7 9 7M5 9v12h14V9M9 21v-7h6v7"/>',
 calendar:'<rect x="3" y="5" width="18" height="16" rx="2"/><path d="M16 3v4M8 3v4M3 10h18M8 14h.01M12 14h.01M16 14h.01M8 17h.01M12 17h.01"/>',
 menu:'<path d="M4 6h16M4 12h16M4 18h16"/>',
 coins:'<ellipse cx="8.5" cy="5" rx="6" ry="2.5"/><path d="M2.5 5v5c0 1.4 2.7 2.5 6 2.5 1.3 0 2.5-.2 3.5-.6M2.5 10v5c0 1.4 2.7 2.5 6 2.5"/><ellipse cx="16.5" cy="14" rx="5" ry="2.3"/><path d="M11.5 14v4c0 1.3 2.2 2.3 5 2.3s5-1 5-2.3v-4M11.5 18c0 1.3 2.2 2.3 5 2.3s5-1 5-2.3"/>',
 book:'<path d="M12 7v14M12 7C9.5 4.7 6.5 4 3 4v14c3.5 0 6.5.7 9 3M12 7c2.5-2.3 5.5-3 9-3v14c-3.5 0-6.5.7-9 3"/>',
 quiz:'<circle cx="12" cy="12" r="9"/><path d="M9.6 9a2.5 2.5 0 0 1 4.8.9c0 1.7-2.4 2.2-2.4 4M12 17.5h.01"/>',
 list:'<rect x="4" y="3" width="16" height="18" rx="2"/><path d="M8 8h8M8 12h8M8 16h5"/>',
 scan:'<path d="M4 8V5a1 1 0 0 1 1-1h3M16 4h3a1 1 0 0 1 1 1v3M20 16v3a1 1 0 0 1-1 1h-3M8 20H5a1 1 0 0 1-1-1v-3M8 9h8M8 12h8M8 15h5"/>',
 shop:'<path d="M5 8h14l1 12H4L5 8Z"/><path d="M9 8V6a3 3 0 0 1 6 0v2"/>',
 timer:'<circle cx="12" cy="13" r="8"/><path d="M12 9v4l3 2M9 2h6M12 2v3M18.5 6.5 20 5"/>',
 route:'<circle cx="6" cy="18" r="2.5"/><circle cx="18" cy="6" r="2.5"/><path d="M8 18h3a3 3 0 0 0 3-3v-3a3 3 0 0 1 3-3h.5"/>',
 chart:'<path d="M4 19V5M4 19h17M8 15l4-4 3 2 5-6"/><path d="M16 7h4v4"/>',
 volume:'<path d="M4 10v4h4l5 4V6l-5 4H4Z"/><path d="M16 9a5 5 0 0 1 0 6M18.5 6.5a9 9 0 0 1 0 11"/>',
 volumeOff:'<path d="M4 10v4h4l5 4V6l-5 4H4Z"/><path d="m17 9 5 6m0-6-5 6"/>',
 flame:'<path d="M12 22a7 7 0 0 0 7-7c0-3-1.6-5.2-4.5-8-.2 2.6-1.5 3.7-2.5 4.2C12 7.5 10.5 4.8 8 3 8.5 7.5 5 10 5 15a7 7 0 0 0 7 7Z"/><path d="M12 22a3.5 3.5 0 0 0 3.5-3.5c0-1.5-.8-2.7-2.3-4-.2 1.3-.8 2-1.7 2.5-.4-1.1-1-1.8-2-2.5-.1 1.8-1 2.7-1 4A3.5 3.5 0 0 0 12 22Z"/>',
 lock:'<rect x="5" y="10" width="14" height="11" rx="2"/><path d="M8 10V7a4 4 0 0 1 8 0v3M12 14v3"/>',
 unlock:'<rect x="5" y="10" width="14" height="11" rx="2"/><path d="M8 10V7a4 4 0 0 1 7.5-2"/><path d="M12 14v3"/>',
 award:'<circle cx="12" cy="8" r="5"/><path d="m8.5 12-1 9 4.5-2.5 4.5 2.5-1-9M10 8l1.3 1.3L14.5 6"/>',
 target:'<circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="5"/><circle cx="12" cy="12" r="1"/>',
 check:'<path d="m5 12 4 4L19 6"/>',
 checkCircle:'<circle cx="12" cy="12" r="9"/><path d="m8 12 2.5 2.5L16.5 8"/>',
 star:'<path d="m12 3 2.8 5.7 6.2.9-4.5 4.4 1.1 6.2-5.6-3-5.6 3 1.1-6.2L3 9.6l6.2-.9L12 3Z"/>',
 trophy:'<path d="M8 21h8M12 17v4M7 4h10v5a5 5 0 0 1-10 0V4Z"/><path d="M7 6H4v2a4 4 0 0 0 4 4M17 6h3v2a4 4 0 0 1-4 4"/>',
 clock:'<circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/>',
 sparkle:'<path d="m12 3 1.5 5.5L19 10l-5.5 1.5L12 17l-1.5-5.5L5 10l5.5-1.5L12 3ZM19 16l.7 2.3L22 19l-2.3.7L19 22l-.7-2.3L16 19l2.3-.7L19 16Z"/>',
 arrow:'<path d="M5 12h14M13 6l6 6-6 6"/>',
 sound:'<path d="M4 10v4h4l5 4V6l-5 4H4Z"/>',
 package:'<path d="m12 3 8 4.5v9L12 21l-8-4.5v-9L12 3Z"/><path d="m4.5 7.7 7.5 4.4 7.5-4.4M12 12.1V21M8 5.2l8 4.6"/>',
 palette:'<path d="M12 3a9 9 0 1 0 0 18h1.2a2 2 0 0 0 1.4-3.4 1.8 1.8 0 0 1 1.3-3.1H18a3 3 0 0 0 3-3c0-4.7-4-8.5-9-8.5Z"/><path d="M7.5 10h.01M10 7.5h.01M15 8.5h.01M8.5 14h.01"/>',
 zap:'<path d="m13 2-9 12h7l-1 8 10-13h-7l1-7Z"/>',
 gift:'<rect x="3" y="9" width="18" height="12" rx="2"/><path d="M2 6h20v3H2zM12 6v15M12 6H8.5a2.5 2.5 0 1 1 2.2-3.7L12 6ZM12 6h3.5a2.5 2.5 0 1 0-2.2-3.7L12 6Z"/>',
 ticket:'<path d="M4 5h16v4a3 3 0 0 0 0 6v4H4v-4a3 3 0 0 0 0-6V5Z"/><path d="M12 7v2M12 12v2M12 17v1"/>',
 backpack:'<rect x="5" y="7" width="14" height="14" rx="3"/><path d="M9 7V5a3 3 0 0 1 6 0v2M5 12H3v5h2M19 12h2v5h-2M9 12h6v4H9z"/>',
 gem:'<path d="m6 3-4 6 10 12L22 9l-4-6H6Z"/><path d="M2 9h20M6 3l3 6 3 12 3-12 3-6"/>',
 leaf:'<path d="M20 4C10 4 4 8 4 15a5 5 0 0 0 5 5c7 0 11-6 11-16Z"/><path d="M3 21c3-5 7-8 12-11"/>',
 sun:'<circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.9 4.9l1.4 1.4m11.4 11.4 1.4 1.4M2 12h2m16 0h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4"/>',
 moon:'<path d="M20.5 14.2A8.5 8.5 0 0 1 9.8 3.5 8.5 8.5 0 1 0 20.5 14.2Z"/>',
 image:'<rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><path d="m21 15-5-5L5 21"/>',
 shoppingBag:'<path d="M5 8h14l1 12H4L5 8Z"/><path d="M9 8V6a3 3 0 0 1 6 0v2"/>',
 medal:'<circle cx="12" cy="8" r="5"/><path d="m8.5 12-2 9 5.5-3 5.5 3-2-9"/>',
};
function ico(name,size=18,cls="inline-icon"){return `<svg class="line-icon ${cls}" style="--icon-size:${size}px" width="${size}" height="${size}" viewBox="0 0 24 24" aria-hidden="true" focusable="false">${ICONS[name]||ICONS.sparkle}</svg>`}
function speak(t){try{const u=new SpeechSynthesisUtterance(t);u.lang="en-US";speechSynthesis.cancel();speechSynthesis.speak(u)}catch(e){}}
function pick(excl){ // 選択中の学習モードを反映
  let all=candidatesForMode().map(({w,i})=>({i,wt:6-w.box}));
  if(shopData.reviewRemaining>0){const weak=all.filter(o=>words[o.i].box<=3);if(weak.length)all=weak}
  if(!all.length)return -1;
  const pl=all.filter(o=>o.i!==excl),pool=pl.length?pl:all;
  let r=Math.random()*pool.reduce((a,o)=>a+o.wt,0);
  for(const o of pool){r-=o.wt;if(r<=0)return o.i}
  return pool[0].i;
}
function grade(i,ok){if(i<0||!words[i])return;recordReview(words[i],ok);words[i].box=ok?Math.min(5,words[i].box+1):1;save()}
function setTab(t){tab=t;cur=null;quiz=null;pulled=[];dexMsg="";closeSb();window.scrollTo(0,0);render()}
function render(){hud();
  $("app").classList.toggle("home-dashboard",tab==="home");
  $("nav").innerHTML=[["study","学習","book"],["review","復習","calendar"],["weak","苦手単語","target"],["quiz","クイズ","quiz"],["list","単語帳","list"],["scan","取り込み","scan"],["shop","ショップ","shop"],["challenge","60秒チャレンジ","timer"],["marathon","マラソンモード","route"],["stats","進捗","chart"]]
    .map(([k,l,ic])=>`<button class="${tab===k?"on":""}" onclick="${k==="study"||k==="quiz"?"activeStudyMode='all';":""}setTab('${k}')">${ico(ic,20,"nav-icon")}<span>${l}</span></button>`).join("");
  sbInfo();
  ({home:rHome,study:rStudy,review:rReview,weak:rWeak,quiz:rQuiz,list:rList,scan:rScan,shop:rShop,challenge:rChallenge,marathon:rMarathon,stats:rStats})[tab]();
}
function shiftCalendar(delta){calendarCursor=new Date(calendarCursor.getFullYear(),calendarCursor.getMonth()+delta,1);rHome()}
function rHome(){
 const year=calendarCursor.getFullYear(),month=calendarCursor.getMonth(),first=new Date(year,month,1),last=new Date(year,month+1,0),offset=first.getDay();
 const visited=new Set(visitDays),studied=new Set(Object.keys(daily).filter(k=>(Number(daily[k])||0)>0));
 const weekdays=["日","月","火","水","木","金","土"];
 let cells=weekdays.map(d=>`<div class="cal-week">${d}</div>`).join("");
 for(let i=0;i<offset;i++)cells+='<div class="cal-day empty">0</div>';
 for(let d=1;d<=last.getDate();d++){const key=`${year}-${String(month+1).padStart(2,"0")}-${String(d).padStart(2,"0")}`,v=visited.has(key),st=studied.has(key),today=key===todayKey();cells+=`<div class="cal-day ${v?"visited":""} ${st?"studied":""}" ${today?'aria-current="date"':''} title="${v?'アクセス済み':''}${st?'・学習記録あり':''}">${d}</div>`}
 const totalVisits=visitDays.length;
 const actions=[
  ["scan","取り込み","scan",true],
  ["study","単語学習","book",true],
  ["review","復習","calendar",false],
  ["weak","苦手単語","target",false],
  ["quiz","4択クイズ","quiz",false],
  ["list","単語帳","list",false],
  ["challenge","60秒チャレンジ","timer",false],
  ["marathon","マラソンモード","route",false],
  ["shop","ショップ","shop",false],
  ["stats","進捗・実績","chart",false]
 ];
 $("app").innerHTML=`<div class="home-head"><h2>ホーム</h2></div>
 <div class="card calendar-card"><div class="cal-top"><strong>${year}年 ${month+1}月</strong><div class="cal-nav"><button onclick="shiftCalendar(-1)" aria-label="前の月">‹</button><button onclick="calendarCursor=new Date(new Date().getFullYear(),new Date().getMonth(),1);rHome()" aria-label="今月へ">今日</button><button onclick="shiftCalendar(1)" aria-label="次の月">›</button></div></div><div class="cal-grid">${cells}</div><div class="cal-legend"><span><i class="cal-dot"></i>アクセスした日</span><span><i class="cal-dot" style="background:var(--ok)"></i>学習した日</span></div></div>
 <div class="home-stats"><div class="home-stat"><span class="hs-icon">${ico("calendar",20)}</span><b>${totalVisits}</b><span>アクセス日数</span></div><div class="home-stat"><span class="hs-icon">${ico("flame",20)}</span><b>${streak()}</b><span>連続学習日数</span></div><div class="home-stat"><span class="hs-icon">${ico("book",20)}</span><b>${todayCount()}</b><span>今日の学習回数</span></div></div>
 <div class="home-section-title">${ico("sparkle",20)} 学習メニュー</div><div class="home-actions">${actions.map(([key,title,icon,primary])=>`<button class="home-action ${primary?"primary":""}" onclick="${key==="study"||key==="quiz"?"activeStudyMode='all';":""}setTab('${key}')"><span class="ha-icon">${ico(icon,23)}</span><b>${title}</b></button>`).join("")}</div>`;
}
function rReview(){activeStudyMode="review";const due=candidatesForMode().length;$("app").innerHTML=`<div class="card"><b class="icon-label">${ico("calendar",18)} 復習</b><div class="analytics-grid"><div class="analytics-tile"><b>${due}</b><span>復習対象</span></div><div class="analytics-tile"><b>${words.filter(w=>reviewMeta[wordKey(w)]).length}</b><span>記録済み単語</span></div></div><div class="mode-row"><button class="btn pri" ${due?"":"disabled"} onclick="activeStudyMode='review';setTab('study')">復習を開始</button><button class="btn" onclick="setTab('stats')">学習分析</button></div><div class="hint">正解が続くと復習間隔が1・3・7・14・30日に延びます。間違えた単語は翌日以降に再出題します。</div></div>`}
function rWeak(){activeStudyMode="weak";const list=candidatesForMode();$("app").innerHTML=`<div class="card"><b class="icon-label">${ico("target",18)} 苦手単語</b><div class="analytics-grid"><div class="analytics-tile"><b>${list.length}</b><span>苦手単語</span></div><div class="analytics-tile"><b>${list.filter(x=>x.w.box<=2).length}</b><span>定着レベル2以下</span></div></div><div class="mode-row"><button class="btn pri" ${list.length?"":"disabled"} onclick="activeStudyMode='weak';setTab('study')">苦手単語を学習</button><button class="btn" onclick="activeStudyMode='weak';setTab('quiz')">苦手単語クイズ</button></div>${list.length?`<div class="list">${list.slice(0,30).map(({w})=>`<div class="shop"><div class="si"><b>${esc(w.w)}</b><div class="hint">${esc(w.m)} · Lv${w.box}/5</div></div></div>`).join("")}</div>`:`<div class="hint">苦手単語はありません。</div>`}</div>`}
function rStudy(){
  if(cur===null){cur=pick(-1);flip=false}
  if(cur<0){$("app").innerHTML=`<div class="card">${activeStudyMode==="review"?"復習対象はありません。":"出題対象の単語がありません。"}<div class="row"><button class="btn" onclick="activeStudyMode='all';setTab('study')">通常学習</button><button class="btn" onclick="setTab('home')">ホーム</button></div></div>`;return}
  const x=words[cur];
  $("app").innerHTML=`<div class="card fc" onclick="flip=!flip;sfx('flip');rStudy()">
    ${flip?`<div class="m">${esc(x.m)}</div>${x.n?`<div class="hint">${esc(x.n)}</div>`:""}`:`<div class="w">${esc(x.w)}</div><div class="box">${esc(x.p||"")}</div><div class="hint">タップして意味を表示</div>`}
    <div class="box" style="margin-top:14px">レベル ${x.box}/5</div></div>
    <div class="row"><button class="btn icon-label" onclick="speak(words[cur].w)">${ico("volume",17)} 発音</button></div>
    <div class="row"><button class="btn ng" onclick="ans(false)">まだ</button><button class="btn ok" onclick="ans(true)">覚えた</button></div>`;
}
function rEmpty(){$("app").innerHTML=`<div class="card">出題範囲の単語がすべてOFFになっています。単語帳でスイッチをONにしてください。<div class="row"><button class="btn pri icon-label" onclick="setTab('list')">${ico("list",18)} 単語帳を開く</button></div></div>`}
function ans(ok){markStudy();sfx(ok?"ok":"flip");grade(cur,ok);cur=pick(cur);flip=false;rStudy()}
let qmode=learningSettings.direction||"en2ja";
function rQuiz(){
  const eligibleCount=candidatesForMode().length;
  if(eligibleCount===0){rEmpty();return}
  if(eligibleCount<4){$("app").innerHTML=`<div class="card">クイズには4語以上が必要です。単語帳で出題対象を増やしてください。</div>`;return}
  if(sessionAnswered>=Number(learningSettings.count||10)&&sessionAnswered>0){
    const total=sessionAnswered,correct=sessionCorrect;
    $("app").innerHTML=`<div class="card"><b class="icon-label">${ico("checkCircle",20)} セット完了</b><div class="analytics-grid"><div class="analytics-tile"><b>${correct} / ${total}</b><span>正解数</span></div><div class="analytics-tile"><b>${Math.round(correct/total*100)}%</b><span>正答率</span></div></div><div class="mode-row"><button class="btn pri" onclick="sessionAnswered=0;sessionCorrect=0;quiz=null;setTab('quiz')">次のセット</button><button class="btn" onclick="setTab('stats')">学習分析</button></div></div>`;return;
  }
  if(!quiz){
    const i=pick(-1);
    const allowed=new Set(candidatesForMode().map(o=>o.i));
    const answerText=k=>String(qmode==="ja2en"?words[k].w:words[k].m).trim().toLocaleLowerCase();
    const sh=words.map((_,k)=>k).filter(k=>allowed.has(k)&&k!==i&&words[k].w!==words[i].w&&answerText(k)!==answerText(i)).sort(()=>Math.random()-.5);
    const seenAnswers=new Set([answerText(i)]),unique=[];
    for(const k of sh){const key=answerText(k);if(!seenAnswers.has(key)){seenAnswers.add(key);unique.push(k)}}
    const same=unique.filter(k=>words[k].p&&words[k].p===words[i].p),others=[...same,...unique.filter(k=>!same.includes(k))].slice(0,3);
    if(others.length<3){quiz=null;$("app").innerHTML=`<div class="card">4択クイズには、意味の異なる単語が4語以上必要です。単語帳で登録内容を確認してください。<div class="row"><button class="btn" onclick="setTab('list')">単語帳</button></div></div>`;return}
    quiz={i,opts:[i,...others].sort(()=>Math.random()-.5),sel:null};
  }
  const x=words[quiz.i],ja=qmode==="ja2en";
  $("app").innerHTML=`<div class="card"><details><summary>学習設定</summary><div class="settings-grid" style="margin-top:10px"><label>出題方向<select onchange="learningSettings.direction=this.value;qmode=this.value;saveLearningSettings();quiz=null;rQuiz()"><option value="en2ja" ${qmode==="en2ja"?"selected":""}>英語 → 日本語</option><option value="ja2en" ${qmode==="ja2en"?"selected":""}>日本語 → 英語</option></select></label><label>1セットの問題数<select onchange="learningSettings.count=+this.value;saveLearningSettings()">${[5,10,20,30,50].map(n=>`<option value="${n}" ${learningSettings.count===n?"selected":""}>${n}問</option>`).join("")}</select></label></div><div class="hint">指定した問題数に達するとセットが終了します。</div></details><div class="box" style="margin:10px 0">正解 ${score.c} / ${score.t}　${ico("flame",16)} コンボ ${prof.combo}</div>
    <div class="q" ${ja?'style="font-size:24px"':""}>${esc(ja?x.m:x.w)}</div><div class="box" style="text-align:center">${esc(x.p||"")}</div><div class="hint" style="text-align:center;margin-top:2px">出典：${esc(srcOf(x))}</div><div class="row"><button class="btn icon-label" ${ja&&quiz.sel===null?"disabled":""} onclick="speak(words[quiz.i].w)">${ico("volume",17)} 発音</button><button class="btn" ${quiz.sel!==null||(prof.coins<10&&shopData.inventory.hintTicket<=0)||quiz.hid?"disabled":""} onclick="useHint()">ヒント ${shopData.inventory.hintTicket>0?ico("ticket",16)+" ×1":ico("coins",16,"coin-mark")+" 10"}</button></div>
    <div class="opts">${quiz.opts.filter(k=>!(quiz.hid||[]).includes(k)).map(k=>{
      let c="";if(quiz.sel!==null){if(k===quiz.i)c="right";else if(k===quiz.sel)c="wrong"}
      return `<button class="btn opt ${c}" ${quiz.sel!==null?"disabled":""} onclick="choose(${k})">${esc(ja?words[k].w:words[k].m)}</button>`}).join("")}</div>
    ${quiz.sel!==null?`<div class="toast">${gain}</div><div class="row"><button class="btn pri" onclick="quiz=null;rQuiz()">次の問題 →</button></div>`:""}</div>`;
}
function choose(k){
  if(quiz.sel!==null)return;
  quiz.sel=k;const ok=k===quiz.i;score.t++;sessionAnswered++;if(ok)sessionCorrect++;markStudy();grade(quiz.i,ok);
  if(ok){score.c++;prof.combo++;const bonus=prof.combo%5===0;let xp=Math.round((10+Math.min(prof.combo-1,5)*2*mu("combo"))*mu("xp")),co=Math.round((5+(bonus?10:0))*mu("coin")),L0=lvOf(prof.xp),extraXP=0,extraCoins=0;
    if(shopData.xpBoostRemaining>0){extraXP=Math.ceil(xp*.5);xp+=extraXP;shopData.xpBoostRemaining--}
    if(shopData.coinBoostRemaining>0){extraCoins=Math.ceil(co*.5);co+=extraCoins;shopData.coinBoostRemaining--}
    if(extraXP||extraCoins)saveShopData();
    prof.xp+=xp;prof.coins+=co;sfx("ok");gain=`+${xp} XP　+${ico("coins",15,"coin-mark")}${co}`+(bonus?`　${ico("flame",15)} 5コンボボーナス!`:"")+(extraXP||extraCoins?`　${ico("zap",14)}ブースト適用`:"");
    if(lvOf(prof.xp)>L0){const lb=Math.round(50*mu("lvb"));prof.coins+=lb;setTimeout(()=>sfx("up"),250);gain+=`　レベルアップ! Lv${lvOf(prof.xp)}(+${ico("coins",14,"coin-mark")}${lb})`}}
  else{prof.combo=0;sfx("ng");gain="残念… コンボがリセットされました"}
  checkAchievements();saveProf();hud();rQuiz();
}
function useHint(){if(!quiz||quiz.sel!==null||quiz.hid)return;if(shopData.inventory.hintTicket>0){shopData.inventory.hintTicket--;saveShopData()}else{if(prof.coins<10)return;prof.coins-=10;saveProf()}quiz.hid=quiz.opts.filter(k=>k!==quiz.i).slice(0,2);hud();rQuiz()}
let ptText="",ptMin=4;
const STOP=new Set("about above after again all also been before being below between both because could does doing down during each from further have having here hers himself into itself just more most myself only other ours ourselves over same should some such than that their theirs them themselves then there these they this those through under until very were what when where which while whom will with would your yours yourself yourselves said says getting goes going went make made like first good great well back much many even still take took come came know known want used find work way thing things people time year years day days little long right left high small large next early young important able ever never always often really must might shall upon yet however although though".split(" "));
const RE_EJ=/^([A-Za-z][A-Za-z'~.\- ]*?)\s*(?:[|｜:：=＝\-–—→\/・]\s*)?(?:(?:名詞|動詞|形容詞|副詞|前置詞|熟語|名|動|形|副|前|フレ)(?:\s*[|｜:：.．]\s*|\s+))?([（(\u3040-\u30ff\u3400-\u9fff〜~･「].*)$/;
const RE_JE=/^([\u3040-\u30ff\u3400-\u9fff（(][^A-Za-z]*?)\s*[|｜:：=＝\-–—→\/]?\s*([A-Za-z][A-Za-z'~.\- ]*)$/;
const hasJa=s=>/[\u3040-\u30ff\u3400-\u9fff]/.test(s);
function parsePairs(text){
  const pairs=[],rest=[];
  text.replace(/[’‘]/g,"'").split(/\r?\n/).forEach(raw=>{
    const line=raw.replace(/^\s*(?:[-*•・●○▪]|\d+[.)．、])\s*/,"").trim();
    if(!line)return;
    let en=null,ja=null,m=line.match(RE_EJ);
    if(m&&hasJa(m[2])){en=m[1];ja=m[2]}
    else{m=line.match(RE_JE);if(m&&hasJa(m[1])){en=m[2];ja=m[1]}}
    en=en&&en.trim().toLowerCase().replace(/[~.\s-]+$/,"");
    if(en&&en.length>1&&en.split(/\s+/).length<=4&&/^[a-z][a-z'~ -]*$/.test(en)){
      pairs.push([en,ja.split("※")[0].trim().replace(/^[（(](.*)[）)]$/,"$1").slice(0,60)]);
    }else rest.push(line);
  });
  return{pairs,rest:rest.join("\n")};
}
function extractText(){
  const{pairs,rest}=parsePairs(ptText),have=new Set(words.map(x=>nk(x.w))),pm=new Map(),cnt=new Map();
  pairs.forEach(([w,m])=>{if(m&&!pm.has(w))pm.set(w,m)});
  (rest.toLowerCase().replace(/[’‘]/g,"'").match(/[a-z]+(?:'[a-z]+)?/g)||[]).forEach(w=>{
    w=w.replace(/'s$/,"");
    if(w.length<ptMin||STOP.has(w))return;
    cnt.set(w,(cnt.get(w)||0)+1);
  });
  for(const [w,n] of [...cnt]){if(w.endsWith("s")&&cnt.has(w.slice(0,-1))){cnt.set(w.slice(0,-1),cnt.get(w.slice(0,-1))+n);cnt.delete(w)}}
  const mk=(w,m,n,pair)=>{const U=UNITW.get(nk(w))||UNITW.get(nk(w).replace(/s$/,""));return{w,m,n,pair,on:!U,unit:U?U.u:0}};
  const a=[...pm].filter(([w])=>!have.has(nk(w))).map(([w,m])=>mk(w,m,1,true));
  const b=[...cnt].filter(([w])=>!have.has(w)&&!have.has(w.replace(/s$/,""))&&!pm.has(w)).sort((x,y)=>y[1]-x[1]||y[0].length-x[0].length).slice(0,50).map(([w,n])=>mk(w,"",n,false));
  cands=[...a,...b];
  const lk=cands.filter(c=>c.unit).length;
  scanMsg=!ptText.trim()?"英文を貼り付けてください。":cands.length?`${cands.length}語を抽出しました（訳あり ${a.length}語）。登録済みの単語は除外されています。`+(lk?`未開放のUnit単語が${lk}語あります。`:"")+"意味がない単語は、追加前に入力してください。":"追加できる単語はありませんでした。";
  rScan();
}
function rScan(){
  $("app").innerHTML=`<div class="card"><b>テキストから単語を追加</b>
    <div class="hint">英文を貼り付けて「単語を抽出」を押してください。英単語の隣に日本語訳がある場合は、訳も取り込みます。抽出結果を確認し、追加する単語を選んでください。</div>
    <textarea id="pt" rows="6" placeholder="ここに英文を貼り付け" oninput="ptText=this.value">${esc(ptText)}</textarea>
    <select onchange="ptMin=+this.value"><option value="4" ${ptMin===4?"selected":""}>標準（4文字以上）</option><option value="7" ${ptMin===7?"selected":""}>難しめの単語のみ（7文字以上）</option></select>
    <div class="row"><button class="btn pri" onclick="extractText()">単語を抽出</button></div>
    <div class="hint">${esc(scanMsg)}</div>
    ${cands.length?`<div class="row"><button class="btn" onclick="cands.forEach(c=>c.on=true);rScan()">全選択</button><button class="btn" onclick="cands.forEach(c=>c.on=false);rScan()">全解除</button></div>
    <ul>${cands.map((c,i)=>`<li><input type="checkbox" style="width:auto;margin:0" ${c.on?"checked":""} onchange="cands[${i}].on=this.checked;rScan()"><div><input value="${esc(c.w)}" oninput="cands[${i}].w=this.value" style="margin:0 0 4px;font-weight:700"><input value="${esc(c.m)}" placeholder="意味を入力" oninput="cands[${i}].m=this.value" style="margin:0"></div><span class="box" style="text-align:right">${c.unit?"[Unit"+c.unit+"] ":""}${c.pair?"訳あり":"×"+c.n}</span></li>`).join("")}</ul>
    <div class="row"><button class="btn pri" onclick="addCands()">選択した単語を追加</button></div>`:""}</div>`;
}
function addCands(){
  const seen=new Set(words.map(x=>x.w.toLowerCase()));let k=0,skip=0;
  cands.filter(c=>c.on).forEach(c=>{const w=c.w.trim(),m=c.m.trim();if(!w||seen.has(w.toLowerCase()))return;if(!m){skip++;return}seen.add(w.toLowerCase());words.push(mkWord(w,m));k++});
  save();cands=cands.filter(c=>c.on&&!c.m.trim());
  scanMsg=`${k}語を単語帳に追加しました。`+(skip?`意味が未入力の${skip}語は残してあります。`:"");
  if(k)sfx("ok");rScan();
}
const SHOP=[
 {id:"coin",n:"コイン獲得量アップ",d:"クイズ正解時のコイン獲得量が増える",max:10,base:100,fx:l=>"獲得コイン +"+pc("coin",l)+"%"},
 {id:"xp",n:"経験値獲得量アップ",d:"クイズ正解時のXP獲得量が増える",max:10,base:80,fx:l=>"獲得XP +"+pc("xp",l)+"%"},
 {id:"combo",n:"コンボ強化",d:"連続正解時の追加XPが増える",max:10,base:120,fx:l=>"コンボボーナス +"+pc("combo",l)+"%"},
 {id:"disc",n:"ガチャ割引",d:"ガチャの費用が下がる",max:10,base:150,fx:l=>"費用 -"+Math.round((1-Math.pow(RT.disc,l))*100)+"%"},
 {id:"lvb",n:"レベルアップ報酬強化",d:"レベルアップ時のコイン報酬が増える",max:10,base:100,fx:l=>"報酬 +"+pc("lvb",l)+"%"}
];
const upCost=s=>Math.round(s.base*Math.pow(1.4,U(s.id))/10)*10;
const SHOP_ITEMS=[
 {id:"hintTicket",name:"ヒントチケット",desc:"クイズのヒントでコインの代わりに使用",price:8,icon:"ticket"},
 {id:"reviewTicket",name:"復習チケット",desc:"次の10問は定着度の低い単語を優先",price:120,icon:"book"},
 {id:"xpBoost",name:"XPブースター",desc:"次の20回のクイズ正解でXP +50%",price:180,icon:"zap"},
 {id:"coinBoost",name:"コインブースター",desc:"次の20回のクイズ正解でコイン +50%",price:180,icon:"coins"}
];
const SHOP_THEMES=[
 {id:"ocean",name:"オーシャン",desc:"青系のテーマ",price:220,icon:"moon",swatch:["#eff8ff","#1677b9"]},
 {id:"forest",name:"フォレスト",desc:"緑系のテーマ",price:220,icon:"leaf",swatch:["#f1f7f0","#2e7d50"]},
 {id:"violet",name:"バイオレット",desc:"紫系のテーマ",price:260,icon:"palette",swatch:["#f7f3ff","#8055c7"]},
 {id:"sunset",name:"サンセット",desc:"オレンジ系のテーマ",price:260,icon:"sun",swatch:["#fff6ef","#d45f3b"]}
];
const EXCHANGE_THEMES=[
 {id:"rose",name:"ローズ",desc:"交換所限定・ピンク系テーマ",medals:6,icon:"palette",swatch:["#fff2f6","#c44579"]},
 {id:"aurora",name:"オーロラ",desc:"交換所限定・ダークテーマ",medals:8,icon:"moon",swatch:["#101b2d","#61a7e8"]},
 {id:"paper",name:"ペーパー",desc:"交換所限定・紙風テーマ",medals:4,icon:"image",swatch:["#f4f0e6","#796b4b"]}
];
const THEME_NAMES={default:"システム設定",ocean:"オーシャン",forest:"フォレスト",violet:"バイオレット",sunset:"サンセット",rose:"ローズ",aurora:"オーロラ",paper:"ペーパー"};
const medalsEarned=()=>Math.floor(totalStudyCount()/25);
const medalsAvailable=()=>Math.max(0,medalsEarned()-(Number(shopData.medalsSpent)||0));
let shopTab="items",shopMsg="";
function shopBalance(){return `<div class="shop-balance"><span class="icon-label">${ico("coins",18,"coin-mark")} 所持コイン <b>${prof.coins}</b></span><span class="icon-label">${ico("medal",18)} 学習メダル <b>${medalsAvailable()}</b></span></div>`}
function shopTabsHtml(){const tabs=[["items","アイテム","package"],["custom","カスタム","palette"],["up","強化","zap"],["daily","日替わり","gift"],["exchange","交換所","medal"],["inventory","所持品","backpack"],["gacha","ガチャ","sparkle"]];return `<div class="shop-tabs">${tabs.map(([id,label,ic])=>`<button class="chip ${shopTab===id?"on":""}" onclick="shopTab='${id}';shopMsg='';rShop()">${ico(ic,16)} ${label}</button>`).join("")}</div>`}
function rShop(){
  const tabs=shopTabsHtml(),balance=shopBalance();
  const body=shopTab==="gacha"?rDexHtml():shopTab==="up"?rUpHtml():shopTab==="items"?rItemsHtml():shopTab==="custom"?rThemesHtml():shopTab==="daily"?rDailyHtml():shopTab==="exchange"?rExchangeHtml():rInventoryHtml();
  $("app").innerHTML=`${tabs}${balance}${shopMsg?`<div class="toast">${shopMsg}</div>`:""}<div id="shopbody">${body}</div>`;
}
function shopProduct({icon="package",name,desc,price,button="購入",disabled=false,action="",tag="",swatch=null}){
 return `<div class="shop-product"><div class="sp-icon">${ico(icon,22)}</div><h3>${name}</h3>${swatch?`<div class="theme-swatch" style="--sw1:${swatch[0]};--sw2:${swatch[1]}"></div>`:""}<p>${desc}</p>${tag?`<span class="owned-label">${tag}</span>`:""}<div class="sp-price">${price}</div><button class="btn pri" ${disabled?"disabled":""} onclick="${action}">${button}</button></div>`;
}
function buyShopItem(id,priceOverride=null,daily=false){
 const item=SHOP_ITEMS.find(x=>x.id===id);if(!item)return;
 const price=priceOverride===null?item.price:priceOverride;
 const day=todayKey(),dailyKey=day+":"+id;
 if(daily&&shopData.dailyBought[dailyKey]){shopMsg="本日分は購入済みです。";rShop();return}
 if(prof.coins<price){shopMsg="コインが足りません。";rShop();return}
 prof.coins-=price;shopData.inventory[id]=(Number(shopData.inventory[id])||0)+1;
 if(daily)shopData.dailyBought[dailyKey]=true;
 saveProf();saveShopData();sfx("up");shopMsg=`${item.name}を購入しました。`;hud();rShop();
}
function buyTheme(id,price){const all=[...SHOP_THEMES,...EXCHANGE_THEMES],theme=all.find(x=>x.id===id);if(!theme||shopData.ownedThemes.includes(id))return;
 if(prof.coins<price){shopMsg="コインが足りません。";rShop();return}
 prof.coins-=price;shopData.ownedThemes.push(id);shopData.theme=id;saveProf();saveShopData();sfx("up");shopMsg=`${theme.name}を購入し、適用しました。`;hud();rShop();
}
function equipTheme(id){if(!shopData.ownedThemes.includes(id))return;shopData.theme=id;saveShopData();shopMsg=`${THEME_NAMES[id]||id}を適用しました。`;rShop()}
function useInventoryItem(id){const inv=shopData.inventory;
 if(!(inv[id]>0)){shopMsg="所持数がありません。";rShop();return}
 if(id==="reviewTicket"){inv[id]--;shopData.reviewRemaining+=10;shopMsg="復習モードを開始しました。次の10問は定着度の低い単語を優先します。"}
 else if(id==="xpBoost"){inv[id]--;shopData.xpBoostRemaining+=20;shopMsg="XPブースターを有効化しました。対象はクイズの次の20回の正解です。"}
 else if(id==="coinBoost"){inv[id]--;shopData.coinBoostRemaining+=20;shopMsg="コインブースターを有効化しました。対象はクイズの次の20回の正解です。"}
 saveShopData();sfx("up");rShop();
}
function rItemsHtml(){return `<div class="card"><div class="shop-section-head"><b class="icon-label">${ico("package",18)} アイテム</b></div><div class="shop-grid">${SHOP_ITEMS.map(i=>shopProduct({icon:i.icon,name:i.name,desc:i.desc,price:`${ico("coins",15,"coin-mark")} ${i.price}`,button:"購入",disabled:prof.coins<i.price,action:`buyShopItem('${i.id}')`})).join("")}</div></div>`}
function rThemesHtml(){const current=THEME_NAMES[shopData.theme]||"システム設定";return `<div class="card"><b class="icon-label">${ico("palette",18)} テーマ</b><div class="shop-note">適用中：${current}</div><div class="shop-grid">${SHOP_THEMES.map(t=>{const owned=shopData.ownedThemes.includes(t.id),equipped=shopData.theme===t.id;return shopProduct({icon:t.icon,name:t.name,desc:t.desc,price:owned?"購入済み":`${ico("coins",15,"coin-mark")} ${t.price}`,button:equipped?"適用中":owned?"適用":"購入",disabled:equipped||(!owned&&prof.coins<t.price),action:owned?`equipTheme('${t.id}')`:`buyTheme('${t.id}',${t.price})`,tag:owned?(equipped?"適用中":"所持済み"):"",swatch:t.swatch})}).join("")}</div><div class="shop-note">「システム設定」は端末のライト／ダーク設定に従います。</div><div class="row"><button class="btn" onclick="equipTheme('default')">システム設定に戻す</button></div></div>`}
function rDailyHtml(){
 const idx=Math.floor(new Date(new Date().getFullYear(),new Date().getMonth(),new Date().getDate()).getTime()/86400000);
 const item=SHOP_ITEMS[idx%SHOP_ITEMS.length],price=Math.max(1,Math.round(item.price*.7)),key=todayKey()+":"+item.id,bought=!!shopData.dailyBought[key];
 return `<div class="card"><b class="icon-label">${ico("gift",18)} 日替わり商品</b><div class="shop-note">毎日1種類が30%引きになります。購入は商品ごとに1日1回です。</div><div class="shop-grid">${shopProduct({icon:"gift",name:item.name+"（本日限定）",desc:item.desc,price:`<s>${item.price}</s>　${ico("coins",15,"coin-mark")} ${price}`,button:bought?"購入済み":"割引価格で購入",disabled:bought||prof.coins<price,action:`buyShopItem('${item.id}',${price},true)`,tag:bought?"本日購入済み":"30% OFF"})}</div></div>`;
}
function buyExchangeItem(id){
 if(id==="rose"||id==="aurora"||id==="paper") {const t=EXCHANGE_THEMES.find(x=>x.id===id);if(!t||shopData.ownedThemes.includes(id))return;if(medalsAvailable()<t.medals){shopMsg="学習メダルが足りません。";rShop();return}shopData.medalsSpent+=t.medals;shopData.ownedThemes.push(id);shopData.theme=id;saveShopData();sfx("up");shopMsg=`${t.name}を交換し、適用しました。`;rShop();return}
 if(id==="hintPack"){if(medalsAvailable()<2){shopMsg="学習メダルが足りません。";rShop();return}shopData.medalsSpent+=2;shopData.inventory.hintTicket+=3;saveShopData();shopMsg="ヒントチケット3枚と交換しました。";rShop();return}
 if(id==="xpPack"){if(medalsAvailable()<3){shopMsg="学習メダルが足りません。";rShop();return}shopData.medalsSpent+=3;shopData.inventory.xpBoost++;saveShopData();shopMsg="XPブースター1個と交換しました。";rShop();return}
 if(id==="coinPack"){if(medalsAvailable()<3){shopMsg="学習メダルが足りません。";rShop();return}shopData.medalsSpent+=3;shopData.inventory.coinBoost++;saveShopData();shopMsg="コインブースター1個と交換しました。";rShop();return}
}
function rExchangeHtml(){const products=[...EXCHANGE_THEMES.map(t=>({id:t.id,icon:t.icon,name:t.name,desc:t.desc,medals:t.medals,swatch:t.swatch})),{id:"hintPack",icon:"ticket",name:"ヒントチケット3枚",desc:"クイズのヒントに使える",medals:2},{id:"xpPack",icon:"zap",name:"XPブースター",desc:"次の20回のクイズ正解でXP +50%",medals:3},{id:"coinPack",icon:"coins",name:"コインブースター",desc:"次の20回のクイズ正解でコイン +50%",medals:3}];return `<div class="card"><b class="icon-label">${ico("medal",18)} 学習メダル交換所</b><div class="shop-note">学習25回ごとにメダルを1枚獲得します。獲得済み ${medalsEarned()}枚 ／ 使用済み ${shopData.medalsSpent}枚。</div><div class="shop-grid">${products.map(t=>{const theme=EXCHANGE_THEMES.some(x=>x.id===t.id),owned=theme&&shopData.ownedThemes.includes(t.id);return shopProduct({icon:t.icon,name:t.name,desc:t.desc,price:`${ico("medal",15)} ${t.medals}枚`,button:owned?"交換済み":"交換",disabled:owned||medalsAvailable()<t.medals,action:`buyExchangeItem('${t.id}')`,tag:owned?"所持済み":"",swatch:t.swatch})}).join("")}</div></div>`}
function rInventoryHtml(){const inv=shopData.inventory,rows=[...SHOP_ITEMS.map(i=>({id:i.id,name:i.name,desc:i.desc,icon:i.icon,count:Number(inv[i.id])||0})),{id:"theme",name:"所持テーマ",desc:"購入済みのテーマ",icon:"palette",count:shopData.ownedThemes.length}];return `<div class="card"><b class="icon-label">${ico("backpack",18)} 所持品</b><div class="shop-note">${shopData.reviewRemaining?`復習モード残り ${shopData.reviewRemaining} 問。`:""}${shopData.xpBoostRemaining?`XPブースター残り ${shopData.xpBoostRemaining} 回。`:""}${shopData.coinBoostRemaining?`コインブースター残り ${shopData.coinBoostRemaining} 回。`:""}</div><div class="shop-grid">${rows.map(r=>{if(r.id==="theme")return shopProduct({icon:r.icon,name:r.name,desc:`${r.count}種類を所持。適用中：${THEME_NAMES[shopData.theme]||"システム設定"}`,price:"",button:"テーマを見る",action:"shopTab='custom';rShop()"});const active=r.id==="reviewTicket"&&shopData.reviewRemaining>0||r.id==="xpBoost"&&shopData.xpBoostRemaining>0||r.id==="coinBoost"&&shopData.coinBoostRemaining>0;return shopProduct({icon:r.icon,name:r.name,desc:r.desc,price:`所持数：${r.count}${active?" ／ 使用中":""}`,button:r.id==="hintTicket"?"クイズを開く":active?"使用中": "使用",disabled:r.count<=0||active,action:r.id==="hintTicket"?"activeStudyMode='all';setTab('quiz')":`useInventoryItem('${r.id}')`,tag:active?"使用中":""})}).join("")}</div></div>`}
function rUpHtml(){return `<div class="card"><b class="icon-label">${ico("star",18)} ステータス強化</b><div class="shop-note">強化すると効果が上がります。</div>${SHOP.map(s=>{const lv=U(s.id),c=upCost(s),mx=lv>=s.max;return`<div class="shop"><div class="si"><b>${s.n}</b> <span class="box">Lv ${lv} / ${s.max}</span><div class="box" style="margin-top:3px">${lv?s.fx(lv):"未強化"}${mx?"":" → "+s.fx(lv+1)}</div></div><button class="btn pri" style="flex:none;min-width:96px" ${mx||prof.coins<c?"disabled":""} onclick="buy('${s.id}')">${mx?"最大":ico("coins",16,"coin-mark")+" "+c}</button></div>`}).join("")}</div>`}
function rDexHtml(){
 const RN={N:"N",R:"R",S:"SR"},pre=gcat==="pre",cp=gpool(),n=cp.filter(p=>gz.owned.includes(p.w)).length,c1=costOf(1),c10=costOf(10);
 return `<div class="card"><b class="icon-label">${ico("sparkle",18)} 単語ガチャ</b>
    <div class="chips">${UNITS.slice(1).map(U=>{const[a,b]=unitCount(U.u);return`<button class="chip ${U.u===gcat?"on":""}" onclick="gcat=${U.u};pulled=[];dexMsg='';rShop()">Unit ${U.u} <small>${a}/${b}</small></button>`}).join("")}<button class="chip pre ${pre?"on":""}" onclick="gcat='pre';pulled=[];dexMsg='';rShop()">プレミアム</button></div>
    <div class="hint">${pre?"プレミアムガチャ":"Unit "+gcat+" ガチャ"}｜開放済み ${n}/${cp.length}語。重複時はコインに還元されます。</div>
    <div class="row"><button class="btn pri" ${prof.coins<c1?"disabled":""} onclick="draw(1)"><span class="icon-label">1回 ${ico("coins",16,"coin-mark")} ${c1}</span></button><button class="btn pri" ${prof.coins<c10?"disabled":""} onclick="draw(10)"><span class="icon-label">10連 ${ico("coins",16,"coin-mark")} ${c10}</span></button></div>
    ${dexMsg?`<div class="toast">${dexMsg}</div>`:""}${pulled.length?`<div class="res">${pulled.map(p=>`<div class="g ${p.r}"><b>${esc(p.w)}</b><span>${esc(p.m)}</span><i>${RN[p.r]} ${p.isNew?"NEW":"重複 +"+ico("coins",13,"coin-mark")+REF[p.r]}</i></div>`).join("")}</div>`:""}</div>`;
}
function buy(id){
  const s=SHOP.find(x=>x.id===id);if(!s)return;const lv=U(id),c=upCost(s);
  if(lv>=s.max||prof.coins<c)return;
  prof.coins-=c;prof.up=prof.up||{};prof.up[id]=lv+1;saveProf();hud();sfx("up");rShop();
}
function unitCount(u){const l=POOL.filter(p=>p.u===u);return[l.filter(p=>gz.owned.includes(p.w)).length,l.length]}
function sumCard(){
  const c=l=>words.filter(x=>l.includes(x.box)).length,have=new Set(words.map(x=>x.w.toLowerCase()));
  const t=[["総単語数",words.length],["習得済み (Lv5)",c([5])],["学習中 (Lv2〜4)",c([2,3,4])],["未学習 (Lv1)",c([1])],["ガチャ開放",gz.owned.length+" / "+POOL.length],["習得率",(words.length?Math.round(c([5])/words.length*100):0)+"%"]];
  const bars=UNITS.map(U=>{const a=U.list.filter(x=>have.has(x.w.toLowerCase())).length,b=U.list.length;return`<div class="bar"><span class="l">Unit ${U.u}</span><span class="t"><i style="width:${a/b*100}%"></i></span><span>${a}/${b}</span></div>`}).join("");
  return `<div class="card"><b class="icon-label">${ico("chart",18)} 単語帳サマリー</b><div class="stile">${t.map(([l,v])=>`<div><b>${v}</b><span>${l}</span></div>`).join("")}</div><div style="margin-top:14px"><b>ユニット別の開放状況</b>${bars}<div class="bar"><span class="l">ユニット外</span><span style="flex:1"></span><span>${words.filter(x=>!x.u).length}語</span></div></div></div>`;
}
function srcOf(x){
  const e=UNITW.get(nk(x.w));
  if(!e||!e.s)return"ユニット外（"+(x.g!==undefined?gnm(x.g):"自分で追加した単語")+"）";
  const g={};e.s.split(",").forEach(t=>{const[u,p]=t.split(".");(g[u]=g[u]||[]).push(p)});
  return Object.entries(g).map(([u,ps])=>`ENRICH II Unit ${u} ／ Reading 1 学習ノート Part ${ps.join("・")}`).join("　＋　");
}
function renameG(g){const v=$("gn"+g).value.trim().slice(0,30);if(v)gnames[g]=v;else delete gnames[g];saveGn();openG=g;rList()}
let og={},GS=[];
function groups(){
  const row=(x,i)=>`<li class="${x.off?"off":""}"><label class="sw" aria-label="出題のON/OFF"><input type="checkbox" ${x.off?"":"checked"} onchange="togW(${i},this.checked)"><i></i></label><div><b>${esc(x.w)}</b><span>${esc(x.m)}</span></div><span class="box">Lv${x.box}</span><button class="del" onclick="delWord(${i})" aria-label="削除">削除</button></li>`;
  const gl=[...new Set(words.filter(x=>!x.u&&x.g!==undefined).map(x=>x.g))].sort((a,b)=>a-b);
  const cu=gl.map((g,k)=>({t:gnm(g),f:x=>!x.u&&x.g===g,o:g===openG||k===gl.length-1,g}));
  if(!cu.length)cu.push({t:"ユニット外の単語（取り込み・手入力）",f:x=>!x.u,o:true});
  const gs=[...UNITS.map(U=>({t:"Unit "+U.u,f:x=>x.u===U.u,o:false})),...cu];GS=gs;
  return gs.map((g,k)=>{let it=words.map((x,i)=>[x,i]).filter(([x])=>g.f(x)&&(!listSearch||x.w.toLowerCase().includes(listSearch.toLowerCase())||x.m.toLowerCase().includes(listSearch.toLowerCase())));
    if(listSort==="lvup")it.sort((a,b)=>a[0].box-b[0].box);
    if(listSort==="lvdown")it.sort((a,b)=>b[0].box-a[0].box);
    if(listSort==="az")it.sort((a,b)=>a[0].w.localeCompare(b[0].w));if(!it.length&&!g.o)return"";
    const on=it.filter(([x])=>!x.off).length,open=og[k]!==undefined?og[k]:g.o;
    const ren=g.g!==undefined?`<div class="row" style="margin:8px 0"><input id="gn${g.g}" value="${esc(gnm(g.g))}" maxlength="30" style="margin:0" aria-label="グループ名"><button class="btn" style="flex:none" onclick="renameG(${g.g})">名前を保存</button></div>`:"";
    const bulk=it.length?`<div class="row" style="margin:8px 0 0"><button class="btn" onclick="togG(${k},true)">このグループを全てON</button><button class="btn" onclick="togG(${k},false)">全てOFF</button></div>`:"";
    return`<details ${open?"open":""} ontoggle="og[${k}]=this.open" style="margin-top:12px"><summary><b>${esc(g.t)}</b> <span class="box">${it.length}${g.g!==undefined?"/100":""}語 ／ 出題 ${on}</span></summary>${ren}${bulk}<ul>${it.length?it.map(([x,i])=>row(x,i)).join(""):"<li><span>まだありません。「取り込み」から追加できます。</span></li>"}</ul></details>`}).join("");
}
function keepScroll(fn){const y=window.scrollY;fn();window.scrollTo(0,y)}
function setOff(x,v){if(v)delete x.off;else x.off=true}
function togW(i,v){setOff(words[i],v);save();keepScroll(rList)}
function togG(k,v){words.filter(GS[k].f).forEach(x=>setOff(x,v));save();keepScroll(rList)}
function setAll(v){words.forEach(x=>setOff(x,v));save();keepScroll(rList)}
function rList(){
  const n=words.length,m=words.filter(x=>!x.off).length;
  $("app").innerHTML=`${sumCard()}<div class="card" style="margin-top:12px"><b class="icon-label">${ico("book",18)} 単語を追加</b>
    <input id="nw" placeholder="英単語 (例: reliable)" autocapitalize="none">
    <input id="nm" placeholder="意味 (例: 信頼できる)">
    <div class="row"><button class="btn pri" onclick="addWord()">追加</button></div></div>
    <div class="card" style="margin-top:12px"><b class="icon-label">${ico("scan",18)} 単語を検索・並べ替え</b>
    <div class="listtools"><input value="${esc(listSearch)}" placeholder="英単語・意味で検索" oninput="listSearch=this.value;rList()">
    <select onchange="listSort=this.value;rList()"><option value="default" ${listSort==="default"?"selected":""}>通常順</option><option value="lvup" ${listSort==="lvup"?"selected":""}>Lvが低い順</option><option value="lvdown" ${listSort==="lvdown"?"selected":""}>Lvが高い順</option><option value="az" ${listSort==="az"?"selected":""}>英単語 A→Z</option></select></div></div>
    <div class="card" style="margin-top:12px"><b class="icon-label">${ico("target",18)} 出題範囲</b>
    <div class="hint">スイッチをONにした単語だけが、学習・クイズで出題されます。現在 <b>${m} / ${n}語</b> が出題対象です。</div>
    <div class="row"><button class="btn" onclick="setAll(true)">全てON</button><button class="btn" onclick="setAll(false)">全てOFF</button></div>
    ${groups()}</div>`;
  sbInfo();
}
function addWord(){
  const w=$("nw").value.trim(),m=$("nm").value.trim();
  if(!w||!m)return;
  words.push(mkWord(w,m));save();rList();
}
function delWord(i){words.splice(i,1);save();cur=null;quiz=null;rList()}
function changeAchievementPage(delta){
 const pages=Math.max(1,Math.ceil(achievementDefs().length/10));
 achievementPage=Math.max(1,Math.min(pages,achievementPage+delta));
 rStats();
}
function missionHtml(){
 const defs=achievementDefs(),pages=Math.max(1,Math.ceil(defs.length/10));
 achievementPage=Math.max(1,Math.min(pages,achievementPage));
 const unlockedCount=defs.filter(a=>achievements.includes(a.id)).length;
 const visible=defs.slice((achievementPage-1)*10,achievementPage*10);
 return `<div class="hint">達成済み ${unlockedCount} / ${defs.length}　各実績は一度だけ報酬を受け取れます。10個ずつ表示しています。</div><div class="achievement-list">`+
 visible.map(a=>{const unlocked=achievements.includes(a.id);return `<div class="achievement-row ${unlocked?"unlocked":""}"><div class="achievement-icon">${unlocked?ico("award",22):ico("lock",22)}</div><div><div class="achievement-title">${esc(a.title)}</div><div class="achievement-desc">${esc(a.desc)}</div><div class="achievement-reward">報酬：+${a.xp} XP / +${ico("coins",14,"coin-mark")}${a.coins}${unlocked?`　${ico("checkCircle",14)} 達成済み`:`　未達成`}</div></div></div>`}).join("")+`</div><div class="row" style="align-items:center;justify-content:center;gap:10px;margin-top:14px"><button class="btn" onclick="changeAchievementPage(-1)" ${achievementPage<=1?"disabled":""}>前の10個</button><b style="padding:0 4px">${achievementPage} / ${pages} ページ</b><button class="btn" onclick="changeAchievementPage(1)" ${achievementPage>=pages?"disabled":""}>次の10個</button></div>`;
}
function challengeQuestion(){
 const pool=words.map((w,i)=>({w,i})).filter(o=>!o.w.off);
 if(pool.length<4){challenge.question=null;return}
 const chosen=pool[Math.floor(Math.random()*pool.length)],others=pool.filter(o=>o.i!==chosen.i&&o.w.m!==chosen.w.m).sort(()=>Math.random()-.5).slice(0,3);
 challenge.question={i:chosen.i,opts:[chosen,...others].sort(()=>Math.random()-.5).map(o=>o.i)};
}
function startChallenge(){
 if(challenge.interval)clearInterval(challenge.interval);
 challenge={active:true,left:60,score:0,question:null,interval:null};challengeQuestion();
 challenge.interval=setInterval(()=>{challenge.left--;if(challenge.left<=0){clearInterval(challenge.interval);challenge.interval=null;challenge.active=false;if(challenge.score>timerData.best){timerData.best=challenge.score;try{localStorage.setItem(TK,JSON.stringify(timerData))}catch(e){}}checkAchievements();saveProf()}rChallenge()},1000);
 rChallenge();
}
function challengeAnswer(k){
 if(!challenge.active||!challenge.question)return;
 const ok=k===challenge.question.i;
 if(ok){challenge.score++;prof.xp+=5;prof.coins+=2;grade(k,true);sfx("ok")}else{sfx("ng");grade(k,false)}
 markStudy();checkAchievements();saveProf();challengeQuestion();rChallenge();
}
function rChallenge(){
 const q=challenge.question;
 $("app").innerHTML=`<div class="card"><b class="icon-label">${ico("timer",18)} 60秒チャレンジ</b><div class="hint">60秒以内の正解数を記録します。正解ごとに +5 XP、+2コイン。</div>
 <div class="stile"><div><b>${challenge.active?challenge.left:60}</b><span>残り秒数</span></div><div><b>${challenge.active?challenge.score:0}</b><span>今回の正解数</span></div><div><b>${timerData.best}</b><span>ハイスコア</span></div><div><b>目標 10回/日</b><span>今日 ${todayCount()}回</span></div></div>
 ${challenge.active&&q?`<div class="timerbar"><i style="width:${challenge.left/60*100}%"></i></div><div class="challengeQ">${esc(words[q.i].w)}</div><div class="opts">${q.opts.map(k=>`<button class="btn opt" onclick="challengeAnswer(${k})">${esc(words[k].m)}</button>`).join("")}</div>`:`<div class="challengeQ">${challenge.left<=0?"チャレンジ終了！":"準備OK？"}</div><div class="hint" style="text-align:center">ベストスコア：${timerData.best}問</div><div class="row"><button class="btn pri icon-label" onclick="startChallenge()">${ico("timer",18)} ${challenge.left<=0?"もう一度挑戦":"スタート"}</button></div>`}
 </div>`;
}
function saveMarathonData(){try{localStorage.setItem(MK,JSON.stringify(marathonData))}catch(e){}}
function marathonQuestion(){
 const all=words.map((w,i)=>({w,i})).filter(o=>!o.w.off);
 if(all.length<4){marathon.question=null;return false}
 // 進行度に応じて、まだ定着していない単語を優先して出題する
 const cutoff=marathon.score>=25?2:marathon.score>=10?3:5;
 let pool=all.filter(o=>o.w.box<=cutoff);
 if(pool.length<4)pool=all;
 const recent=new Set(marathon.recent.slice(-Math.min(5,Math.max(0,pool.length-1))));
 let candidates=pool.filter(o=>!recent.has(o.i));
 if(!candidates.length)candidates=pool;
 const chosen=candidates[Math.floor(Math.random()*candidates.length)];
 const others=all.filter(o=>o.i!==chosen.i).sort(()=>Math.random()-.5).slice(0,3);
 if(others.length<3){marathon.question=null;return false}
 marathon.question={i:chosen.i,opts:[chosen,...others].sort(()=>Math.random()-.5).map(o=>o.i)};
 marathon.recent.push(chosen.i);if(marathon.recent.length>6)marathon.recent.shift();
 return true;
}
function startMarathon(){
 const active=words.filter(w=>!w.off);
 if(active.length<4){marathon={active:false,score:0,question:null,recent:[],last:{message:"出題対象の単語を4語以上ONにしてください。"}};rMarathon();return}
 marathon={active:true,score:0,question:null,recent:[],last:null};
 if(!marathonQuestion()){marathon.active=false;marathon.last={message:"問題を作成できませんでした。出題対象の単語を確認してください。"}}
 rMarathon();
}
function marathonAnswer(k){
 if(!marathon.active||!marathon.question)return;
 const q=marathon.question,word=words[q.i],ok=k===q.i;
 markStudy();
 if(ok){
  marathon.score++;marathonData.totalCorrect++;
  if(marathon.score>marathonData.best)marathonData.best=marathon.score;
  saveMarathonData();
  prof.xp+=5;prof.coins+=2;grade(k,true);sfx("ok");
  marathonQuestion();checkAchievements();saveProf();hud();rMarathon();
 }else{
  grade(q.i,false);sfx("ng");marathonData.runs++;saveMarathonData();
  marathon.active=false;marathon.question=null;
  marathon.last={message:"不正解でラン終了",score:marathon.score,wrong:word.w,correct:word.m};
  checkAchievements();saveProf();rMarathon();
 }
}
function rMarathon(){
 const q=marathon.question;
 const usable=words.filter(w=>!w.off).length;
 const body=marathon.active&&q
  ?`<div class="stile"><div><b>${marathon.score}</b><span>連続正解</span></div><div><b>${marathonData.best}</b><span>自己ベスト</span></div><div><b>${marathonData.runs}</b><span>ラン終了回数</span></div><div><b>${marathonData.totalCorrect}</b><span>累計正解数</span></div></div><div class="challengeQ">${esc(words[q.i].w)}</div><div class="hint" style="text-align:center">${marathon.score>=25?"出題：難しめ":"出題：通常"} ／ 正解 +5 XP・+2コイン</div><div class="opts">${q.opts.map(k=>`<button class="btn opt" onclick="marathonAnswer(${k})">${esc(words[k].m)}</button>`).join("")}</div><div class="row"><button class="btn" onclick="endMarathonManually()">記録を保存して終了</button></div>`
  :`<div class="stile"><div><b>${marathonData.best}</b><span>自己ベスト</span></div><div><b>${marathonData.runs}</b><span>ラン終了回数</span></div><div><b>${marathonData.totalCorrect}</b><span>累計正解数</span></div><div><b>${usable}</b><span>出題対象の単語</span></div></div><div class="challengeQ">${marathon.last&&marathon.last.score!==undefined?`ラン終了：${marathon.last.score}問連続正解`:marathon.last?esc(marathon.last.message):"準備OK？"}</div>${marathon.last&&marathon.last.wrong?`<div class="toast">出題：${esc(marathon.last.wrong)} ／ 正解：${esc(marathon.last.correct)}</div>`:""}<div class="hint" style="text-align:center">不正解で終了します。10問以上では定着度の低い単語を優先して出題します。</div><div class="row"><button class="btn pri icon-label" onclick="startMarathon()">${ico("route",18)} ${marathon.last&&marathon.last.score!==undefined?"もう一度挑戦":"マラソン開始"}</button></div>`;
 $("app").innerHTML=`<div class="card"><b class="icon-label">${ico("route",18)} マラソンモード</b><div class="hint">時間制限なし。不正解で終了します。正解ごとに +5 XP、+2コイン。</div>${body}<div class="card" style="margin-top:14px;padding:14px"><b class="icon-label">${ico("award",18)} マラソン実績</b><div class="hint">10 / 25 / 50 / 100 / 200問の連続正解で実績報酬を獲得。</div></div></div>`;
}
function endMarathonManually(){
 if(!marathon.active)return;
 marathonData.runs++;saveMarathonData();marathon.active=false;marathon.question=null;
 marathon.last={message:"ランを終了しました",score:marathon.score};checkAchievements();saveProf();rMarathon();
}
function rStats(){
  checkAchievements();
  const n=words.length,cnt=[1,2,3,4,5].map(b=>words.filter(x=>x.box===b).length);
  const mastered=cnt[4],pct=n?Math.round(mastered/n*100):0;
  const weekKeys=Array.from({length:7},(_,i)=>{const d=new Date();d.setDate(d.getDate()-(6-i));return `${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,"0")}-${String(d.getDate()).padStart(2,"0")}`});
  const weekTotal=weekKeys.reduce((a,k)=>a+(Number(daily[k])||0),0),weakN=words.filter(isWeak).length,dueN=words.filter(reviewDue).length;
  $("app").innerHTML=`<div class="card"><b class="icon-label">${ico("chart",18)} 学習分析</b><div class="analytics-grid"><div class="analytics-tile"><b>${todayCount()}</b><span>今日の回答数</span></div><div class="analytics-tile"><b>${weekTotal}</b><span>過去7日間の回答数</span></div><div class="analytics-tile"><b>${score.t?Math.round(score.c/score.t*100):0}%</b><span>セッション正答率</span></div><div class="analytics-tile"><b>${weakN}</b><span>苦手単語数</span></div><div class="analytics-tile"><b>${dueN}</b><span>復習対象</span></div><div class="analytics-tile"><b>${mastered}</b><span>定着単語数</span></div></div><div class="bar"><span class="l">過去7日</span><span class="t"><i style="width:${Math.min(100,weekTotal/Math.max(1,learningSettings.count*7)*100)}%"></i></span><span>${weekTotal}</span></div><div class="mode-row"><button class="btn" onclick="setTab('review')">復習</button><button class="btn" onclick="setTab('weak')">苦手単語</button><button class="btn" onclick="setTab('quiz')">クイズ</button></div></div><div class="card"><div class="box">${ico("chart",16)} 定着度（レベル5の割合）</div><div class="big">${pct}%</div>
    <div class="box">${mastered} / ${n} 語</div>
    ${cnt.map((c,i)=>`<div class="bar"><span class="l">レベル ${i+1}</span><span class="t"><i style="width:${n?c/n*100:0}%"></i></span><span>${c}</span></div>`).join("")}
    <div class="hint">「覚えた」「正解」でレベルUP、間違えるとレベル1に戻り、出題頻度が上がります。</div>
    <div class="row"><button class="btn" onclick="if(confirm('XP・コイン・ショップの強化・ガチャの開放状況・追加した単語をすべてリセットし、Unit 1のみの状態に戻します。よろしいですか？')){words=START();save();score={c:0,t:0};prof={xp:0,coins:0,combo:0};saveProf();gz={owned:[],pulls:0};saveGz();gnames={};saveGn();shopData=JSON.parse(JSON.stringify(SHOP_DEFAULTS));try{localStorage.removeItem(SHK)}catch(e){}applyShopTheme();hud();rStats()}">リセット</button></div></div>
    <div class="card" style="margin-top:12px"><b class="icon-label">${ico("trophy",18)} 実績（全${achievementDefs().length}種類）</b><div class="hint">実績を達成するとXPとコインを獲得できます。報酬は各実績1回のみです。</div>${missionHtml()}</div>`;
}
checkAchievements();
render();showTitle();
</script>
</body>
</html>
```
tanseat
