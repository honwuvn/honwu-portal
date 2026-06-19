<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Honwu Vietnam 內部平台 MVP</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <div id="loginView" class="login-view">
    <div class="login-nature"></div>
    <section class="login-card">
      <div class="lang-switch login-lang">
        <button data-lang="zh" class="active">繁中</button>
        <button data-lang="vi">Tiếng Việt</button>
        <button data-lang="en">English</button>
      </div>
      <img src="assets/honwu-logo.jpg" alt="Honwu Vietnam Co., Ltd." class="login-logo" />
      <p class="eyebrow">Sustainable Packaging Solutions</p>
      <h1 data-i18n="loginTitle">公司內部平台</h1>
      <p data-i18n="loginDesc">永續包裝、綠色印刷、內部營運的一站式入口。</p>
      <label data-i18n="userName">使用者名稱</label>
      <input id="loginName" value="王小明" />
      <label data-i18n="userRole">使用者角色</label>
      <select id="loginRole"></select>
      <button id="loginBtn" class="btn primary full" data-i18n="loginBtn">登入平台</button>
      <small data-i18n="loginNote">此網頁 MVP 可直接開啟使用，資料暫存在瀏覽器 localStorage。</small>
    </section>
  </div>

  <div id="appView" class="app hidden">
    <aside class="sidebar">
      <div class="brand">
        <img src="assets/honwu-logo.jpg" alt="Honwu Vietnam Co., Ltd." />
      </div>
      <nav id="nav"></nav>
      <div class="eco-card">
        <div class="leaf-icon">♧</div>
        <strong data-i18n="ecoTitle">我們致力於</strong>
        <span data-i18n="ecoSlogan">永續包裝・綠色未來</span>
        <small data-i18n="ecoDesc">減少環境影響，共創美好未來</small>
      </div>
      <button id="logoutBtn" class="btn ghost logout" data-i18n="logout">登出</button>
    </aside>

    <main class="main">
      <header class="topbar">
        <div id="searchText" class="search">⌕ 搜尋公告、表單、客戶、課程...</div>
        <div class="top-actions">
          <div class="lang-switch">
            <button data-lang="zh" class="active">繁中</button>
            <button data-lang="vi">VI</button>
            <button data-lang="en">EN</button>
          </div>
          <span class="icon">🔔<b>3</b></span>
          <span class="icon">✉</span>
          <div class="user">
            <div id="avatar" class="avatar">王</div>
            <div><strong id="currentUser">王小明</strong><select id="roleSwitcher"></select></div>
          </div>
        </div>
      </header>

      <section class="hero">
        <div>
          <p class="eyebrow">Honwu Vietnam Co., Ltd.</p>
          <h1 id="greeting">早安，王小明！</h1>
          <p id="heroDesc">今天是美好的一天，讓我們一起為永續未來努力！</p>
        </div>
        <div class="hero-text">
          <strong>Sustainable<br/>Packaging Solutions</strong>
          <span id="heroSlogan">永續包裝・綠色未來</span>
        </div>
      </section>

      <section id="content"></section>
      <footer id="footerText">🌿 越南虹育・永續包裝・共創綠色未來</footer>
    </main>
  </div>

  <template id="dashboardTpl">
    <div class="stats">
      <article class="stat"><span class="green">📅</span><div><span data-i18n="todaySchedule">今日行程</span><strong data-count="events">0</strong><small data-i18n="scheduleUnit">個行程</small></div></article>
      <article class="stat"><span class="orange">📋</span><div><span data-i18n="todoItems">待辦事項</span><strong data-count="todos">0</strong><small data-i18n="todoUnit">件待處理</small></div></article>
      <article class="stat"><span class="blue">🧩</span><div><span data-i18n="pendingApproval">待簽核</span><strong data-count="approvals">0</strong><small data-i18n="approvalUnit">件待簽核</small></div></article>
      <article class="stat"><span class="green">🍃</span><div><span data-i18n="sustainability">永續績效</span><strong>84%</strong><small data-i18n="carbonGoal">減碳目標達成率</small></div></article>
    </div>
    <div class="dashboard-grid">
      <section class="panel"><div class="panel-head"><h2 data-i18n="todayScheduleIcon">📅 今日行程</h2><button data-open="info" data-i18n="viewAll">查看全部</button></div><div id="scheduleList" class="timeline"></div></section>
      <section class="panel"><div class="panel-head"><h2 data-i18n="companyNewsIcon">📣 公司公告</h2><button data-open="info" data-i18n="viewAll">查看全部</button></div><div id="announcementList"></div></section>
      <section class="panel progress-panel"><div class="panel-head"><h2 data-i18n="learningProgressIcon">🍃 我的學習進度</h2><button data-open="learning" data-i18n="viewAll">查看全部</button></div><div class="ring"><strong>72%</strong><span data-i18n="completed">已完成</span></div><ul><li><span data-i18n="completedCourses">已完成課程</span> <b>18</b></li><li><span data-i18n="activeCourses">進行中課程</span> <b>7</b></li><li><span data-i18n="pendingCourses">待完成課程</span> <b>5</b></li></ul><button class="btn primary" data-open="learning" data-i18n="goLearning">前往學習中心</button></section>
      <section class="panel quick"><h2 data-i18n="quickTools">快速功能</h2><div class="quick-grid"><button data-open="hr" data-i18n="leaveRequest">請假申請</button><button data-open="finance" data-i18n="expenseRequest">費用申請</button><button data-open="purchase" data-i18n="purchaseRequest">採購申請</button><button data-open="settings" data-i18n="approvalCenter">簽核中心</button><button data-open="sales" data-i18n="customerManagement">客戶管理</button><button data-open="info" data-i18n="documentCenter">文件中心</button></div></section>
      <section class="panel modules"><h2 data-i18n="commonModules">常用模組</h2><div class="module-cards"><button data-open="learning"><span>🌱</span><em data-i18n="learning">學習與訓練</em></button><button data-open="purchase"><span>📦</span><em data-i18n="purchase">採購工具</em></button><button data-open="sales"><span>🤝</span><em data-i18n="sales">業務專用 CRM</em></button><button data-open="finance"><span>📈</span><em data-i18n="finance">財務中心</em></button></div></section>
    </div>
  </template>

  <template id="moduleTpl">
    <div class="module-header"><div><h2 id="moduleTitle"></h2><p id="moduleDesc"></p></div><div><button id="addBtn" class="btn primary">新增</button><button id="exportBtn" class="btn ghost">匯出 JSON</button></div></div>
    <div class="panel"><div class="toolbar"><input id="searchBox" /><button id="resetBtn" class="btn ghost">重設示範資料</button></div><div class="table-wrap"><table><thead></thead><tbody></tbody></table></div></div>
  </template>

  <template id="formTpl">
    <form id="dynamicForm" class="panel form-panel"></form>
  </template>

  <div id="toast"></div>
  <script src="app.js"></script>
</body>
</html>
