<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>SMCTI Science Lab — Chemical Locator S.Y. 2025–2026</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'Segoe UI', Arial, sans-serif; background: #F0F4F9; color: #1a2a3a; min-height: 100vh; }

  header { background: linear-gradient(135deg, #0C447C 0%, #185FA5 60%, #378ADD 100%); color: #fff; padding: 0; box-shadow: 0 2px 12px rgba(12,68,124,0.18); }
  .header-inner { max-width: 1100px; margin: 0 auto; padding: 24px 24px 20px; display: flex; align-items: center; gap: 18px; }
  .logo-circle { width: 56px; height: 56px; border-radius: 50%; background: rgba(255,255,255,0.18); border: 2px solid rgba(255,255,255,0.35); display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
  .logo-circle span { font-size: 13px; font-weight: 700; color: #fff; letter-spacing: 0.5px; text-align: center; line-height: 1.2; }
  .header-text h1 { font-size: 22px; font-weight: 600; letter-spacing: 0.01em; }
  .header-text p { font-size: 13px; color: rgba(255,255,255,0.78); margin-top: 3px; }

  .main { max-width: 1100px; margin: 0 auto; padding: 28px 24px 48px; }

  .toolbar { display: flex; flex-wrap: wrap; gap: 12px; align-items: center; margin-bottom: 18px; }
  .search-wrap { position: relative; flex: 1; min-width: 220px; }
  .search-wrap svg { position: absolute; left: 12px; top: 50%; transform: translateY(-50%); color: #378ADD; pointer-events: none; }
  #searchInput {
    width: 100%; padding: 11px 14px 11px 40px; font-size: 15px;
    border: 1.5px solid #B5D4F4; border-radius: 8px; background: #fff;
    color: #1a2a3a; outline: none; transition: border-color 0.15s, box-shadow 0.15s;
  }
  #searchInput:focus { border-color: #378ADD; box-shadow: 0 0 0 3px rgba(55,138,221,0.13); }
  #searchInput::placeholder { color: #8aaac8; }

  .filters { display: flex; gap: 8px; flex-wrap: wrap; }
  .filter-btn {
    padding: 8px 18px; font-size: 13px; font-weight: 500; border-radius: 20px;
    border: 1.5px solid #B5D4F4; background: #fff; color: #185FA5;
    cursor: pointer; transition: all 0.15s;
  }
  .filter-btn:hover { background: #E6F1FB; }
  .filter-btn.active { background: #185FA5; color: #fff; border-color: #185FA5; }

  .stats { display: grid; grid-template-columns: repeat(4, 1fr); gap: 12px; margin-bottom: 20px; }
  .stat-card { background: #fff; border: 0.5px solid #D0DFF0; border-radius: 10px; padding: 14px 16px; text-align: center; }
  .stat-card .num { font-size: 26px; font-weight: 600; color: #185FA5; }
  .stat-card .lbl { font-size: 12px; color: #5a7a9a; margin-top: 2px; }

  .results-info { font-size: 12.5px; color: #5a7a9a; margin-bottom: 10px; padding: 0 2px; }

  .table-card { background: #fff; border: 0.5px solid #D0DFF0; border-radius: 12px; overflow: hidden; box-shadow: 0 1px 6px rgba(12,68,124,0.06); }
  .table-wrap { overflow-x: auto; }
  table { width: 100%; border-collapse: collapse; font-size: 13.5px; min-width: 560px; }
  thead { background: #0C447C; }
  thead th { color: #B5D4F4; font-weight: 500; padding: 11px 14px; text-align: left; font-size: 12px; letter-spacing: 0.04em; text-transform: uppercase; white-space: nowrap; }
  tbody tr { border-bottom: 0.5px solid #E6EFF8; transition: background 0.1s; }
  tbody tr:last-child { border-bottom: none; }
  tbody tr:hover { background: #F0F7FF; }
  tbody td { padding: 9px 14px; vertical-align: middle; }
  .td-num { color: #8aaac8; font-size: 12px; width: 40px; }
  .td-name { font-weight: 600; color: #0C447C; }
  .td-loc { font-size: 12.5px; color: #5a7a9a; }
  .td-qty { font-weight: 500; color: #185FA5; white-space: nowrap; }

  .badge { display: inline-block; font-size: 11px; padding: 3px 9px; border-radius: 20px; font-weight: 600; letter-spacing: 0.02em; }
  .badge-solid { background: #E6F1FB; color: #185FA5; }
  .badge-liquid { background: #E1F5EE; color: #0F6E56; }

  .no-results { text-align: center; padding: 3rem 1rem; color: #8aaac8; }
  .no-results .icon { font-size: 40px; margin-bottom: 10px; }
  .no-results p { font-size: 15px; }

  mark { background: #FAC775; border-radius: 2px; padding: 0 1px; color: inherit; }

  footer { text-align: center; font-size: 12px; color: #8aaac8; padding: 16px 0 32px; }

  @media (max-width: 600px) {
    .stats { grid-template-columns: repeat(2, 1fr); }
    .header-inner { gap: 12px; }
    .header-text h1 { font-size: 16px; }
  }
  @media print {
    body { background: #fff; }
    .toolbar, .filters, footer { display: none; }
    .table-card { box-shadow: none; border: 1px solid #ccc; }
  }
</style>
</head>
<body>

<header>
  <div class="header-inner">
    <div class="logo-circle"><span>SMCTI<br>QTIME</span></div>
    <div class="header-text">
      <h1>Science Laboratory Chemical Locator</h1>
      <p>St. Mary's College of Tagum, Inc. &nbsp;|&nbsp; Tertiary Education Program &nbsp;|&nbsp; S.Y. 2025–2026</p>
    </div>
  </div>
</header>

<div class="main">

  <div class="toolbar">
    <div class="search-wrap">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input type="text" id="searchInput" placeholder="Search chemical name, location, or quantity…" autocomplete="off" />
    </div>
    <div class="filters">
      <button class="filter-btn active" data-filter="all">All</button>
      <button class="filter-btn" data-filter="solid">Solid</button>
      <button class="filter-btn" data-filter="liquid">Liquid</button>
    </div>
  </div>

  <div class="stats">
    <div class="stat-card"><div class="num" id="totalCount">0</div><div class="lbl">Total chemicals</div></div>
    <div class="stat-card"><div class="num" id="solidCount">0</div><div class="lbl">Solid</div></div>
    <div class="stat-card"><div class="num" id="liquidCount">0</div><div class="lbl">Liquid</div></div>
    <div class="stat-card"><div class="num" id="showingCount">0</div><div class="lbl">Showing</div></div>
  </div>

  <div class="results-info" id="resultsInfo"></div>

  <div class="table-card">
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>#</th>
            <th>Chemical Name</th>
            <th>Type</th>
            <th>Location</th>
            <th>Est. Quantity</th>
          </tr>
        </thead>
        <tbody id="tableBody"></tbody>
      </table>
    </div>
  </div>

</div>

<footer>Faith &bull; Excellence &bull; Service &nbsp;&mdash;&nbsp; SMCTI Science Laboratory S.Y. 2025–2026</footer>

<script>
const chemicals = [
  ["Ammonium Sulfate","solid","Cab.1 left side Cub.1","1 kg"],
  ["Copper Sulfate","solid","Cab.1 left side Cub.1","500 g"],
  ["Magnesium Sulfate","solid","Cab.1 left side Cub.1","250 g"],
  ["Magnesium Heptahydrate A.R. Sulphate","solid","Cab.1 left side Cub.1","250 g"],
  ["Manganese (II) Monohydrate Sulfate","solid","Cab.1 left side Cub.1","500 g"],
  ["Zinc Sulfate","solid","Cab.1 left side Cub.1","250 g"],
  ["Antimony Metal","solid","Cab.1 left side Cub.2 & 3","500 g"],
  ["Copper","solid","Cab.1 left side Cub.2 & 3","1 kl."],
  ["Copper Shots","solid","Cab.1 left side Cub.2 & 3","500 g"],
  ["Copper Turnings","solid","Cab.1 left side Cub.2 & 3","300 g"],
  ["Lead Metal","solid","Cab.1 left side Cub.2 & 3","250 g"],
  ["Lead Shots","solid","Cab.1 left side Cub.2 & 3","500 g"],
  ["Mossy Zinc Granulated","solid","Cab.1 left side Cub.2 & 3","2 kl."],
  ["Mossy Zinc","solid","Cab.1 left side Cub.2 & 3","100 g"],
  ["Steel Shots","solid","Cab.1 left side Cub.2 & 3","100 g"],
  ["Sulphur Powder","solid","Cab.1 left side Cub.2 & 3","500 g"],
  ["Tin Metal Granulated","solid","Cab.1 left side Cub.2 & 3","100 g"],
  ["Zinc Dust","solid","Cab.1 left side Cub.2 & 3","500 g"],
  ["Zinc Metal Pellets","solid","Cab.1 left side Cub.2 & 3","250 g"],
  ["Zinc Metal Solid Granulated","solid","Cab.1 left side Cub.2 & 3","500 g"],
  ["Ammonium Chloride","solid","Cab.1 left side Cub.4","1,500 g"],
  ["Barium Chloride","solid","Cab.1 left side Cub.4","250 g"],
  ["Barium Chloride AR","solid","Cab.1 left side Cub.4","300 g"],
  ["Barium Chloride Dihydrate A.R.","solid","Cab.1 left side Cub.4","500 g"],
  ["Cadmium Chloride","solid","Cab.1 left side Cub.4","500 g"],
  ["Magnesium Chloride","solid","Cab.1 left side Cub.4","500 g"],
  ["Magnesium Chloride (hexahydrate) 98% AR","solid","Cab.1 left side Cub.4","500 g"],
  ["Mercuric Chloride","solid","Cab.1 left side Cub.4","250 g"],
  ["Potassium Chloride","solid","Cab.1 left side Cub.4","500 g"],
  ["Sodium Chloride","solid","Cab.1 left side Cub.4","1 kg."],
  ["Phenolphthalein Powder","solid","Cab.1 left side Cub.5","500 g"],
  ["Starch Soluble (ex. Potato)","solid","Cab.1 left side Cub.5","2 kls."],
  ["Ammonium Dichromate","solid","Cab.1 left side Cub.6","500 g"],
  ["Barium Nitrate","solid","Cab.1 left side Cub.6","500 g"],
  ["Calcium Tetrahydrate Nitrate","solid","Cab.1 left side Cub.6","500 g"],
  ["Cobalt (II) Nitrate Hexahydrate","solid","Cab.1 left side Cub.6","250 g"],
  ["Lithium Nitrate","solid","Cab.1 left side Cub.6","500 g"],
  ["Magnesium Nitrate","solid","Cab.1 left side Cub.6","500 g"],
  ["Potassium Nitrate","solid","Cab.1 left side Cub.6","100 g"],
  ["Silver Nitrate","solid","Cab.1 left side Cub.6","100 g"],
  ["Sodium Nitrate","solid","Cab.1 left side Cub.6","200 g"],
  ["Strontium Nitrate","solid","Cab.1 left side Cub.6","500 g"],
  ["Urea","solid","Cab.1 left side Cub.6","1 kl."],
  ["Calcium Acetate","solid","Cab.1 left side Cub.7","100 g"],
  ["Iron Filings","solid","Cab.1 left side Cub.7","500 g"],
  ["Lead Acetate","solid","Cab.1 left side Cub.7","250 g"],
  ["Phenolphthalein","solid","Cab.1 left side Cub.7","500 g"],
  ["Sodium Acetate","solid","Cab.1 left side Cub.7","250 g"],
  ["Xylene","solid","Cab.1 left side Cub.7","1 L"],
  ["Potassium Hydroxide Pellets","solid","Cab.1 left side Cub.8","500 g"],
  ["Sodium Hydroxide","solid","Cab.1 left side Cub.8","500 g"],
  ["Sodium Hydroxide Pellets","solid","Cab.1 left side Cub.8","500 g"],
  ["Sodium Hydroxide A.R.","solid","Cab.1 left side Cub.8","1 kl"],
  ["Ammonium Carbonate","solid","Cab.1 left side Cub.9","250 g"],
  ["Calcium Carbonate A.R.","solid","Cab.1 left side Cub.9","500 g"],
  ["Calcium Carbonate","solid","Cab.1 left side Cub.9","500 g"],
  ["Copper Carbonate","solid","Cab.1 left side Cub.9","500 g"],
  ["Cupric Carbonate","solid","Cab.1 left side Cub.9","500 g"],
  ["Lithium Carbonate","solid","Cab.1 left side Cub.9","100 g"],
  ["Magnesium Carbonate","solid","Cab.1 left side Cub.9","250 g"],
  ["Sodium Carbonate Anhydrous","solid","Cab.1 left side Cub.9","1 kg."],
  ["Sodium Bicarbonate","solid","Cab.1 left side Cub.9","250 g"],
  ["Baking Soda","solid","Cab.1 left side Cub.10","250 g"],
  ["Blood Agar Base","solid","Cab.1 left side Cub.10","500 g"],
  ["Cornstarch","solid","Cab.1 left side Cub.10","400 g"],
  ["Crystal Violet","solid","Cab.1 left side Cub.10","250 g"],
  ["Crystal Wax","solid","Cab.1 left side Cub.10","500 g"],
  ["Flour","solid","Cab.1 left side Cub.10","250 g"],
  ["Gelatin","solid","Cab.1 left side Cub.10","250 g"],
  ["Gelatin Violet","solid","Cab.1 left side Cub.10","1 L."],
  ["Lactose","solid","Cab.1 left side Cub.10","1 kl."],
  ["Ammonium Oxalate","solid","Cab.1 left side Cub.11","100 g"],
  ["Boric Acid","solid","Cab.1 left side Cub.11","250 g"],
  ["Potassium Acid Phthalate A.R.","solid","Cab.1 left side Cub.11","250 g"],
  ["Potassium Chromate","solid","Cab.1 left side Cub.11","250 g"],
  ["Calcium Oxide","solid","Cab.1 left side Cub.12","250 g"],
  ["Cupric Acid","solid","Cab.1 left side Cub.12","100 g"],
  ["Lead Oxide","solid","Cab.1 left side Cub.12","100 g"],
  ["Manganese","solid","Cab.1 left side Cub.12","500 g"],
  ["Mercuric Acid","solid","Cab.1 left side Cub.12","100 g"],
  ["Zinc Oxide","solid","Cab.1 left side Cub.12","500 g"],
  ["Ammonium Dichromate","solid","Cab.1 left side Cub.13","250 g"],
  ["Diethyl Ether","solid","Cab.1 left side Cub.13","1 L."],
  ["Isopropyl Alcohol 70% (Unscented)","solid","Cab.1 left side Cub.13","250 ml."],
  ["Naphthalene","solid","Cab.1 left side Cub.13","500 g"],
  ["Sodium Carbonate","solid","Cab.1 left side Cub.13","1 kg."],
  ["Potassium Chloride","solid","Cab.1 left side Cub.13","500 g"],
  ["Agar Powder","solid","Cab.1 left side Cub.14","500 g"],
  ["Benzoic Acid Crystal","solid","Cab.1 left side Cub.14","500 g"],
  ["Blood Agar Base","solid","Cab.1 left side Cub.14","500 g"],
  ["BTC","solid","Cab.1 left side Cub.14","500 g"],
  ["Copper (II) Oxide","solid","Cab.1 left side Cub.14","500 g"],
  ["Hydrogen Peroxide","solid","Cab.1 left side Cub.14","500 ml."],
  ["Magnesium Oxide","solid","Cab.1 left side Cub.14","500 g"],
  ["Manganese Dioxide A.R.","solid","Cab.1 left side Cub.14","500 g"],
  ["Naphthalene Ball","solid","Cab.1 left side Cub.14","500 g"],
  ["Starch Soluble","solid","Cab.1 left side Cub.14","500 g"],
  ["Sodium Carbonate","solid","Cab.1 left side Cub.14","200 g"],
  ["Urea","solid","Cab.1 left side Cub.14","250 g"],
  ["Zinc Dust A.R.","solid","Cab.1 left side Cub.14","250 g"],
  ["Ammonium Hydrogen Orthophosphate","solid","Cab.1 left side Cub.15","500 g"],
  ["Ammonium Sulfate","solid","Cab.1 left side Cub.15","500 g"],
  ["Barium Sulfate","solid","Cab.1 left side Cub.15","100 g"],
  ["Calcium Carbide","solid","Cab.1 left side Cub.15","500 g"],
  ["Copper Sulfate","solid","Cab.1 left side Cub.15","1 L."],
  ["Copper Sulfate Anhydrous","solid","Cab.1 left side Cub.15","250 ml."],
  ["Manganese Sulfate","solid","Cab.1 left side Cub.15","500 g"],
  ["Magnesium Sulphate Hydrated","solid","Cab.1 left side Cub.15","500 g"],
  ["Potassium Bisulfate","solid","Cab.1 left side Cub.15","100 g"],
  ["Potassium Sulfate","solid","Cab.1 left side Cub.15","500 g"],
  ["Sodium Meta bisulfate","solid","Cab.1 left side Cub.15","250 g"],
  ["Sodium Sulfate","solid","Cab.1 left side Cub.15","500 g"],
  ["Starch Potato","solid","Cab.1 left side Cub.15","500 g"],
  ["Zinc Sulfate","solid","Cab.1 left side Cub.15","100 g"],
  ["Sodium Sulfate Anhydrous","solid","Cab.1 left side Cub.15","500 g"],
  ["Buffered Formalin","solid","Cab.1 left side Cub.16","1 Gal."],
  ["Denatured Alcohol","solid","Cab.1 left side Cub.16","½ Gal. (3L)"],
  ["Ethyl Alcohol","solid","Cab.1 left side Cub.16","2 Gal."],
  ["Isopropyl Alcohol","solid","Cab.1 left side Cub.16","1 L."],
  ["Ammonium Bromide","solid","Cab.1 left side Cub.17","250 g"],
  ["Ammonium Hydrogen Orthophosphate","solid","Cab.1 left side Cub.17","500 g"],
  ["Ammonium Iodide","solid","Cab.1 left side Cub.17","250 g"],
  ["Calcium Phosphate","solid","Cab.1 left side Cub.17","500 g"],
  ["Potassium Bromide","solid","Cab.1 left side Cub.17","500 g"],
  ["Potassium Iodide","solid","Cab.1 left side Cub.17","500 g"],
  ["Calcium Hydroxide","solid","Cab.1 left side Cub.18","500 g"],
  ["Magnesium Hydroxide A.R.","solid","Cab.1 left side Cub.18","250 g"],
  ["Natrium Hydroxide","solid","Cab.1 left side Cub.18","1 kg."],
  ["Potassium Hydroxide","solid","Cab.1 left side Cub.18","250 g"],
  ["Sodium Hydroxide Pellets A.R.","solid","Cab.1 left side Cub.18","500 g"],
  ["Aluminum Granules","solid","Cab.1 left side Cub.19","500 g"],
  ["Aluminum Powder","solid","Cab.1 left side Cub.19","500 g"],
  ["Iodine Crystal","solid","Cab.1 left side Cub.19","100 g"],
  ["Iron Metal Powder","solid","Cab.1 left side Cub.19","500 g"],
  ["Iron Powder","solid","Cab.1 left side Cub.19","500 g"],
  ["Mossy Zinc Granules","solid","Cab.1 left side Cub.19","1 kg."],
  ["Potassium Ferricyanide Crystal","solid","Cab.1 left side Cub.19","500 g"],
  ["Potassium Permanganate","solid","Cab.1 left side Cub.19","250 g"],
  ["Sulfur Powder","solid","Cab.1 left side Cub.19","500 g"],
  ["Crystal Violet","solid","Cab.1 left side Cub.19","100 g"],
  ["Bromocresol Green Indicator","liquid","Cab.1 right side Cub.1","1 L."],
  ["Bromothymol Blue","liquid","Cab.1 right side Cub.1","1 L."],
  ["Bromothymol Red","liquid","Cab.1 right side Cub.1","1 L."],
  ["Phenyldrazine Hydrochloride","liquid","Cab.1 right side Cub.1","1 L."],
  ["Potassium Iodine","liquid","Cab.1 right side Cub.1","50 ml."],
  ["Sodium Bisulfate","liquid","Cab.1 right side Cub.1","500 ml."],
  ["Potassium Permanganate","liquid","Cab.1 right side Cub.1","1 L."],
  ["Sodium Acetate","liquid","Cab.1 right side Cub.2","2.5 L"],
  ["Betadine","liquid","Cab.1 right side Cub.3","120 ml"],
  ["Crystal Violet","liquid","Cab.1 right side Cub.3","500 ml"],
  ["Iodine","liquid","Cab.1 right side Cub.3","500 ml"],
  ["Methylene Blue","liquid","Cab.1 right side Cub.3","1 L"],
  ["Safranin","liquid","Cab.1 right side Cub.3","250 ml"],
  ["Alcoholic KOH","liquid","Cab.1 right side Cub.4","1 L"],
  ["Isopropyl Alcohol","liquid","Cab.1 right side Cub.4","3 L."],
  ["Amino Acids Solution","liquid","Cab.1 right side Cub.5","1 L"],
  ["Glucose Solution","liquid","Cab.1 right side Cub.5","1.5 L."],
  ["Phenolphthalein Solution","liquid","Cab.1 right side Cub.5","500 ml"],
  ["Ringer's Solution","liquid","Cab.1 right side Cub.5","2 L"],
  ["Zinc Nitrate Solution","liquid","Cab.1 right side Cub.5","1 L."],
  ["Benedict's Solution","liquid","Cab.1 right side Cub.6","9 L."],
  ["Lead Nitrate","liquid","Cab.1 right side Cub.7","1 L"],
  ["Ninhydrin","liquid","Cab.1 right side Cub.7","1 L"],
  ["Strontium Nitrate","liquid","Cab.1 right side Cub.7","1 L"],
  ["Ammonium Carbonate","liquid","Cab.1 right side Cub.8","1 L"],
  ["Potassium Carbonate","liquid","Cab.1 right side Cub.8","1 L"],
  ["Sodium Bicarbonate","liquid","Cab.1 right side Cub.8","1 L"],
  ["Sodium Carbonate","liquid","Cab.1 right side Cub.8","1 L"],
  ["Alcoholic Calcium Chloride","liquid","Cab.1 right side Cub.9","500 ml"],
  ["Barium Chloride","liquid","Cab.1 right side Cub.9","500 ml"],
  ["Calcium Chloride","liquid","Cab.1 right side Cub.9","500 ml"],
  ["Mercuric Chloride","liquid","Cab.1 right side Cub.9","1 L"],
  ["Sodium Chlorate","liquid","Cab.1 right side Cub.9","1 L"],
  ["Strontium Chloride","liquid","Cab.1 right side Cub.9","1 L"],
  ["Analytical Reagent Grade","liquid","Cab.1 right side Cub.10","2 L"],
  ["Barfoeds Reagent","liquid","Cab.1 right side Cub.10","250 ml"],
  ["Benzene Reagent Grade (AR)","liquid","Cab.1 right side Cub.10","1 L"],
  ["Hopkins Cole Reagent","liquid","Cab.1 right side Cub.10","500 ml"],
  ["Molisch Reagent","liquid","Cab.1 right side Cub.10","250 ml"],
  ["Monoclonal Grouping Reagent","liquid","Cab.1 right side Cub.10","10 ml."],
  ["Tollen's Reagent","liquid","Cab.1 right side Cub.10","1 L"],
  ["Albumin Solution (Egg Albumin)","liquid","Cab.1 right side Cub.11","1 L"],
  ["Aluminum Oxide Solution","liquid","Cab.1 right side Cub.11","1 L"],
  ["Amino Acid Solution","liquid","Cab.1 right side Cub.11","1 L"],
  ["Amylase Solution","liquid","Cab.1 right side Cub.11","1 L"],
  ["Beta Naphthol Solution","liquid","Cab.1 right side Cub.11","1 L"],
  ["Chromium Nitrate Solution","liquid","Cab.1 right side Cub.11","80 ml"],
  ["Lugol's Solution","liquid","Cab.1 right side Cub.11","1 L"],
  ["Methyl Orange Solution","liquid","Cab.1 right side Cub.11","1 L"],
  ["Copper Sulfate Solution","liquid","Cab.1 right side Cub.12","1 L"],
  ["Cupric Chloride Solution","liquid","Cab.1 right side Cub.12","2 L"],
  ["Lead Nitrate Solution","liquid","Cab.1 right side Cub.12","500 ml"],
  ["Cupric Acid","liquid","Cab.1 right side Cub.13","3 L"],
  ["Acetic Acid","liquid","Cab.1 right side Cub.14","1 L"],
  ["Acetyl Salicylic Acid","liquid","Cab.1 right side Cub.14","250 ml"],
  ["Ninhydrin","liquid","Cab.1 right side Cub.14","1 L"],
  ["Phosphoric Acid","liquid","Cab.1 right side Cub.14","500 ml"],
  ["Phosphomolybdic Acid","liquid","Cab.1 right side Cub.14","1 L"],
  ["Phosphotungstic Acid","liquid","Cab.1 right side Cub.14","1 L"],
  ["Tannic Acid","liquid","Cab.1 right side Cub.14","1 L"],
  ["Ammonium Hydroxide","liquid","Cab.1 right side Cub.15","2 L"],
  ["Ferric Hydroxide","liquid","Cab.1 right side Cub.15","2 L"],
  ["Sodium Hydroxide","liquid","Cab.1 right side Cub.15","500 ml"],
  ["Acid Alcohol","liquid","Cab.1 right side Cub.16","1 L"],
  ["Alcoholic Calcium Chloride","liquid","Cab.1 right side Cub.16","4 L"],
  ["Benzyl Alcohol","liquid","Cab.1 right side Cub.16","500 ml"],
  ["N-Butyl Alcohol","liquid","Cab.1 right side Cub.16","1 L."],
  ["Ammonium Sulfate","liquid","Cab.1 right side Cub.17","1 L"],
  ["Copper Sulfate","liquid","Cab.1 right side Cub.17","2 L"],
  ["Potassium-B Sulfate","liquid","Cab.1 right side Cub.17","1 L"],
  ["Sodium Thiosulfate","liquid","Cab.1 right side Cub.17","1 L"],
  ["Benzaldehyde A.R. 99%","liquid","Cab.1 right side Cub.18","500 ml"],
  ["Benzene","liquid","Cab.1 right side Cub.18","500 ml"],
  ["Benzol Reinst","liquid","Cab.1 right side Cub.18","1 L"],
  ["CCLA","liquid","Cab.1 right side Cub.18","500 ml"],
  ["Xylene","liquid","Cab.1 right side Cub.18","1 L."]
];

let currentFilter = "all";

const solidTotal = chemicals.filter(c => c[1] === "solid").length;
const liquidTotal = chemicals.filter(c => c[1] === "liquid").length;
document.getElementById("totalCount").textContent = chemicals.length;
document.getElementById("solidCount").textContent = solidTotal;
document.getElementById("liquidCount").textContent = liquidTotal;

function esc(str) {
  return str.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;");
}

function highlight(text, query) {
  if (!query) return esc(text);
  const escaped = query.replace(/[.*+?^${}()|[\]\\]/g, '\\$&');
  return esc(text).replace(new RegExp(`(${esc(escaped)})`, 'gi'), '<mark>$1</mark>');
}

function render() {
  const raw = document.getElementById("searchInput").value;
  const q = raw.trim().toLowerCase();
  const tbody = document.getElementById("tableBody");

  const filtered = chemicals.filter(c => {
    const matchType = currentFilter === "all" || c[1] === currentFilter;
    const matchQ = !q || c[0].toLowerCase().includes(q) || c[2].toLowerCase().includes(q) || c[3].toLowerCase().includes(q);
    return matchType && matchQ;
  });

  document.getElementById("showingCount").textContent = filtered.length;
  const info = document.getElementById("resultsInfo");
  if (q) {
    info.textContent = `${filtered.length} result${filtered.length !== 1 ? "s" : ""} for "${raw.trim()}"`;
  } else {
    info.textContent = `Showing all ${filtered.length} chemical${filtered.length !== 1 ? "s" : ""}`;
  }

  if (filtered.length === 0) {
    tbody.innerHTML = `<tr><td colspan="5"><div class="no-results"><div class="icon">🔍</div><p>No chemicals found. Try a different search term.</p></div></td></tr>`;
    return;
  }

  const qRaw = raw.trim();
  tbody.innerHTML = filtered.map((c, i) => `
    <tr>
      <td class="td-num">${i + 1}</td>
      <td class="td-name">${highlight(c[0], qRaw)}</td>
      <td><span class="badge badge-${c[1]}">${c[1]}</span></td>
      <td class="td-loc">${highlight(c[2], qRaw)}</td>
      <td class="td-qty">${c[3]}</td>
    </tr>
  `).join("");
}

document.getElementById("searchInput").addEventListener("input", render);

document.querySelectorAll(".filter-btn").forEach(btn => {
  btn.addEventListener("click", () => {
    document.querySelectorAll(".filter-btn").forEach(b => b.classList.remove("active"));
    btn.classList.add("active");
    currentFilter = btn.dataset.filter;
    render();
  });
});

render();
</script>
</body>
</html>
