# maddielegden
Maddie RLS
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="theme-color" content="#15131f">
<title>Maddie's Leg Den</title>
<style>
  :root{
    --night:#15131f; --night2:#1d1b2b; --card:#252338; --card2:#2e2b44;
    --moss:#8fd6a0; --moss-deep:#5fae77; --moth:#e8c98a;
    --glow:#c4a9f0; --glow-deep:#9b7fd4; --ink:#f1eefb;
    --ink-soft:#b8b2cf; --ink-faint:#7d7898; --warn:#f0a07a;
    --line:rgba(196,169,240,0.14);
  }
  *{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
  html,body{background:var(--night);}
  body{
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
    color:var(--ink);min-height:100vh;overflow-x:hidden;
    padding-bottom:env(safe-area-inset-bottom);
    background:
      radial-gradient(900px 500px at 80% -5%, rgba(155,127,212,0.20), transparent 60%),
      radial-gradient(700px 500px at 10% 10%, rgba(143,214,160,0.10), transparent 55%),
      var(--night);
  }
  .sky{position:fixed;inset:0;pointer-events:none;z-index:0;overflow:hidden;}
  .firefly{position:absolute;width:5px;height:5px;border-radius:50%;
    background:var(--moth);box-shadow:0 0 8px 2px rgba(232,201,138,0.7);
    opacity:0;animation:float linear infinite;}
  @keyframes float{0%{opacity:0;transform:translateY(0) translateX(0);}
    15%{opacity:.8;}85%{opacity:.8;}
    100%{opacity:0;transform:translateY(-120px) translateX(30px);}}
  .wrap{position:relative;z-index:1;max-width:600px;margin:0 auto;padding:0 18px;}

  header{padding:calc(env(safe-area-inset-top) + 24px) 0 6px;text-align:center;}
  .crest{font-size:38px;line-height:1;filter:drop-shadow(0 0 12px rgba(196,169,240,.4));}
  h1{font-size:24px;font-weight:700;letter-spacing:-.3px;margin-top:6px;}
  .sub{color:var(--ink-soft);font-size:13px;margin-top:4px;line-height:1.45;}

  nav{position:sticky;top:0;z-index:20;display:flex;gap:7px;overflow-x:auto;
    padding:12px 18px 12px;margin:6px -18px 0;
    background:linear-gradient(var(--night) 70%, transparent);scrollbar-width:none;
    -webkit-overflow-scrolling:touch;}
  nav::-webkit-scrollbar{display:none;}
  .tab{flex:0 0 auto;border:1px solid var(--line);background:var(--card);
    color:var(--ink-soft);font-size:13px;font-weight:600;
    padding:9px 14px;border-radius:15px;white-space:nowrap;
    transition:transform .15s ease, background .2s, color .2s;}
  .tab:active{transform:scale(.94);}
  .tab.on{background:linear-gradient(135deg,var(--glow-deep),var(--moss-deep));
    color:#fff;border-color:transparent;box-shadow:0 4px 16px rgba(155,127,212,.35);}

  section{display:none;animation:rise .35s ease;padding-bottom:40px;}
  section.on{display:block;}
  @keyframes rise{from{opacity:0;transform:translateY(8px);}to{opacity:1;transform:none;}}

  .card{background:var(--card);border:1px solid var(--line);border-radius:20px;
    padding:16px;margin-top:12px;box-shadow:0 2px 12px rgba(0,0,0,.15);}
  .card h2{font-size:16px;display:flex;align-items:center;gap:8px;}
  .card h2 .ic{font-size:19px;}
  .card p{color:var(--ink-soft);font-size:14px;line-height:1.5;margin-top:6px;}
  .lead{color:var(--ink-soft);font-size:14px;line-height:1.55;margin:10px 2px 0;}

  ul.dots{list-style:none;margin-top:8px;}
  ul.dots li{position:relative;padding:6px 0 6px 22px;font-size:14px;
    color:var(--ink-soft);line-height:1.5;}
  ul.dots li::before{content:"";position:absolute;left:4px;top:13px;
    width:7px;height:7px;border-radius:50%;background:var(--moss);}
  ul.dots li b{color:var(--ink);font-weight:600;}

  .pill{display:inline-block;font-size:11px;font-weight:700;letter-spacing:.4px;
    text-transform:uppercase;padding:4px 9px;border-radius:999px;margin-bottom:4px;}
  .pill.now{background:rgba(240,160,122,.16);color:var(--warn);}
  .pill.day{background:rgba(232,201,138,.16);color:var(--moth);}
  .pill.night{background:rgba(196,169,240,.16);color:var(--glow);}

  .sosbtn{width:100%;border:none;border-radius:22px;padding:18px;margin-top:14px;
    background:linear-gradient(135deg,#b06a4a,#7d4a8c);color:#fff;
    font-size:17px;font-weight:700;box-shadow:0 8px 26px rgba(176,106,74,.4);
    display:flex;align-items:center;justify-content:center;gap:10px;}
  .sosbtn:active{transform:scale(.98);}

  .step{background:var(--card2);border-radius:16px;padding:14px;margin-top:10px;
    border:1px solid var(--line);}
  .step .num{display:inline-flex;align-items:center;justify-content:center;
    width:26px;height:26px;border-radius:50%;background:var(--glow-deep);
    color:#fff;font-size:13px;font-weight:700;margin-right:8px;}
  .step h3{font-size:15px;display:inline;}
  .step p{margin-top:8px;}

  .warnbox{background:rgba(240,160,122,.10);border:1px solid rgba(240,160,122,.3);
    border-radius:16px;padding:14px;margin-top:12px;}
  .warnbox h2{color:var(--warn);}
  .warnbox p,.warnbox li{color:#e9cdbf;}
  .warnbox ul.dots li::before{background:var(--warn);}

  .tag{display:inline-block;background:var(--card2);border:1px solid var(--line);
    color:var(--moss);font-size:12px;font-weight:600;padding:3px 9px;
    border-radius:999px;margin:3px 4px 0 0;}

  details{background:var(--card2);border:1px solid var(--line);border-radius:14px;
    margin-top:9px;overflow:hidden;}
  summary{list-style:none;padding:13px 14px;font-size:14px;font-weight:600;
    cursor:pointer;display:flex;align-items:center;gap:8px;}
  summary::-webkit-details-marker{display:none;}
  summary .ar{margin-left:auto;color:var(--ink-faint);transition:.2s;}
  details[open] summary .ar{transform:rotate(180deg);}
  details .body{padding:0 14px 14px;}
  details .body p{color:var(--ink-soft);font-size:13.5px;line-height:1.5;}

  .foot{text-align:center;color:var(--ink-faint);font-size:11.5px;
    line-height:1.5;padding:20px 10px 30px;}
  .foot b{color:var(--ink-soft);}

  /* ---------- LOG / CHECK-IN ---------- */
  .qmark{font-size:14px;font-weight:600;margin:16px 2px 2px;}
  .qmark .opt{color:var(--ink-faint);font-weight:500;font-size:12.5px;}

  .scale{display:flex;gap:6px;margin-top:9px;}
  .scale button{flex:1;aspect-ratio:1;border:1px solid var(--line);
    background:var(--card2);color:var(--ink-soft);font-size:15px;font-weight:700;
    border-radius:13px;transition:.12s;}
  .scale button.sel{transform:scale(1.06);color:#fff;border-color:transparent;}
  .scale.sev button.sel{background:linear-gradient(135deg,#b06a4a,#c85c5c);}
  .scale.slp button.sel{background:linear-gradient(135deg,var(--glow-deep),var(--moss-deep));}
  .scaleEnds{display:flex;justify-content:space-between;color:var(--ink-faint);
    font-size:11px;margin-top:5px;padding:0 2px;}

  .chips{display:flex;flex-wrap:wrap;gap:7px;margin-top:9px;}
  .chip{border:1px solid var(--line);background:var(--card2);color:var(--ink-soft);
    font-size:13px;font-weight:600;padding:8px 12px;border-radius:13px;transition:.12s;}
  .chip.sel{background:rgba(232,201,138,.18);border-color:var(--moth);color:var(--moth);}
  .chip.help.sel{background:rgba(143,214,160,.18);border-color:var(--moss);color:var(--moss);}

  .savebtn{width:100%;border:none;border-radius:18px;padding:16px;margin-top:18px;
    background:linear-gradient(135deg,var(--moss-deep),var(--glow-deep));color:#fff;
    font-size:16px;font-weight:700;box-shadow:0 6px 20px rgba(95,174,119,.3);}
  .savebtn:active{transform:scale(.98);}
  .savebtn:disabled{opacity:.45;box-shadow:none;}

  .toast{position:fixed;left:50%;bottom:34px;transform:translateX(-50%) translateY(120px);
    background:var(--card2);border:1px solid var(--moss);color:var(--ink);
    padding:13px 18px;border-radius:16px;font-size:14px;font-weight:600;z-index:50;
    box-shadow:0 8px 30px rgba(0,0,0,.5);transition:transform .35s cubic-bezier(.2,.9,.3,1.2);
    max-width:88%;text-align:center;}
  .toast.show{transform:translateX(-50%) translateY(0);}

  /* insight / response card */
  .insight{background:linear-gradient(135deg,rgba(155,127,212,.16),rgba(143,214,160,.12));
    border:1px solid var(--line);border-radius:20px;padding:16px;margin-top:12px;}
  .insight h2{color:var(--glow);}
  .insight .big{font-size:14px;color:var(--ink);line-height:1.55;margin-top:8px;}
  .insight .big b{color:var(--moss);}

  /* progress ring + stats */
  .statrow{display:flex;gap:10px;margin-top:12px;}
  .stat{flex:1;background:var(--card2);border:1px solid var(--line);
    border-radius:16px;padding:14px 10px;text-align:center;}
  .stat .v{font-size:24px;font-weight:700;color:var(--moth);}
  .stat .l{font-size:11px;color:var(--ink-faint);margin-top:3px;line-height:1.3;}

  .bars{display:flex;align-items:flex-end;gap:5px;height:80px;margin-top:14px;}
  .bar{flex:1;background:var(--card2);border-radius:6px 6px 3px 3px;position:relative;
    min-height:4px;transition:height .4s ease;}
  .bar .bl{position:absolute;bottom:-18px;left:0;right:0;text-align:center;
    font-size:10px;color:var(--ink-faint);}
  .barwrap{margin-bottom:22px;}

  .logitem{background:var(--card2);border:1px solid var(--line);border-radius:14px;
    padding:11px 13px;margin-top:8px;display:flex;align-items:center;gap:11px;}
  .logitem .dot{flex:0 0 auto;width:38px;height:38px;border-radius:11px;
    display:flex;align-items:center;justify-content:center;font-size:15px;font-weight:700;color:#fff;}
  .logitem .d{font-size:13px;color:var(--ink-soft);}
  .logitem .d b{color:var(--ink);}
  .logitem .d small{color:var(--ink-faint);font-size:11.5px;}

  .ringwrap{display:flex;align-items:center;gap:16px;}
  .ring{flex:0 0 auto;}
  .ringtxt{font-size:13.5px;color:var(--ink-soft);line-height:1.5;}
  .ringtxt b{color:var(--moss);}

  .emptynote{text-align:center;color:var(--ink-faint);font-size:13px;
    padding:20px 10px;line-height:1.5;}

  .ghostbtn{width:100%;margin-top:10px;background:transparent;border:1px solid var(--line);
    color:var(--ink-soft);font-size:13px;font-weight:600;padding:11px;border-radius:13px;}

  .ironset{display:flex;gap:8px;margin-top:10px;align-items:center;}
  .ironset input{flex:1;background:var(--card2);border:1px solid var(--line);
    color:var(--ink);font-size:15px;padding:11px 13px;border-radius:13px;outline:none;}
  .ironset input::placeholder{color:var(--ink-faint);}
  .ironset button{background:var(--glow-deep);border:none;color:#fff;font-weight:700;
    font-size:14px;padding:11px 16px;border-radius:13px;}
  .ironresult{margin-top:10px;font-size:13.5px;line-height:1.5;}

  /* criteria checklist */
  .check{display:flex;align-items:flex-start;gap:12px;padding:13px;margin-top:9px;
    background:var(--card2);border:1px solid var(--line);border-radius:15px;
    transition:transform .12s ease;}
  .check:active{transform:scale(.98);}
  .check .box{flex:0 0 auto;width:24px;height:24px;border-radius:8px;
    border:2px solid var(--glow-deep);display:flex;align-items:center;
    justify-content:center;font-size:14px;color:#fff;transition:.15s;margin-top:1px;}
  .check.done .box{background:var(--moss-deep);border-color:var(--moss-deep);}
  .check .ct{font-size:13.5px;line-height:1.45;color:var(--ink-soft);}
  .check.done .ct{color:var(--ink);}

  /* timer */
  .timerwrap{text-align:center;padding:8px 0 2px;}
  .clock{font-size:50px;font-weight:700;font-variant-numeric:tabular-nums;
    letter-spacing:1px;color:var(--moth);text-shadow:0 0 18px rgba(232,201,138,.35);}
  .tlabel{color:var(--ink-faint);font-size:13px;margin-top:2px;}
  .trow{display:flex;gap:8px;margin-top:14px;}
  .trow button{flex:1;border:1px solid var(--line);background:var(--card2);
    color:var(--ink);font-size:14px;font-weight:600;padding:12px;border-radius:14px;}
  .trow button.go{background:linear-gradient(135deg,var(--moss-deep),var(--glow-deep));
    border-color:transparent;color:#fff;}
  .presets{display:flex;gap:8px;margin-top:10px;}
  .presets button{flex:1;background:transparent;border:1px solid var(--line);
    color:var(--ink-soft);font-size:13px;font-weight:600;padding:9px;border-radius:12px;}
  .presets button.sel{border-color:var(--moss);color:var(--moss);}
</style>
</head>
<body>
<div class="sky" id="sky"></div>
<div class="wrap">

  <header>
    <div class="crest">🦇</div>
    <h1>Maddie's Leg Den</h1>
    <div class="sub" id="greeting">A cozy burrow for taming the wriggles 🐛</div>
  </header>

  <nav id="nav">
    <button class="tab on" data-t="home">🏡 Den</button>
    <button class="tab" data-t="log">🐾 Check In</button>
    <button class="tab" data-t="sos">🚨 Right Now</button>
    <button class="tab" data-t="patterns">🔮 Patterns</button>
    <button class="tab" data-t="day">☀️ My Day</button>
    <button class="tab" data-t="night">🌙 Wind Down</button>
    <button class="tab" data-t="timer">⏱️ Timer</button>
    <button class="tab" data-t="iron">🩸 Iron</button>
    <button class="tab" data-t="avoid">⚠️ Watch Out</button>
    <button class="tab" data-t="med">💊 Med Watch</button>
    <button class="tab" data-t="why">🐝 Why?</button>
  </nav>

  <!-- ================= HOME / DEN ================= -->
  <section class="on" id="home">
    <div class="insight" id="todayCard">
      <h2><span class="ic">🦋</span> Today</h2>
      <div class="big" id="todayMsg">Loading your den…</div>
    </div>

    <div class="ringwrap card" id="ringCard" style="display:none;">
      <div class="ring">
        <svg width="78" height="78" viewBox="0 0 78 78">
          <circle cx="39" cy="39" r="32" fill="none" stroke="rgba(196,169,240,.15)" stroke-width="8"/>
          <circle id="ringFill" cx="39" cy="39" r="32" fill="none" stroke="url(#g)" stroke-width="8"
            stroke-linecap="round" stroke-dasharray="201" stroke-dashoffset="201"
            transform="rotate(-90 39 39)"/>
          <defs><linearGradient id="g" x1="0" y1="0" x2="1" y2="1">
            <stop offset="0" stop-color="#8fd6a0"/><stop offset="1" stop-color="#9b7fd4"/>
          </linearGradient></defs>
        </svg>
      </div>
      <div class="ringtxt" id="ringTxt"></div>
    </div>

    <button class="sosbtn" onclick="go('log')" style="background:linear-gradient(135deg,var(--moss-deep),var(--glow-deep));">
      🐾 Do tonight's check-in →
    </button>

    <div class="card">
      <h2><span class="ic">🌟</span> Quick help</h2>
      <p>Legs acting up right now? Jump straight to the rescue steps.</p>
      <button class="ghostbtn" onclick="go('sos')">Open Right Now →</button>
    </div>

    <div class="foot">
      Made with 🦇🐛🦋 for Maddie. Your logs stay private on your phone.<br>
      <b>Supportive info, not medical advice.</b>
    </div>
  </section>

  <!-- ================= CHECK IN / LOG ================= -->
  <section id="log">
    <p class="lead">A 60-second nightly check-in. The more you log, the better I can spot what sets your legs off — and what calms them. No wrong answers. 🐾</p>

    <div class="card">
      <div class="qmark">How bad were your legs today? <span class="opt" id="sevReadout">tap one</span></div>
      <div class="scale sev" id="sevScale"></div>
      <div class="scaleEnds"><span>😌 calm</span><span>😣 awful</span></div>

      <div class="qmark">How did you sleep? <span class="opt" id="slpReadout">tap one</span></div>
      <div class="scale slp" id="slpScale"></div>
      <div class="scaleEnds"><span>😴 rough</span><span>🌙 great</span></div>

      <div class="qmark">Any of these today? <span class="opt">tap any that apply — optional</span></div>
      <div class="chips" id="trigChips"></div>

      <div class="qmark">Anything that helped? <span class="opt">optional</span></div>
      <div class="chips" id="helpChips"></div>

      <button class="savebtn" id="saveBtn" onclick="saveLog()">Save tonight's check-in 🌙</button>
      <button class="ghostbtn" onclick="go('home')">Maybe later</button>
    </div>
  </section>

  <!-- ================= RIGHT NOW ================= -->
  <section id="sos">
    <div class="card">
      <span class="pill now">When legs won't quit</span>
      <h2><span class="ic">🌟</span> First: don't fight it in bed</h2>
      <p>If the creepy-crawly feeling kicks in, don't lie there battling it more than ~20 min. Get up. Staying in bed teaches your brain that bed = frustration. Moving is the cure, not cheating.</p>
    </div>
    <button class="sosbtn" onclick="go('timer')">⏱️ Start a rescue routine →</button>
    <div class="step"><span class="num">1</span><h3>Legs up the wall (5–10 min)</h3>
      <p>Hips near a wall, legs straight up it, lie back. Gravity drains the buzzy feeling out of your calves. Slow breaths. 🦋</p></div>
    <div class="step"><span class="num">2</span><h3>Deep calf stretch (45 sec each)</h3>
      <p>Hands on wall, one foot stepped back, heel pressed down, leg straight. Lean in until the calf pulls. Tired muscles stop firing.</p></div>
    <div class="step"><span class="num">3</span><h3>Counter-pressure</h3>
      <p>Firmly massage calves, or pull on <b>tight compression socks</b> / wrap them snug. Steady pressure drowns out the restless signal — real clinical backing here.</p></div>
    <div class="step"><span class="num">4</span><h3>Temperature trick</h3>
      <p>Warm heating pad on calves ~20 min. If that doesn't help, flip to <b>cold</b> — ice pack on the shins. The strong sensation overrides the wriggle.</p></div>
    <div class="step"><span class="num">5</span><h3>Busy your brain 🦔</h3>
      <p>RLS gets louder when your mind is idle. Audiobook, podcast, or a puzzle while you sit with heat/ice. Distraction turns the volume down.</p></div>
    <div class="step"><span class="num">6</span><h3>Cool the room, then return</h3>
      <p>Fan or A/C (aim 60–67°F). Slide into a cool bed with socks on.</p></div>
    <div class="warnbox"><h2><span class="ic">🚫</span> Don't reach for Benadryl / ZzzQuil</h2>
      <p>Sedating antihistamines block dopamine and can make RLS dramatically worse within an hour. (More in Watch Out.)</p></div>
  </section>

  <!-- ================= PATTERNS ================= -->
  <section id="patterns">
    <p class="lead">This is where your check-ins pay off. The more nights you log, the clearer your personal map gets. 🔮</p>

    <div id="patternsContent"></div>
  </section>

  <!-- ================= MY DAY ================= -->
  <section id="day">
    <p class="lead">RLS is partly set by what happens <i>before</i> bedtime. Win the day, calm the night. Pick even one. 🐛</p>
    <div class="card"><span class="pill day">Morning + afternoon</span>
      <h2><span class="ic">💧</span> Baseline care</h2>
      <ul class="dots">
        <li><b>Sip water all day.</b> Dehydration makes nerves twitchy. A pinch of salt or electrolyte tab helps it absorb.</li>
        <li><b>Move your legs.</b> A 15–20 min walk pushes blood through your calves. Gentle and regular beats intense.</li>
        <li><b>Caffeine curfew at noon.</b> Coffee, soda, energy drinks — cut off by 12 PM. It lingers longer than you'd think.</li>
      </ul></div>
    <div class="card"><h2><span class="ic">🏃‍♀️</span> One note on exercise</h2>
      <p>Daytime movement = good. <b>Hard late-night workouts can backfire</b> and trigger a flare. Keep evenings gentle.</p></div>
    <div class="card"><h2><span class="ic">🦴</span> Stretches worth doing daily</h2>
      <p>Doing these in daylight lowers your baseline, so nights are calmer.</p>
      <ul class="dots">
        <li><b>Wall calf stretch</b> — 45 sec per leg.</li>
        <li><b>Seated hamstring reach</b> — leg out, toes back, hinge forward 30–45 sec.</li>
        <li><b>Legs up the wall</b> — even 5 min resets things.</li>
      </ul></div>
  </section>

  <!-- ================= WIND DOWN ================= -->
  <section id="night">
    <p class="lead">An hour before bed, start telling your nervous system it's safe to rest. 🌙🦇</p>
    <div class="card"><span class="pill night">~1 hr before bed</span>
      <h2><span class="ic">📓</span> Brain dump</h2>
      <p>Stress dumps cortisol that spikes RLS. 5 min writing out whatever's rattling around nudges your brain out of fight-or-flight. Extra worth it for anxious brains.</p></div>
    <div class="card"><h2><span class="ic">🛁</span> Warm then cool</h2>
      <p>Warm Epsom-salt bath relaxes muscles. Then a quick cool rinse on the calves before bed can reset jumpy nerves.</p></div>
    <div class="card"><h2><span class="ic">🌡️</span> Cool, dark cave</h2>
      <ul class="dots">
        <li><b>Room 60–67°F.</b> Warm rooms reliably make RLS worse.</li>
        <li><b>Fan on your feet</b> (or warm socks) — let yourself experiment.</li>
        <li><b>Compression socks</b> in bed can pre-empt the wriggle.</li>
      </ul></div>
    <div class="card"><h2><span class="ic">🍽️</span> Light, clean dinner</h2>
      <p>Heavy sugar / processed carbs before bed spike inflammation, which can block your brain from using iron. Lean and simple at night = fewer flares.</p></div>
  </section>

  <!-- ================= TIMER ================= -->
  <section id="timer">
    <div class="card"><h2><span class="ic">⏱️</span> Rescue timer</h2>
      <p>Pick a length, breathe, let it run while you stretch or use heat. A soft chime sounds when done.</p>
      <div class="presets" id="presets">
        <button data-s="45">45s stretch</button>
        <button data-s="300" class="sel">5 min reset</button>
        <button data-s="1200">20 min heat</button>
      </div>
      <div class="timerwrap"><div class="clock" id="clock">05:00</div>
        <div class="tlabel" id="tlabel">ready when you are 🐛</div></div>
      <div class="trow"><button class="go" id="startBtn" onclick="toggleTimer()">Start</button>
        <button onclick="resetTimer()">Reset</button></div>
    </div>
    <div class="card"><h2><span class="ic">🌬️</span> Breathing pace</h2>
      <p id="breathTxt">Tap below, follow the dot — in for 4, hold, out for 6.</p>
      <div class="timerwrap"><div id="breathCircle" style="width:120px;height:120px;border-radius:50%;
        margin:14px auto 4px;background:radial-gradient(circle,var(--glow),var(--glow-deep));
        box-shadow:0 0 30px rgba(196,169,240,.5);transition:transform 4s ease-in-out;"></div></div>
      <div class="trow"><button class="go" id="breathBtn" onclick="toggleBreath()">Begin</button></div>
    </div>
  </section>

  <!-- ================= IRON ================= -->
  <section id="iron">
    <div class="card"><span class="pill day">The biggest lever</span>
      <h2><span class="ic">🩸</span> Iron is the #1 thing</h2>
      <p>Low brain iron is one of the main drivers of RLS — it starves the dopamine "brake." The newest 2025 guidelines put iron <b>first</b>, ahead of older drugs.</p></div>

    <div class="warnbox" style="background:rgba(143,214,160,.08);border-color:rgba(143,214,160,.3);">
      <h2 style="color:var(--moss)"><span class="ic">🩺</span> Ask for one blood test</h2>
      <p style="color:#cfe8d4">Since your grandma has RLS too, this is worth doing. Ask for a morning <b>ferritin</b> + <b>transferrin saturation</b> test. Guidelines suggest iron treatment helps when ferritin is under ~75. 🦋</p>
      <div class="ironset">
        <input id="ferIn" type="number" inputmode="numeric" placeholder="Your ferritin number…">
        <button onclick="checkFer()">Check</button>
      </div>
      <div class="ironresult" id="ferOut" style="color:#cfe8d4;"></div>
    </div>

    <div class="card"><h2><span class="ic">💊</span> If your doctor okays supplements</h2>
      <ul class="dots">
        <li><b>Gentle iron (bisglycinate)</b> with <b>vitamin C</b> (like OJ). Empty stomach in the evening works well for many.</li>
        <li><b>Never</b> take iron with dairy, calcium, or coffee — they block it.</li>
        <li><b>Magnesium glycinate</b> ~30 min before bed relaxes muscles (skip oxide — upsets stomach).</li>
        <li><b>Vitamin D3 &amp; B12</b> baseline — low levels make nerves more sensitive.</li>
      </ul>
      <p style="margin-top:10px;color:var(--ink-faint);font-size:12.5px;">Iron can harm in excess, so test first — don't megadose on your own.</p></div>
  </section>

  <!-- ================= WATCH OUT ================= -->
  <section id="avoid">
    <p class="lead">Some everyday things quietly crank RLS up. Not rules — just things to notice. 🐝</p>
    <div class="warnbox"><h2><span class="ic">🚫</span> The big one: sedating antihistamines</h2>
      <p>Benadryl (diphenhydramine), ZzzQuil, and "PM" sleep aids block dopamine and can flare RLS hard within an hour. For allergies, ask a pharmacist about gentler options.</p></div>
    <div class="card"><h2><span class="ic">💬</span> Worth a chat with your doctor</h2>
      <p>Some <b>antidepressants</b> (SSRIs/SNRIs like sertraline, venlafaxine, mirtazapine) can worsen RLS. <b>Bupropion</b> usually doesn't — and can even help. If you take anything for mood/anxiety and your legs got worse after starting, mention it. <b>Never stop a prescription on your own</b> — just raise it.</p></div>
    <div class="card"><h2><span class="ic">🔎</span> Common triggers to watch</h2>
      <div><span class="tag">caffeine after noon</span><span class="tag">alcohol</span><span class="tag">nicotine</span>
        <span class="tag">dehydration</span><span class="tag">hot rooms</span><span class="tag">late hard workouts</span>
        <span class="tag">sugary dinners</span><span class="tag">poor sleep</span><span class="tag">some anti-nausea meds</span></div>
      <p style="margin-top:10px;">Everyone's triggers differ — that's exactly what the Check In tab helps you find.</p></div>
  </section>

  <!-- ================= MED WATCH / AUGMENTATION ================= -->
  <section id="med">
    <p class="lead">You're not on RLS medication now — so this is just <i>future-you insurance</i>. If a doctor ever puts you on certain older RLS drugs, there's one pattern that's really good to recognize early. 💊</p>

    <div class="card">
      <h2><span class="ic">🌅</span> The pattern to know: "augmentation"</h2>
      <p>A specific group of older RLS meds — <b>dopamine agonists</b> (ropinirole, pramipexole, rotigotine) and levodopa — can, over months or years, paradoxically make RLS <i>worse</i>. The tricky part is it looks like the disease just "getting worse," so people ask for a higher dose, which makes it worse still.</p>
      <p style="margin-top:8px;">The newest guidelines moved these drugs to <b>last-resort</b> for exactly this reason — iron and gabapentinoids come first now. Most people never need to worry about this.</p>
    </div>

    <div class="card">
      <h2><span class="ic">🔍</span> 4 signs to flag to a doctor</h2>
      <p>If you're ever on those meds and notice these, it's worth a conversation — <b>not</b> a reason to change anything yourself:</p>
      <ul class="dots">
        <li><b>Earlier in the day.</b> Symptoms that used to start after 8 PM now show up in the afternoon or midday.</li>
        <li><b>Spreading.</b> The feeling creeps up into your thighs, or into your arms/torso — not just lower legs.</li>
        <li><b>Faster to hit.</b> Sitting still triggers it within minutes instead of after 30–60 min.</li>
        <li><b>Dose stops lasting.</b> A dose increase helps less, or wears off sooner than it used to.</li>
      </ul>
    </div>

    <div class="warnbox">
      <h2><span class="ic">🛑</span> The one hard rule</h2>
      <p>If any of this ever happens, <b>never stop or change an RLS drug on your own</b> — stopping suddenly can cause a rough rebound. It's very manageable <i>with</i> a doctor: they taper slowly and swap in a non-dopamine option. Just bring it up.</p>
    </div>

    <div class="card">
      <h2><span class="ic">📝</span> Keep a quick med note</h2>
      <p>If you ever start an RLS med, jot the name + start date here so you (and your doctor) can spot timing patterns later. Stays on your phone only.</p>
      <div class="ironset" style="flex-direction:column;align-items:stretch;">
        <input id="medName" type="text" placeholder="Medication name (optional)…" style="flex:none;">
        <input id="medDate" type="text" inputmode="numeric" placeholder="Started when? e.g. Jun 2026" style="flex:none;margin-top:8px;">
        <button onclick="saveMed()" style="margin-top:8px;">Save note</button>
      </div>
      <div class="ironresult" id="medOut" style="color:var(--ink-soft);"></div>
    </div>
  </section>

  <!-- ================= WHY ================= -->
  <section id="why">
    <div class="card"><h2><span class="ic">🧠</span> What's actually happening</h2>
      <p>Your brain uses dopamine as a "brake pedal" for movement, and needs iron to make it. When brain iron runs low, the brake weakens — so at rest, legs get that urge to move. Moving briefly restores the brake, which is why walking helps and lying still feels awful.</p></div>
    <div class="card"><h2><span class="ic">🧬</span> Why you, why now</h2>
      <p>It runs in families — your grandma having it means a genetic thread. Not bad luck you caused; just your wiring. And it's very manageable once you know the levers: iron, triggers, temperature, movement.</p></div>
    <div class="card"><h2><span class="ic">🦇</span> The good news</h2>
      <p>The whole field shifted in 2025 toward iron-first, gentle, preventative care — away from heavy old drugs. Most people get real relief from the things in this app plus fixing iron.</p></div>
    <details><summary>🐛 Is it permanent? <span class="ar">⌄</span></summary>
      <div class="body"><p>RLS waxes and wanes, but severity is very changeable. Many people barely notice it when iron is topped up and triggers managed. Flares are information, not failure.</p></div></details>
    <details><summary>🦋 When should I see a doctor? <span class="ar">⌄</span></summary>
      <div class="body"><p>Worth a visit if it disrupts sleep most nights, worsens, or you want the iron test. Bring your Patterns summary — it makes the appointment way more useful.</p></div></details>
    <details><summary>🦔 Why only at rest? <span class="ar">⌄</span></summary>
      <div class="body"><p>The weak dopamine brake shows up most when you're still and unstimulated — evenings, naps, long drives. Movement and mental focus both mask it, which is why the rescue steps work.</p></div></details>

    <div class="card" style="margin-top:14px;">
      <h2><span class="ic">✅</span> Does it sound like RLS?</h2>
      <p>Doctors look for 5 things together. This isn't a diagnosis — just a way to see if your experience fits the picture, and a handy checklist to show a doctor. Tap the ones that feel true:</p>
      <div id="criteriaList"></div>
      <div class="ironresult" id="criteriaOut" style="margin-top:12px;"></div>
    </div>

    <div class="foot">
      Made with 🦇🐛🦋 for Maddie. Your logs stay private on your phone.<br>
      <b>Supportive info, not medical advice.</b> Iron tests, supplements, and any med changes go through your doctor. You deserve good sleep. 💜
    </div>
  </section>

</div>

<div class="toast" id="toast"></div>

<script>
/* ============ DATA ============ */
var STORE='maddie_rls_v2';
function load(){try{return JSON.parse(localStorage.getItem(STORE))||{logs:[],ferritin:null,meds:null};}
  catch(e){return{logs:[],ferritin:null,meds:null};}}
function save(d){try{localStorage.setItem(STORE,JSON.stringify(d));}catch(e){}}
var data=load();

var TRIGGERS=["☕ Caffeine pm","🍷 Alcohol","🚬 Nicotine","🥤 Low water","🔥 Hot room",
  "🏋️ Late workout","🍰 Heavy/sugary dinner","😣 Stressful day","😴 Poor sleep","💊 New meds"];
var HELPERS=["🧦 Compression","🧘 Stretches","🔥 Heat","🧊 Cold","🚶 Walk","💧 Hydrated",
  "🛁 Warm bath","🧲 Magnesium","🩸 Iron","🌬️ Breathing","📓 Brain dump"];

var CRITERIA=[
  "An urge to move my legs, usually with an uncomfortable creepy/crawly feeling",
  "It starts or gets worse when I'm resting or sitting still",
  "Moving (walking, stretching) makes it better, at least while I'm moving",
  "It's worse in the evening or night than during the day",
  "It's not better explained by something else (cramps, sitting position, etc.)"
];
var critSel=[];

var sel={sev:null,slp:null,trig:[],help:[]};

/* ============ FIREFLIES ============ */
(function(){var sky=document.getElementById('sky');
  for(var i=0;i<14;i++){var f=document.createElement('div');f.className='firefly';
    f.style.left=Math.random()*100+'%';f.style.top=(60+Math.random()*40)+'%';
    var d=6+Math.random()*8;f.style.animationDuration=d+'s';
    f.style.animationDelay=(Math.random()*d)+'s';sky.appendChild(f);}})();

/* ============ TABS ============ */
var tabs=document.querySelectorAll('.tab');
function go(t){
  tabs.forEach(function(b){b.classList.toggle('on',b.dataset.t===t);});
  document.querySelectorAll('section').forEach(function(s){s.classList.toggle('on',s.id===t);});
  window.scrollTo({top:0,behavior:'smooth'});
  if(t==='home')renderHome();
  if(t==='patterns')renderPatterns();
  if(t==='log')renderLog();
  if(t==='why')renderCriteria();
  if(t==='med')renderMed();
}
tabs.forEach(function(b){b.addEventListener('click',function(){go(b.dataset.t);});});

/* ============ TOAST ============ */
var toastT;
function toast(msg){var el=document.getElementById('toast');el.textContent=msg;
  el.classList.add('show');clearTimeout(toastT);
  toastT=setTimeout(function(){el.classList.remove('show');},2600);}

/* ============ DATE HELPERS ============ */
function todayKey(){var d=new Date();return d.getFullYear()+'-'+(d.getMonth()+1)+'-'+d.getDate();}
function niceDate(k){var p=k.split('-');var d=new Date(p[0],p[1]-1,p[2]);
  return d.toLocaleDateString(undefined,{weekday:'short',month:'short',day:'numeric'});}
function loggedToday(){return data.logs.some(function(l){return l.k===todayKey();});}

/* ============ BUILD LOG UI ============ */
function buildScale(id,key){var w=document.getElementById(id);w.innerHTML='';
  for(var i=0;i<=10;i+=2){(function(n){var b=document.createElement('button');b.textContent=n;
    b.onclick=function(){sel[key]=n;w.querySelectorAll('button').forEach(function(x){x.classList.remove('sel');});
      b.classList.add('sel');updateReadout(key,n);checkSave();if(navigator.vibrate)navigator.vibrate(8);};
    w.appendChild(b);})(i);}}
function updateReadout(key,n){
  var sevWords=["none 😌","barely there","mild","noticeable","rough","awful 😣"];
  var slpWords=["very rough 😴","poor","okay","decent","good","great 🌙"];
  var idx=Math.min(5,Math.round(n/2));
  var el=document.getElementById(key==='sev'?'sevReadout':'slpReadout');
  if(el)el.textContent=(key==='sev'?sevWords:slpWords)[idx];
}
function buildChips(id,arr,key,cls){var w=document.getElementById(id);w.innerHTML='';
  arr.forEach(function(t){var b=document.createElement('button');b.className='chip'+(cls?' '+cls:'');
    b.textContent=t;b.onclick=function(){var idx=sel[key].indexOf(t);
      if(idx>=0){sel[key].splice(idx,1);b.classList.remove('sel');}
      else{sel[key].push(t);b.classList.add('sel');}
      if(navigator.vibrate)navigator.vibrate(6);};w.appendChild(b);});}
function checkSave(){document.getElementById('saveBtn').disabled=(sel.sev===null);}
function renderLog(){
  buildScale('sevScale','sev');buildScale('slpScale','slp');
  buildChips('trigChips',TRIGGERS,'trig','');buildChips('helpChips',HELPERS,'help','help');
  sel={sev:null,slp:null,trig:[],help:[]};checkSave();
  var sr=document.getElementById('sevReadout');if(sr)sr.textContent='tap one';
  var lr=document.getElementById('slpReadout');if(lr)lr.textContent='tap one';
}

function saveLog(){
  if(sel.sev===null)return;
  var k=todayKey();
  data.logs=data.logs.filter(function(l){return l.k!==k;}); // overwrite today
  data.logs.push({k:k,t:Date.now(),sev:sel.sev,slp:sel.slp,trig:sel.trig.slice(),help:sel.help.slice()});
  data.logs.sort(function(a,b){return a.t-b.t;});
  save(data);
  var n=data.logs.length;
  var msg=n===1?"First check-in saved! 🌱 This is the whole game — just showing up.":
    "Saved 🌙 "+n+" nights logged. You're building your map.";
  toast(msg);
  if(navigator.vibrate)navigator.vibrate([40,30,40]);
  setTimeout(function(){go('patterns');},700);
}

/* ============ HOME ============ */
function renderHome(){
  var g=document.getElementById('greeting');
  var h=new Date().getHours();
  var hi=h<12?"Morning, Maddie 🌅":h<18?"Afternoon, Maddie ☀️":"Evening, Maddie 🌙";
  g.textContent=hi+" — your burrow's right here.";

  var msg=document.getElementById('todayMsg');
  var ring=document.getElementById('ringCard');
  if(data.logs.length===0){
    msg.innerHTML="Welcome to your den. 🦇<br><br>Tonight, try one tiny thing: tap <b>Check In</b> and rate how your legs felt. That's it. One tap a night is how this whole thing learns to help you.";
    ring.style.display='none';return;
  }
  if(loggedToday()){
    var l=data.logs[data.logs.length-1];
    msg.innerHTML="Tonight's check-in is done — nicely done. 🌟<br><br>"+
      "Legs at <b>"+l.sev+"/10</b>"+(l.slp!==null?", sleep at <b>"+l.slp+"/10</b>":"")+
      ". Peek at <b>Patterns</b> to see what's been helping you most.";
  } else {
    msg.innerHTML="Good to see you. 🐛<br><br>You haven't checked in yet today. When you're winding down, give it 60 seconds — future-you will thank you.";
  }
  // rolling 7-day consistency ring
  ring.style.display='flex';
  var days7=last7Keys();
  var done=days7.filter(function(k){return data.logs.some(function(l){return l.k===k;});}).length;
  var pct=done/7;var circ=201;
  document.getElementById('ringFill').style.strokeDashoffset=circ-(circ*pct);
  document.getElementById('ringTxt').innerHTML="<b>"+done+" of 7</b> nights logged this week.<br>"+
    (done>=5?"Beautiful consistency. 🦋":done>=2?"You're finding the rhythm. Keep going.":"Every single night counts — no streaks to break here.");
}
function last7Keys(){var arr=[];for(var i=6;i>=0;i--){var d=new Date();d.setDate(d.getDate()-i);
  arr.push(d.getFullYear()+'-'+(d.getMonth()+1)+'-'+d.getDate());}return arr;}

/* ============ PATTERNS / THE "RESPONSE" ============ */
function renderPatterns(){
  var c=document.getElementById('patternsContent');
  var n=data.logs.length;
  if(n===0){
    c.innerHTML='<div class="card"><div class="emptynote">🔮<br><br>No check-ins yet. Once you log a few nights, this page fills with <b>your</b> personal patterns — which triggers tend to come before bad nights, and what helps most.<br><br>Start with one tonight!</div>'+
      '<button class="savebtn" onclick="go(\'log\')">Do my first check-in 🐾</button></div>';
    return;
  }

  var recent=data.logs.slice(-14);
  var avgSev=(recent.reduce(function(a,l){return a+l.sev;},0)/recent.length);
  var avgSlp=recent.filter(function(l){return l.slp!==null;});
  var avgSlpV=avgSlp.length?(avgSlp.reduce(function(a,l){return a+l.slp;},0)/avgSlp.length):null;

  // trend: compare first half vs second half of recent
  var trendTxt="Keep logging a few more nights and I'll show you whether things are trending up or down. 🌱";
  if(recent.length>=6){
    var half=Math.floor(recent.length/2);
    var early=recent.slice(0,half),late=recent.slice(half);
    var eAvg=early.reduce(function(a,l){return a+l.sev;},0)/early.length;
    var lAvg=late.reduce(function(a,l){return a+l.sev;},0)/late.length;
    var diff=lAvg-eAvg;
    if(diff<=-1)trendTxt="📉 Your legs have been <b>calmer lately</b> than your earlier nights. Whatever you're doing — keep it up. 🦋";
    else if(diff>=1)trendTxt="📈 Your legs have been <b>a bit rougher lately</b>. Not a failure — a signal. Scroll down to see which triggers showed up most.";
    else trendTxt="〰️ Pretty <b>steady</b> lately. Steady is a fine place to build from.";
  }

  // trigger correlation: avg severity on nights a trigger was present
  var trigStats={};
  TRIGGERS.forEach(function(t){var withT=data.logs.filter(function(l){return l.trig.indexOf(t)>=0;});
    if(withT.length>=2){trigStats[t]={n:withT.length,
      avg:withT.reduce(function(a,l){return a+l.sev;},0)/withT.length};}});
  var trigArr=Object.keys(trigStats).map(function(t){return{t:t,n:trigStats[t].n,avg:trigStats[t].avg};})
    .sort(function(a,b){return b.avg-a.avg;});

  // helper correlation: avg severity on nights a helper was used
  var helpStats={};
  HELPERS.forEach(function(t){var withH=data.logs.filter(function(l){return l.help.indexOf(t)>=0;});
    if(withH.length>=2){helpStats[t]={n:withH.length,
      avg:withH.reduce(function(a,l){return a+l.sev;},0)/withH.length};}});
  var helpArr=Object.keys(helpStats).map(function(t){return{t:t,n:helpStats[t].n,avg:helpStats[t].avg};})
    .sort(function(a,b){return a.avg-b.avg;});

  var html='';

  // headline insight
  html+='<div class="insight"><h2><span class="ic">🔮</span> Your map so far</h2>'+
    '<div class="big">'+trendTxt+'</div></div>';

  // stats
  html+='<div class="statrow">'+
    '<div class="stat"><div class="v">'+n+'</div><div class="l">nights<br>logged</div></div>'+
    '<div class="stat"><div class="v">'+avgSev.toFixed(1)+'</div><div class="l">avg legs<br>(last 14)</div></div>'+
    (avgSlpV!==null?'<div class="stat"><div class="v">'+avgSlpV.toFixed(1)+'</div><div class="l">avg sleep<br>(last 14)</div></div>':'')+
    '</div>';

  // severity bars (last 7 logged)
  var last=data.logs.slice(-7);
  html+='<div class="card"><h2><span class="ic">📊</span> Recent nights</h2><div class="bars barwrap">';
  last.forEach(function(l){var h=Math.max(8,l.sev/10*80);
    var col=l.sev>=7?'#c85c5c':l.sev>=4?'#e8c98a':'#8fd6a0';
    var p=l.k.split('-');
    html+='<div class="bar" style="height:'+h+'px;background:'+col+';"><span class="bl">'+p[1]+'/'+p[2]+'</span></div>';});
  html+='</div></div>';

  // triggers before bad nights
  if(trigArr.length){
    html+='<div class="card"><h2><span class="ic">⚠️</span> Showed up on your rougher nights</h2>'+
      '<p>On nights these appeared, your legs averaged worse. Worth watching — not certainties.</p>';
    trigArr.slice(0,4).forEach(function(x){
      var col=x.avg>=7?'#c85c5c':x.avg>=4?'#e8c98a':'#8fd6a0';
      html+='<div class="logitem"><div class="dot" style="background:'+col+'">'+x.avg.toFixed(0)+'</div>'+
        '<div class="d"><b>'+x.t+'</b><br><small>avg legs '+x.avg.toFixed(1)+'/10 · seen '+x.n+' nights</small></div></div>';});
    html+='</div>';
  }

  // what helps
  if(helpArr.length){
    html+='<div class="card"><h2><span class="ic">💚</span> Seems to help YOU most</h2>'+
      '<p>On nights you did these, your legs tended to be calmer. Your personal toolkit.</p>';
    helpArr.slice(0,4).forEach(function(x){
      html+='<div class="logitem"><div class="dot" style="background:var(--moss-deep)">'+x.avg.toFixed(0)+'</div>'+
        '<div class="d"><b>'+x.t+'</b><br><small>avg legs '+x.avg.toFixed(1)+'/10 · used '+x.n+' nights</small></div></div>';});
    html+='</div>';
  }

  if(!trigArr.length && !helpArr.length){
    html+='<div class="card"><div class="emptynote">Log a few more nights (and tap the trigger/helper chips) and your personal patterns will appear here. 🌱</div></div>';
  }

  // doctor summary + export
  html+='<div class="card"><h2><span class="ic">🩺</span> For your doctor</h2>'+
    '<p>Tap to copy a clean summary you can read out or paste into a note at your appointment.</p>'+
    '<button class="ghostbtn" onclick="copySummary()">📋 Copy my summary</button>'+
    '<button class="ghostbtn" onclick="clearData()" style="border-color:rgba(240,160,122,.3);color:var(--warn);">Clear all my data</button></div>';

  c.innerHTML=html;
}

function copySummary(){
  var n=data.logs.length;var recent=data.logs.slice(-14);
  var avgSev=(recent.reduce(function(a,l){return a+l.sev;},0)/recent.length).toFixed(1);
  var txt="RLS check-in summary (Maddie)\n";
  txt+=n+" nights logged. Avg leg severity last 14 nights: "+avgSev+"/10.\n";
  if(data.ferritin)txt+="Most recent ferritin entered: "+data.ferritin+".\n";
  if(data.meds&&(data.meds.name||data.meds.date))txt+="RLS medication noted: "+(data.meds.name||'(unnamed)')+(data.meds.date?' since '+data.meds.date:'')+".\n";
  // top triggers
  var trigCount={};data.logs.forEach(function(l){l.trig.forEach(function(t){trigCount[t]=(trigCount[t]||0)+1;});});
  var topTrig=Object.keys(trigCount).sort(function(a,b){return trigCount[b]-trigCount[a];}).slice(0,4);
  if(topTrig.length)txt+="Most common triggers noted: "+topTrig.join(", ")+".\n";
  var lastN=data.logs.slice(-7).map(function(l){return niceDate(l.k)+": legs "+l.sev+"/10"+(l.slp!==null?", sleep "+l.slp+"/10":"");}).join("\n");
  txt+="\nLast 7 nights:\n"+lastN;
  if(navigator.clipboard){navigator.clipboard.writeText(txt).then(function(){toast("Summary copied 📋");});}
  else{toast("Copy not supported here");}
}

function clearData(){
  if(confirm("Clear all your check-ins and notes? This can't be undone.")){
    data={logs:[],ferritin:null};save(data);toast("All cleared 🌱");renderPatterns();
  }
}

/* ============ CRITERIA SELF-CHECK ============ */
function renderCriteria(){
  var w=document.getElementById('criteriaList');if(!w)return;
  w.innerHTML='';critSel=[];
  CRITERIA.forEach(function(t,i){
    var d=document.createElement('div');d.className='check';
    d.innerHTML='<div class="box"></div><div class="ct">'+t+'</div>';
    d.onclick=function(){var idx=critSel.indexOf(i);
      if(idx>=0){critSel.splice(idx,1);d.classList.remove('done');d.querySelector('.box').textContent='';}
      else{critSel.push(i);d.classList.add('done');d.querySelector('.box').textContent='✓';}
      if(navigator.vibrate)navigator.vibrate(6);
      var o=document.getElementById('criteriaOut');var n=critSel.length;
      if(n===0){o.innerHTML='';}
      else if(n===5){o.innerHTML='<span class="hi">All 5 fit.</span> That\u2019s the classic RLS picture. Worth showing this to a doctor — especially with your family history. 🦋';}
      else{o.innerHTML='You checked <b>'+n+' of 5</b>. RLS is usually diagnosed when all 5 line up — if some feel iffy, a doctor can help sort out what\u2019s going on. Either way, the comfort tips here still help.';}
    };
    w.appendChild(d);
  });
  document.getElementById('criteriaOut').innerHTML='';
}

/* ============ MED NOTE ============ */
function renderMed(){
  if(data.meds){
    document.getElementById('medName').value=data.meds.name||'';
    document.getElementById('medDate').value=data.meds.date||'';
    document.getElementById('medOut').innerHTML='Saved note: <b>'+(data.meds.name||'(no name)')+'</b>'+(data.meds.date?' · started '+data.meds.date:'');
  }
}
function saveMed(){
  var nm=document.getElementById('medName').value.trim();
  var dt=document.getElementById('medDate').value.trim();
  if(!nm&&!dt){document.getElementById('medOut').textContent='Nothing to save yet — fill in a name or date.';return;}
  data.meds={name:nm,date:dt};save(data);
  document.getElementById('medOut').innerHTML='Saved 💾 <b>'+(nm||'(no name)')+'</b>'+(dt?' · started '+dt:'')+'<br><small style="color:var(--ink-faint)">On your phone only.</small>';
  toast('Med note saved 💊');if(navigator.vibrate)navigator.vibrate(10);
}

/* ============ IRON / FERRITIN ============ */
function checkFer(){
  var v=parseFloat(document.getElementById('ferIn').value);var o=document.getElementById('ferOut');
  if(isNaN(v)){o.textContent="Pop in the number from your blood test 🩸";return;}
  data.ferritin=v;save(data);
  var m;
  if(v<30)m="🔴 Quite low. This is exactly the range where iron often drives RLS — definitely worth talking to your doctor about treatment.";
  else if(v<75)m="🟡 Below ~75 — the 2025 guidelines suggest iron treatment can help RLS in this range. Worth raising with your doctor.";
  else if(v<=100)m="🟢 Decent, though some specialists still treat up to ~100 if RLS is stubborn. A good conversation to have.";
  else m="🟢 Solid iron stores. If legs are still rough, the other levers (triggers, temperature, movement, meds review) matter more for you.";
  o.innerHTML=m+"<br><small style='color:var(--ink-faint)'>Saved. Not medical advice — your doctor reads the full picture.</small>";
  if(navigator.vibrate)navigator.vibrate(10);
}

/* ============ TIMER ============ */
var total=300,left=300,tick=null,running=false;
var clock=document.getElementById('clock'),tlabel=document.getElementById('tlabel'),startBtn=document.getElementById('startBtn');
function fmt(s){var m=Math.floor(s/60),x=s%60;return(m<10?'0':'')+m+':'+(x<10?'0':'')+x;}
function draw(){clock.textContent=fmt(left);}
document.querySelectorAll('#presets button').forEach(function(b){
  b.addEventListener('click',function(){document.querySelectorAll('#presets button').forEach(function(x){x.classList.remove('sel');});
    b.classList.add('sel');total=left=parseInt(b.dataset.s);running=false;clearInterval(tick);
    startBtn.textContent='Start';tlabel.textContent='ready when you are 🐛';draw();});});
function chime(){try{var a=new(window.AudioContext||window.webkitAudioContext)();
  [880,660,990].forEach(function(f,i){var o=a.createOscillator(),g=a.createGain();
    o.frequency.value=f;o.connect(g);g.connect(a.destination);var t=a.currentTime+i*.18;
    g.gain.setValueAtTime(0,t);g.gain.linearRampToValueAtTime(.3,t+.04);
    g.gain.exponentialRampToValueAtTime(.001,t+.5);o.start(t);o.stop(t+.5);});}catch(e){}}
function toggleTimer(){if(running){running=false;clearInterval(tick);startBtn.textContent='Resume';tlabel.textContent='paused';return;}
  running=true;startBtn.textContent='Pause';tlabel.textContent='breathe… you\u2019re doing great 🦋';
  tick=setInterval(function(){left--;draw();if(left<=0){clearInterval(tick);running=false;startBtn.textContent='Start';
    tlabel.textContent='done — nicely done 🌟';clock.textContent='00:00';chime();
    if(navigator.vibrate)navigator.vibrate([200,100,200]);left=total;}},1000);}
function resetTimer(){running=false;clearInterval(tick);left=total;draw();startBtn.textContent='Start';tlabel.textContent='ready when you are 🐛';}
draw();

/* ============ BREATHING ============ */
var breathing=false,bTick=null,phase=0;
var circle=document.getElementById('breathCircle'),breathTxt=document.getElementById('breathTxt'),breathBtn=document.getElementById('breathBtn');
var phases=[['Breathe in…',1.6,4000],['Hold…',1.6,2000],['Breathe out…',1,6000]];
function runPhase(){var p=phases[phase];breathTxt.textContent=p[0];
  circle.style.transitionDuration=(p[2]/1000)+'s';circle.style.transform='scale('+p[1]+')';
  bTick=setTimeout(function(){phase=(phase+1)%phases.length;runPhase();},p[2]);}
function toggleBreath(){if(breathing){breathing=false;clearTimeout(bTick);circle.style.transform='scale(1)';
  breathBtn.textContent='Begin';breathTxt.textContent='Tap below, follow the dot — in for 4, hold, out for 6.';return;}
  breathing=true;phase=0;breathBtn.textContent='Stop';runPhase();}

/* ============ INIT ============ */
renderHome();
</script>
</body>
</html>
