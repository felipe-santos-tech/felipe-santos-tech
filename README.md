<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Space+Grotesk:wght@300;500;700&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Space Grotesk', sans-serif;
    background: #0d1117;
    color: #e6edf3;
    min-height: 100vh;
    padding: 2rem;
  }

  .readme {
    max-width: 860px;
    margin: 0 auto;
    background: #0d1117;
    border: 1px solid #21262d;
    border-radius: 12px;
    overflow: hidden;
  }

  .header {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 2rem;
    padding: 2.5rem 2.5rem 2rem;
    border-bottom: 1px solid #21262d;
    background: linear-gradient(135deg, #0d1117 60%, #111827);
    position: relative;
    overflow: hidden;
  }

  .header::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 200px; height: 200px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(88,166,255,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .header-left h1 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 2rem;
    font-weight: 700;
    color: #e6edf3;
    letter-spacing: -1px;
    margin-bottom: 0.25rem;
  }

  .header-left h1 span { color: #58a6ff; }

  .badge-title {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 20px;
    padding: 4px 14px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: #79c0ff;
    margin-bottom: 1.2rem;
    letter-spacing: 0.5px;
  }

  .badge-title::before { content: '▸'; color: #3fb950; }

  .bio {
    font-size: 0.95rem;
    color: #8b949e;
    line-height: 1.7;
    max-width: 460px;
  }

  .bio strong { color: #e6edf3; }

  .gif-container {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .gif-frame {
    width: 130px; height: 130px;
    border-radius: 50%;
    border: 2px solid #30363d;
    overflow: hidden;
    position: relative;
    background: #161b22;
    display: flex; align-items: center; justify-content: center;
    font-size: 3rem;
  }

  .gif-frame img {
    width: 100%; height: 100%;
    object-fit: cover;
    border-radius: 50%;
  }

  .gif-ring {
    position: absolute;
    inset: -6px;
    border-radius: 50%;
    border: 2px solid transparent;
    background: conic-gradient(from 0deg, #58a6ff, #3fb950, #f78166, #58a6ff) border-box;
    -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: destination-out;
    mask-composite: exclude;
    animation: spin 6s linear infinite;
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .links-row {
    display: flex; gap: 10px; margin-top: 1.2rem; flex-wrap: wrap;
  }

  .link-btn {
    display: inline-flex; align-items: center; gap: 7px;
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 8px;
    padding: 7px 16px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: #e6edf3;
    text-decoration: none;
    transition: all 0.2s;
  }

  .link-btn:hover { border-color: #58a6ff; color: #58a6ff; background: #0d2137; }
  .link-btn .dot { width: 8px; height: 8px; border-radius: 50%; background: #3fb950; animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }

  .section {
    padding: 1.8rem 2.5rem;
    border-bottom: 1px solid #21262d;
  }

  .section:last-child { border-bottom: none; }

  .section-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: #58a6ff;
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-bottom: 1.2rem;
    display: flex; align-items: center; gap: 10px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #21262d;
  }

  .tech-grid {
    display: flex; gap: 10px; flex-wrap: wrap;
  }

  .tech-tag {
    display: inline-flex; align-items: center; gap: 8px;
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 8px;
    padding: 8px 14px;
    font-size: 0.82rem;
    color: #c9d1d9;
    transition: all 0.2s;
  }

  .tech-tag:hover {
    border-color: #30363d;
    transform: translateY(-1px);
    background: #1c2128;
  }

  .tech-tag img { width: 18px; height: 18px; object-fit: contain; }

  .status-bar {
    display: flex; gap: 16px; flex-wrap: wrap;
  }

  .status-item {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 8px;
    padding: 10px 18px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
  }

  .status-item .label { color: #58a6ff; font-size: 0.7rem; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 4px; }
  .status-item .value { color: #e6edf3; font-weight: 700; }

  .typing-demo {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 10px;
    padding: 1.2rem 1.5rem;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.82rem;
    line-height: 2;
  }

  .typing-demo .comment { color: #6e7681; }
  .typing-demo .keyword { color: #ff7b72; }
  .typing-demo .string { color: #a5d6ff; }
  .typing-demo .fn { color: #d2a8ff; }
  .typing-demo .var { color: #79c0ff; }
  .typing-demo .cursor {
    display: inline-block;
    width: 2px; height: 1em;
    background: #58a6ff;
    margin-left: 1px;
    vertical-align: text-bottom;
    animation: blink 1s infinite;
  }

  @keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }

  .snake-gif-section {
    text-align: center;
    padding: 0.5rem 0;
  }

  .wave { display: inline-block; animation: wave-hand 2s infinite; transform-origin: bottom center; }
  @keyframes wave-hand { 0%,100% { transform: rotate(0deg); } 25% { transform: rotate(20deg); } 75% { transform: rotate(-10deg); } }
</style>
</head>
<body>

<div class="readme">

  <!-- HEADER -->
  <div class="header">
    <div class="header-left">
      <div class="badge-title">Fullstack Developer</div>
      <h1>Felipe <span>Santos</span> <span class="wave">👋</span></h1>

      <p class="bio">
        Analista de Sistemas em transição para <strong>Engenharia de Software</strong>.<br>
        Apaixonado por tecnologia — desenvolvo apps <strong>Android nativos</strong> (Kotlin/Java),
        integro e otimizo <strong>bancos de dados SQL</strong> e crio <strong>automações</strong>
        que resolvem problemas reais.
      </p>

      <div class="links-row">
        <a class="link-btn" href="https://www.linkedin.com/in/felipe-santos-tech/">
          <span class="dot"></span> LinkedIn
        </a>
        <a class="link-btn" href="https://felipe-santos-tech.github.io">
          🌐 Portfólio
        </a>
      </div>
    </div>

    <div class="gif-container">
      <div style="position:relative; width:130px; height:130px;">
        <div class="gif-ring"></div>
        <div class="gif-frame">
          <img src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif" alt="coding gif" onerror="this.parentNode.innerHTML='🤖'"/>
        </div>
      </div>
    </div>
  </div>

  <!-- CODE SNIPPET -->
  <div class="section">
    <div class="section-title">// sobre mim</div>
    <div class="typing-demo">
      <div><span class="keyword">const</span> <span class="var">felipe</span> = {</div>
      <div>&nbsp;&nbsp;<span class="var">foco</span>: <span class="string">"Android Nativo · SQL · Automações"</span>,</div>
      <div>&nbsp;&nbsp;<span class="var">missao</span>: <span class="string">"Transformar problemas reais em software eficiente"</span>,</div>
      <div>&nbsp;&nbsp;<span class="var">aprendendo</span>: [<span class="string">"Kotlin"</span>, <span class="string">"Engenharia de Software"</span>],</div>
      <div>&nbsp;&nbsp;<span class="var">disponivel</span>: <span class="keyword">true</span> <span class="comment">// aberto a oportunidades 🚀</span></div>
      <div>}<span class="cursor"></span></div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-title">// stack</div>
    <div class="tech-grid">
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg"/>Java</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/kotlin/kotlin-original.svg"/>Kotlin</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/android/android-original.svg"/>Android</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/androidstudio/androidstudio-original.svg"/>Android Studio</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/delphi/delphi-original.svg"/>Delphi</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/sqlite/sqlite-original.svg"/>SQLite</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg"/>MySQL</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/git/git-original.svg"/>Git</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg"/>HTML5</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg"/>CSS3</span>
      <span class="tech-tag"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg"/>JavaScript</span>
    </div>
  </div>

  <!-- STATUS -->
  <div class="section">
    <div class="section-title">// status atual</div>
    <div class="status-bar">
      <div class="status-item">
        <div class="label">📍 Localização</div>
        <div class="value">Brasil 🇧🇷</div>
      </div>
      <div class="status-item">
        <div class="label">🎯 Foco</div>
        <div class="value">Android + SQL</div>
      </div>
      <div class="status-item">
        <div class="label">📚 Estudando</div>
        <div class="value">Engenharia de SW</div>
      </div>
      <div class="status-item">
        <div class="label">💼 Status</div>
        <div class="value" style="color:#3fb950;">Disponível ✔</div>
      </div>
    </div>
  </div>

  <!-- GIF FOOTER -->
  <div class="section" style="text-align:center; padding: 1.5rem;">
    <img src="https://media.giphy.com/media/M9gbBd9nbDrOTu1T23/giphy.gif" width="80" alt="rocket" style="border-radius:8px; opacity:0.9;"/>
    <p style="margin-top:0.7rem; font-family:'JetBrains Mono',monospace; font-size:0.75rem; color:#484f58;">
      Sempre aberto a novos desafios e oportunidades!
    </p>
  </div>

</div>

</body>
</html>
