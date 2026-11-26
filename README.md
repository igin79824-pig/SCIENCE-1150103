<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>三年級自然科學｜第3單元：奇妙的空氣 冒險闖關學習網</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;700;900&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Noto Sans TC', sans-serif;
      background-color: #f0f9ff;
      background-image: radial-gradient(#bae6fd 1px, transparent 1px);
      background-size: 24px 24px;
      color: #1e293b;
      scroll-behavior: smooth;
    }
    .quest-tab {
      transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
      cursor: pointer;
    }
    .quest-tab.active {
      background: linear-gradient(135deg, #0284c7, #0d9488);
      color: #ffffff;
      box-shadow: 0 6px 16px rgba(2, 132, 199, 0.35);
      transform: translateY(-2px);
      border-color: #7dd3fc;
    }
    .card-pop {
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .card-pop:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 26px -6px rgba(14, 165, 233, 0.14);
    }
    @keyframes earWagLeft {
      0%, 100% { transform: rotate(0deg); }
      50% { transform: rotate(-7deg); }
    }
    @keyframes earWagRight {
      0%, 100% { transform: rotate(0deg); }
      50% { transform: rotate(7deg); }
    }
    .dog-ear-left {
      transform-origin: 48px 34px;
      animation: earWagLeft 2.4s infinite ease-in-out;
    }
    .dog-ear-right {
      transform-origin: 92px 34px;
      animation: earWagRight 2.4s infinite ease-in-out;
    }
    @keyframes bubbleFloatUp {
      0% { transform: translateY(0) scale(0.85); opacity: 0.95; }
      100% { transform: translateY(-78px) scale(1.25); opacity: 0; }
    }
    .cute-bubble-rise {
      animation: bubbleFloatUp 1.5s infinite ease-out;
    }
    @keyframes leakPop {
      0% { transform: translate(0, 0) scale(0.75); opacity: 1; }
      100% { transform: translate(-28px, -24px) scale(1.3); opacity: 0; }
    }
    .leak-pop-anim {
      animation: leakPop 0.9s ease-out forwards;
    }
    @keyframes stripSwayGentle {
      0%, 100% { transform: rotate(var(--wind-min, -20deg)); }
      50% { transform: rotate(var(--wind-max, -12deg)); }
    }
    @keyframes stripSwayStrong {
      0%, 100% { transform: rotate(var(--wind-min, -68deg)); }
      50% { transform: rotate(var(--wind-max, -56deg)); }
    }
    .paper-strip {
      transform-origin: top left;
      transition: transform 0.22s ease-out;
    }
    .paper-strip.blowing-gentle {
      animation: stripSwayGentle 0.75s infinite ease-in-out;
    }
    .paper-strip.blowing-strong {
      animation: stripSwayStrong 0.16s infinite ease-in-out;
    }
    @keyframes windStreamSlow {
      0% { stroke-dashoffset: 48; opacity: 0.7; }
      100% { stroke-dashoffset: 0; opacity: 0.15; }
    }
    @keyframes windStreamFast {
      0% { stroke-dashoffset: 48; opacity: 0.95; }
      100% { stroke-dashoffset: 0; opacity: 0.2; }
    }
    .wind-stream-slow {
      stroke-dasharray: 10 14;
      animation: windStreamSlow 0.95s linear infinite;
    }
    .wind-stream-fast {
      stroke-dasharray: 14 10;
      animation: windStreamFast 0.25s linear infinite;
    }
    /* 外層輕微施力抖動，不干擾內部活塞 SVG 的 translateY 座標 */
    @keyframes syringeStrain {
      0%, 100% { transform: translateX(0); }
      25% { transform: translateX(-1.5px); }
      75% { transform: translateX(1.5px); }
    }
    .syringe-strain-vibe {
      animation: syringeStrain 0.15s infinite linear;
    }
    .modal-backdrop {
      background-color: rgba(15, 23, 42, 0.65);
      backdrop-filter: blur(4px);
    }
  </style>
</head>
<body class="min-h-screen flex flex-col">

  <!-- ==================== 頂部冒險舞台導覽列 ==================== -->
  <header class="bg-gradient-to-r from-sky-500 via-cyan-500 to-teal-500 text-white shadow-lg sticky top-0 z-40 border-b-4 border-sky-200/60">
    <div class="max-w-6xl mx-auto px-4 py-3 flex flex-wrap items-center justify-between gap-3">
      <div class="flex items-center gap-3">
        <div class="w-14 h-14 rounded-2xl bg-white shadow-md flex items-center justify-center shrink-0 border-2 border-sky-200">
          <svg viewBox="0 0 140 110" class="w-12 h-10">
            <path d="M46,35 C18,32 6,58 14,76 C20,88 38,80 46,60 Z" fill="#ffffff" stroke="#38bdf8" stroke-width="3.5" class="dog-ear-left"/>
            <path d="M94,35 C122,32 134,58 126,76 C120,88 102,80 94,60 Z" fill="#ffffff" stroke="#38bdf8" stroke-width="3.5" class="dog-ear-right"/>
            <ellipse cx="70" cy="56" rx="28" ry="25" fill="#ffffff" stroke="#38bdf8" stroke-width="3.5"/>
            <rect x="46" y="34" width="20" height="13" rx="6" fill="#bae6fd" stroke="#0284c7" stroke-width="2.5"/>
            <rect x="74" y="34" width="20" height="13" rx="6" fill="#bae6fd" stroke="#0284c7" stroke-width="2.5"/>
            <line x1="66" y1="40" x2="74" y2="40" stroke="#0284c7" stroke-width="3"/>
            <circle cx="58" cy="56" r="3.5" fill="#1e293b"/>
            <circle cx="82" cy="56" r="3.5" fill="#1e293b"/>
            <ellipse cx="50" cy="63" rx="4.5" ry="2.5" fill="#fda4af" opacity="0.8"/>
            <ellipse cx="90" cy="63" rx="4.5" ry="2.5" fill="#fda4af" opacity="0.8"/>
            <ellipse cx="70" cy="61" rx="4" ry="2.8" fill="#0284c7"/>
            <path d="M64,67 Q70,73 76,67" fill="none" stroke="#1e293b" stroke-width="2.5" stroke-linecap="round"/>
          </svg>
        </div>
        <div>
          <div class="flex flex-wrap items-center gap-1.5">
            <span class="text-xs font-black tracking-wider bg-amber-300 text-slate-900 px-2.5 py-0.5 rounded-full shadow-sm">三年級自然科學冒險</span>
            <span class="text-xs font-bold bg-white/20 px-2.5 py-0.5 rounded-full">第3單元：奇妙的空氣</span>
          </div>
          <h1 class="text-lg sm:text-2xl font-black tracking-tight mt-0.5 drop-shadow-sm">空氣精靈王國大冒險</h1>
        </div>
      </div>

      <div class="flex flex-wrap items-center gap-2">
        <div class="bg-sky-950/35 backdrop-blur px-3 py-1.5 rounded-2xl border border-white/25 flex items-center gap-2 text-xs font-black" title="完成實驗與25題挑戰可點亮寶石！">
          <span class="text-sky-100 hidden sm:inline">能量寶石：</span>
          <span id="gem-space" class="opacity-35 transition-all text-base" title="空間寶石（完成實驗1）">💎</span>
          <span id="gem-wind" class="opacity-35 transition-all text-base" title="風之寶石（完成實驗2）">🌪️</span>
          <span id="gem-compress" class="opacity-35 transition-all text-base" title="壓縮寶石（完成實驗3）">🎈</span>
          <span id="gem-master" class="opacity-35 transition-all text-base" title="空氣大師徽章（完成25題大挑戰）">👑</span>
        </div>

        <button type="button" onclick="openStudentModal()"
          class="bg-white/20 hover:bg-white/30 text-white px-3.5 py-1.5 rounded-full font-bold text-xs sm:text-sm flex items-center gap-1.5 transition border border-white/40">
          <span>🎒</span>
          <span id="student-badge-text">未登錄探險家（點此設定）</span>
        </button>
      </div>
    </div>

    <nav class="bg-sky-900/35 border-t border-white/20">
      <div class="max-w-6xl mx-auto px-4 py-2 flex flex-wrap gap-2">
        <button type="button" data-tab="notes" class="quest-tab active px-3.5 py-2 rounded-2xl font-black text-xs sm:text-sm bg-white/15 text-white border border-transparent hover:bg-white/25">
          🗺️ 第一關：知識藏寶圖
        </button>
        <button type="button" data-tab="lab" class="quest-tab px-3.5 py-2 rounded-2xl font-black text-xs sm:text-sm bg-white/15 text-white border border-transparent hover:bg-white/25">
          🧪 第二關：魔法空氣實驗室
        </button>
        <button type="button" data-tab="match" class="quest-tab px-3.5 py-2 rounded-2xl font-black text-xs sm:text-sm bg-white/15 text-white border border-transparent hover:bg-white/25">
          🧩 第三關：生活特技配對島
        </button>
        <button type="button" data-tab="quiz" class="quest-tab px-3.5 py-2 rounded-2xl font-black text-xs sm:text-sm bg-white/15 text-white border border-transparent hover:bg-white/25">
          🏆 最終關：25題大魔王挑戰
        </button>
      </div>
    </nav>
  </header>

  <!-- ==================== 主內容區塊 ==================== -->
  <main class="flex-1 max-w-6xl w-full mx-auto px-4 py-6 space-y-6">

    <!-- =========================================================
         第一關：知識藏寶圖
         ========================================================= -->
    <section id="tab-notes" class="tab-panel space-y-6">
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 flex flex-col md:flex-row items-center justify-between gap-4">
        <div class="flex items-start gap-3.5">
          <div class="text-4xl bg-sky-100 w-14 h-14 rounded-2xl flex items-center justify-center shrink-0 border border-sky-200">🐶</div>
          <div>
            <span class="text-xs font-black text-sky-600 bg-sky-50 px-2.5 py-0.5 rounded-full border border-sky-200">空氣小耳狗博士的任務指令</span>
            <h2 class="text-xl sm:text-2xl font-black text-slate-900 mt-1">第一關：破解三大空氣秘密！</h2>
            <p class="text-slate-600 text-sm mt-1">仔細閱讀藏寶圖上的三個秘密卷軸，接著就出發前往「第二關：魔法空氣實驗室」親手收集三顆能量寶石吧！</p>
          </div>
        </div>
        <button type="button" data-go-tab="lab"
          class="shrink-0 bg-gradient-to-r from-amber-400 to-orange-400 hover:from-amber-300 hover:to-orange-300 text-slate-950 font-black px-6 py-3.5 rounded-2xl shadow-md transition flex items-center gap-2 border-2 border-amber-200">
          <span>🚀 前往第二關：動手做實驗</span>
        </button>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 border-t-8 border-t-sky-500 card-pop space-y-4">
          <div class="flex items-center justify-between">
            <span class="bg-sky-100 text-sky-800 font-black px-3 py-1 rounded-full text-xs">卷軸 1｜活動 1</span>
            <span class="text-2xl">🫧</span>
          </div>
          <h3 class="text-xl font-black text-slate-800">空氣在哪裡？</h3>
          <ul class="space-y-2.5 text-slate-700 text-sm leading-relaxed">
            <li class="flex items-start gap-2">
              <span class="text-sky-500 font-black">✦</span>
              <span><strong>無所不在但看不見：</strong>地球除了動植物等生物，還有石頭、水（看得見）和空氣（看不見）等非生物物質。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-sky-500 font-black">✦</span>
              <span><strong>縫隙裡的空氣：</strong>海綿、粉筆裡有許多小縫隙，放入水中擠壓會有<strong>氣泡</strong>冒出來。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-sky-500 font-black">✦</span>
              <span><strong>占有空間：</strong>把塞有紙團的杯子<strong>垂直</strong>壓入水底，杯內空氣占據空間使水進不去，紙團依然是<strong>乾的</strong>；若杯子<strong>傾斜</strong>，空氣會變成氣泡跑出、水就會流進去把紙團弄濕。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-sky-500 font-black">✦</span>
              <span><strong>沒有固定形狀：</strong>可填充游泳圈、籃球、餅乾包裝、防撞氣泡袋；<strong>衣物收納袋</strong>則需抽掉空氣以節省空間。</span>
            </li>
          </ul>
        </div>

        <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-teal-200 border-t-8 border-t-teal-500 card-pop space-y-4">
          <div class="flex items-center justify-between">
            <span class="bg-teal-100 text-teal-800 font-black px-3 py-1 rounded-full text-xs">卷軸 2｜活動 2</span>
            <span class="text-2xl">🌪️</span>
          </div>
          <h3 class="text-xl font-black text-slate-800">空氣還有什麼特性？</h3>
          <ul class="space-y-2.5 text-slate-700 text-sm leading-relaxed">
            <li class="flex items-start gap-2">
              <span class="text-teal-500 font-black">✦</span>
              <span><strong>空氣流動形成風：</strong>推動注射筒活塞使空氣從筒口流出，會形成風吹動紙條；<strong>推到底空氣排完後，風就立刻停止</strong>。空氣流動越快，風就越強。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-teal-500 font-black">✦</span>
              <span><strong>空氣可以被壓縮：</strong>抵住注射筒筒口下壓活塞，空氣體積縮小，<strong>越推越重</strong>；塑膠針筒最多約壓到 <code>4～5 mL</code>（<code>5 atm</code> 極限）就壓不下去。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-teal-500 font-black">✦</span>
              <span><strong>放手彈回原位：</strong>鬆手後被壓縮的空氣會立刻膨脹，若無漏氣會彈回原本 <code>20 mL</code>（說明空氣可被壓縮）；若壓力過大導致空氣跑走，則可能彈回 <code>18 mL</code>。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-teal-500 font-black">✦</span>
              <span><strong>生活應用：</strong>利用空氣<strong>會流動、占有空間、可以被壓縮</strong>等特性，可製作<strong>空氣槍玩具、簡易胡蘿蔔空氣發射器</strong>。</span>
            </li>
          </ul>
        </div>

        <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-emerald-200 border-t-8 border-t-emerald-500 card-pop space-y-4">
          <div class="flex items-center justify-between">
            <span class="bg-emerald-100 text-emerald-800 font-black px-3 py-1 rounded-full text-xs">卷軸 3｜活動 3</span>
            <span class="text-2xl">🌱</span>
          </div>
          <h3 class="text-xl font-black text-slate-800">乾淨空氣重要嗎？</h3>
          <ul class="space-y-2.5 text-slate-700 text-sm leading-relaxed">
            <li class="flex items-start gap-2">
              <span class="text-emerald-500 font-black">✦</span>
              <span><strong>生物生存與自然用途：</strong>動植物呼吸需要空氣；風能幫<strong>蒲公英傳播種子</strong>、推動風帆航行。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-emerald-500 font-black">✦</span>
              <span><strong>空氣汙染來源：</strong>砍伐森林造成塵土飛揚、燃燒稻草與廢棄物、工廠與汽機車排放廢氣。</span>
            </li>
            <li class="flex items-start gap-2">
              <span class="text-emerald-500 font-black">✦</span>
              <span><strong>維護空氣品質做法：</strong>多種樹、短程騎腳踏車或步行、多搭乘大眾運輸工具、使用環保低汙染方式（如風力發電）。</span>
            </li>
          </ul>
        </div>
      </div>

      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-slate-200 space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-2">
          <h3 class="text-lg font-black text-slate-800">🚩 環境部「空氣品質指標（AQI）」6 色旗幟防護裝備表</h3>
          <span class="text-xs font-black text-sky-700 bg-sky-100 px-3 py-1 rounded-full">校園升旗辨識必考重點</span>
        </div>
        <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3 text-center text-sm">
          <div class="rounded-2xl overflow-hidden border-2 border-emerald-200 shadow-sm">
            <div class="bg-emerald-500 text-white font-black py-2">良好（綠旗）</div>
            <div class="p-3 bg-emerald-50 text-slate-700 text-xs leading-relaxed font-medium">戶外活動可安心正常進行</div>
          </div>
          <div class="rounded-2xl overflow-hidden border-2 border-amber-200 shadow-sm">
            <div class="bg-amber-400 text-slate-900 font-black py-2">普通（黃旗）</div>
            <div class="p-3 bg-amber-50 text-slate-700 text-xs leading-relaxed font-medium">戶外活動要小心留意</div>
          </div>
          <div class="rounded-2xl overflow-hidden border-2 border-orange-200 shadow-sm">
            <div class="bg-orange-500 text-white font-black py-2">敏感（橘旗）</div>
            <div class="p-3 bg-orange-50 text-slate-700 text-xs leading-relaxed font-medium">敏感體質（過敏、氣喘）要留意</div>
          </div>
          <div class="rounded-2xl overflow-hidden border-2 border-red-200 shadow-sm">
            <div class="bg-red-600 text-white font-black py-2">不良（紅旗）</div>
            <div class="p-3 bg-red-50 text-slate-700 text-xs leading-relaxed font-medium">避免劇烈運動，下課多待室內休息</div>
          </div>
          <div class="rounded-2xl overflow-hidden border-2 border-purple-200 shadow-sm">
            <div class="bg-purple-700 text-white font-black py-2">非常不良（紫旗）</div>
            <div class="p-3 bg-purple-50 text-slate-700 text-xs leading-relaxed font-medium">暫停戶外活動，外出須配戴口罩</div>
          </div>
          <div class="rounded-2xl overflow-hidden border-2 border-rose-300 shadow-sm">
            <div class="bg-rose-900 text-white font-black py-2">危害（褐紅旗）</div>
            <div class="p-3 bg-rose-50 text-slate-700 text-xs leading-relaxed font-medium">全部停止戶外活動，將門窗緊閉</div>
          </div>
        </div>
      </div>

      <div class="text-center pt-2">
        <button type="button" data-go-tab="lab"
          class="bg-gradient-to-r from-sky-600 to-teal-600 hover:from-sky-700 hover:to-teal-700 text-white font-black text-lg px-8 py-4 rounded-2xl shadow-lg transition inline-flex items-center gap-2">
          <span>🧪 前往第二關：動手做實驗收集寶石 👉</span>
        </button>
      </div>
    </section>

    <!-- =========================================================
         第二關：魔法空氣實驗室
         ========================================================= -->
    <section id="tab-lab" class="tab-panel hidden space-y-6">
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 flex flex-wrap items-center justify-between gap-4">
        <div class="flex items-center gap-3">
          <span class="text-4xl">🧪</span>
          <div>
            <span class="text-xs font-black text-teal-700 bg-teal-100 px-2.5 py-0.5 rounded-full">第二關任務：完成 3 項實驗點亮寶石</span>
            <h2 class="text-2xl font-black text-slate-900 mt-0.5">魔法空氣實驗室</h2>
            <p class="text-slate-600 text-sm">和小藍紙團君、風之精靈、空氣寶寶一起動手驗證空氣的神奇特性！</p>
          </div>
        </div>
        <button type="button" data-go-tab="match"
          class="bg-teal-600 hover:bg-teal-700 text-white font-black px-5 py-3 rounded-2xl shadow transition text-sm">
          🧩 前往第三關：生活特技配對島 →
        </button>
      </div>

      <!-- 實驗一：倒扣杯子壓入水中（垂直壓入/拿出 vs. 斜壓入/斜拿出） -->
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-slate-100 pb-3">
          <div>
            <span class="bg-sky-100 text-sky-800 font-black px-3 py-1 rounded-full text-xs">實驗任務 1｜空氣占有空間 💎</span>
            <h3 class="text-xl font-black text-slate-800 mt-1">拯救「小藍紙團君」！垂直壓入 vs. 斜壓入水中</h3>
          </div>
          <div class="flex flex-wrap gap-2">
            <button type="button" onclick="runCupAction('vertical-down')" class="px-3 py-2 rounded-xl bg-sky-600 hover:bg-sky-700 font-black text-xs sm:text-sm text-white shadow-sm">⬇️ 垂直壓入水底</button>
            <button type="button" onclick="runCupAction('vertical-up')" class="px-3 py-2 rounded-xl bg-sky-100 hover:bg-sky-200 font-black text-xs sm:text-sm text-sky-900">⬆️ 垂直拿出水面</button>
            <button type="button" onclick="runCupAction('tilt-down')" class="px-3 py-2 rounded-xl bg-amber-500 hover:bg-amber-600 font-black text-xs sm:text-sm text-slate-950 shadow-sm">↘️ 斜壓入水中</button>
            <button type="button" onclick="runCupAction('tilt-up')" class="px-3 py-2 rounded-xl bg-amber-100 hover:bg-amber-200 font-black text-xs sm:text-sm text-amber-950">↗️ 斜拿出水面</button>
            <button type="button" onclick="resetDryPaper()" class="px-3 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 font-bold text-xs sm:text-sm text-slate-700">🔄 換新乾紙團</button>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
          <div class="bg-sky-50/80 rounded-2xl p-4 border-2 border-sky-100 flex flex-col items-center">
            <svg viewBox="0 0 340 245" class="w-full max-w-sm">
              <rect x="35" y="75" width="270" height="155" rx="10" fill="#ffffff" stroke="#64748b" stroke-width="3"/>
              <rect x="38" y="115" width="264" height="112" rx="6" fill="#bae6fd" opacity="0.85"/>
              <line x1="38" y1="115" x2="302" y2="115" stroke="#0284c7" stroke-width="2" stroke-dasharray="6 4"/>
              <text x="48" y="132" font-size="11" fill="#0369a1" font-weight="bold">水面線</text>

              <g id="cup-group" transform="translate(0, 0) rotate(0, 170, 75)" style="transition: transform 0.55s cubic-bezier(0.34, 1.56, 0.64, 1);">
                <rect id="cup-inner-water" x="131" y="113" width="78" height="0" fill="#7dd3fc" opacity="0.9"/>
                <rect id="cup-inner-air" x="131" y="30" width="78" height="83" fill="#f0f9ff" opacity="0.85"/>

                <g id="cute-paper-ball">
                  <path id="paper-body" d="M142,35 Q152,25 168,33 Q182,24 196,34 Q202,46 190,53 Q170,58 150,53 Q138,47 142,35 Z" fill="#3b82f6"/>
                  <g id="paper-face-happy">
                    <circle cx="161" cy="42" r="2.3" fill="#ffffff"/>
                    <circle cx="179" cy="42" r="2.3" fill="#ffffff"/>
                    <path d="M165,47 Q170,52 175,47" fill="none" stroke="#ffffff" stroke-width="2" stroke-linecap="round"/>
                    <text x="170" y="66" text-anchor="middle" font-size="10" fill="#1d4ed8" font-weight="bold">乾爽小藍紙團</text>
                  </g>
                  <g id="paper-face-wet" class="hidden">
                    <text x="157" y="44" font-size="9" fill="#ffffff" font-weight="bold">×</text>
                    <text x="176" y="44" font-size="9" fill="#ffffff" font-weight="bold">×</text>
                    <path d="M165,50 Q170,45 175,50" fill="none" stroke="#ffffff" stroke-width="2" stroke-linecap="round"/>
                    <text x="170" y="66" text-anchor="middle" font-size="10" fill="#1e3a8a" font-weight="bold">濕答答紙團💦</text>
                  </g>
                </g>

                <path d="M130,28 L210,28 L216,113 L124,113 Z" fill="none" stroke="#334155" stroke-width="3.2"/>
                <line x1="125" y1="111" x2="215" y2="111" stroke="#0ea5e9" stroke-width="3"/>
              </g>

              <g id="cup-escape-bubbles" class="hidden">
                <g class="cute-bubble-rise">
                  <circle cx="218" cy="145" r="10" fill="#ffffff" stroke="#0284c7" stroke-width="2"/>
                  <circle cx="215" cy="143" r="1.5" fill="#0284c7"/>
                  <circle cx="221" cy="143" r="1.5" fill="#0284c7"/>
                  <path d="M215,147 Q218,150 221,147" fill="none" stroke="#0284c7" stroke-width="1.5"/>
                </g>
                <g class="cute-bubble-rise" style="animation-delay: 0.35s;">
                  <circle cx="235" cy="130" r="8" fill="#ffffff" stroke="#0284c7" stroke-width="2"/>
                  <text x="246" y="125" font-size="10" fill="#0369a1" font-weight="bold">氣泡跑出來！</text>
                </g>
              </g>
            </svg>
            <div id="cup-mode-badge" class="text-xs font-black px-3.5 py-1.5 rounded-full bg-sky-100 text-sky-800 border border-sky-200 mt-1">
              目前狀態：垂直在水面上方（0°）
            </div>
          </div>

          <div class="space-y-3 bg-slate-50 p-5 rounded-2xl border border-slate-200">
            <h4 class="font-black text-slate-800 text-base">🔍 實驗現象與秘密解析：</h4>
            <p id="cup-status-text" class="text-sm text-slate-700 leading-relaxed bg-white p-3.5 rounded-xl border border-sky-100 font-medium">
              小藍紙團君正安全地待在杯底！請依序試試「⬇️ 垂直壓入水底」與「↘️ 斜壓入水中」，比較兩者的差別！
            </p>
            <div class="text-xs text-slate-600 space-y-1.5 pt-1">
              <p>✅ <strong>垂直壓入／垂直拿出：</strong>杯子裡的空氣被關在裡面、<strong>占有空間</strong>，水進不去，所以小藍紙團君取出後<strong>依然是乾的</strong>！</p>
              <p>💦 <strong>斜壓入水中／斜拿出水面：</strong>杯子傾斜時，杯內的空氣會從較高的一側變成<strong>氣泡跑出來</strong>，水趁機流進杯子裡，就把紙團弄濕了！</p>
            </div>
          </div>
        </div>
      </div>

      <!-- 實驗二：推注射筒活塞吹動紙條（微風風速調慢 + 推到底 0 mL 風立刻停止） -->
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-teal-200 space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-slate-100 pb-3">
          <div>
            <span class="bg-teal-100 text-teal-800 font-black px-3 py-1 rounded-full text-xs">實驗任務 2｜空氣流動形成風 🌪️</span>
            <h3 class="text-xl font-black text-slate-800 mt-1">召喚「風之精靈」！比較微風（慢速）與強風（快速），推到底風就停止</h3>
          </div>
          <div class="flex flex-wrap gap-2">
            <button type="button" onclick="resetWindSyringe()" class="px-3.5 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 font-bold text-xs sm:text-sm text-slate-700">🔄 拉回 20 mL 吸滿空氣</button>
            <button type="button" onclick="demoPushWind('gentle')" class="px-3.5 py-2 rounded-xl bg-teal-600 hover:bg-teal-700 font-black text-xs sm:text-sm text-white shadow-sm">🍃 慢慢推（柔和慢微風）</button>
            <button type="button" onclick="demoPushWind('strong')" class="px-3.5 py-2 rounded-xl bg-amber-400 hover:bg-amber-500 font-black text-xs sm:text-sm text-slate-950 shadow-sm">💨 快速推到底（強風）</button>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
          <div class="bg-teal-50/70 rounded-2xl p-4 border-2 border-teal-100 flex flex-col items-center">
            <svg viewBox="0 0 390 180" class="w-full max-w-md">
              <rect x="115" y="55" width="150" height="46" rx="6" fill="#ffffff" stroke="#475569" stroke-width="2.5"/>
              <line x1="135" y1="55" x2="135" y2="65" stroke="#64748b" stroke-width="1.5"/>
              <text x="135" y="49" text-anchor="middle" font-size="9" fill="#475569" font-weight="bold">20</text>
              <line x1="190" y1="55" x2="190" y2="65" stroke="#64748b" stroke-width="1.5"/>
              <text x="190" y="49" text-anchor="middle" font-size="9" fill="#475569" font-weight="bold">10</text>
              <line x1="245" y1="55" x2="245" y2="65" stroke="#64748b" stroke-width="1.5"/>
              <text x="245" y="49" text-anchor="middle" font-size="9" fill="#475569" font-weight="bold">0 mL</text>

              <rect id="wind-air-fill" x="135" y="57" width="128" height="42" fill="#ccfbf1" opacity="0.8"/>

              <g id="wind-plunger-group" transform="translate(0, 0)">
                <rect x="25" y="72" width="98" height="12" fill="#94a3b8" stroke="#475569" stroke-width="1.5"/>
                <rect x="15" y="58" width="10" height="40" rx="3" fill="#64748b"/>
                <rect x="123" y="57" width="12" height="42" rx="2" fill="#1e293b"/>
              </g>

              <rect x="265" y="71" width="22" height="14" rx="2" fill="#e2e8f0" stroke="#475569" stroke-width="2"/>

              <g id="wind-stream-group" class="hidden">
                <line id="wind-line-1" x1="292" y1="68" x2="365" y2="62" stroke="#0284c7" stroke-width="2.5" stroke-linecap="round" class="wind-stream-slow"/>
                <line id="wind-line-2" x1="292" y1="78" x2="375" y2="78" stroke="#0ea5e9" stroke-width="3" stroke-linecap="round" class="wind-stream-slow"/>
                <line id="wind-line-3" x1="292" y1="88" x2="365" y2="94" stroke="#0284c7" stroke-width="2.5" stroke-linecap="round" class="wind-stream-slow"/>
                <g transform="translate(332, 36)">
                  <circle cx="10" cy="14" r="8" fill="#ffffff" stroke="#38bdf8" stroke-width="2"/>
                  <circle cx="20" cy="12" r="10" fill="#ffffff" stroke="#38bdf8" stroke-width="2"/>
                  <circle cx="30" cy="14" r="8" fill="#ffffff" stroke="#38bdf8" stroke-width="2"/>
                  <rect x="10" y="12" width="20" height="10" fill="#ffffff"/>
                  <circle cx="17" cy="14" r="1.5" fill="#0284c7"/>
                  <circle cx="25" cy="14" r="1.5" fill="#0284c7"/>
                  <path d="M19,17 Q21,19 23,17" fill="none" stroke="#0284c7" stroke-width="1.5"/>
                </g>
              </g>

              <g transform="translate(285, 75)">
                <rect id="wind-paper-strip" x="0" y="0" width="7" height="60" rx="3" fill="#f43f5e" class="paper-strip" style="transform: rotate(0deg);"/>
              </g>
            </svg>

            <div class="w-full max-w-sm mt-1">
              <label class="flex justify-between text-xs font-bold text-slate-600 mb-1">
                <span>手動拖曳推桿（往右推排出空氣）：</span>
                <span id="wind-vol-label" class="text-teal-700 font-black">筒內空氣：20 mL</span>
              </label>
              <input type="range" id="wind-slider" min="0" max="20" value="20" dir="rtl" oninput="onManualWindSlide(this.value)" class="w-full accent-teal-600 cursor-pointer">
            </div>
          </div>

          <div class="space-y-3 bg-slate-50 p-5 rounded-2xl border border-slate-200">
            <h4 class="font-black text-slate-800 text-base">🔍 氣流與風力觀察：</h4>
            <p id="wind-status-text" class="text-sm text-slate-700 leading-relaxed bg-white p-3.5 rounded-xl border border-teal-100 font-medium">
              目前注射筒內裝滿 20 mL 空氣，活塞靜止不動，沒有風吹出來，紅紙條自然垂直垂下。請推動活塞試試看！
            </p>
            <div class="text-xs text-slate-600 space-y-1.5 pt-1">
              <p>🍃 <strong>慢慢推（風速慢）：</strong>空氣緩緩從筒口流出，風速較慢，紅紙條只會微微、慢慢地飄動。</p>
              <p>💨 <strong>快速推到底（風速快）：</strong>空氣高速衝出形成強風，紅紙條高高飄起；一旦推到底（<code>0 mL</code>）空氣排光，<strong>風力立刻停止</strong>、紙條自然垂落！</p>
            </div>
          </div>
        </div>
      </div>

      <!-- 實驗三：筒口抵住橡皮擦壓縮空氣（修正活塞向下停留於 5mL/4mL + 放開自動彈回） -->
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-indigo-200 space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-slate-100 pb-3">
          <div>
            <span class="bg-indigo-100 text-indigo-800 font-black px-3 py-1 rounded-full text-xs">實驗任務 3｜空氣可以被壓縮 🎈</span>
            <h3 class="text-xl font-black text-slate-800 mt-1">擠擠「空氣寶寶」！壓到 4 或 5 mL 極限後放開自動彈回</h3>
          </div>
          <div class="flex flex-wrap gap-2">
            <button type="button" onclick="pressAndHold(10)" class="px-3 py-2 rounded-xl bg-emerald-100 hover:bg-emerald-200 font-black text-xs sm:text-sm text-emerald-900">🟢 壓到 10 mL（微阻力）</button>
            <button type="button" onclick="pressAndHold(5)" class="px-3 py-2 rounded-xl bg-orange-100 hover:bg-orange-200 font-black text-xs sm:text-sm text-orange-900">🟠 用力壓到 5 mL（強力頂住）</button>
            <button type="button" onclick="pressAndHold(4)" class="px-3 py-2 rounded-xl bg-rose-500 hover:bg-rose-600 font-black text-xs sm:text-sm text-white shadow-sm">🔴 壓到極限 4 mL（壓不下去！）</button>
            <button type="button" onclick="releasePlungerNow()" class="px-3.5 py-2 rounded-xl bg-indigo-600 hover:bg-indigo-700 font-black text-xs sm:text-sm text-white shadow-sm">🖐️ 放開手指（自動彈回）</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 items-center">
          <!-- 外層容器負責輕微抖動，不干擾內部活塞精準向下位移 -->
          <div id="comp-svg-wrapper" class="bg-indigo-50/70 rounded-2xl p-4 border-2 border-indigo-100 flex flex-col items-center">
            <svg viewBox="0 0 330 275" class="w-full max-w-sm">
              <!-- 桌面與可愛橡皮擦先生 -->
              <rect x="35" y="250" width="260" height="8" rx="4" fill="#cbd5e1"/>
              <rect x="115" y="224" width="100" height="26" rx="6" fill="#ffffff" stroke="#475569" stroke-width="2.5"/>
              <circle cx="152" cy="236" r="2" fill="#334155"/>
              <circle cx="178" cy="236" r="2" fill="#334155"/>
              <path d="M161,240 Q165,243 169,240" fill="none" stroke="#334155" stroke-width="1.8" stroke-linecap="round"/>
              <text x="165" y="268" text-anchor="middle" font-size="10" fill="#475569" font-weight="bold">橡皮擦先生（緊緊封住筒口）</text>

              <!-- 注射筒針筒本體（20mL 在 y=90，0mL 在 y=207，總高 117px） -->
              <rect x="138" y="75" width="54" height="134" rx="5" fill="#ffffff" stroke="#475569" stroke-width="2.5"/>
              <rect x="157" y="209" width="16" height="15" fill="#e2e8f0" stroke="#475569" stroke-width="2"/>

              <!-- 精準對應的刻度線（每 1mL = 5.85px） -->
              <line x1="182" y1="90" x2="192" y2="90" stroke="#475569" stroke-width="1.5"/>
              <text x="198" y="94" font-size="10" fill="#334155" font-weight="bold">20 mL（原位）</text>
              <line x1="182" y1="101.7" x2="192" y2="101.7" stroke="#d97706" stroke-width="1.5" stroke-dasharray="3 2"/>
              <text x="198" y="105.7" font-size="9" fill="#b45309" font-weight="bold">18 mL（空氣跑走）</text>
              <line x1="182" y1="148.5" x2="192" y2="148.5" stroke="#059669" stroke-width="1.5"/>
              <text x="198" y="152.5" font-size="10" fill="#059669" font-weight="bold">10 mL（2 atm）</text>
              <line x1="182" y1="177.7" x2="192" y2="177.7" stroke="#ea580c" stroke-width="1.5"/>
              <text x="198" y="181.7" font-size="10" fill="#ea580c" font-weight="bold">5 mL（4 atm）</text>
              <line x1="182" y1="183.6" x2="192" y2="183.6" stroke="#e11d48" stroke-width="2"/>
              <text x="198" y="189" font-size="9.5" fill="#e11d48" font-weight="bold">4 mL 極限（壓不下去！）</text>

              <!-- 被壓縮的空氣區 -->
              <rect id="comp-air-box" x="140" y="90" width="50" height="117" fill="#dbeafe" opacity="0.85"/>

              <!-- 4 隻可愛空氣寶寶（隨活塞向下一起壓扁在底部） -->
              <g id="air-babies-group">
                <circle id="baby-1" cx="155" cy="125" r="8.5" fill="#93c5fd" stroke="#2563eb" stroke-width="1.5"/>
                <circle id="baby-2" cx="175" cy="142" r="8.5" fill="#93c5fd" stroke="#2563eb" stroke-width="1.5"/>
                <circle id="baby-3" cx="155" cy="165" r="8.5" fill="#93c5fd" stroke="#2563eb" stroke-width="1.5"/>
                <circle id="baby-4" cx="175" cy="188" r="8.5" fill="#93c5fd" stroke="#2563eb" stroke-width="1.5"/>
              </g>

              <!-- 漏氣氣泡 -->
              <g id="comp-leak-bubbles" class="hidden">
                <circle cx="132" cy="182" r="5" fill="#38bdf8" class="leak-pop-anim"/>
                <text x="56" y="178" font-size="10" fill="#be123c" font-weight="bold">空氣可能跑走了💨</text>
              </g>

              <!-- 活塞推桿群組（精準往下移動到 10mL / 5mL / 4mL 刻度） -->
              <g id="comp-plunger-group" transform="translate(0, 0)">
                <rect x="135" y="16" width="60" height="10" rx="3" fill="#64748b"/>
                <rect x="158" y="26" width="14" height="52" fill="#94a3b8" stroke="#475569" stroke-width="1.5"/>
                <rect x="140" y="78" width="50" height="12" rx="2" fill="#1e293b"/>
              </g>
            </svg>

            <!-- 壓力與阻力即時儀表板 -->
            <div class="w-full max-w-sm bg-white p-3 rounded-xl border border-indigo-100 space-y-2 mt-1">
              <div class="flex justify-between text-xs font-black">
                <span id="comp-vol-display" class="text-indigo-800">目前刻度：20 mL（原始體積）</span>
                <span id="comp-atm-display" class="text-sky-700">內部壓力：1.0 atm</span>
              </div>
              <div>
                <div class="flex justify-between text-[11px] font-bold text-slate-500 mb-0.5">
                  <span>指尖感受到的頂回阻力（越推越重）：</span>
                  <span id="comp-force-label" class="text-slate-700">輕鬆（0%）</span>
                </div>
                <div class="w-full h-2.5 bg-slate-100 rounded-full overflow-hidden">
                  <div id="comp-force-bar" class="h-full bg-emerald-500 transition-all duration-200" style="width: 5%;"></div>
                </div>
              </div>
              <div class="text-[11px] font-bold text-indigo-700 flex justify-between">
                <span>拖曳滑桿下壓，放開滑鼠/手指會自動彈回：</span>
                <span>極限：4 mL</span>
              </div>
              <input type="range" id="comp-slider" min="4" max="20" value="20" dir="rtl"
                oninput="onManualCompressSlide(this.value)"
                onchange="releasePlungerNow()"
                class="w-full accent-indigo-600 cursor-pointer">
            </div>
          </div>

          <!-- 觀察結論與放手自動彈回設定 -->
          <div class="space-y-3 bg-slate-50 p-5 rounded-2xl border border-slate-200">
            <h4 class="font-black text-slate-800 text-base">🔍 壓到 4 或 5 mL 極限與「放開自動彈回」觀察：</h4>
            <p id="comp-status-text" class="text-sm text-slate-700 leading-relaxed bg-white p-3.5 rounded-xl border border-indigo-100 font-medium">
              目前筒內有 20 mL 空氣，壓到 <strong>4 或 5 mL 就壓不下去了</strong>！無論拖曳滑桿或按上方按鈕下壓，放開後活塞都會<strong>自動彈回</strong>。
            </p>

            <!-- 選擇「放開後自動彈回」的兩種實驗結果情境 -->
            <div class="bg-white p-3.5 rounded-2xl border border-indigo-200 space-y-2">
              <div class="text-xs font-black text-indigo-950">⚙️ 選擇放開手指後的自動彈回結果（點擊可切換並立即測試）：</div>
              <div class="grid grid-cols-1 gap-2">
                <button type="button" id="rebound-mode-20" onclick="setReboundTargetAndTest(20)"
                  class="w-full text-left p-3 rounded-xl border-2 border-emerald-500 bg-emerald-50 text-emerald-950 transition flex items-center justify-between gap-2">
                  <div>
                    <div class="font-black text-xs sm:text-sm">✅ 情境一：放開自動彈回到 20 mL（目前預設）</div>
                    <div class="text-[11px] text-emerald-800 mt-0.5">說明注射筒完全密封，<strong>空氣可被壓縮</strong>，鬆手後立刻膨脹推回 20 mL！</div>
                  </div>
                  <span class="text-lg">🎈</span>
                </button>

                <button type="button" id="rebound-mode-18" onclick="setReboundTargetAndTest(18)"
                  class="w-full text-left p-3 rounded-xl border-2 border-slate-200 bg-slate-50 hover:bg-amber-50 text-slate-800 transition flex items-center justify-between gap-2">
                  <div>
                    <div class="font-black text-xs sm:text-sm">💨 情境二：放開自動彈回到 18 mL</div>
                    <div class="text-[11px] text-slate-600 mt-0.5">說明壓力太大時，<strong>部分空氣可能從縫隙跑走了</strong>，因此只彈回 18 mL！</div>
                  </div>
                  <span class="text-lg">🫧</span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- =========================================================
         第三關：生活特技配對島（支援複選！）
         ========================================================= -->
    <section id="tab-match" class="tab-panel hidden space-y-6">
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 flex flex-wrap items-center justify-between gap-4">
        <div class="flex items-center gap-3">
          <span class="text-4xl">🧩</span>
          <div>
            <span class="text-xs font-black text-amber-800 bg-amber-100 px-2.5 py-0.5 rounded-full">第三關任務：注意！有些物品同時應用多種特性（可複選）</span>
            <h2 class="text-2xl font-black text-slate-900 mt-0.5">生活特技配對島</h2>
            <p class="text-slate-600 text-sm">請勾選每項物品或活動所應用的空氣特性（<strong>可複選</strong>），勾選完成後按下「✅ 確認配對」！</p>
          </div>
        </div>
        <div class="flex items-center gap-3">
          <span id="match-score-badge" class="bg-amber-100 text-amber-950 font-black px-4 py-2 rounded-2xl text-sm border border-amber-300">
            過關進度：0 / 6 題
          </span>
          <button type="button" onclick="resetMatchGame()" class="px-4 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 font-bold text-sm text-slate-700">
            🔄 重新配對
          </button>
        </div>
      </div>

      <div id="match-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5"></div>
    </section>

    <!-- =========================================================
         最終關：25題大魔王挑戰
         ========================================================= -->
    <section id="tab-quiz" class="tab-panel hidden space-y-6">
      <div class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 flex flex-wrap items-center justify-between gap-4">
        <div class="flex items-center gap-3">
          <span class="text-4xl">🏆</span>
          <div>
            <span class="text-xs font-black text-rose-700 bg-rose-100 px-2.5 py-0.5 rounded-full">最終關卡：滿分 100 分可獲得空氣大師皇冠 👑</span>
            <h2 class="text-2xl font-black text-slate-900 mt-0.5">奇妙的空氣：25題大魔王挑戰</h2>
            <p class="text-slate-600 text-sm">包含觀念是非、實驗變因判斷與第 10 題「鯉魚旗飄動時間紀錄表」素養題。</p>
          </div>
        </div>
        <div class="flex flex-wrap items-center gap-2">
          <button type="button" onclick="openStudentModal()" class="px-3.5 py-2 rounded-xl bg-sky-50 hover:bg-sky-100 text-sky-800 font-bold text-sm border border-sky-200">
            🎒 修改班級座號
          </button>
          <button type="button" id="retry-wrong-btn" onclick="startWrongOnlyQuiz()" class="hidden px-3.5 py-2 rounded-xl bg-rose-100 hover:bg-rose-200 text-rose-800 font-bold text-sm">
            🔁 只看錯題並重新挑戰
          </button>
          <button type="button" onclick="resetFullQuiz()" class="px-3.5 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold text-sm">
            🔄 全部重新作答
          </button>
        </div>
      </div>

      <div class="bg-white rounded-2xl p-4 shadow-sm border border-slate-200">
        <div class="flex items-center justify-between text-xs font-bold text-slate-500 mb-2">
          <span>📌 題號導覽（點擊可快速跳題）：</span>
          <span id="quiz-progress-text">已作答：0 / 25 題</span>
        </div>
        <div id="quiz-nav-pills" class="flex flex-wrap gap-1.5"></div>
      </div>

      <div id="quiz-questions-container" class="space-y-5"></div>

      <div id="quiz-submit-area" class="bg-white rounded-3xl p-6 shadow-sm border-2 border-sky-200 text-center space-y-3">
        <p class="text-sm text-slate-600 font-medium">確認所有題目都作答完成後，請按下「送出考卷並批改」！</p>
        <button type="button" onclick="submitQuiz()"
          class="bg-gradient-to-r from-sky-600 to-teal-600 hover:from-sky-700 hover:to-teal-700 text-white font-black text-lg px-10 py-4 rounded-2xl shadow-lg transition">
          ✅ 送出考卷並批改
        </button>
      </div>

      <div id="quiz-result-card" class="hidden bg-gradient-to-br from-sky-50 via-white to-teal-50 rounded-3xl p-6 sm:p-8 shadow-md border-2 border-sky-300 space-y-5">
        <div class="flex flex-wrap items-center justify-between gap-4 border-b border-sky-200 pb-4">
          <div>
            <span class="bg-sky-600 text-white text-xs font-black px-3 py-1 rounded-full">測驗完成紀錄已自動儲存</span>
            <h3 id="result-student-title" class="text-2xl font-black text-slate-900 mt-2">三年 __ 班 __ 號 成績報告</h3>
          </div>
          <div class="text-right">
            <div class="text-xs font-bold text-slate-500">總得分</div>
            <div id="result-score-num" class="text-5xl font-black text-sky-600">100 <span class="text-lg text-slate-600">分</span></div>
          </div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 text-center">
          <div class="bg-white p-4 rounded-2xl border border-slate-200">
            <div class="text-xs font-bold text-slate-500">答對題數</div>
            <div id="result-correct-count" class="text-2xl font-black text-emerald-600 mt-1">25 / 25 題</div>
          </div>
          <div class="bg-white p-4 rounded-2xl border border-slate-200">
            <div class="text-xs font-bold text-slate-500">待加強題數</div>
            <div id="result-wrong-count" class="text-2xl font-black text-rose-600 mt-1">0 題</div>
          </div>
          <div class="bg-white p-4 rounded-2xl border border-slate-200">
            <div class="text-xs font-bold text-slate-500">學習評語</div>
            <div id="result-comment" class="text-base font-black text-sky-800 mt-1.5">空氣科學小博士！</div>
          </div>
        </div>

        <div class="flex flex-wrap justify-center gap-3 pt-2">
          <button type="button" id="result-retry-wrong-btn" onclick="startWrongOnlyQuiz()"
            class="hidden px-6 py-3 rounded-2xl bg-rose-600 hover:bg-rose-700 text-white font-black shadow transition">
            🔁 只看錯題並重新挑戰
          </button>
          <button type="button" onclick="resetFullQuiz()"
            class="px-6 py-3 rounded-2xl bg-slate-800 hover:bg-slate-900 text-white font-black shadow transition">
            🔄 重新挑戰全部 25 題
          </button>
          <button type="button" onclick="openTeacherPasswordModal()"
            class="px-5 py-3 rounded-2xl bg-amber-100 hover:bg-amber-200 text-amber-950 font-bold border border-amber-300 transition">
            🔒 教師管理 / 匯出作答結果
          </button>
        </div>
      </div>
    </section>
  </main>

  <!-- ==================== 頁尾與隱藏教師管理入口 ==================== -->
  <footer class="bg-slate-900 text-slate-400 py-5 mt-10">
    <div class="max-w-6xl mx-auto px-4 flex flex-wrap items-center justify-between gap-3 text-xs">
      <p>國小三年級自然科學｜第3單元《奇妙的空氣》空氣精靈王國大冒險</p>
      <button type="button" onclick="openTeacherPasswordModal()"
        class="text-slate-300 hover:text-amber-300 bg-slate-800 hover:bg-slate-700 px-3.5 py-2 rounded-xl font-bold transition flex items-center gap-1.5">
        <span>🔒</span>
        <span>教師管理 / 匯出作答結果</span>
      </button>
    </div>
  </footer>

  <!-- =========================================================
       彈窗 1：學生班級與座號登錄視窗
       ========================================================= -->
  <div id="student-modal" class="fixed inset-0 modal-backdrop hidden z-50 flex items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-md w-full p-6 shadow-2xl border-2 border-sky-200 space-y-4">
      <div class="flex items-center justify-between">
        <h3 class="text-xl font-black text-sky-900">🎒 登錄小小探險家資料</h3>
        <button type="button" onclick="closeStudentModal()" class="text-slate-400 hover:text-slate-700 text-xl font-bold">✕</button>
      </div>
      <p class="text-sm text-slate-600">請輸入你的班級與座號，完成最終關 25 題挑戰後系統將自動記錄成績！</p>
      <div class="grid grid-cols-2 gap-3">
        <div>
          <label class="block text-xs font-bold text-slate-700 mb-1">班級（例如：301 或 3年1班）</label>
          <input type="text" id="input-student-class" placeholder="請輸入班級"
            class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:border-sky-500 font-bold">
        </div>
        <div>
          <label class="block text-xs font-bold text-slate-700 mb-1">座號（例如：05 或 5）</label>
          <input type="text" id="input-student-seat" placeholder="請輸入座號"
            class="w-full px-3.5 py-2.5 rounded-xl border border-slate-300 focus:outline-none focus:border-sky-500 font-bold">
        </div>
      </div>
      <div id="student-modal-error" class="hidden text-xs font-bold text-rose-600">⚠️ 請完整填寫班級與座號喔！</div>
      <div class="flex justify-end gap-2 pt-2">
        <button type="button" onclick="closeStudentModal()" class="px-4 py-2.5 rounded-xl bg-slate-100 hover:bg-slate-200 font-bold text-sm text-slate-700">稍後再填</button>
        <button type="button" onclick="saveStudentInfo()" class="px-5 py-2.5 rounded-xl bg-sky-600 hover:bg-sky-700 text-white font-black text-sm shadow">確定登錄</button>
      </div>
    </div>
  </div>

  <!-- =========================================================
       彈窗 2：教師密碼驗證視窗（密碼：991201）
       ========================================================= -->
  <div id="teacher-pwd-modal" class="fixed inset-0 modal-backdrop hidden z-50 flex items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-sm w-full p-6 shadow-2xl border-2 border-amber-200 space-y-4">
      <div class="flex items-center justify-between">
        <h3 class="text-xl font-black text-slate-900">🔐 教師管理驗證</h3>
        <button type="button" onclick="closeTeacherPasswordModal()" class="text-slate-400 hover:text-slate-700 text-xl font-bold">✕</button>
      </div>
      <p class="text-sm text-slate-600">此區域為隱藏線上作答結果統計後台，請輸入教師管理密碼以解鎖匯出功能：</p>
      <div>
        <input type="password" id="teacher-pwd-input" placeholder="請輸入管理密碼"
          onkeydown="if(event.key==='Enter') verifyTeacherPassword()"
          class="w-full px-4 py-3 rounded-xl border border-slate-300 focus:outline-none focus:border-amber-500 font-black tracking-widest text-center text-lg">
        <p id="teacher-pwd-error" class="hidden text-xs font-bold text-rose-600 mt-1.5 text-center">❌ 密碼錯誤，請重新輸入！</p>
      </div>
      <div class="flex justify-end gap-2">
        <button type="button" onclick="closeTeacherPasswordModal()" class="px-4 py-2 rounded-xl bg-slate-100 hover:bg-slate-200 font-bold text-sm text-slate-700">取消</button>
        <button type="button" onclick="verifyTeacherPassword()" class="px-5 py-2 rounded-xl bg-amber-500 hover:bg-amber-600 text-slate-950 font-black text-sm shadow">解鎖後台</button>
      </div>
    </div>
  </div>

  <!-- =========================================================
       彈窗 3：教師作答成績管理與 CSV 匯出後台
       ========================================================= -->
  <div id="teacher-dashboard-modal" class="fixed inset-0 modal-backdrop hidden z-50 flex items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-4xl w-full max-h-[90vh] flex flex-col shadow-2xl border border-slate-200 overflow-hidden">
      <div class="bg-slate-900 text-white px-6 py-4 flex items-center justify-between">
        <div>
          <span class="text-xs font-bold text-amber-400">教師專屬隱藏後台（已通過驗證）</span>
          <h3 class="text-xl font-black">📊 線上作答結果統計與成績單匯出</h3>
        </div>
        <button type="button" onclick="closeTeacherDashboard()" class="text-slate-300 hover:text-white text-2xl font-bold">✕</button>
      </div>

      <div class="p-6 overflow-y-auto space-y-5 flex-1">
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
          <div class="bg-sky-50 p-4 rounded-2xl border border-sky-200">
            <div class="text-xs font-bold text-sky-700">累計作答人次</div>
            <div id="stat-total-count" class="text-2xl font-black text-sky-950 mt-1">0 人</div>
          </div>
          <div class="bg-emerald-50 p-4 rounded-2xl border border-emerald-200">
            <div class="text-xs font-bold text-emerald-700">全體平均分數</div>
            <div id="stat-avg-score" class="text-2xl font-black text-emerald-950 mt-1">0 分</div>
          </div>
          <div class="bg-rose-50 p-4 rounded-2xl border border-rose-200">
            <div class="text-xs font-bold text-rose-700">最高頻錯題 TOP 3</div>
            <div id="stat-top-wrong" class="text-sm font-black text-rose-950 mt-1.5">尚無作答紀錄</div>
          </div>
        </div>

        <div class="flex flex-wrap items-center justify-between gap-2 bg-slate-50 p-3.5 rounded-2xl border border-slate-200">
          <div class="flex flex-wrap gap-2">
            <button type="button" onclick="exportRecordsCSV()"
              class="px-4 py-2.5 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white font-black text-sm shadow flex items-center gap-1.5">
              <span>📥</span>
              <span>匯出 Excel 成績單 (.csv)</span>
            </button>
            <button type="button" onclick="copyRecordsSummary()"
              class="px-4 py-2.5 rounded-xl bg-sky-600 hover:bg-sky-700 text-white font-black text-sm shadow flex items-center gap-1.5">
              <span>📋</span>
              <span>複製文字報告</span>
            </button>
          </div>
          <button type="button" onclick="clearAllTeacherRecords()"
            class="px-3.5 py-2 rounded-xl bg-rose-100 hover:bg-rose-200 text-rose-800 font-bold text-xs">
            🗑️ 清空所有紀錄
          </button>
        </div>

        <div class="overflow-x-auto border border-slate-200 rounded-2xl">
          <table class="w-full text-left text-sm">
            <thead class="bg-slate-100 text-slate-700 font-black text-xs uppercase">
              <tr>
                <th class="px-4 py-3">班級</th>
                <th class="px-4 py-3">座號</th>
                <th class="px-4 py-3">總分</th>
                <th class="px-4 py-3">答對題數</th>
                <th class="px-4 py-3">錯題題號</th>
                <th class="px-4 py-3">完成時間</th>
              </tr>
            </thead>
            <tbody id="teacher-records-tbody" class="divide-y divide-slate-200 bg-white">
              <tr>
                <td colspan="6" class="px-4 py-8 text-center text-slate-400 font-bold">目前尚無學生完成測驗紀錄</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>

  <!-- =========================================================
       JavaScript 核心互動邏輯
       ========================================================= -->
  <script>
    // ==================== 1. Web Audio API 音效引擎 ====================
    const AudioCtx = window.AudioContext || window.webkitAudioContext;
    let audioCtx = null;

    function ensureAudioCtx() {
      if (!audioCtx && AudioCtx) audioCtx = new AudioCtx();
      if (audioCtx && audioCtx.state === 'suspended') audioCtx.resume();
    }

    function playTone(freq, duration = 0.15, type = 'sine', vol = 0.12) {
      try {
        ensureAudioCtx();
        if (!audioCtx) return;
        const osc = audioCtx.createOscillator();
        const gain = audioCtx.createGain();
        osc.type = type;
        osc.frequency.setValueAtTime(freq, audioCtx.currentTime);
        gain.gain.setValueAtTime(vol, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + duration);
        osc.connect(gain);
        gain.connect(audioCtx.destination);
        osc.start();
        osc.stop(audioCtx.currentTime + duration);
      } catch (e) {}
    }

    function playWindNoise(duration = 0.35, volume = 0.08) {
      try {
        ensureAudioCtx();
        if (!audioCtx) return;
        const bufferSize = Math.floor(audioCtx.sampleRate * duration);
        const buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
        const data = buffer.getChannelData(0);
        for (let i = 0; i < bufferSize; i++) {
          data[i] = (Math.random() * 2 - 1) * Math.sin((i / bufferSize) * Math.PI);
        }
        const noise = audioCtx.createBufferSource();
        noise.buffer = buffer;
        const filter = audioCtx.createBiquadFilter();
        filter.type = 'bandpass';
        filter.frequency.value = 600;
        const gain = audioCtx.createGain();
        gain.gain.setValueAtTime(volume, audioCtx.currentTime);
        gain.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + duration);
        noise.connect(filter);
        filter.connect(gain);
        gain.connect(audioCtx.destination);
        noise.start();
      } catch (e) {}
    }

    function playCorrectSound() {
      playTone(523.25, 0.12, 'triangle', 0.15);
      setTimeout(() => playTone(659.25, 0.18, 'triangle', 0.15), 100);
    }

    function playWrongSound() {
      playTone(220, 0.22, 'sawtooth', 0.1);
    }

    function unlockGem(gemId) {
      const el = document.getElementById(gemId);
      if (el && el.classList.contains('opacity-35')) {
        el.classList.remove('opacity-35');
        el.classList.add('scale-125');
        setTimeout(() => el.classList.remove('scale-125'), 400);
      }
    }

    // ==================== 2. 分頁切換與全域跳轉委派 ====================
    function switchTab(tabId) {
      document.querySelectorAll('.tab-panel').forEach(panel => panel.classList.add('hidden'));
      const targetPanel = document.getElementById('tab-' + tabId);
      if (targetPanel) targetPanel.classList.remove('hidden');

      document.querySelectorAll('.quest-tab').forEach(btn => {
        if (btn.getAttribute('data-tab') === tabId) btn.classList.add('active');
        else btn.classList.remove('active');
      });

      window.scrollTo({ top: 0, behavior: 'smooth' });

      if (tabId === 'quiz' && (!studentInfo.className || !studentInfo.seatNo)) {
        openStudentModal();
      }
    }

    document.addEventListener('click', (e) => {
      const tabBtn = e.target.closest('[data-tab]');
      if (tabBtn) {
        e.preventDefault();
        switchTab(tabBtn.getAttribute('data-tab'));
        return;
      }
      const goTabBtn = e.target.closest('[data-go-tab]');
      if (goTabBtn) {
        e.preventDefault();
        switchTab(goTabBtn.getAttribute('data-go-tab'));
      }
    });

    // ==================== 3. 學生班級座號管理 ====================
    const STUDENT_KEY = 'air_unit3_student_info';
    let studentInfo = { className: '', seatNo: '' };

    function loadStudentInfo() {
      try {
        const saved = localStorage.getItem(STUDENT_KEY);
        if (saved) {
          studentInfo = JSON.parse(saved);
          updateStudentBadge();
        }
      } catch (e) {}
    }

    function updateStudentBadge() {
      const badgeText = document.getElementById('student-badge-text');
      if (studentInfo.className && studentInfo.seatNo) {
        badgeText.textContent = `探險家：${studentInfo.className} 班 ${studentInfo.seatNo} 號`;
      } else {
        badgeText.textContent = '未登錄探險家（點此設定）';
      }
    }

    function openStudentModal() {
      document.getElementById('input-student-class').value = studentInfo.className || '';
      document.getElementById('input-student-seat').value = studentInfo.seatNo || '';
      document.getElementById('student-modal-error').classList.add('hidden');
      document.getElementById('student-modal').classList.remove('hidden');
    }

    function closeStudentModal() {
      document.getElementById('student-modal').classList.add('hidden');
    }

    function saveStudentInfo() {
      const cls = document.getElementById('input-student-class').value.trim();
      const seat = document.getElementById('input-student-seat').value.trim();
      if (!cls || !seat) {
        document.getElementById('student-modal-error').classList.remove('hidden');
        return;
      }
      studentInfo = { className: cls, seatNo: seat };
      localStorage.setItem(STUDENT_KEY, JSON.stringify(studentInfo));
      updateStudentBadge();
      closeStudentModal();
      playCorrectSound();
    }

    // ==================== 4. 第二關：魔法空氣實驗室 ====================

    // --- 實驗 1：倒扣杯子壓入水中 ---
    let isPaperWet = false;

    function updatePaperAppearance(wet) {
      isPaperWet = wet;
      const body = document.getElementById('paper-body');
      const happy = document.getElementById('paper-face-happy');
      const wetFace = document.getElementById('paper-face-wet');
      const innerWater = document.getElementById('cup-inner-water');

      if (wet) {
        body.setAttribute('fill', '#1d4ed8');
        happy.classList.add('hidden');
        wetFace.classList.remove('hidden');
      } else {
        body.setAttribute('fill', '#3b82f6');
        happy.classList.remove('hidden');
        wetFace.classList.add('hidden');
        innerWater.setAttribute('y', '113');
        innerWater.setAttribute('height', '0');
      }
    }

    function runCupAction(action) {
      const cupGroup = document.getElementById('cup-group');
      const bubbles = document.getElementById('cup-escape-bubbles');
      const badge = document.getElementById('cup-mode-badge');
      const status = document.getElementById('cup-status-text');
      const innerWater = document.getElementById('cup-inner-water');

      bubbles.classList.add('hidden');

      if (action === 'vertical-down') {
        cupGroup.setAttribute('transform', 'translate(0, 102) rotate(0, 170, 75)');
        badge.textContent = '目前狀態：垂直壓入水底（0°）';
        if (!isPaperWet) {
          status.innerHTML = '💎 <strong>實驗成功（點亮空間寶石）：</strong>垂直壓入水底時，杯子裡的<strong>空氣占有空間</strong>把水擋在外面，小藍紙團君完全沒碰到水，還是乾爽的！';
          unlockGem('gem-space');
          playCorrectSound();
        } else {
          status.innerHTML = '⚠️ 剛才紙團已經濕掉了喔！請先按「🔄 換新乾紙團」，再試試垂直壓入水底！';
        }
      } else if (action === 'vertical-up') {
        cupGroup.setAttribute('transform', 'translate(0, 0) rotate(0, 170, 75)');
        badge.textContent = '目前狀態：垂直拿出水面（0°）';
        if (!isPaperWet) {
          status.innerHTML = '✨ <strong>垂直拿出水面：</strong>全程保持垂直，空氣沒有跑掉、水也沒有流進去，取出後的紙團<strong>還是乾的</strong>！';
          playTone(580, 0.14, 'sine', 0.1);
        } else {
          status.innerHTML = '💦 紙團之前因為杯子傾斜進水已經濕掉了，按「🔄 換新乾紙團」可重新實驗！';
        }
      } else if (action === 'tilt-down') {
        cupGroup.setAttribute('transform', 'translate(0, 95) rotate(-26, 170, 75)');
        bubbles.classList.remove('hidden');
        innerWater.setAttribute('y', '42');
        innerWater.setAttribute('height', '71');
        updatePaperAppearance(true);
        badge.textContent = '目前狀態：斜壓入水中（傾斜 26°）';
        status.innerHTML = '🫧 <strong>斜壓入水中：</strong>杯子一傾斜，裡面的空氣就變成<strong>氣泡冒出來跑掉了</strong>，水立刻流進杯子裡，把小藍紙團君弄濕啦！';
        playWrongSound();
      } else if (action === 'tilt-up') {
        cupGroup.setAttribute('transform', 'translate(0, 12) rotate(-26, 170, 75)');
        bubbles.classList.remove('hidden');
        innerWater.setAttribute('y', '52');
        innerWater.setAttribute('height', '61');
        updatePaperAppearance(true);
        badge.textContent = '目前狀態：斜拿出水面（傾斜 26°）';
        status.innerHTML = '🫧 <strong>斜拿出水面：</strong>拿出水面的過程中如果把杯子傾斜，水一樣會灌進杯口把紙團弄濕喔！';
        playWrongSound();
      }
    }

    function resetDryPaper() {
      updatePaperAppearance(false);
      document.getElementById('cup-escape-bubbles').classList.add('hidden');
      document.getElementById('cup-group').setAttribute('transform', 'translate(0, 0) rotate(0, 170, 75)');
      document.getElementById('cup-mode-badge').textContent = '目前狀態：已換上全新乾紙團（0°）';
      document.getElementById('cup-status-text').innerHTML = '✨ 已換上全新的乾爽小藍紙團君！請選擇上方按鈕操作實驗。';
      playTone(520, 0.1, 'sine', 0.08);
    }

    // --- 實驗 2：推注射筒活塞吹動紙條（微風風速調慢 + 推到底 0 mL 風立刻停止） ---
    let currentWindVol = 20;
    let windDemoTimer = null;
    let windStopTimeout = null;

    function renderWindSyringe(vol, isPushing = false, speedMode = 'gentle') {
      currentWindVol = vol;
      document.getElementById('wind-slider').value = vol;
      const translateX = ((20 - vol) / 20) * 130;
      document.getElementById('wind-plunger-group').setAttribute('transform', `translate(${translateX}, 0)`);

      const airWidth = Math.max(0, (vol / 20) * 128);
      document.getElementById('wind-air-fill').setAttribute('x', 263 - airWidth);
      document.getElementById('wind-air-fill').setAttribute('width', airWidth);
      document.getElementById('wind-vol-label').textContent = `筒內空氣：${vol} mL`;

      const strip = document.getElementById('wind-paper-strip');
      const streamGroup = document.getElementById('wind-stream-group');
      const statusText = document.getElementById('wind-status-text');
      const lines = [
        document.getElementById('wind-line-1'),
        document.getElementById('wind-line-2'),
        document.getElementById('wind-line-3')
      ];

      if (isPushing && vol > 0) {
        streamGroup.classList.remove('hidden');
        strip.classList.remove('blowing-gentle', 'blowing-strong');
        if (speedMode === 'strong') {
          lines.forEach(l => l.setAttribute('class', 'wind-stream-fast'));
          strip.style.setProperty('--wind-min', '-68deg');
          strip.style.setProperty('--wind-max', '-56deg');
          strip.classList.add('blowing-strong');
          statusText.innerHTML = `💨 <strong>強風吹出中（風速快，剩餘 ${vol} mL）：</strong>快速推動活塞，空氣高速衝出形成強風，紅紙條高高飄揚！`;
        } else {
          lines.forEach(l => l.setAttribute('class', 'wind-stream-slow'));
          strip.style.setProperty('--wind-min', '-20deg');
          strip.style.setProperty('--wind-max', '-12deg');
          strip.classList.add('blowing-gentle');
          statusText.innerHTML = `🍃 <strong>微風吹出中（風速慢，剩餘 ${vol} mL）：</strong>慢慢推動活塞，空氣緩緩流出形成柔和微風，紅紙條輕輕慢慢飄動。`;
        }
      } else {
        streamGroup.classList.add('hidden');
        strip.classList.remove('blowing-gentle', 'blowing-strong');
        strip.style.transform = 'rotate(0deg)';

        if (vol === 0) {
          unlockGem('gem-wind');
          statusText.innerHTML = `🛑 <strong>推到底了（0 mL，已點亮風之寶石 🌪️）：</strong>筒內空氣已全部排出，沒有空氣繼續流出，<strong>風力立刻停止</strong>，紅紙條自然垂落！`;
        } else {
          statusText.innerHTML = `⏸️ <strong>活塞靜止（剩餘 ${vol} mL）：</strong>空氣沒有流動，因此沒有風，紅紙條自然垂下。`;
        }
      }
    }

    function resetWindSyringe() {
      clearInterval(windDemoTimer);
      clearTimeout(windStopTimeout);
      renderWindSyringe(20, false);
    }

    function onManualWindSlide(val) {
      clearInterval(windDemoTimer);
      clearTimeout(windStopTimeout);
      const newVol = Number(val);
      const diff = currentWindVol - newVol;

      if (diff > 0 && newVol > 0) {
        const mode = diff >= 3 ? 'strong' : 'gentle';
        renderWindSyringe(newVol, true, mode);
        windStopTimeout = setTimeout(() => {
          renderWindSyringe(newVol, false);
        }, 320);
      } else {
        renderWindSyringe(newVol, false);
      }
    }

    function demoPushWind(mode) {
      clearInterval(windDemoTimer);
      clearTimeout(windStopTimeout);

      if (currentWindVol <= 0) {
        renderWindSyringe(20, false);
      }

      // 微風推得更慢 (210ms/mL，約 4.2 秒緩緩推完)，強風快速推完 (35ms/mL)
      const stepMs = mode === 'strong' ? 35 : 210;
      playWindNoise(mode === 'strong' ? 0.55 : 1.6, mode === 'strong' ? 0.1 : 0.035);

      windDemoTimer = setInterval(() => {
        if (currentWindVol > 1) {
          renderWindSyringe(currentWindVol - 1, true, mode);
        } else {
          clearInterval(windDemoTimer);
          renderWindSyringe(0, false);
        }
      }, stepMs);
    }

    // --- 實驗 3：筒口抵住橡皮擦壓縮空氣（修正活塞向下位移 + 壓到 4或5 mL 放開自動彈回） ---
    let reboundTargetVol = 20; // 20 mL（空氣可被壓縮）或 18 mL（空氣可能跑走）
    let autoReleaseTimer = null;

    function setReboundTargetAndTest(targetVol) {
      reboundTargetVol = targetVol;
      const btn20 = document.getElementById('rebound-mode-20');
      const btn18 = document.getElementById('rebound-mode-18');

      if (targetVol === 20) {
        btn20.className = 'w-full text-left p-3 rounded-xl border-2 border-emerald-500 bg-emerald-50 text-emerald-950 transition flex items-center justify-between gap-2';
        btn18.className = 'w-full text-left p-3 rounded-xl border-2 border-slate-200 bg-slate-50 hover:bg-amber-50 text-slate-800 transition flex items-center justify-between gap-2';
      } else {
        btn18.className = 'w-full text-left p-3 rounded-xl border-2 border-amber-500 bg-amber-50 text-amber-950 transition flex items-center justify-between gap-2';
        btn20.className = 'w-full text-left p-3 rounded-xl border-2 border-slate-200 bg-slate-50 hover:bg-emerald-50 text-slate-800 transition flex items-center justify-between gap-2';
      }

      // 立即示範壓到 4 mL 極限後放開自動彈回
      pressAndHold(4);
    }

    function updateCompressUI(vol, isHolding = true, customMessage = null) {
      const clampedVol = Math.max(4, Math.min(20, Number(vol)));
      document.getElementById('comp-slider').value = clampedVol;

      // 精準線性比例：20mL 在 y=90 (translateY=0)，0mL 在 y=207 (總高度 117px)
      // 10mL -> translateY = 58.5；5mL -> translateY = 87.75；4mL -> translateY = 93.6
      const translateY = ((20 - clampedVol) / 20) * 117;
      const plungerGroup = document.getElementById('comp-plunger-group');
      plungerGroup.setAttribute('transform', `translate(0, ${translateY})`);

      const airTopY = 90 + translateY;
      const airHeight = 207 - airTopY;
      const airBox = document.getElementById('comp-air-box');
      airBox.setAttribute('y', airTopY);
      airBox.setAttribute('height', airHeight);

      // 4 隻空氣寶寶同步往下擠在空氣區內
      const ratio = airHeight / 117;
      document.getElementById('baby-1').setAttribute('cy', 207 - 82 * ratio);
      document.getElementById('baby-2').setAttribute('cy', 207 - 65 * ratio);
      document.getElementById('baby-3').setAttribute('cy', 207 - 42 * ratio);
      document.getElementById('baby-4').setAttribute('cy', 207 - 19 * ratio);

      const atm = (20 / clampedVol).toFixed(1);
      document.getElementById('comp-vol-display').textContent = `目前刻度：${clampedVol} mL`;
      document.getElementById('comp-atm-display').textContent = `內部壓力：${atm} atm`;

      const forceBar = document.getElementById('comp-force-bar');
      const forceLabel = document.getElementById('comp-force-label');
      const statusText = document.getElementById('comp-status-text');
      const wrapper = document.getElementById('comp-svg-wrapper');

      wrapper.classList.remove('syringe-strain-vibe');

      if (customMessage) {
        forceBar.style.width = '5%';
        forceBar.className = 'h-full bg-emerald-500 transition-all duration-200';
        forceLabel.textContent = '已放手自動彈回';
        airBox.setAttribute('fill', '#dbeafe');
        statusText.innerHTML = customMessage;
        return;
      }

      if (!isHolding || clampedVol === 20) {
        forceBar.style.width = '5%';
        forceBar.className = 'h-full bg-emerald-500 transition-all duration-200';
        forceLabel.textContent = '輕鬆（無施力）';
        airBox.setAttribute('fill', '#dbeafe');
        statusText.innerHTML = '目前筒內裝有 20 mL 空氣，壓到 <strong>4 或 5 mL 就壓不下去了</strong>！請試著下壓，放開後活塞會自動彈回。';
        return;
      }

      if (clampedVol >= 10) {
        const pct = Math.round(((20 - clampedVol) / 10) * 35) + 10;
        forceBar.style.width = `${pct}%`;
        forceBar.className = 'h-full bg-emerald-500 transition-all duration-200';
        forceLabel.textContent = `還算輕鬆（阻力 ${pct}%）`;
        airBox.setAttribute('fill', '#93c5fd');
        statusText.innerHTML = `🟢 <strong>下壓至 ${clampedVol} mL（約 ${atm} atm）：</strong>活塞往下移動到 ${clampedVol} mL，還算輕鬆，放開手指後會自動彈回！`;
      } else if (clampedVol >= 5) {
        const pct = Math.round(45 + ((10 - clampedVol) / 5) * 42);
        forceBar.style.width = `${pct}%`;
        forceBar.className = 'h-full bg-orange-500 transition-all duration-200';
        forceLabel.textContent = `阻力倍數暴增！（${pct}%）`;
        airBox.setAttribute('fill', '#60a5fa');
        wrapper.classList.add('syringe-strain-vibe');
        statusText.innerHTML = `🟠 <strong>用力下壓至 ${clampedVol} mL（約 ${atm} atm）：</strong>活塞往下壓到 ${clampedVol} mL，越推越重、幾乎壓不下去了！放開後會自動彈回。`;
      } else {
        forceBar.style.width = '100%';
        forceBar.className = 'h-full bg-rose-600 transition-all duration-200';
        forceLabel.textContent = '極限 4 mL！再也壓不下去了（100%）';
        airBox.setAttribute('fill', '#3b82f6');
        wrapper.classList.add('syringe-strain-vibe');
        statusText.innerHTML = `🔴 <strong>壓到極限 4 mL 就再也壓不下去了（5.0 atm）：</strong>活塞已緊緊往下壓至 4 mL，鬆手後即將自動彈回！`;
      }
    }

    // 點擊按鈕下壓後，短暫停留展示下壓狀態，接著自動放開彈回
    function pressAndHold(targetVol) {
      clearTimeout(autoReleaseTimer);
      document.getElementById('comp-leak-bubbles').classList.add('hidden');
      playTone(280 + (20 - targetVol) * 22, 0.16, 'sine', 0.1);
      updateCompressUI(targetVol, true);

      autoReleaseTimer = setTimeout(() => {
        releasePlungerNow();
      }, 1350);
    }

    function onManualCompressSlide(val) {
      clearTimeout(autoReleaseTimer);
      document.getElementById('comp-leak-bubbles').classList.add('hidden');
      updateCompressUI(Number(val), true);
    }

    function releasePlungerNow() {
      clearTimeout(autoReleaseTimer);
      unlockGem('gem-compress');

      if (reboundTargetVol === 20) {
        document.getElementById('comp-leak-bubbles').classList.add('hidden');
        playCorrectSound();
        updateCompressUI(
          20,
          false,
          '✅ <strong>放開後自動彈回到 20 mL（已點亮壓縮寶石 🎈）：</strong>說明注射筒完全密封沒有漏氣，<strong>空氣可以被壓縮</strong>，一鬆手就會立刻膨脹推回原本 20 mL 的位置！'
        );
      } else {
        const leakEl = document.getElementById('comp-leak-bubbles');
        leakEl.classList.remove('hidden');
        playWindNoise(0.4, 0.1);
        updateCompressUI(
          18,
          false,
          '💨 <strong>放開後自動彈回到 18 mL（已點亮壓縮寶石 🎈）：</strong>因為剛才用力下壓時壓力太大，<strong>部分空氣可能從橡皮擦或活塞縫隙跑走了</strong>，所以只彈回到 18 mL 喔！'
        );
      }
    }

    // ==================== 5. 第三關：生活特技配對島（支援複選！） ====================
    const matchItems = [
      {
        id: 'm1',
        emoji: '🥨',
        title: '澎澎的餅乾包裝袋',
        desc: '袋子裡充入氣體變得鼓鼓的，保護餅乾不被壓碎。',
        answers: ['A'],
        explain: '充入空氣占滿袋內空間並形成緩衝墊，避免餅乾碎裂。'
      },
      {
        id: 'm2',
        emoji: '🪁',
        title: '在草地上放風箏',
        desc: '風箏迎風飛上高空，在藍天中隨風飄揚。',
        answers: ['C'],
        explain: '空氣流動形成風，風吹動風箏產生向上的升力。'
      },
      {
        id: 'm3',
        emoji: '🔫',
        title: '空氣槍玩具 / 空氣發射器',
        desc: '推動活塞擠壓筒內空氣，將前端子彈或胡蘿蔔塊射出去。',
        answers: ['A', 'B', 'C'],
        isMulti: true,
        explain: '空氣槍與空氣發射器同時利用了空氣「A. 占有空間」、「B. 可以被壓縮、傳送力量」以及「C. 快速流動形成風」三項特性！'
      },
      {
        id: 'm4',
        emoji: '⛵',
        title: '海上玩風帆船',
        desc: '風吹進大大的船帆裡，推動風帆在水面上前進。',
        answers: ['C'],
        explain: '空氣流動形成的風具有力量，能推動風帆航行。'
      },
      {
        id: 'm5',
        emoji: '🧳',
        title: '壓縮衣物收納袋',
        desc: '把厚棉被裝入袋中並將袋裡的空氣抽出來，體積變扁好收納。',
        answers: ['A'],
        explain: '空氣占有空間，把衣物縫隙與袋內的空氣排出就能節省收納空間。'
      },
      {
        id: 'm6',
        emoji: '🛟',
        title: '充氣後的游泳圈',
        desc: '原本扁扁的游泳圈灌滿空氣後變得圓滾滾，能幫人浮在水面上。',
        answers: ['A'],
        explain: '空氣沒有固定形狀且占有空間，能填充游泳圈使其鼓起產生浮力。'
      }
    ];

    const matchOptions = [
      { key: 'A', label: 'A. 空氣占有空間、無固定形狀' },
      { key: 'B', label: 'B. 空氣可以被壓縮、傳送力量' },
      { key: 'C', label: 'C. 空氣流動會形成風' }
    ];

    let matchSelections = {};
    let matchSolved = {};
    let matchFeedback = {};

    function renderMatchCards() {
      const grid = document.getElementById('match-grid');
      grid.innerHTML = matchItems.map(item => {
        const isSolved = !!matchSolved[item.id];
        const selectedArr = matchSelections[item.id] || [];
        const fb = matchFeedback[item.id];

        return `
          <div class="bg-white rounded-3xl p-5 shadow-sm border-2 ${isSolved ? 'border-emerald-400 bg-emerald-50/25' : 'border-slate-200'} flex flex-col justify-between space-y-4">
            <div>
              <div class="flex items-center justify-between gap-2">
                <div class="flex items-center gap-3">
                  <span class="text-3xl bg-sky-50 w-12 h-12 rounded-2xl flex items-center justify-center border border-sky-100">${item.emoji}</span>
                  <h3 class="font-black text-slate-800 text-base sm:text-lg">${item.title}</h3>
                </div>
              </div>
              <div class="mt-2">
                <span class="inline-block text-[11px] font-black px-2.5 py-0.5 rounded-full ${item.isMulti ? 'bg-amber-100 text-amber-900 border border-amber-300' : 'bg-slate-100 text-slate-600'}">
                  ${item.isMulti ? '✨ 可複選（同時應用多項特性）' : '☑️ 可勾選對應特性'}
                </span>
              </div>
              <p class="text-sm text-slate-600 mt-2 leading-relaxed">${item.desc}</p>
            </div>

            <div class="space-y-2">
              ${matchOptions.map(opt => {
                const checked = selectedArr.includes(opt.key);
                let btnStyle = 'bg-slate-50 hover:bg-sky-50 text-slate-700 border-slate-200';
                if (isSolved && checked) {
                  btnStyle = 'bg-emerald-600 text-white border-emerald-600';
                } else if (checked) {
                  btnStyle = 'bg-sky-600 text-white border-sky-600 shadow-sm';
                }
                return `
                  <button type="button" ${isSolved ? 'disabled' : ''} onclick="toggleMatchOption('${item.id}', '${opt.key}')"
                    class="w-full text-left px-3.5 py-2.5 rounded-xl text-xs sm:text-sm font-bold border transition flex items-center gap-2 ${btnStyle}">
                    <span>${checked ? '☑️' : '⬜'}</span>
                    <span>${opt.label}</span>
                  </button>
                `;
              }).join('')}

              ${!isSolved ? `
                <button type="button" onclick="confirmMatchItem('${item.id}')"
                  class="w-full mt-1 py-2.5 rounded-xl bg-teal-600 hover:bg-teal-700 text-white font-black text-xs sm:text-sm shadow-sm transition">
                  ✅ 確認配對（已選 ${selectedArr.length} 項）
                </button>
              ` : ''}

              ${fb ? `
                <div class="text-xs font-bold p-2.5 rounded-xl border ${fb.ok ? 'text-emerald-800 bg-emerald-50 border-emerald-200' : 'text-rose-800 bg-rose-50 border-rose-200'}">
                  ${fb.text}
                </div>
              ` : ''}
            </div>
          </div>
        `;
      }).join('');
      updateMatchBadge();
    }

    function toggleMatchOption(itemId, optKey) {
      if (matchSolved[itemId]) return;
      const current = matchSelections[itemId] || [];
      if (current.includes(optKey)) {
        matchSelections[itemId] = current.filter(k => k !== optKey);
      } else {
        matchSelections[itemId] = [...current, optKey];
      }
      playTone(460, 0.07, 'sine', 0.08);
      renderMatchCards();
    }

    function confirmMatchItem(itemId) {
      const item = matchItems.find(x => x.id === itemId);
      if (!item) return;
      const chosen = [...(matchSelections[itemId] || [])].sort();
      const target = [...item.answers].sort();

      if (chosen.length === 0) {
        matchFeedback[itemId] = { ok: false, text: '⚠️ 請先至少勾選 1 個特性再按確認喔！' };
        playWrongSound();
        renderMatchCards();
        return;
      }

      const isExactMatch = chosen.length === target.length && chosen.every((v, i) => v === target[i]);
      if (isExactMatch) {
        matchSolved[itemId] = true;
        matchFeedback[itemId] = { ok: true, text: `🎉 配對成功！${item.explain}` };
        playCorrectSound();
      } else {
        playWrongSound();
        const isSubset = chosen.every(v => target.includes(v));
        if (isSubset && chosen.length < target.length) {
          matchFeedback[itemId] = {
            ok: false,
            text: `💡 還差一點點喔！你選的都對，但這項物品同時應用了 ${target.length} 項特性，再檢查一下還有哪幾項沒勾選到？`
          };
        } else {
          matchFeedback[itemId] = {
            ok: false,
            text: '❌ 勾選的組合還不太對喔！想想看它是靠空氣占空間、被壓縮，還是流動形成風？'
          };
        }
      }
      renderMatchCards();
    }

    function updateMatchBadge() {
      const count = Object.keys(matchSolved).length;
      document.getElementById('match-score-badge').textContent = `過關進度：${count} / 6 題`;
    }

    function resetMatchGame() {
      matchSelections = {};
      matchSolved = {};
      matchFeedback = {};
      renderMatchCards();
    }

    // ==================== 6. 最終關：25題大魔王挑戰題庫 ====================
    const quizBank = [
      {
        id: 1,
        type: '是非題',
        question: '把粉筆放進水裡會看到氣泡冒出來，是因為粉筆的縫隙裡有空氣。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 0,
        explain: '粉筆和海綿一樣有許多微小縫隙，縫隙裡充滿空氣，放入水中時空氣跑出來就會形成氣泡。'
      },
      {
        id: 2,
        type: '是非題',
        question: '我們可以看見石頭、水等物質，它們都占有空間；但空氣看不見，所以空氣不占有空間。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 1,
        explain: '空氣雖然看不見、摸不到，但它和石頭、水一樣都是一種物質，同樣占有空間。'
      },
      {
        id: 3,
        type: '是非題',
        question: '空氣可以用來填充各種形狀的氣球，這是因為空氣沒有固定形狀。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 0,
        explain: '空氣沒有固定形狀，會隨著容器（如長條氣球、圓形氣球、游泳圈）的形狀而改變。'
      },
      {
        id: 4,
        type: '是非題',
        question: '往前推動裝滿空氣的注射筒活塞，會使注射筒前端的紙條飄起，是因為空氣流動形成風。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 0,
        explain: '推動活塞擠壓筒內空氣，使空氣從筒口快速流出形成風，就能吹動紙條。'
      },
      {
        id: 5,
        type: '是非題',
        question: '因為空氣看不見，所以風的強弱是無法透過觀察而知道的。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 1,
        explain: '雖然空氣看不見，但我們可以從國旗飄揚的高度、頭髮飄動幅度、風車轉動快慢來判斷風的強弱。'
      },
      {
        id: 6,
        type: '是非題',
        question: '游泳圈利用空氣「會流動、可以被壓縮」等特性，幫助我們浮在水面上。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 1,
        explain: '游泳圈主要是利用空氣「占有空間、沒有固定形狀」的特性，充氣後鼓起來產生浮力。'
      },
      {
        id: 7,
        type: '是非題',
        question: '蒲公英是利用風來幫助傳播種子。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 0,
        explain: '蒲公英的種子輕盈且有絨毛，空氣流動形成的風可以帶它飛向遠方繁殖。'
      },
      {
        id: 8,
        type: '是非題',
        question: '人類大量砍伐森林，完全不會影響空氣品質。',
        options: ['⭕ 正確（O）', '❌ 錯誤（X）'],
        answer: 1,
        explain: '砍伐森林會使地面缺乏植物覆蓋，遇到風容易造成塵土飛揚，也會減少樹木淨化空氣的能力。'
      },
      {
        id: 9,
        type: '選擇題',
        question: '下列哪一個現象可以證明「空氣占有空間」？',
        options: ['① 國旗飄動', '② 杯子會沉入水中', '③ 水槍可以噴水', '④ 捏起來鼓鼓的塑膠袋'],
        answer: 3,
        explain: '裝滿空氣並捏緊袋口的塑膠袋鼓鼓的壓不扁，證明袋子裡的空氣占住了空間。'
      },
      {
        id: 10,
        type: '素養圖表題',
        question: '【素養題】小廷觀察家中的鯉魚旗並記錄不同時間的飄動情形（如下表）。請問哪一個時間記錄到的風最強？',
        hasChart: true,
        options: ['① 上午 8：00（旗子垂直下垂）', '② 上午 9：00（旗子微幅斜飄）', '③ 上午 10：00（旗子幾乎下垂）', '④ 上午 11：00（旗子高高水平飄揚）'],
        answer: 3,
        explain: '空氣流動越快，風就越強，旗子也會飄揚得越高。上午 11：00 鯉魚旗飄得最高，表示當時風最強！'
      },
      {
        id: 11,
        type: '選擇題',
        question: '風車會轉動，是因為下列哪一個空氣的特性所造成？',
        options: ['① 空氣可以被壓縮', '② 空氣占有空間', '③ 空氣流動形成風', '④ 空氣看不見'],
        answer: 2,
        explain: '空氣流動形成的風吹動風車葉片，使風車旋轉。'
      },
      {
        id: 12,
        type: '選擇題',
        question: '下列哪一項物品是利用空氣「占有空間、沒有固定形狀」的特性設計的，可以避免物品碰撞損壞？',
        options: ['① 氣泡袋', '② 毛巾', '③ 紙袋', '④ 原子筆'],
        answer: 0,
        explain: '氣泡袋的每個小泡泡裡都充滿空氣，利用空氣占有空間的特性形成防撞緩衝層。'
      },
      {
        id: 13,
        type: '選擇題',
        question: '下列哪一項活動屬於空氣或風的應用？',
        options: ['① 划船', '② 拔河', '③ 放風箏', '④ 玩磁吸式跳棋'],
        answer: 2,
        explain: '放風箏需要利用風力才能讓風箏飛上天空。'
      },
      {
        id: 14,
        type: '選擇題',
        question: '將注射筒的筒口抵住橡皮擦後，仍然可以向下擠壓活塞，這個實驗主要證明下列哪一個空氣的特性？',
        options: ['① 空氣看不見', '② 空氣占有空間', '③ 空氣可以被壓縮', '④ 空氣流動形成風'],
        answer: 2,
        explain: '筒口被橡皮擦封住後空氣跑不出去，但活塞仍能往下壓、體積變小，證明空氣可以被壓縮。'
      },
      {
        id: 15,
        type: '選擇題',
        question: '接續第 14 題，這個實驗過程中「沒有」利用到空氣的哪一個特性呢？',
        options: ['① 占有空間', '② 可以被壓縮', '③ 會流動形成風', '④ 沒有固定形狀'],
        answer: 2,
        explain: '筒口被橡皮擦堵住，空氣被封在筒內壓縮與膨脹，並沒有流出筒口形成風。'
      },
      {
        id: 16,
        type: '選擇題',
        question: '下列哪一項物品是利用空氣「會流動、占有空間、可以被壓縮」等特性設計而成？',
        options: ['① 釣魚遊戲', '② 簡易空氣發射器', '③ 紙風車', '④ 游泳圈'],
        answer: 1,
        explain: '簡易空氣發射器（或空氣槍）同時利用空氣占有空間、可被壓縮與快速流動的特性將物體射出。'
      },
      {
        id: 17,
        type: '選擇題',
        question: '下列哪一種作法「無法」維護空氣的清新和乾淨？',
        options: ['① 少砍伐、多種樹', '② 用較環保、低汙染的方式發電', '③ 多搭乘大眾運輸工具', '④ 工廠任意排放廢氣'],
        answer: 3,
        explain: '工廠任意排放廢氣會嚴重汙染空氣，危害所有生物的健康。'
      },
      {
        id: 18,
        type: '選擇題',
        question: '把塞緊紙團的杯子「垂直」壓入水箱底部，再垂直拿出水面，杯子裡的紙團會變得怎樣？',
        options: ['① 全部濕透了', '② 還是乾的，沒有被水沾濕', '③ 紙團會浮在水面上', '④ 紙團變成綠色'],
        answer: 1,
        explain: '因為杯內的空氣占有空間，水無法進入杯中，所以紙團取出後依然是乾的。'
      },
      {
        id: 19,
        type: '選擇題',
        question: '接續第 18 題，如果在水中把杯子「斜壓入水中」或「斜拿出水面」，會觀察到什麼現象？',
        options: ['① 沒有任何變化', '② 有氣泡從杯口冒出來，水跑進杯子把紙團弄濕', '③ 杯子會自己飛起來', '④ 水會全部變成氣泡'],
        answer: 1,
        explain: '杯子傾斜時，原本被困在杯裡的空氣會跑出形成氣泡，水就會流進杯子把紙團弄濕。'
      },
      {
        id: 20,
        type: '選擇題',
        question: '使用「衣物收納袋」整理換季厚棉被時，需要怎麼做才能節省收納空間？',
        options: ['① 往袋子裡灌入更多空氣', '② 把袋子裡的空氣抽掉排出', '③ 把袋子放進水裡', '④ 在袋子上戳很多洞'],
        answer: 1,
        explain: '空氣占有空間，把衣物收納袋裡的空氣排出，棉被體積就會大幅縮小、節省空間。'
      },
      {
        id: 21,
        type: '選擇題',
        question: '推動裝滿 20 mL 空氣的注射筒活塞吹動紙條，當活塞已經完全推到底（0 mL）並停下來時，紙條會怎麼樣？',
        options: ['① 繼續被強風吹得高高的', '② 因為空氣已全部排出、不再流動，風停止了，紙條自然垂下', '③ 紙條會被吸進注射筒裡', '④ 紙條會越飄越高'],
        answer: 1,
        explain: '只有空氣在流動的過程中才會形成風；推到底後筒內沒有空氣再流出來，風就停止了。'
      },
      {
        id: 22,
        type: '選擇題',
        question: '用橡皮擦抵住裝有 20 mL 空氣的注射筒筒口，慢慢往下壓活塞，手指會有什麼感覺？',
        options: ['① 越推越輕鬆，完全沒有阻力', '② 越推越重，
