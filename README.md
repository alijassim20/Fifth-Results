# Fifth-Results
نتائج الخامس
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>نتائج الطلاب - اعدادية التآخي للبنين</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background-color: #0a0a0f;
    color: #e8e0d0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    min-height: 100vh;
    direction: rtl;
  }

  .page { display: none; }
  .page.active { display: block; }

  /* LOGIN PAGE */
  #loginPage {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, #0a0a0f 0%, #111122 50%, #0a0a0f 100%);
    padding: 20px;
  }

  .school-header {
    text-align: center;
    margin-bottom: 40px;
  }

  .school-name {
    font-size: 1.6rem;
    font-weight: 700;
    color: #c8a84b;
    letter-spacing: 1px;
    line-height: 1.4;
  }

  .ministry-text {
    font-size: 0.85rem;
    color: #888;
    margin-bottom: 6px;
    letter-spacing: 0.5px;
  }

  .year-text {
    font-size: 0.9rem;
    color: #c8a84b;
    margin-top: 8px;
    font-weight: 600;
  }

  .login-box {
    background: #12121e;
    border: 1px solid #2a2a3a;
    border-radius: 16px;
    padding: 40px 36px;
    width: 100%;
    max-width: 380px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  }

  .login-title {
    font-size: 1.15rem;
    color: #c8a84b;
    text-align: center;
    margin-bottom: 28px;
    font-weight: 600;
  }

  .input-group {
    margin-bottom: 20px;
  }

  .input-group label {
    display: block;
    font-size: 0.85rem;
    color: #aaa;
    margin-bottom: 8px;
  }

  .input-group input {
    width: 100%;
    background: #1a1a28;
    border: 1px solid #333;
    border-radius: 8px;
    padding: 12px 14px;
    color: #e8e0d0;
    font-size: 1rem;
    outline: none;
    transition: border-color 0.2s;
    text-align: center;
    letter-spacing: 2px;
    font-family: monospace;
  }

  .input-group input:focus {
    border-color: #c8a84b;
  }

  .login-btn {
    width: 100%;
    background: linear-gradient(135deg, #b8941e, #c8a84b);
    border: none;
    border-radius: 8px;
    padding: 14px;
    color: #0a0a0f;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    transition: opacity 0.2s;
    margin-top: 4px;
  }

  .login-btn:hover { opacity: 0.9; }

  .error-msg {
    color: #e05555;
    font-size: 0.85rem;
    text-align: center;
    margin-top: 12px;
    display: none;
  }

  /* RESULTS PAGE */
  #resultsPage {
    min-height: 100vh;
    background: #0a0a0f;
    padding: 20px;
    padding-bottom: 40px;
  }

  .results-header {
    background: linear-gradient(135deg, #111122, #1a1a2e);
    border-bottom: 2px solid #c8a84b;
    padding: 20px;
    text-align: center;
    margin-bottom: 28px;
    border-radius: 12px;
  }

  .results-header .school-name-small {
    font-size: 1rem;
    color: #c8a84b;
    font-weight: 700;
  }

  .results-header .ministry-small {
    font-size: 0.75rem;
    color: #888;
    margin-bottom: 4px;
  }

  .student-info-card {
    background: #12121e;
    border: 1px solid #2a2a3a;
    border-radius: 12px;
    padding: 20px 24px;
    margin-bottom: 24px;
    max-width: 700px;
    margin-left: auto;
    margin-right: auto;
  }

  .student-name-display {
    font-size: 1.3rem;
    font-weight: 700;
    color: #c8a84b;
    margin-bottom: 8px;
  }

  .student-meta {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
  }

  .student-meta span {
    font-size: 0.85rem;
    color: #aaa;
  }

  .student-meta strong {
    color: #e8e0d0;
  }

  /* GRADES TABLE */
  .grades-container {
    max-width: 700px;
    margin: 0 auto;
    background: #000000;
    border-radius: 14px;
    overflow: hidden;
    border: 2px solid #c8a84b;
  }

  .grades-title {
    background: #c8a84b;
    color: #000;
    text-align: center;
    padding: 12px;
    font-size: 1rem;
    font-weight: 700;
  }

  table {
    width: 100%;
    border-collapse: collapse;
  }

  thead tr {
    background: #1a1000;
  }

  thead th {
    color: #ffffff;
    padding: 11px 10px;
    font-size: 0.82rem;
    font-weight: 600;
    text-align: center;
    border-bottom: 1px solid #333;
  }

  tbody tr {
    background: #000000;
    border-bottom: 1px solid #1a1a1a;
    transition: background 0.15s;
  }

  tbody tr:hover {
    background: #0d0d0d;
  }

  tbody tr:last-child {
    border-bottom: none;
  }

  tbody td {
    padding: 11px 10px;
    text-align: center;
    font-size: 0.9rem;
    color: #e8e0d0;
  }

  td.subject-name {
    color: #ffffff;
    font-weight: 600;
    text-align: right;
    padding-right: 16px;
  }

  td.grade-cell {
    color: #c8a84b;
    font-weight: 700;
    font-size: 1rem;
    font-family: monospace;
  }

  td.grade-cell.empty {
    color: #444;
  }

  .total-row {
    background: #1a1000 !important;
    border-top: 2px solid #c8a84b !important;
  }

  .total-row td {
    color: #c8a84b !important;
    font-weight: 700;
    font-size: 0.95rem;
  }

  .logout-btn {
    display: block;
    margin: 24px auto 0;
    background: transparent;
    border: 1px solid #444;
    border-radius: 8px;
    padding: 10px 28px;
    color: #888;
    font-size: 0.9rem;
    cursor: pointer;
    transition: all 0.2s;
  }

  .logout-btn:hover {
    border-color: #c8a84b;
    color: #c8a84b;
  }

  /* ADMIN PAGE */
  #adminPage {
    min-height: 100vh;
    background: #0a0a0f;
    padding: 20px;
    padding-bottom: 40px;
  }

  .admin-header {
    background: linear-gradient(135deg, #1a0000, #2a0a00);
    border-bottom: 2px solid #c8a84b;
    border-radius: 12px;
    padding: 20px;
    text-align: center;
    margin-bottom: 28px;
  }

  .admin-title {
    color: #c8a84b;
    font-size: 1.1rem;
    font-weight: 700;
  }

  .admin-subtitle {
    color: #888;
    font-size: 0.8rem;
    margin-top: 4px;
  }

  .search-box {
    max-width: 500px;
    margin: 0 auto 24px;
    display: flex;
    gap: 10px;
  }

  .search-box input {
    flex: 1;
    background: #12121e;
    border: 1px solid #333;
    border-radius: 8px;
    padding: 12px 14px;
    color: #e8e0d0;
    font-size: 0.95rem;
    outline: none;
    transition: border-color 0.2s;
    direction: rtl;
  }

  .search-box input:focus {
    border-color: #c8a84b;
  }

  .search-box button {
    background: #c8a84b;
    border: none;
    border-radius: 8px;
    padding: 12px 20px;
    color: #000;
    font-weight: 700;
    cursor: pointer;
    font-size: 0.9rem;
  }

  .search-results {
    max-width: 700px;
    margin: 0 auto;
  }

  .student-card-admin {
    background: #12121e;
    border: 1px solid #2a2a3a;
    border-radius: 10px;
    padding: 16px 20px;
    margin-bottom: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;
  }

  .student-card-admin .sname {
    font-size: 1rem;
    font-weight: 600;
    color: #e8e0d0;
  }

  .student-card-admin .sclass {
    font-size: 0.8rem;
    color: #888;
    margin-top: 3px;
  }

  .secret-badge {
    background: #1a1000;
    border: 1px solid #c8a84b;
    border-radius: 6px;
    padding: 6px 14px;
    color: #c8a84b;
    font-family: monospace;
    font-size: 1rem;
    font-weight: 700;
    letter-spacing: 2px;
  }

  .no-results {
    text-align: center;
    color: #666;
    padding: 30px;
    font-size: 0.9rem;
  }

  .all-students-table {
    max-width: 700px;
    margin: 0 auto;
    background: #12121e;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid #2a2a3a;
  }

  .all-students-table table {
    width: 100%;
  }

  .all-students-table thead th {
    background: #1a1a00;
    color: #c8a84b;
    padding: 10px 14px;
    font-size: 0.82rem;
    text-align: right;
  }

  .all-students-table tbody td {
    padding: 10px 14px;
    font-size: 0.88rem;
    text-align: right;
    border-bottom: 1px solid #1e1e2a;
    color: #e8e0d0;
  }

  .all-students-table tbody tr:hover {
    background: #1a1a28;
  }

  .code-cell {
    font-family: monospace;
    color: #c8a84b;
    font-weight: 700;
    letter-spacing: 1px;
  }

  .section-label {
    color: #c8a84b;
    font-size: 0.85rem;
    font-weight: 600;
    margin-bottom: 10px;
    max-width: 700px;
    margin-left: auto;
    margin-right: auto;
    padding: 0 4px;
  }
</style>
</head>
<body>

<!-- LOGIN PAGE -->
<div id="loginPage" class="page active">
  <div class="school-header">
    <div class="ministry-text">جمهورية العراق – وزارة التربية</div>
    <div class="ministry-text">المديرية العامة لتربية صلاح الدين – قسم تربية بيجي</div>
    <div class="school-name">اعدادية التآخي للبنين</div>
    <div class="year-text">سجل درجات الطلاب 2025 – 2026</div>
  </div>
  <div class="login-box">
    <div class="login-title">أدخل رمزك السري للاطلاع على نتيجتك</div>
    <div class="input-group">
      <label>الرمز السري</label>
      <input type="text" id="codeInput" placeholder="XXXXXXX" autocomplete="off" onkeydown="if(event.key==='Enter') doLogin()">
    </div>
    <button class="login-btn" onclick="doLogin()">دخول</button>
    <div class="error-msg" id="errorMsg">الرمز السري غير صحيح</div>
  </div>
</div>

<!-- RESULTS PAGE -->
<div id="resultsPage" class="page">
  <div class="results-header">
    <div class="ministry-small">جمهورية العراق – وزارة التربية | المديرية العامة لتربية صلاح الدين – قسم تربية بيجي</div>
    <div class="school-name-small">اعدادية التآخي للبنين &nbsp;|&nbsp; العام الدراسي 2025 – 2026</div>
  </div>

  <div class="student-info-card">
    <div class="student-name-display" id="displayName"></div>
    <div class="student-meta">
      <span>الصف والشعبة: <strong>الخامس العلمي</strong></span>
      <span>المدير: <strong>خالد رسول فهد</strong></span>
    </div>
  </div>

  <div class="grades-container">
    <div class="grades-title">نتائج الفصل الأول</div>
    <table>
      <thead>
        <tr>
          <th style="text-align:right; padding-right:16px;">المادة</th>
          <th>معدل الفصل الأول</th>
        </tr>
      </thead>
      <tbody id="gradesBody"></tbody>
    </table>
  </div>

  <button class="logout-btn" onclick="doLogout()">← رجوع</button>
</div>

<!-- ADMIN PAGE -->
<div id="adminPage" class="page">
  <div class="admin-header">
    <div class="admin-title">لوحة المدير – خالد رسول فهد</div>
    <div class="admin-subtitle">اعدادية التآخي للبنين | 2025 – 2026</div>
  </div>

  <div class="search-box">
    <input type="text" id="adminSearch" placeholder="ابحث باسم الطالب..." oninput="doSearch()">
    <button onclick="doSearch()">بحث</button>
  </div>

  <div class="search-results" id="searchResults"></div>

  <div class="section-label">جميع الطلاب ورموزهم السرية</div>
  <div class="all-students-table">
    <table>
      <thead>
        <tr>
          <th>الاسم</th>
          <th>الصف</th>
          <th>الرمز السري</th>
        </tr>
      </thead>
      <tbody id="allStudentsBody"></tbody>
    </table>
  </div>

  <button class="logout-btn" onclick="doLogout()">← خروج</button>
</div>

<script>
// ===== STUDENT DATA =====
const students = [
  { code: "SL2001", name: "أبو بكر ندا عباس", class: "الخامس العلمي", seq: 1, grades: { "التربية الإسلامية": 50, "اللغة العربية": 45, "اللغة الإنكليزية": 25, "الرياضيات": 26, "الفيزياء": 34, "الكيمياء": 38, "علم الأحياء": 33, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2002", name: "احمد اياد حمود", class: "الخامس العلمي", seq: 2, grades: { "التربية الإسلامية": 100, "اللغة العربية": 93, "اللغة الإنكليزية": 80, "الرياضيات": 84, "الفيزياء": 90, "الكيمياء": 86, "علم الأحياء": 94, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2003", name: "احمد رياض حميد", class: "الخامس العلمي", seq: 3, grades: { "التربية الإسلامية": 100, "اللغة العربية": 95, "اللغة الإنكليزية": 55, "الرياضيات": 50, "الفيزياء": 90, "الكيمياء": 76, "علم الأحياء": 61, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2004", name: "احمد علي احمد", class: "الخامس العلمي", seq: 4, grades: { "التربية الإسلامية": 100, "اللغة العربية": 86, "اللغة الإنكليزية": 75, "الرياضيات": 50, "الفيزياء": 95, "الكيمياء": 63, "علم الأحياء": 74, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2005", name: "احمد ماهر حميد نجرس", class: "الخامس العلمي", seq: 5, grades: { "التربية الإسلامية": 98, "اللغة العربية": 56, "اللغة الإنكليزية": 65, "الرياضيات": 32, "الفيزياء": 56, "الكيمياء": 57, "علم الأحياء": 51, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2006", name: "احمد نعيم كردي", class: "الخامس العلمي", seq: 6, grades: { "التربية الإسلامية": 98, "اللغة العربية": 72, "اللغة الإنكليزية": 50, "الرياضيات": 32, "الفيزياء": 60, "الكيمياء": 60, "علم الأحياء": 58, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2007", name: "إسحاق هشام صباح جمعة", class: "الخامس العلمي", seq: 7, grades: { "التربية الإسلامية": 100, "اللغة العربية": 53, "اللغة الإنكليزية": 60, "الرياضيات": 32, "الفيزياء": 50, "الكيمياء": 34, "علم الأحياء": 43, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2008", name: "اسد محمود عوض", class: "الخامس العلمي", seq: 8, grades: { "التربية الإسلامية": 98, "اللغة العربية": 75, "اللغة الإنكليزية": 65, "الرياضيات": 38, "الفيزياء": 60, "الكيمياء": 56, "علم الأحياء": 53, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2009", name: "بلال نمير محمد مطلك", class: "الخامس العلمي", seq: 9, grades: { "التربية الإسلامية": 95, "اللغة العربية": 56, "اللغة الإنكليزية": 60, "الرياضيات": 28, "الفيزياء": 70, "الكيمياء": 41, "علم الأحياء": 60, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2010", name: "حارث علي محمد خلف", class: "الخامس العلمي", seq: 10, grades: { "التربية الإسلامية": 100, "اللغة العربية": 97, "اللغة الإنكليزية": 97, "الرياضيات": 64, "الفيزياء": 95, "الكيمياء": 80, "علم الأحياء": 91, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2011", name: "حذيفة عدنان نايف", class: "الخامس العلمي", seq: 11, grades: { "التربية الإسلامية": 77, "اللغة العربية": 45, "اللغة الإنكليزية": 52, "الرياضيات": 36, "الفيزياء": 37, "الكيمياء": 50, "علم الأحياء": 50, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2012", name: "حسين احمد حسين", class: "الخامس العلمي", seq: 12, grades: { "التربية الإسلامية": 80, "اللغة العربية": 63, "اللغة الإنكليزية": 60, "الرياضيات": 40, "الفيزياء": 80, "الكيمياء": 51, "علم الأحياء": 52, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2013", name: "خالد حسن شرقي", class: "الخامس العلمي", seq: 13, grades: { "التربية الإسلامية": 100, "اللغة العربية": 90, "اللغة الإنكليزية": 75, "الرياضيات": 56, "الفيزياء": 75, "الكيمياء": 66, "علم الأحياء": 61, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2014", name: "خالد فاروق دحام", class: "الخامس العلمي", seq: 14, grades: { "التربية الإسلامية": 100, "اللغة العربية": 80, "اللغة الإنكليزية": 90, "الرياضيات": 53, "الفيزياء": 90, "الكيمياء": 86, "علم الأحياء": 85, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2015", name: "ريقان ثامر جدوع حلو", class: "الخامس العلمي", seq: 15, grades: { "التربية الإسلامية": 100, "اللغة العربية": 85, "اللغة الإنكليزية": 55, "الرياضيات": 52, "الفيزياء": 75, "الكيمياء": 81, "علم الأحياء": 81, "الحاسوب": null, "التربية الرياضية": 80, "التربية الفنية": 80 } },
  { code: "SL2016", name: "شجاع عامر ثابت", class: "الخامس العلمي", seq: 16, grades: { "التربية الإسلامية": 73, "اللغة العربية": 66, "اللغة الإنكليزية": 60, "الرياضيات": 26, "الفيزياء": 30, "الكيمياء": 43, "علم الأحياء": 54, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2017", name: "ضياء احسان علي", class: "الخامس العلمي", seq: 17, grades: { "التربية الإسلامية": 87, "اللغة العربية": 60, "اللغة الإنكليزية": 30, "الرياضيات": 28, "الفيزياء": 39, "الكيمياء": 38, "علم الأحياء": 41, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2018", name: "عبد الحق نجم عبد الله", class: "الخامس العلمي", seq: 18, grades: { "التربية الإسلامية": 95, "اللغة العربية": 60, "اللغة الإنكليزية": 60, "الرياضيات": 33, "الفيزياء": 80, "الكيمياء": 52, "علم الأحياء": 53, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2019", name: "عبد الرحمن طالل محمود", class: "الخامس العلمي", seq: 19, grades: { "التربية الإسلامية": 71, "اللغة العربية": 55, "اللغة الإنكليزية": 50, "الرياضيات": 29, "الفيزياء": 34, "الكيمياء": 35, "علم الأحياء": 50, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2020", name: "عبد الرحمن ياسر احميد", class: "الخامس العلمي", seq: 20, grades: { "التربية الإسلامية": 100, "اللغة العربية": 63, "اللغة الإنكليزية": 40, "الرياضيات": 53, "الفيزياء": 35, "الكيمياء": 54, "علم الأحياء": 54, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2021", name: "عبد الله عثمان عطية", class: "الخامس العلمي", seq: 21, grades: { "التربية الإسلامية": 100, "اللغة العربية": 85, "اللغة الإنكليزية": 95, "الرياضيات": 35, "الفيزياء": 90, "الكيمياء": 59, "علم الأحياء": 73, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2022", name: "عبد الله نزهان دخيل", class: "الخامس العلمي", seq: 22, grades: { "التربية الإسلامية": 85, "اللغة العربية": 66, "اللغة الإنكليزية": 40, "الرياضيات": 35, "الفيزياء": 36, "الكيمياء": 39, "علم الأحياء": 57, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2023", name: "علي حسين خلف", class: "الخامس العلمي", seq: 23, grades: { "التربية الإسلامية": 90, "اللغة العربية": 76, "اللغة الإنكليزية": 55, "الرياضيات": 42, "الفيزياء": 50, "الكيمياء": 40, "علم الأحياء": 44, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2024", name: "عمر احمد عبد الله", class: "الخامس العلمي", seq: 24, grades: { "التربية الإسلامية": 95, "اللغة العربية": 100, "اللغة الإنكليزية": 65, "الرياضيات": 39, "الفيزياء": 56, "الكيمياء": 43, "علم الأحياء": 50, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2025", name: "عمر ذاكر مصلح احميد", class: "الخامس العلمي", seq: 25, grades: { "التربية الإسلامية": 88, "اللغة العربية": 53, "اللغة الإنكليزية": 60, "الرياضيات": 45, "الفيزياء": 56, "الكيمياء": 35, "علم الأحياء": 30, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2026", name: "عمر قحطان فرحان", class: "الخامس العلمي", seq: 26, grades: { "التربية الإسلامية": 100, "اللغة العربية": 60, "اللغة الإنكليزية": 60, "الرياضيات": 28, "الفيزياء": 50, "الكيمياء": 41, "علم الأحياء": 50, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2027", name: "ليث علي احميد طه", class: "الخامس العلمي", seq: 27, grades: { "التربية الإسلامية": 100, "اللغة العربية": 68, "اللغة الإنكليزية": 72, "الرياضيات": 63, "الفيزياء": 80, "الكيمياء": 59, "علم الأحياء": 53, "الحاسوب": null, "التربية الرياضية": 80, "التربية الفنية": 80 } },
  { code: "SL2028", name: "محمد حسن موسى", class: "الخامس العلمي", seq: 28, grades: { "التربية الإسلامية": 67, "اللغة العربية": 53, "اللغة الإنكليزية": 25, "الرياضيات": 28, "الفيزياء": 95, "الكيمياء": 33, "علم الأحياء": 51, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2029", name: "محمد حسين خلف", class: "الخامس العلمي", seq: 29, grades: { "التربية الإسلامية": 100, "اللغة العربية": 83, "اللغة الإنكليزية": 85, "الرياضيات": 50, "الفيزياء": 80, "الكيمياء": 72, "علم الأحياء": 61, "الحاسوب": null, "التربية الرياضية": 80, "التربية الفنية": 80 } },
  { code: "SL2030", name: "محمد عبد الواحد عبد الله", class: "الخامس العلمي", seq: 30, grades: { "التربية الإسلامية": 100, "اللغة العربية": 75, "اللغة الإنكليزية": 70, "الرياضيات": 56, "الفيزياء": 90, "الكيمياء": 73, "علم الأحياء": 71, "الحاسوب": null, "التربية الرياضية": 90, "التربية الفنية": 90 } },
  { code: "SL2031", name: "محمد مراد خلف", class: "الخامس العلمي", seq: 31, grades: { "التربية الإسلامية": 70, "اللغة العربية": 68, "اللغة الإنكليزية": 55, "الرياضيات": 30, "الفيزياء": 30, "الكيمياء": 34, "علم الأحياء": 55, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2032", name: "معاوية إبراهيم شلال", class: "الخامس العلمي", seq: 32, grades: { "التربية الإسلامية": 93, "اللغة العربية": 68, "اللغة الإنكليزية": 95, "الرياضيات": 42, "الفيزياء": 95, "الكيمياء": 59, "علم الأحياء": 61, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2033", name: "منتظر دخيل احمد عبد الله", class: "الخامس العلمي", seq: 33, grades: { "التربية الإسلامية": 100, "اللغة العربية": 50, "اللغة الإنكليزية": 25, "الرياضيات": 30, "الفيزياء": 30, "الكيمياء": 33, "علم الأحياء": 29, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2034", name: "مهند مثنى احميد", class: "الخامس العلمي", seq: 34, grades: { "التربية الإسلامية": 95, "اللغة العربية": 80, "اللغة الإنكليزية": 60, "الرياضيات": 60, "الفيزياء": 85, "الكيمياء": 50, "علم الأحياء": 52, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2035", name: "مهند مكي احمد", class: "الخامس العلمي", seq: 35, grades: { "التربية الإسلامية": 100, "اللغة العربية": 100, "اللغة الإنكليزية": 97, "الرياضيات": 97, "الفيزياء": 100, "الكيمياء": 98, "علم الأحياء": 100, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2036", name: "يعقوب خلف عبد الله", class: "الخامس العلمي", seq: 36, grades: { "التربية الإسلامية": 93, "اللغة العربية": 68, "اللغة الإنكليزية": 55, "الرياضيات": 62, "الفيزياء": 90, "الكيمياء": 50, "علم الأحياء": 70, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2037", name: "يوسف فؤاد عكلة", class: "الخامس العلمي", seq: 37, grades: { "التربية الإسلامية": 100, "اللغة العربية": 60, "اللغة الإنكليزية": 65, "الرياضيات": 25, "الفيزياء": 60, "الكيمياء": 51, "علم الأحياء": 57, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2038", name: "يوسف محمد محمود", class: "الخامس العلمي", seq: 38, grades: { "التربية الإسلامية": 100, "اللغة العربية": 88, "اللغة الإنكليزية": 75, "الرياضيات": 67, "الفيزياء": 95, "الكيمياء": 53, "علم الأحياء": 55, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2039", name: "اثير جمال محمود فارس", class: "الخامس العلمي", seq: 39, grades: { "التربية الإسلامية": 90, "اللغة العربية": 90, "اللغة الإنكليزية": 98, "الرياضيات": 25, "الفيزياء": 50, "الكيمياء": 60, "علم الأحياء": 73, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2040", name: "احمد عمر شعيب", class: "الخامس العلمي", seq: 40, grades: { "التربية الإسلامية": 88, "اللغة العربية": 60, "اللغة الإنكليزية": 65, "الرياضيات": 35, "الفيزياء": 50, "الكيمياء": 42, "علم الأحياء": 54, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2041", name: "احمد لازم محمد محمود", class: "الخامس العلمي", seq: 41, grades: { "التربية الإسلامية": 50, "اللغة العربية": 50, "اللغة الإنكليزية": 60, "الرياضيات": 52, "الفيزياء": 50, "الكيمياء": 70, "علم الأحياء": 79, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2042", name: "انس عدنان دخيل", class: "الخامس العلمي", seq: 42, grades: { "التربية الإسلامية": 60, "اللغة العربية": 60, "اللغة الإنكليزية": 25, "الرياضيات": 32, "الفيزياء": 85, "الكيمياء": 35, "علم الأحياء": 33, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2043", name: "أنور رمضان حسن", class: "الخامس العلمي", seq: 43, grades: { "التربية الإسلامية": 57, "اللغة العربية": 40, "اللغة الإنكليزية": 60, "الرياضيات": 28, "الفيزياء": 25, "الكيمياء": 35, "علم الأحياء": 33, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2044", name: "أنور سمير حمد", class: "الخامس العلمي", seq: 44, grades: { "التربية الإسلامية": 88, "اللغة العربية": 60, "اللغة الإنكليزية": 50, "الرياضيات": 50, "الفيزياء": 25, "الكيمياء": 51, "علم الأحياء": 54, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2045", name: "بشير جاسم محمد خلف", class: "الخامس العلمي", seq: 45, grades: { "التربية الإسلامية": 85, "اللغة العربية": 52, "اللغة الإنكليزية": 50, "الرياضيات": 36, "الفيزياء": 30, "الكيمياء": 60, "علم الأحياء": 72, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2046", name: "رجب عماد رجب", class: "الخامس العلمي", seq: 46, grades: { "التربية الإسلامية": 100, "اللغة العربية": 80, "اللغة الإنكليزية": 95, "الرياضيات": 50, "الفيزياء": 50, "الكيمياء": 64, "علم الأحياء": 67, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2047", name: "رداد زياد خلف", class: "الخامس العلمي", seq: 47, grades: { "التربية الإسلامية": 94, "اللغة العربية": 25, "اللغة الإنكليزية": 75, "الرياضيات": 42, "الفيزياء": 30, "الكيمياء": 85, "علم الأحياء": 75, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2048", name: "سرمد إبراهيم مزهر", class: "الخامس العلمي", seq: 48, grades: { "التربية الإسلامية": 93, "اللغة العربية": 50, "اللغة الإنكليزية": 70, "الرياضيات": 29, "الفيزياء": 50, "الكيمياء": 40, "علم الأحياء": 51, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2049", name: "سفيان حسن محمود عواد", class: "الخامس العلمي", seq: 49, grades: { "التربية الإسلامية": 82, "اللغة العربية": 30, "اللغة الإنكليزية": 40, "الرياضيات": 29, "الفيزياء": 30, "الكيمياء": 43, "علم الأحياء": 70, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2050", name: "سلوان عنتر حمد", class: "الخامس العلمي", seq: 50, grades: { "التربية الإسلامية": 78, "اللغة العربية": 50, "اللغة الإنكليزية": 70, "الرياضيات": 52, "الفيزياء": 58, "الكيمياء": 35, "علم الأحياء": 50, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2051", name: "سيف برهان خزعل", class: "الخامس العلمي", seq: 51, grades: { "التربية الإسلامية": 100, "اللغة العربية": 80, "اللغة الإنكليزية": 95, "الرياضيات": 52, "الفيزياء": 85, "الكيمياء": 57, "علم الأحياء": 59, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2052", name: "طالل فرج عتيج", class: "الخامس العلمي", seq: 52, grades: { "التربية الإسلامية": 98, "اللغة العربية": 57, "اللغة الإنكليزية": 60, "الرياضيات": 26, "الفيزياء": 70, "الكيمياء": 39, "علم الأحياء": 50, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2053", name: "عبد الباري معد عيد", class: "الخامس العلمي", seq: 53, grades: { "التربية الإسلامية": 100, "اللغة العربية": 70, "اللغة الإنكليزية": 95, "الرياضيات": 50, "الفيزياء": 62, "الكيمياء": 43, "علم الأحياء": 55, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2054", name: "عبد الرحمن احمد شعيب", class: "الخامس العلمي", seq: 54, grades: { "التربية الإسلامية": 98, "اللغة العربية": 75, "اللغة الإنكليزية": 60, "الرياضيات": 35, "الفيزياء": 50, "الكيمياء": 51, "علم الأحياء": 51, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2055", name: "عبد الرحمن رعد خلف", class: "الخامس العلمي", seq: 55, grades: { "التربية الإسلامية": 85, "اللغة العربية": 60, "اللغة الإنكليزية": 25, "الرياضيات": 25, "الفيزياء": 25, "الكيمياء": 35, "علم الأحياء": 44, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2056", name: "عبد الرحمن عمار علي", class: "الخامس العلمي", seq: 56, grades: { "التربية الإسلامية": 85, "اللغة العربية": 70, "اللغة الإنكليزية": 70, "الرياضيات": 40, "الفيزياء": 50, "الكيمياء": 50, "علم الأحياء": 61, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2057", name: "عبد الرحمن ندا عباس", class: "الخامس العلمي", seq: 57, grades: { "التربية الإسلامية": 60, "اللغة العربية": 25, "اللغة الإنكليزية": 40, "الرياضيات": 27, "الفيزياء": 30, "الكيمياء": 42, "علم الأحياء": 43, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2058", name: "عبد السلام عبد الله عبد", class: "الخامس العلمي", seq: 58, grades: { "التربية الإسلامية": 100, "اللغة العربية": 95, "اللغة الإنكليزية": 95, "الرياضيات": 70, "الفيزياء": 95, "الكيمياء": 98, "علم الأحياء": 98, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2059", name: "عبد السلام علي فارس", class: "الخامس العلمي", seq: 59, grades: { "التربية الإسلامية": 100, "اللغة العربية": 80, "اللغة الإنكليزية": 95, "الرياضيات": 43, "الفيزياء": 80, "الكيمياء": 58, "علم الأحياء": 58, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2060", name: "عبد السلام نجم عبد الله", class: "الخامس العلمي", seq: 60, grades: { "التربية الإسلامية": 77, "اللغة العربية": 52, "اللغة الإنكليزية": 40, "الرياضيات": 30, "الفيزياء": 30, "الكيمياء": 33, "علم الأحياء": 39, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2061", name: "عبد الكريم محمد عيد علي", class: "الخامس العلمي", seq: 61, grades: { "التربية الإسلامية": 100, "اللغة العربية": 80, "اللغة الإنكليزية": 70, "الرياضيات": 40, "الفيزياء": 90, "الكيمياء": 51, "علم الأحياء": 72, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2062", name: "عبد الله خلف احمد", class: "الخامس العلمي", seq: 62, grades: { "التربية الإسلامية": 98, "اللغة العربية": 92, "اللغة الإنكليزية": 75, "الرياضيات": 61, "الفيزياء": 90, "الكيمياء": 69, "علم الأحياء": 73, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
  { code: "SL2063", name: "عبد الله عماد خلف", class: "الخامس العلمي", seq: 63, grades: { "التربية الإسلامية": 100, "اللغة العربية": 57, "اللغة الإنكليزية": 60, "الرياضيات": 29, "الفيزياء": 27, "الكيمياء": 41, "علم الأحياء": 52, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2064", name: "عبد الله محمود حمد", class: "الخامس العلمي", seq: 64, grades: { "التربية الإسلامية": 78, "اللغة العربية": 41, "اللغة الإنكليزية": 30, "الرياضيات": 32, "الفيزياء": 25, "الكيمياء": 34, "علم الأحياء": 53, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2065", name: "عبيدة وعد عيد", class: "الخامس العلمي", seq: 65, grades: { "التربية الإسلامية": 100, "اللغة العربية": 60, "اللغة الإنكليزية": 50, "الرياضيات": 43, "الفيزياء": 90, "الكيمياء": 55, "علم الأحياء": 58, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2066", name: "علي جبار احمد", class: "الخامس العلمي", seq: 66, grades: { "التربية الإسلامية": 100, "اللغة العربية": 70, "اللغة الإنكليزية": 40, "الرياضيات": 25, "الفيزياء": 50, "الكيمياء": 39, "علم الأحياء": 57, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2067", name: "علي حسام جاسم", class: "الخامس العلمي", seq: 67, grades: { "التربية الإسلامية": 81, "اللغة العربية": 78, "اللغة الإنكليزية": 55, "الرياضيات": 51, "الفيزياء": 34, "الكيمياء": 66, "علم الأحياء": 55, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2068", name: "عمار اركان عباس", class: "الخامس العلمي", seq: 68, grades: { "التربية الإسلامية": 100, "اللغة العربية": 94, "اللغة الإنكليزية": 98, "الرياضيات": 63, "الفيزياء": 90, "الكيمياء": 58, "علم الأحياء": 58, "الحاسوب": null, "التربية الرياضية": 90, "التربية الفنية": 90 } },
  { code: "SL2069", name: "لازم حازم محمد جدوع", class: "الخامس العلمي", seq: 69, grades: { "التربية الإسلامية": 100, "اللغة العربية": 75, "اللغة الإنكليزية": 60, "الرياضيات": 37, "الفيزياء": 32, "الكيمياء": 50, "علم الأحياء": 54, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2070", name: "ليث عماد خلف", class: "الخامس العلمي", seq: 70, grades: { "التربية الإسلامية": 82, "اللغة العربية": 25, "اللغة الإنكليزية": 25, "الرياضيات": 28, "الفيزياء": 50, "الكيمياء": 36, "علم الأحياء": 52, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2071", name: "مصطفى ناطق عواد", class: "الخامس العلمي", seq: 71, grades: { "التربية الإسلامية": 71, "اللغة العربية": 53, "اللغة الإنكليزية": 35, "الرياضيات": 34, "الفيزياء": 55, "الكيمياء": 41, "علم الأحياء": 40, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2072", name: "منتظر جاسم حسين", class: "الخامس العلمي", seq: 72, grades: { "التربية الإسلامية": 100, "اللغة العربية": 40, "اللغة الإنكليزية": 30, "الرياضيات": 28, "الفيزياء": 50, "الكيمياء": 41, "علم الأحياء": 52, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2073", name: "هيثم هاشم محمد جدوع", class: "الخامس العلمي", seq: 73, grades: { "التربية الإسلامية": 100, "اللغة العربية": 65, "اللغة الإنكليزية": 75, "الرياضيات": 42, "الفيزياء": 30, "الكيمياء": 50, "علم الأحياء": 57, "الحاسوب": null, "التربية الرياضية": 60, "التربية الفنية": 60 } },
  { code: "SL2074", name: "وسام اثير جبار بكر", class: "الخامس العلمي", seq: 74, grades: { "التربية الإسلامية": 100, "اللغة العربية": 90, "اللغة الإنكليزية": 75, "الرياضيات": 75, "الفيزياء": 51, "الكيمياء": 75, "علم الأحياء": 75, "الحاسوب": null, "التربية الرياضية": 100, "التربية الفنية": 100 } },
  { code: "SL2075", name: "وسام ظاهر مجيد", class: "الخامس العلمي", seq: 75, grades: { "التربية الإسلامية": 100, "اللغة العربية": 80, "اللغة الإنكليزية": 75, "الرياضيات": 59, "الفيزياء": 90, "الكيمياء": 71, "علم الأحياء": 71, "الحاسوب": null, "التربية الرياضية": 90, "التربية الفنية": 90 } },
  { code: "SL2076", name: "يوسف عبد الملك علي", class: "الخامس العلمي", seq: 76, grades: { "التربية الإسلامية": 100, "اللغة العربية": 78, "اللغة الإنكليزية": 70, "الرياضيات": 42, "الفيزياء": 90, "الكيمياء": 50, "علم الأحياء": 51, "الحاسوب": null, "التربية الرياضية": 70, "التربية الفنية": 70 } },
];

const ADMIN_CODE = "alijassim";
const SCHOOL_CODE = "ali2027";

// Build lookup map
const codeMap = {};
students.forEach(s => { codeMap[s.code.toUpperCase()] = s; });

function doLogin() {
  const val = document.getElementById('codeInput').value.trim().toUpperCase();
  document.getElementById('errorMsg').style.display = 'none';

  if (val === ADMIN_CODE.toUpperCase()) {
    showAdmin();
    return;
  }
  if (val === SCHOOL_CODE.toUpperCase()) {
    showAdmin();
    return;
  }
  const student = codeMap[val];
  if (student) {
    showResults(student);
  } else {
    document.getElementById('errorMsg').style.display = 'block';
  }
}

function showResults(student) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('resultsPage').classList.add('active');

  document.getElementById('displayName').textContent = student.name;

  const tbody = document.getElementById('gradesBody');
  tbody.innerHTML = '';

  const subjects = Object.keys(student.grades);
  let total = 0;
  let count = 0;

  subjects.forEach(subj => {
    const g = student.grades[subj];
    const tr = document.createElement('tr');
    const tdName = document.createElement('td');
    tdName.className = 'subject-name';
    tdName.textContent = subj;
    const tdGrade = document.createElement('td');
    tdGrade.className = g !== null ? 'grade-cell' : 'grade-cell empty';
    tdGrade.textContent = g !== null ? g : '—';
    tr.appendChild(tdName);
    tr.appendChild(tdGrade);
    tbody.appendChild(tr);
    if (g !== null) { total += g; count++; }
  });

  // Total row
  const trTotal = document.createElement('tr');
  trTotal.className = 'total-row';
  const tdTotalLabel = document.createElement('td');
  tdTotalLabel.className = 'subject-name';
  tdTotalLabel.textContent = 'المجموع الكلي';
  const tdTotalVal = document.createElement('td');
  tdTotalVal.className = 'grade-cell';
  tdTotalVal.textContent = total;
  trTotal.appendChild(tdTotalLabel);
  trTotal.appendChild(tdTotalVal);
  tbody.appendChild(trTotal);

  // Average row
  const avg = count > 0 ? (total / count).toFixed(2) : '—';
  const trAvg = document.createElement('tr');
  trAvg.className = 'total-row';
  const tdAvgLabel = document.createElement('td');
  tdAvgLabel.className = 'subject-name';
  tdAvgLabel.textContent = 'المعدل النهائي';
  const tdAvgVal = document.createElement('td');
  tdAvgVal.className = 'grade-cell';
  tdAvgVal.textContent = avg;
  trAvg.appendChild(tdAvgLabel);
  trAvg.appendChild(tdAvgVal);
  tbody.appendChild(trAvg);
}

function showAdmin() {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('adminPage').classList.add('active');

  const tbody = document.getElementById('allStudentsBody');
  tbody.innerHTML = '';
  students.forEach(s => {
    const tr = document.createElement('tr');
    tr.innerHTML = `<td>${s.name}</td><td>${s.class}</td><td class="code-cell">${s.code}</td>`;
    tbody.appendChild(tr);
  });

  doSearch();
}

function doSearch() {
  const q = document.getElementById('adminSearch').value.trim();
  const container = document.getElementById('searchResults');
  if (!q) { container.innerHTML = ''; return; }

  const results = students.filter(s => s.name.includes(q));
  if (results.length === 0) {
    container.innerHTML = '<div class="no-results">لا توجد نتائج مطابقة</div>';
    return;
  }

  container.innerHTML = results.map(s => `
    <div class="student-card-admin">
      <div>
        <div class="sname">${s.name}</div>
        <div class="sclass">${s.class}</div>
      </div>
      <div class="secret-badge">${s.code}</div>
    </div>
  `).join('');
}

function doLogout() {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('loginPage').classList.add('active');
  document.getElementById('codeInput').value = '';
  document.getElementById('errorMsg').style.display = 'none';
}
</script>
</body>
</html>
