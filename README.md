<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NestJS Rehberi — Sıfırdan Hard Seviyeye</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Sora:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0e0f14;
  --surface: #161820;
  --surface2: #1d1f2a;
  --border: #2a2d3e;
  --text: #e2e4f0;
  --muted: #7a7d94;
  --accent: #4e9bff;
  --accent2: #a78bfa;
  --green: #4ade80;
  --amber: #fbbf24;
  --red: #f87171;
  --cyan: #22d3ee;
  --font-mono: 'JetBrains Mono', monospace;
  --font: 'Sora', sans-serif;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: var(--font);
  background: var(--bg);
  color: var(--text);
  line-height: 1.7;
  display: flex;
}

/* SIDEBAR */
nav {
  width: 260px;
  min-width: 260px;
  background: var(--surface);
  border-right: 1px solid var(--border);
  height: 100vh;
  position: sticky;
  top: 0;
  overflow-y: auto;
  padding: 1.5rem 0;
  scrollbar-width: thin;
  scrollbar-color: var(--border) transparent;
}
.nav-header {
  padding: 0 1.25rem 1.25rem;
  border-bottom: 1px solid var(--border);
  margin-bottom: 1rem;
}
.nav-header h1 {
  font-size: 13px;
  font-weight: 600;
  color: var(--accent);
  letter-spacing: 0.08em;
  text-transform: uppercase;
}
.nav-header span {
  font-size: 11px;
  color: var(--muted);
}
nav a {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 6px 1.25rem;
  font-size: 12.5px;
  color: var(--muted);
  text-decoration: none;
  border-left: 2px solid transparent;
  transition: all 0.15s;
}
nav a:hover { color: var(--text); background: var(--surface2); }
nav a.active { color: var(--accent); border-left-color: var(--accent); background: rgba(78,155,255,0.06); }
.nav-badge {
  margin-left: auto;
  font-size: 9px;
  padding: 1px 6px;
  border-radius: 10px;
  font-weight: 600;
  letter-spacing: 0.04em;
}
.badge-temel { background: rgba(74,222,128,0.15); color: var(--green); }
.badge-orta { background: rgba(251,191,36,0.15); color: var(--amber); }
.badge-ileri { background: rgba(167,139,250,0.15); color: var(--accent2); }
.badge-uzman { background: rgba(248,113,113,0.15); color: var(--red); }

/* MAIN */
main {
  flex: 1;
  max-width: 900px;
  padding: 3rem 3.5rem;
  min-width: 0;
}

/* HERO */
.hero {
  margin-bottom: 3.5rem;
  padding-bottom: 2.5rem;
  border-bottom: 1px solid var(--border);
}
.hero-tag {
  display: inline-block;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent);
  background: rgba(78,155,255,0.1);
  padding: 3px 12px;
  border-radius: 20px;
  margin-bottom: 1rem;
}
.hero h1 {
  font-size: 2.4rem;
  font-weight: 600;
  line-height: 1.2;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #e2e4f0 0%, #7a7d94 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero p {
  font-size: 15px;
  color: var(--muted);
  max-width: 600px;
}
.level-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  margin-top: 2rem;
}
.level-card {
  padding: 12px;
  border-radius: 8px;
  border: 1px solid var(--border);
  background: var(--surface);
}
.level-card .lc-num { font-size: 20px; font-weight: 600; font-family: var(--font-mono); }
.level-card .lc-lbl { font-size: 11px; color: var(--muted); margin-top: 2px; }
.level-card.t .lc-num { color: var(--green); }
.level-card.o .lc-num { color: var(--amber); }
.level-card.i .lc-num { color: var(--accent2); }
.level-card.u .lc-num { color: var(--red); }

/* SECTION */
.section {
  margin-bottom: 4rem;
  scroll-margin-top: 2rem;
}
.section-label {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 0.5rem;
}
.sec-num {
  font-size: 11px;
  font-weight: 700;
  font-family: var(--font-mono);
  color: var(--muted);
  letter-spacing: 0.05em;
}
.sec-badge {
  font-size: 10px;
  font-weight: 600;
  padding: 2px 8px;
  border-radius: 10px;
  letter-spacing: 0.04em;
}
.section h2 {
  font-size: 1.6rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: var(--text);
}
.section > p, .section .intro {
  font-size: 14.5px;
  color: var(--muted);
  margin-bottom: 1.25rem;
  line-height: 1.75;
}
.section h3 {
  font-size: 1rem;
  font-weight: 600;
  color: var(--text);
  margin: 1.75rem 0 0.6rem;
}
.section h4 {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 0.07em;
  margin: 1.25rem 0 0.5rem;
}
.divider {
  border: none;
  border-top: 1px solid var(--border);
  margin: 3.5rem 0;
}

/* CODE BLOCKS */
.code-wrap {
  margin: 1rem 0 1.5rem;
  border-radius: 10px;
  overflow: hidden;
  border: 1px solid var(--border);
}
.code-title {
  background: var(--surface2);
  padding: 7px 14px;
  font-size: 11px;
  font-family: var(--font-mono);
  color: var(--muted);
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  gap: 6px;
}
.code-title::before {
  content: '';
  display: inline-block;
  width: 8px; height: 8px;
  border-radius: 50%;
  background: var(--accent);
  opacity: 0.6;
}
pre {
  background: #0a0c12;
  padding: 1.25rem 1.5rem;
  overflow-x: auto;
  font-family: var(--font-mono);
  font-size: 13px;
  line-height: 1.8;
  tab-size: 2;
}
code { font-family: var(--font-mono); }

/* SYNTAX */
.kw { color: #c792ea; }
.fn { color: #82aaff; }
.str { color: #c3e88d; }
.dec { color: #ffcb6b; }
.cmt { color: #546e7a; font-style: italic; }
.cls { color: #ffcb6b; }
.typ { color: #80cbc4; }
.num { color: #f78c6c; }
.op { color: #89ddff; }
.prop { color: #b0c9f0; }

/* CALLOUTS */
.callout {
  padding: 1rem 1.25rem;
  border-radius: 8px;
  border-left: 3px solid;
  margin: 1.25rem 0;
  font-size: 13.5px;
  line-height: 1.7;
}
.callout.info { background: rgba(78,155,255,0.07); border-color: var(--accent); color: #8ec5ff; }
.callout.warn { background: rgba(251,191,36,0.07); border-color: var(--amber); color: #fcd97c; }
.callout.ok { background: rgba(74,222,128,0.07); border-color: var(--green); color: #7de0a4; }
.callout.danger { background: rgba(248,113,113,0.07); border-color: var(--red); color: #fb9d9d; }
.callout strong { color: inherit; font-weight: 600; }

/* TABLES */
.table-wrap { overflow-x: auto; margin: 1.25rem 0; }
table { width: 100%; border-collapse: collapse; font-size: 13px; }
th {
  background: var(--surface2);
  color: var(--muted);
  font-weight: 600;
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  padding: 8px 12px;
  text-align: left;
  border-bottom: 1px solid var(--border);
}
td {
  padding: 8px 12px;
  border-bottom: 1px solid var(--border);
  color: var(--text);
  vertical-align: top;
}
td code {
  font-size: 12px;
  background: var(--surface2);
  padding: 1px 5px;
  border-radius: 3px;
  color: var(--accent);
}
tr:last-child td { border-bottom: none; }

/* INLINE CODE */
p code, li code {
  font-size: 12px;
  background: var(--surface2);
  padding: 1px 5px;
  border-radius: 3px;
  color: var(--cyan);
  font-family: var(--font-mono);
}
ul, ol { padding-left: 1.5rem; margin: 0.75rem 0; }
li { margin-bottom: 0.4rem; font-size: 14px; color: var(--muted); }
li code { color: var(--cyan); }
</style>
</head>
<body>

<nav id="sidebar">
  <div class="nav-header">
    <h1>NestJS Rehberi</h1>
    <span>Sıfırdan Hard Seviyeye</span>
  </div>
  <a href="#s01">01 · Giriş &amp; Kurulum <span class="nav-badge badge-temel">Temel</span></a>
  <a href="#s02">02 · Controller <span class="nav-badge badge-temel">Temel</span></a>
  <a href="#s03">03 · Service &amp; DI <span class="nav-badge badge-temel">Temel</span></a>
  <a href="#s04">04 · Module Sistemi <span class="nav-badge badge-temel">Temel</span></a>
  <a href="#s05">05 · DTO &amp; Validation <span class="nav-badge badge-orta">Orta</span></a>
  <a href="#s06">06 · TypeORM &amp; DB <span class="nav-badge badge-orta">Orta</span></a>
  <a href="#s07">07 · Authentication <span class="nav-badge badge-orta">Orta</span></a>
  <a href="#s08">08 · Config &amp; Env <span class="nav-badge badge-orta">Orta</span></a>
  <a href="#s09">09 · Interceptors <span class="nav-badge badge-ileri">İleri</span></a>
  <a href="#s10">10 · Exception Filters <span class="nav-badge badge-ileri">İleri</span></a>
  <a href="#s11">11 · Guards &amp; Roles <span class="nav-badge badge-ileri">İleri</span></a>
  <a href="#s12">12 · Middleware <span class="nav-badge badge-ileri">İleri</span></a>
  <a href="#s13">13 · @Req() &amp; @Res() <span class="nav-badge badge-ileri">İleri</span></a>
  <a href="#s14">14 · WebSockets <span class="nav-badge badge-uzman">Uzman</span></a>
  <a href="#s15">15 · Microservices <span class="nav-badge badge-uzman">Uzman</span></a>
  <a href="#s16">16 · CQRS Pattern <span class="nav-badge badge-uzman">Uzman</span></a>
  <a href="#s17">17 · Testing <span class="nav-badge badge-uzman">Uzman</span></a>
  <a href="#s18">18 · Deployment <span class="nav-badge badge-uzman">Uzman</span></a>
</nav>

<main>

  <!-- HERO -->
  <div class="hero">
    <span class="hero-tag">Türkçe Dokümantasyon</span>
    <h1>NestJS Tam Rehber</h1>
    <p>Sıfırdan başlayıp production-ready microservice mimarisine kadar her şeyi kapsayan kapsamlı Türkçe referans kaynağı.</p>
    <div class="level-grid">
      <div class="level-card t"><div class="lc-num">01–04</div><div class="lc-lbl">Temel</div></div>
      <div class="level-card o"><div class="lc-num">05–08</div><div class="lc-lbl">Orta</div></div>
      <div class="level-card i"><div class="lc-num">09–13</div><div class="lc-lbl">İleri</div></div>
      <div class="level-card u"><div class="lc-num">14–18</div><div class="lc-lbl">Uzman</div></div>
    </div>
  </div>

  <!-- BÖLÜM 01 -->
  <section class="section" id="s01">
    <div class="section-label">
      <span class="sec-num">01</span>
      <span class="sec-badge badge-temel">Temel</span>
    </div>
    <h2>NestJS Nedir? Kurulum &amp; Proje Yapısı</h2>
    <p class="intro">
      NestJS, Node.js üzerinde çalışan, TypeScript ile yazılmış, Angular'dan ilham alan bir backend framework'üdür.
      Express veya Fastify üzerine inşa edilmiş olup modüler mimari, dependency injection, decorator tabanlı
      geliştirme ve güçlü CLI araçlarıyla enterprise ölçekli uygulamalar yazmayı kolaylaştırır.
    </p>

    <h3>Neden NestJS?</h3>
    <ul>
      <li>TypeScript first — tip güvenliği, IDE desteği, refactoring kolaylığı</li>
      <li>Angular benzeri modüler mimari — büyük ekiplerde organize kod</li>
      <li>Dependency Injection built-in — test edilebilir, decoupled servisler</li>
      <li>Decorator tabanlı — temiz, okunabilir controller/servis tanımı</li>
      <li>Express veya Fastify — iki transport platformunu da destekler</li>
      <li>WebSocket, Microservice, GraphQL gibi advanced özellikleri yerli destekler</li>
    </ul>

    <h3>Kurulum</h3>
    <div class="callout info">Node.js 18+ ve npm 9+ gereklidir. <code>node --version</code> ile kontrol et.</div>

    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install -g @nestjs/cli
nest new proje-adi
cd proje-adi
npm run start:dev</pre>
    </div>

    <p>CLI sana paket yöneticisini sorar (npm / yarn / pnpm). Proje oluşturulunca şu yapıyı göreceksin:</p>

    <div class="code-wrap">
      <div class="code-title">proje-adi/ — klasör yapısı</div>
      <pre>src/
  app.controller.ts    ← HTTP isteklerini karşılar
  app.service.ts       ← iş mantığı burada
  app.module.ts        ← modülleri birleştirir
  main.ts              ← uygulama başlangıç noktası
test/
  app.e2e-spec.ts
nest-cli.json          ← CLI konfigürasyonu
tsconfig.json
package.json</pre>
    </div>

    <h3>main.ts — Başlangıç Noktası</h3>
    <div class="code-wrap">
      <div class="code-title">src/main.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">NestFactory</span> } <span class="kw">from</span> <span class="str">'@nestjs/core'</span>;
<span class="kw">import</span> { <span class="cls">AppModule</span> } <span class="kw">from</span> <span class="str">'./app.module'</span>;
<span class="kw">import</span> { <span class="cls">ValidationPipe</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="kw">async function</span> <span class="fn">bootstrap</span>() {
  <span class="kw">const</span> app = <span class="kw">await</span> <span class="cls">NestFactory</span>.<span class="fn">create</span>(<span class="cls">AppModule</span>);

  <span class="cmt">// Global validation pipe — tüm DTO'lar otomatik validate edilir</span>
  app.<span class="fn">useGlobalPipes</span>(<span class="kw">new</span> <span class="cls">ValidationPipe</span>({
    whitelist: <span class="kw">true</span>,      <span class="cmt">// DTO'da tanımsız alanları sil</span>
    forbidNonWhitelisted: <span class="kw">true</span>,  <span class="cmt">// bilinmeyen alan gelirse hata fırlat</span>
    transform: <span class="kw">true</span>,     <span class="cmt">// string'den number'a otomatik dönüştür</span>
  }));

  <span class="cmt">// CORS ayarla (frontend farklı porttan çalışıyorsa)</span>
  app.<span class="fn">enableCors</span>({
    origin: <span class="str">'http://localhost:3000'</span>,
    credentials: <span class="kw">true</span>,
  });

  <span class="cmt">// Global prefix — tüm route'lar /api/... ile başlar</span>
  app.<span class="fn">setGlobalPrefix</span>(<span class="str">'api'</span>);

  <span class="kw">await</span> app.<span class="fn">listen</span>(<span class="num">3001</span>);
  console.<span class="fn">log</span>(<span class="str">'Uygulama çalışıyor: http://localhost:3001/api'</span>);
}

<span class="fn">bootstrap</span>();</pre>
    </div>

    <h3>NestJS Yaşam Döngüsü</h3>
    <p>Bir HTTP isteğinin NestJS'te izlediği yol:</p>

    <div class="code-wrap">
      <div class="code-title">request lifecycle (soldan sağa)</div>
      <pre>İstek geldi
  → Middleware (global → modül)
    → Guard (yetki kontrolü)
      → Interceptor (before)
        → Pipe (validasyon + transform)
          → Controller metodu
            → Service
          → Pipe
        → Interceptor (after)
      → Exception Filter (hata varsa)
  → Response</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 02 -->
  <section class="section" id="s02">
    <div class="section-label">
      <span class="sec-num">02</span>
      <span class="sec-badge badge-temel">Temel</span>
    </div>
    <h2>Controller — HTTP İsteklerini Karşılamak</h2>
    <p class="intro">
      Controller, gelen HTTP isteklerini karşılayan ve doğru servise yönlendiren katmandır.
      İş mantığı içermez — sadece routing ve request/response yönetimi yapar.
    </p>

    <h3>Temel Controller</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/users.controller.ts</div>
      <pre><span class="kw">import</span> {
  <span class="cls">Controller</span>, <span class="cls">Get</span>, <span class="cls">Post</span>, <span class="cls">Put</span>, <span class="cls">Delete</span>, <span class="cls">Patch</span>,
  <span class="cls">Body</span>, <span class="cls">Param</span>, <span class="cls">Query</span>, <span class="cls">Headers</span>,
  <span class="cls">HttpCode</span>, <span class="cls">HttpStatus</span>
} <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">UsersService</span> } <span class="kw">from</span> <span class="str">'./users.service'</span>;

<span class="dec">@Controller</span>(<span class="str">'users'</span>)  <span class="cmt">// → /api/users</span>
<span class="kw">export class</span> <span class="cls">UsersController</span> {
  <span class="kw">constructor</span>(<span class="kw">private readonly</span> usersService: <span class="cls">UsersService</span>) {}

  <span class="cmt">// GET /api/users</span>
  <span class="dec">@Get</span>()
  <span class="fn">findAll</span>() {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">findAll</span>();
  }

  <span class="cmt">// GET /api/users?page=1&limit=10</span>
  <span class="dec">@Get</span>(<span class="str">'search'</span>)
  <span class="fn">search</span>(
    <span class="dec">@Query</span>(<span class="str">'page'</span>) page: <span class="typ">number</span>,
    <span class="dec">@Query</span>(<span class="str">'limit'</span>) limit: <span class="typ">number</span>,
    <span class="dec">@Query</span>(<span class="str">'q'</span>) q: <span class="typ">string</span>,
  ) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">search</span>({ page, limit, q });
  }

  <span class="cmt">// GET /api/users/:id</span>
  <span class="dec">@Get</span>(<span class="str">':id'</span>)
  <span class="fn">findOne</span>(<span class="dec">@Param</span>(<span class="str">'id'</span>) id: <span class="typ">string</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">findOne</span>(<span class="op">+</span>id);
  }

  <span class="cmt">// POST /api/users — 201 döner</span>
  <span class="dec">@Post</span>()
  <span class="dec">@HttpCode</span>(<span class="cls">HttpStatus</span>.CREATED)
  <span class="fn">create</span>(<span class="dec">@Body</span>() createUserDto: <span class="cls">CreateUserDto</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">create</span>(createUserDto);
  }

  <span class="cmt">// PUT /api/users/:id — tüm alanları günceller</span>
  <span class="dec">@Put</span>(<span class="str">':id'</span>)
  <span class="fn">update</span>(
    <span class="dec">@Param</span>(<span class="str">'id'</span>) id: <span class="typ">string</span>,
    <span class="dec">@Body</span>() updateUserDto: <span class="cls">UpdateUserDto</span>,
  ) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">update</span>(<span class="op">+</span>id, updateUserDto);
  }

  <span class="cmt">// PATCH /api/users/:id — kısmi güncelleme</span>
  <span class="dec">@Patch</span>(<span class="str">':id'</span>)
  <span class="fn">partialUpdate</span>(
    <span class="dec">@Param</span>(<span class="str">'id'</span>) id: <span class="typ">string</span>,
    <span class="dec">@Body</span>() dto: <span class="kw">Partial</span><<span class="cls">UpdateUserDto</span>>,
  ) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">update</span>(<span class="op">+</span>id, dto);
  }

  <span class="cmt">// DELETE /api/users/:id — 204 döner (içerik yok)</span>
  <span class="dec">@Delete</span>(<span class="str">':id'</span>)
  <span class="dec">@HttpCode</span>(<span class="cls">HttpStatus</span>.NO_CONTENT)
  <span class="fn">remove</span>(<span class="dec">@Param</span>(<span class="str">'id'</span>) id: <span class="typ">string</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">remove</span>(<span class="op">+</span>id);
  }
}</pre>
    </div>

    <h3>Tüm HTTP Decorator'ları</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr><th>Decorator</th><th>HTTP Metodu</th><th>Kullanım</th></tr>
        </thead>
        <tbody>
          <tr><td><code>@Get()</code></td><td>GET</td><td>Veri okuma</td></tr>
          <tr><td><code>@Post()</code></td><td>POST</td><td>Kayıt oluşturma</td></tr>
          <tr><td><code>@Put()</code></td><td>PUT</td><td>Tam güncelleme (tüm alanlar)</td></tr>
          <tr><td><code>@Patch()</code></td><td>PATCH</td><td>Kısmi güncelleme</td></tr>
          <tr><td><code>@Delete()</code></td><td>DELETE</td><td>Silme</td></tr>
          <tr><td><code>@Head()</code></td><td>HEAD</td><td>Sadece header döner</td></tr>
          <tr><td><code>@Options()</code></td><td>OPTIONS</td><td>CORS preflight</td></tr>
          <tr><td><code>@All()</code></td><td>Hepsi</td><td>Tüm metodları yakalar</td></tr>
        </tbody>
      </table>
    </div>

    <h3>Parameter Decorator'ları</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr><th>Decorator</th><th>Karşılığı</th><th>Açıklama</th></tr>
        </thead>
        <tbody>
          <tr><td><code>@Param('id')</code></td><td>req.params.id</td><td>URL parametresi</td></tr>
          <tr><td><code>@Query('page')</code></td><td>req.query.page</td><td>Query string parametresi</td></tr>
          <tr><td><code>@Body()</code></td><td>req.body</td><td>Request body</td></tr>
          <tr><td><code>@Headers('auth')</code></td><td>req.headers.auth</td><td>Header değeri</td></tr>
          <tr><td><code>@Ip()</code></td><td>req.ip</td><td>Client IP adresi</td></tr>
          <tr><td><code>@HostParam()</code></td><td>req.hosts</td><td>Host parametresi</td></tr>
        </tbody>
      </table>
    </div>

    <h3>Route Parametresi ile Çalışma</h3>
    <div class="code-wrap">
      <div class="code-title">nested route örneği</div>
      <pre><span class="cmt">// GET /users/:userId/posts/:postId</span>
<span class="dec">@Get</span>(<span class="str">':userId/posts/:postId'</span>)
<span class="fn">getUserPost</span>(
  <span class="dec">@Param</span>(<span class="str">'userId'</span>) userId: <span class="typ">string</span>,
  <span class="dec">@Param</span>(<span class="str">'postId'</span>) postId: <span class="typ">string</span>,
) {
  <span class="kw">return</span> <span class="kw">this</span>.service.<span class="fn">getUserPost</span>(<span class="op">+</span>userId, <span class="op">+</span>postId);
}

<span class="cmt">// Tüm param'ları obje olarak al</span>
<span class="dec">@Get</span>(<span class="str">':category/:slug'</span>)
<span class="fn">findBySlug</span>(<span class="dec">@Param</span>() params: { category: <span class="typ">string</span>; slug: <span class="typ">string</span> }) {
  <span class="kw">return</span> params;
}</pre>
    </div>

    <div class="callout warn">
      <strong>İpucu:</strong> Controller'da asla veritabanı işlemi veya iş mantığı yazma.
      Tüm mantık Service katmanında olmalı. Controller sadece routing ve DTO aktarımı yapar.
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 03 -->
  <section class="section" id="s03">
    <div class="section-label">
      <span class="sec-num">03</span>
      <span class="sec-badge badge-temel">Temel</span>
    </div>
    <h2>Service &amp; Dependency Injection</h2>
    <p class="intro">
      Service, uygulamanın iş mantığını barındıran katmandır. NestJS'in Dependency Injection (DI) sistemi
      sayesinde sınıflar arası bağımlılıklar framework tarafından otomatik çözümlenir.
      Bu pattern kod test edilebilirliğini ve modülerliği büyük ölçüde artırır.
    </p>

    <h3>Service Oluşturma</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>nest generate service users
<span class="cmt"># kısa: nest g s users</span></pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/users/users.service.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Injectable</span>, <span class="cls">NotFoundException</span>, <span class="cls">ConflictException</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">InjectRepository</span> } <span class="kw">from</span> <span class="str">'@nestjs/typeorm'</span>;
<span class="kw">import</span> { <span class="cls">Repository</span> } <span class="kw">from</span> <span class="str">'typeorm'</span>;
<span class="kw">import</span> { <span class="cls">User</span> } <span class="kw">from</span> <span class="str">'./entities/user.entity'</span>;

<span class="dec">@Injectable</span>()  <span class="cmt">// DI container'a kaydeder</span>
<span class="kw">export class</span> <span class="cls">UsersService</span> {

  <span class="kw">constructor</span>(
    <span class="dec">@InjectRepository</span>(<span class="cls">User</span>)
    <span class="kw">private</span> usersRepo: <span class="cls">Repository</span><<span class="cls">User</span>>,
  ) {}

  <span class="kw">async</span> <span class="fn">findAll</span>(): <span class="cls">Promise</span><<span class="cls">User</span>[]> {
    <span class="kw">return</span> <span class="kw">this</span>.usersRepo.<span class="fn">find</span>();
  }

  <span class="kw">async</span> <span class="fn">findOne</span>(id: <span class="typ">number</span>): <span class="cls">Promise</span><<span class="cls">User</span>> {
    <span class="kw">const</span> user = <span class="kw">await</span> <span class="kw">this</span>.usersRepo.<span class="fn">findOneBy</span>({ id });
    <span class="kw">if</span> (!user) {
      <span class="cmt">// NestJS otomatik 404 döner</span>
      <span class="kw">throw new</span> <span class="cls">NotFoundException</span>(<span class="str">`Kullanıcı #${id} bulunamadı`</span>);
    }
    <span class="kw">return</span> user;
  }

  <span class="kw">async</span> <span class="fn">create</span>(dto: <span class="cls">CreateUserDto</span>): <span class="cls">Promise</span><<span class="cls">User</span>> {
    <span class="kw">const</span> existing = <span class="kw">await</span> <span class="kw">this</span>.usersRepo.<span class="fn">findOneBy</span>({ email: dto.email });
    <span class="kw">if</span> (existing) {
      <span class="kw">throw new</span> <span class="cls">ConflictException</span>(<span class="str">'Bu e-posta zaten kayıtlı'</span>);
    }
    <span class="kw">const</span> user = <span class="kw">this</span>.usersRepo.<span class="fn">create</span>(dto);
    <span class="kw">return</span> <span class="kw">this</span>.usersRepo.<span class="fn">save</span>(user);
  }

  <span class="kw">async</span> <span class="fn">update</span>(id: <span class="typ">number</span>, dto: <span class="kw">Partial</span><<span class="cls">UpdateUserDto</span>>): <span class="cls">Promise</span><<span class="cls">User</span>> {
    <span class="kw">const</span> user = <span class="kw">await</span> <span class="kw">this</span>.<span class="fn">findOne</span>(id);  <span class="cmt">// 404 fırlatır</span>
    <span class="cls">Object</span>.<span class="fn">assign</span>(user, dto);
    <span class="kw">return</span> <span class="kw">this</span>.usersRepo.<span class="fn">save</span>(user);
  }

  <span class="kw">async</span> <span class="fn">remove</span>(id: <span class="typ">number</span>): <span class="cls">Promise</span><<span class="kw">void</span>> {
    <span class="kw">const</span> user = <span class="kw">await</span> <span class="kw">this</span>.<span class="fn">findOne</span>(id);
    <span class="kw">await</span> <span class="kw">this</span>.usersRepo.<span class="fn">remove</span>(user);
  }
}</pre>
    </div>

    <h3>Dependency Injection Derinlemesine</h3>
    <p>NestJS'in DI sistemi üç temel injection scope'u destekler:</p>

    <div class="code-wrap">
      <div class="code-title">injection scope seçenekleri</div>
      <pre><span class="kw">import</span> { <span class="cls">Injectable</span>, <span class="cls">Scope</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="cmt">// DEFAULT — uygulama boyunca tek instance (singleton)</span>
<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">SingletonService</span> {}

<span class="cmt">// REQUEST — her HTTP isteğinde yeni instance</span>
<span class="dec">@Injectable</span>({ scope: <span class="cls">Scope</span>.REQUEST })
<span class="kw">export class</span> <span class="cls">RequestScopedService</span> {}

<span class="cmt">// TRANSIENT — inject edildiği her yerde yeni instance</span>
<span class="dec">@Injectable</span>({ scope: <span class="cls">Scope</span>.TRANSIENT })
<span class="kw">export class</span> <span class="cls">TransientService</span> {}</pre>
    </div>

    <h3>Servisleri Birbirine Inject Etmek</h3>
    <div class="code-wrap">
      <div class="code-title">cross-service injection</div>
      <pre><span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">OrdersService</span> {
  <span class="kw">constructor</span>(
    <span class="kw">private</span> usersService: <span class="cls">UsersService</span>,    <span class="cmt">// UsersModule export etmeli</span>
    <span class="kw">private</span> mailService: <span class="cls">MailService</span>,      <span class="cmt">// MailModule export etmeli</span>
    <span class="kw">private</span> paymentService: <span class="cls">PaymentService</span>, <span class="cmt">// PaymentModule export etmeli</span>
  ) {}

  <span class="kw">async</span> <span class="fn">createOrder</span>(userId: <span class="typ">number</span>, dto: <span class="cls">CreateOrderDto</span>) {
    <span class="kw">const</span> user = <span class="kw">await</span> <span class="kw">this</span>.usersService.<span class="fn">findOne</span>(userId);
    <span class="kw">const</span> order = <span class="kw">await</span> <span class="kw">this</span>.ordersRepo.<span class="fn">save</span>(dto);
    <span class="kw">await</span> <span class="kw">this</span>.mailService.<span class="fn">sendOrderConfirmation</span>(user.email, order);
    <span class="kw">return</span> order;
  }
}</pre>
    </div>

    <div class="callout ok">
      <strong>Best Practice:</strong> Constructor injection kullan (property injection değil).
      Test ederken mock service'i constructor'dan kolayca geçirebilirsin.
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 04 -->
  <section class="section" id="s04">
    <div class="section-label">
      <span class="sec-num">04</span>
      <span class="sec-badge badge-temel">Temel</span>
    </div>
    <h2>Module Sistemi</h2>
    <p class="intro">
      Her NestJS uygulaması modüller ağacından oluşur. Modüller, birbirine ait controller, service ve
      provider'ları paketler. Doğru modülleme, uygulamanın büyüdükçe yönetilebilir kalmasını sağlar.
    </p>

    <h3>Temel Modül Anatomisi</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/users.module.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Module</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">TypeOrmModule</span> } <span class="kw">from</span> <span class="str">'@nestjs/typeorm'</span>;
<span class="kw">import</span> { <span class="cls">UsersController</span> } <span class="kw">from</span> <span class="str">'./users.controller'</span>;
<span class="kw">import</span> { <span class="cls">UsersService</span> } <span class="kw">from</span> <span class="str">'./users.service'</span>;
<span class="kw">import</span> { <span class="cls">User</span> } <span class="kw">from</span> <span class="str">'./entities/user.entity'</span>;

<span class="dec">@Module</span>({
  imports: [
    <span class="cls">TypeOrmModule</span>.<span class="fn">forFeature</span>([<span class="cls">User</span>]),  <span class="cmt">// User entity'yi bu modüle bağla</span>
  ],
  controllers: [<span class="cls">UsersController</span>],       <span class="cmt">// HTTP isteklerini karşıla</span>
  providers: [<span class="cls">UsersService</span>],             <span class="cmt">// DI container'a kaydet</span>
  exports: [<span class="cls">UsersService</span>],               <span class="cmt">// başka modüller inject edebilir</span>
})
<span class="kw">export class</span> <span class="cls">UsersModule</span> {}</pre>
    </div>

    <h3>AppModule — Kök Modül</h3>
    <div class="code-wrap">
      <div class="code-title">src/app.module.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Module</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">ConfigModule</span>, <span class="cls">ConfigService</span> } <span class="kw">from</span> <span class="str">'@nestjs/config'</span>;
<span class="kw">import</span> { <span class="cls">TypeOrmModule</span> } <span class="kw">from</span> <span class="str">'@nestjs/typeorm'</span>;
<span class="kw">import</span> { <span class="cls">UsersModule</span> } <span class="kw">from</span> <span class="str">'./users/users.module'</span>;
<span class="kw">import</span> { <span class="cls">AuthModule</span> } <span class="kw">from</span> <span class="str">'./auth/auth.module'</span>;

<span class="dec">@Module</span>({
  imports: [
    <span class="cls">ConfigModule</span>.<span class="fn">forRoot</span>({ isGlobal: <span class="kw">true</span> }),  <span class="cmt">// .env her yerde erişilir</span>
    <span class="cls">TypeOrmModule</span>.<span class="fn">forRootAsync</span>({
      useFactory: (config: <span class="cls">ConfigService</span>) => ({
        type: <span class="str">'postgres'</span>,
        host: config.<span class="fn">get</span>(<span class="str">'DB_HOST'</span>),
        port: config.<span class="fn">get</span><<span class="typ">number</span>>(<span class="str">'DB_PORT'</span>),
        username: config.<span class="fn">get</span>(<span class="str">'DB_USER'</span>),
        password: config.<span class="fn">get</span>(<span class="str">'DB_PASS'</span>),
        database: config.<span class="fn">get</span>(<span class="str">'DB_NAME'</span>),
        autoLoadEntities: <span class="kw">true</span>,
        synchronize: <span class="kw">true</span>,  <span class="cmt">// sadece dev'de!</span>
      }),
      inject: [<span class="cls">ConfigService</span>],
    }),
    <span class="cls">UsersModule</span>,
    <span class="cls">AuthModule</span>,
  ],
})
<span class="kw">export class</span> <span class="cls">AppModule</span> {}</pre>
    </div>

    <h3>Global Modüller</h3>
    <div class="code-wrap">
      <div class="code-title">global module tanımı</div>
      <pre><span class="kw">import</span> { <span class="cls">Global</span>, <span class="cls">Module</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="cmt">// @Global ile işaretlenmiş modüller her yerde import edilmeden kullanılabilir</span>
<span class="dec">@Global</span>()
<span class="dec">@Module</span>({
  providers: [<span class="cls">DatabaseService</span>, <span class="cls">LoggerService</span>],
  exports: [<span class="cls">DatabaseService</span>, <span class="cls">LoggerService</span>],
})
<span class="kw">export class</span> <span class="cls">CoreModule</span> {}</pre>
    </div>

    <div class="callout warn">
      <strong>Dikkat:</strong> Global modülü sadece gerçekten her yerde lazım olan şeyler için kullan
      (Logger, Config, Database). Aşırı kullanım bağımlılıkları gizler ve kodu test edilmez hale getirir.
    </div>

    <h3>Dynamic Module</h3>
    <div class="code-wrap">
      <div class="code-title">yapılandırılabilir modül örneği</div>
      <pre><span class="dec">@Module</span>({})
<span class="kw">export class</span> <span class="cls">MailModule</span> {
  <span class="kw">static</span> <span class="fn">forRoot</span>(options: <span class="cls">MailOptions</span>): <span class="cls">DynamicModule</span> {
    <span class="kw">return</span> {
      module: <span class="cls">MailModule</span>,
      providers: [
        { provide: <span class="str">'MAIL_OPTIONS'</span>, useValue: options },
        <span class="cls">MailService</span>,
      ],
      exports: [<span class="cls">MailService</span>],
    };
  }
}

<span class="cmt">// Kullanımı AppModule'de:</span>
<span class="cls">MailModule</span>.<span class="fn">forRoot</span>({ host: <span class="str">'smtp.gmail.com'</span>, port: <span class="num">587</span> })</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 05 -->
  <section class="section" id="s05">
    <div class="section-label">
      <span class="sec-num">05</span>
      <span class="sec-badge badge-orta">Orta</span>
    </div>
    <h2>DTO, Validation &amp; Pipes</h2>
    <p class="intro">
      DTO (Data Transfer Object), bir endpoint'e gelen verinin şeklini tanımlayan sınıftır.
      class-validator paketi ile DTO alanlarına kural koyar, class-transformer ile tip dönüşümü yaparsın.
      Pipe'lar bu işlemleri otomatik uygular.
    </p>

    <h3>Kurulum</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install class-validator class-transformer</pre>
    </div>

    <h3>DTO Tanımlama</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/dto/create-user.dto.ts</div>
      <pre><span class="kw">import</span> {
  IsString, IsEmail, IsInt, IsOptional, IsEnum,
  MinLength, MaxLength, Min, Max, IsUrl, Matches,
  IsArray, ArrayMinSize, ValidateNested,
} <span class="kw">from</span> <span class="str">'class-validator'</span>;
<span class="kw">import</span> { <span class="cls">Type</span> } <span class="kw">from</span> <span class="str">'class-transformer'</span>;

<span class="kw">export enum</span> <span class="cls">UserRole</span> {
  ADMIN = <span class="str">'admin'</span>,
  USER = <span class="str">'user'</span>,
  MODERATOR = <span class="str">'moderator'</span>,
}

<span class="kw">export class</span> <span class="cls">AddressDto</span> {
  <span class="dec">@IsString</span>()
  street: <span class="typ">string</span>;

  <span class="dec">@IsString</span>()
  city: <span class="typ">string</span>;
}

<span class="kw">export class</span> <span class="cls">CreateUserDto</span> {
  <span class="dec">@IsString</span>()
  <span class="dec">@MinLength</span>(<span class="num">2</span>, { message: <span class="str">'Ad en az 2 karakter olmalı'</span> })
  <span class="dec">@MaxLength</span>(<span class="num">50</span>)
  name: <span class="typ">string</span>;

  <span class="dec">@IsEmail</span>({}, { message: <span class="str">'Geçerli bir e-posta gir'</span> })
  email: <span class="typ">string</span>;

  <span class="dec">@IsString</span>()
  <span class="dec">@MinLength</span>(<span class="num">8</span>)
  <span class="dec">@Matches</span>(<span class="str">/^(?=.*[A-Z])(?=.*[0-9]).+$/</span>, {
    message: <span class="str">'Şifre en az bir büyük harf ve rakam içermeli'</span>,
  })
  password: <span class="typ">string</span>;

  <span class="dec">@IsInt</span>()
  <span class="dec">@Min</span>(<span class="num">18</span>)
  <span class="dec">@Max</span>(<span class="num">120</span>)
  <span class="dec">@Type</span>(() => <span class="cls">Number</span>)  <span class="cmt">// string'i sayıya çevir</span>
  age: <span class="typ">number</span>;

  <span class="dec">@IsEnum</span>(<span class="cls">UserRole</span>)
  role: <span class="cls">UserRole</span>;

  <span class="dec">@IsOptional</span>()       <span class="cmt">// gönderilmeyebilir</span>
  <span class="dec">@IsUrl</span>()
  avatarUrl?: <span class="typ">string</span>;

  <span class="cmt">// Nested DTO array</span>
  <span class="dec">@IsArray</span>()
  <span class="dec">@ArrayMinSize</span>(<span class="num">1</span>)
  <span class="dec">@ValidateNested</span>({ each: <span class="kw">true</span> })
  <span class="dec">@Type</span>(() => <span class="cls">AddressDto</span>)
  addresses: <span class="cls">AddressDto</span>[];
}</pre>
    </div>

    <h3>PartialType ile Update DTO</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/dto/update-user.dto.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">PartialType</span>, <span class="cls">OmitType</span>, <span class="cls">PickType</span> } <span class="kw">from</span> <span class="str">'@nestjs/mapped-types'</span>;

<span class="cmt">// Tüm alanları opsiyonel yapar — kopyala yapıştır gerekmez</span>
<span class="kw">export class</span> <span class="cls">UpdateUserDto</span> <span class="kw">extends</span> <span class="cls">PartialType</span>(<span class="cls">CreateUserDto</span>) {}

<span class="cmt">// Belirli alanları çıkar</span>
<span class="kw">export class</span> <span class="cls">UserProfileDto</span> <span class="kw">extends</span> <span class="cls">OmitType</span>(<span class="cls">CreateUserDto</span>, [<span class="str">'password'</span>] <span class="kw">as const</span>) {}

<span class="cmt">// Sadece belirli alanları al</span>
<span class="kw">export class</span> <span class="cls">LoginDto</span> <span class="kw">extends</span> <span class="cls">PickType</span>(<span class="cls">CreateUserDto</span>, [<span class="str">'email'</span>, <span class="str">'password'</span>] <span class="kw">as const</span>) {}</pre>
    </div>

    <h3>Custom Pipe</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/pipes/parse-positive-int.pipe.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">PipeTransform</span>, <span class="cls">Injectable</span>, <span class="cls">BadRequestException</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">ParsePositiveIntPipe</span> <span class="kw">implements</span> <span class="cls">PipeTransform</span> {
  <span class="fn">transform</span>(value: <span class="typ">any</span>) {
    <span class="kw">const</span> num = parseInt(value, <span class="num">10</span>);
    <span class="kw">if</span> (isNaN(num) || num <= <span class="num">0</span>) {
      <span class="kw">throw new</span> <span class="cls">BadRequestException</span>(<span class="str">`'${value}' pozitif tam sayı olmalı`</span>);
    }
    <span class="kw">return</span> num;
  }
}

<span class="cmt">// Kullanımı:</span>
<span class="dec">@Get</span>(<span class="str">':id'</span>)
<span class="fn">findOne</span>(<span class="dec">@Param</span>(<span class="str">'id'</span>, <span class="cls">ParsePositiveIntPipe</span>) id: <span class="typ">number</span>) {}</pre>
    </div>

    <h3>Built-in Pipe'lar</h3>
    <div class="table-wrap">
      <table>
        <thead><tr><th>Pipe</th><th>Görevi</th></tr></thead>
        <tbody>
          <tr><td><code>ValidationPipe</code></td><td>DTO'yu class-validator ile doğrular</td></tr>
          <tr><td><code>ParseIntPipe</code></td><td>string → number dönüşümü</td></tr>
          <tr><td><code>ParseFloatPipe</code></td><td>string → float dönüşümü</td></tr>
          <tr><td><code>ParseBoolPipe</code></td><td>string → boolean dönüşümü</td></tr>
          <tr><td><code>ParseUUIDPipe</code></td><td>UUID formatını doğrular</td></tr>
          <tr><td><code>ParseArrayPipe</code></td><td>virgülle ayrılmış string → array</td></tr>
          <tr><td><code>DefaultValuePipe</code></td><td>undefined ise varsayılan değer atar</td></tr>
        </tbody>
      </table>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 06 -->
  <section class="section" id="s06">
    <div class="section-label">
      <span class="sec-num">06</span>
      <span class="sec-badge badge-orta">Orta</span>
    </div>
    <h2>TypeORM &amp; Veritabanı</h2>
    <p class="intro">
      NestJS'in resmi ORM desteği TypeORM üzerinedir. Entity'ler, ilişkiler, migration'lar ve
      QueryBuilder kullanımını öğrenerek production-grade veritabanı katmanı oluşturabilirsin.
    </p>

    <h3>Kurulum</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install @nestjs/typeorm typeorm pg
<span class="cmt"># pg = PostgreSQL driver. MySQL için: npm install mysql2</span></pre>
    </div>

    <h3>Entity Tanımlama</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/entities/user.entity.ts</div>
      <pre><span class="kw">import</span> {
  Entity, PrimaryGeneratedColumn, Column, CreateDateColumn,
  UpdateDateColumn, OneToMany, ManyToOne, BeforeInsert, Index,
} <span class="kw">from</span> <span class="str">'typeorm'</span>;
<span class="kw">import</span> * <span class="kw">as</span> bcrypt <span class="kw">from</span> <span class="str">'bcrypt'</span>;

<span class="dec">@Entity</span>(<span class="str">'users'</span>)
<span class="dec">@Index</span>([<span class="str">'email'</span>], { unique: <span class="kw">true</span> })  <span class="cmt">// DB seviyesinde unique index</span>
<span class="kw">export class</span> <span class="cls">User</span> {
  <span class="dec">@PrimaryGeneratedColumn</span>()
  id: <span class="typ">number</span>;

  <span class="dec">@Column</span>({ length: <span class="num">50</span> })
  name: <span class="typ">string</span>;

  <span class="dec">@Column</span>({ unique: <span class="kw">true</span> })
  email: <span class="typ">string</span>;

  <span class="dec">@Column</span>({ select: <span class="kw">false</span> })  <span class="cmt">// findAll'da şifre gelmez</span>
  password: <span class="typ">string</span>;

  <span class="dec">@Column</span>({
    type: <span class="str">'enum'</span>,
    enum: [<span class="str">'admin'</span>, <span class="str">'user'</span>, <span class="str">'moderator'</span>],
    default: <span class="str">'user'</span>,
  })
  role: <span class="typ">string</span>;

  <span class="dec">@Column</span>({ default: <span class="kw">true</span> })
  isActive: <span class="typ">boolean</span>;

  <span class="dec">@CreateDateColumn</span>()  <span class="cmt">// INSERT'te otomatik set edilir</span>
  createdAt: <span class="cls">Date</span>;

  <span class="dec">@UpdateDateColumn</span>()  <span class="cmt">// UPDATE'te otomatik güncellenir</span>
  updatedAt: <span class="cls">Date</span>;

  <span class="cmt">// İlişki: bir user'ın birden fazla post'u olabilir</span>
  <span class="dec">@OneToMany</span>(() => <span class="cls">Post</span>, (post) => post.author)
  posts: <span class="cls">Post</span>[];

  <span class="cmt">// INSERT'ten önce şifreyi hashle</span>
  <span class="dec">@BeforeInsert</span>()
  <span class="kw">async</span> <span class="fn">hashPassword</span>() {
    <span class="kw">if</span> (<span class="kw">this</span>.password) {
      <span class="kw">this</span>.password = <span class="kw">await</span> bcrypt.<span class="fn">hash</span>(<span class="kw">this</span>.password, <span class="num">12</span>);
    }
  }
}</pre>
    </div>

    <h3>İlişkiler (Relations)</h3>
    <div class="code-wrap">
      <div class="code-title">src/posts/entities/post.entity.ts — ilişki tanımı</div>
      <pre><span class="dec">@Entity</span>(<span class="str">'posts'</span>)
<span class="kw">export class</span> <span class="cls">Post</span> {
  <span class="dec">@PrimaryGeneratedColumn</span>()
  id: <span class="typ">number</span>;

  <span class="dec">@Column</span>()
  title: <span class="typ">string</span>;

  <span class="cmt">// ManyToOne: bir post tek bir user'a ait</span>
  <span class="dec">@ManyToOne</span>(() => <span class="cls">User</span>, (user) => user.posts, { onDelete: <span class="str">'CASCADE'</span> })
  author: <span class="cls">User</span>;

  <span class="dec">@Column</span>()
  authorId: <span class="typ">number</span>;

  <span class="cmt">// ManyToMany: bir post birden fazla tag'e sahip olabilir</span>
  <span class="dec">@ManyToMany</span>(() => <span class="cls">Tag</span>, (tag) => tag.posts)
  <span class="dec">@JoinTable</span>()   <span class="cmt">// ara tablo buraya eklenir</span>
  tags: <span class="cls">Tag</span>[];
}</pre>
    </div>

    <h3>Repository ile CRUD</h3>
    <div class="code-wrap">
      <div class="code-title">repository metodları</div>
      <pre><span class="cmt">// Basit sorgu</span>
<span class="kw">const</span> users = <span class="kw">await</span> <span class="kw">this</span>.repo.<span class="fn">find</span>({
  where: { isActive: <span class="kw">true</span> },
  order: { createdAt: <span class="str">'DESC'</span> },
  take: <span class="num">10</span>,
  skip: <span class="num">0</span>,
  relations: [<span class="str">'posts'</span>],   <span class="cmt">// JOIN ile ilişkili kayıtları getir</span>
});

<span class="cmt">// Sayfalama yardımcısı</span>
<span class="kw">const</span> [items, total] = <span class="kw">await</span> <span class="kw">this</span>.repo.<span class="fn">findAndCount</span>({
  take: limit,
  skip: (page - <span class="num">1</span>) * limit,
});

<span class="cmt">// QueryBuilder — karmaşık sorgular için</span>
<span class="kw">const</span> result = <span class="kw">await</span> <span class="kw">this</span>.repo
  .<span class="fn">createQueryBuilder</span>(<span class="str">'u'</span>)
  .<span class="fn">leftJoinAndSelect</span>(<span class="str">'u.posts'</span>, <span class="str">'p'</span>)
  .<span class="fn">where</span>(<span class="str">'u.role = :role'</span>, { role: <span class="str">'admin'</span> })
  .<span class="fn">andWhere</span>(<span class="str">'p.createdAt > :date'</span>, { date: <span class="kw">new</span> <span class="cls">Date</span>(<span class="str">'2024-01-01'</span>) })
  .<span class="fn">orderBy</span>(<span class="str">'u.name'</span>, <span class="str">'ASC'</span>)
  .<span class="fn">getMany</span>();</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 07 -->
  <section class="section" id="s07">
    <div class="section-label">
      <span class="sec-num">07</span>
      <span class="sec-badge badge-orta">Orta</span>
    </div>
    <h2>Authentication — JWT</h2>
    <p class="intro">
      JWT tabanlı kimlik doğrulaması NestJS'te Passport.js stratejileri üzerinden yapılır.
      Access token + Refresh token mimarisini kurarak güvenli authentication sistemi oluşturacağız.
    </p>

    <h3>Kurulum</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install @nestjs/passport @nestjs/jwt passport passport-jwt bcrypt
npm install -D @types/passport-jwt @types/bcrypt</pre>
    </div>

    <h3>JWT Strategy</h3>
    <div class="code-wrap">
      <div class="code-title">src/auth/strategies/jwt.strategy.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Injectable</span>, <span class="cls">UnauthorizedException</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">PassportStrategy</span> } <span class="kw">from</span> <span class="str">'@nestjs/passport'</span>;
<span class="kw">import</span> { <span class="cls">ExtractJwt</span>, <span class="cls">Strategy</span> } <span class="kw">from</span> <span class="str">'passport-jwt'</span>;
<span class="kw">import</span> { <span class="cls">ConfigService</span> } <span class="kw">from</span> <span class="str">'@nestjs/config'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">JwtStrategy</span> <span class="kw">extends</span> <span class="cls">PassportStrategy</span>(<span class="cls">Strategy</span>) {
  <span class="kw">constructor</span>(
    <span class="kw">private</span> config: <span class="cls">ConfigService</span>,
    <span class="kw">private</span> usersService: <span class="cls">UsersService</span>,
  ) {
    <span class="fn">super</span>({
      jwtFromRequest: <span class="cls">ExtractJwt</span>.<span class="fn">fromAuthHeaderAsBearerToken</span>(),
      secretOrKey: config.<span class="fn">get</span>(<span class="str">'JWT_SECRET'</span>),
      ignoreExpiration: <span class="kw">false</span>,
    });
  }

  <span class="cmt">// Token geçerliyse bu metod çalışır, dönen değer req.user olur</span>
  <span class="kw">async</span> <span class="fn">validate</span>(payload: { sub: <span class="typ">number</span>; email: <span class="typ">string</span> }) {
    <span class="kw">const</span> user = <span class="kw">await</span> <span class="kw">this</span>.usersService.<span class="fn">findOne</span>(payload.sub);
    <span class="kw">if</span> (!user || !user.isActive) {
      <span class="kw">throw new</span> <span class="cls">UnauthorizedException</span>();
    }
    <span class="kw">return</span> user;  <span class="cmt">// → req.user</span>
  }
}</pre>
    </div>

    <h3>Auth Service</h3>
    <div class="code-wrap">
      <div class="code-title">src/auth/auth.service.ts</div>
      <pre><span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">AuthService</span> {
  <span class="kw">constructor</span>(
    <span class="kw">private</span> usersService: <span class="cls">UsersService</span>,
    <span class="kw">private</span> jwtService: <span class="cls">JwtService</span>,
  ) {}

  <span class="kw">async</span> <span class="fn">login</span>(dto: <span class="cls">LoginDto</span>) {
    <span class="kw">const</span> user = <span class="kw">await</span> <span class="kw">this</span>.usersService.<span class="fn">findByEmail</span>(dto.email);
    <span class="kw">if</span> (!user) <span class="kw">throw new</span> <span class="cls">UnauthorizedException</span>(<span class="str">'Kullanıcı bulunamadı'</span>);

    <span class="kw">const</span> ok = <span class="kw">await</span> bcrypt.<span class="fn">compare</span>(dto.password, user.password);
    <span class="kw">if</span> (!ok) <span class="kw">throw new</span> <span class="cls">UnauthorizedException</span>(<span class="str">'Şifre yanlış'</span>);

    <span class="kw">return</span> {
      accessToken: <span class="kw">await</span> <span class="kw">this</span>.<span class="fn">generateAccessToken</span>(user),
      refreshToken: <span class="kw">await</span> <span class="kw">this</span>.<span class="fn">generateRefreshToken</span>(user),
    };
  }

  <span class="kw">private async</span> <span class="fn">generateAccessToken</span>(user: <span class="cls">User</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.jwtService.<span class="fn">signAsync</span>(
      { sub: user.id, email: user.email, role: user.role },
      { secret: <span class="kw">this</span>.config.<span class="fn">get</span>(<span class="str">'JWT_SECRET'</span>), expiresIn: <span class="str">'15m'</span> },
    );
  }

  <span class="kw">private async</span> <span class="fn">generateRefreshToken</span>(user: <span class="cls">User</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.jwtService.<span class="fn">signAsync</span>(
      { sub: user.id },
      { secret: <span class="kw">this</span>.config.<span class="fn">get</span>(<span class="str">'JWT_REFRESH_SECRET'</span>), expiresIn: <span class="str">'7d'</span> },
    );
  }
}</pre>
    </div>

    <h3>Auth Guard</h3>
    <div class="code-wrap">
      <div class="code-title">src/auth/guards/jwt-auth.guard.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Injectable</span>, <span class="cls">ExecutionContext</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">AuthGuard</span> } <span class="kw">from</span> <span class="str">'@nestjs/passport'</span>;
<span class="kw">import</span> { <span class="cls">Reflector</span> } <span class="kw">from</span> <span class="str">'@nestjs/core'</span>;
<span class="kw">import</span> { <span class="cls">IS_PUBLIC_KEY</span> } <span class="kw">from</span> <span class="str">'../decorators/public.decorator'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">JwtAuthGuard</span> <span class="kw">extends</span> <span class="cls">AuthGuard</span>(<span class="str">'jwt'</span>) {
  <span class="kw">constructor</span>(<span class="kw">private</span> reflector: <span class="cls">Reflector</span>) { <span class="fn">super</span>(); }

  <span class="fn">canActivate</span>(ctx: <span class="cls">ExecutionContext</span>) {
    <span class="cmt">// @Public() ile işaretlenen route'ları atla</span>
    <span class="kw">const</span> isPublic = <span class="kw">this</span>.reflector.<span class="fn">getAllAndOverride</span><<span class="typ">boolean</span>>(<span class="cls">IS_PUBLIC_KEY</span>, [
      ctx.<span class="fn">getHandler</span>(),
      ctx.<span class="fn">getClass</span>(),
    ]);
    <span class="kw">if</span> (isPublic) <span class="kw">return true</span>;
    <span class="kw">return super</span>.<span class="fn">canActivate</span>(ctx);
  }
}

<span class="cmt">// Public decorator tanımı</span>
<span class="kw">export const</span> <span class="cls">IS_PUBLIC_KEY</span> = <span class="str">'isPublic'</span>;
<span class="kw">export const</span> <span class="cls">Public</span> = () => <span class="fn">SetMetadata</span>(<span class="cls">IS_PUBLIC_KEY</span>, <span class="kw">true</span>);

<span class="cmt">// Kullanımı:</span>
<span class="dec">@Public</span>()
<span class="dec">@Post</span>(<span class="str">'login'</span>)
<span class="fn">login</span>(<span class="dec">@Body</span>() dto: <span class="cls">LoginDto</span>) {}</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 08 -->
  <section class="section" id="s08">
    <div class="section-label">
      <span class="sec-num">08</span>
      <span class="sec-badge badge-orta">Orta</span>
    </div>
    <h2>Config &amp; Environment</h2>
    <p class="intro">
      @nestjs/config paketi ile .env dosyaları, tip güvenli konfigürasyon nesneleri ve
      ortama göre farklı ayarlar yönetilir.
    </p>

    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install @nestjs/config</pre>
    </div>

    <h3>registerAs ile Namespace Konfigürasyon</h3>
    <div class="code-wrap">
      <div class="code-title">src/config/database.config.ts</div>
      <pre><span class="kw">import</span> { <span class="fn">registerAs</span> } <span class="kw">from</span> <span class="str">'@nestjs/config'</span>;

<span class="kw">export default</span> <span class="fn">registerAs</span>(<span class="str">'database'</span>, () => ({
  host: process.env.DB_HOST || <span class="str">'localhost'</span>,
  port: parseInt(process.env.DB_PORT, <span class="num">10</span>) || <span class="num">5432</span>,
  username: process.env.DB_USER,
  password: process.env.DB_PASS,
  database: process.env.DB_NAME,
}));</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/config/app.config.ts</div>
      <pre><span class="kw">export default</span> <span class="fn">registerAs</span>(<span class="str">'app'</span>, () => ({
  port: parseInt(process.env.PORT, <span class="num">10</span>) || <span class="num">3001</span>,
  jwtSecret: process.env.JWT_SECRET,
  jwtExpiry: process.env.JWT_EXPIRY || <span class="str">'15m'</span>,
  nodeEnv: process.env.NODE_ENV || <span class="str">'development'</span>,
  isDev: process.env.NODE_ENV !== <span class="str">'production'</span>,
}));</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/app.module.ts — config yükleme</div>
      <pre><span class="cls">ConfigModule</span>.<span class="fn">forRoot</span>({
  isGlobal: <span class="kw">true</span>,                   <span class="cmt">// her modülde import gerekmez</span>
  envFilePath: [<span class="str">'.env.local'</span>, <span class="str">'.env'</span>],  <span class="cmt">// .env.local önce okunur</span>
  load: [databaseConfig, appConfig],   <span class="cmt">// namespace config'ler</span>
  validationSchema: Joi.<span class="fn">object</span>({      <span class="cmt">// Joi ile .env doğrulama</span>
    NODE_ENV: Joi.<span class="fn">string</span>().<span class="fn">valid</span>(<span class="str">'development'</span>, <span class="str">'production'</span>),
    DB_HOST: Joi.<span class="fn">string</span>().<span class="fn">required</span>(),
    JWT_SECRET: Joi.<span class="fn">string</span>().<span class="fn">min</span>(<span class="num">32</span>).<span class="fn">required</span>(),
  }),
})</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">servis içinde konfigürasyon okuma</div>
      <pre><span class="kw">import</span> { <span class="cls">ConfigService</span> } <span class="kw">from</span> <span class="str">'@nestjs/config'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">AppService</span> {
  <span class="kw">constructor</span>(<span class="kw">private</span> config: <span class="cls">ConfigService</span>) {}

  <span class="fn">someMethod</span>() {
    <span class="cmt">// Düz okuma</span>
    <span class="kw">const</span> host = <span class="kw">this</span>.config.<span class="fn">get</span>(<span class="str">'database.host'</span>);

    <span class="cmt">// Tip güvenli okuma</span>
    <span class="kw">const</span> port = <span class="kw">this</span>.config.<span class="fn">get</span><<span class="typ">number</span>>(<span class="str">'database.port'</span>);

    <span class="cmt">// Yoksa hata fırlat</span>
    <span class="kw">const</span> secret = <span class="kw">this</span>.config.<span class="fn">getOrThrow</span>(<span class="str">'app.jwtSecret'</span>);
  }
}</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 09 -->
  <section class="section" id="s09">
    <div class="section-label">
      <span class="sec-num">09</span>
      <span class="sec-badge badge-ileri">İleri</span>
    </div>
    <h2>Interceptors</h2>
    <p class="intro">
      Interceptor, controller çalışmadan önce ve sonra araya giren bir middleware benzeri katmandır.
      RxJS Observable tabanlı çalışır ve response transform, logging, cache, timeout gibi cross-cutting
      concerns için kullanılır.
    </p>

    <h3>Transform Interceptor — Tüm Yanıtları Sarmak</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/interceptors/transform.interceptor.ts</div>
      <pre><span class="kw">import</span> {
  Injectable, NestInterceptor, ExecutionContext,
  CallHandler,
} <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">Observable</span> } <span class="kw">from</span> <span class="str">'rxjs'</span>;
<span class="kw">import</span> { <span class="fn">map</span> } <span class="kw">from</span> <span class="str">'rxjs/operators'</span>;

<span class="kw">export interface</span> <span class="cls">ResponseEnvelope</span><<span class="cls">T</span>> {
  data: <span class="cls">T</span>;
  success: <span class="typ">boolean</span>;
  timestamp: <span class="typ">string</span>;
}

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">TransformInterceptor</span><<span class="cls">T</span>>
  <span class="kw">implements</span> <span class="cls">NestInterceptor</span><<span class="cls">T</span>, <span class="cls">ResponseEnvelope</span><<span class="cls">T</span>>>
{
  <span class="fn">intercept</span>(ctx: <span class="cls">ExecutionContext</span>, next: <span class="cls">CallHandler</span>): <span class="cls">Observable</span><<span class="cls">ResponseEnvelope</span><<span class="cls">T</span>>> {
    <span class="kw">return</span> next.<span class="fn">handle</span>().<span class="fn">pipe</span>(
      <span class="fn">map</span>((data) => ({
        data,
        success: <span class="kw">true</span>,
        timestamp: <span class="kw">new</span> <span class="cls">Date</span>().<span class="fn">toISOString</span>(),
      })),
    );
  }
}

<span class="cmt">// Global uygulamak için main.ts'e:</span>
app.<span class="fn">useGlobalInterceptors</span>(<span class="kw">new</span> <span class="cls">TransformInterceptor</span>());</pre>
    </div>

    <h3>Logging Interceptor</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/interceptors/logging.interceptor.ts</div>
      <pre><span class="kw">import</span> { <span class="fn">tap</span> } <span class="kw">from</span> <span class="str">'rxjs/operators'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">LoggingInterceptor</span> <span class="kw">implements</span> <span class="cls">NestInterceptor</span> {
  <span class="kw">private</span> logger = <span class="kw">new</span> <span class="cls">Logger</span>(<span class="str">'HTTP'</span>);

  <span class="fn">intercept</span>(ctx: <span class="cls">ExecutionContext</span>, next: <span class="cls">CallHandler</span>): <span class="cls">Observable</span><<span class="typ">any</span>> {
    <span class="kw">const</span> req = ctx.<span class="fn">switchToHttp</span>().<span class="fn">getRequest</span>();
    <span class="kw">const</span> { method, url } = req;
    <span class="kw">const</span> start = <span class="cls">Date</span>.<span class="fn">now</span>();

    <span class="kw">return</span> next.<span class="fn">handle</span>().<span class="fn">pipe</span>(
      <span class="fn">tap</span>({
        next: () => {
          <span class="kw">const</span> ms = <span class="cls">Date</span>.<span class="fn">now</span>() - start;
          <span class="kw">this</span>.logger.<span class="fn">log</span>(<span class="str">`${method} ${url} — ${ms}ms`</span>);
        },
        error: (err) => {
          <span class="kw">const</span> ms = <span class="cls">Date</span>.<span class="fn">now</span>() - start;
          <span class="kw">this</span>.logger.<span class="fn">error</span>(<span class="str">`${method} ${url} — ${ms}ms — ${err.message}`</span>);
        },
      }),
    );
  }
}</pre>
    </div>

    <h3>Cache Interceptor</h3>
    <div class="code-wrap">
      <div class="code-title">basit in-memory cache interceptor</div>
      <pre><span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">CacheInterceptor</span> <span class="kw">implements</span> <span class="cls">NestInterceptor</span> {
  <span class="kw">private</span> cache = <span class="kw">new</span> <span class="cls">Map</span><<span class="typ">string</span>, { data: <span class="typ">any</span>; expires: <span class="typ">number</span> }>();

  <span class="fn">intercept</span>(ctx: <span class="cls">ExecutionContext</span>, next: <span class="cls">CallHandler</span>): <span class="cls">Observable</span><<span class="typ">any</span>> {
    <span class="kw">const</span> req = ctx.<span class="fn">switchToHttp</span>().<span class="fn">getRequest</span>();
    <span class="kw">const</span> key = req.url;
    <span class="kw">const</span> cached = <span class="kw">this</span>.cache.<span class="fn">get</span>(key);

    <span class="kw">if</span> (cached && cached.expires > <span class="cls">Date</span>.<span class="fn">now</span>()) {
      <span class="kw">return</span> <span class="fn">of</span>(cached.data);  <span class="cmt">// cache'den dön</span>
    }

    <span class="kw">return</span> next.<span class="fn">handle</span>().<span class="fn">pipe</span>(
      <span class="fn">tap</span>((data) => {
        <span class="kw">this</span>.cache.<span class="fn">set</span>(key, { data, expires: <span class="cls">Date</span>.<span class="fn">now</span>() + <span class="num">60_000</span> });
      }),
    );
  }
}</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 10 -->
  <section class="section" id="s10">
    <div class="section-label">
      <span class="sec-num">10</span>
      <span class="sec-badge badge-ileri">İleri</span>
    </div>
    <h2>Exception Filters</h2>
    <p class="intro">
      Exception Filter, fırlatılan hataları yakalayıp HTTP response'a dönüştüren katmandır.
      NestJS varsayılan olarak HttpException'ları işler ama tüm hataları özelleştirmek için
      global filter yazarsın.
    </p>

    <h3>Global Exception Filter</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/filters/all-exceptions.filter.ts</div>
      <pre><span class="kw">import</span> {
  ExceptionFilter, Catch, ArgumentsHost,
  HttpException, HttpStatus, Logger,
} <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">Request</span>, <span class="cls">Response</span> } <span class="kw">from</span> <span class="str">'express'</span>;

<span class="dec">@Catch</span>()  <span class="cmt">// Argümansız = her türlü hatayı yakala</span>
<span class="kw">export class</span> <span class="cls">AllExceptionsFilter</span> <span class="kw">implements</span> <span class="cls">ExceptionFilter</span> {
  <span class="kw">private</span> logger = <span class="kw">new</span> <span class="cls">Logger</span>(<span class="cls">AllExceptionsFilter</span>.name);

  <span class="fn">catch</span>(exception: unknown, host: <span class="cls">ArgumentsHost</span>) {
    <span class="kw">const</span> ctx = host.<span class="fn">switchToHttp</span>();
    <span class="kw">const</span> res = ctx.<span class="fn">getResponse</span><<span class="cls">Response</span>>();
    <span class="kw">const</span> req = ctx.<span class="fn">getRequest</span><<span class="cls">Request</span>>();

    <span class="kw">let</span> status = <span class="cls">HttpStatus</span>.INTERNAL_SERVER_ERROR;
    <span class="kw">let</span> message: <span class="typ">any</span> = <span class="str">'Sunucu hatası'</span>;
    <span class="kw">let</span> code = <span class="str">'INTERNAL_ERROR'</span>;

    <span class="kw">if</span> (exception <span class="kw">instanceof</span> <span class="cls">HttpException</span>) {
      status = exception.<span class="fn">getStatus</span>();
      <span class="kw">const</span> body = exception.<span class="fn">getResponse</span>();
      message = <span class="kw">typeof</span> body === <span class="str">'object'</span> ? (body <span class="kw">as any</span>).message : body;
      code = exception.constructor.name.<span class="fn">replace</span>(<span class="str">'Exception'</span>, <span class="str">''</span>).<span class="fn">toUpperCase</span>();
    } <span class="kw">else if</span> (exception <span class="kw">instanceof</span> <span class="cls">Error</span>) {
      <span class="kmt">// TypeORM veya diğer runtime hataları</span>
      <span class="kw">this</span>.logger.<span class="fn">error</span>(exception.stack);
    }

    res.<span class="fn">status</span>(status).<span class="fn">json</span>({
      success: <span class="kw">false</span>,
      code,
      message,
      path: req.url,
      timestamp: <span class="kw">new</span> <span class="cls">Date</span>().<span class="fn">toISOString</span>(),
    });
  }
}</pre>
    </div>

    <h3>Custom Business Exception</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/exceptions/business.exception.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">HttpException</span>, <span class="cls">HttpStatus</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="kw">export class</span> <span class="cls">BusinessException</span> <span class="kw">extends</span> <span class="cls">HttpException</span> {
  <span class="kw">constructor</span>(
    <span class="kw">public</span> code: <span class="typ">string</span>,
    message: <span class="typ">string</span>,
    status = <span class="cls">HttpStatus</span>.BAD_REQUEST,
  ) {
    <span class="fn">super</span>({ code, message }, status);
  }
}

<span class="cmt">// Kullanımı:</span>
<span class="kw">throw new</span> <span class="cls">BusinessException</span>(
  <span class="str">'INSUFFICIENT_BALANCE'</span>,
  <span class="str">'Yetersiz bakiye'</span>,
  <span class="cls">HttpStatus</span>.UNPROCESSABLE_ENTITY,
);</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 11 -->
  <section class="section" id="s11">
    <div class="section-label">
      <span class="sec-num">11</span>
      <span class="sec-badge badge-ileri">İleri</span>
    </div>
    <h2>Guards &amp; Role Tabanlı Erişim</h2>
    <p class="intro">
      Guard, isteğin ilerleyip ilerlemeyeceğine karar verir (middleware'den farklı olarak
      execution context'e erişimi vardır). JWT Guard sonrasında roles guard ile yetkilendirme yaparız.
    </p>

    <h3>Roles Decorator</h3>
    <div class="code-wrap">
      <div class="code-title">src/auth/decorators/roles.decorator.ts</div>
      <pre><span class="kw">import</span> { <span class="fn">SetMetadata</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="kw">export enum</span> <span class="cls">Role</span> {
  USER = <span class="str">'user'</span>,
  MODERATOR = <span class="str">'moderator'</span>,
  ADMIN = <span class="str">'admin'</span>,
}

<span class="kw">export const</span> <span class="cls">ROLES_KEY</span> = <span class="str">'roles'</span>;
<span class="kw">export const</span> <span class="cls">Roles</span> = (...roles: <span class="cls">Role</span>[]) => <span class="fn">SetMetadata</span>(<span class="cls">ROLES_KEY</span>, roles);</pre>
    </div>

    <h3>Roles Guard</h3>
    <div class="code-wrap">
      <div class="code-title">src/auth/guards/roles.guard.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Injectable</span>, <span class="cls">CanActivate</span>, <span class="cls">ExecutionContext</span>, <span class="cls">ForbiddenException</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">Reflector</span> } <span class="kw">from</span> <span class="str">'@nestjs/core'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">RolesGuard</span> <span class="kw">implements</span> <span class="cls">CanActivate</span> {
  <span class="kw">constructor</span>(<span class="kw">private</span> reflector: <span class="cls">Reflector</span>) {}

  <span class="fn">canActivate</span>(ctx: <span class="cls">ExecutionContext</span>): <span class="typ">boolean</span> {
    <span class="kw">const</span> requiredRoles = <span class="kw">this</span>.reflector.<span class="fn">getAllAndOverride</span><<span class="cls">Role</span>[]>(<span class="cls">ROLES_KEY</span>, [
      ctx.<span class="fn">getHandler</span>(),
      ctx.<span class="fn">getClass</span>(),
    ]);

    <span class="kw">if</span> (!requiredRoles || requiredRoles.length === <span class="num">0</span>) <span class="kw">return true</span>;

    <span class="kw">const</span> req = ctx.<span class="fn">switchToHttp</span>().<span class="fn">getRequest</span>();
    <span class="kw">const</span> user = req.user;

    <span class="kw">if</span> (!user) <span class="kw">throw new</span> <span class="cls">ForbiddenException</span>(<span class="str">'Giriş yapınız'</span>);

    <span class="kw">const</span> hasRole = requiredRoles.<span class="fn">some</span>((r) => user.role === r);
    <span class="kw">if</span> (!hasRole) <span class="kw">throw new</span> <span class="cls">ForbiddenException</span>(<span class="str">'Bu işlem için yetkiniz yok'</span>);

    <span class="kw">return true</span>;
  }
}

<span class="cmt">// Kullanımı controller'da:</span>
<span class="dec">@UseGuards</span>(<span class="cls">JwtAuthGuard</span>, <span class="cls">RolesGuard</span>)
<span class="dec">@Roles</span>(<span class="cls">Role</span>.ADMIN)
<span class="dec">@Delete</span>(<span class="str">':id'</span>)
<span class="fn">remove</span>(<span class="dec">@Param</span>(<span class="str">'id'</span>) id: <span class="typ">string</span>) {
  <span class="kw">return</span> <span class="kw">this</span>.service.<span class="fn">remove</span>(<span class="op">+</span>id);
}</pre>
    </div>

    <div class="callout info">
      <strong>İpucu:</strong> Guard sırası önemlidir. Önce <code>JwtAuthGuard</code> çalışarak
      <code>req.user</code>'ı doldurur, ardından <code>RolesGuard</code> o değeri okur.
      Sırayı tersine çevirirsen <code>req.user</code> undefined gelir.
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 12 -->
  <section class="section" id="s12">
    <div class="section-label">
      <span class="sec-num">12</span>
      <span class="sec-badge badge-ileri">İleri</span>
    </div>
    <h2>Middleware</h2>
    <p class="intro">
      Middleware, Express middleware'ine eşdeğerdir. Guard ve Interceptor'dan farklı olarak
      execution context'e erişimi yoktur. Request öncesi işlemler (rate limit, request ID, logger)
      için kullanılır.
    </p>

    <h3>Request ID Middleware</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/middleware/request-id.middleware.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Injectable</span>, <span class="cls">NestMiddleware</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">Request</span>, <span class="cls">Response</span>, <span class="cls">NextFunction</span> } <span class="kw">from</span> <span class="str">'express'</span>;
<span class="kw">import</span> { <span class="fn">randomUUID</span> } <span class="kw">from</span> <span class="str">'crypto'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">RequestIdMiddleware</span> <span class="kw">implements</span> <span class="cls">NestMiddleware</span> {
  <span class="fn">use</span>(req: <span class="cls">Request</span>, res: <span class="cls">Response</span>, next: <span class="cls">NextFunction</span>) {
    <span class="cmt">// Her isteğe benzersiz ID ekle — logları izlemek için</span>
    req[<span class="str">'requestId'</span>] = <span class="fn">randomUUID</span>();
    res.<span class="fn">setHeader</span>(<span class="str">'X-Request-Id'</span>, req[<span class="str">'requestId'</span>]);
    <span class="fn">next</span>();
  }
}</pre>
    </div>

    <h3>Rate Limit Middleware</h3>
    <div class="code-wrap">
      <div class="code-title">src/common/middleware/rate-limit.middleware.ts</div>
      <pre><span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">RateLimitMiddleware</span> <span class="kw">implements</span> <span class="cls">NestMiddleware</span> {
  <span class="kw">private</span> requests = <span class="kw">new</span> <span class="cls">Map</span><<span class="typ">string</span>, { count: <span class="typ">number</span>; reset: <span class="typ">number</span> }>();

  <span class="fn">use</span>(req: <span class="cls">Request</span>, res: <span class="cls">Response</span>, next: <span class="cls">NextFunction</span>) {
    <span class="kw">const</span> ip = req.ip;
    <span class="kw">const</span> now = <span class="cls">Date</span>.<span class="fn">now</span>();
    <span class="kw">const</span> windowMs = <span class="num">60_000</span>;   <span class="cmt">// 1 dakika</span>
    <span class="kw">const</span> max = <span class="num">100</span>;

    <span class="kw">const</span> entry = <span class="kw">this</span>.requests.<span class="fn">get</span>(ip) || { count: <span class="num">0</span>, reset: now + windowMs };

    <span class="kw">if</span> (now > entry.reset) {
      entry.count = <span class="num">0</span>;
      entry.reset = now + windowMs;
    }

    entry.count++;
    <span class="kw">this</span>.requests.<span class="fn">set</span>(ip, entry);

    res.<span class="fn">setHeader</span>(<span class="str">'X-RateLimit-Limit'</span>, max);
    res.<span class="fn">setHeader</span>(<span class="str">'X-RateLimit-Remaining'</span>, Math.<span class="fn">max</span>(<span class="num">0</span>, max - entry.count));

    <span class="kw">if</span> (entry.count > max) {
      res.<span class="fn">status</span>(<span class="num">429</span>).<span class="fn">json</span>({ message: <span class="str">'Çok fazla istek. 1 dakika bekleyin.'</span> });
      <span class="kw">return</span>;
    }

    <span class="fn">next</span>();
  }
}

<span class="cmt">// Modülde bağla:</span>
<span class="kw">export class</span> <span class="cls">AppModule</span> <span class="kw">implements</span> <span class="cls">NestModule</span> {
  <span class="fn">configure</span>(consumer: <span class="cls">MiddlewareConsumer</span>) {
    consumer
      .<span class="fn">apply</span>(<span class="cls">RequestIdMiddleware</span>, <span class="cls">RateLimitMiddleware</span>)
      .<span class="fn">forRoutes</span>(<span class="str">'*'</span>);  <span class="cmt">// tüm route'lar</span>
  }
}</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 13 -->
  <section class="section" id="s13">
    <div class="section-label">
      <span class="sec-num">13</span>
      <span class="sec-badge badge-ileri">İleri</span>
    </div>
    <h2>@Req() ve @Res() Decorator'ları</h2>
    <p class="intro">
      NestJS'in soyutlamalarını (DTO, Param, Query) kullanmak her zaman öncelikli tercihtir.
      @Req() ve @Res() ham Express nesnelerine doğrudan erişir — bunu sadece framework'ün
      sağlayamadığı şeyler için kullan.
    </p>

    <div class="callout danger">
      <strong>Kritik:</strong> @Res() inject ettiğinde passthrough: true kullanmazsan
      NestJS response yönetiminden çekilir. res.json() veya res.send() çağırmazsan
      istek askıda kalır ve timeout olur.
    </div>

    <h3>@Res() ile Cookie Set Etmek</h3>
    <div class="code-wrap">
      <div class="code-title">src/auth/auth.controller.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Res</span>, <span class="cls">Post</span>, <span class="cls">Body</span>, <span class="cls">HttpCode</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">Response</span> } <span class="kw">from</span> <span class="str">'express'</span>;

<span class="dec">@Post</span>(<span class="str">'login'</span>)
<span class="dec">@HttpCode</span>(<span class="num">200</span>)
<span class="kw">async</span> <span class="fn">login</span>(
  <span class="dec">@Body</span>() dto: <span class="cls">LoginDto</span>,
  <span class="dec">@Res</span>({ passthrough: <span class="kw">true</span> }) res: <span class="cls">Response</span>,  <span class="cmt">// passthrough şart!</span>
) {
  <span class="kw">const</span> { accessToken, refreshToken } = <span class="kw">await</span> <span class="kw">this</span>.authService.<span class="fn">login</span>(dto);

  res.<span class="fn">cookie</span>(<span class="str">'access_token'</span>, accessToken, {
    httpOnly: <span class="kw">true</span>,      <span class="cmt">// JavaScript erişemez — XSS koruması</span>
    secure: <span class="kw">true</span>,        <span class="cmt">// sadece HTTPS üzerinden</span>
    sameSite: <span class="str">'strict'</span>,  <span class="cmt">// CSRF koruması</span>
    maxAge: <span class="num">15</span> * <span class="num">60</span> * <span class="num">1000</span>,  <span class="cmt">// 15 dakika</span>
  });

  res.<span class="fn">cookie</span>(<span class="str">'refresh_token'</span>, refreshToken, {
    httpOnly: <span class="kw">true</span>,
    secure: <span class="kw">true</span>,
    path: <span class="str">'/auth/refresh'</span>,   <span class="cmt">// sadece refresh endpoint'inde gönderilir</span>
    maxAge: <span class="num">7</span> * <span class="num">24</span> * <span class="num">60</span> * <span class="num">60</span> * <span class="num">1000</span>,  <span class="cmt">// 7 gün</span>
  });

  <span class="kw">return</span> { message: <span class="str">'Giriş başarılı'</span> };  <span class="cmt">// passthrough → NestJS gönderir</span>
}</pre>
    </div>

    <h3>@Res() ile Dosya İndirme</h3>
    <div class="code-wrap">
      <div class="code-title">dosya stream ile gönderme</div>
      <pre><span class="kw">import</span> { <span class="cls">createReadStream</span> } <span class="kw">from</span> <span class="str">'fs'</span>;
<span class="kw">import</span> { <span class="fn">join</span> } <span class="kw">from</span> <span class="str">'path'</span>;
<span class="kw">import</span> { <span class="cls">StreamableFile</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="dec">@Get</span>(<span class="str">'download/:filename'</span>)
<span class="kw">async</span> <span class="fn">downloadFile</span>(
  <span class="dec">@Param</span>(<span class="str">'filename'</span>) filename: <span class="typ">string</span>,
  <span class="dec">@Res</span>({ passthrough: <span class="kw">true</span> }) res: <span class="cls">Response</span>,
) {
  <span class="kw">const</span> filePath = <span class="fn">join</span>(__dirname, <span class="str">'../uploads'</span>, filename);

  res.<span class="fn">set</span>({
    <span class="str">'Content-Type'</span>: <span class="str">'application/octet-stream'</span>,
    <span class="str">'Content-Disposition'</span>: <span class="str">`attachment; filename="${filename}"`</span>,
  });

  <span class="kw">const</span> stream = <span class="fn">createReadStream</span>(filePath);
  <span class="kw">return new</span> <span class="cls">StreamableFile</span>(stream);  <span class="cmt">// NestJS otomatik pipe eder</span>
}</pre>
    </div>

    <h3>@Req() ile IP ve Audit Log</h3>
    <div class="code-wrap">
      <div class="code-title">güvenlik logu için req kullanımı</div>
      <pre><span class="kw">import</span> { <span class="cls">Req</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">Request</span> } <span class="kw">from</span> <span class="str">'express'</span>;

<span class="dec">@Post</span>(<span class="str">'login'</span>)
<span class="kw">async</span> <span class="fn">login</span>(<span class="dec">@Body</span>() dto: <span class="cls">LoginDto</span>, <span class="dec">@Req</span>() req: <span class="cls">Request</span>) {
  <span class="cmt">// Reverse proxy arkasında gerçek IP (Nginx/CloudFlare)</span>
  <span class="kw">const</span> clientIp =
    (req.headers[<span class="str">'x-forwarded-for'</span>] <span class="kw">as</span> <span class="typ">string</span>)?.<span class="fn">split</span>(<span class="str">','</span>)[<span class="num">0</span>] ??
    req.socket.remoteAddress;

  <span class="kw">const</span> userAgent = req.headers[<span class="str">'user-agent'</span>];

  <span class="kw">await</span> <span class="kw">this</span>.auditService.<span class="fn">log</span>({
    action: <span class="str">'LOGIN_ATTEMPT'</span>,
    email: dto.email,
    ip: clientIp,
    userAgent,
    timestamp: <span class="kw">new</span> <span class="cls">Date</span>(),
  });

  <span class="kw">return</span> <span class="kw">this</span>.authService.<span class="fn">login</span>(dto);
}</pre>
    </div>

    <h3>Custom Param Decorator — @CurrentUser()</h3>
    <div class="code-wrap">
      <div class="code-title">@Req().user yerine daha temiz çözüm</div>
      <pre><span class="kw">import</span> { <span class="fn">createParamDecorator</span>, <span class="cls">ExecutionContext</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="cmt">// req.user'ı temiz şekilde inject eden decorator</span>
<span class="kw">export const</span> <span class="cls">CurrentUser</span> = <span class="fn">createParamDecorator</span>(
  (field: <span class="kw">keyof</span> <span class="cls">User</span> | <span class="kw">undefined</span>, ctx: <span class="cls">ExecutionContext</span>) => {
    <span class="kw">const</span> user = ctx.<span class="fn">switchToHttp</span>().<span class="fn">getRequest</span>().user;
    <span class="kw">return</span> field ? user?.[field] : user;
  },
);

<span class="cmt">// Kullanımı:</span>
<span class="dec">@Get</span>(<span class="str">'profile'</span>)
<span class="dec">@UseGuards</span>(<span class="cls">JwtAuthGuard</span>)
<span class="fn">getProfile</span>(<span class="dec">@CurrentUser</span>() user: <span class="cls">User</span>) {
  <span class="kw">return</span> user;  <span class="cmt">// tüm user objesi</span>
}

<span class="dec">@Get</span>(<span class="str">'my-role'</span>)
<span class="fn">getRole</span>(<span class="dec">@CurrentUser</span>(<span class="str">'role'</span>) role: <span class="typ">string</span>) {
  <span class="kw">return</span> { role };  <span class="cmt">// sadece role alanı</span>
}</pre>
    </div>

    <h3>@Res() Passthrough Karşılaştırması</h3>
    <div class="table-wrap">
      <table>
        <thead>
          <tr><th>Durum</th><th>Interceptor</th><th>ClassSerializer</th><th>return değeri</th></tr>
        </thead>
        <tbody>
          <tr><td>passthrough: true</td><td>✓ Çalışır</td><td>✓ Çalışır</td><td>NestJS gönderir</td></tr>
          <tr><td>passthrough yok + res.json()</td><td>✗ Bypass</td><td>✗ Bypass</td><td>Sen gönderirsin</td></tr>
          <tr><td>passthrough yok + return</td><td>✗ Bypass</td><td>✗ Bypass</td><td>Timeout!</td></tr>
        </tbody>
      </table>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 14 -->
  <section class="section" id="s14">
    <div class="section-label">
      <span class="sec-num">14</span>
      <span class="sec-badge badge-uzman">Uzman</span>
    </div>
    <h2>WebSockets — Gateway</h2>
    <p class="intro">
      NestJS, Socket.io veya native WebSocket üzerine kurulu Gateway sistemi ile gerçek zamanlı
      iletişim sağlar. Gateway'ler, olayları dinler ve tüm bağlı istemcilere ya da belirli
      odalara (room) mesaj gönderir.
    </p>

    <h3>Kurulum</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install @nestjs/websockets @nestjs/platform-socket.io socket.io</pre>
    </div>

    <h3>Chat Gateway</h3>
    <div class="code-wrap">
      <div class="code-title">src/chat/chat.gateway.ts</div>
      <pre><span class="kw">import</span> {
  WebSocketGateway, WebSocketServer, SubscribeMessage,
  OnGatewayInit, OnGatewayConnection, OnGatewayDisconnect,
  MessageBody, ConnectedSocket,
} <span class="kw">from</span> <span class="str">'@nestjs/websockets'</span>;
<span class="kw">import</span> { <span class="cls">Server</span>, <span class="cls">Socket</span> } <span class="kw">from</span> <span class="str">'socket.io'</span>;
<span class="kw">import</span> { <span class="cls">Logger</span>, <span class="cls">UseGuards</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

<span class="dec">@WebSocketGateway</span>({
  cors: { origin: <span class="str">'*'</span> },
  namespace: <span class="str">'chat'</span>,     <span class="cmt">// ws://localhost:3001/chat</span>
})
<span class="kw">export class</span> <span class="cls">ChatGateway</span>
  <span class="kw">implements</span> <span class="cls">OnGatewayInit</span>, <span class="cls">OnGatewayConnection</span>, <span class="cls">OnGatewayDisconnect</span>
{
  <span class="dec">@WebSocketServer</span>()
  server: <span class="cls">Server</span>;

  <span class="kw">private</span> logger = <span class="kw">new</span> <span class="cls">Logger</span>(<span class="str">'ChatGateway'</span>);

  <span class="fn">afterInit</span>() {
    <span class="kw">this</span>.logger.<span class="fn">log</span>(<span class="str">'WebSocket Gateway başlatıldı'</span>);
  }

  <span class="fn">handleConnection</span>(client: <span class="cls">Socket</span>) {
    <span class="kw">this</span>.logger.<span class="fn">log</span>(<span class="str">`Client bağlandı: ${client.id}`</span>);
    <span class="cmt">// Token doğrulama</span>
    <span class="kw">const</span> token = client.handshake.auth.token;
    <span class="kw">if</span> (!token) { client.<span class="fn">disconnect</span>(); <span class="kw">return</span>; }
  }

  <span class="fn">handleDisconnect</span>(client: <span class="cls">Socket</span>) {
    <span class="kw">this</span>.logger.<span class="fn">log</span>(<span class="str">`Client ayrıldı: ${client.id}`</span>);
    <span class="cmt">// Odadan kaldır, "kullanıcı ayrıldı" broadcast et</span>
    <span class="kw">this</span>.server.<span class="fn">emit</span>(<span class="str">'user_left'</span>, { socketId: client.id });
  }

  <span class="cmt">// 'join_room' eventi: odaya katıl</span>
  <span class="dec">@SubscribeMessage</span>(<span class="str">'join_room'</span>)
  <span class="fn">handleJoinRoom</span>(
    <span class="dec">@MessageBody</span>() roomId: <span class="typ">string</span>,
    <span class="dec">@ConnectedSocket</span>() client: <span class="cls">Socket</span>,
  ) {
    client.<span class="fn">join</span>(roomId);
    <span class="cmt">// Odadaki diğer kullanıcılara bildir</span>
    client.<span class="fn">to</span>(roomId).<span class="fn">emit</span>(<span class="str">'user_joined'</span>, { socketId: client.id, roomId });
    <span class="kw">return</span> { event: <span class="str">'joined'</span>, roomId };  <span class="cmt">// sadece bu client'a döner</span>
  }

  <span class="cmt">// 'send_message' eventi: odaya mesaj gönder</span>
  <span class="dec">@SubscribeMessage</span>(<span class="str">'send_message'</span>)
  <span class="fn">handleMessage</span>(
    <span class="dec">@MessageBody</span>() data: { roomId: <span class="typ">string</span>; text: <span class="typ">string</span> },
    <span class="dec">@ConnectedSocket</span>() client: <span class="cls">Socket</span>,
  ) {
    <span class="kw">const</span> msg = {
      from: client.id,
      text: data.text,
      timestamp: <span class="kw">new</span> <span class="cls">Date</span>().<span class="fn">toISOString</span>(),
    };
    <span class="cmt">// Odadaki herkese (gönderen dahil) yayınla</span>
    <span class="kw">this</span>.server.<span class="fn">to</span>(data.roomId).<span class="fn">emit</span>(<span class="str">'new_message'</span>, msg);
  }

  <span class="cmt">// Gateway dışından mesaj göndermek için (servis üzerinden)</span>
  <span class="fn">broadcastToRoom</span>(roomId: <span class="typ">string</span>, event: <span class="typ">string</span>, data: <span class="typ">any</span>) {
    <span class="kw">this</span>.server.<span class="fn">to</span>(roomId).<span class="fn">emit</span>(event, data);
  }
}</pre>
    </div>

    <h3>Frontend (Client) Tarafı</h3>
    <div class="code-wrap">
      <div class="code-title">istemci tarafı bağlantı — socket.io-client</div>
      <pre><span class="kw">import</span> { io } <span class="kw">from</span> <span class="str">'socket.io-client'</span>;

<span class="kw">const</span> socket = <span class="fn">io</span>(<span class="str">'http://localhost:3001/chat'</span>, {
  auth: { token: localStorage.<span class="fn">getItem</span>(<span class="str">'access_token'</span>) },
});

socket.<span class="fn">on</span>(<span class="str">'connect'</span>, () => {
  console.<span class="fn">log</span>(<span class="str">'Bağlandı'</span>, socket.id);
  socket.<span class="fn">emit</span>(<span class="str">'join_room'</span>, <span class="str">'room-1'</span>);
});

socket.<span class="fn">on</span>(<span class="str">'new_message'</span>, (msg) => console.<span class="fn">log</span>(msg));

socket.<span class="fn">emit</span>(<span class="str">'send_message'</span>, { roomId: <span class="str">'room-1'</span>, text: <span class="str">'Merhaba!'</span> });</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 15 -->
  <section class="section" id="s15">
    <div class="section-label">
      <span class="sec-num">15</span>
      <span class="sec-badge badge-uzman">Uzman</span>
    </div>
    <h2>Microservices</h2>
    <p class="intro">
      NestJS, TCP, Redis, NATS, RabbitMQ ve Kafka gibi transport katmanları üzerinden
      microservice mimarisini birinci sınıf destekler. MessagePattern ile istek/yanıt,
      EventPattern ile fire-and-forget iletişim sağlanır.
    </p>

    <h3>Kurulum</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install @nestjs/microservices
<span class="cmt"># Redis transport için ek driver:</span>
npm install ioredis</pre>
    </div>

    <h3>Microservice Başlatma</h3>
    <div class="code-wrap">
      <div class="code-title">apps/users-ms/src/main.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">NestFactory</span> } <span class="kw">from</span> <span class="str">'@nestjs/core'</span>;
<span class="kw">import</span> { <span class="cls">Transport</span>, <span class="cls">MicroserviceOptions</span> } <span class="kw">from</span> <span class="str">'@nestjs/microservices'</span>;

<span class="kw">async function</span> <span class="fn">bootstrap</span>() {
  <span class="kw">const</span> app = <span class="kw">await</span> <span class="cls">NestFactory</span>.<span class="fn">createMicroservice</span><<span class="cls">MicroserviceOptions</span>>(
    AppModule,
    {
      transport: <span class="cls">Transport</span>.REDIS,
      options: {
        host: process.env.REDIS_HOST || <span class="str">'localhost'</span>,
        port: <span class="num">6379</span>,
      },
    },
  );
  <span class="kw">await</span> app.<span class="fn">listen</span>();
  console.<span class="fn">log</span>(<span class="str">'Users Microservice çalışıyor'</span>);
}
<span class="fn">bootstrap</span>();</pre>
    </div>

    <h3>Microservice Controller</h3>
    <div class="code-wrap">
      <div class="code-title">apps/users-ms/src/users.controller.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Controller</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">MessagePattern</span>, <span class="cls">EventPattern</span>, <span class="cls">Payload</span> } <span class="kw">from</span> <span class="str">'@nestjs/microservices'</span>;

<span class="dec">@Controller</span>()
<span class="kw">export class</span> <span class="cls">UsersController</span> {
  <span class="kw">constructor</span>(<span class="kw">private</span> usersService: <span class="cls">UsersService</span>) {}

  <span class="cmt">// MessagePattern → istek/yanıt (caller cevap bekler)</span>
  <span class="dec">@MessagePattern</span>({ cmd: <span class="str">'get_user'</span> })
  <span class="fn">getUser</span>(<span class="dec">@Payload</span>() id: <span class="typ">number</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">findOne</span>(id);
  }

  <span class="dec">@MessagePattern</span>({ cmd: <span class="str">'create_user'</span> })
  <span class="fn">createUser</span>(<span class="dec">@Payload</span>() dto: <span class="cls">CreateUserDto</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.usersService.<span class="fn">create</span>(dto);
  }

  <span class="cmt">// EventPattern → fire-and-forget (cevap beklenmez)</span>
  <span class="dec">@EventPattern</span>(<span class="str">'user_created'</span>)
  <span class="fn">onUserCreated</span>(<span class="dec">@Payload</span>() data: { userId: <span class="typ">number</span>; email: <span class="typ">string</span> }) {
    <span class="kw">this</span>.usersService.<span class="fn">sendWelcomeEmail</span>(data);
  }
}</pre>
    </div>

    <h3>API Gateway — Microservice'i Çağırmak</h3>
    <div class="code-wrap">
      <div class="code-title">apps/api-gateway/src/users.service.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Inject</span>, <span class="cls">Injectable</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> { <span class="cls">ClientProxy</span> } <span class="kw">from</span> <span class="str">'@nestjs/microservices'</span>;
<span class="kw">import</span> { <span class="fn">lastValueFrom</span> } <span class="kw">from</span> <span class="str">'rxjs'</span>;

<span class="dec">@Injectable</span>()
<span class="kw">export class</span> <span class="cls">UsersGatewayService</span> {
  <span class="kw">constructor</span>(
    <span class="dec">@Inject</span>(<span class="str">'USERS_SERVICE'</span>)
    <span class="kw">private</span> client: <span class="cls">ClientProxy</span>,
  ) {}

  <span class="fn">getUser</span>(id: <span class="typ">number</span>) {
    <span class="cmt">// send() → Observable döner, await için lastValueFrom kullan</span>
    <span class="kw">return</span> <span class="fn">lastValueFrom</span>(<span class="kw">this</span>.client.<span class="fn">send</span>({ cmd: <span class="str">'get_user'</span> }, id));
  }

  <span class="fn">emitUserCreated</span>(data: { userId: <span class="typ">number</span>; email: <span class="typ">string</span> }) {
    <span class="cmt">// emit() → cevap beklemez (EventPattern ile eşleşir)</span>
    <span class="kw">this</span>.client.<span class="fn">emit</span>(<span class="str">'user_created'</span>, data);
  }
}

<span class="cmt">// Module'da client tanımlama:</span>
<span class="dec">@Module</span>({
  imports: [
    <span class="cls">ClientsModule</span>.<span class="fn">register</span>([{
      name: <span class="str">'USERS_SERVICE'</span>,
      transport: <span class="cls">Transport</span>.REDIS,
      options: { host: <span class="str">'localhost'</span>, port: <span class="num">6379</span> },
    }]),
  ],
})
<span class="kw">export class</span> <span class="cls">GatewayModule</span> {}</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 16 -->
  <section class="section" id="s16">
    <div class="section-label">
      <span class="sec-num">16</span>
      <span class="sec-badge badge-uzman">Uzman</span>
    </div>
    <h2>CQRS Pattern</h2>
    <p class="intro">
      CQRS (Command Query Responsibility Segregation), okuma ve yazma operasyonlarını birbirinden
      ayırır. Command veri değiştirir, Query veri okur. Her biri ayrı handler sınıfında yaşar.
      Karmaşık domain mantığını yönetmek çok kolaylaşır.
    </p>

    <h3>Kurulum</h3>
    <div class="code-wrap">
      <div class="code-title">terminal</div>
      <pre>npm install @nestjs/cqrs</pre>
    </div>

    <h3>Command + Handler</h3>
    <div class="code-wrap">
      <div class="code-title">src/orders/commands/create-order.command.ts</div>
      <pre><span class="cmt">// Command: yazma niyetini taşır — sadece data, mantık yok</span>
<span class="kw">export class</span> <span class="cls">CreateOrderCommand</span> {
  <span class="kw">constructor</span>(
    <span class="kw">public readonly</span> userId: <span class="typ">number</span>,
    <span class="kw">public readonly</span> items: <span class="cls">OrderItem</span>[],
    <span class="kw">public readonly</span> addressId: <span class="typ">number</span>,
  ) {}
}</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/orders/handlers/create-order.handler.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">CommandHandler</span>, <span class="cls">ICommandHandler</span>, <span class="cls">EventBus</span> } <span class="kw">from</span> <span class="str">'@nestjs/cqrs'</span>;

<span class="dec">@CommandHandler</span>(<span class="cls">CreateOrderCommand</span>)
<span class="kw">export class</span> <span class="cls">CreateOrderHandler</span> <span class="kw">implements</span> <span class="cls">ICommandHandler</span><<span class="cls">CreateOrderCommand</span>> {
  <span class="kw">constructor</span>(
    <span class="kw">private</span> ordersRepo: <span class="cls">OrdersRepository</span>,
    <span class="kw">private</span> eventBus: <span class="cls">EventBus</span>,
  ) {}

  <span class="kw">async</span> <span class="fn">execute</span>(cmd: <span class="cls">CreateOrderCommand</span>): <span class="cls">Promise</span><<span class="cls">Order</span>> {
    <span class="kw">const</span> order = <span class="kw">await</span> <span class="kw">this</span>.ordersRepo.<span class="fn">create</span>({
      userId: cmd.userId,
      items: cmd.items,
      addressId: cmd.addressId,
      status: <span class="str">'pending'</span>,
    });

    <span class="cmt">// Domain event yayınla — başka handler'lar dinleyebilir</span>
    <span class="kw">this</span>.eventBus.<span class="fn">publish</span>(<span class="kw">new</span> <span class="cls">OrderCreatedEvent</span>(order.id, cmd.userId));

    <span class="kw">return</span> order;
  }
}</pre>
    </div>

    <h3>Query + Handler</h3>
    <div class="code-wrap">
      <div class="code-title">src/orders/queries/get-user-orders.query.ts</div>
      <pre><span class="kw">export class</span> <span class="cls">GetUserOrdersQuery</span> {
  <span class="kw">constructor</span>(
    <span class="kw">public readonly</span> userId: <span class="typ">number</span>,
    <span class="kw">public readonly</span> page: <span class="typ">number</span>,
    <span class="kw">public readonly</span> limit: <span class="typ">number</span>,
  ) {}
}</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/orders/handlers/get-user-orders.handler.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">QueryHandler</span>, <span class="cls">IQueryHandler</span> } <span class="kw">from</span> <span class="str">'@nestjs/cqrs'</span>;

<span class="dec">@QueryHandler</span>(<span class="cls">GetUserOrdersQuery</span>)
<span class="kw">export class</span> <span class="cls">GetUserOrdersHandler</span> <span class="kw">implements</span> <span class="cls">IQueryHandler</span><<span class="cls">GetUserOrdersQuery</span>> {
  <span class="kw">constructor</span>(<span class="kw">private</span> ordersRepo: <span class="cls">OrdersRepository</span>) {}

  <span class="fn">execute</span>(query: <span class="cls">GetUserOrdersQuery</span>): <span class="cls">Promise</span><<span class="cls">Order</span>[]> {
    <span class="kw">return</span> <span class="kw">this</span>.ordersRepo.<span class="fn">findByUser</span>(query.userId, query.page, query.limit);
  }
}</pre>
    </div>

    <h3>Controller'da CommandBus &amp; QueryBus</h3>
    <div class="code-wrap">
      <div class="code-title">src/orders/orders.controller.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">CommandBus</span>, <span class="cls">QueryBus</span> } <span class="kw">from</span> <span class="str">'@nestjs/cqrs'</span>;

<span class="dec">@Controller</span>(<span class="str">'orders'</span>)
<span class="dec">@UseGuards</span>(<span class="cls">JwtAuthGuard</span>)
<span class="kw">export class</span> <span class="cls">OrdersController</span> {
  <span class="kw">constructor</span>(
    <span class="kw">private</span> commandBus: <span class="cls">CommandBus</span>,
    <span class="kw">private</span> queryBus: <span class="cls">QueryBus</span>,
  ) {}

  <span class="dec">@Post</span>()
  <span class="fn">create</span>(<span class="dec">@Body</span>() dto: <span class="cls">CreateOrderDto</span>, <span class="dec">@CurrentUser</span>() user: <span class="cls">User</span>) {
    <span class="kw">return</span> <span class="kw">this</span>.commandBus.<span class="fn">execute</span>(
      <span class="kw">new</span> <span class="cls">CreateOrderCommand</span>(user.id, dto.items, dto.addressId),
    );
  }

  <span class="dec">@Get</span>()
  <span class="fn">findAll</span>(
    <span class="dec">@CurrentUser</span>() user: <span class="cls">User</span>,
    <span class="dec">@Query</span>(<span class="str">'page'</span>) page = <span class="num">1</span>,
    <span class="dec">@Query</span>(<span class="str">'limit'</span>) limit = <span class="num">10</span>,
  ) {
    <span class="kw">return</span> <span class="kw">this</span>.queryBus.<span class="fn">execute</span>(
      <span class="kw">new</span> <span class="cls">GetUserOrdersQuery</span>(user.id, +page, +limit),
    );
  }
}</pre>
    </div>

    <h3>Module'da CQRS Kayıt</h3>
    <div class="code-wrap">
      <div class="code-title">src/orders/orders.module.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">CqrsModule</span> } <span class="kw">from</span> <span class="str">'@nestjs/cqrs'</span>;

<span class="dec">@Module</span>({
  imports: [<span class="cls">CqrsModule</span>],
  controllers: [<span class="cls">OrdersController</span>],
  providers: [
    <span class="cmt">// Tüm handler'ları buraya ekle</span>
    <span class="cls">CreateOrderHandler</span>,
    <span class="cls">GetUserOrdersHandler</span>,
    <span class="cls">OrderCreatedHandler</span>,  <span class="cmt">// Event handler</span>
    <span class="cls">OrdersRepository</span>,
  ],
})
<span class="kw">export class</span> <span class="cls">OrdersModule</span> {}</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 17 -->
  <section class="section" id="s17">
    <div class="section-label">
      <span class="sec-num">17</span>
      <span class="sec-badge badge-uzman">Uzman</span>
    </div>
    <h2>Testing — Unit &amp; E2E</h2>
    <p class="intro">
      NestJS, Jest ile entegre çalışır. Unit testlerde bağımlılıkları mock'layarak sadece test
      edilen birimi izole ederiz. E2E testlerde uygulamanın tamamını ayağa kaldırıp HTTP
      istekleriyle davranışı doğrularız.
    </p>

    <h3>Unit Test — Service</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/users.service.spec.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Test</span>, <span class="cls">TestingModule</span> } <span class="kw">from</span> <span class="str">'@nestjs/testing'</span>;
<span class="kw">import</span> { <span class="cls">getRepositoryToken</span> } <span class="kw">from</span> <span class="str">'@nestjs/typeorm'</span>;
<span class="kw">import</span> { <span class="cls">NotFoundException</span>, <span class="cls">ConflictException</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

describe(<span class="str">'UsersService'</span>, () => {
  <span class="kw">let</span> service: <span class="cls">UsersService</span>;

  <span class="cmt">// Repository metodlarını mock'la — gerçek DB bağlantısı yok</span>
  <span class="kw">const</span> mockRepo = {
    find:         jest.<span class="fn">fn</span>(),
    findOneBy:    jest.<span class="fn">fn</span>(),
    findAndCount: jest.<span class="fn">fn</span>(),
    create:       jest.<span class="fn">fn</span>(),
    save:         jest.<span class="fn">fn</span>(),
    remove:       jest.<span class="fn">fn</span>(),
  };

  <span class="fn">beforeEach</span>(<span class="kw">async</span> () => {
    <span class="kw">const</span> module: <span class="cls">TestingModule</span> = <span class="kw">await</span> <span class="cls">Test</span>.<span class="fn">createTestingModule</span>({
      providers: [
        <span class="cls">UsersService</span>,
        {
          provide: <span class="fn">getRepositoryToken</span>(<span class="cls">User</span>),
          useValue: mockRepo,
        },
      ],
    }).<span class="fn">compile</span>();

    service = module.<span class="fn">get</span><<span class="cls">UsersService</span>>(<span class="cls">UsersService</span>);
    <span class="cmt">// Her testten önce mock'ları sıfırla</span>
    jest.<span class="fn">clearAllMocks</span>();
  });

  describe(<span class="str">'findOne'</span>, () => {
    it(<span class="str">'kullanıcı bulunursa döndürür'</span>, <span class="kw">async</span> () => {
      <span class="kw">const</span> user = { id: <span class="num">1</span>, name: <span class="str">'Ali'</span>, email: <span class="str">'ali@test.com'</span> };
      mockRepo.findOneBy.<span class="fn">mockResolvedValue</span>(user);

      <span class="kw">const</span> result = <span class="kw">await</span> service.<span class="fn">findOne</span>(<span class="num">1</span>);

      expect(result).<span class="fn">toEqual</span>(user);
      expect(mockRepo.findOneBy).<span class="fn">toHaveBeenCalledWith</span>({ id: <span class="num">1</span> });
      expect(mockRepo.findOneBy).<span class="fn">toHaveBeenCalledTimes</span>(<span class="num">1</span>);
    });

    it(<span class="str">'kullanıcı yoksa NotFoundException fırlatır'</span>, <span class="kw">async</span> () => {
      mockRepo.findOneBy.<span class="fn">mockResolvedValue</span>(<span class="kw">null</span>);

      <span class="kw">await</span> expect(service.<span class="fn">findOne</span>(<span class="num">999</span>))
        .rejects
        .<span class="fn">toThrow</span>(<span class="cls">NotFoundException</span>);
    });
  });

  describe(<span class="str">'create'</span>, () => {
    it(<span class="str">'email benzersizse kullanıcı oluşturur'</span>, <span class="kw">async</span> () => {
      <span class="kw">const</span> dto = { name: <span class="str">'Veli'</span>, email: <span class="str">'veli@test.com'</span>, password: <span class="str">'Pass1!'</span> };
      <span class="kw">const</span> saved = { id: <span class="num">2</span>, ...dto };

      mockRepo.findOneBy.<span class="fn">mockResolvedValue</span>(<span class="kw">null</span>);  <span class="cmt">// email yok</span>
      mockRepo.create.<span class="fn">mockReturnValue</span>(saved);
      mockRepo.save.<span class="fn">mockResolvedValue</span>(saved);

      <span class="kw">const</span> result = <span class="kw">await</span> service.<span class="fn">create</span>(dto <span class="kw">as any</span>);
      expect(result.id).<span class="fn">toBe</span>(<span class="num">2</span>);
    });

    it(<span class="str">'email varsa ConflictException fırlatır'</span>, <span class="kw">async</span> () => {
      mockRepo.findOneBy.<span class="fn">mockResolvedValue</span>({ id: <span class="num">1</span> });  <span class="cmt">// email mevcut</span>

      <span class="kw">await</span> expect(service.<span class="fn">create</span>({ email: <span class="str">'var@test.com'</span> } <span class="kw">as any</span>))
        .rejects
        .<span class="fn">toThrow</span>(<span class="cls">ConflictException</span>);
    });
  });
});</pre>
    </div>

    <h3>Unit Test — Controller</h3>
    <div class="code-wrap">
      <div class="code-title">src/users/users.controller.spec.ts</div>
      <pre>describe(<span class="str">'UsersController'</span>, () => {
  <span class="kw">let</span> controller: <span class="cls">UsersController</span>;
  <span class="kw">let</span> service: jest.<span class="cls">Mocked</span><<span class="cls">UsersService</span>>;

  <span class="fn">beforeEach</span>(<span class="kw">async</span> () => {
    <span class="kw">const</span> module = <span class="kw">await</span> <span class="cls">Test</span>.<span class="fn">createTestingModule</span>({
      controllers: [<span class="cls">UsersController</span>],
      providers: [{
        provide: <span class="cls">UsersService</span>,
        useValue: {
          findAll: jest.<span class="fn">fn</span>(),
          findOne: jest.<span class="fn">fn</span>(),
          create: jest.<span class="fn">fn</span>(),
        },
      }],
    }).<span class="fn">compile</span>();

    controller = module.<span class="fn">get</span>(<span class="cls">UsersController</span>);
    service    = module.<span class="fn">get</span>(<span class="cls">UsersService</span>);
  });

  it(<span class="str">'findAll servisi çağırır ve sonucu döndürür'</span>, <span class="kw">async</span> () => {
    <span class="kw">const</span> mockUsers = [{ id: <span class="num">1</span>, name: <span class="str">'Ali'</span> }];
    service.findAll.<span class="fn">mockResolvedValue</span>(mockUsers <span class="kw">as any</span>);

    <span class="kw">const</span> result = <span class="kw">await</span> controller.<span class="fn">findAll</span>();
    expect(result).<span class="fn">toEqual</span>(mockUsers);
    expect(service.findAll).<span class="fn">toHaveBeenCalledTimes</span>(<span class="num">1</span>);
  });
});</pre>
    </div>

    <h3>E2E Test</h3>
    <div class="code-wrap">
      <div class="code-title">test/users.e2e-spec.ts</div>
      <pre><span class="kw">import</span> * <span class="kw">as</span> request <span class="kw">from</span> <span class="str">'supertest'</span>;
<span class="kw">import</span> { <span class="cls">Test</span> } <span class="kw">from</span> <span class="str">'@nestjs/testing'</span>;
<span class="kw">import</span> { <span class="cls">INestApplication</span>, <span class="cls">ValidationPipe</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;

describe(<span class="str">'Users (e2e)'</span>, () => {
  <span class="kw">let</span> app: <span class="cls">INestApplication</span>;
  <span class="kw">let</span> jwtToken: <span class="typ">string</span>;

  <span class="fn">beforeAll</span>(<span class="kw">async</span> () => {
    <span class="kw">const</span> moduleRef = <span class="kw">await</span> <span class="cls">Test</span>.<span class="fn">createTestingModule</span>({
      imports: [<span class="cls">AppModule</span>],
    }).<span class="fn">compile</span>();

    app = moduleRef.<span class="fn">createNestApplication</span>();
    app.<span class="fn">useGlobalPipes</span>(<span class="kw">new</span> <span class="cls">ValidationPipe</span>({ whitelist: <span class="kw">true</span>, transform: <span class="kw">true</span> }));
    <span class="kw">await</span> app.<span class="fn">init</span>();

    <span class="cmt">// Önce login → token al</span>
    <span class="kw">const</span> res = <span class="kw">await</span> <span class="fn">request</span>(app.<span class="fn">getHttpServer</span>())
      .<span class="fn">post</span>(<span class="str">'/auth/login'</span>)
      .<span class="fn">send</span>({ email: <span class="str">'admin@test.com'</span>, password: <span class="str">'Admin1234!'</span> });

    jwtToken = res.body.accessToken;
  });

  <span class="fn">afterAll</span>(<span class="kw">async</span> () => <span class="kw">await</span> app.<span class="fn">close</span>());

  it(<span class="str">'GET /users → 200 ve dizi döner'</span>, () =>
    <span class="fn">request</span>(app.<span class="fn">getHttpServer</span>())
      .<span class="fn">get</span>(<span class="str">'/users'</span>)
      .<span class="fn">set</span>(<span class="str">'Authorization'</span>, <span class="str">`Bearer ${jwtToken}`</span>)
      .<span class="fn">expect</span>(<span class="num">200</span>)
      .<span class="fn">expect</span>((res) => expect(<span class="cls">Array</span>.<span class="fn">isArray</span>(res.body.data)).<span class="fn">toBe</span>(<span class="kw">true</span>)),
  );

  it(<span class="str">'POST /users → 201 ve yeni kullanıcı döner'</span>, () =>
    <span class="fn">request</span>(app.<span class="fn">getHttpServer</span>())
      .<span class="fn">post</span>(<span class="str">'/users'</span>)
      .<span class="fn">set</span>(<span class="str">'Authorization'</span>, <span class="str">`Bearer ${jwtToken}`</span>)
      .<span class="fn">send</span>({
        name: <span class="str">'Test Kullanıcı'</span>,
        email: <span class="str">`test${Date.now()}@mail.com`</span>,
        password: <span class="str">'TestPass1!'</span>,
        age: <span class="num">25</span>,
        role: <span class="str">'user'</span>,
      })
      .<span class="fn">expect</span>(<span class="num">201</span>)
      .<span class="fn">expect</span>((res) => {
        expect(res.body.data.email).<span class="fn">toContain</span>(<span class="str">'test'</span>);
        expect(res.body.data.password).<span class="fn">toBeUndefined</span>();  <span class="cmt">// şifre dönmemeli</span>
      }),
  );

  it(<span class="str">'POST /users → 400 geçersiz email'</span>, () =>
    <span class="fn">request</span>(app.<span class="fn">getHttpServer</span>())
      .<span class="fn">post</span>(<span class="str">'/users'</span>)
      .<span class="fn">set</span>(<span class="str">'Authorization'</span>, <span class="str">`Bearer ${jwtToken}`</span>)
      .<span class="fn">send</span>({ name: <span class="str">'x'</span>, email: <span class="str">'gecersiz-email'</span> })
      .<span class="fn">expect</span>(<span class="num">400</span>),
  );

  it(<span class="str">'GET /users/:id → 404 olmayan ID'</span>, () =>
    <span class="fn">request</span>(app.<span class="fn">getHttpServer</span>())
      .<span class="fn">get</span>(<span class="str">'/users/999999'</span>)
      .<span class="fn">set</span>(<span class="str">'Authorization'</span>, <span class="str">`Bearer ${jwtToken}`</span>)
      .<span class="fn">expect</span>(<span class="num">404</span>),
  );
});</pre>
    </div>
  </section>

  <hr class="divider">

  <!-- BÖLÜM 18 -->
  <section class="section" id="s18">
    <div class="section-label">
      <span class="sec-num">18</span>
      <span class="sec-badge badge-uzman">Uzman</span>
    </div>
    <h2>Deployment &amp; Docker &amp; Production</h2>
    <p class="intro">
      Bir NestJS uygulamasını production'a almak için Dockerfile, docker-compose, güvenlik ayarları
      ve sağlık kontrolü gerekir. Multi-stage build ile küçük, güvenli imajlar oluşturulur.
    </p>

    <h3>Multi-Stage Dockerfile</h3>
    <div class="code-wrap">
      <div class="code-title">Dockerfile</div>
      <pre><span class="cmt"># ---- Stage 1: build ----</span>
FROM node:20-alpine AS builder
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build   <span class="cmt"># dist/ klasörünü üretir</span>
RUN npm prune --production  <span class="cmt"># devDependencies'i kaldır</span>

<span class="cmt"># ---- Stage 2: production ----</span>
FROM node:20-alpine AS production
WORKDIR /app

<span class="cmt"># Güvenlik: root olmayan kullanıcı oluştur</span>
RUN addgroup -S nestjs && adduser -S nestjs -G nestjs

<span class="cmt"># Sadece gerekli dosyaları kopyala</span>
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/package.json ./

USER nestjs

ENV NODE_ENV=production
EXPOSE 3001

HEALTHCHECK --interval=30s --timeout=5s --start-period=10s \
  CMD wget -qO- http://localhost:3001/health || exit 1

CMD ["node", "dist/main"]</pre>
    </div>

    <h3>docker-compose.yml</h3>
    <div class="code-wrap">
      <div class="code-title">docker-compose.yml</div>
      <pre>version: '3.9'

services:
  api:
    build:
      context: .
      target: production
    ports:
      - '3001:3001'
    env_file: .env.production
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_started
    restart: unless-stopped

  postgres:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASS}
      POSTGRES_DB: ${DB_NAME}
    volumes:
      - pgdata:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${DB_USER}"]
      interval: 10s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    command: redis-server --requirepass ${REDIS_PASS}
    volumes:
      - redisdata:/data

volumes:
  pgdata:
  redisdata:</pre>
    </div>

    <h3>Production main.ts</h3>
    <div class="code-wrap">
      <div class="code-title">src/main.ts — güvenlik paketleri dahil</div>
      <pre>npm install helmet compression @nestjs/throttler</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/main.ts</div>
      <pre><span class="kw">import</span> * <span class="kw">as</span> helmet <span class="kw">from</span> <span class="str">'helmet'</span>;
<span class="kw">import</span> * <span class="kw">as</span> compression <span class="kw">from</span> <span class="str">'compression'</span>;

<span class="kw">async function</span> <span class="fn">bootstrap</span>() {
  <span class="kw">const</span> app = <span class="kw">await</span> <span class="cls">NestFactory</span>.<span class="fn">create</span>(<span class="cls">AppModule</span>, {
    <span class="cmt">// Production'da hata stack'ini gizle</span>
    logger: isDev ? [<span class="str">'log'</span>, <span class="str">'debug'</span>, <span class="str">'error'</span>, <span class="str">'warn'</span>] : [<span class="str">'error'</span>, <span class="str">'warn'</span>],
  });

  <span class="cmt">// Güvenlik HTTP header'ları (XSS, clickjacking, MIME sniffing...)</span>
  app.<span class="fn">use</span>(<span class="fn">helmet</span>());

  <span class="cmt">// Gzip compression — response boyutunu %60-80 küçültür</span>
  app.<span class="fn">use</span>(<span class="fn">compression</span>());

  <span class="cmt">// CORS — sadece güvenilen origin'e izin ver</span>
  app.<span class="fn">enableCors</span>({
    origin: process.env.ALLOWED_ORIGIN,
    credentials: <span class="kw">true</span>,
  });

  app.<span class="fn">setGlobalPrefix</span>(<span class="str">'api'</span>);

  app.<span class="fn">useGlobalPipes</span>(<span class="kw">new</span> <span class="cls">ValidationPipe</span>({
    whitelist: <span class="kw">true</span>,
    forbidNonWhitelisted: <span class="kw">true</span>,
    transform: <span class="kw">true</span>,
  }));

  app.<span class="fn">useGlobalFilters</span>(<span class="kw">new</span> <span class="cls">AllExceptionsFilter</span>());
  app.<span class="fn">useGlobalInterceptors</span>(<span class="kw">new</span> <span class="cls">TransformInterceptor</span>());

  <span class="kw">const</span> port = process.env.PORT || <span class="num">3001</span>;
  <span class="kw">await</span> app.<span class="fn">listen</span>(port);
}
<span class="fn">bootstrap</span>();</pre>
    </div>

    <h3>Health Check Endpoint</h3>
    <div class="code-wrap">
      <div class="code-title">terminal + health module</div>
      <pre>npm install @nestjs/terminus</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">src/health/health.controller.ts</div>
      <pre><span class="kw">import</span> { <span class="cls">Controller</span>, <span class="cls">Get</span> } <span class="kw">from</span> <span class="str">'@nestjs/common'</span>;
<span class="kw">import</span> {
  <span class="cls">HealthCheck</span>, <span class="cls">HealthCheckService</span>,
  <span class="cls">TypeOrmHealthIndicator</span>, <span class="cls">MemoryHealthIndicator</span>,
} <span class="kw">from</span> <span class="str">'@nestjs/terminus'</span>;

<span class="dec">@Controller</span>(<span class="str">'health'</span>)
<span class="kw">export class</span> <span class="cls">HealthController</span> {
  <span class="kw">constructor</span>(
    <span class="kw">private</span> health: <span class="cls">HealthCheckService</span>,
    <span class="kw">private</span> db: <span class="cls">TypeOrmHealthIndicator</span>,
    <span class="kw">private</span> memory: <span class="cls">MemoryHealthIndicator</span>,
  ) {}

  <span class="dec">@Get</span>()
  <span class="dec">@HealthCheck</span>()
  <span class="fn">check</span>() {
    <span class="kw">return</span> <span class="kw">this</span>.health.<span class="fn">check</span>([
      () => <span class="kw">this</span>.db.<span class="fn">pingCheck</span>(<span class="str">'database'</span>),
      () => <span class="kw">this</span>.memory.<span class="fn">checkHeap</span>(<span class="str">'memory_heap'</span>, <span class="num">200</span> * <span class="num">1024</span> * <span class="num">1024</span>),  <span class="cmt">// 200MB</span>
    ]);
  }
}</pre>
    </div>

    <h3>Migration — Production'da Veritabanı Değişiklikleri</h3>
    <div class="code-wrap">
      <div class="code-title">migration komutları</div>
      <pre><span class="cmt"># Migration oluştur</span>
npm run typeorm migration:generate src/migrations/AddUserRole

<span class="cmt"># Bekleyen migration'ları çalıştır</span>
npm run typeorm migration:run

<span class="cmt"># Son migration'ı geri al</span>
npm run typeorm migration:revert</pre>
    </div>

    <div class="code-wrap">
      <div class="code-title">package.json — migration script</div>
      <pre>"scripts": {
  "typeorm": "typeorm-ts-node-commonjs -d src/datasource.ts",
  "build": "nest build",
  "start:prod": "node dist/main"
}</pre>
    </div>

    <h3>Production Kontrol Listesi</h3>
    <div class="callout ok">
      <strong>Deployment öncesi şunları kontrol et:</strong><br><br>
      <strong>Güvenlik</strong> — JWT_SECRET en az 64 karakter. .env.production hiçbir zaman git'e commit edilmez.<br>
      <strong>Veritabanı</strong> — synchronize: false. Migration'lar elle yönetilir.<br>
      <strong>Rate Limiting</strong> — @nestjs/throttler ile brute-force koruması.<br>
      <strong>CORS</strong> — Sadece frontend domain'i izin listesinde.<br>
      <strong>HTTPS</strong> — TLS/SSL sertifikası (Let's Encrypt veya load balancer'da).<br>
      <strong>Loglama</strong> — Winston veya Pino ile structured log (JSON formatı).<br>
      <strong>Health Check</strong> — /health endpoint'i (Kubernetes liveness/readiness probe).<br>
      <strong>Graceful Shutdown</strong> — SIGTERM sinyalinde aktif bağlantılar temizlenir.
    </div>

    <div class="code-wrap">
      <div class="code-title">graceful shutdown — main.ts</div>
      <pre><span class="kw">await</span> app.<span class="fn">listen</span>(port);

<span class="cmt">// SIGTERM (Docker stop, Kubernetes pod termination)</span>
process.<span class="fn">on</span>(<span class="str">'SIGTERM'</span>, <span class="kw">async</span> () => {
  console.<span class="fn">log</span>(<span class="str">'SIGTERM alındı — graceful shutdown...'</span>);
  <span class="kw">await</span> app.<span class="fn">close</span>();
  process.<span class="fn">exit</span>(<span class="num">0</span>);
});</pre>
    </div>
  </section>

</main>

<script>
  const links = document.querySelectorAll('#sidebar a');
  const sections = document.querySelectorAll('section.section[id]');

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          links.forEach((l) => l.classList.remove('active'));
          const active = document.querySelector(`#sidebar a[href="#${entry.target.id}"]`);
          if (active) active.classList.add('active');
        }
      });
    },
    { rootMargin: '-20% 0px -75% 0px' }
  );

  sections.forEach((s) => observer.observe(s));
</script>
</body>
</html>
