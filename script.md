
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:var(--font-sans)}
.script-wrap{padding:1.5rem 0}
.top-bar{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.5rem;flex-wrap:wrap;gap:10px}
.top-bar h1{font-size:16px;font-weight:500;color:var(--color-text-primary)}
.pills{display:flex;gap:8px;flex-wrap:wrap}
.pill{padding:4px 12px;border-radius:20px;font-size:11px;font-weight:500;font-family:var(--font-sans)}
.pill-total{background:var(--color-background-secondary);color:var(--color-text-secondary);border:.5px solid var(--color-border-tertiary)}
.pill-age{background:#EEEDFE;color:#3C3489}
.pill-dur{background:#E1F5EE;color:#085041}

.scene-card{background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);margin-bottom:10px;overflow:hidden}
.scene-header{display:flex;align-items:center;gap:12px;padding:10px 14px;border-bottom:.5px solid var(--color-border-tertiary);cursor:pointer;user-select:none}
.scene-num{width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:500;font-family:var(--font-sans);flex-shrink:0}
.scene-meta{flex:1}
.scene-title{font-size:13px;font-weight:500;color:var(--color-text-primary)}
.scene-sub{font-size:11px;color:var(--color-text-secondary);margin-top:1px}
.scene-time{font-size:11px;color:var(--color-text-tertiary);font-family:var(--font-sans);flex-shrink:0}
.chevron{font-size:12px;color:var(--color-text-tertiary);transition:transform .2s;flex-shrink:0}
.chevron.open{transform:rotate(180deg)}

.scene-body{padding:12px 14px 14px;display:none}
.scene-body.open{display:block}

.row{display:grid;grid-template-columns:90px 1fr;gap:8px;margin-bottom:10px;align-items:start}
.row:last-child{margin-bottom:0}
.row-label{font-size:10px;font-weight:500;color:var(--color-text-tertiary);text-transform:uppercase;letter-spacing:.5px;padding-top:2px}
.row-val{font-size:13px;color:var(--color-text-primary);line-height:1.55}

.vo-text{font-size:13px;color:var(--color-text-primary);line-height:1.65;background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:9px 12px;border-left:3px solid #7F77DD;border-radius:0;border-radius:var(--border-radius-md)}
.vo-text em{color:#534AB7;font-style:normal;font-weight:500}

.visual-tag{display:inline-flex;align-items:center;gap:5px;background:var(--color-background-secondary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:4px 9px;font-size:11px;color:var(--color-text-secondary);margin:3px 3px 0 0}

.onscreen-tag{display:inline-block;background:#FAECE7;color:#712B13;font-size:11px;padding:3px 8px;border-radius:var(--border-radius-md);margin:2px 2px 0 0}

.timing-bar{height:4px;border-radius:2px;margin-bottom:10px}

.legend{display:flex;gap:16px;flex-wrap:wrap;margin-top:1rem;padding-top:1rem;border-top:.5px solid var(--color-border-tertiary)}
.legend-item{display:flex;align-items:center;gap:6px;font-size:11px;color:var(--color-text-secondary)}
.legend-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0}

.total-bar{background:var(--color-background-secondary);border-radius:var(--border-radius-lg);padding:12px 16px;margin-bottom:1.5rem;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px}
.total-bar-stat{text-align:center}
.total-bar-num{font-size:20px;font-weight:500;color:var(--color-text-primary)}
.total-bar-lbl{font-size:11px;color:var(--color-text-secondary);margin-top:1px}
</style>

<h2 class="sr-only">TikTok video script for mass transfer phenomena, 9 scenes, ~50 seconds, targeted at 7-year-olds</h2>

<div class="script-wrap">
  <div class="top-bar">
    <h1>Mass transfer — TikTok script</h1>
    <div class="pills">
      <span class="pill pill-age">Age 7+</span>
      <span class="pill pill-dur">~50 sec</span>
      <span class="pill pill-total">9 scenes</span>
    </div>
  </div>

  <div class="total-bar">
    <div class="total-bar-stat"><div class="total-bar-num">0:00–0:04</div><div class="total-bar-lbl">Hook</div></div>
    <div style="color:var(--color-text-tertiary);font-size:12px">→</div>
    <div class="total-bar-stat"><div class="total-bar-num">0:05–0:12</div><div class="total-bar-lbl">Explain</div></div>
    <div style="color:var(--color-text-tertiary);font-size:12px">→</div>
    <div class="total-bar-stat"><div class="total-bar-num">0:13–0:28</div><div class="total-bar-lbl">Examples</div></div>
    <div style="color:var(--color-text-tertiary);font-size:12px">→</div>
    <div class="total-bar-stat"><div class="total-bar-num">0:29–0:40</div><div class="total-bar-lbl">Quiz + Types</div></div>
    <div style="color:var(--color-text-tertiary);font-size:12px">→</div>
    <div class="total-bar-stat"><div class="total-bar-num">0:41–0:50</div><div class="total-bar-lbl">CTA</div></div>
  </div>

  <div id="cards"></div>

  <div class="legend">
    <div class="legend-item"><div class="legend-dot" style="background:#7F77DD"></div>Voiceover</div>
    <div class="legend-item"><div class="legend-dot" style="background:#D85A30"></div>On-screen text</div>
    <div class="legend-item"><div class="legend-dot" style="background:#1D9E75"></div>Visual / action</div>
    <div class="legend-item"><div class="legend-dot" style="background:#BA7517"></div>Sound cue</div>
  </div>
</div>

<script>
const scenes = [
  {
    num:1, color:'#534AB7', bg:'#EEEDFE',
    title:'Hook', emoji:'🤯',
    time:'0:00–0:04', timing:8,
    vo: 'Wait — <em>how does your nose smell cookies from the next room?</em> The answer will blow your mind.',
    onscreen:['Cookie 🍪 → Kid 🧒','HOW?! 🤯','👇 keep watching'],
    visuals:['Animated particles fill background','Trending badge top-left','Cookie + kid icon row appears'],
    sound:'Whoosh sound effect at start',
  },
  {
    num:2, color:'#185FA5', bg:'#E6F1FB',
    title:'Molecules can\'t sit still', emoji:'💨',
    time:'0:05–0:09', timing:10,
    vo: 'Everything is made of tiny, <em>tiny</em> balls called molecules — and they never stop moving!',
    onscreen:['CROWDED 😬 → EMPTY 😊','like kids rushing out of school 🏫'],
    visuals:['Side-by-side boxes: crowded emoji faces vs empty','School analogy card slides in'],
    sound:'Upbeat "boing" as molecules bounce',
  },
  {
    num:3, color:'#0F6E56', bg:'#E1F5EE',
    title:'The cookie example', emoji:'🍪',
    time:'0:10–0:16', timing:12,
    vo: 'Hot cookie in the kitchen — <em>millions</em> of smell molecules shoot into the air, zoom through the house, and hit your nose. Yummy detected!',
    onscreen:['🍪 wiggle animation','↓↓↓ millions fly out','🧒 YUMMY DETECTED! 🎉'],
    visuals:['Giant wiggling cookie top','Bouncing yellow dots fall','Kid bounces at bottom, spinning emoji'],
    sound:'"Ta-daa" jingle on YUMMY DETECTED',
  },
  {
    num:4, color:'#993C1D', bg:'#FAECE7',
    title:'The science word', emoji:'🧪',
    time:'0:17–0:21', timing:8,
    vo: 'Scientists call this… <em>diffusion.</em> Stuff. Moves. By itself. From crowded to empty.',
    onscreen:['…','DIFFUSION 💥','stuff moves • by itself • crowded→empty'],
    visuals:['Dramatic pause, particles slow','Word DIFFUSION pops on screen','Pill tags animate in one by one'],
    sound:'Deep "boom" on DIFFUSION reveal',
  },
  {
    num:5, color:'#3C3489', bg:'#EEEDFE',
    title:'Lungs & blood', emoji:'🫁',
    time:'0:22–0:28', timing:12,
    vo: 'Your body does this <em>sixty thousand times a day.</em> Breathe in — oxygen floods your blood. Breathe out — CO₂ escapes. You are a <em>walking mass-transfer machine!</em>',
    onscreen:['😮‍💨 O₂ in → blood','💨 CO₂ out → air','🧒💨🔵❤️ bouncing row'],
    visuals:['Lung icon pulses','Three colored cards slide in','Real lung photo / X-ray recommended here','Skip graphic blood photo — use red blob'],
    sound:'Heartbeat rhythm under voiceover',
  },
  {
    num:6, color:'#854F0B', bg:'#FAEEDA',
    title:'Quiz time!', emoji:'🎮',
    time:'0:29–0:33', timing:8,
    vo: 'Quiz time! You spray perfume. The whole room smells amazing. What just happened?',
    onscreen:['🧠 QUIZ TIME!','A) Magic ✨','B) Diffusion 💨','C) Perfume is alive 🧴'],
    visuals:['Brain emoji bounces in','3 answer buttons appear with delay','Comment flood overlay on B'],
    sound:'Game-show "ding ding" intro',
  },
  {
    num:7, color:'#0C447C', bg:'#E6F1FB',
    title:'Mass transfer types', emoji:'📚',
    time:'0:34–0:38', timing:8,
    vo: 'Diffusion is just one type. There\'s also <em>convection</em> — when wind helps molecules move — and <em>permeation</em>, sneaking through tiny holes.',
    onscreen:['💨 Diffusion — spreads alone','🌀 Convection — wind helps','🧱 Permeation — through holes'],
    visuals:['3 rows slide in one by one','Icons animate: float, spin, wiggle','Real photos: beach, coffee mug here'],
    sound:'Soft "pop" for each row appearing',
  },
  {
    num:8, color:'#633806', bg:'#FAEEDA',
    title:'Hot = faster!', emoji:'🌡️',
    time:'0:39–0:43', timing:8,
    vo: 'Oh — and heat makes molecules go <em>way</em> faster. Cold is slow like a snail. Hot is fast like a bunny!',
    onscreen:['🧊 ice → slow 🐌','🔥 fire → fast 🐇','hot cookie = smells from farther away! 🤯'],
    visuals:['Animated bar chart grows','Snail vs rabbit icons bounce','Bar for fire pulses red'],
    sound:'Speed-up whoosh on hot bar',
  },
  {
    num:9, color:'#72243E', bg:'#FBEAF0',
    title:'CTA + outro', emoji:'📣',
    time:'0:44–0:50', timing:10,
    vo: 'Your nose is a mass-transfer detector! Follow for more mind-blowing science — and drop a 💨 in the comments if you get it!',
    onscreen:['💾 Save to show your teacher','💨 Drop 💨 if you get it','🔁 Send to a friend who hates science','🎵 Duet with your teacher!'],
    visuals:['4 CTA cards bounce in','Particle burst animation','Handle @sciencekid.lab pulses'],
    sound:'Upbeat outro music fades in',
  },
];

const container = document.getElementById('cards');

scenes.forEach((s,i)=>{
  const card = document.createElement('div');
  card.className = 'scene-card';

  const timingW = Math.round(s.timing / 50 * 100);

  card.innerHTML = `
    <div class="timing-bar" style="background:${s.bg};width:${timingW}%;min-width:4px"></div>
    <div class="scene-header" onclick="toggle(${i})">
      <div class="scene-num" style="background:${s.bg};color:${s.color}">${s.num}</div>
      <div class="scene-meta">
        <div class="scene-title">${s.emoji} ${s.title}</div>
        <div class="scene-sub">${s.time}</div>
      </div>
      <div class="scene-time">${s.time.split('–')[1]}</div>
      <div class="chevron" id="chev${i}">▾</div>
    </div>
    <div class="scene-body" id="body${i}">
      <div class="row">
        <div class="row-label" style="color:#7F77DD">Voiceover</div>
        <div class="vo-text">${s.vo}</div>
      </div>
      <div class="row">
        <div class="row-label" style="color:#D85A30">On-screen</div>
        <div>${s.onscreen.map(t=>`<span class="onscreen-tag">${t}</span>`).join('')}</div>
      </div>
      <div class="row">
        <div class="row-label" style="color:#1D9E75">Visuals</div>
        <div>${s.visuals.map(v=>`<span class="visual-tag">${v}</span>`).join('')}</div>
      </div>
      <div class="row">
        <div class="row-label" style="color:#BA7517">Sound</div>
        <div class="row-val">${s.sound}</div>
      </div>
    </div>
  `;
  container.appendChild(card);
});

function toggle(i){
  const body = document.getElementById('body'+i);
  const chev = document.getElementById('chev'+i);
  const isOpen = body.classList.contains('open');
  body.classList.toggle('open',!isOpen);
  chev.classList.toggle('open',!isOpen);
}

toggle(0);
</script>
