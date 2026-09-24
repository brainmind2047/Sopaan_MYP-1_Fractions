<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Fractions</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Grade 6 Mathematics · Chapter 6</div>
  <div class="chapter-title">Fractions</div>
  <div class="chapter-sub">Exercises 6A–6J · Review Sets · Step-by-Step Practice</div><div class="chapter-credit">Follows Haese Mathematics 6 (MYP 1), Chapter 6</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Grade 6 Mathematics<br>Exercises follow the structure of <i>Mathematics 6 (MYP 1), 3rd edition</i>, Haese Mathematics. Questions, steps and solutions written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).replace(/\s+/g,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[];
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')') && (a.k==='n'||a.k==='v'||a.k==='(')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(\d+)(?: |\+|-)(\d+)\/(\d+)$/))){ if(+m[3]===0) return null; return {v:+m[1]+m[2]/m[3],form:'mixed',w:+m[1],n:+m[2],d:+m[3]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ return wordsNorm(a)===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null) return Math.abs(n1-n2)<1e-3;
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var SECTIONS = [{"id": "s1", "label": "Ex 6A", "sub": "Fractions", "slides": [{"kind": "blank", "p": "State the numerator of each fraction:", "tag": "", "marks": "", "flat": [{"t": "a) {2/7} → __B1__", "a": {"B1": "2"}}, {"t": "b) {5/9} → __B1__", "a": {"B1": "5"}}, {"t": "c) {3/4} → __B1__", "a": {"B1": "3"}}, {"t": "d) {1/6} → __B1__", "a": {"B1": "1"}}], "sol": "The numerator is the top number: the number of parts we are looking at."}, {"kind": "blank", "p": "State the denominator of each fraction:", "tag": "", "marks": "", "flat": [{"t": "a) {2/7} → __B1__", "a": {"B1": "7"}}, {"t": "b) {5/9} → __B1__", "a": {"B1": "9"}}, {"t": "c) {3/4} → __B1__", "a": {"B1": "4"}}, {"t": "d) {1/6} → __B1__", "a": {"B1": "6"}}], "sol": "The denominator is the bottom number: the number of equal parts in a whole."}, {"kind": "blank", "p": "How many equal parts are there if a whole is divided into:", "tag": "", "marks": "", "flat": [{"t": "a) halves → __B1__", "a": {"B1": "2"}}, {"t": "b) fifths → __B1__", "a": {"B1": "5"}}, {"t": "c) eighths → __B1__", "a": {"B1": "8"}}, {"t": "d) ninths → __B1__", "a": {"B1": "9"}}, {"t": "e) twentieths → __B1__", "a": {"B1": "20"}}, {"t": "f) thousandths → __B1__", "a": {"B1": "1000"}}], "sol": "The name tells you the denominator."}, {"kind": "blank", "p": "Write as a fraction (e.g. {3/4}):", "tag": "", "marks": "", "flat": [{"t": "a) two thirds → __B1__", "a": {"B1": "2/3"}, "expr": "fe"}, {"t": "b) five sixths → __B1__", "a": {"B1": "5/6"}, "expr": "fe"}, {"t": "c) three tenths → __B1__", "a": {"B1": "3/10"}, "expr": "fe"}, {"t": "d) seven twelfths → __B1__", "a": {"B1": "7/12"}, "expr": "fe"}, {"t": "e) nine hundredths → __B1__", "a": {"B1": "9/100"}, "expr": "fe"}, {"t": "f) four ninths → __B1__", "a": {"B1": "4/9"}, "expr": "fe"}], "sol": "The number word is the numerator; the part name gives the denominator.\na) {2/3}\nb) {5/6}\nc) {3/10}\nd) {7/12}\ne) {9/100}\nf) {4/9}"}, {"kind": "blank", "p": "Write in words:", "tag": "", "marks": "", "flat": [{"t": "a) {3/5} → __B1__", "a": {"B1": "three fifths"}, "expr": "words"}, {"t": "b) {1/4} → __B1__", "a": {"B1": "one quarter"}, "expr": "words", "accept": ["one fourth", "a quarter"]}, {"t": "c) {5/8} → __B1__", "a": {"B1": "five eighths"}, "expr": "words"}, {"t": "d) {7/10} → __B1__", "a": {"B1": "seven tenths"}, "expr": "words"}, {"t": "e) {2/9} → __B1__", "a": {"B1": "two ninths"}, "expr": "words"}, {"t": "f) {11/12} → __B1__", "a": {"B1": "eleven twelfths"}, "expr": "words"}], "sol": "Say the numerator, then the name of the parts (plural if the numerator is more than 1)."}, {"kind": "blank", "p": "What fraction of each diagram is shaded?", "tag": "", "marks": "", "flat": [{"t": "a) __B1__", "a": {"B1": "1/4"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 120 72\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" x=\"34.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"60.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"34.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"60.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/></svg>", "expr": "fv"}, {"t": "b) __B1__", "a": {"B1": "2/3"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 120 46\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" x=\"21.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"47.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"73.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/></svg>", "expr": "fv"}, {"t": "c) __B1__", "a": {"B1": "3/8"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,10.0 A34,34 0 0 1 174.0,20.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L174.0,20.0 A34,34 0 0 1 184.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L184.0,44.0 A34,34 0 0 1 174.0,68.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L174.0,68.0 A34,34 0 0 1 150.0,78.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,78.0 A34,34 0 0 1 126.0,68.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L126.0,68.0 A34,34 0 0 1 116.0,44.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L116.0,44.0 A34,34 0 0 1 126.0,20.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L126.0,20.0 A34,34 0 0 1 150.0,10.0 Z\"/></svg>", "expr": "fv"}, {"t": "d) __B1__", "a": {"B1": "5/12"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 124 98\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" x=\"10.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"36.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"62.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"88.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"10.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"36.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"62.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"88.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"10.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"36.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"62.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"88.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/></svg>", "expr": "fv"}, {"t": "e) __B1__", "a": {"B1": "5/6"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,10.0 A34,34 0 0 1 179.4,27.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L179.4,27.0 A34,34 0 0 1 179.4,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L179.4,61.0 A34,34 0 0 1 150.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,78.0 A34,34 0 0 1 120.6,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L120.6,61.0 A34,34 0 0 1 120.6,27.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L120.6,27.0 A34,34 0 0 1 150.0,10.0 Z\"/></svg>", "expr": "fv"}, {"t": "f) __B1__", "a": {"B1": "7/10"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 150 72\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" x=\"10.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"36.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"62.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"88.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"114.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"10.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"36.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"62.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"88.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"114.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/></svg>", "expr": "fv"}], "sol": "Count the shaded parts (numerator) and all the equal parts (denominator).\na) {1/4}\nb) {2/3}\nc) {3/8}\nd) {5/12}\ne) {5/6}\nf) {7/10}"}, {"kind": "blank", "p": "What fraction of the dots are red?", "tag": "", "marks": "", "flat": [{"t": "a) __B1__", "a": {"B1": "5/8"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 228 42\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><circle class=\"dr\" cx=\"23.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"49.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"75.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"101.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"127.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"153.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"179.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"205.0\" cy=\"20\" r=\"9\"/></svg>", "expr": "fv"}, {"t": "b) __B1__", "a": {"B1": "4/10"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 228 68\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><circle class=\"dr\" cx=\"23.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"49.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"75.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"101.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"127.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"153.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"179.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"205.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"23.0\" cy=\"46\" r=\"9\"/><circle class=\"dw\" cx=\"49.0\" cy=\"46\" r=\"9\"/></svg>", "expr": "fv"}, {"t": "c) __B1__", "a": {"B1": "7/12"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 228 68\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><circle class=\"dr\" cx=\"23.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"49.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"75.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"101.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"127.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"153.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"179.0\" cy=\"20\" r=\"9\"/><circle class=\"dw\" cx=\"205.0\" cy=\"20\" r=\"9\"/><circle class=\"dr\" cx=\"23.0\" cy=\"46\" r=\"9\"/><circle class=\"dw\" cx=\"49.0\" cy=\"46\" r=\"9\"/><circle class=\"dr\" cx=\"75.0\" cy=\"46\" r=\"9\"/><circle class=\"dw\" cx=\"101.0\" cy=\"46\" r=\"9\"/></svg>", "expr": "fv"}], "sol": "Red dots ÷ total dots.\na) 5 of 8: {5/8}\nb) 4 of 10: {4/10} = {2/5}\nc) 7 of 12: {7/12}"}, {"kind": "blank", "p": "A class has 9 children. 4 are wearing a hat and 2 are wearing glasses.", "tag": "", "marks": "", "flat": [{"t": "a) What fraction are wearing a hat? __B1__", "a": {"B1": "4/9"}, "expr": "fv"}, {"t": "b) What fraction are NOT wearing a hat? __B1__", "a": {"B1": "5/9"}, "expr": "fv"}, {"t": "c) What fraction are wearing glasses? __B1__", "a": {"B1": "2/9"}, "expr": "fv"}], "sol": "a) {4/9}\nb) 9 − 4 = 5, so {5/9}\nc) {2/9}"}]}, {"id": "s2", "label": "Ex 6B", "sub": "Fractions as division", "slides": [{"kind": "blank", "p": "Write as a fraction:", "tag": "", "marks": "", "flat": [{"t": "a) 4 ÷ 7 = __B1__", "a": {"B1": "4/7"}, "expr": "fe"}, {"t": "b) 2 ÷ 9 = __B1__", "a": {"B1": "2/9"}, "expr": "fe"}, {"t": "c) 5 ÷ 11 = __B1__", "a": {"B1": "5/11"}, "expr": "fe"}, {"t": "d) 3 ÷ 8 = __B1__", "a": {"B1": "3/8"}, "expr": "fe"}, {"t": "e) 1 ÷ 6 = __B1__", "a": {"B1": "1/6"}, "expr": "fe"}, {"t": "f) 13 ÷ 15 = __B1__", "a": {"B1": "13/15"}, "expr": "fe"}], "sol": "a ÷ b = {a/b}: the first number is the numerator."}, {"kind": "blank", "p": "Write as a division:", "tag": "", "marks": "", "flat": [{"t": "a) {1/4} = __B1__ ÷ __B2__", "a": {"B1": "1", "B2": "4"}}, {"t": "b) {3/5} = __B1__ ÷ __B2__", "a": {"B1": "3", "B2": "5"}}, {"t": "c) {7/9} = __B1__ ÷ __B2__", "a": {"B1": "7", "B2": "9"}}, {"t": "d) {5/12} = __B1__ ÷ __B2__", "a": {"B1": "5", "B2": "12"}}], "sol": "The bar means 'divided by': numerator ÷ denominator."}, {"kind": "blank", "p": "Write as a division, and hence as a whole number:", "tag": "", "marks": "", "flat": [{"t": "a) {24/6} = __B1__", "a": {"B1": "4"}, "expr": "fv"}, {"t": "b) {35/7} = __B1__", "a": {"B1": "5"}, "expr": "fv"}, {"t": "c) {72/8} = __B1__", "a": {"B1": "9"}, "expr": "fv"}, {"t": "d) {13/13} = __B1__", "a": {"B1": "1"}, "expr": "fv"}, {"t": "e) {0/5} = __B1__", "a": {"B1": "0"}, "expr": "fv"}, {"t": "f) {96/12} = __B1__", "a": {"B1": "8"}, "expr": "fv"}], "sol": "Divide the numerator by the denominator (e.g. {24/6} = 24 ÷ 6 = 4).\na) {24/6} = 4\nb) {35/7} = 5\nc) {72/8} = 9\nd) {13/13} = 1\ne) {0/5} = 0\nf) {96/12} = 8"}, {"kind": "blank", "p": "3 pizzas are shared equally between 4 people.", "tag": "", "marks": "", "flat": [{"t": "a) Each person gets __B1__ of a pizza", "a": {"B1": "3/4"}, "expr": "fv"}, {"t": "b) 3 pizzas ÷ 4 people = __B1__", "a": {"B1": "3/4"}, "expr": "fv"}], "sol": "Each pizza gives each person {1/4}; with 3 pizzas that is {3/4} each.\n3 ÷ 4 = {3/4}"}]}, {"id": "s3", "label": "Ex 6C", "sub": "Proper and improper fractions", "slides": [{"kind": "blank", "p": "Is each number a proper fraction, an improper fraction, or a mixed number? (type proper, improper or mixed)", "tag": "", "marks": "", "flat": [{"t": "a) {3/5} → __B1__", "a": {"B1": "proper"}, "accept": ["proper fraction", "proper number"]}, {"t": "b) {9/4} → __B1__", "a": {"B1": "improper"}, "accept": ["improper fraction", "improper number"]}, {"t": "c) {1 2/3} → __B1__", "a": {"B1": "mixed"}, "accept": ["mixed fraction", "mixed number"]}, {"t": "d) {7/8} → __B1__", "a": {"B1": "proper"}, "accept": ["proper fraction", "proper number"]}, {"t": "e) {12/5} → __B1__", "a": {"B1": "improper"}, "accept": ["improper fraction", "improper number"]}, {"t": "f) {4 1/6} → __B1__", "a": {"B1": "mixed"}, "accept": ["mixed fraction", "mixed number"]}, {"t": "g) {11/11} → __B1__", "a": {"B1": "improper"}, "accept": ["improper fraction", "improper number"]}, {"t": "h) {2/15} → __B1__", "a": {"B1": "proper"}, "accept": ["proper fraction", "proper number"]}], "sol": "proper: numerator < denominator · improper: numerator ≥ denominator · mixed: a whole number and a proper fraction"}, {"kind": "blank", "p": "This diagram shows some pizzas.", "tag": "", "marks": "", "flat": [{"t": "a) How many halves are there in {3 1/2} pizzas? __B1__", "a": {"B1": "7"}}, {"t": "b) {3 1/2} = __B1__ halves, i.e. __B2__/2", "a": {"B1": "7", "B2": "7"}}], "sol": "Each whole pizza has 2 halves: 3 × 2 = 6, plus 1 more half = 7.\nSo {3 1/2} = {7/2}.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 338 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M46.0,44 L46.0,10.0 A34,34 0 0 1 46.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M46.0,44 L46.0,78.0 A34,34 0 0 1 46.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M128.0,44 L128.0,10.0 A34,34 0 0 1 128.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M128.0,44 L128.0,78.0 A34,34 0 0 1 128.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M210.0,44 L210.0,10.0 A34,34 0 0 1 210.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M210.0,44 L210.0,78.0 A34,34 0 0 1 210.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M292.0,44 L292.0,10.0 A34,34 0 0 1 292.0,78.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M292.0,44 L292.0,78.0 A34,34 0 0 1 292.0,10.0 Z\"/></svg>"}, {"kind": "blank", "p": "Describe the shaded region as a mixed number:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__", "a": {"B1": "1 3/4"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M109.0,44 L109.0,10.0 A34,34 0 0 1 143.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M109.0,44 L143.0,44.0 A34,34 0 0 1 109.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M109.0,44 L109.0,78.0 A34,34 0 0 1 75.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M109.0,44 L75.0,44.0 A34,34 0 0 1 109.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M191.0,44 L191.0,10.0 A34,34 0 0 1 225.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M191.0,44 L225.0,44.0 A34,34 0 0 1 191.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M191.0,44 L191.0,78.0 A34,34 0 0 1 157.0,44.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M191.0,44 L157.0,44.0 A34,34 0 0 1 191.0,10.0 Z\"/></svg>", "expr": "fm"}, {"t": "b) __B1__", "a": {"B1": "2 5/6"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L68.0,10.0 A34,34 0 0 1 97.4,27.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L97.4,27.0 A34,34 0 0 1 97.4,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L97.4,61.0 A34,34 0 0 1 68.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L68.0,78.0 A34,34 0 0 1 38.6,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L38.6,61.0 A34,34 0 0 1 38.6,27.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L38.6,27.0 A34,34 0 0 1 68.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,10.0 A34,34 0 0 1 179.4,27.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L179.4,27.0 A34,34 0 0 1 179.4,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L179.4,61.0 A34,34 0 0 1 150.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,78.0 A34,34 0 0 1 120.6,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L120.6,61.0 A34,34 0 0 1 120.6,27.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L120.6,27.0 A34,34 0 0 1 150.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L232.0,10.0 A34,34 0 0 1 261.4,27.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L261.4,27.0 A34,34 0 0 1 261.4,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L261.4,61.0 A34,34 0 0 1 232.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L232.0,78.0 A34,34 0 0 1 202.6,61.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L202.6,61.0 A34,34 0 0 1 202.6,27.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L202.6,27.0 A34,34 0 0 1 232.0,10.0 Z\"/></svg>", "expr": "fm"}, {"t": "c) __B1__", "a": {"B1": "3 2/5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 466 40\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"12.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"32.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"52.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"72.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"92.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"126.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"146.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"166.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"186.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"206.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"240.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"260.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"280.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"300.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"320.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"354.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"374.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"394.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"414.0\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" x=\"434.0\" y=\"10\" width=\"20\" height=\"20\"/></svg>", "expr": "fm"}], "sol": "Count the full wholes, then the fraction of the last one.\na) {1 3/4}\nb) {2 5/6}\nc) {3 2/5}"}, {"kind": "blank", "p": "Write as an improper fraction:", "tag": "", "marks": "", "flat": [{"t": "a) {1 1/3} = __B1__", "a": {"B1": "4/3"}, "expr": "fi"}, {"t": "b) {2 1/4} = __B1__", "a": {"B1": "9/4"}, "expr": "fi"}, {"t": "c) {3 2/5} = __B1__", "a": {"B1": "17/5"}, "expr": "fi"}, {"t": "d) {1 5/6} = __B1__", "a": {"B1": "11/6"}, "expr": "fi"}, {"t": "e) {4 3/8} = __B1__", "a": {"B1": "35/8"}, "expr": "fi"}, {"t": "f) {2 7/10} = __B1__", "a": {"B1": "27/10"}, "expr": "fi"}], "sol": "Multiply the whole number by the denominator and add the numerator (e.g. {2 1/4} = {8/4} + {1/4} = {9/4}).\na) {1 1/3} = {4/3}\nb) {2 1/4} = {9/4}\nc) {3 2/5} = {17/5}\nd) {1 5/6} = {11/6}\ne) {4 3/8} = {35/8}\nf) {2 7/10} = {27/10}"}, {"kind": "blank", "p": "Write as a mixed number:", "tag": "", "marks": "", "flat": [{"t": "a) {7/2} = __B1__", "a": {"B1": "3 1/2"}, "expr": "fm"}, {"t": "b) {9/4} = __B1__", "a": {"B1": "2 1/4"}, "expr": "fm"}, {"t": "c) {17/5} = __B1__", "a": {"B1": "3 2/5"}, "expr": "fm"}, {"t": "d) {20/3} = __B1__", "a": {"B1": "6 2/3"}, "expr": "fm"}, {"t": "e) {29/6} = __B1__", "a": {"B1": "4 5/6"}, "expr": "fm"}, {"t": "f) {43/8} = __B1__", "a": {"B1": "5 3/8"}, "expr": "fm"}, {"t": "g) {25/7} = __B1__", "a": {"B1": "3 4/7"}, "expr": "fm"}, {"t": "h) {31/10} = __B1__", "a": {"B1": "3 1/10"}, "expr": "fm"}], "sol": "Divide: the quotient is the whole number and the remainder is the new numerator (e.g. {17/5}: 17 ÷ 5 = 3 r 2, so {3 2/5}).\na) {7/2} = {3 1/2}\nb) {9/4} = {2 1/4}\nc) {17/5} = {3 2/5}\nd) {20/3} = {6 2/3}\ne) {29/6} = {4 5/6}\nf) {43/8} = {5 3/8}\ng) {25/7} = {3 4/7}\nh) {31/10} = {3 1/10}"}, {"kind": "blank", "p": "23 apples are shared equally between 4 children. How many apples does each child receive? (answer as a mixed number)", "tag": "", "marks": "", "flat": [{"t": "__B1__ apples", "a": {"B1": "5 3/4"}, "expr": "fm"}], "sol": "23 ÷ 4 = 5 remainder 3, so each child gets {5 3/4} apples."}, {"kind": "blank", "p": "After a party there were 15 quarter sandwiches left over.", "tag": "", "marks": "", "flat": [{"t": "a) How many whole sandwiches can be made? __B1__", "a": {"B1": "3"}}, {"t": "b) How many quarters are left over? __B1__", "a": {"B1": "3"}}, {"t": "c) {15/4} = __B1__", "a": {"B1": "3 3/4"}, "expr": "fm"}], "sol": "15 ÷ 4 = 3 remainder 3\nSo {15/4} = {3 3/4}."}]}, {"id": "s4", "label": "Ex 6D", "sub": "Fractions on a number line", "slides": [{"kind": "blank", "p": "State the value shown by each red dot:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__", "a": {"B1": "3/5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 70\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"16.0\" y1=\"38.0\" x2=\"284.0\" y2=\"38.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"30.0\" y1=\"30\" x2=\"30.0\" y2=\"46\"/><text class=\"lb\" x=\"30.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"78.0\" y1=\"33\" x2=\"78.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"126.0\" y1=\"33\" x2=\"126.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"174.0\" y1=\"33\" x2=\"174.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"222.0\" y1=\"33\" x2=\"222.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"270.0\" y1=\"30\" x2=\"270.0\" y2=\"46\"/><text class=\"lb\" x=\"270.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><circle class=\"dr\" cx=\"174.0\" cy=\"38\" r=\"5\"/></svg>", "expr": "fv"}, {"t": "b) __B1__", "a": {"B1": "7/8"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 70\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"16.0\" y1=\"38.0\" x2=\"284.0\" y2=\"38.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"30.0\" y1=\"30\" x2=\"30.0\" y2=\"46\"/><text class=\"lb\" x=\"30.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"60.0\" y1=\"33\" x2=\"60.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"90.0\" y1=\"33\" x2=\"90.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"120.0\" y1=\"33\" x2=\"120.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"150.0\" y1=\"33\" x2=\"150.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"180.0\" y1=\"33\" x2=\"180.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"210.0\" y1=\"33\" x2=\"210.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"240.0\" y1=\"33\" x2=\"240.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"270.0\" y1=\"30\" x2=\"270.0\" y2=\"46\"/><text class=\"lb\" x=\"270.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><circle class=\"dr\" cx=\"240.0\" cy=\"38\" r=\"5\"/></svg>", "expr": "fv"}, {"t": "c) __B1__", "a": {"B1": "1 1/4"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 70\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"16.0\" y1=\"38.0\" x2=\"284.0\" y2=\"38.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"30.0\" y1=\"30\" x2=\"30.0\" y2=\"46\"/><text class=\"lb\" x=\"30.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"60.0\" y1=\"33\" x2=\"60.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"90.0\" y1=\"33\" x2=\"90.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"120.0\" y1=\"33\" x2=\"120.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"150.0\" y1=\"30\" x2=\"150.0\" y2=\"46\"/><text class=\"lb\" x=\"150.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"180.0\" y1=\"33\" x2=\"180.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"210.0\" y1=\"33\" x2=\"210.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"240.0\" y1=\"33\" x2=\"240.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"270.0\" y1=\"30\" x2=\"270.0\" y2=\"46\"/><text class=\"lb\" x=\"270.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><circle class=\"dr\" cx=\"180.0\" cy=\"38\" r=\"5\"/></svg>", "expr": "fv"}, {"t": "d) __B1__", "a": {"B1": "2 2/3"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 70\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"16.0\" y1=\"38.0\" x2=\"284.0\" y2=\"38.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"30.0\" y1=\"30\" x2=\"30.0\" y2=\"46\"/><text class=\"lb\" x=\"30.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"56.7\" y1=\"33\" x2=\"56.7\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"83.3\" y1=\"33\" x2=\"83.3\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"110.0\" y1=\"30\" x2=\"110.0\" y2=\"46\"/><text class=\"lb\" x=\"110.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"136.7\" y1=\"33\" x2=\"136.7\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"163.3\" y1=\"33\" x2=\"163.3\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"190.0\" y1=\"30\" x2=\"190.0\" y2=\"46\"/><text class=\"lb\" x=\"190.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"216.7\" y1=\"33\" x2=\"216.7\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"243.3\" y1=\"33\" x2=\"243.3\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"270.0\" y1=\"30\" x2=\"270.0\" y2=\"46\"/><text class=\"lb\" x=\"270.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><circle class=\"dr\" cx=\"243.3\" cy=\"38\" r=\"5\"/></svg>", "expr": "fv"}, {"t": "e) __B1__", "a": {"B1": "3 1/2"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 70\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"16.0\" y1=\"38.0\" x2=\"284.0\" y2=\"38.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"30.0\" y1=\"30\" x2=\"30.0\" y2=\"46\"/><text class=\"lb\" x=\"30.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"90.0\" y1=\"33\" x2=\"90.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"150.0\" y1=\"30\" x2=\"150.0\" y2=\"46\"/><text class=\"lb\" x=\"150.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.9\" x1=\"210.0\" y1=\"33\" x2=\"210.0\" y2=\"43\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1.4\" x1=\"270.0\" y1=\"30\" x2=\"270.0\" y2=\"46\"/><text class=\"lb\" x=\"270.0\" y=\"58.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><circle class=\"dr\" cx=\"210.0\" cy=\"38\" r=\"5\"/></svg>", "expr": "fv"}], "sol": "Count how many equal spaces there are between whole numbers.\na) 5 spaces, dot at the 3rd: {3/5}\nb) {7/8}\nc) {1 1/4}\nd) {2 2/3}\ne) {3 1/2}"}, {"kind": "blank", "p": "Write in ascending order (separate with commas, e.g. {1/2}, {3/4}):", "tag": "", "marks": "", "flat": [{"t": "a) {9/5}, {2/5}, {1 3/5}, {6/5} → __B1__", "a": {"B1": "2/5, 6/5, 1 3/5, 9/5"}, "expr": "flist"}, {"t": "b) {2 1/6}, {15/6}, {10/6}, {1 5/6} → __B1__", "a": {"B1": "10/6, 1 5/6, 2 1/6, 15/6"}, "expr": "flist"}], "sol": "Write all the fractions with a common denominator, then order the numerators.\na) {2/5}, {6/5}, {1 3/5}, {9/5}\nb) {10/6}, {1 5/6}, {2 1/6}, {15/6}"}]}, {"id": "s5", "label": "Ex 6E", "sub": "Equal fractions", "slides": [{"kind": "blank", "p": "Write a fraction equal to {6/10} by:", "tag": "", "marks": "", "flat": [{"t": "a) multiplying the numerator and denominator by 3: __B1__", "a": {"B1": "18/30"}, "expr": "fe"}, {"t": "b) dividing the numerator and denominator by 2: __B1__", "a": {"B1": "3/5"}, "expr": "fe"}], "sol": "a) {6/10} = {18/30}\nb) {6/10} = {3/5}"}, {"kind": "blank", "p": "Write {3/4} with denominator:", "tag": "", "marks": "", "flat": [{"t": "a) {3/4} = __B1__/8", "a": {"B1": "6"}}, {"t": "b) {3/4} = __B1__/12", "a": {"B1": "9"}}, {"t": "c) {3/4} = __B1__/16", "a": {"B1": "12"}}, {"t": "d) {3/4} = __B1__/20", "a": {"B1": "15"}}, {"t": "e) {3/4} = __B1__/100", "a": {"B1": "75"}}], "sol": "Multiply the top by the same number as the bottom (e.g. 4 × 3 = 12, so 3 × 3 = 9).\na) {6/8}\nb) {9/12}\nc) {12/16}\nd) {15/20}\ne) {75/100}"}, {"kind": "blank", "p": "Write {2/5} with numerator:", "tag": "", "marks": "", "flat": [{"t": "a) {2/5} = 4/__B1__", "a": {"B1": "10"}}, {"t": "b) {2/5} = 6/__B1__", "a": {"B1": "15"}}, {"t": "c) {2/5} = 10/__B1__", "a": {"B1": "25"}}, {"t": "d) {2/5} = 20/__B1__", "a": {"B1": "50"}}], "sol": "Multiply the bottom by the same number as the top.\na) {4/10}\nb) {6/15}\nc) {10/25}\nd) {20/50}"}, {"kind": "blank", "p": "Write with denominator 24:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} = __B1__/24", "a": {"B1": "12"}}, {"t": "b) {2/3} = __B1__/24", "a": {"B1": "16"}}, {"t": "c) {3/8} = __B1__/24", "a": {"B1": "9"}}, {"t": "d) {5/6} = __B1__/24", "a": {"B1": "20"}}, {"t": "e) {7/12} = __B1__/24", "a": {"B1": "14"}}, {"t": "f) 1 = __B1__/24", "a": {"B1": "24"}}], "sol": "24 ÷ denominator gives the number to multiply by.\na) {1/2} = {12/24}\nb) {2/3} = {16/24}\nc) {3/8} = {9/24}\nd) {5/6} = {20/24}\ne) {7/12} = {14/24}\nf) 1 = {24/24}"}, {"kind": "blank", "p": "Write with denominator 100:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} = __B1__/100", "a": {"B1": "50"}}, {"t": "b) {1/4} = __B1__/100", "a": {"B1": "25"}}, {"t": "c) {3/5} = __B1__/100", "a": {"B1": "60"}}, {"t": "d) {7/10} = __B1__/100", "a": {"B1": "70"}}, {"t": "e) {9/20} = __B1__/100", "a": {"B1": "45"}}, {"t": "f) {13/50} = __B1__/100", "a": {"B1": "26"}}, {"t": "g) {17/25} = __B1__/100", "a": {"B1": "68"}}, {"t": "h) 1 = __B1__/100", "a": {"B1": "100"}}], "sol": "100 ÷ denominator gives the number to multiply by.\na) {1/2} = {50/100}\nb) {1/4} = {25/100}\nc) {3/5} = {60/100}\nd) {7/10} = {70/100}\ne) {9/20} = {45/100}\nf) {13/50} = {26/100}\ng) {17/25} = {68/100}\nh) 1 = {100/100}"}]}, {"id": "s6", "label": "Ex 6F", "sub": "Lowest terms", "slides": [{"kind": "blank", "p": "Write in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) {6/8} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "b) {4/12} = __B1__", "a": {"B1": "1/3"}, "expr": "fl"}, {"t": "c) {3/15} = __B1__", "a": {"B1": "1/5"}, "expr": "fl"}, {"t": "d) {10/25} = __B1__", "a": {"B1": "2/5"}, "expr": "fl"}, {"t": "e) {8/20} = __B1__", "a": {"B1": "2/5"}, "expr": "fl"}, {"t": "f) {14/21} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "g) {18/24} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "h) {36/48} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "i) {20/100} = __B1__", "a": {"B1": "1/5"}, "expr": "fl"}, {"t": "j) {45/60} = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}], "sol": "Divide the numerator and denominator by their HCF.\na) HCF of 6 and 8 is 2: {6/8} = {3/4}\nb) HCF of 4 and 12 is 4: {4/12} = {1/3}\nc) HCF of 3 and 15 is 3: {3/15} = {1/5}\nd) HCF of 10 and 25 is 5: {10/25} = {2/5}\ne) HCF of 8 and 20 is 4: {8/20} = {2/5}\nf) HCF of 14 and 21 is 7: {14/21} = {2/3}\ng) HCF of 18 and 24 is 6: {18/24} = {3/4}\nh) HCF of 36 and 48 is 12: {36/48} = {3/4}\ni) HCF of 20 and 100 is 20: {20/100} = {1/5}\nj) HCF of 45 and 60 is 15: {45/60} = {3/4}"}, {"kind": "mcq", "text": "Which fraction is written in lowest terms?", "opts": ["{6/9}", "{4/10}", "{7/12}", "{15/20}"], "correct": 2, "tag": "", "sol": "7 and 12 have no common factor except 1. The others simplify: {6/9} = {2/3}, {4/10} = {2/5}, {15/20} = {3/4}."}, {"kind": "blank", "p": "A box has 12 shapes: 3 cubes, 4 cones, 2 spheres and 3 cylinders. In lowest terms, what fraction are:", "tag": "", "marks": "", "flat": [{"t": "a) cubes? __B1__", "a": {"B1": "1/4"}, "expr": "fl"}, {"t": "b) cones? __B1__", "a": {"B1": "1/3"}, "expr": "fl"}, {"t": "c) spheres? __B1__", "a": {"B1": "1/6"}, "expr": "fl"}, {"t": "d) not cylinders? __B1__", "a": {"B1": "3/4"}, "expr": "fl"}], "sol": "a) {3/12} = {1/4}\nb) {4/12} = {1/3}\nc) {2/12} = {1/6}\nd) {9/12} = {3/4}"}]}, {"id": "s7", "label": "Ex 6G", "sub": "Comparing fractions", "slides": [{"kind": "blank", "p": "Use < or > to complete:", "tag": "", "marks": "", "flat": [{"t": "a) {4/9} __B1__ {7/9}", "a": {"B1": "<"}}, {"t": "b) {5/6} __B1__ {1/6}", "a": {"B1": ">"}}, {"t": "c) {11/8} __B1__ {9/8}", "a": {"B1": ">"}}, {"t": "d) {2 1/5} __B1__ {12/5}", "a": {"B1": "<"}}], "sol": "Write both with the same denominator (or as improper fractions), then compare the numerators.\na) {4/9} = {4/9} and {7/9} = {7/9}, so {4/9} < {7/9}\nb) {5/6} = {5/6} and {1/6} = {1/6}, so {5/6} > {1/6}\nc) {11/8} = {11/8} and {9/8} = {9/8}, so {11/8} > {9/8}\nd) {11/5} = {11/5} and {12/5} = {12/5}, so {2 1/5} < {12/5}"}, {"kind": "blank", "p": "Use < or > to complete:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} __B1__ {2/5}", "a": {"B1": ">"}}, {"t": "b) {2/3} __B1__ {3/4}", "a": {"B1": "<"}}, {"t": "c) {5/8} __B1__ {3/5}", "a": {"B1": ">"}}, {"t": "d) {7/10} __B1__ {2/3}", "a": {"B1": ">"}}, {"t": "e) {5/4} __B1__ {1 1/3}", "a": {"B1": "<"}}, {"t": "f) {3 1/2} __B1__ {17/5}", "a": {"B1": ">"}}], "sol": "Write both with the same denominator (or as improper fractions), then compare the numerators.\na) {1/2} = {5/10} and {2/5} = {4/10}, so {1/2} > {2/5}\nb) {2/3} = {8/12} and {3/4} = {9/12}, so {2/3} < {3/4}\nc) {5/8} = {25/40} and {3/5} = {24/40}, so {5/8} > {3/5}\nd) {7/10} = {21/30} and {2/3} = {20/30}, so {7/10} > {2/3}\ne) {5/4} = {15/12} and {4/3} = {16/12}, so {5/4} < {1 1/3}\nf) {7/2} = {35/10} and {17/5} = {34/10}, so {3 1/2} > {17/5}"}, {"kind": "blank", "p": "Asha ate {2 1/3} rotis. Ravi cut his rotis into thirds and ate 8 of the thirds. Who ate more? (type Asha or Ravi)", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "Ravi"}}], "sol": "Asha: {2 1/3} = {7/3}. Ravi: {8/3}. {8/3} > {7/3}, so Ravi ate more."}, {"kind": "blank", "p": "Meera spends {1/4} of her pocket money on books and {2/9} on snacks. Does she spend more on books or snacks? (type books or snacks)", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "books"}}], "sol": "{1/4} = {9/36} and {2/9} = {8/36}, so she spends more on books."}, {"kind": "blank", "p": "Write in ascending order (separate with commas, e.g. {1/2}, {3/4}):", "tag": "", "marks": "", "flat": [{"t": "a) {5/6}, {7/12}, {2/3} → __B1__", "a": {"B1": "7/12, 2/3, 5/6"}, "expr": "flist"}, {"t": "b) {3/10}, {1/2}, {2/5} → __B1__", "a": {"B1": "3/10, 2/5, 1/2"}, "expr": "flist"}, {"t": "c) {7/4}, {3/2}, {1 5/8} → __B1__", "a": {"B1": "3/2, 1 5/8, 7/4"}, "expr": "flist"}], "sol": "Write all the fractions with a common denominator, then order the numerators.\na) {7/12}, {2/3}, {5/6}\nb) {3/10}, {2/5}, {1/2}\nc) {3/2}, {1 5/8}, {7/4}"}, {"kind": "blank", "p": "Write in descending order (separate with commas, e.g. {1/2}, {3/4}):", "tag": "", "marks": "", "flat": [{"t": "a) {3/4}, {5/8}, {11/16} → __B1__", "a": {"B1": "3/4, 11/16, 5/8"}, "expr": "flist"}, {"t": "b) {2 1/3}, {9/4}, {13/6} → __B1__", "a": {"B1": "2 1/3, 9/4, 13/6"}, "expr": "flist"}], "sol": "Write all the fractions with a common denominator, then order the numerators.\na) {3/4}, {11/16}, {5/8}\nb) {2 1/3}, {9/4}, {13/6}"}, {"kind": "mcq", "text": "Are improper fractions always larger than proper fractions?", "opts": ["Yes, an improper fraction is at least 1, and a proper fraction is less than 1", "No, never", "Only when the denominators are equal", "Only for halves"], "correct": 0, "tag": "", "sol": "Improper fractions are ≥ 1; proper fractions are < 1. So an improper fraction is always larger."}]}, {"id": "s8", "label": "Ex 6H.1", "sub": "Adding and subtracting (same denominator)", "slides": [{"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1/7} + {3/7} = __B1__", "a": {"B1": "4/7"}, "expr": "fv"}, {"t": "b) {5/9} − {2/9} = __B1__", "a": {"B1": "1/3"}, "expr": "fv"}, {"t": "c) {3/8} + {4/8} = __B1__", "a": {"B1": "7/8"}, "expr": "fv"}, {"t": "d) {11/12} − {6/12} = __B1__", "a": {"B1": "5/12"}, "expr": "fv"}, {"t": "e) {2/11} + {5/11} + {3/11} = __B1__", "a": {"B1": "10/11"}, "expr": "fv"}, {"t": "f) {9/10} − {3/10} − {4/10} = __B1__", "a": {"B1": "1/5"}, "expr": "fv"}], "sol": "Same denominator: add or subtract the numerators; the denominator stays the same.\na) {1/7} + {3/7} = {4/7}\nb) {5/9} − {2/9} = {1/3}\nc) {3/8} + {4/8} = {7/8}\nd) {11/12} − {6/12} = {5/12}\ne) {2/11} + {5/11} + {3/11} = {10/11}\nf) {9/10} − {3/10} − {4/10} = {1/5}"}, {"kind": "blank", "p": "Find, giving your answer in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) {1/4} + {1/4} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "b) {5/6} − {1/6} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "c) {3/10} + {5/10} = __B1__", "a": {"B1": "4/5"}, "expr": "fl"}, {"t": "d) {7/8} − {3/8} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "e) {4/9} + {2/9} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "f) {13/15} − {4/15} = __B1__", "a": {"B1": "3/5"}, "expr": "fl"}], "sol": "Add or subtract the numerators, then simplify using the HCF.\na) {1/4} + {1/4} = {1/2}\nb) {5/6} − {1/6} = {2/3}\nc) {3/10} + {5/10} = {4/5}\nd) {7/8} − {3/8} = {1/2}\ne) {4/9} + {2/9} = {2/3}\nf) {13/15} − {4/15} = {3/5}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) 3 + {2/5} + {1/5} = __B1__", "a": {"B1": "3 3/5"}, "expr": "fv"}, {"t": "b) 2 + {5/8} + {1/8} = __B1__", "a": {"B1": "2 3/4"}, "expr": "fv"}, {"t": "c) 4 + {6/7} − {2/7} = __B1__", "a": {"B1": "4 4/7"}, "expr": "fv"}, {"t": "d) 1 + {4/5} + {3/5} = __B1__", "a": {"B1": "2 2/5"}, "expr": "fv"}], "sol": "Add the fractions, then add the whole number.\na) 3 + {2/5} + {1/5} = {3 3/5}\nb) 2 + {5/8} + {1/8} = {2 3/4}\nc) 4 + {6/7} − {2/7} = {4 4/7}\nd) 1 + {4/5} + {3/5} = {2 2/5}"}, {"kind": "blank", "p": "Ravi painted {3/10} of a fence on Monday and {4/10} on Tuesday. What fraction has he painted so far?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "7/10"}, "expr": "fv"}], "sol": "{3/10} + {4/10} = {7/10}"}, {"kind": "blank", "p": "A jug is {7/8} full. Priya pours out {3/8} of a jug. What fraction of the jug is left? (lowest terms)", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "1/2"}, "expr": "fl"}], "sol": "{7/8} − {3/8} = {4/8} = {1/2}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1 2/5} + {2 1/5} = __B1__", "a": {"B1": "3 3/5"}, "expr": "fv"}, {"t": "b) {3 4/7} − {1 2/7} = __B1__", "a": {"B1": "2 2/7"}, "expr": "fv"}, {"t": "c) {2 3/8} + {1 7/8} = __B1__", "a": {"B1": "4 1/4"}, "expr": "fv"}, {"t": "d) {4 1/6} − {2 5/6} = __B1__", "a": {"B1": "1 1/3"}, "expr": "fv"}, {"t": "e) {1 3/10} + {2 9/10} = __B1__", "a": {"B1": "4 1/5"}, "expr": "fv"}], "sol": "Convert to improper fractions (or add wholes and fractions separately), then simplify.\na) {1 2/5} + {2 1/5} = {3 3/5}\nb) {3 4/7} − {1 2/7} = {2 2/7}\nc) {2 3/8} + {1 7/8} = {4 1/4}\nd) {4 1/6} − {2 5/6} = {1 1/3}\ne) {1 3/10} + {2 9/10} = {4 1/5}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) 1 − {3/8} = __B1__", "a": {"B1": "5/8"}, "expr": "fv"}, {"t": "b) 2 − {4/5} = __B1__", "a": {"B1": "1 1/5"}, "expr": "fv"}, {"t": "c) 5 − {2 1/3} = __B1__", "a": {"B1": "2 2/3"}, "expr": "fv"}, {"t": "d) 7 − {3 5/9} = __B1__", "a": {"B1": "3 4/9"}, "expr": "fv"}], "sol": "Write the whole number as a fraction with the same denominator (e.g. 1 = {8/8}).\na) 1 − {3/8} = {5/8}\nb) 2 − {4/5} = {1 1/5}\nc) 5 − {2 1/3} = {2 2/3}\nd) 7 − {3 5/9} = {3 4/9}"}]}, {"id": "s9", "label": "Ex 6H.2", "sub": "Adding and subtracting (unequal denominators)", "slides": [{"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} + {1/4} = __B1__", "a": {"B1": "3/4"}, "expr": "fv"}, {"t": "b) {1/3} + {1/6} = __B1__", "a": {"B1": "1/2"}, "expr": "fv"}, {"t": "c) {3/4} − {1/8} = __B1__", "a": {"B1": "5/8"}, "expr": "fv"}, {"t": "d) {2/5} + {3/10} = __B1__", "a": {"B1": "7/10"}, "expr": "fv"}, {"t": "e) {5/6} − {1/3} = __B1__", "a": {"B1": "1/2"}, "expr": "fv"}, {"t": "f) {1/2} − {1/5} = __B1__", "a": {"B1": "3/10"}, "expr": "fv"}, {"t": "g) {2/3} + {1/4} = __B1__", "a": {"B1": "11/12"}, "expr": "fv"}, {"t": "h) {7/9} − {1/2} = __B1__", "a": {"B1": "5/18"}, "expr": "fv"}], "sol": "Write both fractions with a common denominator first.\na) {1/2} + {1/4} = {3/4}\nb) {1/3} + {1/6} = {1/2}\nc) {3/4} − {1/8} = {5/8}\nd) {2/5} + {3/10} = {7/10}\ne) {5/6} − {1/3} = {1/2}\nf) {1/2} − {1/5} = {3/10}\ng) {2/3} + {1/4} = {11/12}\nh) {7/9} − {1/2} = {5/18}"}, {"kind": "blank", "p": "Find, giving your answer in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} + {1/6} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "b) {7/10} − {1/5} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "c) {1/4} + {5/12} = __B1__", "a": {"B1": "2/3"}, "expr": "fl"}, {"t": "d) {5/6} − {7/12} = __B1__", "a": {"B1": "1/4"}, "expr": "fl"}, {"t": "e) {3/4} + {1/12} = __B1__", "a": {"B1": "5/6"}, "expr": "fl"}, {"t": "f) 1 − {3/10} − {1/5} = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}], "sol": "Use a common denominator, then simplify.\na) {1/2} + {1/6} = {2/3}\nb) {7/10} − {1/5} = {1/2}\nc) {1/4} + {5/12} = {2/3}\nd) {5/6} − {7/12} = {1/4}\ne) {3/4} + {1/12} = {5/6}\nf) 1 − {3/10} − {1/5} = {1/2}"}, {"kind": "blank", "p": "Neha ate {1/3} of a cake and Arjun ate {1/4} of it.", "tag": "", "marks": "", "flat": [{"t": "a) What fraction did they eat altogether? __B1__", "a": {"B1": "7/12"}, "expr": "fv"}, {"t": "b) What fraction is left? __B1__", "a": {"B1": "5/12"}, "expr": "fv"}], "sol": "a) {4/12} + {3/12} = {7/12}\nb) 1 − {7/12} = {5/12}"}, {"kind": "blank", "p": "A tank of feed is {9/10} full. The chickens eat {2/5} of a tank. How full is the tank now? (lowest terms)", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "1/2"}, "expr": "fl"}], "sol": "{9/10} − {4/10} = {5/10} = {1/2}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1 1/2} + {2 1/4} = __B1__", "a": {"B1": "3 3/4"}, "expr": "fv"}, {"t": "b) {3 2/3} − {1 1/6} = __B1__", "a": {"B1": "2 1/2"}, "expr": "fv"}, {"t": "c) {2 1/5} + {1 3/10} = __B1__", "a": {"B1": "3 1/2"}, "expr": "fv"}, {"t": "d) {4 1/2} − {2 3/4} = __B1__", "a": {"B1": "1 3/4"}, "expr": "fv"}], "sol": "Write as improper fractions with a common denominator, add or subtract, then write as a mixed number.\na) {1 1/2} + {2 1/4} = {3 3/4}\nb) {3 2/3} − {1 1/6} = {2 1/2}\nc) {2 1/5} + {1 3/10} = {3 1/2}\nd) {4 1/2} − {2 3/4} = {1 3/4}"}, {"kind": "blank", "p": "Samir spent {2 1/2} hours on Saturday and {1 3/4} hours on Sunday on a project. How long did he spend in total?", "tag": "", "marks": "", "flat": [{"t": "__B1__ hours", "a": {"B1": "4 1/4"}, "expr": "fv"}], "sol": "{5/2} + {7/4} = {10/4} + {7/4} = {17/4} = {4 1/4} hours"}, {"kind": "blank", "p": "{8 1/3} tonnes of sand must be moved. A truck moves {5 1/2} tonnes in the first load. How much is left?", "tag": "", "marks": "", "flat": [{"t": "__B1__ tonnes", "a": {"B1": "2 5/6"}, "expr": "fv"}], "sol": "{25/3} − {11/2} = {50/6} − {33/6} = {17/6} = {2 5/6} tonnes"}]}, {"id": "s10", "label": "Ex 6I", "sub": "Multiplying by a whole number", "slides": [{"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1/5} × 3 = __B1__", "a": {"B1": "3/5"}, "expr": "fv"}, {"t": "b) {2/9} × 4 = __B1__", "a": {"B1": "8/9"}, "expr": "fv"}, {"t": "c) {3/20} × 5 = __B1__", "a": {"B1": "3/4"}, "expr": "fv"}, {"t": "d) 2 × {3/11} = __B1__", "a": {"B1": "6/11"}, "expr": "fv"}], "sol": "Multiply the numerator by the whole number; the denominator stays the same.\na) {1/5} × 3 = {3/5}\nb) {2/9} × 4 = {8/9}\nc) {3/20} × 5 = {3/4}\nd) 2 × {3/11} = {6/11}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1/4} × 8 = __B1__", "a": {"B1": "2"}, "expr": "fv"}, {"t": "b) {1/3} × 15 = __B1__", "a": {"B1": "5"}, "expr": "fv"}, {"t": "c) {3/5} × 10 = __B1__", "a": {"B1": "6"}, "expr": "fv"}, {"t": "d) {5/6} × 12 = __B1__", "a": {"B1": "10"}, "expr": "fv"}, {"t": "e) 7 × {2/7} = __B1__", "a": {"B1": "2"}, "expr": "fv"}, {"t": "f) 4 × {3/8} = __B1__", "a": {"B1": "1 1/2"}, "expr": "fv"}], "sol": "Multiply, then simplify.\na) {1/4} × 8 = 2\nb) {1/3} × 15 = 5\nc) {3/5} × 10 = 6\nd) {5/6} × 12 = 10\ne) 7 × {2/7} = 2\nf) 4 × {3/8} = {1 1/2}"}, {"kind": "blank", "p": "Find, giving your answer in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) {1/10} × 4 = __B1__", "a": {"B1": "2/5"}, "expr": "fl"}, {"t": "b) {5/12} × 3 = __B1__", "a": {"B1": "1 1/4"}, "expr": "fl"}, {"t": "c) 6 × {5/9} = __B1__", "a": {"B1": "3 1/3"}, "expr": "fl"}, {"t": "d) {3/16} × 4 = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "e) {7/15} × 5 = __B1__", "a": {"B1": "2 1/3"}, "expr": "fl"}, {"t": "f) 9 × {5/6} = __B1__", "a": {"B1": "7 1/2"}, "expr": "fl"}], "sol": "Multiply the numerator, then divide top and bottom by the HCF.\na) {1/10} × 4 = {2/5}\nb) {5/12} × 3 = {1 1/4}\nc) 6 × {5/9} = {3 1/3}\nd) {3/16} × 4 = {3/4}\ne) {7/15} × 5 = {2 1/3}\nf) 9 × {5/6} = {7 1/2}"}]}, {"id": "s11", "label": "Ex 6J", "sub": "A fraction of a quantity", "slides": [{"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} of 18 = __B1__", "a": {"B1": "9"}, "expr": "fv"}, {"t": "b) {1/3} of 24 = __B1__", "a": {"B1": "8"}, "expr": "fv"}, {"t": "c) {1/4} of 36 = __B1__", "a": {"B1": "9"}, "expr": "fv"}, {"t": "d) {1/5} of 45 = __B1__", "a": {"B1": "9"}, "expr": "fv"}, {"t": "e) {1/8} of 64 = __B1__", "a": {"B1": "8"}, "expr": "fv"}, {"t": "f) {1/10} of 90 = __B1__", "a": {"B1": "9"}, "expr": "fv"}], "sol": "To find {1/n} of a number, divide by n.\na) {1/2} of 18 = 9\nb) {1/3} of 24 = 8\nc) {1/4} of 36 = 9\nd) {1/5} of 45 = 9\ne) {1/8} of 64 = 8\nf) {1/10} of 90 = 9"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {2/3} of 12 = __B1__", "a": {"B1": "8"}, "expr": "fv"}, {"t": "b) {3/4} of 20 = __B1__", "a": {"B1": "15"}, "expr": "fv"}, {"t": "c) {2/5} of 35 = __B1__", "a": {"B1": "14"}, "expr": "fv"}, {"t": "d) {5/6} of 42 = __B1__", "a": {"B1": "35"}, "expr": "fv"}, {"t": "e) {3/8} of 48 = __B1__", "a": {"B1": "18"}, "expr": "fv"}, {"t": "f) {7/10} of 150 = __B1__", "a": {"B1": "105"}, "expr": "fv"}], "sol": "Divide by the denominator, then multiply by the numerator.\na) {2/3} of 12 = 8\nb) {3/4} of 20 = 15\nc) {2/5} of 35 = 14\nd) {5/6} of 42 = 35\ne) {3/8} of 48 = 18\nf) {7/10} of 150 = 105"}, {"kind": "blank", "p": "Viktor played 18 games and won one third of them. How many games did he win?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "6"}, "expr": "fv"}], "sol": "{1/3} of 18 = 18 ÷ 3 = 6"}, {"kind": "blank", "p": "Ling had ₹1200. She spent one quarter of it on a racket. How much did the racket cost?", "tag": "", "marks": "", "flat": [{"t": "₹__B1__", "a": {"B1": "300"}, "expr": "fv"}], "sol": "{1/4} of 1200 = 300"}, {"kind": "blank", "p": "A farmer had 120 plants. One sixth of them died.", "tag": "", "marks": "", "flat": [{"t": "a) How many plants died? __B1__", "a": {"B1": "20"}, "expr": "fv"}, {"t": "b) What fraction were still alive? __B1__", "a": {"B1": "5/6"}, "expr": "fv"}, {"t": "c) How many were still alive? __B1__", "a": {"B1": "100"}, "expr": "fv"}], "sol": "a) 120 ÷ 6 = 20\nb) 1 − {1/6} = {5/6}\nc) 120 − 20 = 100"}, {"kind": "blank", "p": "45 passengers were on a bus. Three fifths of them were students. How many were students?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "27"}, "expr": "fv"}], "sol": "{3/5} of 45 = 45 ÷ 5 × 3 = 27"}, {"kind": "blank", "p": "A truck must carry 2400 kg of equipment, but can only carry {5/8} of it in one load.", "tag": "", "marks": "", "flat": [{"t": "a) first load: __B1__ kg", "a": {"B1": "1500"}, "expr": "fv"}, {"t": "b) second load: __B1__ kg", "a": {"B1": "900"}, "expr": "fv"}], "sol": "a) {5/8} of 2400 = 300 × 5 = 1500 kg\nb) 2400 − 1500 = 900 kg"}]}, {"id": "s12", "label": "Review 6A", "sub": "Review set 6A", "slides": [{"kind": "blank", "p": "What fraction is shaded?", "tag": "", "marks": "", "flat": [{"t": "a) __B1__", "a": {"B1": "3/5"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,10.0 A34,34 0 0 1 182.3,33.5 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L182.3,33.5 A34,34 0 0 1 170.0,71.5 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L170.0,71.5 A34,34 0 0 1 130.0,71.5 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L130.0,71.5 A34,34 0 0 1 117.7,33.5 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L117.7,33.5 A34,34 0 0 1 150.0,10.0 Z\"/></svg>", "expr": "fv"}, {"t": "b) __B1__", "a": {"B1": "7/12"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 124 98\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" x=\"10.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"36.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"62.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"88.0\" y=\"10\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"10.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"36.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"shd\" x=\"62.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"88.0\" y=\"36\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"10.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"36.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"62.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/><rect class=\"cell\" x=\"88.0\" y=\"62\" width=\"26\" height=\"26\" style=\"stroke:var(--ink);stroke-width:1.1\"/></svg>", "expr": "fv"}], "sol": "a) {3/5}\nb) {7/12}"}, {"kind": "blank", "p": "Write as a fraction:", "tag": "", "marks": "", "flat": [{"t": "a) 6 ÷ 11 = __B1__", "a": {"B1": "6/11"}, "expr": "fe"}, {"t": "b) 15 ÷ 19 = __B1__", "a": {"B1": "15/19"}, "expr": "fe"}], "sol": "a ÷ b = {a/b}\na) {6/11}\nb) {15/19}"}, {"kind": "blank", "p": "Write as a mixed number:", "tag": "", "marks": "", "flat": [{"t": "a) {9/5} = __B1__", "a": {"B1": "1 4/5"}, "expr": "fm"}, {"t": "b) {13/3} = __B1__", "a": {"B1": "4 1/3"}, "expr": "fm"}, {"t": "c) {35/6} = __B1__", "a": {"B1": "5 5/6"}, "expr": "fm"}], "sol": "Divide; the remainder becomes the numerator.\na) {9/5} = {1 4/5}\nb) {13/3} = {4 1/3}\nc) {35/6} = {5 5/6}"}, {"kind": "blank", "p": "Use < or > to complete:", "tag": "", "marks": "", "flat": [{"t": "a) {6/10} __B1__ {3/5} + {1/10}", "a": {"B1": "<"}}, {"t": "b) {19/7} __B1__ {2 3/7}", "a": {"B1": ">"}}, {"t": "c) {4/5} __B1__ {22/25}", "a": {"B1": "<"}}], "sol": "Write both with the same denominator (or as improper fractions), then compare the numerators.\na) {3/5} = {6/10} and {7/10} = {7/10}, so {6/10} < {3/5} + {1/10}\nb) {19/7} = {19/7} and {17/7} = {17/7}, so {19/7} > {2 3/7}\nc) {4/5} = {20/25} and {22/25} = {22/25}, so {4/5} < {22/25}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {12/7} − {8/7} = __B1__", "a": {"B1": "4/7"}, "expr": "fv"}, {"t": "b) {8/11} + {9/11} = __B1__", "a": {"B1": "1 6/11"}, "expr": "fv"}, {"t": "c) {3/8} + {1/4} = __B1__", "a": {"B1": "5/8"}, "expr": "fv"}, {"t": "d) {5 1/3} − {1 1/9} = __B1__", "a": {"B1": "4 2/9"}, "expr": "fv"}], "sol": "Use a common denominator.\na) {12/7} − {8/7} = {4/7}\nb) {8/11} + {9/11} = {1 6/11}\nc) {3/8} + {1/4} = {5/8}\nd) {5 1/3} − {1 1/9} = {4 2/9}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {4/9} × 2 = __B1__", "a": {"B1": "8/9"}, "expr": "fv"}, {"t": "b) {3/8} × 24 = __B1__", "a": {"B1": "9"}, "expr": "fv"}, {"t": "c) {5/6} × 3 = __B1__", "a": {"B1": "2 1/2"}, "expr": "fv"}], "sol": "Multiply the numerator by the whole number.\na) {4/9} × 2 = {8/9}\nb) {3/8} × 24 = 9\nc) {5/6} × 3 = {2 1/2}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {1/4} of 200 = __B1__", "a": {"B1": "50"}, "expr": "fv"}, {"t": "b) {2/5} of 100 = __B1__", "a": {"B1": "40"}, "expr": "fv"}, {"t": "c) {3/8} of 56 = __B1__", "a": {"B1": "21"}, "expr": "fv"}], "sol": "Divide by the denominator, multiply by the numerator.\na) {1/4} of 200 = 50\nb) {2/5} of 100 = 40\nc) {3/8} of 56 = 21"}, {"kind": "blank", "p": "An athlete runs {2/5} of a 20 km race in the first hour and {3/10} in the second hour.", "tag": "", "marks": "", "flat": [{"t": "a) Fraction of the race completed: __B1__", "a": {"B1": "7/10"}, "expr": "fv"}, {"t": "b) Distance run: __B1__ km", "a": {"B1": "14"}, "expr": "fv"}, {"t": "c) Fraction still to run: __B1__", "a": {"B1": "3/10"}, "expr": "fv"}, {"t": "d) Distance still to run: __B1__ km", "a": {"B1": "6"}, "expr": "fv"}], "sol": "a) {4/10} + {3/10} = {7/10}\nb) {7/10} of 20 = 14 km\nc) 1 − {7/10} = {3/10}\nd) 20 − 14 = 6 km"}]}, {"id": "s13", "label": "Review 6B", "sub": "Review set 6B", "slides": [{"kind": "blank", "p": "What mixed number is shaded? Then write it as an improper fraction.", "tag": "", "marks": "", "flat": [{"t": "a) __B1__", "a": {"B1": "2 3/4"}, "expr": "fm"}, {"t": "b) __B1__", "a": {"B1": "11/4"}, "expr": "fi"}], "sol": "a) two full shapes and 3 quarters: {2 3/4}\nb) 2 × 4 + 3 = 11, so {11/4}", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 88\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L68.0,10.0 A34,34 0 0 1 102.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L102.0,44.0 A34,34 0 0 1 68.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L68.0,78.0 A34,34 0 0 1 34.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M68.0,44 L34.0,44.0 A34,34 0 0 1 68.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,10.0 A34,34 0 0 1 184.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L184.0,44.0 A34,34 0 0 1 150.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L150.0,78.0 A34,34 0 0 1 116.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M150.0,44 L116.0,44.0 A34,34 0 0 1 150.0,10.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L232.0,10.0 A34,34 0 0 1 266.0,44.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L266.0,44.0 A34,34 0 0 1 232.0,78.0 Z\"/><path class=\"shd\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L232.0,78.0 A34,34 0 0 1 198.0,44.0 Z\"/><path class=\"cell\" style=\"stroke:var(--ink);stroke-width:1.1\" d=\"M232.0,44 L198.0,44.0 A34,34 0 0 1 232.0,10.0 Z\"/></svg>"}, {"kind": "blank", "p": "Write as a division, and hence as a whole number:", "tag": "", "marks": "", "flat": [{"t": "a) {40/8} = __B1__", "a": {"B1": "5"}, "expr": "fv"}, {"t": "b) {72/9} = __B1__", "a": {"B1": "8"}, "expr": "fv"}, {"t": "c) {99/11} = __B1__", "a": {"B1": "9"}, "expr": "fv"}], "sol": "Divide numerator by denominator.\na) {40/8} = 5\nb) {72/9} = 8\nc) {99/11} = 9"}, {"kind": "blank", "p": "It rained on one fifth of the 30 days of a holiday. On how many days did it rain?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "6"}, "expr": "fv"}], "sol": "{1/5} of 30 = 6"}, {"kind": "blank", "p": "Write as an improper fraction:", "tag": "", "marks": "", "flat": [{"t": "a) {3 5/6} = __B1__", "a": {"B1": "23/6"}, "expr": "fi"}, {"t": "b) {4 3/7} = __B1__", "a": {"B1": "31/7"}, "expr": "fi"}, {"t": "c) {5 2/5} = __B1__", "a": {"B1": "27/5"}, "expr": "fi"}], "sol": "Whole × denominator + numerator.\na) {3 5/6} = {23/6}\nb) {4 3/7} = {31/7}\nc) {5 2/5} = {27/5}"}, {"kind": "blank", "p": "Write in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) {2/16} = __B1__", "a": {"B1": "1/8"}, "expr": "fl"}, {"t": "b) {25/45} = __B1__", "a": {"B1": "5/9"}, "expr": "fl"}, {"t": "c) {60/32} = __B1__", "a": {"B1": "15/8"}, "expr": "fl"}], "sol": "Divide the numerator and denominator by their HCF.\na) HCF of 2 and 16 is 2: {2/16} = {1/8}\nb) HCF of 25 and 45 is 5: {25/45} = {5/9}\nc) HCF of 60 and 32 is 4: {60/32} = {15/8}"}, {"kind": "blank", "p": "Write in ascending order (separate with commas, e.g. {1/2}, {3/4}):", "tag": "", "marks": "", "flat": [{"t": "a) {4/5}, {7/10}, {2/3} → __B1__", "a": {"B1": "2/3, 7/10, 4/5"}, "expr": "flist"}, {"t": "b) {1 5/6}, {19/12}, {5/3} → __B1__", "a": {"B1": "19/12, 5/3, 1 5/6"}, "expr": "flist"}], "sol": "Write all the fractions with a common denominator, then order the numerators.\na) {2/3}, {7/10}, {4/5}\nb) {19/12}, {5/3}, {1 5/6}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) 3 + {3/5} + {4/5} = __B1__", "a": {"B1": "4 2/5"}, "expr": "fv"}, {"t": "b) {4 1/10} − {2 3/10} = __B1__", "a": {"B1": "1 4/5"}, "expr": "fv"}, {"t": "c) {11/6} + {14/18} = __B1__", "a": {"B1": "2 11/18"}, "expr": "fv"}], "sol": "Use a common denominator.\na) 3 + {3/5} + {4/5} = {4 2/5}\nb) {4 1/10} − {2 3/10} = {1 4/5}\nc) {11/6} + {14/18} = {2 11/18}"}, {"kind": "blank", "p": "Adam ate {5 1/3} samosas and Jill ate {3 2/3} samosas.", "tag": "", "marks": "", "flat": [{"t": "a) Adam's amount as an improper fraction: __B1__", "a": {"B1": "16/3"}, "expr": "fi"}, {"t": "b) Total eaten: __B1__", "a": {"B1": "9"}, "expr": "fv"}, {"t": "c) How many more did Adam eat? __B1__", "a": {"B1": "1 2/3"}, "expr": "fv"}], "sol": "a) {16/3}\nb) {16/3} + {11/3} = {27/3} = 9\nc) {16/3} − {11/3} = {5/3} = {1 2/3}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) {3/5} × 4 = __B1__", "a": {"B1": "2 2/5"}, "expr": "fv"}, {"t": "b) {2/7} × 21 = __B1__", "a": {"B1": "6"}, "expr": "fv"}, {"t": "c) 8 × {7/10} = __B1__", "a": {"B1": "5 3/5"}, "expr": "fv"}], "sol": "Multiply the numerator by the whole number.\na) {3/5} × 4 = {2 2/5}\nb) {2/7} × 21 = 6\nc) 8 × {7/10} = {5 3/5}"}, {"kind": "blank", "p": "Judy has 60 cards to write. She writes {1/3} of them on Monday, then {2/5} of the remaining cards on Tuesday.", "tag": "", "marks": "", "flat": [{"t": "a) Cards written on Monday: __B1__", "a": {"B1": "20"}, "expr": "fv"}, {"t": "b) Cards left after Monday: __B1__", "a": {"B1": "40"}, "expr": "fv"}, {"t": "c) Cards written on Tuesday: __B1__", "a": {"B1": "16"}, "expr": "fv"}, {"t": "d) Cards still to write: __B1__", "a": {"B1": "24"}, "expr": "fv"}], "sol": "a) {1/3} of 60 = 20\nb) 60 − 20 = 40\nc) {2/5} of 40 = 16\nd) 40 − 16 = 24"}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-g6-ch6';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Fractions</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('');
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { h += fr(esc(slide.p)); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi'].indexOf(qstep.expr)>=0?' fr':qstep.expr==='flist'?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi'].indexOf(step.expr)>=0?' fr':step.expr==='flist'?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — revisit it anytime from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+(item.status!=='unanswered'?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick);
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };

renderLogin();
})();
</script>
</body>
</html>
