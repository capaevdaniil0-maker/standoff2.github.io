<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Школа Standoff — журнал</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
      background: #f0f4f8;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }
    .app {
      max-width: 1100px;
      width: 100%;
      background: #ffffff;
      border-radius: 28px;
      padding: 30px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.07);
    }
    .header {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      margin-bottom: 6px;
    }
    h1 {
      font-size: 2rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .subhead { color: #64748b; margin-bottom: 1.5rem; }
    .btn {
      padding: 8px 18px;
      border: none;
      border-radius: 12px;
      font-weight: 600;
      font-size: 0.95rem;
      cursor: pointer;
      transition: 0.15s;
      background: #e2e8f0;
      color: #1e293b;
      white-space: nowrap;
    }
    .btn-primary { background: #3b82f6; color: #fff; }
    .btn-primary:hover { background: #2563eb; }
    .btn-success { background: #22c55e; color: #fff; }
    .btn-success:hover { background: #16a34a; }
    .btn-danger { background: #ef4444; color: #fff; }
    .btn-danger:hover { background: #dc2626; }
    .btn-warning { background: #f59e0b; color: #fff; }
    .btn-warning:hover { background: #d97706; }
    .btn-sm { padding: 4px 14px; font-size: 0.85rem; }
    .btn-outline { background: transparent; border: 1px solid #d1d9e6; }
    .btn-outline:hover { background: #f1f5f9; }
    .card {
      background: #f8fafc;
      border-radius: 16px;
      padding: 16px 20px;
      margin-bottom: 16px;
    }
    .flex-row {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }
    .flex-row input[type="text"],
    .flex-row input[type="number"],
    .flex-row input[type="password"] {
      padding: 10px 14px;
      border: 1px solid #d1d9e6;
      border-radius: 10px;
      font-size: 1rem;
      background: #fff;
      flex: 1 1 180px;
      outline: none;
    }
    .flex-row input:focus { border-color: #3b82f6; box-shadow: 0 0 0 3px rgba(59,130,246,0.2); }
    .student-item {
      background: #fff;
      border-radius: 14px;
      padding: 14px 18px;
      border: 1px solid #e9edf3;
      margin-bottom: 12px;
    }
    .student-header {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      margin-bottom: 6px;
    }
    .student-name {
      font-size: 1.2rem;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 12px;
      cursor: pointer;
    }
    .student-avg {
      background: #dbeafe;
      padding: 2px 14px;
      border-radius: 30px;
      font-size: 0.9rem;
      font-weight: 500;
      color: #1e40af;
    }
    .grades-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 8px 0 12px;
      align-items: center;
    }
    .grade-chip {
      padding: 4px 14px;
      border-radius: 30px;
      font-size: 0.95rem;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
      border: 2px solid transparent;
    }
    .grade-chip:hover { border-color: #94a3b8; }
    .grade-chip .del-grade {
      cursor: pointer;
      color: #94a3b8;
      font-weight: 700;
      margin-left: 4px;
    }
    .grade-chip .del-grade:hover { color: #dc2626; }
    .grade-5 { background: #dcfce7; color: #15803d; }
    .grade-4 { background: #dbeafe; color: #1d4ed8; }
    .grade-3 { background: #fef9c3; color: #a16207; }
    .grade-2 { background: #fee2e2; color: #b91c1c; }
    .grade-1 { background: #fecaca; color: #991b1b; }
    .add-grade-form {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      align-items: center;
      margin-top: 4px;
    }
    .add-grade-form input { width: 80px; padding: 6px 10px; border: 1px solid #d1d9e6; border-radius: 8px; }
    .total-avg {
      font-size: 1.4rem;
      font-weight: 700;
      color: #0f172a;
    }
    .empty { color: #94a3b8; text-align: center; padding: 30px 0; }
    .footer { font-size: 0.85rem; color: #94a3b8; margin-top: 20px; text-align: center; }
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 8px;
      margin: 8px 0 4px;
      font-size: 0.9rem;
      color: #475569;
    }
    .stats-grid span { background: #f1f5f9; padding: 4px 10px; border-radius: 20px; text-align: center; }
    .sort-select {
      padding: 8px 12px;
      border-radius: 10px;
      border: 1px solid #d1d9e6;
      background: #fff;
      font-size: 0.95rem;
      outline: none;
    }
    .hidden { display: none !important; }
    .file-input-hidden { display: none; }
    .admin-panel { border-top: 2px dashed #d1d9e6; padding-top: 16px; margin-top: 10px; }
    .login-error { color: #dc2626; margin: 6px 0; }
    @media (max-width: 600px) {
      .app { padding: 16px; }
      .header { flex-direction: column; align-items: stretch; }
    }
  </style>
</head>
<body>
<div class="app">
  <div class="header">
    <h1>🏫 Школа Standoff</h1>
    <div>
      <span id="statusLabel" style="font-size:0.9rem; color:#64748b;">Режим просмотра</span>
    </div>
  </div>
  <p class="subhead">Журнал успеваемости игроков</p>

  <!-- Форма входа (всегда видна) -->
  <div class="card" id="loginCard">
    <div class="flex-row">
      <input type="password" id="passwordInput" placeholder="Введите пароль для редактирования" />
      <button class="btn btn-primary" id="loginBtn">Войти в панель управления</button>
      <button class="btn btn-outline hidden" id="logoutBtn">Выйти</button>
    </div>
    <div id="loginError" class="login-error hidden">Неверный пароль. Попробуйте снова.</div>
  </div>

  <!-- Панель управления (скрыта по умолчанию) -->
  <div id="adminPanel" class="admin-panel hidden">
    <div class="card">
      <div class="flex-row">
        <input type="text" id="studentNameInput" placeholder="Имя ученика" />
        <button class="btn btn-success" id="addStudentBtn">➕ Добавить</button>
        <button class="btn btn-warning" id="exportBtn">📥 Скачать бэкап</button>
        <button class="btn btn-warning" id="importBtn">📤 Восстановить</button>
        <input type="file" id="fileInput" accept=".json" class="file-input-hidden" />
        <select id="sortSelect" class="sort-select">
          <option value="name">Сортировка: по имени</option>
          <option value="avg">по среднему баллу</option>
          <option value="count">по количеству оценок</option>
        </select>
      </div>
    </div>
  </div>

  <!-- Контейнер учеников -->
  <div id="studentsContainer"></div>

  <!-- Общая статистика -->
  <div class="card" style="margin-top:10px;">
    <div style="display:flex; flex-wrap:wrap; justify-content:space-between; align-items:center; gap:10px;">
      <span style="font-weight:500;">📊 Общая статистика класса:</span>
      <span id="classStats" style="font-size:0.95rem; color:#475569;">—</span>
      <span style="font-weight:500;">Общий средний:</span>
      <span class="total-avg" id="totalAvg">—</span>
    </div>
  </div>
  <div class="footer">Данные сохраняются в браузере. <strong></strong></div>
</div>

<script>
  (function() {
    // ----- НАСТРОЙКИ -----
    const PASSWORD = '6789';
    const STORAGE_KEY = 'standoffSchoolJournal';

    // ----- СОСТОЯНИЕ -----
    let data = {};
    let isAdmin = false;
    let sortMode = 'name';

    // ----- DOM-ЭЛЕМЕНТЫ -----
    const container = document.getElementById('studentsContainer');
    const totalAvgSpan = document.getElementById('totalAvg');
    const classStatsSpan = document.getElementById('classStats');
    const loginCard = document.getElementById('loginCard');
    const passwordInput = document.getElementById('passwordInput');
    const loginBtn = document.getElementById('loginBtn');
    const logoutBtn = document.getElementById('logoutBtn');
    const loginError = document.getElementById('loginError');
    const adminPanel = document.getElementById('adminPanel');
    const statusLabel = document.getElementById('statusLabel');
    const studentNameInput = document.getElementById('studentNameInput');
    const addStudentBtn = document.getElementById('addStudentBtn');
    const exportBtn = document.getElementById('exportBtn');
    const importBtn = document.getElementById('importBtn');
    const fileInput = document.getElementById('fileInput');
    const sortSelect = document.getElementById('sortSelect');

    // ----- ЗАГРУЗКА / СОХРАНЕНИЕ -----
    function loadData() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (raw) {
          const parsed = JSON.parse(raw);
          if (typeof parsed === 'object' && parsed !== null) {
            data = parsed;
            return;
          }
        }
      } catch (e) {
        console.warn('Ошибка загрузки данных', e);
      }
      data = {};
    }

    function saveData() {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
    }

    // ----- ВСПОМОГАТЕЛЬНЫЕ ФУНКЦИИ -----
    function computeAvg(grades) {
      if (!grades || grades.length === 0) return null;
      const sum = grades.reduce((a, b) => a + b, 0);
      return sum / grades.length;
    }

    function formatAvg(val) {
      if (val === null || isNaN(val)) return '—';
      return val.toFixed(1);
    }

    function escapeHtml(str) {
      const div = document.createElement('div');
      div.textContent = str;
      return div.innerHTML;
    }

    function getStudentStats(grades) {
      const total = grades.length;
      if (total === 0) return { total, count5:0, count4:0, count3:0, count2:0, count1:0, successRate:0 };
      let c5=0,c4=0,c3=0,c2=0,c1=0;
      grades.forEach(g => {
        if (g >= 5) c5++;
        else if (g >= 4) c4++;
        else if (g >= 3) c3++;
        else if (g >= 2) c2++;
        else c1++;
      });
      const success = (c5 + c4) / total * 100;
      return { total, count5:c5, count4:c4, count3:c3, count2:c2, count1:c1, successRate: success };
    }

    // ----- ОТРИСОВКА -----
    function render() {
      let studentNames = Object.keys(data);
      if (studentNames.length === 0) {
        container.innerHTML = `<div class="empty">Пока нет учеников. ${isAdmin ? 'Добавьте первого!' : 'Ожидайте добавления.'}</div>`;
        totalAvgSpan.textContent = '—';
        classStatsSpan.textContent = '—';
        updateUI();
        return;
      }

      // Сортировка
      if (sortMode === 'avg') {
        studentNames.sort((a,b) => {
          const avgA = computeAvg(data[a]) || 0;
          const avgB = computeAvg(data[b]) || 0;
          return avgB - avgA;
        });
      } else if (sortMode === 'count') {
        studentNames.sort((a,b) => (data[b]?.length || 0) - (data[a]?.length || 0));
      } else {
        studentNames.sort((a,b) => a.localeCompare(b));
      }

      let html = '';
      let totalSum = 0, totalCount = 0;
      let totalSuccessSum = 0, totalSuccessCount = 0;

      studentNames.forEach(name => {
        const grades = data[name] || [];
        const avg = computeAvg(grades);
        const avgDisplay = formatAvg(avg);
        const stats = getStudentStats(grades);
        if (grades.length > 0) {
          const sum = grades.reduce((a,b) => a+b, 0);
          totalSum += sum;
          totalCount += grades.length;
          totalSuccessSum += stats.count5 + stats.count4;
          totalSuccessCount += stats.total;
        }

        html += `<div class="student-item" data-student="${escapeHtml(name)}">`;
        html += `<div class="student-header">`;
        html += `<div class="student-name" data-student="${escapeHtml(name)}">`;
        html += `${escapeHtml(name)} <span class="student-avg">Ср. ${avgDisplay}</span>`;
        html += `</div>`;
        if (isAdmin) {
          html += `<button class="btn btn-danger btn-sm delete-student-btn" data-student="${escapeHtml(name)}">🗑 Удалить</button>`;
        }
        html += `</div>`;

        // Статистика ученика
        html += `<div class="stats-grid">`;
        html += `<span>📊 ${stats.total} оценок</span>`;
        html += `<span>⭐ 5: ${stats.count5}</span>`;
        html += `<span>🔵 4: ${stats.count4}</span>`;
        html += `<span>🟡 3: ${stats.count3}</span>`;
        html += `<span>🔴 2: ${stats.count2}</span>`;
        html += `<span>🏆 успеваемость: ${stats.total > 0 ? stats.successRate.toFixed(1) : 0}%</span>`;
        html += `</div>`;

        // Список оценок
        html += `<div class="grades-list">`;
        if (grades.length === 0) {
          html += `<span style="color:#94a3b8; font-size:0.9rem;">Нет оценок</span>`;
        } else {
          grades.forEach((grade, idx) => {
            let gradeClass = 'grade-5';
            if (grade < 2) gradeClass = 'grade-1';
            else if (grade < 3) gradeClass = 'grade-2';
            else if (grade < 4) gradeClass = 'grade-3';
            else if (grade < 5) gradeClass = 'grade-4';
            html += `<span class="grade-chip ${gradeClass}" data-student="${escapeHtml(name)}" data-index="${idx}">${grade}`;
            if (isAdmin) {
              html += ` <span class="del-grade" data-student="${escapeHtml(name)}" data-index="${idx}">✕</span>`;
            }
            html += `</span>`;
          });
        }
        html += `</div>`;

        // Форма добавления оценки (только для администратора)
        if (isAdmin) {
          html += `<div class="add-grade-form">`;
          html += `<input type="number" min="1" max="5" step="0.5" placeholder="Оценка" class="grade-input" data-student="${escapeHtml(name)}" value="5">`;
          html += `<button class="btn btn-primary btn-sm add-grade-btn" data-student="${escapeHtml(name)}">➕</button>`;
          html += `</div>`;
        }

        html += `</div>`;
      });

      container.innerHTML = html;

      // Общая статистика
      if (totalCount > 0) {
        const overallAvg = totalSum / totalCount;
        totalAvgSpan.textContent = overallAvg.toFixed(1);
        const classSuccess = totalSuccessCount > 0 ? (totalSuccessSum / totalSuccessCount * 100) : 0;
        classStatsSpan.textContent = `👥 ${studentNames.length} учеников, 📝 ${totalCount} оценок, 🏆 успеваемость ${classSuccess.toFixed(1)}%`;
      } else {
        totalAvgSpan.textContent = '—';
        classStatsSpan.textContent = `👥 ${studentNames.length} учеников, оценок нет`;
      }

      updateUI();
    }

    // ----- ОБНОВЛЕНИЕ ИНТЕРФЕЙСА (вход/выход) -----
    function updateUI() {
      if (isAdmin) {
        loginBtn.classList.add('hidden');
        logoutBtn.classList.remove('hidden');
        adminPanel.classList.remove('hidden');
        statusLabel.textContent = 'Режим редактирования';
        loginError.classList.add('hidden');
      } else {
        loginBtn.classList.remove('hidden');
        logoutBtn.classList.add('hidden');
        adminPanel.classList.add('hidden');
        statusLabel.textContent = 'Режим просмотра';
      }
      // Показываем/скрываем кнопки удаления и добавления оценок через CSS? 
      // Они уже управляются через рендеринг (if isAdmin), поэтому перерендерим.
      // Для обновления кнопок после входа/выхода перерисовываем список.
      // Мы вызываем render() после входа/выхода, поэтому здесь дополнительно ничего не нужно.
    }

    // ----- РЕДАКТИРОВАНИЕ ОЦЕНКИ (клик по оценке) -----
    function makeGradeEditable(gradeSpan) {
      const student = gradeSpan.dataset.student;
      const index = parseInt(gradeSpan.dataset.index, 10);
      const currentValue = data[student]?.[index];
      if (currentValue === undefined) return;

      const input = document.createElement('input');
      input.type = 'number';
      input.min = 1;
      input.max = 5;
      input.step = 0.5;
      input.value = currentValue;
      input.style.width = '60px';
      input.style.padding = '2px 6px';
      input.style.borderRadius = '8px';
      input.style.border = '2px solid #3b82f6';
      input.style.fontSize = '0.95rem';
      input.style.fontWeight = '600';

      gradeSpan.replaceWith(input);
      input.focus();
      input.select();

      function saveEdit() {
        const newVal = parseFloat(input.value);
        if (!isNaN(newVal) && newVal >= 1 && newVal <= 5) {
          if (data[student]) {
            data[student][index] = newVal;
            saveData();
            render();
          }
        } else {
          render(); // откат
        }
      }

      input.addEventListener('blur', saveEdit);
      input.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
          e.preventDefault();
          input.blur();
        }
        if (e.key === 'Escape') {
          render();
        }
      });
    }

    // ----- РЕДАКТИРОВАНИЕ ИМЕНИ (двойной клик) -----
    function makeNameEditable(nameSpan) {
      const student = nameSpan.dataset.student;
      if (!student || !data[student]) return;
      const currentName = student;

      const input = document.createElement('input');
      input.type = 'text';
      input.value = currentName;
      input.style.fontSize = '1.2rem';
      input.style.fontWeight = '600';
      input.style.border = '2px solid #3b82f6';
      input.style.borderRadius = '10px';
      input.style.padding = '4px 10px';
      input.style.background = '#fff';
      input.style.width = 'auto';
      input.style.minWidth = '150px';

      nameSpan.replaceWith(input);
      input.focus();
      input.select();

      function saveName() {
        const newName = input.value.trim();
        if (newName && newName !== currentName) {
          const exists = Object.keys(data).some(k => k.toLowerCase() === newName.toLowerCase());
          if (exists) {
            alert('Ученик с таким именем уже существует');
            render();
            return;
          }
          data[newName] = data[currentName];
          delete data[currentName];
          saveData();
          render();
        } else {
          render();
        }
      }

      input.addEventListener('blur', saveName);
      input.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
          e.preventDefault();
          input.blur();
        }
        if (e.key === 'Escape') {
          render();
        }
      });
    }

    // ----- ОБРАБОТЧИКИ СОБЫТИЙ (делегирование на контейнере) -----
    function handleContainerClick(e) {
      const target = e.target;

      // Удаление оценки (крестик)
      if (target.classList.contains('del-grade')) {
        if (!isAdmin) return;
        const student = target.dataset.student;
        const index = parseInt(target.dataset.index, 10);
        if (student && data[student] && !isNaN(index) && data[student][index] !== undefined) {
          data[student].splice(index, 1);
          saveData();
          render();
        }
        return;
      }

      // Кнопка добавить оценку
      if (target.classList.contains('add-grade-btn')) {
        if (!isAdmin) return;
        const student = target.dataset.student;
        const input = document.querySelector(`.grade-input[data-student="${student}"]`);
        if (!input) return;
        const val = parseFloat(input.value);
        if (isNaN(val) || val < 1 || val > 5) {
          alert('Оценка должна быть числом от 1 до 5 (можно с шагом 0.5)');
          return;
        }
        if (data[student]) {
          data[student].push(val);
          saveData();
          render();
          input.value = '5';
        }
        return;
      }

      // Удаление ученика
      if (target.classList.contains('delete-student-btn')) {
        if (!isAdmin) return;
        const student = target.dataset.student;
        if (student && data[student]) {
          if (confirm(`Удалить ученика «${student}» и все его оценки?`)) {
            delete data[student];
            saveData();
            render();
          }
        }
        return;
      }

      // Клик по оценке (редактирование) — только для администратора
      if (target.classList.contains('grade-chip') && !target.classList.contains('del-grade')) {
        if (!isAdmin) return;
        makeGradeEditable(target);
        return;
      }
    }

    function handleContainerDblClick(e) {
      const target = e.target;
      const nameSpan = target.closest('.student-name');
      if (nameSpan && isAdmin) {
        makeNameEditable(nameSpan);
      }
    }

    function handleGradeInputKeypress(e) {
      if (e.key === 'Enter') {
        const input = e.currentTarget;
        const student = input.dataset.student;
        const btn = document.querySelector(`.add-grade-btn[data-student="${student}"]`);
        if (btn) btn.click();
      }
    }

    // ----- ВХОД / ВЫХОД -----
    function login() {
      const pwd = passwordInput.value.trim();
      if (pwd === PASSWORD) {
        isAdmin = true;
        sessionStorage.setItem('isAdmin', 'true');
        loginError.classList.add('hidden');
        passwordInput.value = '';
        render(); // перерисовываем с кнопками администратора
      } else {
        loginError.classList.remove('hidden');
        passwordInput.value = '';
        passwordInput.focus();
      }
    }

    function logout() {
      isAdmin = false;
      sessionStorage.removeItem('isAdmin');
      render(); // перерисовываем без кнопок
    }

    // ----- ДОБАВЛЕНИЕ УЧЕНИКА -----
    function addStudent() {
      if (!isAdmin) return;
      const name = studentNameInput.value.trim();
      if (!name) { alert('Введите имя'); return; }
      const exists = Object.keys(data).some(k => k.toLowerCase() === name.toLowerCase());
      if (exists) { alert('Такой ученик уже есть'); return; }
      data[name] = [];
      saveData();
      render();
      studentNameInput.value = '';
      studentNameInput.focus();
    }

    // ----- ЭКСПОРТ / ИМПОРТ -----
    function exportData() {
      const json = JSON.stringify(data, null, 2);
      const blob = new Blob([json], { type: 'application/json' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = `standoff-backup-${new Date().toISOString().slice(0,10)}.json`;
      a.click();
      URL.revokeObjectURL(url);
    }

    function importData(file) {
      const reader = new FileReader();
      reader.onload = function(e) {
        try {
          const imported = JSON.parse(e.target.result);
          if (typeof imported === 'object' && imported !== null) {
            const valid = Object.values(imported).every(v => Array.isArray(v));
            if (valid) {
              if (confirm('Импорт заменит все текущие данные. Продолжить?')) {
                data = imported;
                saveData();
                render();
                alert('Данные успешно восстановлены!');
              }
            } else {
              alert('Неверный формат файла');
            }
          } else {
            alert('Неверный формат файла');
          }
        } catch (err) {
          alert('Ошибка чтения файла');
        }
      };
      reader.readAsText(file);
    }

    // ----- ИНИЦИАЛИЗАЦИЯ -----
    function init() {
      loadData();
      // Проверяем сессию
      if (sessionStorage.getItem('isAdmin') === 'true') {
        isAdmin = true;
      }
      render();

      // Навешиваем обработчики событий
      container.addEventListener('click', handleContainerClick);
      container.addEventListener('dblclick', handleContainerDblClick);
      container.addEventListener('keypress', function(e) {
        if (e.target.classList.contains('grade-input')) {
          handleGradeInputKeypress(e);
        }
      });

      loginBtn.addEventListener('click', login);
      passwordInput.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') login();
      });
      logoutBtn.addEventListener('click', logout);

      addStudentBtn.addEventListener('click', addStudent);
      studentNameInput.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') addStudent();
      });

      exportBtn.addEventListener('click', exportData);
      importBtn.addEventListener('click', function() { fileInput.click(); });
      fileInput.addEventListener('change', function(e) {
        if (this.files.length > 0) {
          importData(this.files[0]);
          this.value = '';
        }
      });

      sortSelect.addEventListener('change', function() {
        sortMode = this.value;
        render();
      });

      console.log('Приложение запущено. Пароль: 6789');
    }

    // Запуск
    document.addEventListener('DOMContentLoaded', init);
  })();
</script>
</body>
</html>
