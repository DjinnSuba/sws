# sws


<style>
*{box-sizing:border-box;margin:0;padding:0}
.wrap{display:flex;justify-content:center;gap:24px;padding:1.5rem 0;flex-wrap:wrap}
.phone{width:300px;height:620px;background:#0a0a0a;border-radius:40px;border:3px solid #2a2a2a;position:relative;overflow:hidden;flex-shrink:0}
.screen{width:100%;height:100%;position:relative;overflow:hidden}
.scene{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transform:translateX(100%);transition:opacity .4s ease, transform .4s cubic-bezier(.4,0,.2,1)}
.scene.active{opacity:1;pointer-events:all;transform:translateX(0)}
.scene.exit-left{opacity:0;transform:translateX(-100%)}
.scene.enter-right{opacity:0;transform:translateX(100%)}

.prog{position:absolute;top:0;left:0;right:0;height:3px;background:rgba(255,255,255,.15);z-index:10}
.prog-fill{height:100%;background:#fff;transition:width .35s ease}
.tt-ui{position:absolute;bottom:0;left:0;right:0;padding:10px 10px 20px;background:linear-gradient(transparent,rgba(0,0,0,.78));z-index:9}
.tt-handle{color:#fff;font-size:11px;font-weight:700;font-family:var(--font-sans)}
.tt-tag{color:#81b3ff;font-size:10px;font-family:var(--font-sans);margin-top:2px}
.tt-side{position:absolute;right:8px;bottom:70px;display:flex;flex-direction:column;align-items:center;gap:16px;z-index:9}
.tt-btn{display:flex;flex-direction:column;align-items:center;gap:2px}
.tt-btn svg{width:24px;height:24px;fill:#fff}
.tt-count{color:#fff;font-size:9px;font-family:var(--font-sans)}
.soundbar{position:absolute;bottom:24px;left:50%;transform:translateX(-50%);display:flex;align-items:flex-end;gap:3px}
.bar{width:4px;background:rgba(255,255,255,.5);border-radius:2px;animation:eq .6s ease-in-out infinite alternate}
.bar:nth-child(1){height:8px;animation-delay:0s}.bar:nth-child(2){height:14px;animation-delay:.1s}.bar:nth-child(3){height:20px;animation-delay:.2s}.bar:nth-child(4){height:12px;animation-delay:.3s}.bar:nth-child(5){height:18px;animation-delay:.15s}.bar:nth-child(6){height:8px;animation-delay:.05s}
@keyframes eq{from{transform:scaleY(1)}to{transform:scaleY(0.3)}}
.viral-badge{position:absolute;top:14px;left:12px;background:#ff2d55;color:#fff;font-size:10px;font-weight:700;font-family:var(--font-sans);padding:3px 8px;border-radius:20px;z-index:10}
.caption{position:absolute;bottom:92px;left:10px;right:44px;color:#fff;font-size:12px;font-weight:700;font-family:var(--font-sans);line-height:1.4;text-shadow:0 1px 6px rgba(0,0,0,.9)}
canvas{position:absolute;inset:0;pointer-events:none}

@keyframes pop{from{transform:scale(1)}to{transform:scale(1.12)}}
@keyframes float{0%,100%{transform:translateY(0) rotate(-5deg)}50%{transform:translateY(-12px) rotate(5deg)}}
@keyframes bounce{0%,100%{transform:translateY(0)}50%{transform:translateY(-8px)}}
@keyframes spin{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
@keyframes wiggle{0%,100%{transform:rotate(-8deg)}50%{transform:rotate(8deg)}}
@keyframes pulse{0%,100%{transform:scale(1)}50%{transform:scale(1.2)}}
@keyframes slideIn{from{transform:translateY(30px);opacity:0}to{transform:translateY(0);opacity:1}}

.star{position:absolute;font-size:16px;animation:float 2s ease-in-out infinite}
.kidchar{font-size:52px;animation:bounce 1s ease-in-out infinite}

.nb{padding:6px 20px;border-radius:20px;border:.5px solid var(--color-border-secondary);background:var(--color-background-secondary);color:var(--color-text-primary);font-size:13px;cursor:pointer;font-family:var(--font-sans);transition:background .15s}
.nb:hover{background:var(--color-background-tertiary)}
.scount{text-align:center;font-size:12px;color:var(--color-text-secondary);margin-top:8px;font-family:var(--font-sans)}

.qopt{width:100%;padding:10px 14px;border-radius:10px;border:1.5px solid rgba(255,255,255,.25);background:rgba(255,255,255,.08);color:#e0e7ff;font-size:12px;font-family:var(--font-sans);cursor:pointer;text-align:left;margin-bottom:8px;transition:background .2s}
.qopt:hover{background:rgba(255,255,255,.18)}
.qopt.ok{background:#166534;border-color:#4ade80;color:#bbf7d0}
.qopt.no{background:#7f1d1d;border-color:#f87171;color:#fecaca}
.res{color:#86efac;font-size:13px;font-weight:700;font-family:var(--font-sans);text-align:center;margin-top:8px;opacity:0;transition:opacity .4s}
.res.show{opacity:1}

.photo-placeholder{border-radius:10px;overflow:hidden;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;font-family:var(--font-sans);text-align:center;border:2px dashed rgba(255,255,255,.3)}
</style>

<h2 class="sr-only">TikTok-style mass transfer video for kids, 8 scenes with animations, kiddie characters, and viral elements</h2>

<div class="wrap">
  <div class="phone">
    <div class="screen">
      <div class="prog"><div class="prog-fill" id="pf" style="width:12.5%"></div></div>

      <!-- S0: HOOK -->
      <div class="scene active s0-bg" id="sc0" style="background:#1a0033">
        <canvas id="c0" width="300" height="620"></canvas>
        <div class="star" style="top:55px;left:22px;animation-delay:.3s">⭐</div>
        <div class="star" style="top:70px;right:28px;animation-delay:.8s">✨</div>
        <div class="star" style="top:160px;left:36px;animation-delay:1.3s">💫</div>
        <div style="position:absolute;top:80px;left:0;right:0;text-align:center">
          <div style="font-size:70px;animation:pop .7s infinite alternate">🤯</div>
        </div>
        <div style="position:absolute;top:190px;left:12px;right:12px;background:rgba(255,255,255,.12);border-radius:16px;padding:14px 12px;text-align:center;border:2px solid rgba(255,255,255,.2)">
          <div style="font-size:26px;margin-bottom:6px">👃❓</div>
          <div style="color:#fff;font-size:15px;font-weight:900;font-family:var(--font-sans);line-height:1.3">How does your nose smell cookies from another room?</div>
        </div>
        <div style="position:absolute;top:340px;left:12px;right:44px;display:flex;gap:8px">
          <div style="flex:1;background:rgba(255,200,0,.15);border-radius:12px;padding:8px;text-align:center;border:1.5px solid rgba(255,200,0,.3)">
            <div style="font-size:22px">🍪</div>
            <div style="color:#fde68a;font-size:10px;font-weight:700;font-family:var(--font-sans);margin-top:2px">kitchen</div>
          </div>
          <div style="flex:1;display:flex;align-items:center;justify-content:center;font-size:20px;color:#fff;font-weight:900;font-family:var(--font-sans)">→→→</div>
          <div style="flex:1;background:rgba(100,200,255,.15);border-radius:12px;padding:8px;text-align:center;border:1.5px solid rgba(100,200,255,.3)">
            <div style="font-size:22px">🧒</div>
            <div style="color:#7dd3fc;font-size:10px;font-weight:700;font-family:var(--font-sans);margin-top:2px">your room</div>
          </div>
        </div>
        <div style="position:absolute;top:430px;left:0;right:44px;text-align:center;color:#f9a8d4;font-size:13px;font-weight:700;font-family:var(--font-sans);animation:pulse 1s infinite">👇 keep watching!</div>
        <div class="viral-badge">🔥 trending</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div><div class="tt-tag">#learnontiktok #science #foryou</div></div>
        <div class="tt-side">
          <div class="tt-btn"><svg viewBox="0 0 24 24"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg><div class="tt-count">248K</div></div>
          <div class="tt-btn"><svg viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2z"/></svg><div class="tt-count">4.1K</div></div>
          <div class="tt-btn"><svg viewBox="0 0 24 24"><path d="M17 3H7c-1.1 0-2 .9-2 2v16l7-3 7 3V5c0-1.1-.9-2-2-2z"/></svg><div class="tt-count">89K</div></div>
        </div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S1: CROWDED→EMPTY (FIXED) -->
      <div class="scene" id="sc1" style="background:#001a33">
        <canvas id="c1" width="300" height="620"></canvas>
        <div style="position:absolute;top:52px;left:0;right:0;text-align:center">
          <div style="display:inline-flex;align-items:center;gap:8px;background:rgba(255,255,255,.1);border-radius:20px;padding:6px 16px;border:1.5px solid rgba(255,255,255,.2)">
            <div style="color:#fde68a;font-size:14px;font-weight:900;font-family:var(--font-sans)">CROWDED</div>
            <div style="color:#fff;font-size:16px">→</div>
            <div style="color:#7dd3fc;font-size:14px;font-weight:900;font-family:var(--font-sans)">EMPTY</div>
          </div>
        </div>
        <div style="position:absolute;top:110px;left:10px;right:44px;display:flex;gap:8px;align-items:stretch">
          <div style="flex:1;background:rgba(253,230,138,.12);border-radius:12px;padding:10px 8px;text-align:center;border:1.5px solid rgba(253,230,138,.35)">
            <div style="font-size:11px;font-weight:700;font-family:var(--font-sans);color:#fde68a;margin-bottom:6px">CROWDED 😵</div>
            <div style="display:flex;flex-wrap:wrap;gap:3px;justify-content:center">
              <span style="font-size:13px">😬</span><span style="font-size:13px">😬</span><span style="font-size:13px">😬</span>
              <span style="font-size:13px">😬</span><span style="font-size:13px">😬</span><span style="font-size:13px">😬</span>
              <span style="font-size:13px">😬</span><span style="font-size:13px">😬</span><span style="font-size:13px">😬</span>
            </div>
            <div style="color:rgba(253,230,138,.7);font-size:9px;font-family:var(--font-sans);margin-top:4px">too many molecules!</div>
          </div>
          <div style="display:flex;align-items:center;justify-content:center;padding:0 2px">
            <div style="color:#fff;font-size:18px;font-weight:900;font-family:var(--font-sans)">→</div>
          </div>
          <div style="flex:1;background:rgba(125,211,252,.1);border-radius:12px;padding:10px 8px;text-align:center;border:1.5px solid rgba(125,211,252,.3)">
            <div style="font-size:11px;font-weight:700;font-family:var(--font-sans);color:#7dd3fc;margin-bottom:6px">EMPTY 😌</div>
            <div style="display:flex;flex-wrap:wrap;gap:3px;justify-content:center">
              <span style="font-size:13px">😊</span>
              <span style="font-size:13px" style="opacity:.3"> </span>
              <span style="font-size:13px"> </span>
            </div>
            <div style="color:rgba(125,211,252,.7);font-size:9px;font-family:var(--font-sans);margin-top:4px">so much space!</div>
          </div>
        </div>
        <div style="position:absolute;top:268px;left:12px;right:44px;background:rgba(255,255,255,.08);border-radius:12px;padding:10px 12px;text-align:center">
          <div style="font-size:13px;margin-bottom:4px">🏫</div>
          <div style="color:#e0f2fe;font-size:11px;font-weight:700;font-family:var(--font-sans)">like kids rushing OUT of school</div>
          <div style="color:rgba(255,255,255,.5);font-size:10px;font-family:var(--font-sans);margin-top:2px">crowded classroom → empty playground</div>
        </div>
        <div style="position:absolute;top:350px;left:12px;right:44px">
          <div style="color:#fff;font-size:11px;font-weight:700;font-family:var(--font-sans);text-align:center;margin-bottom:6px">molecules do the SAME thing! 🎉</div>
          <div style="display:flex;justify-content:center;gap:6px">
            <div style="font-size:22px;animation:wiggle 1s infinite">🔵</div>
            <div style="font-size:22px;animation:wiggle 1s infinite;animation-delay:.2s">🔵</div>
            <div style="color:#fff;font-size:18px;font-weight:900;font-family:var(--font-sans);align-self:center">→→→</div>
            <div style="font-size:22px;animation:wiggle 1s infinite;animation-delay:.4s">🔵</div>
            <div style="font-size:22px;animation:float 2s infinite;animation-delay:.6s;opacity:.5">🔵</div>
          </div>
        </div>
        <div class="viral-badge">💡 big contrast words — fixed!</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S2: COOKIE EXAMPLE -->
      <div class="scene" id="sc2" style="background:#001a0d">
        <canvas id="c2" width="300" height="620"></canvas>
        <div style="position:absolute;top:44px;left:0;right:0;text-align:center">
          <div style="font-size:60px;animation:wiggle 1.2s infinite">🍪</div>
          <div style="color:#fde68a;font-size:13px;font-weight:900;font-family:var(--font-sans);margin-top:4px">HOT COOKIE!</div>
        </div>
        <div style="position:absolute;top:160px;left:0;right:44px;text-align:center">
          <div style="color:#86efac;font-size:22px;font-weight:900;font-family:var(--font-sans);letter-spacing:2px">↓↓↓↓↓</div>
          <div style="color:rgba(255,255,255,.6);font-size:10px;font-family:var(--font-sans)">gazillions of smell molecules fly out</div>
        </div>
        <div style="position:absolute;top:210px;left:12px;right:44px;display:flex;justify-content:space-around">
          <div style="text-align:center"><div style="font-size:18px;animation:float 1.5s infinite">🟡</div></div>
          <div style="text-align:center"><div style="font-size:18px;animation:float 1.5s infinite;animation-delay:.3s">🟡</div></div>
          <div style="text-align:center"><div style="font-size:18px;animation:float 1.5s infinite;animation-delay:.6s">🟡</div></div>
          <div style="text-align:center"><div style="font-size:18px;animation:float 1.5s infinite;animation-delay:.9s">🟡</div></div>
          <div style="text-align:center"><div style="font-size:18px;animation:float 1.5s infinite;animation-delay:1.2s">🟡</div></div>
        </div>
        <div style="position:absolute;top:265px;left:0;right:44px;text-align:center">
          <div style="color:#86efac;font-size:22px;font-weight:900;font-family:var(--font-sans);letter-spacing:2px">↓↓↓↓↓</div>
          <div style="color:rgba(255,255,255,.6);font-size:10px;font-family:var(--font-sans)">zoom through the whole house</div>
        </div>
        <div style="position:absolute;top:316px;left:0;right:0;text-align:center">
          <div style="font-size:56px;animation:bounce 1s infinite">🧒</div>
          <div style="font-size:26px;margin-top:-8px;animation:spin 1s linear infinite">😋</div>
          <div style="color:#fff;font-size:12px;font-weight:700;font-family:var(--font-sans);margin-top:2px">YUMMY DETECTED! 🎉</div>
        </div>
        <div style="position:absolute;top:430px;left:12px;right:44px;background:rgba(134,239,172,.12);border-radius:12px;padding:8px 12px;border:1.5px solid rgba(134,239,172,.3);text-align:center">
          <div style="color:#86efac;font-size:11px;font-weight:700;font-family:var(--font-sans)">this is called → DIFFUSION ✨</div>
        </div>
        <div class="viral-badge">🍪 viral element 2: food = views</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S3: THE SCIENCE WORD -->
      <div class="scene" id="sc3" style="background:#1a0a00">
        <canvas id="c3" width="300" height="620"></canvas>
        <div style="position:absolute;top:52px;left:0;right:0;text-align:center">
          <div style="color:#fde68a;font-size:11px;font-weight:700;font-family:var(--font-sans);letter-spacing:2px">the science word is…</div>
          <div style="color:#fff;font-size:46px;font-weight:900;font-family:var(--font-sans);margin-top:4px;animation:pop .8s infinite alternate">DIFFUSION</div>
          <div style="display:flex;justify-content:center;gap:5px;margin-top:8px;flex-wrap:wrap;padding:0 16px">
            <div style="background:#854F0B;color:#fde68a;font-size:10px;font-weight:700;font-family:var(--font-sans);padding:4px 10px;border-radius:20px">stuff moves 📦</div>
            <div style="background:#854F0B;color:#fde68a;font-size:10px;font-weight:700;font-family:var(--font-sans);padding:4px 10px;border-radius:20px">by itself 🤸</div>
            <div style="background:#854F0B;color:#fde68a;font-size:10px;font-weight:700;font-family:var(--font-sans);padding:4px 10px;border-radius:20px">crowded → empty 💨</div>
          </div>
        </div>
        <div style="position:absolute;top:218px;left:8px;right:44px;display:grid;grid-template-columns:1fr 1fr;gap:7px">
          <div style="background:rgba(255,255,255,.08);border-radius:12px;padding:9px 8px;text-align:center;border:1.5px solid rgba(255,255,255,.15)">
            <div style="font-size:28px">🫁</div>
            <div style="color:#fed7aa;font-size:10px;font-weight:700;font-family:var(--font-sans);margin-top:3px">your lungs</div>
            <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans);margin-top:2px">O₂ in → CO₂ out</div>
          </div>
          <div style="background:rgba(255,255,255,.08);border-radius:12px;padding:9px 8px;text-align:center;border:1.5px solid rgba(255,255,255,.15)">
            <div style="font-size:28px">☕</div>
            <div style="color:#fed7aa;font-size:10px;font-weight:700;font-family:var(--font-sans);margin-top:3px">coffee aroma</div>
            <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans);margin-top:2px">use real photo 📸</div>
          </div>
          <div style="background:rgba(255,255,255,.08);border-radius:12px;padding:9px 8px;text-align:center;border:1.5px solid rgba(255,255,255,.15)">
            <div style="font-size:28px">🌊</div>
            <div style="color:#fed7aa;font-size:10px;font-weight:700;font-family:var(--font-sans);margin-top:3px">ocean salt</div>
            <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans);margin-top:2px">use real photo 📸</div>
          </div>
          <div style="background:rgba(255,255,255,.08);border-radius:12px;padding:9px 8px;text-align:center;border:1.5px solid rgba(255,255,255,.15)">
            <div style="font-size:28px">🩸</div>
            <div style="color:#fed7aa;font-size:10px;font-weight:700;font-family:var(--font-sans);margin-top:3px">your blood</div>
            <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans);margin-top:2px">use real photo 📸</div>
          </div>
        </div>
        <div class="viral-badge">🧠 viral element 3: word reveal</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S4: LUNGS EXPLAINER (NEW) -->
      <div class="scene" id="sc4" style="background:#0a001a">
        <canvas id="c4" width="300" height="620"></canvas>
        <div style="position:absolute;top:42px;left:0;right:0;text-align:center">
          <div style="font-size:52px;animation:pulse 1.5s infinite">🫁</div>
          <div style="color:#c4b5fd;font-size:15px;font-weight:900;font-family:var(--font-sans);margin-top:4px">your body does this 60,000×/day!</div>
        </div>
        <div style="position:absolute;top:148px;left:10px;right:44px">
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:8px;background:rgba(59,130,246,.15);border-radius:12px;padding:8px 10px;border:1.5px solid rgba(59,130,246,.3)">
            <div style="font-size:24px;animation:bounce 1s infinite">😮‍💨</div>
            <div>
              <div style="color:#93c5fd;font-size:11px;font-weight:700;font-family:var(--font-sans)">breathe IN → oxygen enters blood</div>
              <div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:1px">O₂ is crowded in air → moves into blood</div>
            </div>
          </div>
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:8px;background:rgba(239,68,68,.12);border-radius:12px;padding:8px 10px;border:1.5px solid rgba(239,68,68,.25)">
            <div style="font-size:24px;animation:bounce 1s infinite;animation-delay:.3s">💨</div>
            <div>
              <div style="color:#fca5a5;font-size:11px;font-weight:700;font-family:var(--font-sans)">breathe OUT → CO₂ leaves blood</div>
              <div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:1px">CO₂ is crowded in blood → escapes to air</div>
            </div>
          </div>
          <div style="display:flex;align-items:center;gap:8px;background:rgba(236,72,153,.12);border-radius:12px;padding:8px 10px;border:1.5px solid rgba(236,72,153,.25)">
            <div style="font-size:24px;animation:pulse 1s infinite;animation-delay:.5s">🩸</div>
            <div>
              <div style="color:#f9a8d4;font-size:11px;font-weight:700;font-family:var(--font-sans)">blood carries O₂ to every cell</div>
              <div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:1px">your whole body runs on diffusion!</div>
            </div>
          </div>
        </div>
        <div style="position:absolute;top:376px;left:10px;right:44px;background:rgba(167,139,250,.12);border-radius:14px;padding:10px 12px;border:2px solid rgba(167,139,250,.3);text-align:center">
          <div style="color:#c4b5fd;font-size:12px;font-weight:700;font-family:var(--font-sans)">🤯 you are a walking mass-transfer machine!</div>
          <div style="display:flex;justify-content:center;gap:4px;margin-top:8px;font-size:26px">
            <span style="animation:bounce 1s infinite">🧒</span>
            <span style="animation:bounce 1s infinite;animation-delay:.2s">💨</span>
            <span style="animation:bounce 1s infinite;animation-delay:.4s">🔵</span>
            <span style="animation:bounce 1s infinite;animation-delay:.6s">❤️</span>
          </div>
        </div>
        <div class="viral-badge">🫁 bonus: body science = saves</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div><div class="tt-tag">#bodyscience #lungs #diffusion</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S5: QUIZ -->
      <div class="scene" id="sc5" style="background:#1a001a">
        <canvas id="c5" width="300" height="620"></canvas>
        <div style="width:100%;height:100%;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:16px">
          <div style="font-size:40px;margin-bottom:8px;animation:bounce 1s infinite">🧠</div>
          <div style="color:#fff;font-size:14px;font-weight:900;font-family:var(--font-sans);text-align:center;margin-bottom:14px;line-height:1.4;padding:0 4px">You spray perfume. The whole room smells nice. That's…?</div>
          <button class="qopt" onclick="ans(this,false)">A) Magic ✨</button>
          <button class="qopt" onclick="ans(this,true)">B) Diffusion — mass transfer! 💨</button>
          <button class="qopt" onclick="ans(this,false)">C) The perfume bottle is alive 🧴</button>
          <div class="res" id="qres">🎉 Drop a 💨 if you got it!</div>
        </div>
        <div class="viral-badge">🎮 viral element 4: comment bait</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div><div class="tt-tag">#quiz #drop 💨 below!</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S6: TYPES -->
      <div class="scene" id="sc6" style="background:#000d1a">
        <canvas id="c6" width="300" height="620"></canvas>
        <div style="position:absolute;top:44px;left:0;right:0;text-align:center">
          <div style="color:#7dd3fc;font-size:22px;font-weight:900;font-family:var(--font-sans)">MASS TRANSFER</div>
          <div style="color:rgba(255,255,255,.4);font-size:10px;font-family:var(--font-sans);margin-top:2px">= all the ways stuff moves around</div>
        </div>
        <div style="position:absolute;top:106px;left:10px;right:44px;display:flex;flex-direction:column;gap:8px">
          <div style="display:flex;align-items:center;gap:10px;background:rgba(56,132,205,.15);border-radius:12px;padding:10px 12px;border:1.5px solid rgba(56,132,205,.3)">
            <div style="font-size:28px;animation:float 2s infinite">💨</div>
            <div>
              <div style="color:#7dd3fc;font-size:12px;font-weight:700;font-family:var(--font-sans)">Diffusion</div>
              <div style="color:rgba(255,255,255,.55);font-size:10px;font-family:var(--font-sans)">molecules spread all by themselves</div>
            </div>
          </div>
          <div style="display:flex;align-items:center;gap:10px;background:rgba(15,110,86,.2);border-radius:12px;padding:10px 12px;border:1.5px solid rgba(29,158,117,.3)">
            <div style="font-size:28px;animation:spin 3s linear infinite">🌀</div>
            <div>
              <div style="color:#5DCAA5;font-size:12px;font-weight:700;font-family:var(--font-sans)">Convection</div>
              <div style="color:rgba(255,255,255,.55);font-size:10px;font-family:var(--font-sans)">wind or stirring helps them move</div>
            </div>
          </div>
          <div style="display:flex;align-items:center;gap:10px;background:rgba(83,74,183,.2);border-radius:12px;padding:10px 12px;border:1.5px solid rgba(127,119,221,.3)">
            <div style="font-size:28px;animation:wiggle 1.5s infinite">🧱</div>
            <div>
              <div style="color:#AFA9EC;font-size:12px;font-weight:700;font-family:var(--font-sans)">Permeation</div>
              <div style="color:rgba(255,255,255,.55);font-size:10px;font-family:var(--font-sans)">sneaking through tiny holes</div>
            </div>
          </div>
        </div>
        <div style="position:absolute;top:370px;left:10px;right:44px;background:rgba(255,255,255,.06);border-radius:12px;padding:10px;text-align:center;border:1px dashed rgba(255,255,255,.2)">
          <div style="color:#fde68a;font-size:11px;font-weight:700;font-family:var(--font-sans);margin-bottom:6px">spot them in real life! 🕵️</div>
          <div style="display:flex;justify-content:space-around">
            <div style="text-align:center"><div style="font-size:20px">🌊</div><div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:2px">ocean</div></div>
            <div style="text-align:center"><div style="font-size:20px">🫁</div><div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:2px">lungs</div></div>
            <div style="text-align:center"><div style="font-size:20px">☕</div><div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:2px">coffee</div></div>
            <div style="text-align:center"><div style="font-size:20px">🌸</div><div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:2px">flowers</div></div>
          </div>
        </div>
        <div class="viral-badge">📚 viral element 5: saveable list</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S7: HEAT FACT -->
      <div class="scene" id="sc7" style="background:#0d0d00">
        <canvas id="c7" width="300" height="620"></canvas>
        <div style="position:absolute;top:48px;left:0;right:0;text-align:center">
          <div style="font-size:50px;animation:bounce 1s infinite">🌡️</div>
          <div style="color:#fde68a;font-size:16px;font-weight:900;font-family:var(--font-sans);margin-top:4px">heat = FASTER molecules!</div>
        </div>
        <div style="position:absolute;top:158px;left:12px;right:44px">
          <div style="display:flex;align-items:flex-end;justify-content:space-between;background:rgba(255,255,255,.06);border-radius:12px;padding:10px 14px;height:90px">
            <div style="display:flex;flex-direction:column;align-items:center;gap:4px">
              <div style="width:20px;background:#378ADD;border-radius:3px;height:18px"></div>
              <div style="font-size:13px">🧊</div>
              <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans)">ice</div>
            </div>
            <div style="display:flex;flex-direction:column;align-items:center;gap:4px">
              <div style="width:20px;background:#1D9E75;border-radius:3px;height:34px"></div>
              <div style="font-size:13px">💧</div>
              <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans)">water</div>
            </div>
            <div style="display:flex;flex-direction:column;align-items:center;gap:4px">
              <div style="width:20px;background:#D85A30;border-radius:3px;height:52px;animation:eq .6s infinite alternate"></div>
              <div style="font-size:13px">♨️</div>
              <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans)">steam</div>
            </div>
            <div style="display:flex;flex-direction:column;align-items:center;gap:4px">
              <div style="width:20px;background:#E24B4A;border-radius:3px;height:62px;animation:eq .4s infinite alternate"></div>
              <div style="font-size:13px">🔥</div>
              <div style="color:rgba(255,255,255,.45);font-size:9px;font-family:var(--font-sans)">fire</div>
            </div>
          </div>
        </div>
        <div style="position:absolute;top:308px;left:12px;right:44px;background:rgba(253,230,138,.1);border-radius:12px;padding:10px 12px;border:1.5px solid rgba(253,230,138,.25);text-align:center">
          <div style="color:#fde68a;font-size:12px;font-weight:700;font-family:var(--font-sans)">hotter cookie = smells from farther away! 🤯</div>
        </div>
        <div style="position:absolute;top:368px;left:12px;right:44px;display:flex;justify-content:space-around">
          <div style="text-align:center;animation:float 2s infinite"><div style="font-size:30px">🐌</div><div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:2px">cold: slow</div></div>
          <div style="color:#fff;font-size:18px;align-self:center">→</div>
          <div style="text-align:center;animation:bounce .6s infinite"><div style="font-size:30px">🐇</div><div style="color:rgba(255,255,255,.5);font-size:9px;font-family:var(--font-sans);margin-top:2px">hot: fast!</div></div>
        </div>
        <div class="viral-badge">🌡️ viral element 6: surprising fact</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>

      <!-- S8: CTA -->
      <div class="scene" id="sc8" style="background:#1a000d">
        <canvas id="c8" width="300" height="620"></canvas>
        <div style="position:absolute;top:54px;left:0;right:0;text-align:center">
          <div style="display:flex;justify-content:center;gap:4px;font-size:36px;margin-bottom:8px">
            <span style="animation:bounce 1s infinite">🤯</span>
            <span style="animation:bounce 1s infinite;animation-delay:.15s">😱</span>
            <span style="animation:bounce 1s infinite;animation-delay:.3s">🧪</span>
            <span style="animation:bounce 1s infinite;animation-delay:.45s">🌟</span>
          </div>
          <div style="color:#f0abfc;font-size:18px;font-weight:900;font-family:var(--font-sans);line-height:1.3;padding:0 12px">your nose is a mass transfer detector!</div>
        </div>
        <div style="position:absolute;top:180px;left:10px;right:44px;display:flex;flex-direction:column;gap:8px">
          <div style="background:rgba(255,255,255,.1);border-radius:12px;padding:10px 12px;display:flex;align-items:center;gap:10px;border:1.5px solid rgba(255,255,255,.2)">
            <div style="font-size:22px;animation:bounce 1s infinite">💾</div>
            <div style="color:#fff;font-size:11px;font-weight:700;font-family:var(--font-sans)">Save to show your teacher</div>
          </div>
          <div style="background:rgba(255,255,255,.1);border-radius:12px;padding:10px 12px;display:flex;align-items:center;gap:10px;border:1.5px solid rgba(255,255,255,.2)">
            <div style="font-size:22px;animation:wiggle 1.5s infinite">💨</div>
            <div style="color:#fff;font-size:11px;font-weight:700;font-family:var(--font-sans)">Drop 💨 if you get it now</div>
          </div>
          <div style="background:rgba(255,255,255,.1);border-radius:12px;padding:10px 12px;display:flex;align-items:center;gap:10px;border:1.5px solid rgba(255,255,255,.2)">
            <div style="font-size:22px;animation:spin 3s linear infinite">🔁</div>
            <div style="color:#fff;font-size:11px;font-weight:700;font-family:var(--font-sans)">Send to a friend who hates science</div>
          </div>
          <div style="background:rgba(255,255,255,.1);border-radius:12px;padding:10px 12px;display:flex;align-items:center;gap:10px;border:1.5px solid rgba(255,255,255,.2)">
            <div style="font-size:22px;animation:float 2s infinite">🎵</div>
            <div style="color:#fff;font-size:11px;font-weight:700;font-family:var(--font-sans)">Duet with your teacher!</div>
          </div>
        </div>
        <div class="viral-badge">📣 viral element 7: multi-CTA</div>
        <div class="tt-ui"><div class="tt-handle">@sciencekid.lab</div><div class="tt-tag">#sciencetok #viral #foryoupage</div></div>
        <div class="soundbar"><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div><div class="bar"></div></div>
      </div>
    </div>
  </div>

  <div style="display:flex;flex-direction:column;gap:10px;max-width:280px;padding-top:8px">
    <div style="background:var(--color-background-secondary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:14px 16px">
      <div id="leg-badge" style="display:inline-block;background:#ff2d55;color:#fff;font-size:10px;font-weight:700;font-family:var(--font-sans);padding:3px 8px;border-radius:20px;margin-bottom:8px">Scene 1 of 9</div>
      <div id="leg-title" style="font-size:15px;font-weight:500;color:var(--color-text-primary);font-family:var(--font-sans);margin-bottom:4px">Hook — the mystery question</div>
      <div id="leg-desc" style="font-size:13px;color:var(--color-text-secondary);font-family:var(--font-sans);line-height:1.5">Opens with a relatable mystery kids already wonder about. Animated particles + trending badge trigger the "watch more" reflex within the first second.</div>
    </div>

    <div style="background:var(--color-background-secondary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:14px 16px">
      <div style="font-size:12px;font-weight:500;color:var(--color-text-primary);font-family:var(--font-sans);margin-bottom:8px">photo guidance for scene 4</div>
      <div id="photo-tip" style="font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans);line-height:1.6">
        ✅ <strong style="color:var(--color-text-primary)">Use real photos for:</strong> beach/ocean (salt dissolving), steaming coffee mug (aroma = diffusion), close-up of lungs diagram or X-ray.<br><br>
        ⚠️ <strong style="color:var(--color-text-primary)">For blood</strong> — skip the graphic photo. Use a red cell illustration or animated red blob instead. Kids + parents find blood photos off-putting and it hurts watch-time.<br><br>
        💡 <strong style="color:var(--color-text-primary)">Best combo:</strong> real photo with a semi-transparent overlay label (e.g. "DIFFUSION HAPPENING HERE →") keeps it educational without losing the visual punch.
      </div>
    </div>

    <div style="background:var(--color-background-secondary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:14px 16px">
      <div style="font-size:12px;font-weight:500;color:var(--color-text-primary);font-family:var(--font-sans);margin-bottom:8px">transition types used</div>
      <div style="display:flex;flex-direction:column;gap:6px">
        <div style="display:flex;align-items:center;gap:8px"><div style="width:8px;height:8px;border-radius:50%;background:#7dd3fc;flex-shrink:0"></div><div style="font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans)">Slide left/right (all scene changes)</div></div>
        <div style="display:flex;align-items:center;gap:8px"><div style="width:8px;height:8px;border-radius:50%;background:#86efac;flex-shrink:0"></div><div style="font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans)">Bounce — characters & CTA elements</div></div>
        <div style="display:flex;align-items:center;gap:8px"><div style="width:8px;height:8px;border-radius:50%;background:#fde68a;flex-shrink:0"></div><div style="font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans)">Float — molecules & stickers</div></div>
        <div style="display:flex;align-items:center;gap:8px"><div style="width:8px;height:8px;border-radius:50%;background:#f9a8d4;flex-shrink:0"></div><div style="font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans)">Wiggle — food & fun elements</div></div>
        <div style="display:flex;align-items:center;gap:8px"><div style="width:8px;height:8px;border-radius:50%;background:#fca5a5;flex-shrink:0"></div><div style="font-size:12px;color:var(--color-text-secondary);font-family:var(--font-sans)">Spin — convection & CTA icons</div></div>
      </div>
    </div>
  </div>
</div>

<div style="display:flex;justify-content:center;gap:10px;margin-top:1rem">
  <button class="nb" onclick="prev()">← Prev</button>
  <button class="nb" onclick="next()">Next →</button>
</div>
<div class="scount" id="sc">Scene 1 of 9 — Hook</div>

<script>
const TOTAL = 9;
const sceneData = [
  {title:'Hook — the mystery question', desc:'Opens with a relatable mystery kids already wonder about. Animated particles + trending badge trigger the "watch more" reflex within the first second.'},
  {title:'Crowded → empty (fixed!)', desc:'CROWDED and EMPTY now sit side-by-side in separate boxes — no overlap. Kid emoji faces + school analogy make the concept click instantly.'},
  {title:'The cookie example', desc:'Food visuals trigger dopamine. Giant wobbling cookie + bouncing kid + spinning yummy face tells the whole story without a word of reading.'},
  {title:'The science word — diffusion', desc:'Satisfying reveal + real-life icon grid. Coffee and ocean tiles are marked "use real photo" — swap the emoji tile with your actual photo here.'},
  {title:'Lungs & blood explainer', desc:'NEW scene: explains how diffusion keeps you alive. O₂ in, CO₂ out — shown with kid-friendly icons. Use a lung diagram or X-ray photo here, skip graphic blood photos.'},
  {title:'Interactive quiz', desc:'Forces a choice — their comment drives the algorithm. "Drop 💨 if you got it" is a proven comment-flood mechanic.'},
  {title:'Mass transfer types', desc:'Saveable 3-row list. Screenshots = saves = strongest algorithmic signal on TikTok.'},
  {title:'Heat = faster molecules', desc:'Snail vs rabbit animation shows the idea without any reading. Surprising fact format reliably generates "wait, really?!" comments.'},
  {title:'CTA + outro', desc:'4 specific CTAs with bouncing icons. Duet CTA brings the creator into other accounts\' feeds for extra reach.'},
];
let cur = 0;

function cfgCanvas(id,count,speed,colors){
  const cv=document.getElementById(id);
  if(!cv)return;
  const ctx=cv.getContext('2d'),W=cv.width,H=cv.height,pts=[];
  for(let i=0;i<count;i++) pts.push({x:Math.random()*W,y:Math.random()*H,vx:(Math.random()-.5)*speed,vy:(Math.random()-.5)*speed,r:2+Math.random()*3,c:colors[Math.floor(Math.random()*colors.length)]});
  (function loop(){ctx.clearRect(0,0,W,H);for(const p of pts){p.x+=p.vx;p.y+=p.vy;if(p.x<0||p.x>W)p.vx*=-1;if(p.y<0||p.y>H)p.vy*=-1;ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);ctx.fillStyle=p.c;ctx.fill();}requestAnimationFrame(loop);})();
}

cfgCanvas('c0',60,1.2,['rgba(179,136,255,.65)','rgba(100,100,255,.45)','rgba(255,255,255,.25)']);
cfgCanvas('c1',80,1.5,['rgba(253,230,138,.55)','rgba(125,211,252,.45)','rgba(255,255,255,.2)']);
cfgCanvas('c2',50,0.9,['rgba(253,230,138,.6)','rgba(134,239,172,.45)','rgba(255,255,255,.2)']);
cfgCanvas('c3',40,1.0,['rgba(253,186,116,.55)','rgba(252,165,165,.45)']);
cfgCanvas('c4',45,0.8,['rgba(196,181,253,.55)','rgba(249,168,212,.45)','rgba(255,255,255,.2)']);
cfgCanvas('c5',55,0.9,['rgba(240,171,252,.55)','rgba(196,181,253,.45)','rgba(255,255,255,.2)']);
cfgCanvas('c6',50,0.9,['rgba(125,211,252,.5)','rgba(93,202,165,.45)','rgba(175,169,236,.45)']);
cfgCanvas('c7',38,1.8,['rgba(253,230,138,.65)','rgba(239,159,39,.55)','rgba(226,75,74,.45)']);
cfgCanvas('c8',55,0.7,['rgba(240,171,252,.55)','rgba(196,181,253,.45)','rgba(255,255,255,.2)']);

function showScene(n, dir){
  const all = document.querySelectorAll('.scene');
  const prev_el = document.getElementById('sc'+cur);
  const next_el = document.getElementById('sc'+n);
  if(prev_el){
    prev_el.style.transition='opacity .38s ease, transform .38s cubic-bezier(.4,0,.2,1)';
    prev_el.style.opacity='0';
    prev_el.style.transform = dir>0 ? 'translateX(-100%)' : 'translateX(100%)';
    prev_el.classList.remove('active');
    setTimeout(()=>{prev_el.style.transform='translateX(100%)';prev_el.style.transition='none';},420);
  }
  if(next_el){
    next_el.style.transition='none';
    next_el.style.opacity='0';
    next_el.style.transform = dir>0 ? 'translateX(100%)' : 'translateX(-100%)';
    next_el.classList.add('active');
    next_el.style.pointerEvents='all';
    setTimeout(()=>{
      next_el.style.transition='opacity .38s ease, transform .38s cubic-bezier(.4,0,.2,1)';
      next_el.style.opacity='1';
      next_el.style.transform='translateX(0)';
    },20);
  }
  cur=n;
  document.getElementById('pf').style.width=Math.round(((n+1)/TOTAL)*100)+'%';
  document.getElementById('sc').textContent='Scene '+(n+1)+' of '+TOTAL+' — '+sceneData[n].title;
  document.getElementById('leg-badge').textContent='Scene '+(n+1)+' of '+TOTAL;
  document.getElementById('leg-title').textContent=sceneData[n].title;
  document.getElementById('leg-desc').textContent=sceneData[n].desc;
}

function next(){if(cur<TOTAL-1)showScene(cur+1,1)}
function prev(){if(cur>0)showScene(cur-1,-1)}

function ans(btn,ok){
  document.querySelectorAll('.qopt').forEach(b=>b.onclick=null);
  btn.classList.add(ok?'ok':'no');
  if(!ok)document.querySelectorAll('.qopt')[1].classList.add('ok');
  const r=document.getElementById('qres');
  r.textContent=ok?'🎉 Drop a 💨 if you got it!':'😅 It\'s diffusion — molecules spread!';
  r.classList.add('show');
}
</script>
