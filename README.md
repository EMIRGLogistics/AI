<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>EMIRG AI — Operational Intelligence</title>
<meta name="description" content="EMIRG AI maps your operations, integrates your tech, automates your workflows, and forecasts your demand. Measurable ROI in 60 days.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=Outfit:wght@300;400;500&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --black:   #000000;
  --bg:      #050507;
  --s1:      #0a0c0f;
  --s2:      #0f1115;
  --border:  #1a1d24;
  --border2: #252830;
  --dim:     #3a3f4a;
  --muted:   #5a6070;
  --soft:    #8090a0;
  --text:    #b0bcc8;
  --light:   #d8e4ee;
  --white:   #edf4fa;

  --blue:    #2563eb;
  --blue2:   #3b82f6;
  --blueglow:rgba(37,99,235,.12);
  --blueedge:rgba(37,99,235,.3);

  --green:   #16a34a;
  --green2:  #22c55e;
  --greenglow:rgba(34,197,94,.1);
  --greenedge:rgba(34,197,94,.28);

  --display: 'Syne', sans-serif;
  --body:    'Outfit', sans-serif;
  --mono:    'JetBrains Mono', monospace;
  --nav-h:   60px;
}
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;font-size:15px;}
body{font-family:var(--body);background:var(--bg);color:var(--text);overflow-x:hidden;-webkit-font-smoothing:antialiased;cursor:none;}
*{-webkit-tap-highlight-color:transparent;}
::-webkit-scrollbar{width:2px;}
::-webkit-scrollbar-thumb{background:var(--dim);}
a{color:inherit;text-decoration:none;}
button{font-family:var(--body);cursor:none;}
select,input,textarea{font-family:var(--body);}

/* CURSOR */
#cur{position:fixed;z-index:9999;pointer-events:none;width:7px;height:7px;border-radius:50%;background:var(--green2);top:0;left:0;transform:translate(-50%,-50%);transition:width .2s,height .2s,background .2s;mix-blend-mode:screen;}
#cur-r{position:fixed;z-index:9998;pointer-events:none;width:28px;height:28px;border-radius:50%;border:1px solid rgba(34,197,94,.3);top:0;left:0;transform:translate(-50%,-50%);transition:all .11s linear;}
#cur.big{width:16px;height:16px;background:var(--blue2);}

/* PROGRESS */
#pg{position:fixed;top:0;left:0;height:1.5px;background:linear-gradient(90deg,var(--blue),var(--green2));z-index:9997;width:0;}

/* NAV */
.nav{
  position:fixed;top:0;left:0;right:0;z-index:800;height:var(--nav-h);
  display:flex;align-items:center;justify-content:space-between;padding:0 44px;
  background:rgba(5,5,7,.92);backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
}
.nav-logo{display:flex;align-items:center;gap:10px;cursor:none;}
.logo-sq{
  width:34px;height:34px;background:var(--blue);border-radius:6px;
  display:flex;align-items:center;justify-content:center;
  font-family:var(--display);font-size:13px;font-weight:800;color:#fff;
  letter-spacing:.5px;flex-shrink:0;
}
.logo-name{font-family:var(--display);font-size:17px;font-weight:800;color:var(--white);letter-spacing:.5px;}
.nav-links{display:flex;gap:0;}
.nl{padding:7px 13px;font-size:12.5px;font-weight:400;color:var(--muted);background:none;border:none;cursor:none;border-radius:5px;transition:color .2s;}
.nl:hover,.nl.on{color:var(--light);}
.nav-btn{
  padding:8px 20px;background:var(--green);color:#fff;border-radius:7px;
  font-size:12.5px;font-weight:500;border:none;cursor:none;
  transition:all .2s;white-space:nowrap;letter-spacing:.1px;
}
.nav-btn:hover{background:var(--green2);}
.ham{display:none;flex-direction:column;gap:4px;background:none;border:none;cursor:none;padding:7px;}
.ham span{width:18px;height:1.5px;background:var(--muted);display:block;border-radius:1px;transition:all .25s;}

/* MOBILE DRAWER */
.mob-nav{
  position:fixed;top:0;right:-100%;bottom:0;z-index:900;
  width:min(260px,80vw);background:var(--s1);border-left:1px solid var(--border);
  padding:80px 24px 40px;transition:right .32s cubic-bezier(.16,1,.3,1);
  display:flex;flex-direction:column;gap:4px;
}
.mob-nav.open{right:0;}
.mob-x{position:absolute;top:16px;right:16px;background:none;border:none;color:var(--muted);font-size:20px;cursor:none;padding:6px;}
.mob-nav .nl{font-size:17px;padding:12px 0;border-bottom:1px solid var(--border);width:100%;border-radius:0;color:var(--soft);}
.mob-nav .nav-btn{margin-top:18px;width:100%;padding:13px;font-size:14px;text-align:center;display:block;}
.mob-ov{position:fixed;inset:0;z-index:850;background:rgba(0,0,0,.8);display:none;}
.mob-ov.open{display:block;}

/* HERO */
#s-hero{min-height:100svh;padding-top:var(--nav-h);display:flex;align-items:center;position:relative;overflow:hidden;}
.hero-grid{
  position:absolute;inset:0;pointer-events:none;
  background-image:linear-gradient(rgba(37,99,235,.035) 1px,transparent 1px),linear-gradient(90deg,rgba(37,99,235,.035) 1px,transparent 1px);
  background-size:48px 48px;
}
canvas#dots{position:absolute;inset:0;width:100%;height:100%;pointer-events:none;}
.hero-inner{
  max-width:1200px;margin:0 auto;width:100%;padding:80px 44px;
  position:relative;z-index:1;
  display:grid;grid-template-columns:1fr 1fr;gap:64px;align-items:center;
}
.hero-tag{
  display:inline-flex;align-items:center;gap:8px;
  font-family:var(--mono);font-size:10px;letter-spacing:2.5px;text-transform:uppercase;
  color:var(--green2);margin-bottom:22px;
  animation:up .6s .1s both;
}
.hero-tag::before{content:'';width:22px;height:1px;background:var(--green2);}
h1.hero-h{
  font-family:var(--display);font-weight:800;
  font-size:clamp(52px,7.5vw,96px);line-height:.9;
  letter-spacing:-2px;color:var(--white);margin-bottom:22px;
  animation:up .6s .18s both;
}
h1.hero-h .b{color:var(--blue2);}
h1.hero-h .g{color:var(--green2);}
.hero-sub{
  font-size:16px;color:var(--muted);line-height:1.8;max-width:460px;
  margin-bottom:32px;animation:up .6s .26s both;
}
.hero-sub strong{color:var(--text);font-weight:500;}
.hero-btns{display:flex;gap:10px;flex-wrap:wrap;animation:up .6s .34s both;}
.hero-stats{
  display:flex;gap:0;margin-top:44px;padding-top:36px;border-top:1px solid var(--border);
  animation:up .6s .42s both;flex-wrap:wrap;
}
.hst{flex:1;min-width:80px;padding-right:20px;margin-right:20px;border-right:1px solid var(--border);}
.hst:last-child{border-right:none;margin-right:0;padding-right:0;}
.hst-n{font-family:var(--display);font-size:32px;font-weight:800;color:var(--white);line-height:1;letter-spacing:-1px;margin-bottom:3px;}
.hst-n .a{color:var(--green2);}
.hst-l{font-family:var(--mono);font-size:9px;color:var(--dim);letter-spacing:1px;text-transform:uppercase;}

/* HERO RIGHT — terminal */
.terminal{
  background:var(--s1);border:1px solid var(--border);border-radius:12px;
  overflow:hidden;box-shadow:0 24px 64px rgba(0,0,0,.5);
  animation:up .6s .28s both;
}
.term-top{
  background:var(--s2);padding:10px 16px;border-bottom:1px solid var(--border);
  display:flex;align-items:center;gap:10px;
}
.tdots{display:flex;gap:5px;}
.td{width:9px;height:9px;border-radius:50%;}
.t-label{flex:1;text-align:center;font-family:var(--mono);font-size:9px;letter-spacing:2px;text-transform:uppercase;color:var(--dim);}
.t-live{display:flex;align-items:center;gap:6px;font-family:var(--mono);font-size:8.5px;color:var(--green2);letter-spacing:1px;}
.lpulse{width:6px;height:6px;border-radius:50%;background:var(--green2);animation:glow 1.8s infinite;}
@keyframes glow{0%,100%{box-shadow:0 0 0 0 rgba(34,197,94,.4)}50%{box-shadow:0 0 0 5px rgba(34,197,94,0)}}
.term-body{padding:16px;font-family:var(--mono);font-size:11.5px;line-height:2;}
.tc-p{color:rgba(34,197,94,.5);}
.tc-ok{color:var(--green2);}
.tc-b{color:var(--blue2);}
.tc-w{color:#f59e0b;}
.tc-r{color:#ef4444;}
.tc-d{color:var(--dim);}
.tc-t{color:var(--text);}
.tc-cur{display:inline-block;width:6px;height:11px;background:var(--green2);vertical-align:middle;animation:blink .9s steps(1) infinite;}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.term-foot{
  background:var(--s2);padding:10px 16px;border-top:1px solid var(--border);
  display:grid;grid-template-columns:repeat(3,1fr);
}
.tf{text-align:center;padding:6px 0;}
.tf:not(:last-child){border-right:1px solid var(--border);}
.tf-n{font-family:var(--display);font-size:22px;font-weight:800;line-height:1;margin-bottom:3px;}
.tf-l{font-family:var(--mono);font-size:8px;color:var(--muted);letter-spacing:1px;text-transform:uppercase;}

@keyframes up{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}

/* TICKER */
.ticker{overflow:hidden;background:var(--s1);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:11px 0;}
.tick-inner{display:flex;white-space:nowrap;animation:tick 38s linear infinite;}
.tk{display:inline-flex;align-items:center;gap:8px;padding:0 24px;font-family:var(--mono);font-size:9.5px;color:var(--dim);}
.tk .tv{color:var(--blue2);}
@keyframes tick{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}

/* BUTTONS */
.btn-g{display:inline-flex;align-items:center;gap:7px;padding:12px 28px;background:var(--green);color:#fff;border-radius:7px;font-size:14px;font-weight:500;border:none;cursor:none;transition:all .2s;white-space:nowrap;}
.btn-g:hover{background:var(--green2);transform:translateY(-1px);box-shadow:0 6px 24px rgba(34,197,94,.22);}
.btn-o{display:inline-flex;align-items:center;gap:7px;padding:12px 28px;background:transparent;color:var(--light);border-radius:7px;font-size:14px;font-weight:400;border:1px solid var(--border2);cursor:none;transition:all .2s;white-space:nowrap;}
.btn-o:hover{border-color:var(--soft);}
.btn-b{display:inline-flex;align-items:center;gap:7px;padding:12px 28px;background:var(--blue);color:#fff;border-radius:7px;font-size:14px;font-weight:500;border:none;cursor:none;transition:all .2s;white-space:nowrap;}
.btn-b:hover{background:var(--blue2);transform:translateY(-1px);}

/* LAYOUT */
.wrap{max-width:1200px;margin:0 auto;padding:0 44px;}
.sec{padding:96px 0;}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
.g3{display:grid;grid-template-columns:repeat(3,1fr);gap:16px;}
.g4{display:grid;grid-template-columns:repeat(4,1fr);gap:0;}
.split{display:grid;grid-template-columns:1fr 1fr;gap:64px;align-items:center;}
.split.top{align-items:start;}
.col{display:flex;flex-direction:column;}

/* LABELS */
.tag{
  display:inline-flex;align-items:center;gap:8px;
  font-family:var(--mono);font-size:9px;letter-spacing:2.5px;text-transform:uppercase;
  color:var(--blue2);margin-bottom:14px;
}
.tag::before{content:'';width:16px;height:1px;background:var(--blue2);flex-shrink:0;}
.tag.g{color:var(--green2);}
.tag.g::before{background:var(--green2);}

/* HEADINGS */
.h1{font-family:var(--display);font-weight:800;font-size:clamp(40px,5.5vw,72px);line-height:.92;letter-spacing:-1.5px;color:var(--white);}
.h1 .b{color:var(--blue2);}
.h1 .g{color:var(--green2);}
.h2{font-family:var(--display);font-weight:800;font-size:clamp(26px,3.5vw,44px);line-height:.95;letter-spacing:-1px;color:var(--white);}
.h2 .b{color:var(--blue2);}
.h2 .g{color:var(--green2);}
.body{font-size:15px;color:var(--muted);line-height:1.8;}
.body strong{color:var(--text);font-weight:500;}

/* REVEAL */
.rv{opacity:0;transform:translateY(22px);transition:opacity .65s cubic-bezier(.16,1,.3,1),transform .65s cubic-bezier(.16,1,.3,1);}
.rv.in{opacity:1;transform:none;}
.d1{transition-delay:.07s;}.d2{transition-delay:.14s;}.d3{transition-delay:.21s;}.d4{transition-delay:.28s;}

/* DIVIDER */
.div{width:100%;height:1px;background:var(--border);}

/* CARDS */
.card{background:var(--s1);border:1px solid var(--border);border-radius:10px;padding:24px;transition:border-color .25s,transform .25s;}
.card:hover{border-color:var(--border2);transform:translateY(-2px);}

/* SERVICES GRID */
.svc-grid{display:grid;grid-template-columns:1fr 1fr;gap:1px;background:var(--border);border:1px solid var(--border);border-radius:12px;overflow:hidden;}
.svc{background:var(--s1);padding:36px 32px;position:relative;overflow:hidden;transition:background .25s;}
.svc:hover{background:var(--s2);}
.svc-num{position:absolute;right:18px;bottom:10px;font-family:var(--display);font-size:100px;font-weight:800;color:rgba(255,255,255,.018);line-height:1;pointer-events:none;}
.svc-ico{font-size:24px;margin-bottom:14px;}
.svc-title{font-family:var(--display);font-size:24px;font-weight:800;color:var(--white);letter-spacing:-.5px;margin-bottom:10px;line-height:1;}
.svc-body{font-size:13px;color:var(--muted);line-height:1.75;max-width:320px;}
.svc-list{margin-top:14px;display:flex;flex-direction:column;gap:5px;}
.sl{font-size:12px;color:var(--dim);display:flex;gap:7px;align-items:flex-start;}
.sl::before{content:'›';color:var(--blue2);flex-shrink:0;}
.chip{display:inline-block;padding:3px 10px;border-radius:20px;font-family:var(--mono);font-size:8.5px;letter-spacing:1px;text-transform:uppercase;margin-top:14px;}
.chip-g{background:var(--greenglow);border:1px solid var(--greenedge);color:var(--green2);}
.chip-b{background:var(--blueglow);border:1px solid var(--blueedge);color:var(--blue2);}
.chip-d{background:rgba(255,255,255,.03);border:1px solid var(--border);color:var(--muted);}

/* RESULTS BAR */
.results-band{background:var(--s1);border-top:1px solid var(--border);border-bottom:1px solid var(--border);}
.rb-inner{display:grid;grid-template-columns:repeat(4,1fr);gap:0;}
.rb-cell{padding:36px 28px;border-right:1px solid var(--border);}
.rb-cell:last-child{border-right:none;}
.rb-n{font-family:var(--display);font-size:50px;font-weight:800;line-height:1;letter-spacing:-2px;margin-bottom:7px;}
.rb-l{font-size:13px;color:var(--muted);line-height:1.5;}

/* PROCESS */
.proc-item{border-bottom:1px solid var(--border);}
.proc-btn{width:100%;display:flex;align-items:center;gap:16px;padding:20px 0;background:none;border:none;cursor:none;text-align:left;}
.proc-btn:hover .pn{color:var(--blue2);}
.pn{font-family:var(--display);font-size:44px;font-weight:800;color:var(--border2);line-height:1;width:52px;flex-shrink:0;letter-spacing:-2px;transition:color .25s;}
.pt{font-family:var(--display);font-size:22px;font-weight:800;color:var(--light);flex:1;letter-spacing:-.3px;}
.pa{font-size:18px;color:var(--blue2);transition:transform .3s;flex-shrink:0;}
.proc-item.open .pa{transform:rotate(90deg);}
.proc-item.open .pn{color:var(--blue2);}
.proc-body{max-height:0;overflow:hidden;transition:max-height .4s cubic-bezier(.16,1,.3,1);}
.proc-in{padding:0 0 20px 68px;font-size:13.5px;color:var(--muted);line-height:1.8;max-width:560px;}
.proc-chips{display:flex;gap:7px;flex-wrap:wrap;margin-top:10px;}

/* ROI CALC */
.calc{background:var(--s1);border:1px solid var(--border);border-radius:12px;overflow:hidden;}
.calc-head{background:var(--s2);padding:16px 22px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.calc-title{font-family:var(--display);font-size:19px;font-weight:800;color:var(--white);letter-spacing:-.3px;}
.calc-live{display:flex;align-items:center;gap:6px;font-family:var(--mono);font-size:8.5px;color:var(--green2);letter-spacing:1.5px;text-transform:uppercase;}
.calc-body{padding:22px;}
.sl-g{margin-bottom:18px;}
.sl-l{font-family:var(--mono);font-size:9px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:9px;display:flex;justify-content:space-between;}
.sl-v{color:var(--blue2);font-weight:500;}
input[type=range]{width:100%;-webkit-appearance:none;appearance:none;height:3px;background:var(--border2);border-radius:2px;outline:none;cursor:none;}
input[type=range]::-webkit-slider-thumb{-webkit-appearance:none;width:16px;height:16px;border-radius:50%;background:var(--blue);cursor:none;box-shadow:0 0 10px rgba(37,99,235,.4);}
input[type=range]::-moz-range-thumb{width:16px;height:16px;border-radius:50%;background:var(--blue);cursor:none;border:none;}
.calc-out{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:6px;}
.co{background:var(--s2);border:1px solid var(--border);border-radius:8px;padding:14px;text-align:center;}
.co-n{font-family:var(--display);font-size:26px;font-weight:800;line-height:1;margin-bottom:4px;}
.co-l{font-family:var(--mono);font-size:8.5px;color:var(--muted);letter-spacing:.8px;text-transform:uppercase;line-height:1.4;}
.calc-note{margin-top:12px;font-family:var(--mono);font-size:9px;color:var(--dim);text-align:center;letter-spacing:.5px;}

/* FAQ */
.faq-item{border-bottom:1px solid var(--border);}
.faq-btn{width:100%;display:flex;align-items:center;justify-content:space-between;padding:18px 0;background:none;border:none;cursor:none;text-align:left;}
.faq-q{font-family:var(--display);font-size:18px;font-weight:800;color:var(--light);letter-spacing:-.2px;}
.faq-ic{font-size:18px;color:var(--blue2);transition:transform .3s;margin-left:16px;flex-shrink:0;}
.faq-item.open .faq-ic{transform:rotate(45deg);}
.faq-ans{max-height:0;overflow:hidden;transition:max-height .4s cubic-bezier(.16,1,.3,1);}
.faq-in{padding-bottom:18px;font-size:13.5px;color:var(--muted);line-height:1.8;max-width:660px;}

/* TESTIMONIALS */
.tcard{background:var(--s1);border:1px solid var(--border);border-radius:10px;padding:26px;position:relative;}
.tcard-q{font-family:var(--display);font-size:72px;color:var(--blue2);opacity:.1;position:absolute;top:2px;left:14px;line-height:1;pointer-events:none;}
.tcard-text{font-style:italic;font-size:15px;color:var(--light);line-height:1.7;padding-top:18px;margin-bottom:16px;}
.tcard-line{width:24px;height:1px;background:var(--blueedge);margin-bottom:12px;}
.tcard-name{font-size:13px;font-weight:500;color:var(--text);margin-bottom:2px;}
.tcard-role{font-family:var(--mono);font-size:9px;color:var(--muted);letter-spacing:.8px;text-transform:uppercase;}

/* CTA */
.cta-sec{background:var(--s1);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:96px 44px;text-align:center;position:relative;overflow:hidden;}
.cta-glow{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:600px;height:600px;border-radius:50%;background:radial-gradient(ellipse,rgba(37,99,235,.06) 0%,transparent 68%);pointer-events:none;}

/* MODAL */
#modal{display:none;position:fixed;inset:0;z-index:9000;background:rgba(0,0,0,.85);backdrop-filter:blur(16px);align-items:center;justify-content:center;padding:20px;}
#mbox{background:var(--s1);border:1px solid var(--border);border-radius:14px;width:100%;max-width:520px;overflow:hidden;animation:mup .35s cubic-bezier(.16,1,.3,1);box-shadow:0 32px 80px rgba(0,0,0,.6);}
@keyframes mup{from{opacity:0;transform:scale(.96) translateY(12px)}to{opacity:1;transform:none}}
.m-top{background:var(--s2);padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.m-id{display:flex;align-items:center;gap:10px;}
.m-sq{width:30px;height:30px;background:var(--blue);border-radius:6px;display:flex;align-items:center;justify-content:center;font-family:var(--display);font-size:12px;font-weight:800;color:#fff;flex-shrink:0;}
.m-title{font-family:var(--display);font-size:16px;font-weight:800;color:var(--white);letter-spacing:-.2px;}
.m-sub{font-family:var(--mono);font-size:8.5px;color:var(--muted);letter-spacing:.8px;margin-top:1px;}
.m-x{background:none;border:none;color:var(--muted);font-size:20px;cursor:none;padding:4px 7px;border-radius:5px;}
.m-x:hover{color:var(--light);background:var(--border);}
.m-scroll{padding:22px 20px;max-height:76svh;overflow-y:auto;}
.m-desc{font-size:13px;color:var(--muted);line-height:1.7;margin-bottom:18px;}
.m-lbl{display:block;font-family:var(--mono);font-size:8.5px;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:6px;}
.m-inp{width:100%;padding:11px 13px;background:var(--s2);border:1px solid var(--border);border-radius:8px;color:var(--light);font-size:16px;outline:none;transition:border-color .2s;-webkit-appearance:none;appearance:none;margin-bottom:12px;}
.m-inp:focus{border-color:var(--blueedge);}
.m-inp::placeholder{color:var(--dim);}
.m-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;}
.m-row .m-inp{margin-bottom:0;}
.m-row-wrap{margin-bottom:12px;}
.m-submit{width:100%;padding:14px;margin-top:6px;background:var(--green);color:#fff;border:none;border-radius:8px;font-size:14px;font-weight:500;cursor:none;transition:background .2s;display:flex;align-items:center;justify-content:center;gap:7px;}
.m-submit:hover:not(:disabled){background:var(--green2);}
.m-submit:disabled{opacity:.5;}
.m-err{display:none;padding:9px 12px;background:rgba(239,68,68,.07);border:1px solid rgba(239,68,68,.2);border-radius:7px;font-size:12.5px;color:#ef4444;margin-bottom:12px;}
.m-foot{text-align:center;font-family:var(--mono);font-size:9px;color:var(--dim);margin-top:10px;letter-spacing:.5px;}
.m-success{display:none;text-align:center;padding:16px 0;}
.m-s-ico{font-size:40px;margin-bottom:12px;}
.m-s-h{font-family:var(--display);font-size:24px;font-weight:800;color:var(--white);margin-bottom:6px;}
.m-s-b{font-size:13px;color:var(--muted);line-height:1.65;}
.m-s-close{margin-top:18px;padding:11px 30px;background:var(--green);color:#fff;border:none;border-radius:7px;font-size:14px;font-weight:500;cursor:none;}

/* FOOTER */
.footer{background:var(--s1);border-top:1px solid var(--border);padding:52px 44px 30px;}
.footer-top{display:flex;align-items:flex-start;justify-content:space-between;gap:40px;flex-wrap:wrap;margin-bottom:40px;}
.footer-brand{max-width:280px;}
.footer-about{font-size:13px;color:var(--muted);line-height:1.8;margin-top:12px;}
.footer-cols{display:flex;gap:52px;flex-wrap:wrap;}
.fc-h{font-family:var(--mono);font-size:9px;letter-spacing:2px;text-transform:uppercase;color:var(--muted);margin-bottom:14px;}
.fc-links{display:flex;flex-direction:column;gap:8px;}
.fc-l{font-size:13px;color:var(--dim);cursor:none;transition:color .2s;}
.fc-l:hover{color:var(--light);}
.footer-bar{border-top:1px solid var(--border);padding-top:22px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;}
.footer-copy{font-family:var(--mono);font-size:9px;color:var(--muted);letter-spacing:.5px;}
.footer-pw{font-family:var(--mono);font-size:9px;color:var(--muted);letter-spacing:.5px;}
.footer-pw span{color:var(--blue2);}

/* RESPONSIVE — TABLET */
@media(max-width:1050px){
  .nav{padding:0 22px;}
  .nav-links{display:none;}
  .ham{display:flex;}
  .wrap{padding:0 24px;}
  .hero-inner{padding:72px 24px;grid-template-columns:1fr;gap:44px;}
  .svc-grid{grid-template-columns:1fr;}
  .rb-inner{grid-template-columns:1fr 1fr;}
  .split{grid-template-columns:1fr;gap:40px;}
  .g3{grid-template-columns:1fr 1fr;}
  .cta-sec{padding:72px 24px;}
  .footer{padding:44px 24px 26px;}
  .sec{padding:72px 0;}
}
/* MOBILE */
@media(max-width:640px){
  :root{--nav-h:56px;}
  html{font-size:14px;}
  .nav{padding:0 14px;}
  .wrap{padding:0 14px;}
  .sec{padding:56px 0;}
  .hero-inner{padding:52px 14px;gap:36px;}
  h1.hero-h{font-size:clamp(44px,12vw,72px);}
  .hero-btns{flex-direction:column;}
  .hero-btns .btn-g,.hero-btns .btn-o{width:100%;justify-content:center;}
  .hero-stats{flex-wrap:wrap;gap:14px;}
  .hst{border-right:none;margin-right:0;padding-right:0;flex:0 0 calc(50% - 7px);}
  .g2{grid-template-columns:1fr;}
  .g3{grid-template-columns:1fr;}
  .g4{grid-template-columns:1fr 1fr;}
  .rb-inner{grid-template-columns:1fr 1fr;}
  .rb-cell{padding:24px 16px;}
  .rb-n{font-size:38px;}
  .calc-out{grid-template-columns:1fr;}
  .proc-in{padding-left:0;}
  .pn{font-size:34px;width:42px;}
  .footer-top{flex-direction:column;gap:28px;}
  .footer-cols{gap:32px;}
  .footer-bar{flex-direction:column;text-align:center;}
  .cta-sec{padding:56px 14px;}
  body{cursor:auto;}
  #cur,#cur-r{display:none;}
  button,a,.btn-g,.btn-o,.btn-b{cursor:pointer;}
  .nl,.nav-btn,.ham,.mob-x,.proc-btn,.faq-btn,.fc-l,input[type=range],.m-submit,.m-s-close{cursor:pointer;}
  .m-row{grid-template-columns:1fr;}
  .m-row-wrap{margin-bottom:0;}
  #modal{align-items:flex-end;padding:0;}
  #mbox{border-radius:16px 16px 0 0;max-height:88svh;}
  @keyframes mup{from{opacity:0;transform:translateY(44px)}to{opacity:1;transform:none}}
  .m-scroll{max-height:78svh;}
  .footer-brand{max-width:100%;}
}
@media(max-width:380px){
  .rb-inner{grid-template-columns:1fr;}
  h1.hero-h{font-size:44px;}
}
</style>
</head>
<body>

<div id="cur"></div>
<div id="cur-r"></div>
<div id="pg"></div>
<div class="mob-ov" id="mob-ov" onclick="cMob()"></div>

<nav class="mob-nav" id="mob-nav">
  <button class="mob-x" onclick="cMob()">×</button>
  <button class="nl" onclick="sTo('s-services');cMob()">Services</button>
  <button class="nl" onclick="sTo('s-results');cMob()">Results</button>
  <button class="nl" onclick="sTo('s-method');cMob()">Method</button>
  <button class="nl" onclick="sTo('s-roi');cMob()">ROI</button>
  <button class="nl" onclick="sTo('s-faq');cMob()">FAQ</button>
  <button class="nav-btn" onclick="oMod('consult');cMob()" style="margin-top:16px;">Book Free Call →</button>
</nav>

<!-- NAV -->
<header class="nav" id="nav">
  <div class="nav-logo" onclick="sTo('s-hero')">
    <div class="logo-sq">EA</div>
    <div class="logo-name">EMIRG AI</div>
  </div>
  <nav class="nav-links">
    <button class="nl on" onclick="sTo('s-hero')">Home</button>
    <button class="nl" onclick="sTo('s-services')">Services</button>
    <button class="nl" onclick="sTo('s-results')">Results</button>
    <button class="nl" onclick="sTo('s-method')">Method</button>
    <button class="nl" onclick="sTo('s-roi')">ROI</button>
    <button class="nl" onclick="sTo('s-faq')">FAQ</button>
  </nav>
  <div style="display:flex;align-items:center;gap:8px;">
    <button class="nav-btn" onclick="oMod('consult')">Book Free Call →</button>
    <button class="ham" id="ham" onclick="oMob()"><span></span><span></span><span></span></button>
  </div>
</header>

<!-- ═══ HERO ═══ -->
<section id="s-hero">
  <div class="hero-grid"></div>
  <canvas id="dots"></canvas>
  <div class="hero-inner">
    <div>
      <div class="hero-tag">AI Consultancy · Canada · 2024</div>
      <h1 class="hero-h">
        <span class="b">INTELLIGENT</span><br>
        OPERATIONS<br>
        <span class="g">DELIVERED.</span>
      </h1>
      <p class="hero-sub">EMIRG AI maps your operations, integrates your tech stack, automates your workflows, and forecasts your demand. <strong>Measurable ROI in 60 days.</strong></p>
      <div class="hero-btns">
        <button class="btn-g" onclick="oMod('consult')">Book Free Discovery Call</button>
        <button class="btn-o" onclick="sTo('s-roi')">Calculate My ROI →</button>
      </div>
      <div class="hero-stats">
        <div class="hst"><div class="hst-n"><span class="a">43</span>%</div><div class="hst-l">Efficiency Gain</div></div>
        <div class="hst"><div class="hst-n"><span class="a">60</span>D</div><div class="hst-l">Avg. ROI Horizon</div></div>
        <div class="hst"><div class="hst-n">$<span class="a">284</span>K</div><div class="hst-l">Savings Found (CAD)</div></div>
        <div class="hst"><div class="hst-n"><span class="a">−68</span>%</div><div class="hst-l">Error Reduction</div></div>
      </div>
    </div>
    <div>
      <div class="terminal">
        <div class="term-top">
          <div class="tdots"><div class="td" style="background:#ff5f57"></div><div class="td" style="background:#ffbd2e"></div><div class="td" style="background:#28c840"></div></div>
          <div class="t-label">EMIRG AI // OPS ENGINE</div>
          <div class="t-live"><div class="lpulse"></div>LIVE</div>
        </div>
        <div class="term-body">
          <div><span class="tc-p">$</span> <span class="tc-t">emirg scan --ops --depth full</span></div>
          <div><span class="tc-ok">✓</span> <span class="tc-t">Process nodes discovered: </span><span class="tc-w">147</span></div>
          <div><span class="tc-ok">✓</span> <span class="tc-t">Bottlenecks flagged: </span><span style="color:#ef4444">23</span></div>
          <div><span class="tc-ok">✓</span> <span class="tc-t">Automation candidates: </span><span class="tc-b">31</span></div>
          <div><span class="tc-ok">✓</span> <span class="tc-t">Est. savings: </span><span class="tc-ok">$284,000 CAD/yr</span></div>
          <div><span class="tc-p">$</span> <span class="tc-cur"></span></div>
        </div>
        <div class="term-foot">
          <div class="tf"><div class="tf-n" style="color:var(--green2);" id="tc1">0</div><div class="tf-l">Nodes</div></div>
          <div class="tf"><div class="tf-n" style="color:#ef4444;" id="tc2">0</div><div class="tf-l">Bottlenecks</div></div>
          <div class="tf"><div class="tf-n" style="color:var(--blue2);" id="tc3">0</div><div class="tf-l">Automations</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker">
  <div class="tick-inner">
    <div class="tk">Operational Mapping <span class="tv">✦ AI-Native</span></div>
    <div class="tk">Tech Integration <span class="tv">✦ Zero Downtime</span></div>
    <div class="tk">Autonomous Workflows <span class="tv">✦ 24/7 Active</span></div>
    <div class="tk">Demand Forecasting <span class="tv">✦ 94% Accuracy</span></div>
    <div class="tk">ROI Horizon <span class="tv">✦ 60 Days Avg.</span></div>
    <div class="tk">PIPEDA Compliant <span class="tv">✦ SOC2 Aligned</span></div>
    <div class="tk">Powered by Claude <span class="tv">✦ Anthropic</span></div>
    <div class="tk">Brant, Ontario <span class="tv">✦ Serving Canada</span></div>
    <div class="tk">Operational Mapping <span class="tv">✦ AI-Native</span></div>
    <div class="tk">Tech Integration <span class="tv">✦ Zero Downtime</span></div>
    <div class="tk">Autonomous Workflows <span class="tv">✦ 24/7 Active</span></div>
    <div class="tk">Demand Forecasting <span class="tv">✦ 94% Accuracy</span></div>
    <div class="tk">ROI Horizon <span class="tv">✦ 60 Days Avg.</span></div>
    <div class="tk">PIPEDA Compliant <span class="tv">✦ SOC2 Aligned</span></div>
    <div class="tk">Powered by Claude <span class="tv">✦ Anthropic</span></div>
    <div class="tk">Brant, Ontario <span class="tv">✦ Serving Canada</span></div>
  </div>
</div>

<!-- ═══ SERVICES ═══ -->
<section id="s-services">
  <div class="sec">
    <div class="wrap" style="margin-bottom:44px;">
      <div class="tag rv">Core Services</div>
      <h2 class="h1 rv d1" style="margin-bottom:14px;">FOUR PILLARS.<br><span class="b">ONE</span> TRANSFORMATION.</h2>
      <p class="body rv d2" style="max-width:520px;">We don't sell software. We deliver working systems that permanently change how your business operates.</p>
    </div>
    <div class="wrap">
      <div class="svc-grid rv">
        <div class="svc">
          <div class="svc-num">01</div>
          <div class="svc-ico">🗺️</div>
          <div class="svc-title">OPERATIONAL<br>MAPPING</div>
          <p class="svc-body">AI maps every process, workflow, and decision point — many for the first time. Delivers a living Operations Map in 2 weeks.</p>
          <div class="svc-list">
            <div class="sl">Full process documentation</div>
            <div class="sl">Bottleneck &amp; redundancy identification</div>
            <div class="sl">ROI-prioritised improvement roadmap</div>
          </div>
          <div class="chip chip-g">Flagship</div>
        </div>
        <div class="svc">
          <div class="svc-num">02</div>
          <div class="svc-ico">🔗</div>
          <div class="svc-title">TECHNOLOGY<br>INTEGRATION</div>
          <p class="svc-body">Audit, rationalise, and connect your tools into one coherent intelligence layer. No more data silos.</p>
          <div class="svc-list">
            <div class="sl">Tech stack audit &amp; rationalisation</div>
            <div class="sl">API &amp; no-code integration builds</div>
            <div class="sl">ERP, CRM, and analytics connectivity</div>
          </div>
          <div class="chip chip-b">High Impact</div>
        </div>
        <div class="svc">
          <div class="svc-num">03</div>
          <div class="svc-ico">🤖</div>
          <div class="svc-title">AUTONOMY &amp;<br>AUTOMATION</div>
          <p class="svc-body">Turn manual processes into AI-powered workflows that run 24/7 — freeing your team for high-value work.</p>
          <div class="svc-list">
            <div class="sl">AI agent design &amp; deployment</div>
            <div class="sl">Approval &amp; routing automation</div>
            <div class="sl">Multi-system orchestration</div>
          </div>
          <div class="chip chip-d">AI-Powered</div>
        </div>
        <div class="svc">
          <div class="svc-num">04</div>
          <div class="svc-ico">📈</div>
          <div class="svc-title">DEMAND<br>PLANNING</div>
          <p class="svc-body">Replace guesswork with machine precision. AI models your demand at 94% accuracy — live, adaptive, explainable.</p>
          <div class="svc-list">
            <div class="sl">Predictive demand modelling</div>
            <div class="sl">Inventory optimisation</div>
            <div class="sl">Live dashboard + AI alerts</div>
          </div>
          <div class="chip chip-g">94% Accuracy</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ RESULTS BAND ═══ -->
<div class="results-band" id="s-results">
  <div class="rb-inner">
    <div class="rb-cell rv"><div class="rb-n" style="color:var(--green2);">+43%</div><div class="rb-l">Avg. operational efficiency improvement</div></div>
    <div class="rb-cell rv d1"><div class="rb-n" style="color:var(--blue2);">$284K</div><div class="rb-l">Avg. annual savings found per client (CAD)</div></div>
    <div class="rb-cell rv d2"><div class="rb-n" style="color:var(--white);">60d</div><div class="rb-l">Avg. days to first measurable ROI</div></div>
    <div class="rb-cell rv d3"><div class="rb-n" style="color:var(--blue2);">−68%</div><div class="rb-l">Avg. process error rate reduction</div></div>
  </div>
</div>

<!-- ═══ PROOF ═══ -->
<section>
  <div class="sec">
    <div class="wrap">
      <div class="split top" style="gap:56px;">
        <div>
          <div class="tag rv">Client Results</div>
          <h2 class="h2 rv d1" style="margin-bottom:16px;">REAL NUMBERS.<br><span class="g">REAL CLIENTS.</span></h2>
          <div class="col rv d2" style="gap:10px;margin-bottom:28px;" id="hbars">
            <div style="display:flex;align-items:center;gap:12px;">
              <div style="font-size:12px;color:var(--muted);width:140px;flex-shrink:0;">Process Efficiency</div>
              <div style="flex:1;height:3px;background:var(--border2);border-radius:2px;overflow:hidden;"><div class="hbf" data-w="86%" style="background:var(--green2);height:100%;width:0;border-radius:2px;transition:width 1.3s cubic-bezier(.16,1,.3,1);"></div></div>
              <div style="font-family:var(--mono);font-size:10px;color:var(--muted);width:40px;text-align:right;flex-shrink:0;">+43%</div>
            </div>
            <div style="display:flex;align-items:center;gap:12px;">
              <div style="font-size:12px;color:var(--muted);width:140px;flex-shrink:0;">Staff Productivity</div>
              <div style="flex:1;height:3px;background:var(--border2);border-radius:2px;overflow:hidden;"><div class="hbf" data-w="72%" style="background:var(--blue2);height:100%;width:0;border-radius:2px;transition:width 1.3s cubic-bezier(.16,1,.3,1);"></div></div>
              <div style="font-family:var(--mono);font-size:10px;color:var(--muted);width:40px;text-align:right;flex-shrink:0;">+36%</div>
            </div>
            <div style="display:flex;align-items:center;gap:12px;">
              <div style="font-size:12px;color:var(--muted);width:140px;flex-shrink:0;">Error Rate</div>
              <div style="flex:1;height:3px;background:var(--border2);border-radius:2px;overflow:hidden;"><div class="hbf" data-w="68%" style="background:var(--blue2);height:100%;width:0;border-radius:2px;transition:width 1.3s cubic-bezier(.16,1,.3,1);"></div></div>
              <div style="font-family:var(--mono);font-size:10px;color:var(--muted);width:40px;text-align:right;flex-shrink:0;">−68%</div>
            </div>
            <div style="display:flex;align-items:center;gap:12px;">
              <div style="font-size:12px;color:var(--muted);width:140px;flex-shrink:0;">Reporting Time</div>
              <div style="flex:1;height:3px;background:var(--border2);border-radius:2px;overflow:hidden;"><div class="hbf" data-w="81%" style="background:var(--green2);height:100%;width:0;border-radius:2px;transition:width 1.3s cubic-bezier(.16,1,.3,1);"></div></div>
              <div style="font-family:var(--mono);font-size:10px;color:var(--muted);width:40px;text-align:right;flex-shrink:0;">−81%</div>
            </div>
          </div>
          <button class="btn-b rv d3" onclick="oMod('consult')">Get Your Numbers →</button>
        </div>
        <div class="col rv d1" style="gap:14px;">
          <div class="tcard">
            <div class="tcard-q">"</div>
            <div class="tcard-text">"Client onboarding went from 3 weeks to 4 days. EMIRG found 14 redundant steps we never knew existed."</div>
            <div class="tcard-line"></div>
            <div class="tcard-name">Chief Operating Officer</div>
            <div class="tcard-role">Professional Services · Toronto · 2025</div>
          </div>
          <div class="tcard">
            <div class="tcard-q">"</div>
            <div class="tcard-text">"The demand planning model paid for our engagement six times over. 94.2% accuracy for 8 straight months."</div>
            <div class="tcard-line"></div>
            <div class="tcard-name">Director of Supply Chain</div>
            <div class="tcard-role">Mid-Market Manufacturer · Alberta · 2025</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ METHOD ═══ -->
<section id="s-method" style="background:var(--s1);border-top:1px solid var(--border);border-bottom:1px solid var(--border);">
  <div class="sec">
    <div class="wrap">
      <div class="split top" style="gap:64px;">
        <div>
          <div class="tag rv">Method</div>
          <h2 class="h1 rv d1" style="margin-bottom:16px;">5 PHASES.<br><span class="g">WEEK 1</span> DELIVERY.</h2>
          <p class="body rv d2" style="margin-bottom:28px;">First deliverable in Week 1. Measurable ROI by Day 60. Every engagement is fixed-scope and fully staffed — no surprises.</p>
          <div class="card rv d3" style="padding:18px 20px;border-color:var(--blueedge);margin-bottom:24px;">
            <div style="font-family:var(--mono);font-size:8.5px;letter-spacing:1.5px;text-transform:uppercase;color:var(--blue2);margin-bottom:10px;">Every Engagement Includes</div>
            <div class="col" style="gap:7px;">
              <div style="font-size:13px;color:var(--dim);display:flex;gap:8px;"><span style="color:var(--green2);">✓</span> Full Operations Map — visual &amp; interactive</div>
              <div style="font-size:13px;color:var(--dim);display:flex;gap:8px;"><span style="color:var(--green2);">✓</span> ROI-prioritised improvement roadmap</div>
              <div style="font-size:13px;color:var(--dim);display:flex;gap:8px;"><span style="color:var(--green2);">✓</span> 90-day implementation support</div>
              <div style="font-size:13px;color:var(--dim);display:flex;gap:8px;"><span style="color:var(--green2);">✓</span> Staff training on all deployed systems</div>
            </div>
          </div>
          <button class="btn-g rv d4" onclick="oMod('consult')">Book Discovery Call →</button>
        </div>
        <div class="proc-list rv d1">
          <div class="proc-item open">
            <button class="proc-btn" onclick="tProc(this)">
              <div class="pn">01</div><div class="pt">Discovery &amp; Intake</div><div class="pa">›</div>
            </button>
            <div class="proc-body"><div class="proc-in">Stakeholder interviews, system audit, data collection. AI baseline established Day 1 — every improvement measured against it.<div class="proc-chips"><span class="chip chip-d">Week 1–2</span><span class="chip chip-b">First deliverable: Day 7</span></div></div></div>
          </div>
          <div class="proc-item">
            <button class="proc-btn" onclick="tProc(this)">
              <div class="pn">02</div><div class="pt">AI Operational Mapping</div><div class="pa">›</div>
            </button>
            <div class="proc-body"><div class="proc-in">Claude analyses every workflow, identifies dependencies and hidden costs. Full Operations Map with ROI-ranked recommendations delivered.<div class="proc-chips"><span class="chip chip-d">Day 10–14</span><span class="chip chip-g">Claude-Powered</span></div></div></div>
          </div>
          <div class="proc-item">
            <button class="proc-btn" onclick="tProc(this)">
              <div class="pn">03</div><div class="pt">Insight Report &amp; Roadmap</div><div class="pa">›</div>
            </button>
            <div class="proc-body"><div class="proc-in">Board-ready transformation plan with projected ROI, effort estimates, and quick-win sequencing. Ready to act on, not just read.<div class="proc-chips"><span class="chip chip-d">Week 2–3</span><span class="chip chip-b">Board-Ready</span></div></div></div>
          </div>
          <div class="proc-item">
            <button class="proc-btn" onclick="tProc(this)">
              <div class="pn">04</div><div class="pt">Implementation Sprint</div><div class="pa">›</div>
            </button>
            <div class="proc-body"><div class="proc-in">We build alongside your team. Automations deploy. Integrations go live. Dashboards launch. Staff get trained. Real change — not more documents.<div class="proc-chips"><span class="chip chip-d">Week 3–8</span><span class="chip chip-g">Hands-On</span></div></div></div>
          </div>
          <div class="proc-item">
            <button class="proc-btn" onclick="tProc(this)">
              <div class="pn">05</div><div class="pt">Continuous Intelligence</div><div class="pa">›</div>
            </button>
            <div class="proc-body"><div class="proc-in">Optional retained monitoring, quarterly re-mapping, and new opportunity identification. Operations that get smarter every quarter.<div class="proc-chips"><span class="chip chip-d">Ongoing</span><span class="chip chip-b">Optional</span></div></div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ ROI ═══ -->
<section id="s-roi">
  <div class="sec">
    <div class="wrap">
      <div class="split top" style="gap:64px;">
        <div>
          <div class="tag rv">ROI Calculator</div>
          <h2 class="h1 rv d1" style="margin-bottom:16px;">SEE YOUR<br><span class="b">NUMBERS</span><br>FIRST.</h2>
          <p class="body rv d2" style="margin-bottom:24px;">Every engagement starts with a projected ROI model shared upfront. Adjust the sliders — we'll confirm in your free call.</p>
          <div style="display:flex;gap:10px;flex-wrap:wrap;" class="rv d3">
            <button class="btn-g" onclick="oMod('consult')">Book Free Call →</button>
            <button class="btn-o" onclick="oMod('audit')">Request Audit</button>
          </div>
        </div>
        <div class="calc rv d1">
          <div class="calc-head">
            <div class="calc-title">ROI ESTIMATOR</div>
            <div class="calc-live"><div class="lpulse"></div>LIVE</div>
          </div>
          <div class="calc-body">
            <div class="sl-g"><div class="sl-l">Team Size<span class="sl-v" id="lbl-t">25 employees</span></div><input type="range" id="sl-t" min="5" max="500" value="25" oninput="cROI()"></div>
            <div class="sl-g"><div class="sl-l">Avg. Salary (CAD)<span class="sl-v" id="lbl-s">$75,000</span></div><input type="range" id="sl-s" min="40000" max="200000" step="5000" value="75000" oninput="cROI()"></div>
            <div class="sl-g"><div class="sl-l">% Time on Manual Work<span class="sl-v" id="lbl-m">30%</span></div><input type="range" id="sl-m" min="10" max="60" value="30" oninput="cROI()"></div>
            <div class="sl-g"><div class="sl-l">Process Error Rate<span class="sl-v" id="lbl-e">8%</span></div><input type="range" id="sl-e" min="1" max="25" value="8" oninput="cROI()"></div>
            <div class="calc-out">
              <div class="co"><div class="co-n" style="color:var(--green2);" id="roi-s">$284K</div><div class="co-l">Annual Savings</div></div>
              <div class="co"><div class="co-n" style="color:var(--blue2);" id="roi-p">60 days</div><div class="co-l">Payback</div></div>
              <div class="co"><div class="co-n" id="roi-h">2,340h</div><div class="co-l">Hours Back</div></div>
            </div>
            <div class="calc-note">Based on EMIRG AI engagement averages. Confirmed in discovery call.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ FAQ ═══ -->
<section id="s-faq" style="background:var(--s1);border-top:1px solid var(--border);">
  <div class="sec">
    <div class="wrap" style="max-width:780px;">
      <div class="tag rv" style="justify-content:center;">FAQ</div>
      <h2 class="h1 rv d1" style="text-align:center;margin-bottom:44px;">COMMON <span class="b">QUESTIONS.</span></h2>
      <div>
        <div class="faq-item">
          <button class="faq-btn" onclick="tFaq(this)"><div class="faq-q">How long does an engagement take?</div><div class="faq-ic">+</div></button>
          <div class="faq-ans"><div class="faq-in">6–10 weeks end to end. First deliverable in Week 1. Measurable ROI within 60–90 days. Optional retained support after that.</div></div>
        </div>
        <div class="faq-item">
          <button class="faq-btn" onclick="tFaq(this)"><div class="faq-q">Do I need technical staff?</div><div class="faq-ic">+</div></button>
          <div class="faq-ans"><div class="faq-in">No. We handle architecture, integration, and deployment. Your team participates in interviews and provides system access — we handle the rest and train your staff on everything deployed.</div></div>
        </div>
        <div class="faq-item">
          <button class="faq-btn" onclick="tFaq(this)"><div class="faq-q">How is our data protected?</div><div class="faq-ic">+</div></button>
          <div class="faq-ans"><div class="faq-in">Mutual NDA from day one. SOC2-aligned infrastructure. PIPEDA-compliant pipelines. Your data is never used to train AI models without explicit written consent. On-premise deployment available.</div></div>
        </div>
        <div class="faq-item">
          <button class="faq-btn" onclick="tFaq(this)"><div class="faq-q">What ROI can I expect?</div><div class="faq-ic">+</div></button>
          <div class="faq-ans"><div class="faq-in">Our portfolio averages: 43% efficiency improvement, $284K savings identified, 60-day ROI horizon. We share a projected ROI model before any engagement starts. If we don't believe we can deliver value, we say so.</div></div>
        </div>
        <div class="faq-item">
          <button class="faq-btn" onclick="tFaq(this)"><div class="faq-q">How does demand planning work?</div><div class="faq-ic">+</div></button>
          <div class="faq-ans"><div class="faq-in">We ingest 12–36 months of historical data, identify demand drivers and seasonality, and deploy a live forecasting dashboard with AI-generated weekly alerts. Current portfolio accuracy: 94.2%.</div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══ CTA ═══ -->
<div class="cta-sec">
  <div class="cta-glow"></div>
  <div style="position:relative;z-index:1;max-width:640px;margin:0 auto;">
    <div class="tag rv" style="justify-content:center;">Start Today</div>
    <h2 class="h1 rv d1" style="margin-bottom:16px;">YOUR OPERATIONS<br>COULD BE <span class="g">THIS</span> CLEAN.</h2>
    <p class="body rv d2" style="margin-bottom:32px;max-width:480px;margin-left:auto;margin-right:auto;text-align:center;">Free 45-min discovery call. We map one process live, identify your top 3 inefficiencies, give you a projected ROI. No cost. No obligation.</p>
    <div style="display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-bottom:44px;" class="rv d3">
      <button class="btn-g" onclick="oMod('consult')" style="font-size:15px;padding:14px 36px;">Book Free Discovery Call</button>
      <button class="btn-o" onclick="oMod('audit')">Request Process Audit</button>
    </div>
    <div style="display:flex;gap:32px;justify-content:center;flex-wrap:wrap;padding-top:32px;border-top:1px solid var(--border);" class="rv d4">
      <div style="text-align:center;"><div style="font-family:var(--mono);font-size:8.5px;letter-spacing:2px;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">Location</div><div style="font-size:13px;color:var(--text);">Brant, Ontario · Canada</div></div>
      <div style="width:1px;background:var(--border);"></div>
      <div style="text-align:center;"><div style="font-family:var(--mono);font-size:8.5px;letter-spacing:2px;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">Response</div><div style="font-size:13px;color:var(--text);">Within 1 business day</div></div>
      <div style="width:1px;background:var(--border);"></div>
      <div style="text-align:center;"><div style="font-family:var(--mono);font-size:8.5px;letter-spacing:2px;text-transform:uppercase;color:var(--dim);margin-bottom:5px;">First Deliverable</div><div style="font-size:13px;color:var(--text);">Week 1 — not Month 3</div></div>
    </div>
  </div>
</div>

<!-- ═══ FOOTER ═══ -->
<footer class="footer">
  <div class="footer-top">
    <div class="footer-brand">
      <div style="display:flex;align-items:center;gap:9px;margin-bottom:2px;">
        <div class="logo-sq">EA</div>
        <div class="logo-name">EMIRG AI</div>
      </div>
      <div class="footer-about">AI-powered operations consulting for Canadian businesses. We map, automate, integrate, and optimise.</div>
      <div style="display:flex;gap:8px;flex-wrap:wrap;margin-top:14px;">
        <div style="padding:4px 10px;background:var(--blueglow);border:1px solid var(--blueedge);border-radius:5px;font-family:var(--mono);font-size:8.5px;color:var(--blue2);">PIPEDA Compliant</div>
        <div style="padding:4px 10px;background:var(--greenglow);border:1px solid var(--greenedge);border-radius:5px;font-family:var(--mono);font-size:8.5px;color:var(--green2);">NDA Protected</div>
        <div style="padding:4px 10px;background:var(--blueglow);border:1px solid var(--blueedge);border-radius:5px;font-family:var(--mono);font-size:8.5px;color:var(--blue2);">SOC2 Aligned</div>
      </div>
    </div>
    <div class="footer-cols">
      <div>
        <div class="fc-h">Services</div>
        <div class="fc-links">
          <div class="fc-l" onclick="sTo('s-services')">Operational Mapping</div>
          <div class="fc-l" onclick="sTo('s-services')">Tech Integration</div>
          <div class="fc-l" onclick="sTo('s-services')">Autonomy &amp; Automation</div>
          <div class="fc-l" onclick="sTo('s-services')">Demand Planning</div>
        </div>
      </div>
      <div>
        <div class="fc-h">Contact</div>
        <div class="fc-links">
          <div class="fc-l">logistics@emirg-group.com</div>
          <div class="fc-l">Brant, Ontario</div>
          <div style="margin-top:10px;"><button class="btn-g" onclick="oMod('consult')" style="font-size:12.5px;padding:9px 18px;width:100%;">Book a Call →</button></div>
        </div>
      </div>
    </div>
  </div>
  <div class="footer-bar">
    <div class="footer-copy">© 2026 EMIRG AI Inc. · Brant, Ontario, Canada</div>
    <div class="footer-pw">Powered by <span>Anthropic Claude</span></div>
  </div>
</footer>

<!-- ═══ MODAL ═══ -->
<div id="modal" onclick="mOut(event)">
  <div id="mbox">
    <div class="m-top">
      <div class="m-id">
        <div class="m-sq">EA</div>
        <div><div class="m-title" id="m-title">Book a Free Discovery Call</div><div class="m-sub">EMIRG AI · logistics@emirg-group.com</div></div>
      </div>
      <button class="m-x" onclick="cMod()">×</button>
    </div>
    <div class="m-scroll">
      <div id="m-success" class="m-success">
        <div class="m-s-ico">✅</div>
        <div class="m-s-h">MESSAGE SENT</div>
        <div class="m-s-b">Heading to <strong style="color:var(--green2);">logistics@emirg-group.com</strong>.<br>We'll respond within 1 business day.</div>
        <button class="m-s-close" onclick="cMod()">Close</button>
      </div>
      <div id="m-form">
        <p class="m-desc" id="m-desc">Tell us about your business and we'll confirm your free 45-minute discovery call within <strong style="color:var(--light);">1 business day.</strong></p>
        <div class="m-row-wrap"><div class="m-row"><div><label class="m-lbl">First Name *</label><input id="fn" type="text" class="m-inp" placeholder="Jane" autocomplete="given-name"></div><div><label class="m-lbl">Last Name *</label><input id="ln" type="text" class="m-inp" placeholder="Smith" autocomplete="family-name"></div></div></div>
        <label class="m-lbl">Company</label><input id="co" type="text" class="m-inp" placeholder="Acme Corp" autocomplete="organization">
        <div class="m-row-wrap"><div class="m-row"><div><label class="m-lbl">Email *</label><input id="em" type="email" class="m-inp" placeholder="jane@company.com" autocomplete="email"></div><div><label class="m-lbl">Phone</label><input id="ph" type="tel" class="m-inp" placeholder="(519) 555-0100" autocomplete="tel"></div></div></div>
        <div id="m-ext" style="display:none;">
          <label class="m-lbl">Industry</label>
          <select id="ind" class="m-inp"><option value="">Select...</option><option>Manufacturing</option><option>Logistics &amp; Freight</option><option>Healthcare</option><option>Legal &amp; Professional</option><option>Construction</option><option>Retail &amp; E-Commerce</option><option>Finance &amp; Insurance</option><option>Agriculture</option><option>Other</option></select>
          <label class="m-lbl">Top Challenge</label>
          <select id="ch" class="m-inp"><option value="">Select...</option><option>Manual tasks taking too long</option><option>No process documentation</option><option>Poor demand forecasting</option><option>Disconnected systems</option><option>Approval bottlenecks</option><option>Data silos</option><option>Other</option></select>
        </div>
        <label class="m-lbl">Message</label>
        <textarea id="msg" rows="3" class="m-inp" style="resize:vertical;min-height:76px;" placeholder="Tell us about your business or current challenges..."></textarea>
        <div id="m-err" class="m-err"></div>
        <button id="m-btn" class="m-submit" onclick="sendForm()"><span id="m-ico">📨</span><span id="m-txt">Send Inquiry</span></button>
        <div class="m-foot">Sent to logistics@emirg-group.com · Reply within 1 business day</div>
      </div>
    </div>
  </div>
</div>

<script>
/* CURSOR */
const cur=document.getElementById('cur'),cr=document.getElementById('cur-r');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cur.style.left=mx+'px';cur.style.top=my+'px';});
(function loop(){rx+=(mx-rx)*.12;ry+=(my-ry)*.12;cr.style.left=rx+'px';cr.style.top=ry+'px';requestAnimationFrame(loop);})();
document.querySelectorAll('button,a,[onclick]').forEach(el=>{el.addEventListener('mouseenter',()=>cur.classList.add('big'));el.addEventListener('mouseleave',()=>cur.classList.remove('big'));});

/* PROGRESS */
const pg=document.getElementById('pg');
window.addEventListener('scroll',()=>{const d=document.documentElement;pg.style.width=(d.scrollTop/(d.scrollHeight-d.clientHeight)*100)+'%';},{passive:true});

/* NAV ACTIVE */
const secs=[['s-hero',0],['s-services',1],['s-results',2],['s-method',3],['s-roi',4],['s-faq',5]];
const nls=document.querySelectorAll('.nav-links .nl');
window.addEventListener('scroll',()=>{const mid=window.scrollY+window.innerHeight*.35;secs.forEach(([id,i])=>{const el=document.getElementById(id);if(!el)return;if(mid>=el.offsetTop&&mid<el.offsetTop+el.offsetHeight){nls.forEach(b=>b.classList.remove('on'));if(nls[i])nls[i].classList.add('on');}});},{passive:true});

/* NAV / MOBILE */
function sTo(id){document.getElementById(id)?.scrollIntoView({behavior:'smooth'});}
function oMob(){document.getElementById('mob-nav').classList.add('open');document.getElementById('mob-ov').classList.add('open');document.body.style.overflow='hidden';}
function cMob(){document.getElementById('mob-nav').classList.remove('open');document.getElementById('mob-ov').classList.remove('open');document.body.style.overflow='';}

/* SCROLL REVEAL */
const ro=new IntersectionObserver(es=>es.forEach(e=>{if(e.isIntersecting)e.target.classList.add('in');}),{threshold:.07});
document.querySelectorAll('.rv').forEach(el=>ro.observe(el));

/* H-BARS */
const bo=new IntersectionObserver(es=>{es.forEach(e=>{if(!e.isIntersecting)return;e.target.querySelectorAll('.hbf').forEach((b,i)=>{b.style.width='0';setTimeout(()=>b.style.width=b.dataset.w||'0%',i*60+80);});bo.unobserve(e.target);});},{threshold:.3});
const hb=document.getElementById('hbars');if(hb)bo.observe(hb);

/* TERMINAL COUNTERS */
let cStarted=false;
const cTargets={tc1:147,tc2:23,tc3:31};
function runCounters(){if(cStarted)return;cStarted=true;Object.entries(cTargets).forEach(([id,t])=>{const el=document.getElementById(id);if(!el)return;let v=0;const s=Math.ceil(t/40);const iv=setInterval(()=>{v=Math.min(v+s,t);el.textContent=v;if(v>=t)clearInterval(iv);},28);});}
const to=new IntersectionObserver(es=>{es.forEach(e=>{if(e.isIntersecting)runCounters();});},{threshold:.2});
const te=document.querySelector('.terminal');if(te)to.observe(te);

/* DOTS CANVAS */
(function(){
  const c=document.getElementById('dots');
  if(!c||window.innerWidth<640){if(c)c.style.display='none';return;}
  const ctx=c.getContext('2d');let W,H,pts,t=0;
  const resize=()=>{W=c.width=c.offsetWidth;H=c.height=c.offsetHeight;pts=Array.from({length:50},()=>({x:Math.random()*W,y:Math.random()*H,vx:(Math.random()-.5)*.25,vy:(Math.random()-.5)*.25,r:.6+Math.random()*1.2,ph:Math.random()*Math.PI*2}));};
  resize();window.addEventListener('resize',resize,{passive:true});
  const draw=()=>{ctx.clearRect(0,0,W,H);t+=.007;pts.forEach(p=>{p.x+=p.vx;p.y+=p.vy;if(p.x<0||p.x>W)p.vx*=-1;if(p.y<0||p.y>H)p.vy*=-1;});
    for(let i=0;i<pts.length;i++)for(let j=i+1;j<pts.length;j++){const a=pts[i],b=pts[j],d=Math.hypot(a.x-b.x,a.y-b.y);if(d>200)continue;ctx.beginPath();ctx.moveTo(a.x,a.y);ctx.lineTo(b.x,b.y);ctx.strokeStyle=`rgba(37,99,235,${(1-d/200)*.08})`;ctx.lineWidth=.5;ctx.stroke();}
    pts.forEach(n=>{const p=Math.sin(t+n.ph);ctx.beginPath();ctx.arc(n.x,n.y,n.r*(1+p*.2),0,Math.PI*2);ctx.fillStyle=`rgba(37,99,235,${.18+p*.07})`;ctx.fill();});
    requestAnimationFrame(draw);};draw();
})();

/* PROCESS ACCORDION */
function tProc(btn){const item=btn.closest('.proc-item'),body=item.querySelector('.proc-body'),isOpen=item.classList.contains('open');document.querySelectorAll('.proc-item').forEach(i=>{i.classList.remove('open');i.querySelector('.proc-body').style.maxHeight='0';});if(!isOpen){item.classList.add('open');body.style.maxHeight=body.scrollHeight+'px';}}
(function(){const f=document.querySelector('.proc-item.open');if(f){const b=f.querySelector('.proc-body');if(b)b.style.maxHeight=b.scrollHeight+'px';}})();

/* FAQ */
function tFaq(btn){const item=btn.closest('.faq-item'),ans=item.querySelector('.faq-ans'),isOpen=item.classList.contains('open');document.querySelectorAll('.faq-item').forEach(i=>{i.classList.remove('open');i.querySelector('.faq-ans').style.maxHeight='0';});if(!isOpen){item.classList.add('open');ans.style.maxHeight=ans.scrollHeight+'px';}}

/* ROI CALCULATOR */
function cROI(){
  const t=+document.getElementById('sl-t').value,s=+document.getElementById('sl-s').value,m=+document.getElementById('sl-m').value/100,e=+document.getElementById('sl-e').value/100;
  document.getElementById('lbl-t').textContent=t+' employees';
  document.getElementById('lbl-s').textContent='$'+s.toLocaleString('en-CA');
  document.getElementById('lbl-m').textContent=Math.round(m*100)+'%';
  document.getElementById('lbl-e').textContent=Math.round(e*100)+'%';
  const total=Math.round((t*s*m*.31+t*s*e*.68*.4)/1000)*1000;
  const hrs=Math.round(t*2080*m*.31);
  const pay=total>0?Math.round(55000/total*365):999;
  document.getElementById('roi-s').textContent='$'+Math.round(total/1000)+'K';
  document.getElementById('roi-p').textContent=pay<=365?pay+' days':'>1yr';
  document.getElementById('roi-h').textContent=hrs.toLocaleString()+'h';
}
cROI();

/* MODAL */
let mT='consult';
const mCfg={
  consult:{title:'Book a Free Discovery Call',desc:"Tell us about your business and we'll confirm your free 45-min call within <strong style='color:var(--light)'>1 business day</strong>.",ext:false},
  audit:{title:'Request a Process Audit',desc:"Submit your details and we'll schedule your complimentary operations audit.",ext:true}
};
function oMod(type){
  mT=type;const c=mCfg[type]||mCfg.consult;
  document.getElementById('m-title').textContent=c.title;
  document.getElementById('m-desc').innerHTML=c.desc;
  document.getElementById('m-ext').style.display=c.ext?'block':'none';
  document.getElementById('m-form').style.display='block';
  document.getElementById('m-success').style.display='none';
  document.getElementById('m-err').style.display='none';
  document.getElementById('m-ico').textContent='📨';
  document.getElementById('m-txt').textContent='Send Inquiry';
  document.getElementById('m-btn').disabled=false;
  const modal=document.getElementById('modal');
  modal.style.display='flex';document.body.style.overflow='hidden';
  const box=document.getElementById('mbox');box.style.animation='none';box.offsetHeight;box.style.animation='mup .35s cubic-bezier(.16,1,.3,1)';
}
function cMod(){document.getElementById('modal').style.display='none';document.body.style.overflow='';}
function mOut(e){if(e.target===document.getElementById('modal'))cMod();}
document.addEventListener('keydown',e=>{if(e.key==='Escape')cMod();});
let t0=0;
document.getElementById('mbox').addEventListener('touchstart',e=>{t0=e.touches[0].clientY;},{passive:true});
document.getElementById('mbox').addEventListener('touchmove',e=>{if(e.touches[0].clientY-t0>80)cMod();},{passive:true});

function sendForm(){
  const fn=document.getElementById('fn').value.trim(),ln=document.getElementById('ln').value.trim(),em=document.getElementById('em').value.trim();
  const co=document.getElementById('co').value.trim(),ph=document.getElementById('ph').value.trim(),msg=document.getElementById('msg').value.trim();
  const ind=document.getElementById('ind')?.value||'',ch=document.getElementById('ch')?.value||'';
  const err=document.getElementById('m-err');
  if(!fn||!ln){err.textContent='⚠ Please enter your name.';err.style.display='block';return;}
  if(!em||!em.includes('@')){err.textContent='⚠ Please enter a valid email.';err.style.display='block';return;}
  const labels={consult:'DISCOVERY CALL REQUEST',audit:'PROCESS AUDIT REQUEST'};
  const subj=`${labels[mT]||'INQUIRY'} — ${fn} ${ln}${co?' · '+co:''}`;
  const body=`${labels[mT]||'INQUIRY'} — EMIRG AI\n${'─'.repeat(48)}\n\nName: ${fn} ${ln}\nCompany: ${co||'N/A'}\nEmail: ${em}\nPhone: ${ph||'N/A'}\n${ind?'Industry: '+ind+'\n':''}${ch?'Challenge: '+ch+'\n':''}\nMESSAGE\n${'─'.repeat(48)}\n${msg||'No message.'}\n\n${'─'.repeat(48)}\nSubmitted via EMIRG AI Website\nTimestamp: ${new Date().toLocaleString('en-CA',{timeZone:'America/Toronto'})} ET`;
  document.getElementById('m-ico').textContent='⏳';document.getElementById('m-txt').textContent='Sending...';document.getElementById('m-btn').disabled=true;
  window.location.href=`mailto:logistics@emirg-group.com?subject=${encodeURIComponent(subj)}&body=${encodeURIComponent(body)}`;
  setTimeout(()=>{document.getElementById('m-form').style.display='none';document.getElementById('m-success').style.display='block';},800);
}
</script>
</body>
</html>
