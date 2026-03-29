<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>C-Lite Fans | Vanya Electrical — Delhi</title>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@300;400;500;600;700&family=Exo+2:ital,wght@0,200;0,300;0,400;0,600;0,700;1,200&family=JetBrains+Mono:wght@300;400&display=swap" rel="stylesheet">
<style>
  *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
  :root{
    --bg:#06080f;--surface:#0b0e18;--card:#0f1220;--border:#1a2035;
    --blue:#1a6fff;--cyan:#00d4ff;--text:#e8edf8;--muted:#5a6480;--soft:#8a95b0;
  }
  html{scroll-behavior:smooth}
  body{font-family:"Exo 2",sans-serif;background:var(--bg);color:var(--text);overflow-x:hidden}
  /* custom cursor - does NOT hide default cursor */
  #cur{position:fixed;width:6px;height:6px;background:var(--cyan);border-radius:50%;pointer-events:none;z-index:99999;transform:translate(-50%,-50%);box-shadow:0 0 10px var(--cyan)}
  #cur-ring{position:fixed;width:28px;height:28px;border:1px solid rgba(0,212,255,.4);border-radius:50%;pointer-events:none;z-index:99998;transform:translate(-50%,-50%);transition:width .2s,height .2s}
  body.h #cur{width:10px;height:10px;background:var(--blue)}
  body.h #cur-ring{width:44px;height:44px;border-color:rgba(26,111,255,.5)}

  /* LOADER */
  #loader{
    position:fixed;inset:0;background:var(--bg);z-index:99990;
    display:flex;flex-direction:column;align-items:center;justify-content:center;
    gap:0;transition:opacity 1s ease;overflow:hidden;
  }
  #loader.out{opacity:0;pointer-events:none}
  #loader::before{
    content:"";position:absolute;inset:0;
    background-image:linear-gradient(rgba(26,111,255,.05) 1px,transparent 1px),linear-gradient(90deg,rgba(26,111,255,.05) 1px,transparent 1px);
    background-size:50px 50px;
    animation:loaderGridPulse 2s ease-in-out infinite;
  }
  @keyframes loaderGridPulse{0%,100%{opacity:.5}50%{opacity:1}}
  .l-glow{
    position:absolute;width:340px;height:340px;border-radius:50%;
    background:radial-gradient(circle,rgba(0,212,255,.12) 0%,rgba(26,111,255,.06) 40%,transparent 70%);
    animation:loaderGlowPulse 1.5s ease-in-out infinite;
  }
  @keyframes loaderGlowPulse{0%,100%{transform:scale(1);opacity:.6}50%{transform:scale(1.15);opacity:1}}
  .l-wind{position:absolute;width:100%;height:100%;pointer-events:none}
  .l-wind-line{
    position:absolute;height:1px;border-radius:1px;
    background:linear-gradient(90deg,transparent,rgba(0,212,255,.5),transparent);
    animation:windBlow linear infinite;
    opacity:0;
  }
  @keyframes windBlow{
    0%{transform:translateX(-120px);opacity:0}
    15%{opacity:1}
    85%{opacity:.6}
    100%{transform:translateX(100vw);opacity:0}
  }
  .l-fan-wrap{position:relative;z-index:2;margin-bottom:36px}
  #loaderFanBlades{transform-origin:50% 50%;animation:fanSpin 0.9s linear infinite}
  #loaderFanBlades.speeding{animation:fanSpinFast 0.3s linear infinite}
  @keyframes fanSpin{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
  @keyframes fanSpinFast{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
  .hub-ring{transform-origin:center;animation:hubRingAnim 2s linear infinite reverse}
  @keyframes hubRingAnim{from{stroke-dashoffset:0}to{stroke-dashoffset:-220}}
  .radar-ring{transform-origin:center;animation:radarSweep 2s linear infinite;transform-box:fill-box}
  @keyframes radarSweep{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
  .l-brand{
    font-family:"Rajdhani",sans-serif;font-size:2.8rem;font-weight:700;
    letter-spacing:10px;text-transform:uppercase;
    background:linear-gradient(135deg,#fff 0%,var(--cyan) 55%,var(--blue) 100%);
    -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
    animation:loaderBrandPulse 1.5s ease-in-out infinite;
    position:relative;z-index:2;
  }
  @keyframes loaderBrandPulse{0%,100%{opacity:.75;letter-spacing:10px}50%{opacity:1;letter-spacing:12px}}
  .l-tagline{
    font-family:"JetBrains Mono",monospace;font-size:.62rem;
    letter-spacing:5px;text-transform:uppercase;color:var(--muted);
    margin-top:10px;position:relative;z-index:2;
    animation:loaderTagPulse 1.5s .3s ease-in-out infinite;
  }
  @keyframes loaderTagPulse{0%,100%{opacity:.4}50%{opacity:.9}}
  .l-progress-wrap{margin-top:28px;width:220px;height:2px;background:var(--border);position:relative;overflow:hidden;z-index:2;}
  .l-progress-bar{height:100%;width:0%;background:linear-gradient(90deg,var(--blue),var(--cyan));box-shadow:0 0 8px var(--cyan);animation:loaderProgress 2.2s cubic-bezier(.4,0,.2,1) forwards;}
  @keyframes loaderProgress{0%{width:0%}60%{width:75%}85%{width:90%}100%{width:100%}}
  .l-status{font-family:"JetBrains Mono",monospace;font-size:.52rem;letter-spacing:3px;color:var(--blue);margin-top:10px;z-index:2;animation:statusCycle 2.2s steps(1) forwards;}

  /* NAV */
  nav{position:fixed;top:0;left:0;right:0;z-index:500;height:64px;padding:0 48px;display:flex;align-items:center;justify-content:space-between;transition:background .4s}
  nav.s{background:rgba(6,8,15,.95);backdrop-filter:blur(20px);border-bottom:1px solid var(--border)}
  .nav-logo{font-family:"Rajdhani",sans-serif;font-size:1.5rem;font-weight:700;letter-spacing:4px;text-decoration:none;background:linear-gradient(135deg,#fff,var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
  .nav-links{display:flex;gap:32px;list-style:none}
  .nav-links a{font-size:.7rem;letter-spacing:2px;text-transform:uppercase;text-decoration:none;color:var(--soft);font-weight:500;transition:color .2s;position:relative}
  .nav-links a::after{content:"";position:absolute;bottom:-3px;left:0;width:0;height:1px;background:var(--cyan);transition:width .3s}
  .nav-links a:hover{color:var(--cyan)}
  .nav-links a:hover::after{width:100%}
  .nav-btn{font-size:.65rem;letter-spacing:2px;text-transform:uppercase;font-weight:600;border:1px solid var(--blue);color:var(--blue);padding:8px 20px;text-decoration:none;transition:all .25s;font-family:"Exo 2",sans-serif}
  .nav-btn:hover{background:var(--blue);color:#fff;box-shadow:0 0 20px rgba(26,111,255,.4)}
  .nav-burger{display:none;flex-direction:column;gap:4px;cursor:pointer}
  .nav-burger span{width:20px;height:1px;background:var(--text);display:block;transition:all .3s}
  .mob-nav{position:fixed;inset:0;background:var(--bg);z-index:490;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:32px;transform:translateX(100%);transition:transform .5s cubic-bezier(.77,0,.18,1)}
  .mob-nav.open{transform:none}
  .mob-nav a{font-family:"Rajdhani",sans-serif;font-size:2.2rem;font-weight:600;letter-spacing:4px;text-transform:uppercase;text-decoration:none;color:var(--text);transition:color .2s}
  .mob-nav a:hover{color:var(--cyan)}

  /* HERO */
  .hero{min-height:100vh;display:flex;align-items:center;position:relative;overflow:hidden;padding:0 48px}
  .hero-grid{position:absolute;inset:0;background-image:linear-gradient(rgba(26,111,255,.04) 1px,transparent 1px),linear-gradient(90deg,rgba(26,111,255,.04) 1px,transparent 1px);background-size:60px 60px;animation:gridShift 20s linear infinite}
  @keyframes gridShift{from{transform:translateY(0)}to{transform:translateY(60px)}}
  .hero-orb1{position:absolute;width:700px;height:700px;border-radius:50%;background:radial-gradient(circle,rgba(26,111,255,.12) 0%,transparent 70%);top:-200px;right:-100px;animation:orbF 8s ease-in-out infinite}
  .hero-orb2{position:absolute;width:500px;height:500px;border-radius:50%;background:radial-gradient(circle,rgba(0,212,255,.07) 0%,transparent 70%);bottom:-150px;left:-50px;animation:orbF 10s ease-in-out infinite reverse}
  @keyframes orbF{0%,100%{transform:translateY(0)}50%{transform:translateY(-30px)}}
  .hero-content{position:relative;z-index:2;max-width:620px}
  .hero-tag{display:inline-flex;align-items:center;gap:8px;border:1px solid rgba(0,212,255,.25);padding:6px 14px;margin-bottom:24px;animation:fadeUp .8s .2s both}
  .hero-tag-dot{width:6px;height:6px;background:var(--cyan);border-radius:50%;animation:blink 1.5s infinite}
  @keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}
  .hero-tag span{font-family:"JetBrains Mono",monospace;font-size:.62rem;letter-spacing:3px;text-transform:uppercase;color:var(--cyan)}
  .hero-h1{font-family:"Rajdhani",sans-serif;font-size:clamp(3rem,8vw,6.5rem);font-weight:700;line-height:.95;letter-spacing:2px;animation:fadeUp .8s .35s both}
  .hero-h1 .l1{display:block;color:var(--text)}
  .hero-h1 .l2{display:block;background:linear-gradient(135deg,var(--blue) 0%,var(--cyan) 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
  .hero-h1 .l3{display:block;color:rgba(232,237,248,.3);font-weight:300}
  .hero-desc{margin-top:24px;font-size:.9rem;color:var(--soft);line-height:1.8;font-weight:300;max-width:480px;animation:fadeUp .8s .5s both}
  .hero-actions{margin-top:36px;display:flex;gap:16px;flex-wrap:wrap;animation:fadeUp .8s .65s both}
  .btn-blue{background:linear-gradient(135deg,var(--blue),#0055cc);color:#fff;padding:13px 32px;font-size:.72rem;letter-spacing:2px;text-transform:uppercase;font-weight:600;text-decoration:none;transition:all .3s;display:inline-block;font-family:"Exo 2",sans-serif}
  .btn-blue:hover{transform:translateY(-2px);box-shadow:0 8px 32px rgba(26,111,255,.45)}
  .btn-ghost{border:1px solid var(--border);color:var(--soft);padding:13px 32px;font-size:.72rem;letter-spacing:2px;text-transform:uppercase;font-weight:500;text-decoration:none;transition:all .3s;display:inline-block;font-family:"Exo 2",sans-serif}
  .btn-ghost:hover{border-color:var(--cyan);color:var(--cyan)}
  .hero-right{position:absolute;right:0;top:50%;transform:translateY(-50%);width:46%;height:78vh;display:grid;grid-template-columns:1fr 1fr;grid-template-rows:1fr 1fr;gap:2px;opacity:.5;animation:fadeUp .8s .3s both}
  .hero-right img{width:100%;height:100%;object-fit:cover;transition:opacity .4s}
  .hero-right img:hover{opacity:.75}
  .hero-fade{position:absolute;right:0;top:0;bottom:0;width:46%;background:linear-gradient(90deg,var(--bg) 0%,transparent 40%)}
  .hero-stats{margin-top:44px;display:flex;gap:36px;animation:fadeUp .8s .8s both}
  .hs-num{font-family:"Rajdhani",sans-serif;font-size:1.8rem;font-weight:700;color:var(--cyan);line-height:1}
  .hs-lbl{font-size:.6rem;letter-spacing:2px;text-transform:uppercase;color:var(--muted);margin-top:2px}
  .hero-scroll{position:absolute;bottom:28px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:8px;animation:fadeUp .8s 1s both}
  .hero-scroll span{font-family:"JetBrains Mono",monospace;font-size:.55rem;letter-spacing:3px;color:var(--muted)}
  .scroll-dot{width:1px;height:40px;background:linear-gradient(to bottom,var(--blue),transparent);animation:sBeat 2s infinite}
  @keyframes sBeat{0%,100%{opacity:.3}50%{opacity:1}}
  @keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}

  /* MARQUEE */
  .mq{background:var(--surface);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:12px 0;overflow:hidden}
  .mq-inner{display:flex;animation:mq 24s linear infinite;white-space:nowrap}
  .mq-item{font-family:"JetBrains Mono",monospace;font-size:.6rem;letter-spacing:4px;text-transform:uppercase;color:var(--muted);padding:0 36px;flex-shrink:0;display:flex;align-items:center;gap:36px}
  .mq-item .dot{color:var(--blue)}
  @keyframes mq{from{transform:translateX(0)}to{transform:translateX(-50%)}}

  /* SECTION */
  section{padding:100px 48px}
  .sec-hd{text-align:center;margin-bottom:60px}
  .sec-tag{display:inline-flex;align-items:center;gap:10px;margin-bottom:12px}
  .sec-tag span{font-family:"JetBrains Mono",monospace;font-size:.6rem;letter-spacing:4px;text-transform:uppercase;color:var(--blue)}
  .sec-tag::before,.sec-tag::after{content:"";width:24px;height:1px;background:var(--blue);opacity:.5}
  .sec-title{font-family:"Rajdhani",sans-serif;font-size:clamp(2rem,5vw,3.5rem);font-weight:700;letter-spacing:1px;color:var(--text);line-height:1.05}
  .hi{color:var(--cyan)}
  .sec-sub{margin-top:12px;font-size:.82rem;color:var(--muted);line-height:1.8;max-width:500px;margin-left:auto;margin-right:auto}

  /* PRODUCT TABS */
  #products{background:var(--bg)}
  .prod-tabs{display:flex;justify-content:center;gap:2px;margin-bottom:48px;flex-wrap:wrap}
  .tab-btn{font-family:"Exo 2",sans-serif;font-size:.7rem;letter-spacing:2px;text-transform:uppercase;font-weight:600;padding:10px 28px;border:1px solid var(--border);background:transparent;color:var(--muted);cursor:pointer;transition:all .25s}
  .tab-btn.active{background:var(--blue);border-color:var(--blue);color:#fff;box-shadow:0 4px 20px rgba(26,111,255,.35)}
  .tab-btn:hover:not(.active){border-color:var(--blue);color:var(--blue)}
  .tab-panel{display:none;animation:fadeUp .4s ease both}
  .tab-panel.active{display:block}
  .prod-grid{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:var(--border)}
  .prod-grid.cols3{grid-template-columns:repeat(3,1fr);max-width:900px}
  .prod-grid.cols2{grid-template-columns:repeat(2,1fr);max-width:640px}
  .prod-card{background:var(--card);position:relative;overflow:hidden;cursor:pointer}
  .prod-img{position:relative;padding-top:100%;overflow:hidden;background:#090c18}
  .prod-img img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;transition:transform .6s ease,filter .4s;filter:brightness(.95)}
  .prod-card:hover .prod-img img{transform:scale(1.06);filter:brightness(1.05)}
  .prod-scan{position:absolute;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,var(--cyan),transparent);top:-2px;opacity:0;transition:opacity .2s}
  .prod-card:hover .prod-scan{opacity:1;animation:scanD 1.2s ease infinite}
  @keyframes scanD{from{top:-2px}to{top:100%}}
  .prod-corner{position:absolute;width:16px;height:16px;opacity:0;transition:opacity .3s}
  .prod-corner.tl{top:8px;left:8px;border-top:1px solid var(--cyan);border-left:1px solid var(--cyan)}
  .prod-corner.br{bottom:8px;right:8px;border-bottom:1px solid var(--cyan);border-right:1px solid var(--cyan)}
  .prod-card:hover .prod-corner{opacity:1}
  .prod-body{padding:16px 18px 20px;border-top:1px solid var(--border)}
  .prod-series{font-family:"JetBrains Mono",monospace;font-size:.56rem;letter-spacing:3px;text-transform:uppercase;color:var(--blue);margin-bottom:5px}
  .prod-name{font-family:"Rajdhani",sans-serif;font-size:1.1rem;font-weight:600;color:var(--text)}
  .prod-specs{margin-top:8px;display:flex;gap:6px;flex-wrap:wrap}
  .spec-tag{font-size:.56rem;letter-spacing:1px;border:1px solid var(--border);color:var(--muted);padding:3px 8px;font-family:"JetBrains Mono",monospace}
  .prod-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(11,14,24,.95) 0%,rgba(11,14,24,.4) 55%,transparent 100%);opacity:0;transition:opacity .4s;display:flex;align-items:flex-end;padding:20px}
  .prod-card:hover .prod-overlay{opacity:1}
  .ov-name{font-family:"Rajdhani",sans-serif;font-size:1.15rem;font-weight:700;color:#fff;margin-bottom:4px}
  .ov-detail{font-size:.68rem;color:rgba(255,255,255,.5);line-height:1.5;margin-bottom:10px}
  .ov-cta{font-size:.6rem;letter-spacing:2px;text-transform:uppercase;color:var(--cyan);font-family:"JetBrains Mono",monospace;display:flex;align-items:center;gap:6px}
  .ov-cta::after{content:"→";transition:transform .2s}
  .prod-card:hover .ov-cta::after{transform:translateX(4px)}

  .cat-badge{display:inline-block;font-family:"JetBrains Mono",monospace;font-size:.55rem;letter-spacing:2px;text-transform:uppercase;padding:2px 8px;margin-bottom:6px;border:1px solid}
  .cat-badge.table{color:#00d4ff;border-color:rgba(0,212,255,.35);background:rgba(0,212,255,.06)}
  .cat-badge.wall{color:#a78bfa;border-color:rgba(167,139,250,.35);background:rgba(167,139,250,.06)}
  .cat-badge.compact{color:#34d399;border-color:rgba(52,211,153,.35);background:rgba(52,211,153,.06)}

  /* FEATURES */
  #features{background:var(--surface)}
  .feat-grid{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--border)}
  .feat-item{background:var(--card);padding:40px 32px;transition:background .3s}
  .feat-item:hover{background:#121525}
  .feat-icon{width:48px;height:48px;border:1px solid var(--border);display:flex;align-items:center;justify-content:center;font-size:1.3rem;margin-bottom:20px;transition:border-color .3s;position:relative}
  .feat-item:hover .feat-icon{border-color:var(--blue)}
  .feat-num{font-family:"JetBrains Mono",monospace;font-size:.56rem;letter-spacing:3px;color:var(--blue);margin-bottom:8px}
  .feat-title{font-family:"Rajdhani",sans-serif;font-size:1.1rem;font-weight:600;color:var(--text);margin-bottom:8px}
  .feat-desc{font-size:.75rem;color:var(--muted);line-height:1.8}

  /* ABOUT */
  .about-strip{background:var(--bg);padding:100px 48px}
  .about-inner{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:center}
  .about-visual{display:grid;grid-template-columns:1fr 1fr;gap:3px}
  .about-visual img{width:100%;aspect-ratio:1;object-fit:cover;filter:brightness(.88) saturate(.85);transition:all .5s}
  .about-visual img:hover{filter:brightness(1.05) saturate(1.1)}
  .about-visual .span2{grid-column:span 2;aspect-ratio:2/1}
  .about-body{margin-top:24px;font-size:.82rem;color:var(--muted);line-height:2;font-weight:300}
  .about-stats{margin-top:40px;display:grid;grid-template-columns:repeat(3,1fr);gap:20px;border-top:1px solid var(--border);padding-top:28px}
  .a-stat-num{font-family:"Rajdhani",sans-serif;font-size:2.2rem;font-weight:700;color:var(--blue);line-height:1}
  .a-stat-lbl{font-size:.58rem;letter-spacing:2px;text-transform:uppercase;color:var(--muted);margin-top:3px}

  /* CONTACT */
  #contact{background:var(--surface);padding:100px 48px;position:relative;overflow:hidden}
  #contact::before{content:"";position:absolute;width:600px;height:600px;border-radius:50%;background:radial-gradient(circle,rgba(26,111,255,.05) 0%,transparent 70%);right:-200px;top:-200px;pointer-events:none}
  .contact-inner{max-width:1000px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:80px}
  .contact-body{margin-top:16px;font-size:.8rem;color:var(--muted);line-height:1.9}
  .c-items{margin-top:36px;display:flex;flex-direction:column;gap:0}
  .c-item{padding:20px 0;border-bottom:1px solid var(--border);display:flex;gap:16px;align-items:flex-start}
  .c-item:first-child{border-top:1px solid var(--border)}
  .c-icon{width:36px;height:36px;border:1px solid var(--border);display:flex;align-items:center;justify-content:center;font-size:.9rem;flex-shrink:0;transition:border-color .3s}
  .c-item:hover .c-icon{border-color:var(--blue)}
  .c-label{font-family:"JetBrains Mono",monospace;font-size:.56rem;letter-spacing:3px;text-transform:uppercase;color:var(--blue);margin-bottom:5px}
  .c-val{font-size:.78rem;color:var(--soft);line-height:1.6}
  .c-val a{color:var(--soft);text-decoration:none;transition:color .2s}
  .c-val a:hover{color:var(--cyan)}
  .c-form{display:flex;flex-direction:column;gap:14px}
  .f-group{display:flex;flex-direction:column;gap:5px}
  .f-label{font-family:"JetBrains Mono",monospace;font-size:.56rem;letter-spacing:2px;text-transform:uppercase;color:var(--muted)}
  .f-in,.f-ta{background:rgba(255,255,255,.02);border:1px solid var(--border);color:var(--text);padding:11px 14px;font-family:"Exo 2",sans-serif;font-size:.78rem;font-weight:300;outline:none;transition:border-color .3s;width:100%;resize:none}
  .f-in:focus,.f-ta:focus{border-color:var(--blue);box-shadow:0 0 0 3px rgba(26,111,255,.08)}
  .f-in::placeholder,.f-ta::placeholder{color:var(--muted)}
  .f-ta{height:110px}
  .f-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}
  .f-btn{background:linear-gradient(135deg,var(--blue),#0055cc);color:#fff;border:none;padding:13px 32px;font-size:.68rem;letter-spacing:2px;text-transform:uppercase;font-weight:600;cursor:pointer;transition:all .3s;align-self:flex-start;font-family:"Exo 2",sans-serif;margin-top:4px}
  .f-btn:hover{transform:translateY(-2px);box-shadow:0 8px 28px rgba(26,111,255,.45)}
  .f-ok{display:none;font-family:"JetBrains Mono",monospace;font-size:.66rem;letter-spacing:2px;color:var(--cyan);margin-top:8px}

  /* FOOTER */
  footer{background:var(--bg);border-top:1px solid var(--border);padding:32px 48px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:16px}
  .f-brand{font-family:"Rajdhani",sans-serif;font-size:1.2rem;font-weight:700;letter-spacing:4px;background:linear-gradient(135deg,#fff,var(--cyan));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
  .f-copy{font-family:"JetBrains Mono",monospace;font-size:.56rem;letter-spacing:2px;color:var(--muted);text-transform:uppercase}
  .f-links{display:flex;gap:24px}
  .f-links a{font-size:.58rem;letter-spacing:2px;text-transform:uppercase;color:var(--muted);text-decoration:none;transition:color .2s}
  .f-links a:hover{color:var(--cyan)}

  /* REVEAL using IntersectionObserver (initial hidden) */
  .rv{opacity:0;transform:translateY(28px);transition:opacity .7s ease,transform .7s ease}
  .rv.in{opacity:1;transform:none}
  .rv-l{opacity:0;transform:translateX(-28px);transition:opacity .7s ease,transform .7s ease}
  .rv-l.in{opacity:1;transform:none}
  .rv-r{opacity:0;transform:translateX(28px);transition:opacity .7s ease,transform .7s ease}
  .rv-r.in{opacity:1;transform:none}

  @media(max-width:1024px){.prod-grid{grid-template-columns:repeat(2,1fr)!important}.prod-grid.cols3{grid-template-columns:repeat(2,1fr)!important}.feat-grid{grid-template-columns:repeat(2,1fr)}}
  @media(max-width:768px){
    nav{padding:0 20px}.nav-links,.nav-btn{display:none}.nav-burger{display:flex}
    section,.hero,.about-strip{padding:60px 20px}.hero{padding:80px 20px 60px}
    .hero-right,.hero-fade{display:none}
    .about-inner,.contact-inner{grid-template-columns:1fr;gap:40px}
    .prod-grid{grid-template-columns:1fr 1fr!important;max-width:100%!important}
    .feat-grid{grid-template-columns:1fr}
    footer{flex-direction:column;align-items:center;text-align:center;padding:24px 20px}
    .f-row{grid-template-columns:1fr}
    .prod-tabs{gap:4px}
    .tab-btn{padding:8px 16px;font-size:.62rem}
  }
  @media(max-width:480px){.prod-grid{grid-template-columns:1fr!important}}
</style>
</head>
<body>

<div id="cur"></div>
<div id="cur-ring"></div>

<div id="loader">
  <div class="l-glow"></div>
  <div class="l-wind" id="lWind"></div>
  <div class="l-fan-wrap">
    <svg id="loaderFanSvg" width="220" height="220" viewBox="0 0 220 220" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <radialGradient id="bladeGrad" cx="50%" cy="50%" r="50%">
          <stop offset="0%" stop-color="#00d4ff" stop-opacity="0.9"/>
          <stop offset="100%" stop-color="#1a6fff" stop-opacity="0.7"/>
        </radialGradient>
        <radialGradient id="hubGrad" cx="40%" cy="35%" r="60%">
          <stop offset="0%" stop-color="#2a9fff"/>
          <stop offset="100%" stop-color="#0a3080"/>
        </radialGradient>
        <filter id="bladeGlow"><feGaussianBlur stdDeviation="3" result="blur"/><feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
        <filter id="hubGlow"><feGaussianBlur stdDeviation="5" result="blur"/><feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
      </defs>
      <g class="radar-ring" style="transform-origin:110px 110px">
        <circle cx="110" cy="110" r="100" fill="none" stroke="rgba(26,111,255,.08)" stroke-width="1"/>
        <path d="M110,110 L110,10 A100,100 0 0,1 195,60 Z" fill="url(#bladeGrad)" opacity="0.07"/>
      </g>
      <circle cx="110" cy="110" r="100" fill="none" stroke="rgba(0,212,255,.12)" stroke-width=".5" stroke-dasharray="4 6"/>
      <circle cx="110" cy="110" r="88" fill="none" stroke="rgba(26,111,255,.08)" stroke-width=".5"/>
      <g id="loaderFanBlades">
        <path d="M110,110 C105,90 95,55 110,18 C120,18 135,30 130,55 C127,70 118,90 110,110Z" fill="url(#bladeGrad)" filter="url(#bladeGlow)" opacity="0.92"/>
        <path d="M110,110 C107,92 100,62 111,28 C114,28 118,35 116,55 C114,68 112,90 110,110Z" fill="rgba(255,255,255,.15)"/>
        <path d="M110,110 C128,118 161,124 193,107 C198,117 194,134 170,141 C156,145 136,138 110,110Z" fill="url(#bladeGrad)" filter="url(#bladeGlow)" opacity="0.92"/>
        <path d="M110,110 C126,117 154,122 186,110 C188,115 185,122 170,127 C158,131 136,126 110,110Z" fill="rgba(255,255,255,.15)"/>
        <path d="M110,110 C92,118 59,152 42,183 C32,178 28,161 45,143 C56,130 78,120 110,110Z" fill="url(#bladeGrad)" filter="url(#bladeGlow)" opacity="0.92"/>
        <path d="M110,110 C94,118 65,148 50,174 C44,170 42,163 54,150 C64,138 82,122 110,110Z" fill="rgba(255,255,255,.15)"/>
        <circle cx="110" cy="110" r="22" fill="none" stroke="rgba(0,212,255,.35)" stroke-width="1" stroke-dasharray="8 4" class="hub-ring"/>
        <circle cx="110" cy="110" r="18" fill="url(#hubGrad)" filter="url(#hubGlow)"/>
        <circle cx="104" cy="104" r="6" fill="rgba(255,255,255,.2)"/>
        <circle cx="110" cy="110" r="4" fill="#00d4ff" opacity=".9"/>
        <circle cx="110" cy="110" r="2" fill="#fff"/>
      </g>
      <circle cx="110" cy="110" r="26" fill="none" stroke="rgba(0,212,255,.2)" stroke-width=".5"/>
      <rect x="108" y="8" width="4" height="10" rx="2" fill="rgba(0,212,255,.3)"/>
      <circle cx="110" cy="8" r="4" fill="rgba(26,111,255,.5)" stroke="rgba(0,212,255,.4)" stroke-width=".5"/>
    </svg>
  </div>
  <div class="l-brand">C-LITE</div>
  <div class="l-tagline">Vanya Electrical &nbsp;·&nbsp; Delhi</div>
  <div class="l-progress-wrap"><div class="l-progress-bar" id="lBar"></div></div>
  <div class="l-status" id="lStatus">INITIALISING SYSTEMS</div>
</div>

<div class="mob-nav" id="mobNav">
  <a href="#products" data-mob-link>Products</a>
  <a href="#features" data-mob-link>Features</a>
  <a href="#about" data-mob-link>About</a>
  <a href="#contact" data-mob-link>Contact</a>
</div>

<nav id="nav">
  <a href="#" class="nav-logo">C-LITE</a>
  <ul class="nav-links">
    <li><a href="#products">Products</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#contact" class="nav-btn">Get Quote</a>
  <div class="nav-burger" id="burger"><span></span><span></span><span></span></div>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-grid"></div><div class="hero-orb1"></div><div class="hero-orb2"></div>
  <div class="hero-content">
    <div class="hero-tag"><div class="hero-tag-dot"></div><span>Vanya Electrical — Delhi</span></div>
    <h1 class="hero-h1"><span class="l1">NEXT-GEN</span><span class="l2">AIRFLOW</span><span class="l3">TECHNOLOGY</span></h1>
    <p class="hero-desc">Precision-engineered fans designed for maximum performance, minimum energy consumption and lasting style. Ceiling fans, table fans and wall fans — built in Delhi, trusted across India.</p>
    <div class="hero-actions"><a href="#products" class="btn-blue">Explore Products</a><a href="#contact" class="btn-ghost">Dealer Enquiry</a></div>
    <div class="hero-stats"><div><div class="hs-num">16+</div><div class="hs-lbl">Models</div></div><div><div class="hs-num">BEE★</div><div class="hs-lbl">Star Rated</div></div><div><div class="hs-num">5yr</div><div class="hs-lbl">Warranty</div></div></div>
  </div>
  <div class="hero-right">
    <img src="https://picsum.photos/id/20/400/400" alt="Fan design"><img src="https://picsum.photos/id/21/400/400" alt="Fan detail"><img src="https://picsum.photos/id/22/400/400" alt="Fan blade"><img src="https://picsum.photos/id/23/400/400" alt="Fan motor">
  </div>
  <div class="hero-fade"></div>
  <div class="hero-scroll"><span>Scroll</span><div class="scroll-dot"></div></div>
</section>

<!-- MARQUEE -->
<div class="mq"><div class="mq-inner"><div class="mq-item">Ceiling Fans <span class="dot">◆</span> Table Fans <span class="dot">◆</span> Wall Fans <span class="dot">◆</span> Energy Efficient <span class="dot">◆</span> BEE Star Rated <span class="dot">◆</span> C-Lite by Vanya Electrical <span class="dot">◆</span> Bawana Delhi <span class="dot">◆</span></div><div class="mq-item">Ceiling Fans <span class="dot">◆</span> Table Fans <span class="dot">◆</span> Wall Fans <span class="dot">◆</span> Energy Efficient <span class="dot">◆</span> BEE Star Rated <span class="dot">◆</span> C-Lite by Vanya Electrical <span class="dot">◆</span> Bawana Delhi <span class="dot">◆</span></div><div class="mq-item">Ceiling Fans <span class="dot">◆</span> Table Fans <span class="dot">◆</span> Wall Fans <span class="dot">◆</span> Energy Efficient <span class="dot">◆</span> BEE Star Rated <span class="dot">◆</span> C-Lite by Vanya Electrical <span class="dot">◆</span> Bawana Delhi <span class="dot">◆</span></div></div></div>

<!-- PRODUCTS -->
<section id="products">
  <div class="sec-hd rv"><div class="sec-tag"><span>Our Range</span></div><h2 class="sec-title">The <span class="hi">C-Lite</span> Collection</h2><p class="sec-sub">Three categories, one standard of quality — engineered for every space in your home or office.</p></div>
  <div class="prod-tabs rv" role="tablist" aria-label="Product categories">
    <button class="tab-btn active" id="tab-ceiling-btn" role="tab" aria-selected="true" aria-controls="tab-ceiling">⟳ Ceiling Fans</button>
    <button class="tab-btn" id="tab-table-btn" role="tab" aria-selected="false" aria-controls="tab-table">⊙ Table Fans</button>
    <button class="tab-btn" id="tab-small-btn" role="tab" aria-selected="false" aria-controls="tab-small">◈ Compact Fans</button>
  </div>
  <!-- CEILING FANS -->
  <div class="tab-panel active" id="tab-ceiling" role="tabpanel" aria-labelledby="tab-ceiling-btn">
    <div class="prod-grid">
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/1/400/400" alt="Indigo Breeze"><div class="prod-overlay"><div><div class="ov-name">Indigo Breeze</div><div class="ov-detail">3-blade · 1200mm · Indigo Blue</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 01</div><div class="prod-name">Indigo Breeze</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">74W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/2/400/400" alt="Obsidian Copper"><div class="prod-overlay"><div><div class="ov-name">Obsidian Copper</div><div class="ov-detail">3-blade · 1200mm · Matt Black + Copper</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 02</div><div class="prod-name">Obsidian Copper</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">72W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/3/400/400" alt="Shadow Pro"><div class="prod-overlay"><div><div class="ov-name">Shadow Pro</div><div class="ov-detail">3-blade · 1200mm · Charcoal + Copper</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 03</div><div class="prod-name">Shadow Pro</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">72W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/4/400/400" alt="Noir Petal"><div class="prod-overlay"><div><div class="ov-name">Noir Petal</div><div class="ov-detail">3-blade · 1200mm · Floral accent</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 04</div><div class="prod-name">Noir Petal</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">70W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/5/400/400" alt="Aura Dark"><div class="prod-overlay"><div><div class="ov-name">Aura Dark</div><div class="ov-detail">3-blade · 1200mm · Rose gold leaf motif</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 05</div><div class="prod-name">Aura Dark</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">70W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/6/400/400" alt="Eclipse"><div class="prod-overlay"><div><div class="ov-name">Eclipse</div><div class="ov-detail">3-blade · 1200mm · Copper circle ring</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 06</div><div class="prod-name">Eclipse</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">72W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/7/400/400" alt="Heritage Brown"><div class="prod-overlay"><div><div class="ov-name">Heritage Brown</div><div class="ov-detail">3-blade · 1200mm · Classic brown</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 07</div><div class="prod-name">Heritage Brown</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">75W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/8/400/400" alt="Ivory Gold"><div class="prod-overlay"><div><div class="ov-name">Ivory Gold</div><div class="ov-detail">3-blade · 1200mm · Ivory + Gold trim</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-SERIES / 08</div><div class="prod-name">Ivory Gold</div><div class="prod-specs"><span class="spec-tag">1200mm</span><span class="spec-tag">3-Blade</span><span class="spec-tag">74W</span></div></div></div>
    </div>
  </div>
  <!-- TABLE FANS -->
  <div class="tab-panel" id="tab-table" role="tabpanel" aria-labelledby="tab-table-btn">
    <div class="prod-grid cols3">
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/9/400/400" alt="Breeze Table"><div class="prod-overlay"><div><div class="ov-name">Breeze Table</div><div class="ov-detail">400mm · 3-speed · Quiet operation</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-TABLE / 01</div><div class="prod-name">Breeze Table</div><div class="prod-specs"><span class="spec-tag">400mm</span><span class="spec-tag">40W</span><span class="spec-tag">3-Speed</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/10/400/400" alt="C-Lite Desk"><div class="prod-overlay"><div><div class="ov-name">C-Lite Desk</div><div class="ov-detail">350mm · Compact design</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-TABLE / 02</div><div class="prod-name">C-Lite Desk</div><div class="prod-specs"><span class="spec-tag">350mm</span><span class="spec-tag">35W</span><span class="spec-tag">Adjustable tilt</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/11/400/400" alt="Industrial Pro"><div class="prod-overlay"><div><div class="ov-name">Industrial Pro</div><div class="ov-detail">450mm · High airflow</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-TABLE / 03</div><div class="prod-name">Industrial Pro</div><div class="prod-specs"><span class="spec-tag">450mm</span><span class="spec-tag">55W</span><span class="spec-tag">Metal blades</span></div></div></div>
    </div>
  </div>
  <!-- COMPACT FANS -->
  <div class="tab-panel" id="tab-small" role="tabpanel" aria-labelledby="tab-small-btn">
    <div class="prod-grid cols2">
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/12/400/400" alt="Wall Breeze"><div class="prod-overlay"><div><div class="ov-name">Wall Breeze</div><div class="ov-detail">300mm wall fan · 2-speed</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-COMPACT / 01</div><div class="prod-name">Wall Breeze</div><div class="prod-specs"><span class="spec-tag">300mm</span><span class="spec-tag">30W</span></div></div></div>
      <div class="prod-card rv"><div class="prod-img"><div class="prod-scan"></div><div class="prod-corner tl"></div><div class="prod-corner br"></div><img src="https://picsum.photos/id/13/400/400" alt="Mini Jet"><div class="prod-overlay"><div><div class="ov-name">Mini Jet</div><div class="ov-detail">250mm personal fan · USB ready</div><div class="ov-cta">Enquire Now</div></div></div></div><div class="prod-body"><div class="prod-series">CL-COMPACT / 02</div><div class="prod-name">Mini Jet</div><div class="prod-specs"><span class="spec-tag">250mm</span><span class="spec-tag">15W</span><span class="spec-tag">USB</span></div></div></div>
    </div>
  </div>
</section>

<!-- FEATURES etc. (unchanged but keep structure) -->
<section id="features"><div class="sec-hd rv"><div class="sec-tag"><span>Why choose us</span></div><h2 class="sec-title">Engineered for <span class="hi">excellence</span></h2><p class="sec-sub">Superior technology meets modern aesthetics — every fan is a statement.</p></div>
<div class="feat-grid"><div class="feat-item rv"><div class="feat-icon">⚡</div><div class="feat-num">01</div><div class="feat-title">Energy Efficient</div><div class="feat-desc">BEE Star rated motors that save up to 35% electricity without compromising airflow.</div></div>
<div class="feat-item rv"><div class="feat-icon">🌀</div><div class="feat-num">02</div><div class="feat-title">High Air Delivery</div><div class="feat-desc">Optimised blade pitch and aerodynamic design for maximum air circulation.</div></div>
<div class="feat-item rv"><div class="feat-icon">🔇</div><div class="feat-num">03</div><div class="feat-title">Silent Operation</div><div class="feat-desc">Precision ball bearings and noise-dampening technology for whisper-quiet performance.</div></div></div></section>

<section class="about-strip" id="about"><div class="about-inner"><div class="about-visual"><img src="https://picsum.photos/id/14/400/400" alt="Factory"><img src="https://picsum.photos/id/15/400/400" alt="Craftsmanship"><img class="span2" src="https://picsum.photos/id/16/800/400" alt="Assembly"></div><div><div class="sec-tag"><span>Our story</span></div><h2 class="sec-title">C-Lite by <span class="hi">Vanya Electrical</span></h2><div class="about-body">Based in Bawana, Delhi, we’ve been manufacturing high-quality fans for over a decade. Our commitment to innovation and reliability has made C-Lite a trusted name across India. Every fan undergoes rigorous testing to ensure it meets the highest standards of performance and durability.</div><div class="about-stats"><div><div class="a-stat-num">10+</div><div class="a-stat-lbl">Years</div></div><div><div class="a-stat-num">500+</div><div class="a-stat-lbl">Dealers</div></div><div><div class="a-stat-num">100k+</div><div class="a-stat-lbl">Units sold</div></div></div></div></div></section>

<section id="contact"><div class="contact-inner"><div><div class="sec-tag"><span>Get in touch</span></div><h2 class="sec-title">Let’s talk.</h2><div class="contact-body">Have a question about our products or want to become a dealer? Reach out to us — we’d love to hear from you.</div><div class="c-items"><div class="c-item"><div class="c-icon">📍</div><div><div class="c-label">Visit us</div><div class="c-val">C-Lite by Vanya Electrical, Bawana Industrial Area, Delhi - 110039</div></div></div><div class="c-item"><div class="c-icon">📞</div><div><div class="c-label">Call us</div><div class="c-val"><a href="tel:+911234567890">+91 123 456 7890</a></div></div></div><div class="c-item"><div class="c-icon">✉️</div><div><div class="c-label">Email us</div><div class="c-val"><a href="mailto:info@clitefans.com">info@clitefans.com</a></div></div></div></div></div><div><form id="contactForm" class="c-form"><div class="f-row"><div class="f-group"><label class="f-label">Name</label><input type="text" class="f-in" placeholder="Your name" required></div><div class="f-group"><label class="f-label">Email</label><input type="email" class="f-in" placeholder="you@example.com" required></div></div><div class="f-group"><label class="f-label">Message</label><textarea class="f-ta" placeholder="Tell us about your requirement..."></textarea></div><button type="submit" class="f-btn">Send message</button><div class="f-ok" id="formOk">✓ Thank you! We'll get back soon.</div></form></div></div></section>

<footer><div class="f-brand">C-LITE</div><div class="f-copy">© 2025 Vanya Electrical — Delhi</div><div class="f-links"><a href="#">Privacy</a><a href="#">Terms</a><a href="#">Support</a></div></footer>

<script>
  (function(){
    // --- Loader and wind animation cleanup
    let windInterval;
    function startWindLines() {
      const windContainer = document.getElementById('lWind');
      if(!windContainer) return;
      function addWindLine() {
        const line = document.createElement('div');
        line.className = 'l-wind-line';
        const duration = 2 + Math.random() * 3;
        line.style.animationDuration = duration + 's';
        line.style.top = Math.random() * 100 + '%';
        line.style.width = (50 + Math.random() * 100) + 'px';
        windContainer.appendChild(line);
        setTimeout(() => { if(line && line.remove) line.remove(); }, duration * 1000);
      }
      windInterval = setInterval(addWindLine, 200);
    }
    function stopWindLines() { if(windInterval) { clearInterval(windInterval); windInterval = null; } }
    startWindLines();
    // Remove loader after progress bar animation ends (using transitionend / animationend)
    const loader = document.getElementById('loader');
    const progressBar = document.getElementById('lBar');
    const removeLoader = () => {
      stopWindLines();
      loader.classList.add('out');
      setTimeout(() => { if(loader && loader.remove) loader.remove(); }, 1000);
    };
    if(progressBar) {
      progressBar.addEventListener('animationend', removeLoader, { once: true });
    } else {
      setTimeout(removeLoader, 2200);
    }

    // --- Custom cursor (do not hide default)
    const cur = document.getElementById('cur');
    const curRing = document.getElementById('cur-ring');
    if(cur && curRing) {
      document.body.style.cursor = 'auto';
      document.addEventListener('mousemove', (e) => {
        cur.style.transform = `translate(${e.clientX}px, ${e.clientY}px) translate(-50%,-50%)`;
        curRing.style.transform = `translate(${e.clientX}px, ${e.clientY}px) translate(-50%,-50%)`;
      });
      const links = document.querySelectorAll('a, button, .tab-btn, .nav-burger, .f-btn');
      links.forEach(link => {
        link.addEventListener('mouseenter', () => document.body.classList.add('h'));
        link.addEventListener('mouseleave', () => document.body.classList.remove('h'));
      });
    }

    // --- Navbar scroll effect
    const nav = document.getElementById('nav');
    window.addEventListener('scroll', () => { if(window.scrollY > 50) nav.classList.add('s'); else nav.classList.remove('s'); });

    // --- Mobile menu
    const burger = document.getElementById('burger');
    const mobNav = document.getElementById('mobNav');
    function toggleMob() { mobNav.classList.toggle('open'); burger.setAttribute('aria-expanded', mobNav.classList.contains('open')); }
    function closeMob() { mobNav.classList.remove('open'); burger.setAttribute('aria-expanded', 'false'); }
    if(burger && mobNav) {
      burger.addEventListener('click', toggleMob);
      document.querySelectorAll('[data-mob-link]').forEach(link => link.addEventListener('click', closeMob));
    }

    // --- Product tabs with ARIA
    const tabBtns = document.querySelectorAll('.tab-btn');
    const panels = document.querySelectorAll('.tab-panel');
    function switchTab(tabId, btnElement) {
      panels.forEach(panel => { panel.classList.remove('active'); panel.setAttribute('aria-hidden', 'true'); });
      tabBtns.forEach(btn => { btn.classList.remove('active'); btn.setAttribute('aria-selected', 'false'); });
      const activePanel = document.getElementById(tabId);
      if(activePanel) { activePanel.classList.add('active'); activePanel.setAttribute('aria-hidden', 'false'); }
      if(btnElement) { btnElement.classList.add('active'); btnElement.setAttribute('aria-selected', 'true'); }
    }
    tabBtns.forEach(btn => {
      btn.addEventListener('click', (e) => {
        const targetId = btn.id.replace('-btn', '');
        switchTab(`tab-${targetId}`, btn);
      });
    });

    // --- IntersectionObserver for reveal animations (replaces scroll listener)
    const revealElements = document.querySelectorAll('.rv, .rv-l, .rv-r');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if(entry.isIntersecting) {
          entry.target.classList.add('in');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.15, rootMargin: '0px 0px -20px 0px' });
    revealElements.forEach(el => observer.observe(el));

    // --- Contact form simple handling
    const contactForm = document.getElementById('contactForm');
    const formOk = document.getElementById('formOk');
    if(contactForm) {
      contactForm.addEventListener('submit', (e) => {
        e.preventDefault();
        if(formOk) formOk.style.display = 'block';
        contactForm.reset();
        setTimeout(() => { if(formOk) formOk.style.display = 'none'; }, 3000);
      });
    }
  })();
</script>
</body>
</html>
