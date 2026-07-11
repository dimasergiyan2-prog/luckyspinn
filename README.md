<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KILAU168 Rewards — Member Loyalty</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700;900&family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root{
    --gold-1:#f6d97a; --gold-2:#c9962f; --gold-3:#8a6416;
    --bg-0:#08070c; --bg-card:rgba(255,255,255,0.03);
    --ink-0:#f5f1e8; --ink-1:#c9c2d6; --ink-2:#877e97; --line:rgba(246,217,122,0.16);
    --teal:#22c9a8; --crimson:#e0455a;
  }
  *{box-sizing:border-box;}
  body{
    margin:0; min-height:100vh;
    background:radial-gradient(ellipse at 50% -10%, rgba(124,77,255,0.16), transparent 45%), var(--bg-0);
    color:var(--ink-0); font-family:'Manrope',sans-serif; padding-bottom:60px;
  }
  h1,h2,h3{font-family:'Cinzel',serif;}
  .brand-title{
    font-weight:900; font-size:22px; margin:0;
    background:linear-gradient(180deg,#fff8e6,var(--gold-1) 55%,var(--gold-3));
    -webkit-background-clip:text; background-clip:text; color:transparent;
  }
  nav{
    display:flex; align-items:center; justify-content:space-between; padding:16px 5vw;
    border-bottom:1px solid var(--line); position:sticky; top:0; background:rgba(8,7,12,0.85); backdrop-filter:blur(10px); z-index:10;
  }
  .tag{font-size:11px; font-weight:700; letter-spacing:0.06em; color:var(--teal); background:rgba(34,201,168,0.12); border:1px solid rgba(34,201,168,0.3); padding:5px 12px; border-radius:99px;}

  .wrap{max-width:960px; margin:0 auto; padding:0 5vw;}

  /* login gate */
  .gate{
    max-width:420px; margin:60px auto; text-align:center; padding:36px 28px; border:1px solid var(--line);
    border-radius:18px; background:var(--bg-card);
  }
  .gate p{color:var(--ink-2); font-size:13px; margin-bottom:22px;}
  .gate input{
    width:100%; padding:13px 14px; border-radius:10px; border:1px solid var(--line); background:rgba(255,255,255,0.03);
    color:var(--ink-0); font-size:14px; margin-bottom:14px; outline:none;
  }
  .gate input:focus{border-color:var(--gold-2);}
  .btn-primary{
    width:100%; padding:14px; border:none; border-radius:10px; cursor:pointer;
    background:linear-gradient(180deg,var(--gold-1),var(--gold-2)); color:#241505; font-weight:800; font-family:'Cinzel',serif; font-size:14px;
  }
  .gate .hint{font-size:11px; color:var(--ink-2); margin-top:12px;}

  /* member dashboard */
  .dash-header{display:flex; align-items:center; justify-content:space-between; padding:26px 0 10px; flex-wrap:wrap; gap:14px;}
  .member-chip{display:flex; align-items:center; gap:10px; font-size:13px; color:var(--ink-1);}
  .member-chip .av{width:34px; height:34px; border-radius:50%; background:linear-gradient(180deg,var(--gold-1),var(--gold-2)); display:flex; align-items:center; justify-content:center; color:#241505; font-weight:800; font-family:'Cinzel',serif;}
  .logout{font-size:11px; color:var(--ink-2); cursor:pointer; text-decoration:underline;}
  .points-card{
    display:flex; align-items:center; justify-content:space-between; padding:22px 26px; border-radius:16px;
    background:linear-gradient(135deg, rgba(124,77,255,0.14), rgba(201,150,47,0.10)); border:1px solid var(--line); margin-bottom:30px;
  }
  .points-card .lbl{font-size:11px; letter-spacing:0.1em; color:var(--ink-2); text-transform:uppercase;}
  .points-card .val{font-family:'Cinzel',serif; font-size:34px; color:var(--gold-1);}

  .grid2{display:grid; grid-template-columns:340px 1fr; gap:28px;}
  @media(max-width:800px){.grid2{grid-template-columns:1fr;}}

  .panel{border:1px solid var(--line); border-radius:16px; padding:24px; background:var(--bg-card); margin-bottom:24px;}
  .panel h3{font-size:16px; color:var(--gold-1); margin:0 0 18px;}

  /* spin wheel */
  .wheel-wrap{position:relative; width:240px; height:240px; margin:0 auto 20px;}
  .pointer{position:absolute; top:-12px; left:50%; transform:translateX(-50%); z-index:5;
    width:0; height:0; border-left:12px solid transparent; border-right:12px solid transparent; border-top:18px solid var(--gold-1);}
  .wheel{width:100%; height:100%; border-radius:50%; border:5px solid var(--gold-1); box-shadow:0 0 0 3px #241505; transition:transform 4s cubic-bezier(.16,.85,.24,1);}
  .wheel svg{width:100%; height:100%; display:block; border-radius:50%;}
  .hub{position:absolute; top:50%; left:50%; width:46px; height:46px; transform:translate(-50%,-50%);
    background:linear-gradient(180deg,var(--gold-1),var(--gold-2)); border-radius:50%; z-index:4;
    display:flex; align-items:center; justify-content:center; font-family:'Cinzel',serif; font-weight:900; color:#241505; font-size:10px; box-shadow:0 0 0 4px #08070c;}
  .spin-btn{width:100%; padding:13px; border:none; border-radius:10px; cursor:pointer;
    background:linear-gradient(180deg,var(--gold-1),var(--gold-2)); color:#241505; font-weight:800; font-family:'Cinzel',serif; font-size:14px;}
  .spin-btn:disabled{opacity:0.5; cursor:not-allowed;}
  .spin-note{font-size:11px; color:var(--ink-2); text-align:center; margin-top:10px;}

  /* catalog */
  .catalog-grid{display:grid; grid-template-columns:1fr 1fr; gap:14px;}
  @media(max-width:520px){.catalog-grid{grid-template-columns:1fr;}}
  .item-card{border:1px solid var(--line); border-radius:12px; padding:16px; background:rgba(255,255,255,0.02);}
  .item-card .ic{font-size:22px; margin-bottom:8px;}
  .item-card .nm{font-size:13px; font-weight:700; margin-bottom:2px;}
  .item-card .cost{font-size:12px; color:var(--gold-1); font-weight:800; margin-bottom:10px;}
  .redeem-btn{width:100%; padding:9px; border-radius:8px; border:1px solid var(--gold-2); background:transparent; color:var(--gold-1); font-weight:700; font-size:12px; cursor:pointer;}
  .redeem-btn:disabled{opacity:0.35; cursor:not-allowed; border-color:var(--ink-2); color:var(--ink-2);}

  /* history */
  .hist-row{display:flex; justify-content:space-between; padding:10px 0; border-bottom:1px solid var(--line); font-size:12.5px;}
  .hist-row:last-child{border-bottom:none;}
  .hist-row .desc{color:var(--ink-1);}
  .hist-row .when{color:var(--ink-2); font-size:11px; display:block;}
  .hist-row .amt.plus{color:var(--teal); font-weight:800;}
  .hist-row .amt.minus{color:var(--crimson); font-weight:800;}
  .empty{color:var(--ink-2); font-size:12px; text-align:center; padding:14px 0;}

  .toast{
    position:fixed; bottom:24px; left:50%; transform:translateX(-50%) translateY(20px); opacity:0;
    background:#1b1428; border:1px solid var(--gold-2); color:var(--ink-0); padding:12px 22px; border-radius:10px;
    font-size:13px; font-weight:700; transition:all .3s; z-index:50; box-shadow:0 10px 30px rgba(0,0,0,0.5);
  }
  .toast.show{opacity:1; transform:translateX(-50%) translateY(0);}
</style>
</head>
<body>

<nav>
  <h1 class="brand-title">KILAU168 REWARDS</h1>
  <div class="tag">🏷️ Loyalty Poin — Bukan Uang Tunai</div>
</nav>

<div class="wrap">

  <!-- LOGIN GATE -->
  <div class="gate" id="gate">
    <h2 style="margin:0 0 6px; font-size:18px; color:var(--gold-1);">Masuk Member</h2>
    <p>Masukkan User ID kamu untuk melihat poin & katalog reward.</p>
    <input id="memberInput" type="text" placeholder="contoh: budi123">
    <button class="btn-primary" id="loginBtn">MASUK / DAFTAR MEMBER</button>
    <div class="hint">Member baru otomatis terdaftar dengan 0 poin.</div>
  </div>

  <!-- DASHBOARD (hidden until login) -->
  <div id="dashboard" style="display:none;">
    <div class="dash-header">
      <div class="member-chip"><div class="av" id="avatarLetter">B</div><span id="memberLabel">Member</span></div>
      <span class="logout" id="logoutBtn">Ganti Member</span>
    </div>

    <div class="points-card">
      <div>
        <div class="lbl">Saldo Poin Kamu</div>
        <div class="val" id="pointsVal">0</div>
      </div>
      <div style="font-size:34px;">💎</div>
    </div>

    <div class="grid2">
      <div>
        <div class="panel">
          <h3>Spin Harian</h3>
          <div class="wheel-wrap">
            <div class="pointer"></div>
            <div class="hub">SPIN</div>
            <div class="wheel" id="wheel"><svg viewBox="0 0 200 200" id="wheelSvg"></svg></div>
          </div>
          <button class="spin-btn" id="spinBtn">PUTAR (1x / hari)</button>
          <div class="spin-note" id="spinNote">Spin gratis tersedia hari ini.</div>
        </div>
      </div>

      <div>
        <div class="panel">
          <h3>Tukar Poin — Katalog Reward</h3>
          <div class="catalog-grid" id="catalogGrid"></div>
        </div>
        <div class="panel">
          <h3>Riwayat Poin</h3>
          <div id="historyList"><div class="empty">Belum ada riwayat.</div></div>
        </div>
      </div>
    </div>
  </div>

</div>

<div class="toast" id="toast"></div>

<script>
  // ---------- CONFIG ----------
  const catalog = [
    {id:'r1', icon:'🎟️', name:'Voucher Diskon 10%', cost:300},
    {id:'r2', icon:'🚚', name:'Gratis Ongkir', cost:200},
    {id:'r3', icon:'☕', name:'Voucher Kopi Gratis', cost:150},
    {id:'r4', icon:'🎁', name:'Bonus Produk Sample', cost:500},
    {id:'r5', icon:'💰', name:'Voucher Diskon 25%', cost:800},
    {id:'r6', icon:'👑', name:'Status VIP 1 Bulan', cost:1200},
  ];

  const spinSegments = [
    {label:'10', value:10, color:'#3a2f4d'},
    {label:'25', value:25, color:'#7c4dff'},
    {label:'50', value:50, color:'#228cc9'},
    {label:'15', value:15, color:'#3a2f4d'},
    {label:'75', value:75, color:'#22c97c'},
    {label:'30', value:30, color:'#e0455a'},
    {label:'100',value:100,color:'#c9962f'},
    {label:'20', value:20, color:'#f6d97a'},
  ];

  let currentMember = null;
  let memberData = null; // {points, history:[], lastSpin: 'YYYY-MM-DD'}

  const gate = document.getElementById('gate');
  const dashboard = document.getElementById('dashboard');
  const toast = document.getElementById('toast');

  function showToast(msg){
    toast.textContent = msg;
    toast.classList.add('show');
    setTimeout(() => toast.classList.remove('show'), 2600);
  }

  function todayStr(){
    return new Date().toISOString().slice(0,10);
  }

  function fmt(n){ return n.toLocaleString('id-ID'); }

  async function loadMember(id){
    try{
      const res = await window.storage.get('member:' + id, false);
      return res ? JSON.parse(res.value) : {points:0, history:[], lastSpin:null};
    }catch(e){
      return {points:0, history:[], lastSpin:null};
    }
  }

  async function saveMember(id, data){
    try{
      await window.storage.set('member:' + id, JSON.stringify(data), false);
    }catch(e){
      showToast('Gagal menyimpan data, coba lagi.');
    }
  }

  function addHistory(desc, delta){
    memberData.history.unshift({desc, delta, when: new Date().toLocaleString('id-ID')});
    memberData.history = memberData.history.slice(0, 20);
  }

  function renderHistory(){
    const el = document.getElementById('historyList');
    if(!memberData.history.length){
      el.innerHTML = '<div class="empty">Belum ada riwayat.</div>';
      return;
    }
    el.innerHTML = memberData.history.map(h => `
      <div class="hist-row">
        <div><div class="desc">${h.desc}</div><span class="when">${h.when}</span></div>
        <div class="amt ${h.delta >= 0 ? 'plus' : 'minus'}">${h.delta >= 0 ? '+' : ''}${fmt(h.delta)}</div>
      </div>
    `).join('');
  }

  function renderPoints(){
    document.getElementById('pointsVal').textContent = fmt(memberData.points);
  }

  function renderCatalog(){
    const grid = document.getElementById('catalogGrid');
    grid.innerHTML = catalog.map(item => `
      <div class="item-card">
        <div class="ic">${item.icon}</div>
        <div class="nm">${item.name}</div>
        <div class="cost">${fmt(item.cost)} poin</div>
        <button class="redeem-btn" data-id="${item.id}" ${memberData.points < item.cost ? 'disabled' : ''}>TUKAR</button>
      </div>
    `).join('');
    grid.querySelectorAll('.redeem-btn').forEach(btn => {
      btn.addEventListener('click', () => redeemItem(btn.dataset.id));
    });
  }

  async function redeemItem(id){
    const item = catalog.find(c => c.id === id);
    if(!item || memberData.points < item.cost) return;
    memberData.points -= item.cost;
    addHistory('Tukar: ' + item.name, -item.cost);
    await saveMember(currentMember, memberData);
    renderPoints(); renderCatalog(); renderHistory();
    showToast('Berhasil ditukar: ' + item.name + ' 🎉');
  }

  // ---------- wheel build ----------
  const svg = document.getElementById('wheelSvg');
  const n = spinSegments.length, anglePer = 360/n, cx=100, cy=100, r=100;
  spinSegments.forEach((seg,i) => {
    const startA = i*anglePer - 90, endA = startA + anglePer;
    const x1 = cx + r*Math.cos(startA*Math.PI/180), y1 = cy + r*Math.sin(startA*Math.PI/180);
    const x2 = cx + r*Math.cos(endA*Math.PI/180), y2 = cy + r*Math.sin(endA*Math.PI/180);
    const path = document.createElementNS('http://www.w3.org/2000/svg','path');
    path.setAttribute('d', `M${cx},${cy} L${x1},${y1} A${r},${r} 0 0,1 ${x2},${y2} Z`);
    path.setAttribute('fill', seg.color);
    path.setAttribute('stroke', '#08070c');
    svg.appendChild(path);
    const midA = startA + anglePer/2;
    const tx = cx + (r*0.62)*Math.cos(midA*Math.PI/180), ty = cy + (r*0.62)*Math.sin(midA*Math.PI/180);
    const text = document.createElementNS('http://www.w3.org/2000/svg','text');
    text.setAttribute('x', tx); text.setAttribute('y', ty);
    text.setAttribute('fill', '#0c0912'); text.setAttribute('font-size','12'); text.setAttribute('font-weight','800');
    text.setAttribute('text-anchor','middle');
    text.setAttribute('transform', `rotate(${midA+90}, ${tx}, ${ty})`);
    text.textContent = seg.label;
    svg.appendChild(text);
  });

  let currentRotation = 0;
  const wheel = document.getElementById('wheel');
  const spinBtn = document.getElementById('spinBtn');
  const spinNote = document.getElementById('spinNote');

  function refreshSpinAvailability(){
    if(memberData.lastSpin === todayStr()){
      spinBtn.disabled = true;
      spinNote.textContent = 'Kamu sudah spin hari ini. Kembali lagi besok!';
    } else {
      spinBtn.disabled = false;
      spinNote.textContent = 'Spin gratis tersedia hari ini.';
    }
  }

  spinBtn.addEventListener('click', () => {
    if(memberData.lastSpin === todayStr()) return;
    spinBtn.disabled = true;

    const winnerIndex = Math.floor(Math.random()*n);
    const targetCenter = winnerIndex*anglePer + anglePer/2;
    currentRotation += 5*360 + (360 - targetCenter);
    wheel.style.transform = `rotate(${currentRotation}deg)`;

    setTimeout(async () => {
      const seg = spinSegments[winnerIndex];
      memberData.points += seg.value;
      memberData.lastSpin = todayStr();
      addHistory('Hasil Spin Harian', seg.value);
      await saveMember(currentMember, memberData);
      renderPoints(); renderCatalog(); renderHistory(); refreshSpinAvailability();
      showToast(`🎉 Kamu dapat ${seg.value} poin!`);
    }, 4200);
  });

  // ---------- login flow ----------
  document.getElementById('loginBtn').addEventListener('click', async () => {
    const val = document.getElementById('memberInput').value.trim();
    if(!val){ showToast('Isi ID member / email dulu ya.'); return; }
    currentMember = val.toLowerCase();
    memberData = await loadMember(currentMember);
    document.getElementById('memberLabel').textContent = val;
    document.getElementById('avatarLetter').textContent = val[0].toUpperCase();
    gate.style.display = 'none';
    dashboard.style.display = 'block';
    renderPoints(); renderCatalog(); renderHistory(); refreshSpinAvailability();
  });

  document.getElementById('logoutBtn').addEventListener('click', () => {
    currentMember = null; memberData = null;
    dashboard.style.display = 'none';
    gate.style.display = 'block';
    document.getElementById('memberInput').value = '';
  });
</script>
</body>
</html>
