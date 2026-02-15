<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Founder Evaluation Calculator — Are You Ready to Build?</title>
<meta name="description" content="A free, honest self-assessment tool for startup founders. Evaluate your market timing, founder-market fit, technical moat, distribution strategy, and more.">
<meta property="og:title" content="Founder Evaluation Calculator">
<meta property="og:description" content="Find out where you stand as a founder. Free, anonymous, brutally honest.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700;1,9..40,300&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    theme: {
      extend: {
        fontFamily: {
          sans: ['DM Sans', 'sans-serif'],
          serif: ['DM Serif Display', 'serif'],
        },
        colors: {
          ink: '#0f0e0d',
          cream: '#faf8f4',
          stone: '#e8e4dc',
          muted: '#9b968e',
          accent: '#e85d26',
          'accent-light': '#fef0e9',
          'accent-dark': '#c44b1a',
          emerald: '#1a7a4a',
          'emerald-light': '#e8f5ee',
          amber: '#c47a15',
          'amber-light': '#fef3dc',
          ruby: '#c42828',
          'ruby-light': '#fde8e8',
        },
        borderRadius: {
          '2xl': '1rem',
          '3xl': '1.5rem',
          '4xl': '2rem',
        },
        boxShadow: {
          'card': '0 2px 24px rgba(15,14,13,0.06), 0 1px 4px rgba(15,14,13,0.04)',
          'card-hover': '0 8px 40px rgba(15,14,13,0.10), 0 2px 8px rgba(15,14,13,0.06)',
          'pill': '0 1px 8px rgba(15,14,13,0.08)',
          'elevated': '0 16px 64px rgba(15,14,13,0.12), 0 4px 16px rgba(15,14,13,0.06)',
        }
      }
    }
  }
</script>
<style>
  * { -webkit-font-smoothing: antialiased; -moz-osx-font-smoothing: grayscale; }

  body {
    background-color: #faf8f4;
    background-image:
      radial-gradient(ellipse 80% 60% at 50% -10%, rgba(232,93,38,0.07) 0%, transparent 60%),
      radial-gradient(ellipse 60% 40% at 80% 90%, rgba(26,122,74,0.04) 0%, transparent 50%);
    min-height: 100vh;
  }

  /* ── Scrollbar ── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: #d0ccc4; border-radius: 99px; }

  /* ── Progress bar ── */
  .progress-track {
    height: 3px;
    background: #e8e4dc;
    border-radius: 99px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #e85d26, #c44b1a);
    border-radius: 99px;
    transition: width 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  /* ── Slider ── */
  input[type=range] {
    -webkit-appearance: none;
    appearance: none;
    width: 100%;
    height: 5px;
    border-radius: 99px;
    outline: none;
    cursor: pointer;
    background: #e8e4dc;
    position: relative;
  }
  input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 22px;
    height: 22px;
    border-radius: 50%;
    background: #ffffff;
    border: 2px solid #e85d26;
    box-shadow: 0 2px 8px rgba(232,93,38,0.25), 0 1px 3px rgba(15,14,13,0.1);
    cursor: pointer;
    transition: transform 0.15s ease, box-shadow 0.15s ease;
  }
  input[type=range]::-webkit-slider-thumb:hover {
    transform: scale(1.15);
    box-shadow: 0 4px 16px rgba(232,93,38,0.35), 0 2px 6px rgba(15,14,13,0.12);
  }
  input[type=range]::-moz-range-thumb {
    width: 22px;
    height: 22px;
    border-radius: 50%;
    background: #ffffff;
    border: 2px solid #e85d26;
    box-shadow: 0 2px 8px rgba(232,93,38,0.25);
    cursor: pointer;
  }

  /* ── Option buttons ── */
  .option-btn {
    position: relative;
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 14px 18px;
    border-radius: 14px;
    border: 1.5px solid #e8e4dc;
    background: #ffffff;
    cursor: pointer;
    transition: all 0.18s ease;
    text-align: left;
    width: 100%;
    color: #0f0e0d;
  }
  .option-btn:hover {
    border-color: rgba(232,93,38,0.4);
    background: #fef7f3;
    box-shadow: 0 2px 12px rgba(232,93,38,0.08);
  }
  .option-btn.selected {
    border-color: #e85d26;
    background: #fef0e9;
    box-shadow: 0 2px 12px rgba(232,93,38,0.12);
  }
  .option-btn .radio-ring {
    flex-shrink: 0;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 2px solid #d0ccc4;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 1px;
    transition: all 0.15s ease;
    background: #fff;
  }
  .option-btn.selected .radio-ring {
    border-color: #e85d26;
    background: #e85d26;
  }
  .option-btn .radio-dot {
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: #fff;
    opacity: 0;
    transform: scale(0);
    transition: all 0.15s ease;
  }
  .option-btn.selected .radio-dot {
    opacity: 1;
    transform: scale(1);
  }

  /* ── Animations ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  @keyframes scaleIn {
    from { opacity: 0; transform: scale(0.94) translateY(10px); }
    to { opacity: 1; transform: scale(1) translateY(0); }
  }
  @keyframes countUp {
    from { opacity: 0; transform: scale(0.7); }
    to { opacity: 1; transform: scale(1); }
  }
  @keyframes pulse-ring {
    0% { transform: scale(1); opacity: 0.4; }
    100% { transform: scale(1.5); opacity: 0; }
  }
  .animate-fadeUp { animation: fadeUp 0.45s cubic-bezier(0.34, 1.2, 0.64, 1) both; }
  .animate-fadeIn { animation: fadeIn 0.3s ease both; }
  .animate-scaleIn { animation: scaleIn 0.5s cubic-bezier(0.34, 1.2, 0.64, 1) both; }
  .animate-countUp { animation: countUp 0.6s cubic-bezier(0.34, 1.56, 0.64, 1) both; }
  .delay-100 { animation-delay: 0.1s; }
  .delay-200 { animation-delay: 0.2s; }
  .delay-300 { animation-delay: 0.3s; }
  .delay-400 { animation-delay: 0.4s; }
  .delay-500 { animation-delay: 0.5s; }

  /* ── Result score ring ── */
  .score-ring {
    position: relative;
    display: inline-flex;
    align-items: center;
    justify-content: center;
  }
  .score-ring svg { transform: rotate(-90deg); }
  .score-circle-bg { fill: none; stroke: #e8e4dc; stroke-width: 8; }
  .score-circle-fill {
    fill: none;
    stroke-width: 8;
    stroke-linecap: round;
    transition: stroke-dashoffset 1.2s cubic-bezier(0.34, 1.1, 0.64, 1);
  }
  .score-ring .score-text {
    position: absolute;
    text-align: center;
    transform: none;
  }

  /* ── Category bar ── */
  .cat-bar-track {
    height: 8px;
    background: #e8e4dc;
    border-radius: 99px;
    overflow: hidden;
  }
  .cat-bar-fill {
    height: 100%;
    border-radius: 99px;
    transition: width 0.8s cubic-bezier(0.34, 1.1, 0.64, 1);
  }

  /* ── Toast ── */
  #toast {
    position: fixed;
    bottom: 28px;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: #0f0e0d;
    color: #fff;
    padding: 12px 22px;
    border-radius: 99px;
    font-size: 14px;
    font-weight: 500;
    transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
    z-index: 9999;
    white-space: nowrap;
    box-shadow: 0 8px 32px rgba(15,14,13,0.2);
  }
  #toast.show { transform: translateX(-50%) translateY(0); }

  /* ── Misc ── */
  .gradient-text {
    background: linear-gradient(135deg, #e85d26 0%, #c44b1a 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .card {
    background: #fff;
    border-radius: 24px;
    box-shadow: 0 2px 24px rgba(15,14,13,0.06), 0 1px 4px rgba(15,14,13,0.04);
    border: 1px solid rgba(232,228,220,0.8);
  }
  .btn-primary {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    background: #e85d26;
    color: #fff;
    font-weight: 600;
    font-size: 15px;
    padding: 14px 28px;
    border-radius: 14px;
    border: none;
    cursor: pointer;
    transition: all 0.18s ease;
    box-shadow: 0 2px 12px rgba(232,93,38,0.3);
    letter-spacing: -0.01em;
  }
  .btn-primary:hover {
    background: #c44b1a;
    transform: translateY(-1px);
    box-shadow: 0 6px 20px rgba(232,93,38,0.35);
  }
  .btn-primary:active { transform: translateY(0); }
  .btn-secondary {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    background: #fff;
    color: #0f0e0d;
    font-weight: 600;
    font-size: 15px;
    padding: 13px 24px;
    border-radius: 14px;
    border: 1.5px solid #e8e4dc;
    cursor: pointer;
    transition: all 0.18s ease;
    letter-spacing: -0.01em;
  }
  .btn-secondary:hover {
    border-color: #0f0e0d;
    background: #faf8f4;
    transform: translateY(-1px);
  }

  .slider-label {
    display: flex;
    justify-content: space-between;
    font-size: 12px;
    color: #9b968e;
    margin-top: 8px;
  }

  .tag {
    display: inline-flex;
    align-items: center;
    padding: 4px 12px;
    border-radius: 99px;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 0.03em;
    text-transform: uppercase;
  }
  .tag-accent { background: #fef0e9; color: #e85d26; }
  .tag-emerald { background: #e8f5ee; color: #1a7a4a; }
  .tag-amber { background: #fef3dc; color: #c47a15; }
  .tag-ruby { background: #fde8e8; color: #c42828; }
</style>
</head>
<body class="font-sans text-ink">

<!-- Toast -->
<div id="toast">✓ Link copied to clipboard</div>

<!-- ══════════════════════════════════════════════════════════
     LANDING SCREEN
══════════════════════════════════════════════════════════ -->
<div id="screen-landing" class="min-h-screen flex flex-col">
  <!-- Header -->
  <header class="px-5 py-5 flex items-center justify-between max-w-2xl mx-auto w-full">
    <div class="flex items-center gap-2">
      <div style="width:32px;height:32px;background:#e85d26;border-radius:9px;display:flex;align-items:center;justify-content:center;">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M8 2L14 12H2L8 2Z" fill="white"/></svg>
      </div>
      <span style="font-weight:700;font-size:15px;letter-spacing:-0.02em;">FounderScore</span>
    </div>
    <span class="tag tag-accent">Free Tool</span>
  </header>

  <!-- Hero -->
  <main class="flex-1 flex flex-col items-center justify-center px-5 py-12 max-w-2xl mx-auto w-full">
    <div class="animate-fadeUp text-center w-full">
      <div class="inline-flex items-center gap-2 mb-6 px-4 py-2 rounded-full" style="background:#fef0e9;border:1px solid rgba(232,93,38,0.2);">
        <div style="width:6px;height:6px;border-radius:50%;background:#e85d26;"></div>
        <span style="font-size:13px;font-weight:600;color:#e85d26;letter-spacing:0.02em;">6-MINUTE ASSESSMENT</span>
      </div>
      <h1 class="font-serif text-4xl sm:text-5xl leading-tight mb-5" style="letter-spacing:-0.02em;">
        Are you ready<br/>
        <span class="gradient-text">to build?</span>
      </h1>
      <p class="text-muted text-lg leading-relaxed mb-10 max-w-md mx-auto" style="font-weight:300;">
        An honest evaluation of your startup readiness across five critical dimensions. No fluff, no hype — just clarity.
      </p>

      <button onclick="startAssessment()" class="btn-primary text-base px-8 py-4 mb-4 w-full max-w-xs">
        Start Free Assessment
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8H13M13 8L9 4M13 8L9 12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </button>
      <p style="font-size:13px;color:#9b968e;">No sign-up required · Takes ~6 minutes</p>
    </div>

    <!-- Dimension pills -->
    <div class="animate-fadeUp delay-200 mt-12 w-full max-w-lg">
      <p style="font-size:12px;font-weight:600;color:#9b968e;letter-spacing:0.06em;text-transform:uppercase;text-align:center;margin-bottom:16px;">What you'll evaluate</p>
      <div style="display:flex;flex-wrap:wrap;gap:8px;justify-content:center;">
        <span class="tag tag-accent">Market Timing</span>
        <span class="tag" style="background:#f0edf9;color:#6b3fa0;">Founder-Market Fit</span>
        <span class="tag" style="background:#e6f2fb;color:#1a5fa0;">Technical Moat</span>
        <span class="tag tag-emerald">Distribution</span>
        <span class="tag tag-amber">Team & Execution</span>
      </div>
    </div>

    <!-- Trust signals -->
    <div class="animate-fadeUp delay-300 mt-12 grid grid-cols-3 gap-4 w-full max-w-md">
      <div class="card p-4 text-center">
        <div style="font-size:22px;font-weight:700;color:#0f0e0d;font-family:'DM Serif Display',serif;">5</div>
        <div style="font-size:11px;color:#9b968e;margin-top:2px;">Dimensions</div>
      </div>
      <div class="card p-4 text-center">
        <div style="font-size:22px;font-weight:700;color:#0f0e0d;font-family:'DM Serif Display',serif;">25</div>
        <div style="font-size:11px;color:#9b968e;margin-top:2px;">Questions</div>
      </div>
      <div class="card p-4 text-center">
        <div style="font-size:22px;font-weight:700;color:#0f0e0d;font-family:'DM Serif Display',serif;">Free</div>
        <div style="font-size:11px;color:#9b968e;margin-top:2px;">Always</div>
      </div>
    </div>
  </main>
</div>

<!-- ══════════════════════════════════════════════════════════
     QUIZ SCREEN
══════════════════════════════════════════════════════════ -->
<div id="screen-quiz" class="hidden min-h-screen flex flex-col">
  <!-- Top bar -->
  <div class="sticky top-0 z-50 bg-cream border-b border-stone" style="border-bottom-color:#e8e4dc;">
    <div class="max-w-2xl mx-auto px-5 py-4">
      <div class="flex items-center justify-between mb-3">
        <button onclick="goBack()" class="flex items-center gap-1.5 text-muted hover:text-ink transition-colors" style="font-size:14px;font-weight:500;background:none;border:none;cursor:pointer;padding:0;">
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M10 4L6 8L10 12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>
          Back
        </button>
        <span id="progress-label" style="font-size:13px;font-weight:600;color:#9b968e;"></span>
        <span id="category-label" class="tag tag-accent" style="font-size:11px;"></span>
      </div>
      <div class="progress-track">
        <div class="progress-fill" id="progress-fill" style="width:0%;"></div>
      </div>
    </div>
  </div>

  <!-- Question area -->
  <div class="flex-1 max-w-2xl mx-auto w-full px-5 py-8">
    <div id="question-container"></div>
    <div class="flex gap-3 mt-8">
      <button id="btn-next" onclick="nextQuestion()" class="btn-primary flex-1">
        Continue
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8H13M13 8L9 4M13 8L9 12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </button>
    </div>
    <p id="quiz-hint" style="font-size:12px;color:#9b968e;text-align:center;margin-top:12px;">Select an option to continue</p>
  </div>
</div>

<!-- ══════════════════════════════════════════════════════════
     RESULT SCREEN
══════════════════════════════════════════════════════════ -->
<div id="screen-result" class="hidden min-h-screen">
  <div class="max-w-2xl mx-auto px-5 py-10">

    <!-- Header -->
    <div class="animate-fadeIn text-center mb-8">
      <div class="flex items-center justify-center gap-2 mb-2">
        <div style="width:32px;height:32px;background:#e85d26;border-radius:9px;display:flex;align-items:center;justify-content:center;">
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M8 2L14 12H2L8 2Z" fill="white"/></svg>
        </div>
        <span style="font-weight:700;font-size:15px;letter-spacing:-0.02em;">FounderScore</span>
      </div>
      <p style="font-size:13px;color:#9b968e;margin-top:4px;">Your assessment results</p>
    </div>

    <!-- Score hero card -->
    <div class="card p-8 text-center mb-6 animate-scaleIn">
      <div class="score-ring mb-5 mx-auto" style="width:160px;height:160px;">
        <svg width="160" height="160" viewBox="0 0 160 160">
          <circle class="score-circle-bg" cx="80" cy="80" r="68"/>
          <circle class="score-circle-fill" id="result-circle" cx="80" cy="80" r="68"
            stroke="#e85d26"
            stroke-dasharray="427.26"
            stroke-dashoffset="427.26"/>
        </svg>
        <div class="score-text">
          <div id="result-score-num" class="font-serif animate-countUp delay-300" style="font-size:46px;line-height:1;letter-spacing:-0.03em;"></div>
          <div style="font-size:13px;color:#9b968e;font-weight:500;margin-top:2px;">/ 100</div>
        </div>
      </div>
      <div id="result-tier-badge" class="tag mb-3 mx-auto" style="display:inline-flex;"></div>
      <h2 id="result-headline" class="font-serif text-2xl sm:text-3xl mb-3" style="letter-spacing:-0.02em;"></h2>
      <p id="result-summary" class="text-muted text-base leading-relaxed max-w-md mx-auto" style="font-weight:300;"></p>
    </div>

    <!-- Category breakdown -->
    <div class="card p-6 mb-6 animate-fadeUp delay-200">
      <h3 style="font-size:13px;font-weight:700;letter-spacing:0.06em;text-transform:uppercase;color:#9b968e;margin-bottom:20px;">Score Breakdown</h3>
      <div id="category-breakdown" class="space-y-5"></div>
    </div>

    <!-- Insights -->
    <div id="insights-container" class="mb-6 animate-fadeUp delay-300"></div>

    <!-- Actions -->
    <div class="flex flex-col sm:flex-row gap-3 animate-fadeUp delay-400">
      <button onclick="shareResults()" class="btn-primary flex-1">
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M11 1.5a1.5 1.5 0 110 3 1.5 1.5 0 010-3zM5 6.5a1.5 1.5 0 110 3 1.5 1.5 0 010-3zM11 11.5a1.5 1.5 0 110 3 1.5 1.5 0 010-3z" fill="currentColor"/><path d="M9.5 3.5L6.5 7M6.5 9l3 2.5" stroke="currentColor" stroke-width="1.4" stroke-linecap="round"/></svg>
        Share My Results
      </button>
      <button onclick="retakeAssessment()" class="btn-secondary flex-1">
        Retake Assessment
      </button>
    </div>
    <p style="font-size:12px;color:#9b968e;text-align:center;margin-top:12px;">Retake after implementing changes to track your progress.</p>
  </div>
</div>

<script>
// ══════════════════════════════════════════════════════════
//  DATA MODEL
// ══════════════════════════════════════════════════════════

const CATEGORIES = [
  {
    id: 'market_timing',
    label: 'Market Timing',
    color: '#e85d26',
    lightColor: '#fef0e9',
    emoji: '📈',
    icon: `<svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 12L6 7L9 10L13 4" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>`,
    questions: [
      {
        id: 'mt_1',
        type: 'options',
        text: 'How would you describe the current market momentum for your category?',
        subtext: 'Think about search trends, funding activity, and media coverage.',
        options: [
          { text: 'The market barely exists yet — we\'re creating a new behavior', score: 40 },
          { text: 'Early adopters exist but the mass market hasn\'t arrived', score: 70 },
          { text: 'Growing fast — clear tailwinds like AI, regulation, or demographics', score: 95 },
          { text: 'At peak hype — lots of competitors pouring in right now', score: 55 },
          { text: 'Mature or declining — we\'re disrupting an old category', score: 45 },
        ]
      },
      {
        id: 'mt_2',
        type: 'options',
        text: 'What is the primary driver behind why this market is growing now?',
        subtext: 'The best startups ride a macro wave, not just build a feature.',
        options: [
          { text: 'A new technology just became viable (AI, mobile, cloud, etc.)', score: 90 },
          { text: 'A regulatory change opened a new opportunity', score: 85 },
          { text: 'Demographics or consumer behavior shifted', score: 75 },
          { text: 'Competitors made a wrong move, creating a gap', score: 65 },
          { text: 'Not sure — the opportunity just feels right', score: 25 },
        ]
      },
      {
        id: 'mt_3',
        type: 'options',
        text: 'How established are existing alternatives to your solution?',
        subtext: 'The right incumbents are strong enough to prove demand but slow enough to beat.',
        options: [
          { text: 'No alternatives exist — customers use workarounds (spreadsheets, email)', score: 80 },
          { text: 'Old incumbents dominating — ripe for disruption', score: 85 },
          { text: 'Well-funded, fast-moving startups already competing', score: 50 },
          { text: 'A few direct competitors, but differentiation is clear', score: 70 },
          { text: 'The space is crowded with near-identical products', score: 30 },
        ]
      },
      {
        id: 'mt_4',
        type: 'slider',
        text: 'On a scale of 1–10, how confident are you about the timing?',
        subtext: 'Could this have succeeded 3 years ago? Will it still work in 3 years?',
        min: 1, max: 10,
        labels: ['Too early', 'Perfect window', 'Too late'],
        scoreMultiplier: 10
      },
      {
        id: 'mt_5',
        type: 'options',
        text: 'What does your TAM (Total Addressable Market) look like?',
        options: [
          { text: 'Niche but defensible — <$500M', score: 55 },
          { text: 'Solid mid-market — $500M–$5B', score: 75 },
          { text: 'Large opportunity — $5B–$50B', score: 90 },
          { text: 'Massive, but hard to capture — $50B+', score: 70 },
          { text: 'Honestly unsure — haven\'t calculated it rigorously', score: 20 },
        ]
      },
    ]
  },
  {
    id: 'founder_fit',
    label: 'Founder-Market Fit',
    color: '#6b3fa0',
    lightColor: '#f0edf9',
    emoji: '🧠',
    icon: `<svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M8 3a3 3 0 100 6 3 3 0 000-6zM2 13c0-2.21 2.686-4 6-4s6 1.79 6 4" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/></svg>`,
    questions: [
      {
        id: 'ff_1',
        type: 'options',
        text: 'Why are you the right person to build this?',
        subtext: '"Unfair advantage" is the most important filter VCs use.',
        options: [
          { text: 'I lived this problem deeply — personally or professionally for years', score: 95 },
          { text: 'I have domain expertise in this exact industry or technology', score: 85 },
          { text: 'I have a unique network or distribution channel others lack', score: 80 },
          { text: 'I\'m passionate about this and willing to learn', score: 45 },
          { text: 'I spotted a gap in the market, but I\'m not the target user', score: 40 },
        ]
      },
      {
        id: 'ff_2',
        type: 'slider',
        text: 'How many years of relevant industry experience do you have?',
        min: 0, max: 15,
        labels: ['0 years', '7+ years', '15 years'],
        scoreMultiplier: 6.67
      },
      {
        id: 'ff_3',
        type: 'options',
        text: 'How well do you know your target customer?',
        subtext: 'The best founders talk to customers before writing a single line of code.',
        options: [
          { text: 'I am the customer — I face this exact problem daily', score: 95 },
          { text: 'I\'ve done 20+ customer discovery interviews this month', score: 85 },
          { text: 'I\'ve spoken with a handful of potential users', score: 55 },
          { text: 'I know the pain exists from research and reading', score: 30 },
          { text: 'Not many conversations yet — still validating the problem', score: 15 },
        ]
      },
      {
        id: 'ff_4',
        type: 'options',
        text: 'What\'s your team\'s technical capability relative to what you\'re building?',
        options: [
          { text: 'We can build the entire product in-house without external help', score: 90 },
          { text: 'We can build the MVP, but we\'ll need to hire for scale', score: 75 },
          { text: 'We\'re partly technical — outsourcing some development', score: 55 },
          { text: 'Non-technical team — relying on a technical co-founder search', score: 35 },
          { text: 'No technical capability yet — no-code tools only', score: 25 },
        ]
      },
      {
        id: 'ff_5',
        type: 'options',
        text: 'Have you successfully built and shipped products before?',
        options: [
          { text: 'Yes — I\'ve built and scaled a successful startup', score: 95 },
          { text: 'Yes — I\'ve built products at a startup, though haven\'t founded before', score: 80 },
          { text: 'Side projects and small products, but nothing at scale', score: 55 },
          { text: 'Big company experience — never been at an early-stage startup', score: 45 },
          { text: 'First-time builder — learning as I go', score: 40 },
        ]
      },
    ]
  },
  {
    id: 'technical_moat',
    label: 'Technical Moat',
    color: '#1a5fa0',
    lightColor: '#e6f2fb',
    emoji: '🔬',
    icon: `<svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M8 1v4M8 11v4M1 8h4M11 8h4M3.5 3.5l2.8 2.8M9.7 9.7l2.8 2.8M3.5 12.5l2.8-2.8M9.7 6.3l2.8-2.8" stroke="currentColor" stroke-width="1.6" stroke-linecap="round"/></svg>`,
    questions: [
      {
        id: 'tm_1',
        type: 'options',
        text: 'How defensible is your core product or technology?',
        subtext: 'If you succeed, how hard is it for a well-funded competitor to replicate you?',
        options: [
          { text: 'Patent-protected or genuinely novel research-backed IP', score: 95 },
          { text: 'Proprietary data that gets better with usage (data flywheel)', score: 90 },
          { text: 'Network effects — value increases with each new user', score: 88 },
          { text: 'Deep workflow integrations with high switching costs', score: 75 },
          { text: 'A strong brand and community moat', score: 65 },
          { text: 'Better UX on existing tech — easy to copy in 6–12 months', score: 30 },
        ]
      },
      {
        id: 'tm_2',
        type: 'options',
        text: 'How long would it take a well-resourced team to replicate your core product?',
        options: [
          { text: 'Probably impossible without our unique data or IP', score: 95 },
          { text: 'More than 2 years — we\'d have significant lead time', score: 80 },
          { text: '6 months to a year — we rely on execution speed', score: 55 },
          { text: '3–6 months — any strong team could catch up', score: 35 },
          { text: 'A month or two — it\'s mostly a commodity feature', score: 15 },
        ]
      },
      {
        id: 'tm_3',
        type: 'options',
        text: 'Does your product improve as it gets more users or data?',
        subtext: 'Products with compounding loops get better over time. Others plateau.',
        options: [
          { text: 'Yes — every user makes the core product meaningfully better', score: 95 },
          { text: 'Somewhat — more users improve some features but not the core', score: 65 },
          { text: 'Marginally — we get feedback but no automatic improvements', score: 40 },
          { text: 'Not really — it\'s the same product regardless of usage', score: 20 },
        ]
      },
      {
        id: 'tm_4',
        type: 'slider',
        text: 'How deep is the technical complexity of what you\'re building?',
        subtext: 'Rate the technical barrier to entry for competitors (1 = trivial, 10 = PhD-level)',
        min: 1, max: 10,
        labels: ['Commodity tech', 'Novel complexity', 'Frontier R&D'],
        scoreMultiplier: 10
      },
      {
        id: 'tm_5',
        type: 'options',
        text: 'What is your primary build vs. buy strategy?',
        options: [
          { text: 'Building proprietary tech that others can\'t access', score: 90 },
          { text: 'Building on top of foundational models / platforms, but adding unique layers', score: 70 },
          { text: 'Orchestrating existing APIs and tools with strong UX', score: 55 },
          { text: 'Primarily no-code tools wrapped in a nice interface', score: 30 },
          { text: 'Still figuring out the technology approach', score: 15 },
        ]
      },
    ]
  },
  {
    id: 'distribution',
    label: 'Distribution',
    color: '#1a7a4a',
    lightColor: '#e8f5ee',
    emoji: '📣',
    icon: `<svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 8l3-5 3 3 3-4 3 4" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>`,
    questions: [
      {
        id: 'dist_1',
        type: 'options',
        text: 'What is your primary go-to-market motion?',
        subtext: 'The best founders know exactly how they\'ll acquire their first 1,000 customers.',
        options: [
          { text: 'Product-led growth — the product sells and spreads itself', score: 90 },
          { text: 'Community-led — we have or can build a passionate community', score: 80 },
          { text: 'Founder-led sales — direct relationships and outbound', score: 75 },
          { text: 'Content/SEO — inbound marketing with strong content strategy', score: 70 },
          { text: 'Paid acquisition — SEM, social ads, performance marketing', score: 55 },
          { text: 'Not sure yet — we\'ll try different things and see', score: 15 },
        ]
      },
      {
        id: 'dist_2',
        type: 'options',
        text: 'Do you have an existing audience or community you can launch to?',
        subtext: 'Distribution at launch dramatically changes your chances of survival.',
        options: [
          { text: 'Yes — a large audience (10K+ followers, newsletter, community)', score: 95 },
          { text: 'Yes — a niche but highly relevant audience of 1K–10K', score: 80 },
          { text: 'A small but engaged network in the relevant industry', score: 60 },
          { text: 'Starting from scratch — building audience simultaneously', score: 30 },
          { text: 'No current audience and no clear plan to build one', score: 10 },
        ]
      },
      {
        id: 'dist_3',
        type: 'options',
        text: 'What is your realistic CAC (Cost to Acquire a Customer)?',
        options: [
          { text: 'Essentially free — word of mouth, viral, or organic referrals', score: 95 },
          { text: 'Low — under $50 per customer through content or community', score: 80 },
          { text: 'Moderate — $50–$500 with solid LTV to support it', score: 65 },
          { text: 'High — $500–$5K, requires enterprise sales motion', score: 50 },
          { text: 'Unknown — haven\'t modeled or tested acquisition costs', score: 10 },
        ]
      },
      {
        id: 'dist_4',
        type: 'slider',
        text: 'How strong is your current pipeline of potential customers?',
        min: 1, max: 10,
        labels: ['Empty pipeline', 'Strong conversations', 'Waitlist ready'],
        scoreMultiplier: 10
      },
      {
        id: 'dist_5',
        type: 'options',
        text: 'Do you have any unfair distribution advantages?',
        subtext: 'Partnerships, exclusives, regulatory access, press relationships, etc.',
        options: [
          { text: 'Yes — exclusive partnerships or channels no competitor has', score: 95 },
          { text: 'Yes — strong relationships in the exact industry we\'re targeting', score: 80 },
          { text: 'Some — we know the right people but nothing locked in', score: 60 },
          { text: 'No — we\'re starting from the same position as everyone else', score: 30 },
        ]
      },
    ]
  },
  {
    id: 'team_execution',
    label: 'Team & Execution',
    color: '#c47a15',
    lightColor: '#fef3dc',
    emoji: '⚡',
    icon: `<svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M9 2L4 9h4l-1 5 5-7H8L9 2z" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>`,
    questions: [
      {
        id: 'te_1',
        type: 'options',
        text: 'What is your team composition right now?',
        subtext: 'The best early-stage teams are small, committed, and complementary.',
        options: [
          { text: 'Solo founder with a clear co-founder search in progress', score: 45 },
          { text: 'Two complementary co-founders (e.g. technical + business)', score: 90 },
          { text: 'Three or more co-founders with clear equity and roles', score: 75 },
          { text: 'A larger team of employees or contractors', score: 65 },
          { text: 'Solo founder with no co-founder plans — fully committed', score: 55 },
        ]
      },
      {
        id: 'te_2',
        type: 'options',
        text: 'How committed is the founding team?',
        subtext: 'Most startups die because the team runs out of energy, not money.',
        options: [
          { text: 'Full-time, with financial runway to sustain at least 12 months', score: 95 },
          { text: 'Full-time but bootstrapping — limited runway', score: 70 },
          { text: 'Part-time — transitioning to full-time within 3 months', score: 55 },
          { text: 'Side project — hoping to go full-time if it works', score: 25 },
        ]
      },
      {
        id: 'te_3',
        type: 'options',
        text: 'What best describes your current velocity and shipping speed?',
        subtext: 'Speed of learning and iteration beats everything else at the early stage.',
        options: [
          { text: 'Shipping weekly — customer feedback loops are tight', score: 95 },
          { text: 'Shipping monthly — reasonable pace with good processes', score: 75 },
          { text: 'Building in stealth — focusing on getting v1 right', score: 50 },
          { text: 'Slow — too many competing priorities or team blockers', score: 25 },
          { text: 'Haven\'t shipped anything yet — still in planning phase', score: 15 },
        ]
      },
      {
        id: 'te_4',
        type: 'slider',
        text: 'How would you rate your team\'s execution and accountability?',
        min: 1, max: 10,
        labels: ['Chaotic', 'Structured', 'Machine-like'],
        scoreMultiplier: 10
      },
      {
        id: 'te_5',
        type: 'options',
        text: 'How clear is your next 90-day milestone?',
        subtext: 'The best founders always know exactly what they\'re optimizing for.',
        options: [
          { text: 'Crystal clear — one north star metric we\'re racing toward', score: 95 },
          { text: 'Clear — 2–3 milestones we\'re confident about', score: 75 },
          { text: 'Somewhat clear — directionally right but details fuzzy', score: 50 },
          { text: 'Vague — we\'re exploring, not yet executing', score: 25 },
          { text: 'No clear goal — we need to figure that out first', score: 10 },
        ]
      },
    ]
  },
];

// ══════════════════════════════════════════════════════════
//  STATE
// ══════════════════════════════════════════════════════════

let allQuestions = [];
let state = {
  currentIndex: 0,
  answers: {},
};

function buildQuestionList() {
  allQuestions = [];
  CATEGORIES.forEach(cat => {
    cat.questions.forEach(q => {
      allQuestions.push({ ...q, categoryId: cat.id });
    });
  });
}

// ══════════════════════════════════════════════════════════
//  SCREEN MANAGEMENT
// ══════════════════════════════════════════════════════════

function showScreen(id) {
  ['screen-landing', 'screen-quiz', 'screen-result'].forEach(s => {
    document.getElementById(s).classList.add('hidden');
  });
  document.getElementById(id).classList.remove('hidden');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

// ══════════════════════════════════════════════════════════
//  ASSESSMENT FLOW
// ══════════════════════════════════════════════════════════

function startAssessment() {
  buildQuestionList();
  state.currentIndex = 0;
  state.answers = {};
  showScreen('screen-quiz');
  renderQuestion();
}

function renderQuestion() {
  const q = allQuestions[state.currentIndex];
  const cat = CATEGORIES.find(c => c.id === q.categoryId);
  const total = allQuestions.length;
  const progress = ((state.currentIndex) / total) * 100;

  // Update header
  document.getElementById('progress-label').textContent = `${state.currentIndex + 1} of ${total}`;
  document.getElementById('category-label').textContent = cat.label;
  document.getElementById('progress-fill').style.width = progress + '%';

  // Question HTML
  const container = document.getElementById('question-container');
  let optionsHTML = '';

  if (q.type === 'options') {
    const currentAnswer = state.answers[q.id];
    optionsHTML = `<div class="space-y-2.5">` + q.options.map((opt, i) => `
      <button class="option-btn ${currentAnswer === i ? 'selected' : ''}" onclick="selectOption('${q.id}', ${i}, ${opt.score}, this)">
        <div class="radio-ring"><div class="radio-dot"></div></div>
        <div>
          <div style="font-size:14px;font-weight:500;line-height:1.45;">${opt.text}</div>
        </div>
      </button>
    `).join('') + `</div>`;
  } else {
    const val = state.answers[q.id]?.rawVal ?? Math.round((q.max + q.min) / 2);
    const score = Math.round(((val - q.min) / (q.max - q.min)) * (q.scoreMultiplier * q.max - q.scoreMultiplier * q.min) + q.scoreMultiplier * q.min);
    optionsHTML = `
      <div class="card p-6">
        <div style="text-align:center;margin-bottom:20px;">
          <span style="font-size:52px;font-weight:700;font-family:'DM Serif Display',serif;letter-spacing:-0.03em;color:#0f0e0d;" id="slider-display-${q.id}">${val}</span>
          <span style="font-size:20px;color:#9b968e;"> / ${q.max}</span>
        </div>
        <input type="range" min="${q.min}" max="${q.max}" value="${val}" step="1"
          id="slider-${q.id}"
          oninput="updateSlider('${q.id}', ${q.scoreMultiplier}, ${q.min}, ${q.max})"
          onchange="updateSlider('${q.id}', ${q.scoreMultiplier}, ${q.min}, ${q.max})"
          style="background: linear-gradient(to right, ${cat.color} 0%, ${cat.color} ${((val - q.min) / (q.max - q.min)) * 100}%, #e8e4dc ${((val - q.min) / (q.max - q.min)) * 100}%, #e8e4dc 100%);"
        />
        <div class="slider-label">
          <span>${q.labels[0]}</span>
          <span>${q.labels[1]}</span>
          <span>${q.labels[2]}</span>
        </div>
      </div>
    `;
    // Set slider answer
    if (!state.answers[q.id]) {
      state.answers[q.id] = { rawVal: val, score: Math.max(10, Math.round((val / q.max) * 100)) };
    }
  }

  container.innerHTML = `
    <div class="animate-fadeUp">
      <div class="flex items-center gap-2 mb-4">
        <div style="width:28px;height:28px;border-radius:8px;background:${cat.lightColor};color:${cat.color};display:flex;align-items:center;justify-content:center;">${cat.icon}</div>
        <span style="font-size:12px;font-weight:600;color:${cat.color};letter-spacing:0.04em;text-transform:uppercase;">${cat.label}</span>
      </div>
      <h2 style="font-size:19px;font-weight:600;line-height:1.4;letter-spacing:-0.02em;margin-bottom:${q.subtext ? '8px' : '20px'};">${q.text}</h2>
      ${q.subtext ? `<p style="font-size:14px;color:#9b968e;margin-bottom:20px;line-height:1.5;font-weight:300;">${q.subtext}</p>` : ''}
      ${optionsHTML}
    </div>
  `;

  updateContinueButton();
}

function selectOption(qId, optIndex, score, btn) {
  state.answers[qId] = { selectedIndex: optIndex, score };
  // Visual update
  btn.closest('.space-y-2\\.5, .space-y-2_5, [class*="space-y"]').querySelectorAll('.option-btn').forEach(b => b.classList.remove('selected'));
  // Re-find siblings
  document.querySelectorAll(`#question-container .option-btn`).forEach(b => b.classList.remove('selected'));
  btn.classList.add('selected');
  updateContinueButton();
}

function updateSlider(qId, multiplier, min, max) {
  const slider = document.getElementById(`slider-${qId}`);
  const val = parseInt(slider.value);
  document.getElementById(`slider-display-${qId}`).textContent = val;
  const pct = ((val - min) / (max - min)) * 100;
  const cat = CATEGORIES.find(c => c.questions.some(q => q.id === qId));
  slider.style.background = `linear-gradient(to right, ${cat.color} 0%, ${cat.color} ${pct}%, #e8e4dc ${pct}%, #e8e4dc 100%)`;
  state.answers[qId] = { rawVal: val, score: Math.max(10, Math.round((val / max) * 100)) };
  updateContinueButton();
}

function updateContinueButton() {
  const q = allQuestions[state.currentIndex];
  const answered = !!state.answers[q.id];
  const btn = document.getElementById('btn-next');
  const hint = document.getElementById('quiz-hint');
  const isLast = state.currentIndex === allQuestions.length - 1;
  btn.textContent = isLast ? 'See My Results →' : 'Continue →';
  btn.style.opacity = answered ? '1' : '0.45';
  btn.style.pointerEvents = answered ? 'auto' : 'none';
  if (hint) hint.style.display = answered ? 'none' : 'block';

  // Re-inject icon
  btn.innerHTML = isLast
    ? `See My Results <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8H13M13 8L9 4M13 8L9 12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>`
    : `Continue <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8H13M13 8L9 4M13 8L9 12" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/></svg>`;
}

function nextQuestion() {
  const q = allQuestions[state.currentIndex];
  if (!state.answers[q.id]) return;

  if (state.currentIndex < allQuestions.length - 1) {
    state.currentIndex++;
    renderQuestion();
    window.scrollTo({ top: 0, behavior: 'smooth' });
  } else {
    showResults();
  }
}

function goBack() {
  if (state.currentIndex > 0) {
    state.currentIndex--;
    renderQuestion();
  } else {
    showScreen('screen-landing');
  }
}

// ══════════════════════════════════════════════════════════
//  RESULTS CALCULATION
// ══════════════════════════════════════════════════════════

function calcCategoryScores() {
  return CATEGORIES.map(cat => {
    const scores = cat.questions.map(q => state.answers[q.id]?.score ?? 50);
    const avg = Math.round(scores.reduce((a, b) => a + b, 0) / scores.length);
    return { ...cat, score: avg };
  });
}

function calcOverallScore(catScores) {
  const weighted = catScores.reduce((a, c) => a + c.score, 0);
  return Math.round(weighted / catScores.length);
}

function getTier(score) {
  if (score >= 80) return { label: 'Ready to Raise', class: 'tag-emerald', color: '#1a7a4a', ringColor: '#1a7a4a' };
  if (score >= 65) return { label: 'Strong Foundation', class: 'tag-accent', color: '#e85d26', ringColor: '#e85d26' };
  if (score >= 50) return { label: 'Promising Early Stage', class: 'tag-amber', color: '#c47a15', ringColor: '#c47a15' };
  return { label: 'Needs Work', class: 'tag-ruby', color: '#c42828', ringColor: '#c42828' };
}

function getHeadline(score) {
  if (score >= 80) return 'You\'ve got the fundamentals right.';
  if (score >= 65) return 'A solid base — sharpen your edges.';
  if (score >= 50) return 'You\'re early. That\'s okay. Keep going.';
  return 'Honest feedback: more work needed.';
}

function getSummary(score) {
  if (score >= 80) return 'Your scores suggest strong alignment across market, team, and strategy. You\'re in the top cohort of startup-ready founders. Focus on execution and fundraise with conviction.';
  if (score >= 65) return 'You have a real opportunity here. There are specific dimensions holding your score back — address those and you\'ll be in a strong position to build and fundraise.';
  if (score >= 50) return 'You\'re making real progress, but there are foundational gaps to address. Use this as a checklist, not a death sentence. Many great companies started from here.';
  return 'The honest truth: several critical areas need attention before you\'re ready to build at scale. That\'s better to know now than after raising money.';
}

const INSIGHTS = {
  market_timing: {
    low: { title: 'Rethink your market timing', body: 'A great product in a bad-timing market rarely wins. Study the macro tailwinds: regulation, technology shifts, demographic changes. The best founders pick a wave and surf it — they don\'t paddle against the current.' },
    mid: { title: 'Strengthen your market thesis', body: 'Your timing sense is reasonable, but you need a sharper narrative. Can you articulate in one sentence why THIS moment is the right time? Investors will ask, and your team needs to believe it.' },
    high: { title: 'Your timing thesis is strong', body: 'You\'ve picked the right wave. Now make sure your execution speed matches the window — market timing advantages can close faster than you expect.' },
  },
  founder_fit: {
    low: { title: 'Build your domain authority first', body: 'Founder-market fit is the most under-rated success factor. Consider spending 90 days embedded with your target customer before writing code. Talk to 50 people in the space. The insights will reshape your product entirely.' },
    mid: { title: 'Deepen your customer intimacy', body: 'You know enough to start but not enough to be certain. Run structured customer discovery: 2–3 interviews per week minimum. The goal is to understand their pain so deeply that you can predict their next sentence.' },
    high: { title: 'Leverage your unfair advantage', body: 'Your founder-market fit is a significant moat — use it in every conversation. Your expertise should be front and center in marketing, fundraising, and recruiting.' },
  },
  technical_moat: {
    low: { title: 'Plan your defensibility roadmap', body: 'If your core technology is easy to replicate, competitors will catch up the moment you show traction. Define what your moat will be at Series A: proprietary data, network effects, or deep integrations. Build toward it from day one.' },
    mid: { title: 'Accelerate your data or network advantages', body: 'You have some defensibility, but it\'s not yet a true moat. Focus on building loops that make your product better as more people use it — that\'s where compounding advantage lives.' },
    high: { title: 'Your moat is your competitive edge', body: 'Technical defensibility is rare. Make sure you\'re quantifying this for investors — proprietary data, network scale, or novel IP are the kind of moats that command premium valuations.' },
  },
  distribution: {
    low: { title: 'Distribution is your #1 priority', body: 'Most startups die from distribution failure, not product failure. Before writing more code: identify your first 10 customers by name, map exactly how you\'ll reach them, and start those conversations now. Sales skills are learnable. Start today.' },
    mid: { title: 'Build a repeatable acquisition engine', body: 'You have some distribution levers, but no clear winner yet. Run structured experiments: one channel at a time, 30-day sprints, clear success metrics. Double down on what works, kill what doesn\'t.' },
    high: { title: 'You have distribution leverage', body: 'Strong distribution is the most underappreciated startup advantage. You can acquire customers efficiently — make sure your product and retention are strong enough to capitalize on it.' },
  },
  team_execution: {
    low: { title: 'Fix team and process fundamentals first', body: 'Execution issues compound over time. Define a single north-star metric for the next 90 days and hold weekly reviews. If you have a co-founder gap, filling it should be your top priority — the right complement changes everything.' },
    mid: { title: 'Increase your iteration velocity', body: 'Startups win by learning faster than anyone else. Set a goal: ship something to a real customer every 2 weeks. Even a prototype, a Loom demo, or a Figma mockup counts. Speed of feedback is speed of progress.' },
    high: { title: 'Protect your execution engine', body: 'Your team and process are an asset. As you grow, actively protect the culture of speed and accountability — it\'s easy to lose as headcount scales. Document your operating cadence now.' },
  },
};

function getInsights(catScores) {
  return catScores.map(cat => {
    const key = cat.score >= 70 ? 'high' : cat.score >= 50 ? 'mid' : 'low';
    return { ...INSIGHTS[cat.id][key], category: cat };
  });
}

function showResults() {
  const catScores = calcCategoryScores();
  const overall = calcOverallScore(catScores);
  const tier = getTier(overall);

  // Save to URL (simple encoding)
  const resultData = {
    s: overall,
    c: catScores.map(c => c.score),
  };
  const encoded = btoa(JSON.stringify(resultData));
  history.replaceState(null, '', `#r=${encoded}`);

  showScreen('screen-result');

  // Score number
  document.getElementById('result-score-num').textContent = overall;

  // Ring animation
  const circumference = 427.26;
  const offset = circumference - (overall / 100) * circumference;
  const circle = document.getElementById('result-circle');
  circle.style.stroke = tier.ringColor;
  setTimeout(() => { circle.style.strokeDashoffset = offset; }, 200);

  // Tier badge
  const badge = document.getElementById('result-tier-badge');
  badge.className = `tag ${tier.class}`;
  badge.textContent = tier.label;

  // Headlines
  document.getElementById('result-headline').textContent = getHeadline(overall);
  document.getElementById('result-summary').textContent = getSummary(overall);

  // Category breakdown
  const breakdownEl = document.getElementById('category-breakdown');
  breakdownEl.innerHTML = catScores.map((cat, i) => `
    <div>
      <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;">
        <div style="display:flex;align-items:center;gap:8px;">
          <div style="width:24px;height:24px;border-radius:7px;background:${cat.lightColor};color:${cat.color};display:flex;align-items:center;justify-content:center;font-size:12px;">${cat.icon}</div>
          <span style="font-size:14px;font-weight:500;">${cat.label}</span>
        </div>
        <span style="font-size:14px;font-weight:700;color:${cat.color};">${cat.score}</span>
      </div>
      <div class="cat-bar-track">
        <div class="cat-bar-fill" id="catbar-${cat.id}" style="width:0%;background:${cat.color};transition-delay:${i * 0.1 + 0.4}s;"></div>
      </div>
    </div>
  `).join('');

  setTimeout(() => {
    catScores.forEach(cat => {
      const bar = document.getElementById(`catbar-${cat.id}`);
      if (bar) bar.style.width = cat.score + '%';
    });
  }, 100);

  // Insights — show the 3 lowest or most interesting
  const insights = getInsights(catScores);
  const sorted = [...insights].sort((a, b) => a.category.score - b.category.score);
  const toShow = sorted.slice(0, 3);

  const insightsEl = document.getElementById('insights-container');
  insightsEl.innerHTML = `
    <h3 style="font-size:13px;font-weight:700;letter-spacing:0.06em;text-transform:uppercase;color:#9b968e;margin-bottom:14px;">Personalized Insights</h3>
    <div class="space-y-3">
      ${toShow.map((ins, i) => `
        <div class="card p-5 animate-fadeUp delay-${(i+3)*100}">
          <div style="display:flex;align-items:center;gap:8px;margin-bottom:10px;">
            <div style="width:28px;height:28px;border-radius:8px;background:${ins.category.lightColor};color:${ins.category.color};display:flex;align-items:center;justify-content:center;">${ins.category.icon}</div>
            <div>
              <div style="font-size:11px;font-weight:700;letter-spacing:0.05em;text-transform:uppercase;color:${ins.category.color};">${ins.category.label}</div>
              <div style="font-size:14px;font-weight:600;color:#0f0e0d;letter-spacing:-0.01em;">${ins.title}</div>
            </div>
          </div>
          <p style="font-size:14px;color:#5a554f;line-height:1.65;font-weight:300;">${ins.body}</p>
        </div>
      `).join('')}
    </div>
  `;
}

// ══════════════════════════════════════════════════════════
//  SHARING
// ══════════════════════════════════════════════════════════

function shareResults() {
  const url = window.location.href;
  if (navigator.share) {
    navigator.share({
      title: 'My FounderScore Results',
      text: 'I just took the Founder Evaluation Calculator. See how you compare!',
      url,
    }).catch(() => copyToClipboard(url));
  } else {
    copyToClipboard(url);
  }
}

function copyToClipboard(text) {
  if (navigator.clipboard) {
    navigator.clipboard.writeText(text).then(showToast);
  } else {
    const ta = document.createElement('textarea');
    ta.value = text;
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    document.body.removeChild(ta);
    showToast();
  }
}

function showToast() {
  const toast = document.getElementById('toast');
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 2800);
}

// ══════════════════════════════════════════════════════════
//  RETAKE
// ══════════════════════════════════════════════════════════

function retakeAssessment() {
  history.replaceState(null, '', window.location.pathname);
  startAssessment();
}

// ══════════════════════════════════════════════════════════
//  URL RESULT RESTORE
// ══════════════════════════════════════════════════════════

function tryRestoreFromURL() {
  const hash = window.location.hash;
  const match = hash.match(/^#r=(.+)$/);
  if (!match) return false;
  try {
    const data = JSON.parse(atob(match[1]));
    if (!data.s || !data.c || data.c.length !== CATEGORIES.length) return false;

    buildQuestionList();
    // Restore synthetic answers
    CATEGORIES.forEach((cat, i) => {
      cat.questions.forEach(q => {
        state.answers[q.id] = { score: data.c[i] };
      });
    });
    showResults();
    return true;
  } catch (e) { return false; }
}

// ══════════════════════════════════════════════════════════
//  INIT
// ══════════════════════════════════════════════════════════

document.addEventListener('DOMContentLoaded', () => {
  if (!tryRestoreFromURL()) {
    showScreen('screen-landing');
  }
});
</script>
</body>
</html>
