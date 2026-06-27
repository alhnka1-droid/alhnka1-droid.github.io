<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>منجرة الجبيل — حاسبة الخزائن</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap" rel="stylesheet">
<style>
:root {
  --wood: #7C4A1E;
  --wood-light: #B5752F;
  --wood-dark: #4A2800;
  --gold: #C8963C;
  --bg: #F7F3EE;
  --surface: #FFFFFF;
  --surface2: #F0EAE0;
  --border: #DDD0BC;
  --text: #2A1A08;
  --muted: #7A6248;
  --accent: #C8963C;
  --accent-light: #FDF3E0;
  --green: #1E6B3A;
  --green-light: #E6F5ED;
  --red: #B03020;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: 'Cairo', sans-serif; background: var(--bg); color: var(--text); min-height: 100vh; }

/* HEADER */
header {
  background: var(--wood-dark);
  padding: 0;
  text-align: center;
  position: relative;
}
.header-top {
  background: var(--gold);
  height: 4px;
}
.header-body {
  padding: 22px 20px 18px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
}
.header-icon { font-size: 2rem; }
.header-name {
  font-size: 1.8rem;
  font-weight: 900;
  color: #fff;
  letter-spacing: 1px;
}
.header-sub {
  font-size: 0.85rem;
  color: var(--gold);
  font-weight: 600;
  letter-spacing: 2px;
}
.header-bottom {
  background: var(--gold);
  height: 4px;
}

/* TABS */
.tabs {
  display: flex;
  background: var(--wood-dark);
  border-bottom: 3px solid var(--gold);
}
.tab {
  flex: 1;
  padding: 12px;
  text-align: center;
  font-size: 0.9rem;
  font-weight: 700;
  color: rgba(255,255,255,0.5);
  cursor: pointer;
  transition: all 0.2s;
  border: none;
  background: none;
  font-family: 'Cairo', sans-serif;
}
.tab.active {
  color: var(--gold);
  background: rgba(200,150,60,0.15);
  border-bottom: 3px solid var(--gold);
  margin-bottom: -3px;
}

.container { max-width: 600px; margin: 0 auto; padding: 16px 14px 60px; }

/* PANEL */
.panel { display: none; }
.panel.active { display: block; }

/* CARD */
.card {
  background: var(--surface);
  border-radius: 14px;
  border: 1px solid var(--border);
  padding: 18px 16px;
  margin-bottom: 14px;
}
.card-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--wood-dark);
  margin-bottom: 14px;
  display: flex;
  align-items: center;
  gap: 8px;
  padding-bottom: 10px;
  border-bottom: 1.5px solid var(--surface2);
}

/* GRID */
.g2 { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.g3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; }
@media(max-width:500px) { .g3 { grid-template-columns: 1fr 1fr; } }

label {
  display: block;
  font-size: 0.78rem;
  font-weight: 700;
  color: var(--muted);
  margin-bottom: 5px;
}
input[type="number"] {
  width: 100%;
  padding: 9px 11px;
  border: 1.5px solid var(--border);
  border-radius: 9px;
  font-family: 'Cairo', sans-serif;
  font-size: 0.92rem;
  color: var(--text);
  background: var(--bg);
  transition: border-color 0.2s;
}
input[type="number"]:focus { outline: none; border-color: var(--gold); background: #fff; }
select {
  width: 100%;
  padding: 9px 11px;
  border: 1.5px solid var(--border);
  border-radius: 9px;
  font-family: 'Cairo', sans-serif;
  font-size: 0.92rem;
  color: var(--text);
  background: var(--bg);
}

/* PRICE ROW */
.price-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  padding: 10px 12px;
  background: var(--surface2);
  border-radius: 10px;
  margin-bottom: 8px;
  border: 1px solid var(--border);
  align-items: center;
}
.price-label { font-size: 0.85rem; font-weight: 700; color: var(--text); }
.price-sub { font-size: 0.72rem; color: var(--muted); }

/* SAVE BTN */
.save-btn {
  width: 100%;
  padding: 13px;
  background: var(--wood);
  color: #fff;
  border: none;
  border-radius: 11px;
  font-family: 'Cairo', sans-serif;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 4px;
  transition: opacity 0.2s;
}
.save-btn:hover { opacity: 0.88; }
.save-notice {
  text-align: center;
  font-size: 0.78rem;
  color: var(--green);
  margin-top: 8px;
  font-weight: 600;
  display: none;
}

/* CALC PANEL */
/* Quick calc */
.quick-box {
  background: var(--accent-light);
  border: 1.5px solid var(--gold);
  border-radius: 14px;
  padding: 18px 16px;
  margin-bottom: 14px;
}
.quick-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--wood-dark);
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  gap: 6px;
}
.quick-inputs { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; margin-bottom: 12px; }
@media(max-width:460px) { .quick-inputs { grid-template-columns: 1fr 1fr; } }
.quick-result {
  background: var(--wood-dark);
  color: #fff;
  border-radius: 10px;
  padding: 12px 16px;
  display: none;
}
.quick-result.show { display: block; }
.qr-row { display: flex; justify-content: space-between; font-size: 0.85rem; padding: 3px 0; opacity: 0.85; }
.qr-total { display: flex; justify-content: space-between; font-size: 1.1rem; font-weight: 900; margin-top: 8px; padding-top: 8px; border-top: 1px solid rgba(255,255,255,0.25); color: var(--gold); }

/* Detail calc */
.detail-box {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 18px 16px;
  margin-bottom: 14px;
}
.detail-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--wood-dark);
  margin-bottom: 14px;
  display: flex;
  align-items: center;
  gap: 6px;
  padding-bottom: 10px;
  border-bottom: 1.5px solid var(--surface2);
}
.doors-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 10px; }
@media(max-width:460px) { .doors-grid { grid-template-columns: 1fr 1fr; } }
.door-type-card {
  background: var(--surface2);
  border-radius: 10px;
  padding: 10px;
  border: 1.5px solid var(--border);
  text-align: center;
}
.door-type-name { font-size: 0.78rem; font-weight: 700; color: var(--muted); margin-bottom: 6px; }

/* CALC BTN */
.calc-btn {
  width: 100%;
  padding: 14px;
  background: linear-gradient(135deg, var(--wood-dark), var(--wood));
  color: #fff;
  border: none;
  border-radius: 12px;
  font-family: 'Cairo', sans-serif;
  font-size: 1.05rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 6px;
  transition: opacity 0.2s;
}
.calc-btn:hover { opacity: 0.9; }

/* RESULT */
.result-card {
  background: var(--wood-dark);
  border-radius: 16px;
  padding: 20px 18px;
  margin-top: 16px;
  display: none;
  color: #fff;
}
.result-card.show { display: block; }
.res-title { font-size: 0.9rem; font-weight: 700; opacity: 0.7; margin-bottom: 14px; border-bottom: 1px solid rgba(255,255,255,0.15); padding-bottom: 10px; }
.res-row { display: flex; justify-content: space-between; padding: 6px 0; font-size: 0.88rem; border-bottom: 1px solid rgba(255,255,255,0.07); }
.res-row .lbl { opacity: 0.75; }
.res-total { display: flex; justify-content: space-between; margin-top: 12px; padding-top: 12px; border-top: 2px solid rgba(255,255,255,0.2); }
.res-total .lbl { font-size: 0.95rem; font-weight: 700; }
.res-total .val { font-size: 1.5rem; font-weight: 900; color: var(--gold); }
.res-sell { background: rgba(200,150,60,0.15); border-radius: 10px; padding: 11px 14px; margin-top: 12px; display: flex; justify-content: space-between; align-items: center; }
.res-sell .lbl { font-size: 0.9rem; }
.res-sell .val { font-size: 1.3rem; font-weight: 900; color: #A8FFCC; }
.res-profit { background: rgba(255,255,255,0.07); border-radius: 10px; padding: 10px 14px; margin-top: 8px; display: flex; justify-content: space-between; align-items: center; }
.res-profit .lbl { font-size: 0.85rem; opacity: 0.8; }
.res-profit .val { font-size: 1.1rem; font-weight: 700; color: #A8FFCC; }
.print-btn { width: 100%; padding: 11px; background: rgba(255,255,255,0.1); border: 1px solid rgba(255,255,255,0.3); color: #fff; border-radius: 10px; font-family: 'Cairo', sans-serif; font-size: 0.9rem; font-weight: 700; cursor: pointer; margin-top: 14px; }

.hint { font-size: 0.74rem; color: var(--muted); margin-top: 4px; }
.divider { height: 1px; background: var(--border); margin: 12px 0; }
.no-prices { background: #FFF3CD; border: 1px solid #F0A800; border-radius: 10px; padding: 12px 14px; font-size: 0.85rem; color: #7A5000; text-align: center; margin-bottom: 14px; display: none; }

@media print {
  header, .tabs, .detail-box, .quick-box, .calc-btn, .print-btn, .no-prices { display: none !important; }
  .result-card { display: block !important; background: #fff !important; color: #000 !important; }
  .res-total .val, .res-sell .val, .res-profit .val { color: #000 !important; }
}
</style>
</head>
<body>

<header>
  <div class="header-top"></div>
  <div class="header-body">
    <div class="header-icon">🪵</div>
    <div class="header-name">منجرة الجبيل</div>
    <div class="header-sub">حاسبة تكاليف خزائن الملابس</div>
  </div>
  <div class="header-bottom"></div>
</header>

<div class="tabs">
  <button class="tab active" onclick="switchTab('calc')">🧮 الحاسبة</button>
  <button class="tab" onclick="switchTab('settings')">⚙️ الأسعار</button>
</div>

<!-- ===== SETTINGS PANEL ===== -->
<div id="panel-settings" class="panel">
  <div class="container">

    <div class="card">
      <div class="card-title">🪵 أسعار المواد (ريال / م²)</div>
      <div class="price-row">
        <div><div class="price-label">MDF ميلامين صيني</div><div class="price-sub">هيكل + أبواب خشب</div></div>
        <div><label>السعر</label><input type="number" id="s-mdf-cn" placeholder="85"></div>
      </div>
      <div class="price-row">
        <div><div class="price-label">MDF ميلامين سعودي</div><div class="price-sub">هيكل + أبواب خشب</div></div>
        <div><label>السعر</label><input type="number" id="s-mdf-sa" placeholder="120"></div>
      </div>
      <div class="price-row">
        <div><div class="price-label">أبواب زجاج</div><div class="price-sub">سعر المتر المربع</div></div>
        <div><label>السعر</label><input type="number" id="s-glass" placeholder="180"></div>
      </div>
      <div class="price-row">
        <div><div class="price-label">أبواب مرايا</div><div class="price-sub">سعر المتر المربع</div></div>
        <div><label>السعر</label><input type="number" id="s-mirror" placeholder="220"></div>
      </div>
    </div>

    <div class="card">
      <div class="card-title">👷 العمالة والربح</div>
      <div class="g2">
        <div><label>تكلفة العمالة (ريال / م²)</label><input type="number" id="s-labor" placeholder="120"></div>
        <div><label>نسبة الربح (%)</label><input type="number" id="s-profit" placeholder="30"></div>
      </div>
    </div>

    <div class="card">
      <div class="card-title">⚡ السعر السريع (شامل كل شيء)</div>
      <p class="hint" style="margin-bottom:12px">سعر المتر المربع الشامل لكل التكاليف والربح — للعرض السريع للعميل</p>
      <div class="price-row">
        <div><div class="price-label">MDF صيني — سعر شامل</div></div>
        <div><label>ريال / م²</label><input type="number" id="s-quick-cn" placeholder="450"></div>
      </div>
      <div class="price-row">
        <div><div class="price-label">MDF سعودي — سعر شامل</div></div>
        <div><label>ريال / م²</label><input type="number" id="s-quick-sa" placeholder="600"></div>
      </div>
      <div class="price-row">
        <div><div class="price-label">زجاج / مرايا — إضافة</div></div>
        <div><label>ريال / م²</label><input type="number" id="s-quick-glass" placeholder="150"></div>
      </div>
    </div>

    <button class="save-btn" onclick="savePrices()">💾 حفظ الأسعار</button>
    <div class="save-notice" id="save-notice">✅ تم حفظ الأسعار بنجاح</div>

  </div>
</div>

<!-- ===== CALC PANEL ===== -->
<div id="panel-calc" class="panel active">
  <div class="container">

    <div class="no-prices" id="no-prices-warning">
      ⚠️ لم تُدخل الأسعار بعد — اذهب إلى تبويب <strong>الأسعار</strong> وأدخل أسعارك أولاً
    </div>

    <!-- QUICK CALC -->
    <div class="quick-box">
      <div class="quick-title">⚡ السعر السريع للعميل</div>
      <div class="quick-inputs">
        <div><label>العرض (م)</label><input type="number" id="q-w" placeholder="2.0" step="0.1" oninput="quickCalc()"></div>
        <div><label>الارتفاع (م)</label><input type="number" id="q-h" placeholder="2.4" step="0.1" oninput="quickCalc()"></div>
        <div>
          <label>نوع الخشب</label>
          <select id="q-type" onchange="quickCalc()">
            <option value="cn">MDF صيني</option>
            <option value="sa">MDF سعودي</option>
          </select>
        </div>
        <div><label>أبواب زجاج / مرايا (م²)</label><input type="number" id="q-glass" placeholder="0" step="0.1" oninput="quickCalc()"></div>
      </div>
      <div class="quick-result" id="quick-result">
        <div class="qr-row"><span>مساحة الخزانة</span><span id="qr-area">—</span></div>
        <div class="qr-row"><span>سعر الخشب</span><span id="qr-wood">—</span></div>
        <div class="qr-row"><span>إضافة الزجاج / مرايا</span><span id="qr-glass">—</span></div>
        <div class="qr-total"><span>سعر العميل</span><span id="qr-total">—</span></div>
      </div>
    </div>

    <!-- DETAIL CALC -->
    <div class="detail-box">
      <div class="detail-title">📋 الحساب التفصيلي الدقيق</div>

      <div class="card-title" style="font-size:0.85rem; border:none; padding:0; margin-bottom:10px;">📐 أبعاد الخزانة</div>
      <div class="g3" style="margin-bottom:14px">
        <div><label>العرض (سم)</label><input type="number" id="d-w" placeholder="200"></div>
        <div><label>الارتفاع (سم)</label><input type="number" id="d-h" placeholder="240"></div>
        <div><label>العمق (سم)</label><input type="number" id="d-d" placeholder="60"></div>
      </div>

      <div class="card-title" style="font-size:0.85rem; border:none; padding:0; margin-bottom:10px;">🪵 نوع خشب الهيكل</div>
      <div class="g2" style="margin-bottom:14px">
        <div>
          <label>النوع</label>
          <select id="d-mdf">
            <option value="cn">MDF ميلامين صيني</option>
            <option value="sa">MDF ميلامين سعودي</option>
          </select>
        </div>
        <div></div>
      </div>

      <div class="card-title" style="font-size:0.85rem; border:none; padding:0; margin-bottom:10px;">🚪 الأبواب</div>
      <div class="doors-grid" style="margin-bottom:14px">
        <div class="door-type-card">
          <div class="door-type-name">خشب (م²)</div>
          <input type="number" id="d-door-wood" placeholder="0" step="0.01">
        </div>
        <div class="door-type-card">
          <div class="door-type-name">زجاج (م²)</div>
          <input type="number" id="d-door-glass" placeholder="0" step="0.01">
        </div>
        <div class="door-type-card">
          <div class="door-type-name">مرايا (م²)</div>
          <input type="number" id="d-door-mirror" placeholder="0" step="0.01">
        </div>
      </div>

      <div class="card-title" style="font-size:0.85rem; border:none; padding:0; margin-bottom:10px;">🗄️ الأدراج</div>
      <div class="g3" style="margin-bottom:14px">
        <div><label>عدد الأدراج</label><input type="number" id="d-drawers" placeholder="0"></div>
        <div><label>عرض الدرج (سم)</label><input type="number" id="d-dw" placeholder="50"></div>
        <div><label>نوع خشب الأدراج</label>
          <select id="d-dmdf" style="margin-top:0">
            <option value="cn">صيني</option>
            <option value="sa">سعودي</option>
          </select>
        </div>
      </div>

      <div class="card-title" style="font-size:0.85rem; border:none; padding:0; margin-bottom:10px;">💹 الربح</div>
      <div class="g2" style="margin-bottom:6px">
        <div><label>نسبة ربح إضافية (%)</label><input type="number" id="d-profit-override" placeholder="اتركه فارغاً للافتراضي"></div>
        <div></div>
      </div>
      <div class="hint">إذا تركته فارغاً سيستخدم النسبة المحفوظة في الإعدادات</div>

    </div>

    <button class="calc-btn" onclick="detailCalc()">🧮 احسب التكلفة التفصيلية</button>

    <!-- RESULT -->
    <div class="result-card" id="result-card">
      <div class="res-title">📊 نتيجة الحساب التفصيلي — منجرة الجبيل</div>
      <div class="res-row"><span class="lbl">🪵 هيكل MDF</span><span id="r-frame">—</span></div>
      <div class="res-row"><span class="lbl">🚪 أبواب</span><span id="r-doors">—</span></div>
      <div class="res-row"><span class="lbl">🗄️ أدراج</span><span id="r-drawers">—</span></div>
      <div class="res-row"><span class="lbl">👷 عمالة</span><span id="r-labor">—</span></div>
      <div class="res-total"><span class="lbl">إجمالي التكلفة</span><span class="val" id="r-cost">—</span></div>
      <div class="res-sell"><span class="lbl">🏷️ سعر البيع للعميل</span><span class="val" id="r-sell">—</span></div>
      <div class="res-profit"><span class="lbl">📈 صافي الربح</span><span class="val" id="r-profit">—</span></div>
      <div id="r-area-note" style="font-size:0.75rem;opacity:0.6;margin-top:10px;text-align:center"></div>
      <button class="print-btn" onclick="window.print()">🖨️ طباعة / حفظ PDF</button>
    </div>

  </div>
</div>

<script>
const STORE = 'mnjara_jubail_prices';

function loadPrices() {
  try { return JSON.parse(localStorage.getItem(STORE)) || {}; } catch(e) { return {}; }
}

function savePrices() {
  const p = {
    mdfCn: +document.getElementById('s-mdf-cn').value || 0,
    mdfSa: +document.getElementById('s-mdf-sa').value || 0,
    glass: +document.getElementById('s-glass').value || 0,
    mirror: +document.getElementById('s-mirror').value || 0,
    labor: +document.getElementById('s-labor').value || 0,
    profit: +document.getElementById('s-profit').value || 0,
    quickCn: +document.getElementById('s-quick-cn').value || 0,
    quickSa: +document.getElementById('s-quick-sa').value || 0,
    quickGlass: +document.getElementById('s-quick-glass').value || 0,
  };
  localStorage.setItem(STORE, JSON.stringify(p));
  const n = document.getElementById('save-notice');
  n.style.display = 'block';
  setTimeout(() => n.style.display = 'none', 2500);
}

function fillSettings() {
  const p = loadPrices();
  if (p.mdfCn) document.getElementById('s-mdf-cn').value = p.mdfCn;
  if (p.mdfSa) document.getElementById('s-mdf-sa').value = p.mdfSa;
  if (p.glass) document.getElementById('s-glass').value = p.glass;
  if (p.mirror) document.getElementById('s-mirror').value = p.mirror;
  if (p.labor) document.getElementById('s-labor').value = p.labor;
  if (p.profit) document.getElementById('s-profit').value = p.profit;
  if (p.quickCn) document.getElementById('s-quick-cn').value = p.quickCn;
  if (p.quickSa) document.getElementById('s-quick-sa').value = p.quickSa;
  if (p.quickGlass) document.getElementById('s-quick-glass').value = p.quickGlass;
}

function checkPrices() {
  const p = loadPrices();
  const hasAny = p.mdfCn || p.mdfSa || p.quickCn || p.quickSa;
  document.getElementById('no-prices-warning').style.display = hasAny ? 'none' : 'block';
}

function sar(n) {
  return n.toLocaleString('ar-SA', { minimumFractionDigits: 0, maximumFractionDigits: 0 }) + ' ر.س';
}

function switchTab(tab) {
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.getElementById('panel-' + tab).classList.add('active');
  event.target.classList.add('active');
  if (tab === 'calc') checkPrices();
}

function quickCalc() {
  const p = loadPrices();
  const w = parseFloat(document.getElementById('q-w').value) || 0;
  const h = parseFloat(document.getElementById('q-h').value) || 0;
  const type = document.getElementById('q-type').value;
  const glassArea = parseFloat(document.getElementById('q-glass').value) || 0;
  if (!w || !h) { document.getElementById('quick-result').classList.remove('show'); return; }
  const area = w * h;
  const pricePerM2 = type === 'cn' ? (p.quickCn || 0) : (p.quickSa || 0);
  const glassExtra = glassArea * (p.quickGlass || 0);
  const woodCost = area * pricePerM2;
  const total = woodCost + glassExtra;
  document.getElementById('qr-area').textContent = area.toFixed(2) + ' م²';
  document.getElementById('qr-wood').textContent = sar(woodCost);
  document.getElementById('qr-glass').textContent = glassArea ? sar(glassExtra) : '—';
  document.getElementById('qr-total').textContent = sar(total);
  document.getElementById('quick-result').classList.add('show');
}

function detailCalc() {
  const p = loadPrices();
  const W = (parseFloat(document.getElementById('d-w').value) || 0) / 100;
  const H = (parseFloat(document.getElementById('d-h').value) || 0) / 100;
  const D = (parseFloat(document.getElementById('d-d').value) || 0) / 100;
  if (!W || !H || !D) { alert('يرجى إدخال أبعاد الخزانة'); return; }
  const mdfType = document.getElementById('d-mdf').value;
  const mdfPrice = mdfType === 'cn' ? (p.mdfCn || 0) : (p.mdfSa || 0);
  // هيكل: جانبان + سقف + أرضية + ظهر
  const frameArea = (2 * H * D) + (2 * W * D) + (W * H);
  const frameCost = frameArea * 1.10 * mdfPrice;
  // أبواب
  const doorWood = parseFloat(document.getElementById('d-door-wood').value) || 0;
  const doorGlass = parseFloat(document.getElementById('d-door-glass').value) || 0;
  const doorMirror = parseFloat(document.getElementById('d-door-mirror').value) || 0;
  const doorCost = (doorWood * mdfPrice) + (doorGlass * (p.glass || 0)) + (doorMirror * (p.mirror || 0));
  // أدراج
  const dCount = parseFloat(document.getElementById('d-drawers').value) || 0;
  const dW = (parseFloat(document.getElementById('d-dw').value) || 50) / 100;
  const dMdfType = document.getElementById('d-dmdf').value;
  const dMdfPrice = dMdfType === 'cn' ? (p.mdfCn || 0) : (p.mdfSa || 0);
  const drawerAreaEach = (dW * 0.5) + (dW * 0.15) + (2 * 0.5 * 0.15) + (dW * 0.15);
  const drawerCost = drawerAreaEach * dCount * 1.10 * dMdfPrice;
  // عمالة
  const totalArea = frameArea * 1.10;
  const laborCost = totalArea * (p.labor || 0);
  // إجمالي
  const totalCost = frameCost + doorCost + drawerCost + laborCost;
  const profitOverride = parseFloat(document.getElementById('d-profit-override').value);
  const profitPct = (!isNaN(profitOverride) && profitOverride > 0) ? profitOverride : (p.profit || 0);
  const sellPrice = totalCost * (1 + profitPct / 100);
  const profit = sellPrice - totalCost;
  document.getElementById('r-frame').textContent = sar(frameCost);
  document.getElementById('r-doors').textContent = doorCost ? sar(doorCost) : '—';
  document.getElementById('r-drawers').textContent = drawerCost ? sar(drawerCost) : '—';
  document.getElementById('r-labor').textContent = sar(laborCost);
  document.getElementById('r-cost').textContent = sar(totalCost);
  document.getElementById('r-sell').textContent = sar(sellPrice);
  document.getElementById('r-profit').textContent = sar(profit);
  document.getElementById('r-area-note').textContent = 'مساحة الهيكل: ' + frameArea.toFixed(2) + ' م² (بعد الهدر: ' + (frameArea * 1.10).toFixed(2) + ' م²)';
  const rc = document.getElementById('result-card');
  rc.classList.add('show');
  rc.scrollIntoView({ behavior: 'smooth', block: 'start' });
}

// تهيئة
fillSettings();
checkPrices();
</script>
</body>
</html>
