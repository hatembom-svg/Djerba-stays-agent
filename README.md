# Djerba-stays-agent
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="mobile-web-app-capable" content="yes">
<title>Djerba Stays — Agent</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap" rel="stylesheet">
<style>
  :root {
    --sand:    #F5EDD8;
    --gold:    #C8973A;
    --gold2:   #E8B84B;
    --ocean:   #1A5F7A;
    --deep:    #0D3547;
    --white:   #FFFFFF;
    --danger:  #C0392B;
    --success: #1A7A4A;
    --purple:  #5C3A7A;
    --slate:   #2C4A5A;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

  body {
    font-family: 'Cairo', sans-serif;
    background: var(--deep);
    min-height: 100dvh;
    display: flex;
    flex-direction: column;
    align-items: center;
    overflow-x: hidden;
  }

  /* Background pattern */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      radial-gradient(circle at 20% 20%, rgba(200,151,58,0.12) 0%, transparent 50%),
      radial-gradient(circle at 80% 80%, rgba(26,95,122,0.2) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
  }

  /* Geometric motif top */
  .geo-top {
    width: 100%;
    height: 6px;
    background: linear-gradient(90deg, var(--gold) 0%, var(--gold2) 50%, var(--gold) 100%);
    position: relative;
    z-index: 2;
  }

  header {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: 480px;
    padding: 28px 24px 20px;
    text-align: center;
  }

  .brand-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 4px;
  }

  .brand-icon {
    width: 36px;
    height: 36px;
    background: linear-gradient(135deg, var(--gold), var(--gold2));
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    flex-shrink: 0;
  }

  .brand-name {
    font-size: 22px;
    font-weight: 900;
    color: var(--white);
    letter-spacing: 0.5px;
  }

  .brand-name span {
    color: var(--gold2);
  }

  .sub-label {
    font-size: 13px;
    color: rgba(255,255,255,0.5);
    font-weight: 400;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-top: 2px;
  }

  /* Divider */
  .divider {
    width: 48px;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold), transparent);
    margin: 12px auto 0;
  }

  /* Grid */
  .grid {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: 480px;
    padding: 8px 16px 32px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  /* Card button */
  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 22px 12px 20px;
    border-radius: 18px;
    border: 1px solid rgba(255,255,255,0.08);
    text-decoration: none;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: transform 0.15s ease, box-shadow 0.15s ease;
    -webkit-user-select: none;
    user-select: none;
    min-height: 130px;
  }

  .card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: rgba(255,255,255,0);
    transition: background 0.15s ease;
    border-radius: inherit;
  }

  .card:active {
    transform: scale(0.96);
  }

  .card:active::before {
    background: rgba(255,255,255,0.08);
  }

  /* Color variants */
  .card.checkin {
    background: linear-gradient(145deg, #1A6B4A, #0F4A32);
    box-shadow: 0 4px 20px rgba(26,106,74,0.35);
  }
  .card.checkout {
    background: linear-gradient(145deg, #1A4A6B, #0F2F4A);
    box-shadow: 0 4px 20px rgba(26,74,107,0.35);
  }
  .card.encaissement {
    background: linear-gradient(145deg, #6B4A1A, #4A2F0A);
    box-shadow: 0 4px 20px rgba(200,151,58,0.3);
  }
  .card.incident {
    background: linear-gradient(145deg, #6B1A1A, #4A0F0F);
    box-shadow: 0 4px 20px rgba(192,57,43,0.35);
  }
  .card.menage {
    background: linear-gradient(145deg, #1A3D6B, #0F2545);
    box-shadow: 0 4px 20px rgba(92,58,122,0.3);
  }
  .card.maintenance {
    background: linear-gradient(145deg, #2A3A4A, #1A252F);
    box-shadow: 0 4px 20px rgba(44,74,90,0.4);
  }

  /* Icon circle */
  .icon-wrap {
    width: 54px;
    height: 54px;
    border-radius: 50%;
    background: rgba(255,255,255,0.12);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 26px;
    border: 1.5px solid rgba(255,255,255,0.15);
    flex-shrink: 0;
  }

  /* Text */
  .card-texts {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 3px;
  }

  .card-ar {
    font-size: 15px;
    font-weight: 700;
    color: var(--white);
    line-height: 1.2;
    text-align: center;
  }

  .card-fr {
    font-size: 11px;
    font-weight: 400;
    color: rgba(255,255,255,0.55);
    text-transform: uppercase;
    letter-spacing: 0.8px;
    text-align: center;
  }

  /* Corner badge glow */
  .card::after {
    content: '';
    position: absolute;
    top: -20px;
    right: -20px;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background: rgba(255,255,255,0.04);
  }

  /* Footer */
  footer {
    position: relative;
    z-index: 2;
    padding: 0 16px 24px;
    text-align: center;
  }

  .time-display {
    font-size: 12px;
    color: rgba(255,255,255,0.3);
    font-weight: 400;
  }

  /* Pulse animation for checkin */
  @keyframes pulse-ring {
    0% { box-shadow: 0 4px 20px rgba(26,106,74,0.35), 0 0 0 0 rgba(26,106,74,0.4); }
    70% { box-shadow: 0 4px 20px rgba(26,106,74,0.35), 0 0 0 8px rgba(26,106,74,0); }
    100% { box-shadow: 0 4px 20px rgba(26,106,74,0.35), 0 0 0 0 rgba(26,106,74,0); }
  }

  /* Stagger entrance animation */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(16px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .card { animation: fadeUp 0.4s ease both; }
  .card:nth-child(1) { animation-delay: 0.05s; }
  .card:nth-child(2) { animation-delay: 0.10s; }
  .card:nth-child(3) { animation-delay: 0.15s; }
  .card:nth-child(4) { animation-delay: 0.20s; }
  .card:nth-child(5) { animation-delay: 0.25s; }
  .card:nth-child(6) { animation-delay: 0.30s; }

  header { animation: fadeUp 0.4s ease both; animation-delay: 0.02s; }
</style>
</head>
<body>

<div class="geo-top"></div>

<header>
  <div class="brand-row">
    <div class="brand-icon">🌴</div>
    <div class="brand-name">Djerba <span>Stays</span></div>
  </div>
  <div class="sub-label">Agent Portal</div>
  <div class="divider"></div>
</header>

<div class="grid">

  <a class="card checkin" href="https://forms.gle/WwEno2HkrthLaC356" target="_blank">
    <div class="icon-wrap">🔑</div>
    <div class="card-texts">
      <div class="card-ar">دخول حريف</div>
      <div class="card-fr">Check-in</div>
    </div>
  </a>

  <a class="card checkout" href="https://forms.gle/PDR1cR1chboGijTz9" target="_blank">
    <div class="icon-wrap">🚪</div>
    <div class="card-texts">
      <div class="card-ar">خروج حريف</div>
      <div class="card-fr">Check-out</div>
    </div>
  </a>

  <a class="card encaissement" href="https://forms.gle/qVjR4GXvzrMruu656" target="_blank">
    <div class="icon-wrap">💰</div>
    <div class="card-texts">
      <div class="card-ar">دفوعات و استخلاص</div>
      <div class="card-fr">Encaissement</div>
    </div>
  </a>

  <a class="card incident" href="https://forms.gle/QyMx8vGTDdLaTwH2A" target="_blank">
    <div class="icon-wrap">⚠️</div>
    <div class="card-texts">
      <div class="card-ar">حوادث و مشاكل</div>
      <div class="card-fr">Incident</div>
    </div>
  </a>

  <a class="card menage" href="https://forms.gle/vmNMGVNgCX2KHWML8" target="_blank">
    <div class="icon-wrap">🧹</div>
    <div class="card-texts">
      <div class="card-ar">تنظيف</div>
      <div class="card-fr">Ménage</div>
    </div>
  </a>

  <a class="card maintenance" href="https://forms.gle/6mWdX1jK29asCTGn6" target="_blank">
    <div class="icon-wrap">🔧</div>
    <div class="card-texts">
      <div class="card-ar">صيانة</div>
      <div class="card-fr">Maintenance</div>
    </div>
  </a>

</div>

<footer>
  <div class="time-display" id="clock"></div>
</footer>

<script>
  function updateClock() {
    const now = new Date();
    const opts = { weekday: 'long', day: 'numeric', month: 'long', hour: '2-digit', minute: '2-digit' };
    document.getElementById('clock').textContent = now.toLocaleDateString('ar-TN', opts);
  }
  updateClock();
  setInterval(updateClock, 60000);
</script>

</body>
</html>