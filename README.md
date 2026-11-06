<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>ALAN M. JOSE // SYSTEM PROFILE</title>
<style>
  :root {
    --bg: #0a0e14;
    --panel: #0d1320;
    --border: #1f2b3d;
    --accent: #00ff9c;
    --accent-dim: #00ff9c33;
    --text: #c9d4e3;
    --muted: #5a6b82;
    --warn: #ffb86b;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    min-height: 100vh;
    display: grid;
    place-items: center;
    background:
      radial-gradient(ellipse at 50% -20%, #0e1a2b 0%, var(--bg) 60%),
      var(--bg);
    font-family: "JetBrains Mono", "Fira Code", "Cascadia Code", monospace;
    color: var(--text);
    padding: 2rem 1rem;
    overflow-x: hidden;
  }

  /* scanline overlay */
  body::after {
    content: "";
    position: fixed;
    inset: 0;
    pointer-events: none;
    background: repeating-linear-gradient(
      0deg,
      transparent 0 2px,
      rgba(0, 255, 156, 0.015) 2px 4px
    );
    z-index: 10;
  }

  .card {
    width: min(760px, 100%);
    border: 1px solid var(--border);
    border-radius: 10px;
    background: linear-gradient(180deg, var(--panel), #0a0f18);
    box-shadow:
      0 0 0 1px #000,
      0 0 40px -10px var(--accent-dim),
      inset 0 1px 0 #ffffff08;
    overflow: hidden;
    animation: rise 0.8s cubic-bezier(0.2, 0.9, 0.3, 1) both;
  }

  @keyframes rise {
    from { opacity: 0; transform: translateY(16px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* header */
  .card__head {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    padding: 0.85rem 1.1rem;
    border-bottom: 1px solid var(--border);
    background: #0a1018;
  }

  .dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--muted);
  }
  .dot--r { background: #ff5f57; }
  .dot--y { background: #febc2e; }
  .dot--g { background: #28c840; box-shadow: 0 0 8px #28c840aa; }

  .card__title {
    margin-left: auto;
    font-size: 0.72rem;
    letter-spacing: 0.18em;
    color: var(--muted);
    text-transform: uppercase;
  }

  /* body */
  .card__body { padding: 1.4rem 1.4rem 1.6rem; }

  .id-row {
    display: flex;
    align-items: baseline;
    gap: 0.9rem;
    flex-wrap: wrap;
    margin-bottom: 1.3rem;
  }

  .name {
    font-size: 1.55rem;
    font-weight: 700;
    letter-spacing: 0.03em;
    color: #eaf2ff;
    text-shadow: 0 0 18px var(--accent-dim);
  }

  .handle {
    font-size: 0.8rem;
    color: var(--accent);
    opacity: 0.85;
  }

  .status {
    margin-left: auto;
    display: inline-flex;
    align-items: center;
    gap: 0.45rem;
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    color: var(--accent);
    padding: 0.28rem 0.65rem;
    border: 1px solid #00ff9c40;
    border-radius: 999px;
    background: #00ff9c0d;
    text-transform: uppercase;
  }

  .status::before {
    content: "";
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 10px var(--accent);
    animation: pulse 1.6s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50%      { opacity: 0.35; transform: scale(0.75); }
  }

  /* grid of specs */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 0.9rem;
    margin-bottom: 1.3rem;
  }

  .box {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 0.8rem 0.9rem;
    background: #0b111b;
    transition: border-color 0.25s ease, transform 0.25s ease;
  }

  .box:hover {
    border-color: #00ff9c55;
    transform: translateY(-2px);
  }

  .box__label {
    font-size: 0.64rem;
    letter-spacing: 0.16em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 0.5rem;
  }

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.35rem;
  }

  .tag {
    font-size: 0.72rem;
    padding: 0.18rem 0.5rem;
    border-radius: 4px;
    color: #b9c8dc;
    background: #131d2c;
    border: 1px solid #1d2a3d;
    transition: color 0.2s, border-color 0.2s, background 0.2s;
  }

  .tag:hover {
    color: var(--accent);
    border-color: #00ff9c66;
    background: #00ff9c0d;
  }

  /* domains */
  .domains {
    display: grid;
    gap: 0.5rem;
    margin-bottom: 1.3rem;
  }

  .domain {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-size: 0.78rem;
    padding: 0.5rem 0.7rem;
    border-left: 2px solid #1d2a3d;
    background: linear-gradient(90deg, #0b111b, transparent);
    transition: border-color 0.25s, background 0.25s;
  }

  .domain:hover {
    border-left-color: var(--accent);
    background: linear-gradient(90deg, #00ff9c0a, transparent);
  }

  .domain code {
    color: var(--warn);
    font-size: 0.72rem;
    letter-spacing: 0.05em;
  }

  .domain span { color: var(--text); }

  /* footer */
  .foot {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    font-size: 0.68rem;
    letter-spacing: 0.14em;
    color: var(--muted);
    text-transform: uppercase;
    padding-top: 0.9rem;
    border-top: 1px dashed #1a2436;
  }

  .blink { animation: blink 1.2s steps(2, start) infinite; }
  @keyframes blink { to { visibility: hidden; } }

  /* typing bar */
  .bar {
    height: 2px;
    background: #0f1826;
    overflow: hidden;
    border-radius: 2px;
    margin-top: 0.9rem;
  }
  .bar::before {
    content: "";
    display: block;
    height: 100%;
    width: 35%;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    animation: sweep 2.4s ease-in-out infinite;
  }
  @keyframes sweep {
    0%   { transform: translateX(-120%); }
    100% { transform: translateX(340%); }
  }

  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after { animation: none !important; transition: none !important; }
  }
</style>
</head>
<body>
  <article class="card" role="region" aria-label="System profile for Alan M. Jose">
    <header class="card__head">
      <span class="dot dot--r"></span>
      <span class="dot dot--y"></span>
      <span class="dot dot--g"></span>
      <span class="card__title">system_manifest // alan.m.jose</span>
    </header>

    <div class="card__body">
      <div class="id-row">
        <h1 class="name">ALAN M. JOSE</h1>
        <span class="handle">@sancasle04</span>
        <span class="status">nominal</span>
      </div>

      <div class="grid">
        <div class="box">
          <div class="box__label">Languages</div>
          <div class="tags">
            <span class="tag">C11 / C99</span>
            <span class="tag">C++20</span>
            <span class="tag">x86_64 asm</span>
            <span class="tag">Rust</span>
          </div>
        </div>

        <div class="box">
          <div class="box__label">Subsystems</div>
          <div class="tags">
            <span class="tag">Linux Kernel</span>
            <span class="tag">Memory Mgmt</span>
            <span class="tag">Concurrency</span>
            <span class="tag">POSIX</span>
          </div>
        </div>

        <div class="box">
          <div class="box__label">Toolchain</div>
          <div class="tags">
            <span class="tag">GDB</span>
            <span class="tag">Valgrind</span>
            <span class="tag">QEMU</span>
            <span class="tag">GCC / Clang</span>
          </div>
        </div>
      </div>

      <div class="domains" aria-label="Core domains">
        <div class="domain">
          <code>0x0001</code><span>[SYSTEMS] allocators, cache-friendly structures, pthreads</span>
        </div>
        <div class="domain">
          <code>0x0002</code><span>[KERNEL] custom modules, syscalls, virtual memory</span>
        </div>
        <div class="domain">
          <code>0x0003</code><span>[TOOLING] bare-metal QEMU, GDB dumps, Valgrind profiles</span>
        </div>
      </div>

      <div class="bar" aria-hidden="true"></div>

      <footer class="foot">
        <span>core active <span class="blink">_</span></span>
        <span>0x00 // all systems nominal</span>
      </footer>
    </div>
  </article>
</body>
</html>
