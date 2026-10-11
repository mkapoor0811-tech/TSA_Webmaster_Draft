const soundEngine = {
  ctx: null,
  init() {
    if (!this.ctx) {
      this.ctx = new (window.AudioContext || window.webkitAudioContext)();
    }
  },
  playTone(freq, type, duration) {
    try {
      this.init();
      if (this.ctx.state === "suspended") this.ctx.resume();
      const osc = this.ctx.createOscillator();
      const gain = this.ctx.createGain();
      osc.type = type;
      osc.frequency.setValueAtTime(freq, this.ctx.currentTime);
      gain.gain.setValueAtTime(0.04, this.ctx.currentTime);
      gain.gain.exponentialRampToValueAtTime(0.001, this.ctx.currentTime + duration);
      osc.connect(gain);
      gain.connect(this.ctx.destination);
      osc.start();
      osc.stop(this.ctx.currentTime + duration);
    } catch (e) {}
  },
  click() { this.playTone(400, "triangle", 0.08); },
  fanfare() {
    setTimeout(() => this.playTone(523.25, "sine", 0.15), 0);
    setTimeout(() => this.playTone(659.25, "sine", 0.20), 100);
    setTimeout(() => this.playTone(783.99, "sine", 0.35), 200);
  }
};

const app = {
  state: {
    xp: 0,
    level: 1,
    nodes: [false, false, false, false],
    quizzes: [false, false, false, false, false],
    bossDefeated: false
  },

  quizData: [
    { correct: 0, exp: "Correct! The bias shifts the decision threshold independently of inputs." },
    { correct: 1, exp: "Correct! Orthogonal vectors have a dot product of 0, meaning zero directional correlation." },
    { correct: 0, exp: "Correct! Dividing by sqrt(d_k) prevents large dot products from causing vanishing gradients in softmax." },
    { correct: 0, exp: "Correct! 42 / 70 = 60%, which is below the 80% federal limit and shows adverse impact." },
    { correct: 0, exp: "Correct! Systems that affect student educational opportunities are classified as High Risk." }
  ],

  init() {
    try {
      const saved = localStorage.getItem("nexus_citadel_state_clean_v3");
      if (saved) this.state = JSON.parse(saved);
    } catch (e) {
      console.warn("Storage fallback initiated", e);
    }
    this.sync();
  },

  save() {
    try {
      localStorage.setItem("nexus_citadel_state_clean_v3", JSON.stringify(this.state));
    } catch (e) {
      console.warn("Storage write failure", e);
    }
  },

  nav(tabId) {
    soundEngine.click();
    document.querySelectorAll(".tab-page").forEach(p => p.classList.remove("active"));
    document.querySelectorAll(".nav-btn").forEach(b => b.classList.remove("active"));
    const page = document.getElementById("tab-" + tabId);
    if (page) page.classList.add("active");
    const btn = document.querySelector(`.nav-btn[data-tab="${tabId}"]`);
    if (btn) btn.classList.add("active");
    window.scrollTo({ top: 0, behavior: "smooth" });

    if (tabId === "dragon") {
      dragonBossRaid.checkUnlock();
    }
  },

  collectCore(idx) {
    if (this.state.nodes[idx]) return;
    soundEngine.fanfare();
    this.state.nodes[idx] = true;
    this.state.xp = Math.min(1000, this.state.xp + 50);
    this.save();
    this.sync();

    const banner = document.getElementById("coreBanner" + idx);
    if (banner) {
      banner.classList.add("collected");
      banner.innerHTML = `
        <div class="core-glyph">✓</div>
        <div>
          <strong>Archon Rune ${idx + 1} Captured!</strong>
          <small>Tensor node checkpoint secured in vault (+50 XP)</small>
        </div>
      `;
    }
  },

  quiz(idx, pick, btn) {
    const data = this.quizData[idx];
    const fb = document.getElementById("qfb" + idx);
    const parent = btn.parentElement;
    parent.querySelectorAll("button").forEach(b => b.disabled = true);

    if (pick === data.correct) {
      soundEngine.fanfare();
      btn.classList.add("correct");
      fb.style.color = "#6ee7b7";
      fb.textContent = "✓ " + data.exp;

      if (!this.state.quizzes[idx]) {
        this.state.quizzes[idx] = true;
        this.state.xp = Math.min(1000, this.state.xp + 160);
        this.save();
        this.sync();
      }
    } else {
      soundEngine.click();
      btn.classList.add("wrong");
      parent.children[data.correct].classList.add("correct");
      fb.style.color = "#fca5a5";
      fb.textContent = "Review: " + data.exp;
    }
  },

  sync() {
    this.state.level = this.state.xp >= 750 ? 4 : this.state.xp >= 500 ? 3 : this.state.xp >= 250 ? 2 : 1;
    document.getElementById("hudXp").textContent = this.state.xp;
    document.getElementById("hubScoreVal").textContent = this.state.xp;
    document.getElementById("hubLvlVal").textContent = this.state.level;
    document.getElementById("hubFillBar").style.width = (this.state.xp / 10) + "%";

    const collectedCount = this.state.nodes.filter(Boolean).length;
    document.getElementById("coreCounter").textContent = `${collectedCount}/4 RUNES`;

    for (let i = 0; i < 4; i++) {
      const comp = document.getElementById("comp" + i);
      if (comp) {
        comp.textContent = this.state.quizzes[i] ? "100% Verified" : "0%";
        comp.style.color = this.state.quizzes[i] ? "#d97706" : "#94a3b8";
      }
    }

    const diploma = document.getElementById("diplomaBanner");
    if (diploma) diploma.style.display = this.state.xp >= 1000 ? "flex" : "none";

    dragonBossRaid.checkUnlock();
  },

  judgePass() {
    soundEngine.fanfare();
    this.state = {
      xp: 1000,
      level: 4,
      nodes: [true, true, true, true],
      quizzes: [true, true, true, true, true],
      bossDefeated: true
    };
    this.save();
    this.sync();
  },

  reset() {
    if (confirm("Reset Citadel workshop progress?")) {
      this.state = {
        xp: 0,
        level: 1,
        nodes: [false, false, false, false],
        quizzes: [false, false, false, false, false],
        bossDefeated: false
      };
      this.save();
      location.reload();
    }
  }
};

const companion = {
  speak(who) {
    soundEngine.click();
    const princeLines = [
      "Check out Figure 1.2 below to trace how a perceptron sums inputs before step activation!",
      "If learning rate alpha is too high in Figure 3.2, gradients overshoot the loss bowl into divergence.",
      "The dot product calculates cosine similarity between word vectors."
    ];
    const princessLines = [
      "In Figure 2.1, notice how adding and subtracting vectors moves meanings geometrically across the plane!",
      "Review the C.R.A.F.T. matrix in Figure 2.2 before prompt engineering; constraints keep models factual.",
      "Always check paper DOIs on real databases before citing AI summaries."
    ];

    if (who === "prince") {
      const text = princeLines[Math.floor(Math.random() * princeLines.length)];
      document.getElementById("princeSpeech").innerHTML = `<strong>Prince Valen:</strong> "${text}"`;
    } else {
      const text = princessLines[Math.floor(Math.random() * princessLines.length)];
      document.getElementById("princessSpeech").innerHTML = `<strong>Princess Aurelia:</strong> "${text}"`;
    }
  },

  track(e) {
    const pl = document.getElementById("princeEyeL");
    const pr = document.getElementById("princeEyeR");
    const al = document.getElementById("princessEyeL");
    const ar = document.getElementById("princessEyeR");
    if (!pl || !pr || !al || !ar) return;

    const r1 = pl.getBoundingClientRect();
    const a1 = Math.atan2(e.clientY - r1.top, e.clientX - r1.left);
    pl.setAttribute("cx", 43 + Math.cos(a1) * 1.5);
    pl.setAttribute("cy", 44 + Math.sin(a1) * 1.5);
    pr.setAttribute("cx", 57 + Math.cos(a1) * 1.5);
    pr.setAttribute("cy", 44 + Math.sin(a1) * 1.5);

    const r2 = al.getBoundingClientRect();
    const a2 = Math.atan2(e.clientY - r2.top, e.clientX - r2.left);
    al.setAttribute("cx", 43 + Math.cos(a2) * 1.5);
    al.setAttribute("cy", 44 + Math.sin(a2) * 1.5);
    ar.setAttribute("cx", 57 + Math.cos(a2) * 1.5);
    ar.setAttribute("cy", 44 + Math.sin(a2) * 1.5);
  }
};

const govBench = {
  controls: [
    { title: "1. Training Data Provenance & Lineage", desc: "Auditors verify data collection licenses, scrub student identifiers under FERPA guidelines, and check representation ratios across demographic groups to prevent baked-in historical bias." },
    { title: "2. Model Card & Architectural Disclosure", desc: "Standardized documentation detailing intended use cases, known failure boundaries, training hyperparameters, evaluation benchmarks, and ethical limitations per NIST AI RMF." },
    { title: "3. Adversarial Red-Teaming & Stress Tests", desc: "Security teams execute prompt injection attacks, jailbreak simulations, and adversarial tests to verify safety guardrails before deploying software in schools." },
    { title: "4. Telemetry Drift & Continuous Auditing", desc: "Real-time production monitoring tracking concept drift, prediction variance, disparate impact shifts, and maintaining active counselor override controls." }
  ],
  inspect(idx) {
    soundEngine.click();
    document.querySelectorAll(".btn-pipeline").forEach((b, i) => b.classList.toggle("active", i === idx));
    const data = this.controls[idx];
    document.getElementById("govPipeTitle").textContent = data.title;
    document.getElementById("govPipeDesc").textContent = data.desc;
  }
};

const tier1Bench = {
  update() {
    const x = parseInt(document.getElementById("sliderB1X").value) / 10;
    const w = parseInt(document.getElementById("sliderB1W").value) / 10;
    const b = parseInt(document.getElementById("sliderB1B").value) / 10;

    document.getElementById("lblB1X").textContent = x.toFixed(1);
    document.getElementById("lblB1W").textContent = w.toFixed(1);
    document.getElementById("lblB1B").textContent = b.toFixed(1);

    const sum = (w * x) + b;
    const fired = sum > 0;

    document.getElementById("b1Sum").textContent = sum.toFixed(2);
    const outEl = document.getElementById("b1Output");
    const expEl = document.getElementById("b1Explanation");
    const statusEl = document.getElementById("b1Status");

    if (fired) {
      outEl.textContent = "FIRED (1.0)";
      outEl.style.color = "#059669";
      statusEl.textContent = "STATE: ACTIVE";
      statusEl.style.color = "#059669";
      expEl.textContent = "Neuron fired. Affine calculation exceeds zero threshold.";
    } else {
      outEl.textContent = "SUPPRESSED (0.0)";
      outEl.style.color = "#dc2626";
      statusEl.textContent = "STATE: INACTIVE";
      statusEl.style.color = "#dc2626";
      expEl.textContent = "Neuron suppressed. Affine sum is below zero threshold.";
    }
  }
};

const vectorExplorer = {
  canvas: document.getElementById("vectorCanvas"),
  ctx: null,
  words: [
    { label: "King", x: 300, y: 65, color: "#38bdf8" },
    { label: "Queen", x: 280, y: 90, color: "#a855f7" },
    { label: "Man", x: 190, y: 145, color: "#0284c7" },
    { label: "Woman", x: 170, y: 170, color: "#ec4899" },
    { label: "Citadel", x: 90, y: 70, color: "#d97706" }
  ],
  dragged: null,

  init() {
    if (!this.canvas) return;
    this.ctx = this.canvas.getContext("2d");

    this.canvas.addEventListener("mousedown", e => {
      const r = this.canvas.getBoundingClientRect();
      const mx = e.clientX - r.left, my = e.clientY - r.top;
      this.words.forEach(w => {
        if (Math.hypot(w.x - mx, w.y - my) < 18) this.dragged = w;
      });
    });

    window.addEventListener("mousemove", e => {
      if (!this.dragged) return;
      const r = this.canvas.getBoundingClientRect();
      this.dragged.x = Math.max(20, Math.min(this.canvas.width - 20, e.clientX - r.left));
      this.dragged.y = Math.max(20, Math.min(this.canvas.height - 20, e.clientY - r.top));
      this.calc();
    });

    window.addEventListener("mouseup", () => { this.dragged = null; });
    this.animate();
    this.calc();
  },

  calc() {
    const k = this.words[0], q = this.words[1];
    document.getElementById("vLblA").textContent = `${k.label} [${(k.x/460).toFixed(2)}, ${(1 - k.y/230).toFixed(2)}]`;
    document.getElementById("vLblB").textContent = `${q.label} [${(q.x/460).toFixed(2)}, ${(1 - q.y/230).toFixed(2)}]`;

    const ox = 20, oy = 210;
    const ax = k.x - ox, ay = oy - k.y;
    const bx = q.x - ox, by = oy - q.y;
    const dot = (ax * bx) + (ay * by);
    const mag = Math.hypot(ax, ay) * Math.hypot(bx, by);
    const sim = mag ? Math.max(0, Math.min(1, dot / mag)) : 0;
    document.getElementById("vSimVal").textContent = sim.toFixed(3);
  },

  snapAnalogy() {
    soundEngine.fanfare();
    const k = this.words[0], m = this.words[2], w = this.words[3], q = this.words[1];
    q.x = Math.round(k.x - m.x + w.x);
    q.y = Math.round(k.y - m.y + w.y);
    this.calc();
    document.getElementById("vStatusTxt").textContent = "Solved! Geometric vector displacement snapped Queen to coordinate position.";
  },

  animate() {
    this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
    const ox = 20, oy = 210;

    this.ctx.strokeStyle = "rgba(217, 119, 6, 0.25)";
    this.ctx.beginPath();
    this.ctx.moveTo(ox, 10);
    this.ctx.lineTo(ox, oy);
    this.ctx.lineTo(450, oy);
    this.ctx.stroke();

    this.words.forEach(w => {
      this.ctx.beginPath();
      this.ctx.moveTo(ox, oy);
      this.ctx.lineTo(w.x, w.y);
      this.ctx.strokeStyle = w.color + "55";
      this.ctx.stroke();

      this.ctx.beginPath();
      this.ctx.arc(w.x, w.y, 6, 0, Math.PI * 2);
      this.ctx.fillStyle = w.color;
      this.ctx.fill();

      this.ctx.fillStyle = "#ffffff";
      this.ctx.font = "11px monospace";
      this.ctx.fillText(w.label, w.x + 8, w.y + 4);
    });

    requestAnimationFrame(() => this.animate());
  }
};

const gradientLab = {
  canvas: document.getElementById("lossCanvas"),
  ctx: null,
  weight: 3.2,
  learningRate: 0.20,

  init() {
    if (!this.canvas) return;
    this.ctx = this.canvas.getContext("2d");
    this.render();
  },

  setRate(val) {
    this.learningRate = val / 100;
    const label = document.getElementById("lrLabel");
    if (this.learningRate > 0.8) {
      label.textContent = `${this.learningRate.toFixed(2)} (Exploding Gradient Danger)`;
      label.style.color = "#dc2626";
    } else {
      label.textContent = `${this.learningRate.toFixed(2)} (Optimal Convergence)`;
      label.style.color = "#059669";
    }
  },

  step() {
    soundEngine.click();
    const deriv = 2 * this.weight;
    this.weight = this.weight - (this.learningRate * deriv);
    if (Math.abs(this.weight) > 4.5) {
      this.weight = Math.sign(this.weight) * 4.4;
    } else if (Math.abs(this.weight) < 0.05) {
      soundEngine.fanfare();
    }
    this.render();
  },

  reset() {
    soundEngine.click();
    this.weight = 3.2;
    this.render();
  },

  render() {
    this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
    const cx = this.canvas.width / 2;
    const cy = this.canvas.height - 30;

    this.ctx.beginPath();
    this.ctx.strokeStyle = "rgba(217, 119, 6, 0.4)";
    this.ctx.lineWidth = 2.5;
    for (let x = -4; x <= 4; x += 0.1) {
      const px = cx + (x * 45);
      const py = cy - (Math.pow(x, 2) * 8.5);
      if (x === -4) this.ctx.moveTo(px, py);
      else this.ctx.lineTo(px, py);
    }
    this.ctx.stroke();

    const marbleX = cx + (this.weight * 45);
    const marbleY = cy - (Math.pow(this.weight, 2) * 8.5);
    const deriv = 2 * this.weight;

    this.ctx.beginPath();
    this.ctx.strokeStyle = "#f59e0b";
    this.ctx.lineWidth = 1.5;
    this.ctx.moveTo(marbleX - 25, marbleY + (deriv * 3.5));
    this.ctx.lineTo(marbleX + 25, marbleY - (deriv * 3.5));
    this.ctx.stroke();

    this.ctx.beginPath();
    this.ctx.arc(marbleX, marbleY, 7, 0, Math.PI * 2);
    this.ctx.fillStyle = "#dc2626";
    this.ctx.fill();
    this.ctx.strokeStyle = "#ffffff";
    this.ctx.lineWidth = 1.5;
    this.ctx.stroke();

    document.getElementById("gradWeight").textContent = this.weight.toFixed(3);
    document.getElementById("gradDeriv").textContent = deriv.toFixed(3);
    document.getElementById("gradLoss").textContent = Math.pow(this.weight, 2).toFixed(3);
  }
};

const confusionMatrixLab = {
  update(rawVal) {
    const cutoff = parseInt(rawVal) / 100;
    document.getElementById("cmThresholdLbl").textContent = cutoff.toFixed(2);

    const tp = Math.round(110 * (1 - cutoff * 0.65));
    const fp = Math.round(65 * Math.pow(1 - cutoff, 1.4));
    const fn = Math.round(110 - tp);
    const tn = Math.round(120 - fp);

    document.getElementById("cmTP").textContent = tp;
    document.getElementById("cmFP").textContent = fp;
    document.getElementById("cmFN").textContent = fn;
    document.getElementById("cmTN").textContent = tn;

    const rateA = 0.70;
    const rateB = (tp + fp) > 0 ? ((tp * 0.55 + fp * 0.8) / 150) : 0.05;
    const ratio = Math.min(100, Math.max(15, (rateB / rateA) * 100));

    const ratioEl = document.getElementById("cmAdverseRatio");
    const legalEl = document.getElementById("cmLegalStatus");
    const recEl = document.getElementById("cmPolicyRecommendation");
    const verdictEl = document.getElementById("cmVerdict");

    ratioEl.textContent = ratio.toFixed(1) + "%";

    if (cutoff < 0.35) {
      verdictEl.textContent = "THRESHOLD: LOW (AGGRESSIVE ALERTS)";
    } else if (cutoff > 0.65) {
      verdictEl.textContent = "THRESHOLD: HIGH (MINIMAL FALSE ALARMS)";
    } else {
      verdictEl.textContent = "THRESHOLD: 0.50 (STANDARD BALANCE)";
    }

    if (ratio < 80.0) {
      legalEl.textContent = "VIOLATES 80% FOUR-FIFTHS RULE";
      legalEl.style.color = "#dc2626";
      recEl.textContent = `Discriminatory adverse impact detected (${ratio.toFixed(1)}%). Lowering cutoff reduces missed students but flags Group B with false positive deficit stigmas.`;
    } else {
      legalEl.textContent = "SATISFIES 80% PARITY THRESHOLD";
      legalEl.style.color = "#059669";
      recEl.textContent = `Regulatory compliance achieved (${ratio.toFixed(1)}%). Selection distribution satisfies EEOC adverse impact thresholds.`;
    }
  }
};

const dragonBossRaid = {
  canvas: document.getElementById("bossCombatCanvas"),
  ctx: null,
  bossHp: 100,
  playerHp: 100,
  currentRound: 0,
  questions: [
    {
      attackName: "Stochastic Hallucination Fireball",
      bossDesc: "Ignis breathes synthetic academic citations with completely fabricated author names and fake DOIs!",
      question: "Which verification step should the Dino Mech execute to catch this hallucination?",
      choices: [
        { text: "Look up the paper title or DOI in PubMed or Google Scholar to confirm it physically exists", correct: true },
        { text: "Copy the synthetic bibliography directly into the paper without checking", correct: false },
        { text: "Ask Ignis if he is confident in his references", correct: false }
      ],
      winLog: "✓ Direct Hit! PubMed verification unmasked the fake DOI. Dino Plasma Cannon dealt 34 damage!"
    },
    {
      attackName: "Exploding Gradient Conflagration",
      bossDesc: "Ignis sets the learning rate to 2.5, causing parameter updates to oscillate wildly into infinity!",
      question: "What mathematical adjustment will stabilize the Dino Mech's descent curve?",
      choices: [
        { text: "Apply learning rate decay and gradient clipping to stabilize the weight updates", correct: true },
        { text: "Double the learning rate to 5.0 to finish training faster", correct: false },
        { text: "Delete the loss function from memory", correct: false }
      ],
      winLog: "✓ Critical Defense! Gradient clipping stabilized the curve. Dino Tail Strike dealt 34 damage!"
    },
    {
      attackName: "Proxy Variable Infernal Trap",
      bossDesc: "Ignis deploys an attendance model claiming zero bias, but relying heavily on student home ZIP codes!",
      question: "How does the four-fifths rule catch this disguised demographic bias?",
      choices: [
        { text: "It divides Group B's pass rate by Group A's pass rate to detect adverse impact below 80%", correct: true },
        { text: "It automatically deletes all student discipline records", correct: false },
        { text: "It assumes models are fair as long as race is omitted from the table", correct: false }
      ],
      winLog: "✓ Victory Strike! The Four-Fifths audit stripped the proxy bias. Ignis has been subdued!"
    }
  ],

  checkUnlock() {
    const isReady = app.state.xp >= 600 || app.state.level >= 3;
    const lockedEl = document.getElementById("dragonLockedCard");
    const arenaEl = document.getElementById("dragonUnlockedArena");
    const statusEl = document.getElementById("portalDragonStatus");

    if (isReady) {
      if (lockedEl) lockedEl.style.display = "none";
      if (arenaEl) arenaEl.style.display = "block";
      if (statusEl) statusEl.textContent = "⚔️ Arena Unlocked!";
      this.init();
    } else {
      if (lockedEl) lockedEl.style.display = "block";
      if (arenaEl) arenaEl.style.display = "none";
      if (statusEl) statusEl.textContent = "🔒 Complete Modules to Unlock";
    }
  },

  init() {
    if (!this.canvas) return;
    this.ctx = this.canvas.getContext("2d");
    this.loadRound();
    this.drawArena();
  },

  loadRound() {
    if (this.currentRound >= this.questions.length) {
      this.victory();
      return;
    }
    const qData = this.questions[this.currentRound];
    document.getElementById("bossIncomingMove").textContent = `Ignis attacks with: ${qData.attackName}!`;
    document.getElementById("bossMoveDescription").textContent = qData.bossDesc;
    document.getElementById("questionPromptHeading").textContent = qData.question;

    const grid = document.getElementById("combatTacticsGrid");
    grid.innerHTML = "";
    qData.choices.forEach(c => {
      const btn = document.createElement("button");
      btn.type = "button";
      btn.className = "tactical-btn";
      btn.textContent = c.text;
      btn.onclick = () => this.handleAnswer(c.correct, qData.winLog);
      grid.appendChild(btn);
    });
  },

  handleAnswer(isCorrect, winLogText) {
    const log = document.getElementById("combatLogBox");
    if (isCorrect) {
      soundEngine.fanfare();
      this.bossHp = Math.max(0, this.bossHp - 34);
      document.getElementById("bossHpFill").style.width = this.bossHp + "%";
      document.getElementById("bossHpText").textContent = `${this.bossHp} / 100`;
      log.innerHTML = `<p style="color: #6ee7b7;">${winLogText}</p>`;
      this.currentRound++;
      setTimeout(() => this.loadRound(), 800);
    } else {
      soundEngine.click();
      this.playerHp = Math.max(0, this.playerHp - 25);
      document.getElementById("playerHpFill").style.width = this.playerHp + "%";
      document.getElementById("playerHpText").textContent = `${this.playerHp} / 100`;
      log.innerHTML = `<p style="color: #fca5a5;">❌ Incorrect answer! Ignis hit the Dino Mech for 25 damage. Review your concepts and choose again!</p>`;
      if (this.playerHp <= 0) {
        log.innerHTML = `<p style="color: #ef4444;">⚠️ Dino Mech energy depleted! Resetting round health...</p>`;
        this.playerHp = 100;
        document.getElementById("playerHpFill").style.width = "100%";
        document.getElementById("playerHpText").textContent = "100 / 100";
      }
    }
  },

  victory() {
    soundEngine.fanfare();
    document.getElementById("bossIncomingMove").textContent = "ARENA VICTORY: IGNIS IS SUBDUED!";
    document.getElementById("bossMoveDescription").textContent = "You demonstrated mastery over ML mathematics, prompt calibration, and algorithmic governance.";
    document.getElementById("questionPromptHeading").textContent = "All challenges completed!";
    document.getElementById("combatTacticsGrid").innerHTML = "<button class='btn-royal-gold' onclick='app.nav(\"hub\")'>View Verified Portfolio →</button>";
    document.getElementById("combatLogBox").innerHTML = "<p style='color: #fbbf24;'>Bonus +150 XP Awarded! All competencies verified.</p>";
    app.state.bossDefeated = true;
    app.state.xp = Math.min(1000, app.state.xp + 150);
    app.save();
    app.sync();
  },

  drawArena() {
    this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);

    this.ctx.strokeStyle = "#334155";
    this.ctx.lineWidth = 2;
    this.ctx.beginPath();
    this.ctx.moveTo(0, 185);
    this.ctx.lineTo(this.canvas.width, 185);
    this.ctx.stroke();

    this.ctx.fillStyle = "#0284c7";
    this.ctx.beginPath();
    this.ctx.ellipse(120, 145, 34, 22, 0, 0, Math.PI * 2);
    this.ctx.fill();

    this.ctx.beginPath();
    this.ctx.arc(150, 128, 14, 0, Math.PI * 2);
    this.ctx.fill();
    this.ctx.fillStyle = "#fef08a";
    this.ctx.fillRect(152, 124, 4, 4);

    this.ctx.strokeStyle = "#0284c7";
    this.ctx.lineWidth = 6;
    this.ctx.beginPath();
    this.ctx.moveTo(90, 145);
    this.ctx.lineTo(60, 158);
    this.ctx.moveTo(110, 165);
    this.ctx.lineTo(110, 184);
    this.ctx.moveTo(135, 165);
    this.ctx.lineTo(135, 184);
    this.ctx.stroke();

    this.ctx.fillStyle = "#dc2626";
    this.ctx.beginPath();
    this.ctx.arc(620, 120, 44, 0, Math.PI * 2);
    this.ctx.fill();

    this.ctx.fillStyle = "#d97706";
    this.ctx.beginPath();
    this.ctx.moveTo(590, 95);
    this.ctx.lineTo(570, 55);
    this.ctx.lineTo(605, 90);
    this.ctx.fill();

    this.ctx.fillStyle = "#fef08a";
    this.ctx.beginPath();
    this.ctx.arc(595, 110, 6, 0, Math.PI * 2);
    this.ctx.fill();
    this.ctx.fillStyle = "#0f172a";
    this.ctx.fillRect(593, 107, 3, 6);
  }
};

const socraticSim = {
  setMode(mode) {
    soundEngine.click();
    const btnS = document.getElementById("btnModeSocratic");
    const btnU = document.getElementById("btnModeUnstructured");
    const badge = document.getElementById("tutorModeBadge");
    const prompt = document.getElementById("chatStudentPrompt");
    const resp = document.getElementById("chatAiResponse");
    const integrity = document.getElementById("chatIntegrityScore");
    const expl = document.getElementById("chatExplanation");

    if (mode === "socratic") {
      btnS.classList.add("active");
      btnU.classList.remove("active");
      badge.textContent = "MODE: SOCRATIC COACH";
      prompt.textContent = `"Context: AP World History essay on the Industrial Revolution. Role: Debate coach. Action: Challenge my thesis that steam power was purely beneficial for working-class families. Format: 3 targeted counter-questions. Target: High school student."`;
      resp.textContent = `"Let's test your thesis with three historical questions: 1. How did rapid urbanization and unregulated factory working conditions impact infant mortality rates? 2. What happened to skilled artisan cottage weavers when power looms automated production? 3. Did economic gains distribute evenly, or did real wages stagnate during the first 50 years? How will you counter these points in your paper?"`;
      integrity.textContent = "Zone 1: Ethical Socratic Support (100% Student Authorship Preserved)";
      integrity.style.color = "#059669";
      expl.textContent = "Using AI to pressure-test argumentation refines reasoning skills without generating submitted text.";
    } else {
      btnU.classList.add("active");
      btnS.classList.remove("active");
      badge.textContent = "MODE: DIRECT GENERATION ENGINE";
      prompt.textContent = `"Write my AP World History essay on whether steam power was good or bad for families."`;
      resp.textContent = `"The Industrial Revolution, marked by the invention of steam power, brought extensive economic transformations to nineteenth-century family dynamics. In this essay, I will explore both the positive and negative facets of mechanized labor, concluding that technological advancement catalyzed irreversible societal shifts."`;
      integrity.textContent = "Zone 4: Direct Plagiarism Violation (0% Student Authorship)";
      integrity.style.color = "#dc2626";
      expl.textContent = "Directly generating essays bypasses the student's learning process and constitutes an explicit honor code violation.";
    }
  }
};

const citadelParticles = {
  canvas: document.getElementById("citadelCanvas"),
  ctx: null,
  spores: [],

  init() {
    if (!this.canvas) return;
    this.ctx = this.canvas.getContext("2d");
    this.resize();
    window.addEventListener("resize", () => this.resize());
    this.animate();
  },

  resize() {
    this.canvas.width = window.innerWidth;
    this.canvas.height = window.innerHeight;
    this.spores = Array.from({ length: 40 }, () => ({
      x: Math.random() * this.canvas.width,
      y: Math.random() * this.canvas.height,
      radius: Math.random() * 2 + 0.8,
      speedX: (Math.random() - 0.5) * 0.35,
      speedY: -Math.random() * 0.45 - 0.15,
      alpha: Math.random() * 0.4 + 0.2
    }));
  },

  animate() {
    this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height);
    this.spores.forEach(s => {
      s.x += s.speedX;
      s.y += s.speedY;
      if (s.y < 0) s.y = this.canvas.height;
      if (s.x < 0) s.x = this.canvas.width;
      if (s.x > this.canvas.width) s.x = 0;

      this.ctx.beginPath();
      this.ctx.arc(s.x, s.y, s.radius, 0, Math.PI * 2);
      this.ctx.fillStyle = `rgba(217, 119, 6, ${s.alpha})`;
      this.ctx.fill();
    });
    requestAnimationFrame(() => this.animate());
  }
};

window.addEventListener("DOMContentLoaded", () => {
  app.init();
  citadelParticles.init();
  tier1Bench.update();
  vectorExplorer.init();
  gradientLab.init();
  confusionMatrixLab.update(50);
  window.addEventListener("mousemove", e => companion.track(e));
});
