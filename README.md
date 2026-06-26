<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ReWatch — Marketplace</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --black: #0A0A0A;
    --cream: #F5F0E8;
    --gold: #C9A84C;
    --gold-light: #E8D49A;
    --dark: #2A2A2A;
    --mid: #6B6B6B;
    --border: #E0D8CC;
  }

  body {
    background: var(--cream);
    color: var(--black);
    font-family: 'Inter', sans-serif;
    font-weight: 300;
    min-height: 100vh;
  }

  /* HEADER */
  header {
    border-bottom: 1px solid var(--border);
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    background: var(--cream);
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo {
    font-family: 'Inter', sans-serif;
    font-size: 1.4rem;
    font-weight: 800;
    letter-spacing: -0.02em;
    color: var(--black);
    text-decoration: none;
    text-transform: uppercase;
  }

  .logo span {
    color: var(--gold);
    font-style: italic;
  }

  .header-actions {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  /* BUTTONS */
  .btn {
    font-family: 'Inter', sans-serif;
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.6rem 1.4rem;
    border: none;
    cursor: pointer;
    transition: all 0.2s;
    text-decoration: none;
    display: inline-block;
  }

  .btn-primary {
    background: var(--black);
    color: var(--cream);
  }

  .btn-primary:hover {
    background: var(--dark);
  }

  .btn-outline {
    background: transparent;
    color: var(--black);
    border: 1px solid var(--border);
  }

  .btn-outline:hover {
    border-color: var(--black);
  }

  .btn-gold {
    background: var(--gold);
    color: var(--black);
  }

  .btn-gold:hover {
    background: var(--gold-light);
  }

  .btn-danger {
    background: transparent;
    color: #C0392B;
    border: 1px solid #C0392B;
    font-size: 0.7rem;
    padding: 0.4rem 0.9rem;
  }

  .btn-danger:hover {
    background: #C0392B;
    color: white;
  }

  /* HERO */
  .hero {
    border-bottom: 1px solid var(--border);
    padding: 5rem 2rem;
    text-align: center;
    position: relative;
    overflow: hidden;
    background: var(--black);
  }

  .hero::before {
    content: '';
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 400px;
    height: 400px;
    border-radius: 50%;
    border: 1px solid #2a2a2a;
    pointer-events: none;
  }

  .hero::after {
    content: '';
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 600px;
    height: 600px;
    border-radius: 50%;
    border: 1px solid #1e1e1e;
    opacity: 0.6;
    pointer-events: none;
  }

  .hero h1 {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(2.5rem, 6vw, 4.5rem);
    font-weight: 300;
    line-height: 1.1;
    letter-spacing: 0.02em;
    position: relative;
    z-index: 1;
    color: #ffffff;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--gold);
  }

  .hero-sub {
    font-size: 0.8rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: #6B6B6B;
    margin-top: 1.2rem;
    position: relative;
    z-index: 1;
  }

  .gold-line {
    display: block;
    width: 48px;
    height: 1px;
    background: var(--gold);
    margin: 1.5rem auto;
    position: relative;
    z-index: 1;
  }

  /* TOOLBAR */
  .toolbar {
    padding: 1.2rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid var(--border);
    gap: 1rem;
    flex-wrap: wrap;
  }

  .search-wrap {
    position: relative;
    flex: 1;
    max-width: 320px;
  }

  .search-wrap input {
    width: 100%;
    padding: 0.55rem 1rem 0.55rem 2.4rem;
    border: 1px solid var(--border);
    background: white;
    font-family: 'Inter', sans-serif;
    font-size: 0.8rem;
    color: var(--black);
    outline: none;
    transition: border-color 0.2s;
  }

  .search-wrap input:focus { border-color: var(--gold); }

  .search-icon {
    position: absolute;
    left: 0.8rem;
    top: 50%;
    transform: translateY(-50%);
    color: var(--mid);
    font-size: 0.85rem;
    pointer-events: none;
  }

  .count {
    font-size: 0.75rem;
    color: var(--mid);
    letter-spacing: 0.05em;
  }

  /* GRID */
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1px;
    background: var(--border);
    border-top: 1px solid var(--border);
  }

  /* CARD */
  .card {
    background: var(--cream);
    cursor: pointer;
    transition: background 0.15s;
    position: relative;
  }

  .card:hover { background: white; }

  .card-img {
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
    display: block;
    background: #E8E3DB;
  }

  .card-img-placeholder {
    width: 100%;
    aspect-ratio: 1;
    background: #EDE8E0;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--border);
    font-size: 3rem;
  }

  .card-body {
    padding: 1.2rem;
  }

  .card-brand {
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.3rem;
  }

  .card-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.2rem;
    font-weight: 400;
    color: var(--black);
    margin-bottom: 0.5rem;
    line-height: 1.2;
  }

  .card-price {
    font-size: 1rem;
    font-weight: 500;
    color: var(--black);
    margin-bottom: 0.5rem;
  }

  .card-location {
    font-size: 0.72rem;
    color: var(--mid);
  }

  /* EMPTY */
  .empty {
    grid-column: 1 / -1;
    background: var(--cream);
    text-align: center;
    padding: 6rem 2rem;
  }

  .empty-icon { font-size: 3rem; margin-bottom: 1rem; opacity: 0.3; }

  .empty h3 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.6rem;
    font-weight: 300;
    margin-bottom: 0.5rem;
  }

  .empty p { font-size: 0.8rem; color: var(--mid); }

  /* MODAL OVERLAY */
  .overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.6);
    z-index: 200;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.25s;
  }

  .overlay.open {
    opacity: 1;
    pointer-events: all;
  }

  .modal {
    background: var(--cream);
    width: 100%;
    max-width: 560px;
    max-height: 90vh;
    overflow-y: auto;
    transform: translateY(16px);
    transition: transform 0.25s;
  }

  .overlay.open .modal { transform: translateY(0); }

  .modal-header {
    padding: 1.5rem 2rem;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .modal-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.4rem;
    font-weight: 300;
  }

  .modal-close {
    background: none;
    border: none;
    font-size: 1.4rem;
    cursor: pointer;
    color: var(--mid);
    line-height: 1;
    padding: 0.2rem;
  }

  .modal-close:hover { color: var(--black); }

  .modal-body { padding: 2rem; }

  /* FORM */
  .form-group { margin-bottom: 1.4rem; }

  label {
    display: block;
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--mid);
    margin-bottom: 0.45rem;
  }

  input[type="text"],
  input[type="number"],
  input[type="tel"],
  input[type="email"],
  input[type="url"],
  textarea,
  select {
    width: 100%;
    padding: 0.7rem 1rem;
    border: 1px solid var(--border);
    background: white;
    font-family: 'Inter', sans-serif;
    font-size: 0.85rem;
    color: var(--black);
    outline: none;
    transition: border-color 0.2s;
  }

  input:focus,
  textarea:focus,
  select:focus {
    border-color: var(--gold);
  }

  textarea { resize: vertical; min-height: 90px; }

  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .form-actions {
    display: flex;
    gap: 0.8rem;
    justify-content: flex-end;
    margin-top: 1.5rem;
    padding-top: 1.5rem;
    border-top: 1px solid var(--border);
  }

  /* IMAGE UPLOAD */
  .upload-area {
    border: 1px dashed var(--border);
    padding: 2rem;
    text-align: center;
    cursor: pointer;
    transition: border-color 0.2s;
    background: white;
    position: relative;
  }

  .upload-area:hover { border-color: var(--gold); }

  .upload-area input[type="file"] {
    position: absolute;
    inset: 0;
    opacity: 0;
    cursor: pointer;
    width: 100%;
    height: 100%;
    padding: 0;
    border: none;
  }

  .upload-text {
    font-size: 0.75rem;
    color: var(--mid);
    pointer-events: none;
  }

  .upload-preview {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-top: 0.8rem;
  }

  .upload-preview img {
    width: 72px;
    height: 72px;
    object-fit: cover;
    border: 1px solid var(--border);
  }

  .upload-preview .rm-img {
    position: relative;
    display: inline-block;
  }

  .upload-preview .rm-img button {
    position: absolute;
    top: -6px;
    right: -6px;
    background: var(--black);
    color: white;
    border: none;
    border-radius: 50%;
    width: 18px;
    height: 18px;
    font-size: 10px;
    cursor: pointer;
    line-height: 1;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* DETAIL MODAL */
  .detail-imgs {
    display: flex;
    gap: 0.5rem;
    overflow-x: auto;
    padding-bottom: 0.5rem;
    margin-bottom: 1.5rem;
  }

  .detail-imgs img {
    height: 220px;
    width: auto;
    object-fit: cover;
    flex-shrink: 0;
    max-width: 100%;
  }

  .detail-brand {
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.4rem;
  }

  .detail-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 300;
    margin-bottom: 0.5rem;
    line-height: 1.1;
  }

  .detail-price {
    font-size: 1.4rem;
    font-weight: 500;
    margin-bottom: 1.2rem;
  }

  .detail-desc {
    font-size: 0.85rem;
    line-height: 1.7;
    color: var(--dark);
    margin-bottom: 1.5rem;
    white-space: pre-wrap;
  }

  .detail-sep {
    height: 1px;
    background: var(--border);
    margin: 1.5rem 0;
    position: relative;
  }

  .detail-sep::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 48px;
    height: 1px;
    background: var(--gold);
  }

  .contact-section h4 {
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--mid);
    margin-bottom: 1rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 0.7rem;
    font-size: 0.85rem;
    margin-bottom: 0.6rem;
  }

  .contact-item a {
    color: var(--black);
    text-decoration: none;
  }

  .contact-item a:hover {
    color: var(--gold);
  }

  .contact-label {
    font-size: 0.65rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--mid);
    min-width: 60px;
  }

  .badge {
    display: inline-block;
    font-size: 0.65rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.25rem 0.6rem;
    background: var(--black);
    color: var(--cream);
    margin-right: 0.4rem;
    margin-bottom: 0.4rem;
  }

  .meta-row {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    margin-bottom: 1rem;
  }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem;
    text-align: center;
    font-size: 0.72rem;
    color: var(--mid);
    letter-spacing: 0.05em;
  }

  footer strong { color: var(--gold); }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--cream); }
  ::-webkit-scrollbar-thumb { background: var(--border); }

  @media (max-width: 600px) {
    .hero { padding: 3rem 1.5rem; }
    .toolbar { padding: 1rem 1.2rem; }
    .search-wrap { max-width: 100%; }
    .modal-body { padding: 1.5rem; }
    .form-row { grid-template-columns: 1fr; }
    .detail-imgs img { height: 180px; }
  }
</style>
</head>
<body>

<header>
  <a href="#" class="logo" onclick="showList(); return false;">ReWatch</a>
  <div class="header-actions">
    <button class="btn btn-primary" onclick="openSell()">+ Vendi</button>
  </div>
</header>

<!-- HERO -->
<section class="hero" id="heroSection">
  <h1 style="color:#ffffff;">Compra e vendi orologi<br><em>senza commissioni</em></h1>
  <span class="gold-line"></span>
  <p class="hero-sub">Annunci diretti — venditore e acquirente in contatto diretto</p>
</section>

<!-- TOOLBAR -->
<div class="toolbar">
  <div class="search-wrap">
    <span class="search-icon">⌕</span>
    <input type="text" id="searchInput" placeholder="Cerca marca, modello…" oninput="renderList()">
  </div>
  <span class="count" id="countLabel"></span>
</div>

<!-- GRID -->
<div class="grid" id="grid"></div>

<!-- FOOTER -->
<footer>
  Marketplace <strong>zero commissioni</strong> — i venditori e gli acquirenti si accordano direttamente.<br>
  Nessun intermediario, nessuna fee, nessun account richiesto.
</footer>

<!-- SELL MODAL -->
<div class="overlay" id="sellOverlay" onclick="closeSell(event)">
  <div class="modal" role="dialog" aria-modal="true" aria-label="Pubblica annuncio">
    <div class="modal-header">
      <span class="modal-title">Pubblica annuncio</span>
      <button class="modal-close" onclick="closeSell()">✕</button>
    </div>
    <div class="modal-body">
      <div class="form-group">
        <label>Marca *</label>
        <input type="text" id="fBrand" placeholder="es. Rolex, Omega, Tudor…">
      </div>
      <div class="form-group">
        <label>Modello *</label>
        <input type="text" id="fModel" placeholder="es. Submariner Date 116610LN">
      </div>
      <div class="form-row">
        <div class="form-group">
          <label>Prezzo (€) *</label>
          <input type="number" id="fPrice" placeholder="12000" min="0">
        </div>
        <div class="form-group">
          <label>Anno</label>
          <input type="number" id="fYear" placeholder="2019" min="1900" max="2099">
        </div>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label>Condizione</label>
          <select id="fCond">
            <option value="">— seleziona —</option>
            <option>Nuovo / Mai indossato</option>
            <option>Ottimo</option>
            <option>Buono</option>
            <option>Discreto</option>
            <option>Da revisionare</option>
          </select>
        </div>
        <div class="form-group">
          <label>Città</label>
          <input type="text" id="fCity" placeholder="es. Milano">
        </div>
      </div>
      <div class="form-group">
        <label>Descrizione</label>
        <textarea id="fDesc" placeholder="Condizioni, storia, accessori inclusi (scatola, garanzia, documenti)…"></textarea>
      </div>
      <div class="form-group">
        <label>Foto (max 6)</label>
        <div class="upload-area">
          <div class="upload-text">📷 Clicca o trascina le foto qui</div>
          <input type="file" id="fPhotos" multiple accept="image/*" onchange="handlePhotos(event)">
        </div>
        <div class="upload-preview" id="photoPreview"></div>
      </div>
      <div class="form-group">
        <label>Telefono / WhatsApp *</label>
        <input type="tel" id="fPhone" placeholder="+39 333 000 0000">
      </div>
      <div class="form-group">
        <label>Email</label>
        <input type="email" id="fEmail" placeholder="tua@email.com">
      </div>
      <div class="form-group">
        <label>Instagram / Link annuncio</label>
        <input type="url" id="fLink" placeholder="https://…">
      </div>
      <div class="form-actions">
        <button class="btn btn-outline" onclick="closeSell()">Annulla</button>
        <button class="btn btn-gold" onclick="publishListing()">Pubblica</button>
      </div>
    </div>
  </div>
</div>

<!-- DETAIL MODAL -->
<div class="overlay" id="detailOverlay" onclick="closeDetail(event)">
  <div class="modal" role="dialog" aria-modal="true" aria-label="Dettaglio annuncio">
    <div class="modal-header">
      <span class="modal-title" id="detailModalTitle">Dettaglio</span>
      <button class="modal-close" onclick="closeDetail()">✕</button>
    </div>
    <div class="modal-body" id="detailBody"></div>
  </div>
</div>

<script>
  // ── DATA ──────────────────────────────────────────────────────────────────
  const STORAGE_KEY = 'orologi_listings_v1';

  function load() {
    try { return JSON.parse(localStorage.getItem(STORAGE_KEY)) || []; } catch { return []; }
  }

  function save(data) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
  }

  // ── PHOTOS ────────────────────────────────────────────────────────────────
  let pendingPhotos = [];

  function handlePhotos(e) {
    const files = Array.from(e.target.files).slice(0, 6 - pendingPhotos.length);
    files.forEach(file => {
      const reader = new FileReader();
      reader.onload = ev => {
        pendingPhotos.push(ev.target.result);
        renderPhotoPreview();
      };
      reader.readAsDataURL(file);
    });
    e.target.value = '';
  }

  function renderPhotoPreview() {
    const el = document.getElementById('photoPreview');
    el.innerHTML = pendingPhotos.map((src, i) => `
      <div class="rm-img">
        <img src="${src}" alt="">
        <button onclick="removePhoto(${i})" title="Rimuovi">✕</button>
      </div>`).join('');
  }

  function removePhoto(i) {
    pendingPhotos.splice(i, 1);
    renderPhotoPreview();
  }

  // ── SELL MODAL ────────────────────────────────────────────────────────────
  function openSell() {
    document.getElementById('sellOverlay').classList.add('open');
    document.body.style.overflow = 'hidden';
  }

  function closeSell(e) {
    if (e && e.target !== document.getElementById('sellOverlay')) return;
    document.getElementById('sellOverlay').classList.remove('open');
    document.body.style.overflow = '';
  }

  function val(id) { return document.getElementById(id).value.trim(); }

  function publishListing() {
    const brand = val('fBrand'), model = val('fModel'), phone = val('fPhone'), price = val('fPrice');
    if (!brand || !model || !phone || !price) {
      alert('Compila i campi obbligatori: Marca, Modello, Prezzo, Telefono.');
      return;
    }

    const listing = {
      id: Date.now().toString(),
      brand, model, price: parseFloat(price),
      year: val('fYear'), cond: val('fCond'), city: val('fCity'),
      desc: val('fDesc'), phone: val('fPhone'), email: val('fEmail'),
      link: val('fLink'), photos: [...pendingPhotos],
      date: new Date().toLocaleDateString('it-IT')
    };

    const data = load();
    data.unshift(listing);
    save(data);

    // Reset
    ['fBrand','fModel','fPrice','fYear','fCond','fCity','fDesc','fPhone','fEmail','fLink']
      .forEach(id => document.getElementById(id).value = '');
    pendingPhotos = [];
    renderPhotoPreview();

    closeSell();
    renderList();
  }

  // ── LIST ──────────────────────────────────────────────────────────────────
  function renderList() {
    const q = document.getElementById('searchInput').value.toLowerCase();
    let data = load();
    if (q) data = data.filter(l =>
      (l.brand + l.model + l.city + l.desc).toLowerCase().includes(q)
    );

    document.getElementById('countLabel').textContent =
      data.length === 0 ? '' : `${data.length} annunci`;

    const grid = document.getElementById('grid');
    if (!data.length) {
      grid.innerHTML = `<div class="empty">
        <div class="empty-icon">⊙</div>
        <h3>Nessun annuncio</h3>
        <p>Sii il primo a vendere il tuo orologio.</p>
      </div>`;
      return;
    }

    grid.innerHTML = data.map(l => {
      const img = l.photos?.[0]
        ? `<img class="card-img" src="${l.photos[0]}" alt="${l.brand} ${l.model}" loading="lazy">`
        : `<div class="card-img-placeholder">⊙</div>`;
      return `<div class="card" onclick="openDetail('${l.id}')">
        ${img}
        <div class="card-body">
          <div class="card-brand">${l.brand}</div>
          <div class="card-title">${l.model}${l.year ? ' · ' + l.year : ''}</div>
          <div class="card-price">€ ${Number(l.price).toLocaleString('it-IT')}</div>
          ${l.city ? `<div class="card-location">📍 ${l.city}</div>` : ''}
        </div>
      </div>`;
    }).join('');
  }

  function showList() {
    document.getElementById('heroSection').style.display = '';
    renderList();
  }

  // ── DETAIL ────────────────────────────────────────────────────────────────
  function openDetail(id) {
    const data = load();
    const l = data.find(x => x.id === id);
    if (!l) return;

    document.getElementById('detailModalTitle').textContent = `${l.brand} ${l.model}`;

    const imgs = l.photos?.length
      ? `<div class="detail-imgs">${l.photos.map(s => `<img src="${s}" alt="">`).join('')}</div>`
      : '';

    const meta = [
      l.cond ? `<span class="badge">${l.cond}</span>` : '',
      l.year ? `<span class="badge">${l.year}</span>` : '',
      l.city ? `<span class="badge">📍 ${l.city}</span>` : '',
    ].join('');

    const contact = [
      l.phone ? `<div class="contact-item"><span class="contact-label">Tel</span>
        <a href="tel:${l.phone}">${l.phone}</a></div>` : '',
      l.phone ? `<div class="contact-item"><span class="contact-label">WhatsApp</span>
        <a href="https://wa.me/${l.phone.replace(/\D/g,'')}" target="_blank">Apri chat</a></div>` : '',
      l.email ? `<div class="contact-item"><span class="contact-label">Email</span>
        <a href="mailto:${l.email}">${l.email}</a></div>` : '',
      l.link ? `<div class="contact-item"><span class="contact-label">Link</span>
        <a href="${l.link}" target="_blank" rel="noopener">Visita →</a></div>` : '',
    ].join('');

    document.getElementById('detailBody').innerHTML = `
      ${imgs}
      <div class="detail-brand">${l.brand}</div>
      <div class="detail-title">${l.model}</div>
      <div class="detail-price">€ ${Number(l.price).toLocaleString('it-IT')}</div>
      ${meta ? `<div class="meta-row">${meta}</div>` : ''}
      ${l.desc ? `<div class="detail-desc">${l.desc}</div>` : ''}
      <div class="detail-sep"></div>
      <div class="contact-section">
        <h4>Contatta il venditore</h4>
        ${contact}
      </div>
      <div class="detail-sep"></div>
      <div style="text-align:right">
        <button class="btn btn-danger" onclick="deleteListing('${l.id}')">Rimuovi annuncio</button>
      </div>
      <div style="font-size:0.7rem;color:var(--mid);margin-top:0.8rem;text-align:right">
        Pubblicato il ${l.date}
      </div>
    `;

    document.getElementById('detailOverlay').classList.add('open');
    document.body.style.overflow = 'hidden';
  }

  function closeDetail(e) {
    if (e && e.target !== document.getElementById('detailOverlay')) return;
    document.getElementById('detailOverlay').classList.remove('open');
    document.body.style.overflow = '';
  }

  function deleteListing(id) {
    if (!confirm('Vuoi rimuovere questo annuncio?')) return;
    const data = load().filter(x => x.id !== id);
    save(data);
    closeDetail();
    renderList();
  }

  // ── ESC KEY ───────────────────────────────────────────────────────────────
  document.addEventListener('keydown', e => {
    if (e.key === 'Escape') {
      closeSell();
      closeDetail();
    }
  });

  // ── INIT ──────────────────────────────────────────────────────────────────
  renderList();
</script>
</body>
</html>
