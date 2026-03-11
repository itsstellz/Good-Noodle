[index.html](https://github.com/user-attachments/files/25886904/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Studio Flow</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root{--cream:#F7F4EF;--warm-white:#FDFBF8;--dusty-rose:#C4987A;--terracotta:#A0624A;--deep:#2C1F1A;--mid:#6B4F3F;--light-mid:#9E7B6A;--sage:#8A9E7E;--sage-light:#C2D4BA;--text:#3A2A22;--text-light:#7A5F54}
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'DM Sans',sans-serif;background:var(--cream);color:var(--text);min-height:100vh;overflow-x:hidden}
body::before{content:'';position:fixed;top:-200px;right:-200px;width:600px;height:600px;background:radial-gradient(circle,rgba(196,152,122,.12) 0%,transparent 70%);pointer-events:none;z-index:0}
body::after{content:'';position:fixed;bottom:-150px;left:-150px;width:500px;height:500px;background:radial-gradient(circle,rgba(138,158,126,.1) 0%,transparent 70%);pointer-events:none;z-index:0}
.app{max-width:820px;margin:0 auto;padding:0 24px 80px;position:relative;z-index:1}

header{padding:40px 0 28px;text-align:center;border-bottom:1px solid rgba(196,152,122,.25)}
.eyebrow{font-size:10px;letter-spacing:.22em;text-transform:uppercase;color:var(--dusty-rose);margin-bottom:10px}
header h1{font-family:'Cormorant Garamond',serif;font-size:40px;font-weight:300;color:var(--deep);line-height:1.1}
header h1 em{font-style:italic;color:var(--terracotta)}
header p{margin-top:8px;font-size:13px;color:var(--text-light);font-weight:300}

.tabs{display:flex;margin:28px 0 36px;border-bottom:1.5px solid rgba(196,152,122,.2);overflow-x:auto}
.tab-btn{flex-shrink:0;padding:12px 20px;font-family:'DM Sans',sans-serif;font-size:11px;letter-spacing:.1em;text-transform:uppercase;background:none;border:none;cursor:pointer;color:var(--text-light);position:relative;transition:color .2s;white-space:nowrap}
.tab-btn::after{content:'';position:absolute;bottom:-1.5px;left:0;right:0;height:2px;background:var(--terracotta);opacity:0;transition:opacity .2s}
.tab-btn.active{color:var(--terracotta)}.tab-btn.active::after{opacity:1}
.tab-btn .tab-count{display:inline-block;background:var(--terracotta);color:white;border-radius:100px;font-size:9px;padding:1px 6px;margin-left:5px;font-family:'DM Sans',sans-serif;letter-spacing:0;vertical-align:middle}
.tab-panel{display:none}.tab-panel.active{display:block;animation:fadeIn .25s ease}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}

.section-label{font-size:9.5px;letter-spacing:.2em;text-transform:uppercase;color:var(--light-mid);margin-bottom:16px;display:flex;align-items:center;gap:10px}
.section-label::after{content:'';flex:1;height:1px;background:rgba(196,152,122,.2)}

/* CHIPS */
.yesterday-section{margin-bottom:32px}
.workout-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(148px,1fr));gap:9px}
.workout-chip{background:var(--warm-white);border:1.5px solid rgba(196,152,122,.25);border-radius:12px;padding:13px 14px;cursor:pointer;transition:all .2s ease;text-align:left;position:relative;overflow:hidden}
.workout-chip::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(196,152,122,.08),transparent);opacity:0;transition:opacity .2s}
.workout-chip:hover{border-color:var(--dusty-rose);transform:translateY(-1px)}.workout-chip:hover::before{opacity:1}
.workout-chip.selected{background:var(--deep);border-color:var(--deep);transform:translateY(-2px);box-shadow:0 8px 24px rgba(44,31,26,.18)}
.workout-chip.selected .chip-name{color:var(--cream)}.workout-chip.selected .chip-sub{color:rgba(247,244,239,.6)}
.chip-icon{font-size:17px;margin-bottom:5px;display:block}.chip-name{font-size:12.5px;font-weight:500;color:var(--text);display:block}.chip-sub{font-size:11px;color:var(--text-light);display:block;margin-top:2px}
.rest-option{margin-top:10px}
.rest-btn{background:none;border:1.5px dashed rgba(196,152,122,.35);border-radius:12px;padding:11px 20px;font-family:'DM Sans',sans-serif;font-size:12px;color:var(--text-light);cursor:pointer;letter-spacing:.05em;transition:all .2s;width:100%}
.rest-btn:hover{border-color:var(--dusty-rose);color:var(--dusty-rose)}.rest-btn.selected{background:rgba(196,152,122,.1);border-color:var(--dusty-rose);color:var(--terracotta);border-style:solid}

/* FEEL / TIME */
.feel-row{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:32px}
.feel-pill{padding:9px 16px;border-radius:100px;border:1.5px solid rgba(196,152,122,.25);background:var(--warm-white);font-size:12px;cursor:pointer;transition:all .2s;color:var(--text-light)}
.feel-pill:hover{border-color:var(--dusty-rose);color:var(--text)}.feel-pill.selected{background:var(--sage);border-color:var(--sage);color:white}
.time-row{display:flex;gap:8px;margin-bottom:32px}
.time-pill{flex:1;padding:10px;border-radius:10px;border:1.5px solid rgba(196,152,122,.25);background:var(--warm-white);font-size:12px;cursor:pointer;transition:all .2s;color:var(--text-light);text-align:center}
.time-pill:hover{border-color:var(--dusty-rose);color:var(--text)}.time-pill.selected{background:var(--terracotta);border-color:var(--terracotta);color:white}

.focus-note{background:var(--warm-white);border:1.5px solid rgba(196,152,122,.2);border-radius:14px;padding:14px 18px;margin-bottom:32px;font-size:13px;color:var(--text);font-family:'DM Sans',sans-serif;width:100%;resize:none;outline:none;transition:border-color .2s;font-weight:300;min-height:52px}
.focus-note:focus{border-color:var(--dusty-rose)}.focus-note::placeholder{color:rgba(122,95,84,.45);font-style:italic}

.generate-btn{width:100%;padding:17px;background:var(--deep);color:var(--cream);border:none;border-radius:14px;font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:300;letter-spacing:.04em;cursor:pointer;transition:all .25s ease;margin-bottom:36px}
.generate-btn:hover{background:var(--terracotta);transform:translateY(-2px);box-shadow:0 12px 36px rgba(160,98,74,.28)}.generate-btn:disabled{opacity:.45;cursor:not-allowed;transform:none}
.generate-btn .btn-sub{font-family:'DM Sans',sans-serif;font-size:11px;letter-spacing:.12em;text-transform:uppercase;opacity:.6;display:block;margin-top:2px}

/* LOADING */
.loading-state{text-align:center;padding:40px 20px}
.loading-dots{display:flex;justify-content:center;gap:8px;margin-bottom:14px}
.loading-dots span{width:8px;height:8px;background:var(--dusty-rose);border-radius:50%;animation:bounce 1.2s ease infinite}
.loading-dots span:nth-child(2){animation-delay:.2s}.loading-dots span:nth-child(3){animation-delay:.4s}
@keyframes bounce{0%,80%,100%{transform:scale(.7);opacity:.4}40%{transform:scale(1);opacity:1}}
.loading-text{font-family:'Cormorant Garamond',serif;font-size:19px;font-weight:300;font-style:italic;color:var(--mid)}
.loading-sub{font-size:11px;color:var(--text-light);margin-top:6px;letter-spacing:.05em}

/* RESULT */
.result-card{background:var(--warm-white);border:1.5px solid rgba(196,152,122,.2);border-radius:20px;overflow:hidden;animation:slideUp .4s ease;margin-bottom:20px}
@keyframes slideUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}
.result-header{background:var(--deep);padding:22px 28px;color:var(--cream)}
.result-header .workout-title{font-family:'Cormorant Garamond',serif;font-size:26px;font-weight:300;margin-bottom:3px}
.result-header .workout-meta{font-size:10px;letter-spacing:.15em;text-transform:uppercase;opacity:.55}
.result-header .workout-tagline{margin-top:8px;font-size:13px;opacity:.7;font-style:italic;font-family:'Cormorant Garamond',serif}
.result-body{padding:24px 28px}

/* EXERCISE TABLE in result */
.ex-result-table{width:100%;border-collapse:collapse;margin-top:4px}
.ex-result-table th{text-align:left;font-size:9px;letter-spacing:.18em;text-transform:uppercase;color:var(--light-mid);padding:0 8px 12px 0;font-weight:400;border-bottom:1px solid rgba(196,152,122,.2)}
.ex-result-table th:not(:first-child){text-align:center}
.ex-result-table td{padding:10px 8px 10px 0;border-bottom:1px solid rgba(196,152,122,.08);vertical-align:top;font-size:13px}
.ex-result-table tr:last-child td{border-bottom:none}
.ex-result-table td:not(:first-child){text-align:center;color:var(--text-light);font-size:12.5px}
.ex-nm{font-weight:500;color:var(--text);line-height:1.3}
.ex-fm{font-size:11px;color:var(--light-mid);margin-top:3px;font-style:italic;line-height:1.35}
.ex-wt{color:var(--terracotta)!important;font-weight:600!important;font-size:13px!important}
.ex-sets-td{color:var(--mid)!important}
.section-header-row td{padding-top:18px!important;padding-bottom:4px!important;border-bottom:none!important}
.section-header-row .ex-nm{font-family:'Cormorant Garamond',serif;font-size:16px;font-weight:400;color:var(--terracotta);font-style:normal}
.coach-box{background:rgba(138,158,126,.1);border-left:3px solid var(--sage);border-radius:0 10px 10px 0;padding:12px 16px;margin-bottom:20px;font-size:13px;color:var(--mid);font-style:italic;font-family:'Cormorant Garamond',serif;line-height:1.6}
.result-actions{display:flex;gap:10px;padding:0 28px 24px}
.action-btn{flex:1;padding:11px;border-radius:10px;font-family:'DM Sans',sans-serif;font-size:12px;cursor:pointer;transition:all .2s}
.action-btn.secondary{background:none;border:1.5px solid rgba(196,152,122,.3);color:var(--text-light)}.action-btn.secondary:hover{border-color:var(--dusty-rose);color:var(--terracotta)}
.action-btn.primary{background:var(--terracotta);border:none;color:white}.action-btn.primary:hover{background:var(--deep)}
.error-msg{background:rgba(160,98,74,.08);border:1px solid rgba(160,98,74,.22);border-radius:12px;padding:14px 18px;font-size:13px;color:var(--terracotta);text-align:center;margin-bottom:18px}

/* GUIDE TAB */
.guide-intro{margin-bottom:28px}
.guide-intro p{font-size:13px;color:var(--text-light);line-height:1.7}
.guide-nav{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:28px}
.guide-nav-btn{padding:8px 16px;border-radius:100px;border:1.5px solid rgba(196,152,122,.25);background:var(--warm-white);font-size:11.5px;cursor:pointer;transition:all .2s;color:var(--text-light)}
.guide-nav-btn:hover{border-color:var(--dusty-rose);color:var(--text)}.guide-nav-btn.active{background:var(--deep);border-color:var(--deep);color:var(--cream)}
.guide-section{display:none}.guide-section.active{display:block;animation:fadeIn .2s ease}
.guide-card{background:var(--warm-white);border:1.5px solid rgba(196,152,122,.16);border-radius:16px;margin-bottom:12px;overflow:hidden}
.guide-card-header{display:flex;align-items:center;justify-content:space-between;padding:16px 20px;cursor:pointer;user-select:none}
.guide-card-header:hover{background:rgba(196,152,122,.04)}
.guide-card-left{}
.guide-ex-name{font-family:'Cormorant Garamond',serif;font-size:19px;font-weight:300;color:var(--deep)}
.guide-ex-sub{font-size:11px;color:var(--text-light);margin-top:2px;letter-spacing:.04em}
.guide-card-right{display:flex;align-items:center;gap:10px;flex-shrink:0}
.guide-weight-badge{background:rgba(160,98,74,.1);color:var(--terracotta);border-radius:100px;padding:4px 12px;font-size:11px;font-weight:500;white-space:nowrap}
.guide-sets-badge{background:rgba(44,31,26,.07);color:var(--mid);border-radius:100px;padding:4px 12px;font-size:11px;white-space:nowrap}
.guide-toggle{font-size:14px;color:var(--light-mid);transition:transform .2s}
.guide-card.expanded .guide-toggle{transform:rotate(180deg)}
.guide-detail{max-height:0;overflow:hidden;transition:max-height .3s ease}
.guide-card.expanded .guide-detail{max-height:500px;border-top:1px solid rgba(196,152,122,.12)}
.guide-detail-inner{padding:16px 20px 20px;display:grid;grid-template-columns:1fr 1fr;gap:16px}
.guide-detail-inner.single{grid-template-columns:1fr}
.guide-detail-block label{font-size:9px;letter-spacing:.18em;text-transform:uppercase;color:var(--light-mid);display:block;margin-bottom:6px}
.guide-detail-block p{font-size:13px;color:var(--text);line-height:1.6}
.guide-tip-box{background:rgba(138,158,126,.08);border-left:3px solid var(--sage-light);border-radius:0 8px 8px 0;padding:10px 14px;font-size:12.5px;color:var(--mid);font-style:italic;font-family:'Cormorant Garamond',serif;line-height:1.55;margin-top:12px;grid-column:1/-1}
.guide-prog{margin-top:8px}
.prog-row{display:flex;align-items:center;gap:10px;margin-bottom:6px}
.prog-label{font-size:11px;color:var(--text-light);width:70px;flex-shrink:0}
.prog-bar-bg{flex:1;height:6px;background:rgba(196,152,122,.15);border-radius:3px}
.prog-bar{height:100%;border-radius:3px;background:var(--terracotta);transition:width .5s ease}
.guide-section-title{font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:300;color:var(--deep);margin-bottom:6px}
.guide-section-title em{font-style:italic;color:var(--terracotta)}
.guide-section-sub{font-size:12.5px;color:var(--text-light);margin-bottom:20px;line-height:1.6}

/* WEEKLY */
.week-intro{text-align:center;padding:48px 20px}
.week-intro-icon{font-size:36px;margin-bottom:16px}
.week-intro-title{font-family:'Cormorant Garamond',serif;font-size:26px;font-weight:300;color:var(--deep);margin-bottom:10px}
.week-intro-title em{font-style:italic;color:var(--terracotta)}
.week-intro-sub{font-size:13px;color:var(--text-light);line-height:1.65;max-width:380px;margin:0 auto 28px}
.week-gen-big-btn{padding:15px 36px;background:var(--deep);color:var(--cream);border:none;border-radius:12px;font-family:'Cormorant Garamond',serif;font-size:20px;font-weight:300;cursor:pointer;transition:all .25s}
.week-gen-big-btn:hover{background:var(--terracotta);transform:translateY(-2px);box-shadow:0 10px 28px rgba(160,98,74,.25)}
.week-header-row{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:18px}
.week-label{font-family:'Cormorant Garamond',serif;font-size:24px;font-weight:300;color:var(--deep)}
.week-label span{font-style:italic;color:var(--terracotta)}
.regen-small{padding:8px 16px;background:none;border:1.5px solid rgba(196,152,122,.3);border-radius:8px;font-size:11px;color:var(--text-light);cursor:pointer;transition:all .2s;letter-spacing:.06em}
.regen-small:hover{border-color:var(--dusty-rose);color:var(--terracotta)}
.week-summary{display:flex;gap:8px;margin-bottom:22px;flex-wrap:wrap}
.summary-chip{padding:6px 13px;border-radius:100px;font-size:11px;color:var(--text-light);background:var(--warm-white);border:1px solid rgba(196,152,122,.2)}
.summary-chip strong{color:var(--text)}
.week-grid{display:flex;flex-direction:column;gap:9px}
.day-row{background:var(--warm-white);border:1.5px solid rgba(196,152,122,.18);border-radius:16px;overflow:hidden;transition:border-color .2s}
.day-row.today-row{border-color:var(--terracotta);box-shadow:0 4px 20px rgba(160,98,74,.12)}.day-row.rest-row{opacity:.8}
.day-header{display:flex;align-items:center;justify-content:space-between;padding:14px 20px;cursor:pointer;user-select:none}
.day-header:hover{background:rgba(196,152,122,.04)}
.day-left{display:flex;align-items:center;gap:14px}
.day-name{font-size:10.5px;letter-spacing:.15em;text-transform:uppercase;color:var(--light-mid)}
.day-workout-name{font-family:'Cormorant Garamond',serif;font-size:19px;font-weight:300;color:var(--deep);margin-top:1px}
.day-workout-name.rest-label{font-style:italic;color:var(--light-mid);font-size:17px}
.day-badge{padding:4px 10px;border-radius:100px;font-size:10px;letter-spacing:.06em;font-weight:500;text-transform:uppercase}
.badge-cardio{background:rgba(138,158,126,.15);color:var(--sage)}.badge-glutes{background:rgba(196,152,122,.15);color:var(--terracotta)}.badge-upper{background:rgba(44,31,26,.08);color:var(--mid)}.badge-core{background:rgba(160,98,74,.1);color:var(--dusty-rose)}.badge-full{background:rgba(196,152,122,.12);color:var(--terracotta)}.badge-studio{background:rgba(138,158,126,.15);color:var(--sage)}.badge-golf{background:rgba(44,31,26,.06);color:var(--mid)}.badge-rest{background:rgba(196,152,122,.08);color:var(--light-mid)}.badge-today{background:var(--terracotta);color:white}
.day-right{display:flex;align-items:center;gap:10px}
.day-dur{font-size:11px;color:var(--light-mid)}
.day-toggle{font-size:15px;color:var(--light-mid);transition:transform .2s;line-height:1}
.day-row.expanded .day-toggle{transform:rotate(180deg)}
.day-detail{max-height:0;overflow:hidden;transition:max-height .35s ease}
.day-row.expanded .day-detail{max-height:1400px;border-top:1px solid rgba(196,152,122,.12)}
.day-detail-inner{padding:18px 20px 22px}
.exercise-table{width:100%;border-collapse:collapse}
.exercise-table th{text-align:left;font-size:9px;letter-spacing:.18em;text-transform:uppercase;color:var(--light-mid);padding:0 0 10px;font-weight:400;border-bottom:1px solid rgba(196,152,122,.15)}
.exercise-table th.center{text-align:center}
.exercise-table td{padding:9px 0;border-bottom:1px solid rgba(196,152,122,.08);font-size:13px;vertical-align:top}
.exercise-table tr:last-child td{border-bottom:none}
.ex-name{font-weight:400;color:var(--text);line-height:1.3}.ex-tip{font-size:11px;color:var(--light-mid);margin-top:3px;font-style:italic;line-height:1.4}
.ex-sets{text-align:center;color:var(--terracotta);font-weight:500;font-size:13px;padding-left:12px;white-space:nowrap}
.day-note{margin-top:14px;background:rgba(138,158,126,.08);border-left:3px solid var(--sage-light);border-radius:0 8px 8px 0;padding:10px 14px;font-size:12.5px;color:var(--mid);font-style:italic;font-family:'Cormorant Garamond',serif;line-height:1.55}
.rest-detail{font-style:italic;color:var(--text-light);font-size:13px;line-height:1.6}

/* ARCHIVE */
.archive-empty{text-align:center;padding:60px 20px}
.archive-empty-icon{font-size:40px;margin-bottom:18px}
.archive-empty-title{font-family:'Cormorant Garamond',serif;font-size:24px;font-weight:300;color:var(--deep);margin-bottom:10px}
.archive-empty-title em{font-style:italic;color:var(--terracotta)}
.archive-empty-sub{font-size:13px;color:var(--text-light);line-height:1.65;max-width:340px;margin:0 auto}
.archive-header-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:20px}
.archive-title{font-family:'Cormorant Garamond',serif;font-size:24px;font-weight:300;color:var(--deep)}
.archive-title span{font-style:italic;color:var(--terracotta)}
.archive-stats{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:20px}
.archive-stat{padding:6px 14px;border-radius:100px;font-size:11px;color:var(--text-light);background:var(--warm-white);border:1px solid rgba(196,152,122,.2)}
.archive-stat strong{color:var(--text)}
.archive-filter-row{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:20px}
.filter-chip{padding:7px 14px;border-radius:100px;border:1.5px solid rgba(196,152,122,.22);background:var(--warm-white);font-size:11px;cursor:pointer;transition:all .2s;color:var(--text-light)}
.filter-chip:hover{border-color:var(--dusty-rose);color:var(--text)}.filter-chip.active{background:var(--deep);border-color:var(--deep);color:var(--cream)}
.month-group{margin-bottom:28px}
.month-heading{font-size:10px;letter-spacing:.18em;text-transform:uppercase;color:var(--light-mid);margin-bottom:12px;padding-bottom:8px;border-bottom:1px solid rgba(196,152,122,.15)}
.archive-entry{background:var(--warm-white);border:1.5px solid rgba(196,152,122,.16);border-radius:14px;margin-bottom:9px;overflow:hidden;transition:border-color .2s}
.archive-entry:hover{border-color:rgba(196,152,122,.35)}
.entry-header{display:flex;align-items:center;justify-content:space-between;padding:14px 18px;cursor:pointer;user-select:none}
.entry-left{display:flex;align-items:center;gap:12px}
.entry-date-block{text-align:center;min-width:42px}
.entry-day-num{font-family:'Cormorant Garamond',serif;font-size:24px;font-weight:300;color:var(--deep);line-height:1}
.entry-day-name{font-size:9px;letter-spacing:.12em;text-transform:uppercase;color:var(--light-mid);margin-top:1px}
.entry-workout-name{font-family:'Cormorant Garamond',serif;font-size:17px;font-weight:300;color:var(--deep)}
.entry-meta{font-size:11px;color:var(--text-light);margin-top:2px}
.entry-right{display:flex;align-items:center;gap:10px}
.entry-badge{padding:3px 9px;border-radius:100px;font-size:9.5px;letter-spacing:.06em;font-weight:500;text-transform:uppercase}
.entry-toggle{font-size:14px;color:var(--light-mid);transition:transform .2s}
.archive-entry.expanded .entry-toggle{transform:rotate(180deg)}
.entry-detail{max-height:0;overflow:hidden;transition:max-height .3s ease}
.archive-entry.expanded .entry-detail{max-height:2000px;border-top:1px solid rgba(196,152,122,.1)}
.entry-detail-inner{padding:16px 18px 18px}
.entry-workout-html{font-size:13px;line-height:1.8;color:var(--text);font-weight:300}
.entry-workout-html table{width:100%;border-collapse:collapse;font-size:12.5px}
.entry-workout-html th{font-size:9px;letter-spacing:.15em;text-transform:uppercase;color:var(--light-mid);padding:0 6px 8px 0;font-weight:400;border-bottom:1px solid rgba(196,152,122,.15);text-align:left}
.entry-workout-html th:not(:first-child){text-align:center}
.entry-workout-html td{padding:8px 6px 8px 0;border-bottom:1px solid rgba(196,152,122,.07);vertical-align:top}
.entry-workout-html tr:last-child td{border-bottom:none}
.entry-workout-html td:not(:first-child){text-align:center;color:var(--text-light)}
.entry-workout-html .coach-box{background:rgba(138,158,126,.08);border-left:3px solid var(--sage);border-radius:0 8px 8px 0;padding:10px 14px;margin:0 0 14px;font-size:12px;color:var(--mid);font-style:italic;font-family:'Cormorant Garamond',serif}
.entry-feel-tag{display:inline-block;padding:3px 10px;border-radius:100px;font-size:10px;background:rgba(138,158,126,.12);color:var(--sage);border:1px solid rgba(138,158,126,.2);margin-bottom:10px}
.entry-note-row{margin-top:10px;font-size:12px;color:var(--text-light);font-style:italic;border-top:1px solid rgba(196,152,122,.1);padding-top:10px}
.entry-actions{display:flex;gap:8px;margin-top:12px}
.entry-del-btn{padding:7px 14px;background:none;border:1.5px solid rgba(196,152,122,.25);border-radius:8px;font-size:11px;color:var(--text-light);cursor:pointer;transition:all .2s}
.entry-del-btn:hover{border-color:#c0392b;color:#c0392b}
.streak-banner{background:var(--deep);border-radius:14px;padding:16px 20px;margin-bottom:24px;display:flex;align-items:center;gap:16px;color:var(--cream)}
.streak-fire{font-size:28px}.streak-count{font-family:'Cormorant Garamond',serif;font-size:22px;font-weight:300}.streak-sub{font-size:11px;opacity:.65;letter-spacing:.05em;margin-top:1px}
</style>
</head>
<body>
<div class="app">

<header>
  <div class="eyebrow">Adaptive Fitness</div>
  <h1>Studio <em>Flow</em></h1>
  <p>Your workouts, built around your life — not the other way around</p>
</header>

<div class="tabs">
  <button class="tab-btn active" onclick="switchTab('today',this)">Today</button>
  <button class="tab-btn" onclick="switchTab('guide',this)">Exercise Guide</button>
  <button class="tab-btn" onclick="switchTab('week',this)">Weekly Plan</button>
  <button class="tab-btn" id="archiveTabBtn" onclick="switchTab('archive',this)">Archive</button>
</div>

<!-- ══ TODAY ══ -->
<div id="tab-today" class="tab-panel active">
  <div class="yesterday-section">
    <div class="section-label">What did you do yesterday?</div>
    <div class="workout-grid">
      <div class="workout-chip" data-value="12330" onclick="sel(this)"><span class="chip-icon">🏃‍♀️</span><span class="chip-name">12·3·30</span><span class="chip-sub">Incline walk</span></div>
      <div class="workout-chip" data-value="heated_pilates" onclick="sel(this)"><span class="chip-icon">🔥</span><span class="chip-name">Heated Pilates</span><span class="chip-sub">Heated Room</span></div>
      <div class="workout-chip" data-value="lagree" onclick="sel(this)"><span class="chip-icon">⚡</span><span class="chip-name">Lagree</span><span class="chip-sub">Megaformer</span></div>
      <div class="workout-chip" data-value="glutes_gym" onclick="sel(this)"><span class="chip-icon">🍑</span><span class="chip-name">Glute Day</span><span class="chip-sub">Gym — lower</span></div>
      <div class="workout-chip" data-value="upper_gym" onclick="sel(this)"><span class="chip-icon">💪</span><span class="chip-name">Upper Body</span><span class="chip-sub">Gym — upper</span></div>
      <div class="workout-chip" data-value="abs_core" onclick="sel(this)"><span class="chip-icon">🌀</span><span class="chip-name">Abs + Core</span><span class="chip-sub">Gym / mat</span></div>
      <div class="workout-chip" data-value="stairmaster" onclick="sel(this)"><span class="chip-icon">🪜</span><span class="chip-name">Stairmaster</span><span class="chip-sub">Cardio</span></div>
      <div class="workout-chip" data-value="rowing" onclick="sel(this)"><span class="chip-icon">🚣‍♀️</span><span class="chip-name">Rowing</span><span class="chip-sub">Full body cardio</span></div>
      <div class="workout-chip" data-value="golf_18" onclick="sel(this)"><span class="chip-icon">⛳</span><span class="chip-name">Golf 18 holes</span><span class="chip-sub">With cart</span></div>
      <div class="workout-chip" data-value="golf_range" onclick="sel(this)"><span class="chip-icon">🏌️‍♀️</span><span class="chip-name">Driving Range</span><span class="chip-sub">Golf practice</span></div>
      <div class="workout-chip" data-value="full_body_gym" onclick="sel(this)"><span class="chip-icon">🏋️‍♀️</span><span class="chip-name">Full Body</span><span class="chip-sub">Gym session</span></div>
    </div>
    <div class="rest-option"><button class="rest-btn" id="restBtn" onclick="selRest()">Rest day / Nothing yesterday</button></div>
  </div>

  <div class="section-label">What do you want to focus on today?</div>
  <div class="workout-grid" style="margin-bottom:32px">
    <div class="workout-chip" data-value="glutes_gym" onclick="selFocus(this)"><span class="chip-icon">🍑</span><span class="chip-name">Glute Day</span><span class="chip-sub">Hip thrusts, RDLs</span></div>
    <div class="workout-chip" data-value="upper_gym" onclick="selFocus(this)"><span class="chip-icon">💪</span><span class="chip-name">Upper Body</span><span class="chip-sub">Arms, back, shoulders</span></div>
    <div class="workout-chip" data-value="abs_core" onclick="selFocus(this)"><span class="chip-icon">🌀</span><span class="chip-name">Abs + Core</span><span class="chip-sub">Pilates-style</span></div>
    <div class="workout-chip" data-value="full_body_gym" onclick="selFocus(this)"><span class="chip-icon">🏋️‍♀️</span><span class="chip-name">Full Body</span><span class="chip-sub">Total burn</span></div>
    <div class="workout-chip" data-value="12330" onclick="selFocus(this)"><span class="chip-icon">🏃‍♀️</span><span class="chip-name">12·3·30</span><span class="chip-sub">+ core finisher</span></div>
    <div class="workout-chip" data-value="stairmaster" onclick="selFocus(this)"><span class="chip-icon">🪜</span><span class="chip-name">Stairmaster</span><span class="chip-sub">Cardio + glutes</span></div>
    <div class="workout-chip" data-value="heated_pilates" onclick="selFocus(this)"><span class="chip-icon">🔥</span><span class="chip-name">Heated Pilates</span><span class="chip-sub">Stretch & tone</span></div>
    <div class="workout-chip" data-value="lagree" onclick="selFocus(this)"><span class="chip-icon">⚡</span><span class="chip-name">Lagree</span><span class="chip-sub">Slow burn</span></div>
    <div class="workout-chip" data-value="surprise" onclick="selFocus(this)"><span class="chip-icon">✨</span><span class="chip-name">Surprise Me</span><span class="chip-sub">AI picks for you</span></div>
  </div>

  <div class="section-label">How do you feel today?</div>
  <div class="feel-row">
    <div class="feel-pill" onclick="selFeel(this)" data-value="fresh">Fresh & energized ✨</div>
    <div class="feel-pill" onclick="selFeel(this)" data-value="good">Pretty good 💚</div>
    <div class="feel-pill" onclick="selFeel(this)" data-value="tired">A little tired 😴</div>
    <div class="feel-pill" onclick="selFeel(this)" data-value="sore">Sore / achy 🩹</div>
    <div class="feel-pill" onclick="selFeel(this)" data-value="low">Low energy 🌫️</div>
  </div>

  <div class="section-label">Time available</div>
  <div class="time-row">
    <div class="time-pill" onclick="selTime(this)" data-value="20">20 min</div>
    <div class="time-pill" onclick="selTime(this)" data-value="30">30 min</div>
    <div class="time-pill" onclick="selTime(this)" data-value="45">45 min</div>
    <div class="time-pill" onclick="selTime(this)" data-value="60">60 min</div>
    <div class="time-pill" onclick="selTime(this)" data-value="90">90+ min</div>
  </div>

  <div class="section-label">Anything specific?</div>
  <textarea class="focus-note" id="focusNote" placeholder="e.g. 'glutes are super sore' or 'want to add stairmaster after' or 'skip single-leg moves'…" rows="2"></textarea>

  <button class="generate-btn" id="generateBtn" onclick="generateWorkout()">
    Build My Workout
    <span class="btn-sub">Pulled from your personal guide</span>
  </button>
  <div id="outputSection"></div>
</div>

<!-- ══ GUIDE TAB ══ -->
<div id="tab-guide" class="tab-panel">
  <div class="guide-intro">
    <p>Your personal exercise library — specific weights, sets, and reps calibrated for your body and goals. Tap any exercise to see full details and form cues. These are the exact prescriptions the AI pulls from when building your workouts.</p>
  </div>
  <div class="guide-nav" id="guideNav">
    <button class="guide-nav-btn active" onclick="switchGuide('glutes',this)">🍑 Glutes</button>
    <button class="guide-nav-btn" onclick="switchGuide('upper',this)">💪 Upper Body</button>
    <button class="guide-nav-btn" onclick="switchGuide('core',this)">🌀 Core</button>
    <button class="guide-nav-btn" onclick="switchGuide('cardio',this)">🏃‍♀️ Cardio</button>
    <button class="guide-nav-btn" onclick="switchGuide('fullbody',this)">🏋️ Full Body</button>
  </div>
  <div id="guideContent"></div>
</div>

<!-- ══ WEEK TAB ══ -->
<div id="tab-week" class="tab-panel">
  <div id="weekContent">
    <div class="week-intro">
      <div class="week-intro-icon">📅</div>
      <div class="week-intro-title">Your <em>Week at a Glance</em></div>
      <div class="week-intro-sub">A smart 7-day split built from your exercise guide — specific weights, sets & reps for every move. Tap any day to expand.</div>
      <button class="week-gen-big-btn" onclick="generateWeek()">Generate This Week's Plan</button>
    </div>
  </div>
</div>

<!-- ══ ARCHIVE TAB ══ -->
<div id="tab-archive" class="tab-panel">
  <div id="archiveContent"></div>
</div>

</div>

<script>
// ════════════════════════════════════════
// EXERCISE GUIDE DATABASE
// ════════════════════════════════════════
const GUIDE = {
  glutes: {
    title: "Glute Growth", subtitle: "Hip-hinge focused — grow the glutes without bulking the quads. All weights calibrated for your frame (122 lbs, beginner-intermediate).",
    exercises: [
      { name:"Smith Machine Hip Thrust", sub:"Primary glute builder", weight:"45 lb plate each side (115 lbs total)", sets:"4 sets × 12 reps", rest:"90 sec", muscles:"Glutes max, glutes med", form:"Bar across hip bones with pad. Drive through heels, squeeze hard at top for 2 sec. Keep chin tucked.", tip:"At the top your shins should be vertical — adjust foot position if knees cave.", progress:"Once 4×12 feels easy, add 5 lbs per side.", intensity:85, beginner:false },
      { name:"Dumbbell Romanian Deadlift", sub:"Hamstrings + glutes, not quads", weight:"25–30 lb dumbbells", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Glutes, hamstrings", form:"Hinge at hips, push them back. Dumbbells stay close to legs. Feel deep stretch in hamstrings. Drive hips forward to stand.", tip:"Soften knees slightly — this is NOT a squat. It's a hip hinge.", progress:"Move to 35 lbs when 3×15 is easy.", intensity:70, beginner:true },
      { name:"Cable Kickback", sub:"Isolation — shape without bulk", weight:"10–15 lbs on cable", sets:"3 sets × 20 reps each leg", rest:"45 sec", muscles:"Glutes max", form:"Lean forward slightly on cable machine. Kick straight back, squeeze glute hard at top. Don't swing.", tip:"Control the return — the eccentric (lowering) builds shape.", progress:"Add weight when form stays perfect for all 20 reps.", intensity:55, beginner:true },
      { name:"Leg Press — High Foot Placement", sub:"Glute-bias leg press", weight:"90–110 lbs (1 full stack side + extra)", sets:"4 sets × 15 reps", rest:"75 sec", muscles:"Glutes, light quads", form:"Place feet HIGH on platform, shoulder-width. Push through heels, don't lock out knees at top.", tip:"High foot placement shifts load from quads to glutes.", progress:"Add 10 lbs when 4×15 is comfortable.", intensity:75, beginner:true },
      { name:"Glute Bridge with Dumbbell", sub:"Floor variation — great for activation", weight:"35–40 lb dumbbell on hips", sets:"3 sets × 20 reps", rest:"45 sec", muscles:"Glutes max, core", form:"Feet flat on floor hip-width. Drive hips up, squeeze glutes, hold 1 sec at top. Don't arch lower back.", tip:"Great warm-up or finisher. Use bodyweight first to activate.", progress:"Increase weight or add a band above knees.", intensity:50, beginner:true },
      { name:"Side-Lying Clamshell with Band", sub:"Glute med — prevents thigh bulk", weight:"Light resistance band above knees", sets:"3 sets × 25 reps each side", rest:"30 sec", muscles:"Glutes medius, hip abductors", form:"Lie on side, knees bent 45°. Rotate top knee up like a clamshell. Don't roll your hips back.", tip:"Slow and controlled — you should feel the outer glute burning.", progress:"Move to medium resistance band.", intensity:40, beginner:true },
      { name:"Single-Leg Glute Bridge", sub:"Unilateral balance + glute", weight:"Bodyweight or 15–20 lb dumbbell", sets:"3 sets × 15 reps each leg", rest:"45 sec", muscles:"Glutes, hamstrings, core", form:"One foot on floor, other leg extended or bent. Drive single hip up, squeeze at top.", tip:"Keeps both glutes even — fixes imbalances.", progress:"Add a dumbbell once bodyweight feels too easy.", intensity:55, beginner:true },
      { name:"Sumo Squat with Kettlebell", sub:"Inner thigh + glute, less quad than regular squat", weight:"25–30 lb kettlebell", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Glutes, inner thighs, light quads", form:"Wide stance, toes out 45°. Hold KB between legs. Sit back not down. Keep chest proud.", tip:"The wide stance targets glutes over quads — this is your squat alternative.", progress:"35 lb KB when form is solid.", intensity:65, beginner:true },
    ]
  },
  upper: {
    title: "Upper Body Tone", subtitle: "Lean arms, defined shoulders, open back — no bulk, just long and sculpted. Light-moderate weights, higher reps.",
    exercises: [
      { name:"Lat Pulldown — Cable", sub:"V-taper back, great posture", weight:"40–50 lbs", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Lats, biceps, rear delts", form:"Grip wide. Pull bar to upper chest, elbows drive down and back. Lean back slightly.", tip:"Think 'elbows to back pockets' — don't just pull with hands.", progress:"Increase to 55 lbs once 3×15 is easy.", intensity:65, beginner:true },
      { name:"Seated Cable Row", sub:"Mid-back definition", weight:"35–45 lbs", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Rhomboids, mid traps, biceps", form:"Sit tall, pull handle to belly button, squeeze shoulder blades together. Hold 1 sec.", tip:"Don't use momentum — control each rep.", progress:"Add 5 lbs.", intensity:60, beginner:true },
      { name:"Dumbbell Shoulder Press", sub:"Toned shoulders without width", weight:"12–15 lb dumbbells", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Front + lateral deltoids", form:"Seated or standing, press overhead without flaring elbows too wide. Slow down on the way down.", tip:"Don't lock out at the top — keep tension in the shoulder.", progress:"Move to 17.5 lbs.", intensity:60, beginner:true },
      { name:"Lateral Raise", sub:"Shoulder cap — sculpted look", weight:"8–10 lb dumbbells", sets:"3 sets × 20 reps", rest:"45 sec", muscles:"Lateral deltoids", form:"Slight bend in elbow, raise to shoulder height. Lead with elbows, not wrists. Small thumb-down tilt.", tip:"Go lighter than you think — 8 lbs should burn by rep 15.", progress:"12 lbs when 3×20 is easy.", intensity:50, beginner:true },
      { name:"Tricep Pushdown — Cable Rope", sub:"Tones backs of arms", weight:"20–25 lbs", sets:"3 sets × 20 reps", rest:"45 sec", muscles:"Triceps", form:"Rope attachment, elbows pinned to sides. Push rope down AND apart at the bottom. Squeeze at the end.", tip:"Keep elbows glued — no swinging.", progress:"Add 5 lbs.", intensity:50, beginner:true },
      { name:"Dumbbell Bicep Curl", sub:"Lean, defined arms", weight:"12–15 lb dumbbells", sets:"3 sets × 15 reps", rest:"45 sec", muscles:"Biceps", form:"Alternate arms. Full range of motion — all the way down. Don't swing.", tip:"Slow the way down — 2 seconds up, 3 seconds down.", progress:"Move to 17.5 lbs.", intensity:50, beginner:true },
      { name:"Face Pull — Cable", sub:"Rear delts + posture", weight:"20–25 lbs", sets:"3 sets × 20 reps", rest:"45 sec", muscles:"Rear deltoids, external rotators", form:"Rope at face height. Pull toward face, flare elbows wide. Hands end beside ears.", tip:"Essential for posture — counteracts phone/desk habits.", progress:"25–30 lbs.", intensity:45, beginner:true },
      { name:"Single-Arm Dumbbell Row", sub:"Back definition", weight:"20–25 lb dumbbell", sets:"3 sets × 15 reps each arm", rest:"60 sec", muscles:"Lats, rhomboids, rear delt", form:"Knee on bench. Pull elbow straight back past hip. Don't rotate torso.", tip:"Imagine tucking the dumbbell into your back pocket.", progress:"30 lb dumbbell.", intensity:60, beginner:true },
    ]
  },
  core: {
    title: "Abs + Core", subtitle: "Pilates-inspired — flat stomach, strong center, no bulky ab muscles. Controlled movement over heavy weight.",
    exercises: [
      { name:"Dead Bug", sub:"Deep core — the base of everything", weight:"Bodyweight (or 5 lb dumbbell overhead)", sets:"3 sets × 10 reps each side", rest:"30 sec", muscles:"Transverse abdominis, deep core", form:"Lie on back, arms up, knees at 90°. Lower opposite arm+leg slowly, exhale. Lower back stays PRESSED to floor.", tip:"If your back lifts off the floor, you've gone too far.", progress:"Add a 5 lb dumbbell in extended hand.", intensity:45, beginner:true },
      { name:"Plank Hold", sub:"Full core stability", weight:"Bodyweight", sets:"3 sets × 45–60 sec", rest:"30 sec", muscles:"Full core, shoulders, glutes", form:"Forearms or hands. Body in one straight line. Squeeze glutes and abs simultaneously. Breathe.", tip:"Focus on squeezing your belly button toward your spine.", progress:"Progress to 75 sec or add shoulder taps.", intensity:50, beginner:true },
      { name:"Bicycle Crunch", sub:"Waist definition", weight:"Bodyweight", sets:"3 sets × 20 reps each side", rest:"30 sec", muscles:"Obliques, rectus abdominis", form:"Hands lightly behind head. Twist elbow toward opposite knee SLOWLY. Full rotation, not just a nod.", tip:"Slow down by 50% — fast bicycles are almost useless.", progress:"Add a 2 lb ankle weight.", intensity:50, beginner:true },
      { name:"Hanging Knee Raise", sub:"Lower abs + hip flexors", weight:"Bodyweight", sets:"3 sets × 15 reps", rest:"45 sec", muscles:"Lower abs, hip flexors", form:"Hang from bar. Bring knees up to 90° or higher. Don't swing. Lower slowly.", tip:"The hardest part is not swinging — pause at the bottom each time.", progress:"Straighten legs to full leg raise.", intensity:60, beginner:false },
      { name:"Russian Twist", sub:"Oblique definition", weight:"10–15 lb plate or dumbbell", sets:"3 sets × 20 reps (10 each side)", rest:"30 sec", muscles:"Obliques, core rotation", form:"Lean back 45°, feet slightly elevated. Rotate the weight side to side. Keep abs braced.", tip:"The key is rotation from your waist, not just your arms.", progress:"15–20 lb weight.", intensity:55, beginner:true },
      { name:"Cable Crunch", sub:"Adds definition, not bulk", weight:"30–40 lbs", sets:"3 sets × 20 reps", rest:"45 sec", muscles:"Rectus abdominis", form:"Kneel at cable, rope above head. Crunch elbows toward knees. Round your spine.", tip:"Don't use your hips to pull down — all abs.", progress:"Add 5 lbs.", intensity:60, beginner:false },
      { name:"Side Plank with Hip Dip", sub:"Oblique shaping", weight:"Bodyweight", sets:"3 sets × 12 dips each side", rest:"30 sec", muscles:"Obliques, glute med", form:"Side plank on forearm. Lower hip toward floor, then raise past starting point. Slow.", tip:"Stack feet or stagger them for an easier variation.", progress:"Add a light dumbbell on hip.", intensity:55, beginner:true },
    ]
  },
  cardio: {
    title: "Cardio & Fat Loss", subtitle: "Zone 2 and LISS cardio — the best approach for fat loss without losing muscle. These burn fat while protecting your lean physique.",
    exercises: [
      { name:"12·3·30 Treadmill", sub:"The signature protocol", weight:"Incline 12%, Speed 3.0 mph", sets:"30 minutes continuous", rest:"N/A", muscles:"Glutes, hamstrings, cardio system", form:"Hold rails only lightly for balance. Let arms swing naturally. Lean into the incline.", tip:"Don't hold the rails — it cuts your calorie burn by up to 30%.", progress:"Once 30 min is easy, try 35 min or add 1 min per week.", intensity:70, beginner:true },
      { name:"StairMaster", sub:"Cardio + glute activation", weight:"Level 6–8 out of 20", sets:"30–45 minutes", rest:"N/A", muscles:"Glutes, quads, cardio", form:"Stand tall, don't lean on the sides. Full step down each time.", tip:"For more glute activation, push through the heel and skip steps at a slower pace.", progress:"Increase level by 1 every 2 weeks.", intensity:75, beginner:true },
      { name:"Rowing Machine", sub:"Full body fat burn", weight:"Damper setting 4–5", sets:"20–30 minutes or 5×500m intervals", rest:"90 sec between intervals", muscles:"Back, legs, arms, core, cardio", form:"Drive with legs first (60%), then lean back (20%), then arms (20%). Don't hunch forward.", tip:"Most people use too much arms — it's 60% legs.", progress:"Decrease 500m split time by 5 sec.", intensity:80, beginner:false },
      { name:"Incline Walk — Outdoor / Track", sub:"Active recovery cardio", weight:"Bodyweight", sets:"45–60 min walk", rest:"N/A", muscles:"Glutes, overall fat burn", form:"Brisk pace, arms swinging. Find hills naturally.", tip:"Great on rest days — burns fat without stressing muscles.", progress:"Increase pace or find steeper hills.", intensity:45, beginner:true },
      { name:"Jump Rope Intervals", sub:"HIIT — maximize fat burn", weight:"Bodyweight", sets:"10 × 30 sec on / 30 sec off", rest:"30 sec", muscles:"Full body, cardio", form:"Stay on balls of feet, light jumps, slight knee bend. Elbows in.", tip:"Even a basic jump (no tricks) is incredibly effective.", progress:"Increase to 20 intervals.", intensity:85, beginner:false },
    ]
  },
  fullbody: {
    title: "Full Body Tone", subtitle: "Compound movements that burn fat and hit multiple muscle groups — efficient and effective for a lean physique.",
    exercises: [
      { name:"Goblet Squat — Kettlebell", sub:"Tones legs without quad bulk", weight:"25–30 lb kettlebell", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Glutes, quads, core", form:"Hold KB at chest. Sit back and down, elbows inside knees at bottom. Drive up through heels.", tip:"The goblet position naturally keeps your torso upright — better than barbell squats for aesthetics.", progress:"35 lb KB.", intensity:65, beginner:true },
      { name:"Dumbbell Reverse Lunge", sub:"Glute + quad tone, no bulk", weight:"15–20 lb dumbbells", sets:"3 sets × 12 reps each leg", rest:"60 sec", muscles:"Glutes, hamstrings, quads", form:"Step back, drop rear knee toward floor. Front shin stays vertical. Push through front heel to return.", tip:"Reverse lunges are easier on knees than forward lunges and hit glutes more.", progress:"20–25 lb dumbbells.", intensity:65, beginner:true },
      { name:"Dumbbell Chest Press — Bench", sub:"Chest tone without bulk", weight:"15–20 lb dumbbells", sets:"3 sets × 15 reps", rest:"60 sec", muscles:"Chest, triceps, front delt", form:"Lie on bench. Lower dumbbells to chest level (elbows at 45°). Press up, don't lock out.", tip:"Don't flare elbows at 90° — keep them at 45° to protect shoulders.", progress:"22.5 lb dumbbells.", intensity:60, beginner:true },
      { name:"Kettlebell Swing", sub:"Posterior chain + cardio", weight:"20–25 lb kettlebell", sets:"4 sets × 20 reps", rest:"60 sec", muscles:"Glutes, hamstrings, core, cardio", form:"Hip hinge, not squat. Hike KB between legs. Explode hips forward. Bell swings to shoulder height by momentum.", tip:"The power comes from your HIPS snapping forward — not your arms pulling.", progress:"30 lb KB.", intensity:80, beginner:false },
      { name:"Dumbbell Deadlift", sub:"Full posterior chain", weight:"30–35 lb dumbbells", sets:"3 sets × 12 reps", rest:"75 sec", muscles:"Glutes, hamstrings, lower back, traps", form:"Hinge at hips, push them back. Keep spine neutral. Drive hips forward to stand.", tip:"Think 'push the floor away' not 'pull the weight up'.", progress:"40 lb dumbbells.", intensity:70, beginner:true },
      { name:"Farmer's Carry", sub:"Core stability + total tone", weight:"25 lb dumbbells each hand", sets:"4 × 40 meter walks", rest:"60 sec", muscles:"Core, traps, forearms, full body", form:"Stand tall, shoulders back, brace core. Walk at a controlled pace.", tip:"One of the best total-body exercises that also improves posture.", progress:"30 lb dumbbells.", intensity:60, beginner:true },
    ]
  }
};

// Formatted for AI prompt injection
function buildGuidePrompt(focusKey) {
  const sections = focusKey === 'surprise' ? Object.values(GUIDE) : [GUIDE[focusKey] || GUIDE['glutes']];
  let txt = '';
  sections.forEach(sec => {
    txt += `\n\n=== ${sec.title} ===\n`;
    sec.exercises.forEach(ex => {
      txt += `• ${ex.name} — ${ex.weight} | ${ex.sets} | Rest: ${ex.rest} | Form: ${ex.form} | Tip: ${ex.tip}\n`;
    });
  });
  return txt;
}

// ════════════════════════════════════════
// STORAGE
// ════════════════════════════════════════
const STORAGE_KEY = 'sf-archive-v2';
async function loadArchive(){ try{ const r=await window.storage.get(STORAGE_KEY); return r?JSON.parse(r.value):[]; }catch(e){return[];} }
async function saveArchive(e){ try{ await window.storage.set(STORAGE_KEY,JSON.stringify(e)); }catch(e){console.error(e);} }
async function addEntry(entry){ const a=await loadArchive(); a.unshift(entry); await saveArchive(a); updateArchiveBadge(a.length); }
async function deleteEntry(id){ let a=await loadArchive(); a=a.filter(e=>e.id!==id); await saveArchive(a); updateArchiveBadge(a.length); renderArchive(); }
function updateArchiveBadge(n){ const b=document.getElementById('archiveTabBtn'); const ex=b.querySelector('.tab-count'); if(ex)ex.remove(); if(n>0){const s=document.createElement('span');s.className='tab-count';s.textContent=n;b.appendChild(s);} }

// ════════════════════════════════════════
// STATE
// ════════════════════════════════════════
const ts={ yesterday:null, focus:null, feel:null, time:null };
const TODAY_IDX=(new Date().getDay()+6)%7;
const wLabels={ '12330':'12·3·30','heated_pilates':'Heated Pilates','lagree':'Lagree','glutes_gym':'Glute Day','upper_gym':'Upper Body','abs_core':'Abs & Core','stairmaster':'Stairmaster','rowing':'Rowing','golf_18':'Golf 18 Holes','golf_range':'Driving Range','full_body_gym':'Full Body Gym','rest':'Rest Day' };
const feelLabels={ fresh:'Fresh & energized ✨',good:'Pretty good 💚',tired:'A little tired 😴',sore:'Sore / achy 🩹',low:'Low energy 🌫️' };
const bMap={ glutes:'badge-glutes',upper:'badge-upper',cardio:'badge-cardio',core:'badge-core',full:'badge-full',studio:'badge-studio',golf:'badge-golf',rest:'badge-rest' };
const tLabel={ glutes:'🍑 Glutes',upper:'💪 Upper',cardio:'🏃‍♀️ Cardio',core:'🌀 Core',full:'🏋️ Full Body',studio:'🔥 Studio',golf:'⛳ Golf',rest:'😌 Rest' };
const focusToGuideKey={ glutes_gym:'glutes',upper_gym:'upper',abs_core:'core',full_body_gym:'fullbody','12330':'cardio',stairmaster:'cardio',heated_pilates:'fullbody',lagree:'fullbody',surprise:'surprise' };

const SYS=`You are an expert fitness coach for a 29-year-old Asian female, 5'5", 122 lbs. Goals: lose body fat, slender toned model-build, grow glutes WITHOUT bulky thighs. Equipment: dumbbells, kettlebells, smith machine, leg press, rowing machine, StairMaster, cables, barbell. IMPORTANT: You must use the EXACT exercises, weights, sets, and reps from the provided exercise guide below. Do not invent new weights or rep schemes — use the guide prescriptions precisely. Adjust only if energy level is low (reduce weight 10%) or the person is sore (skip that muscle group).`;

// ════════════════════════════════════════
// TABS
// ════════════════════════════════════════
function switchTab(name,btn){
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
  btn.classList.add('active');
  document.getElementById('tab-'+name).classList.add('active');
  if(name==='archive') renderArchive();
  if(name==='guide') renderGuide('glutes');
}

// ════════════════════════════════════════
// SELECTORS
// ════════════════════════════════════════
function sel(el){ document.querySelectorAll('.yesterday-section .workout-chip').forEach(c=>c.classList.remove('selected')); document.getElementById('restBtn').classList.remove('selected'); el.classList.add('selected'); ts.yesterday=el.dataset.value; }
function selRest(){ document.querySelectorAll('.yesterday-section .workout-chip').forEach(c=>c.classList.remove('selected')); const b=document.getElementById('restBtn'); b.classList.toggle('selected'); ts.yesterday=b.classList.contains('selected')?'rest':null; }
function selFocus(el){ 
  // Focus grid is second .workout-grid
  document.querySelectorAll('#tab-today .workout-grid:nth-child(2) .workout-chip, #tab-today .workout-grid + .workout-grid .workout-chip').forEach(c=>c.classList.remove('selected'));
  // Just deselect all chips in the focus section
  el.closest('.workout-grid').querySelectorAll('.workout-chip').forEach(c=>c.classList.remove('selected'));
  el.classList.add('selected'); ts.focus=el.dataset.value; 
}
function selFeel(el){ document.querySelectorAll('.feel-pill').forEach(c=>c.classList.remove('selected')); el.classList.add('selected'); ts.feel=el.dataset.value; }
function selTime(el){ document.querySelectorAll('.time-pill').forEach(c=>c.classList.remove('selected')); el.classList.add('selected'); ts.time=el.dataset.value; }

// ════════════════════════════════════════
// GENERATE TODAY
// ════════════════════════════════════════
async function generateWorkout(){
  const note=document.getElementById('focusNote').value.trim();
  if(!ts.yesterday){showErr("Select what you did yesterday.");return;}
  if(!ts.focus){showErr("What do you want to focus on today?");return;}
  if(!ts.feel){showErr("How are you feeling today?");return;}
  if(!ts.time){showErr("How much time do you have?");return;}

  const out=document.getElementById('outputSection');
  out.innerHTML=`<div class="loading-state"><div class="loading-dots"><span></span><span></span><span></span></div><div class="loading-text">Building from your guide…</div><div class="loading-sub">Pulling exact weights & reps for you</div></div>`;
  document.getElementById('generateBtn').disabled=true;

  const guideKey=focusToGuideKey[ts.focus]||'glutes';
  const guideText=buildGuidePrompt(guideKey);

  const prompt=`EXERCISE GUIDE TO USE:${guideText}

---
Yesterday: ${wLabels[ts.yesterday]||ts.yesterday}
Today's focus: ${ts.focus}
Feeling: ${ts.feel}
Time: ${ts.time} min
${note?'Note: '+note:''}

Create today's workout using ONLY exercises from the guide above with their EXACT weights, sets, and reps. 

Output as an HTML table with this exact structure:
<div class="coach-box">[One sentence why this workout makes sense after yesterday, and any adjustments for energy level]</div>
<table class="ex-result-table">
<thead><tr><th>Exercise</th><th>Weight</th><th>Sets</th><th>Reps</th></tr></thead>
<tbody>
[For each section, add a row: <tr class="section-header-row"><td colspan="4"><div class="ex-nm">[Section Name]</div></td></tr>]
[For each exercise: <tr><td><div class="ex-nm">[Name]</div><div class="ex-fm">[Key form cue]</div></td><td class="ex-wt">[weight]</td><td class="ex-sets-td">[sets]</td><td>[reps or duration]</td></tr>]
</tbody>
</table>
<p style="font-size:12px;color:var(--text-light);margin-top:16px;font-style:italic">[Brief closing note — total time estimate, what to focus on]</p>

Select 4–7 exercises appropriate for the time available. If feeling tired or sore, reduce weight by 10% and note it.`;

  try{
    const r=await fetch('https://api.anthropic.com/v1/messages',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:1200,system:SYS,messages:[{role:'user',content:prompt}]})});
    const d=await r.json();
    const txt=d.content?.map(b=>b.text||'').join('')||'';
    const focusLabel={glutes_gym:'Glute Day',upper_gym:'Upper Body',abs_core:'Abs & Core',full_body_gym:'Full Body',stairmaster:'Stairmaster + Glutes','12330':'12·3·30 Cardio',heated_pilates:'Heated Pilates',lagree:'Lagree',surprise:'Custom Mix'}[ts.focus]||'Workout';

    window._pendingWorkout={ html:txt, yesterday:ts.yesterday, feel:ts.feel, time:ts.time, note:note, workoutName:focusLabel, type:guideKey };

    out.innerHTML=`
      <div class="result-card">
        <div class="result-header">
          <div class="workout-meta">Today · ${ts.time} min · From your guide</div>
          <div class="workout-title">${focusLabel}</div>
          <div class="workout-tagline">After ${wLabels[ts.yesterday]||ts.yesterday} · Feeling ${feelLabels[ts.feel]||ts.feel}</div>
        </div>
        <div class="result-body">${txt}</div>
        <div class="result-actions">
          <button class="action-btn secondary" onclick="generateWorkout()">↻ Regenerate</button>
          <button class="action-btn primary" id="doneBtn" onclick="logWorkout()">✓ Log This Workout</button>
        </div>
      </div>`;
  }catch(e){ showErr('Something went wrong. Try again.'); console.error(e); }
  document.getElementById('generateBtn').disabled=false;
}

async function logWorkout(){
  const btn=document.getElementById('doneBtn');
  if(!window._pendingWorkout)return;
  btn.textContent='Saving…';btn.disabled=true;
  const now=new Date();
  await addEntry({ id:Date.now().toString(), date:now.toISOString(), workoutName:window._pendingWorkout.workoutName, type:window._pendingWorkout.type||'full', yesterday:window._pendingWorkout.yesterday, feel:window._pendingWorkout.feel, time:window._pendingWorkout.time, note:window._pendingWorkout.note, html:window._pendingWorkout.html });
  btn.textContent='✓ Logged!';btn.style.background='var(--sage)';window._pendingWorkout=null;
}

function showErr(msg){ const o=document.getElementById('outputSection'); o.innerHTML=`<div class="error-msg">${msg}</div>`; setTimeout(()=>{if(o.querySelector('.error-msg'))o.innerHTML='';},3000); }

// ════════════════════════════════════════
// GUIDE TAB
// ════════════════════════════════════════
let currentGuide='glutes';
function switchGuide(key,btn){
  document.querySelectorAll('.guide-nav-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  currentGuide=key;
  renderGuide(key);
}

function renderGuide(key){
  const gc=document.getElementById('guideContent');
  const sec=GUIDE[key];
  if(!sec){gc.innerHTML='';return;}
  let html=`<div class="guide-section-title">${sec.title}</div><div class="guide-section-sub">${sec.subtitle}</div>`;
  sec.exercises.forEach((ex,i)=>{
    const id=`gex-${key}-${i}`;
    html+=`
    <div class="guide-card" id="${id}">
      <div class="guide-card-header" onclick="toggleGuide('${id}')">
        <div class="guide-card-left">
          <div class="guide-ex-name">${ex.name}</div>
          <div class="guide-ex-sub">${ex.sub}</div>
        </div>
        <div class="guide-card-right">
          <span class="guide-weight-badge">${ex.weight}</span>
          <span class="guide-sets-badge">${ex.sets.split('×')[0].trim()}</span>
          <span class="guide-toggle">▾</span>
        </div>
      </div>
      <div class="guide-detail">
        <div class="guide-detail-inner">
          <div class="guide-detail-block">
            <label>Prescription</label>
            <p><strong>${ex.sets}</strong><br>Rest: ${ex.rest}</p>
          </div>
          <div class="guide-detail-block">
            <label>Weight</label>
            <p><strong>${ex.weight}</strong></p>
          </div>
          <div class="guide-detail-block">
            <label>Muscles</label>
            <p>${ex.muscles}</p>
          </div>
          <div class="guide-detail-block">
            <label>Progression</label>
            <p>${ex.progress}</p>
          </div>
          <div class="guide-detail-block single" style="grid-column:1/-1">
            <label>Form</label>
            <p>${ex.form}</p>
          </div>
          <div class="guide-tip-box">💡 ${ex.tip}</div>
          <div class="guide-detail-block single" style="grid-column:1/-1">
            <label>Intensity</label>
            <div class="guide-prog">
              <div class="prog-row"><div class="prog-bar-bg"><div class="prog-bar" style="width:${ex.intensity}%"></div></div><span style="font-size:11px;color:var(--text-light)">${ex.intensity}%</span></div>
            </div>
          </div>
        </div>
      </div>
    </div>`;
  });
  gc.innerHTML=html;
}

function toggleGuide(id){ document.getElementById(id).classList.toggle('expanded'); }

// ════════════════════════════════════════
// WEEKLY
// ════════════════════════════════════════
async function generateWeek(){
  const wc=document.getElementById('weekContent');
  wc.innerHTML=`<div class="loading-state" style="padding:56px 20px"><div class="loading-dots"><span></span><span></span><span></span></div><div class="loading-text">Building your week from the guide…</div><div class="loading-sub">With specific weights & reps for every exercise</div></div>`;

  // Build full guide text for the prompt
  let fullGuide='';
  Object.values(GUIDE).forEach(sec=>{ fullGuide+=`\n${sec.title}:\n`; sec.exercises.forEach(ex=>{ fullGuide+=`• ${ex.name}: ${ex.weight}, ${ex.sets}, Rest ${ex.rest}\n`; }); });

  const prompt=`Using ONLY the exercises from this guide:${fullGuide}

Return a valid JSON array of 7 objects (Monday–Sunday). Raw JSON only, no markdown.

Each object:
- "day": day name
- "workoutName": e.g. "Glute Focus", "Upper Body Tone", "12·3·30 + Core", "Rest & Recover"
- "type": glutes|upper|cardio|core|full|studio|rest
- "duration": minutes (0 for rest)
- "note": one coach tip for the day
- "exercises": array (empty for rest) with: {"name","weight","sets","reps","tip"}

Rules: 2 rest days (Wed + Sun). Tue = Glute day. One cardio day (12-3-30 or StairMaster). One upper day. One core or full body day. One studio-style day (lower intensity). Use EXACT weights from guide. 5–7 exercises per active day.`;

  try{
    const r=await fetch('https://api.anthropic.com/v1/messages',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:2000,system:SYS,messages:[{role:'user',content:prompt}]})});
    const d=await r.json();
    let raw=d.content?.map(b=>b.text||'').join('')||'[]';
    raw=raw.replace(/```json|```/g,'').trim();
    renderWeek(JSON.parse(raw));
  }catch(e){
    wc.innerHTML=`<div class="error-msg" style="margin-bottom:20px">Couldn't generate. Please try again.</div><div style="text-align:center"><button class="week-gen-big-btn" onclick="generateWeek()">Try Again</button></div>`;
    console.error(e);
  }
}

function renderWeek(days){
  const wc=document.getElementById('weekContent');
  const active=days.filter(d=>d.type!=='rest').length;
  const totalMin=days.reduce((s,d)=>s+(d.duration||0),0);

  let html=`<div class="week-header-row"><div class="week-label">This <span>Week</span></div><button class="regen-small" onclick="generateWeek()">↻ New Plan</button></div>
  <div class="week-summary">
    <div class="summary-chip"><strong>${active}</strong> active days</div>
    <div class="summary-chip"><strong>${7-active}</strong> rest days</div>
    <div class="summary-chip"><strong>${totalMin} min</strong> total</div>
    <div class="summary-chip">From: <strong>Your Guide</strong></div>
  </div><div class="week-grid">`;

  days.forEach((day,i)=>{
    const isToday=i===TODAY_IDX, isRest=day.type==='rest';
    const rowCls=[isToday?'today-row':'',isRest?'rest-row':''].filter(Boolean).join(' ');
    let tableRows='';
    (day.exercises||[]).forEach(ex=>{
      tableRows+=`<tr><td><div class="ex-name">${ex.name}</div><div class="ex-tip">${ex.tip||''}</div></td><td style="text-align:center;color:var(--terracotta);font-size:12px;font-weight:500;padding-left:8px;white-space:nowrap">${ex.weight||''}</td><td class="ex-sets" style="padding-left:8px">${ex.sets}×${ex.reps||''}</td></tr>`;
    });
    const detail=isRest
      ?`<div class="rest-detail">${day.note||'Rest, stretch, or take a gentle walk.'}</div>`
      :`<table class="exercise-table"><thead><tr><th>Exercise</th><th class="center">Weight</th><th class="center">Sets×Reps</th></tr></thead><tbody>${tableRows}</tbody></table>${day.note?`<div class="day-note">${day.note}</div>`:''}`;

    html+=`<div class="day-row ${rowCls}" id="dr-${i}">
      <div class="day-header" onclick="toggleDay(${i})">
        <div class="day-left">
          <div><div class="day-name">${day.day}</div><div class="day-workout-name${isRest?' rest-label':''}">${day.workoutName}</div></div>
          <div style="display:flex;gap:6px">${isToday?`<span class="day-badge badge-today">Today</span>`:''}<span class="day-badge ${bMap[day.type]||'badge-rest'}">${tLabel[day.type]||day.type}</span></div>
        </div>
        <div class="day-right">${!isRest?`<span class="day-dur">${day.duration} min</span>`:''}<span class="day-toggle">▾</span></div>
      </div>
      <div class="day-detail"><div class="day-detail-inner">${detail}</div></div>
    </div>`;
  });
  html+=`</div>`;
  wc.innerHTML=html;
  if(TODAY_IDX>=0&&TODAY_IDX<7) setTimeout(()=>toggleDay(TODAY_IDX),180);
}

function toggleDay(i){ document.getElementById('dr-'+i).classList.toggle('expanded'); }

// ════════════════════════════════════════
// ARCHIVE
// ════════════════════════════════════════
let archiveFilter='all';
async function renderArchive(){
  const ac=document.getElementById('archiveContent');
  ac.innerHTML=`<div class="loading-state"><div class="loading-dots"><span></span><span></span><span></span></div><div class="loading-text">Loading your history…</div></div>`;
  const entries=await loadArchive();
  if(entries.length===0){ ac.innerHTML=`<div class="archive-empty"><div class="archive-empty-icon">📓</div><div class="archive-empty-title">Your <em>History</em> Lives Here</div><div class="archive-empty-sub">Once you log a workout from the Today tab, it'll appear here with the full plan, weights, and notes.</div></div>`; return; }
  updateArchiveBadge(entries.length);
  const totalMin=entries.reduce((s,e)=>s+(parseInt(e.time)||0),0);
  const thisWeek=entries.filter(e=>(new Date()-new Date(e.date))<7*86400000).length;
  const streak=calcStreak(entries);
  const typeCounts={};entries.forEach(e=>{typeCounts[e.type]=(typeCounts[e.type]||0)+1;});
  const topType=Object.entries(typeCounts).sort((a,b)=>b[1]-a[1])[0];
  const filtered=archiveFilter==='all'?entries:entries.filter(e=>e.type===archiveFilter);
  const groups={};
  filtered.forEach(e=>{ const d=new Date(e.date); const k=d.toLocaleDateString('en-US',{month:'long',year:'numeric'}); if(!groups[k])groups[k]=[]; groups[k].push(e); });

  let html='';
  if(streak>1) html+=`<div class="streak-banner"><div class="streak-fire">🔥</div><div class="streak-text"><div class="streak-count">${streak}-day streak</div><div class="streak-sub">Keep the momentum going</div></div></div>`;
  html+=`<div class="archive-header-row"><div class="archive-title">Your <span>Archive</span></div></div>
  <div class="archive-stats">
    <div class="archive-stat"><strong>${entries.length}</strong> workouts</div>
    <div class="archive-stat"><strong>${thisWeek}</strong> this week</div>
    <div class="archive-stat"><strong>${Math.floor(totalMin/60)}h ${totalMin%60}m</strong> total</div>
    ${topType?`<div class="archive-stat">Top: <strong>${tLabel[topType[0]]||topType[0]}</strong></div>`:''}
  </div>
  <div class="archive-filter-row">${['all','glutes','upper','cardio','core','full','studio'].map(f=>`<div class="filter-chip${archiveFilter===f?' active':''}" onclick="setFilter('${f}')">${f==='all'?'All':tLabel[f]||f}</div>`).join('')}</div>`;

  if(!filtered.length){ html+=`<div style="text-align:center;padding:40px;color:var(--text-light);font-size:13px;font-style:italic">No ${archiveFilter} workouts logged yet.</div>`; }
  else{
    Object.entries(groups).forEach(([month,me])=>{
      html+=`<div class="month-group"><div class="month-heading">${month} · ${me.length} workout${me.length!==1?'s':''}</div>`;
      me.forEach(entry=>{
        const d=new Date(entry.date);
        html+=`<div class="archive-entry" id="ae-${entry.id}">
          <div class="entry-header" onclick="toggleEntry('${entry.id}')">
            <div class="entry-left">
              <div class="entry-date-block"><div class="entry-day-num">${d.getDate()}</div><div class="entry-day-name">${d.toLocaleDateString('en-US',{weekday:'short'}).toUpperCase()}</div></div>
              <div><div class="entry-workout-name">${entry.workoutName}</div><div class="entry-meta">${d.toLocaleTimeString('en-US',{hour:'numeric',minute:'2-digit'})}${entry.time?' · '+entry.time+' min':''}${entry.yesterday?' · After '+(wLabels[entry.yesterday]||entry.yesterday):''}</div></div>
            </div>
            <div class="entry-right"><span class="entry-badge ${bMap[entry.type]||'badge-full'}">${tLabel[entry.type]||entry.type}</span><span class="entry-toggle">▾</span></div>
          </div>
          <div class="entry-detail" id="aed-${entry.id}">
            <div class="entry-detail-inner">
              ${entry.feel?`<div class="entry-feel-tag">${feelLabels[entry.feel]||entry.feel}</div>`:''}
              <div class="entry-workout-html">${entry.html}</div>
              ${entry.note?`<div class="entry-note-row">📝 ${entry.note}</div>`:''}
              <div class="entry-actions"><button class="entry-del-btn" onclick="confirmDelete('${entry.id}')">🗑 Remove</button></div>
            </div>
          </div>
        </div>`;
      });
      html+=`</div>`;
    });
  }
  ac.innerHTML=html;
}

function toggleEntry(id){ document.getElementById('ae-'+id).classList.toggle('expanded'); }
function setFilter(f){ archiveFilter=f; renderArchive(); }
function confirmDelete(id){ if(confirm('Remove this workout?')) deleteEntry(id); }
function calcStreak(entries){
  const today=new Date(); today.setHours(0,0,0,0);
  let streak=0,check=new Date(today);
  const dates=new Set(entries.map(e=>{const d=new Date(e.date);d.setHours(0,0,0,0);return d.toDateString();}));
  while(dates.has(check.toDateString())){streak++;check.setDate(check.getDate()-1);}
  return streak;
}

// INIT
(async()=>{ const e=await loadArchive(); updateArchiveBadge(e.length); renderGuide('glutes'); })();
</script>
</body>
</html>
