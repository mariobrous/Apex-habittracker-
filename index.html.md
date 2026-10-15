#   
<!DOCTYPE html>  
<html lang="es">  
<head>  
  <meta charset="UTF-8" />  
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />  
  <title>ApexHabit — Panel de Alto Rendimiento</title>  
  <style>  
    :root {  
      --bg-main: #090d16;  
      --bg-card: #111827;  
      --bg-card-hover: #1f2937;  
      --border: #1e293b;  
      --text-main: #f8fafc;  
      --text-muted: #94a3b8;  
      --accent: #10b981;  
      --accent-glow: rgba(16, 185, 129, 0.2);  
      --blue: #3b82f6;  
      --amber: #f59e0b;  
      --danger: #ef4444;  
    }  
  
    * {  
      box-sizing: border-box;  
      margin: 0;  
      padding: 0;  
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;  
      -webkit-tap-highlight-color: transparent;  
    }  
  
    body {  
      background-color: var(--bg-main);  
      color: var(--text-main);  
      padding: 16px;  
      line-height: 1.5;  
    }  
  
    .container {  
      max-width: 1100px;  
      margin: 0 auto;  
    }  
  
    /* Header */  
    .header {  
      display: flex;  
      flex-wrap: wrap;  
      justify-content: space-between;  
      align-items: center;  
      gap: 12px;  
      padding-bottom: 16px;  
      margin-bottom: 20px;  
      border-bottom: 1px solid var(--border);  
    }  
  
    .brand {  
      display: flex;  
      align-items: center;  
      gap: 10px;  
    }  
  
    .brand-title {  
      font-size: 1.35rem;  
      font-weight: 800;  
      letter-spacing: -0.5px;  
      color: var(--text-main);  
    }  
  
    .badge-save {  
      font-size: 0.75rem;  
      padding: 4px 10px;  
      border-radius: 999px;  
      background: var(--accent-glow);  
      color: var(--accent);  
      border: 1px solid var(--accent);  
      font-weight: 600;  
    }  
  
    .actions {  
      display: flex;  
      flex-wrap: wrap;  
      gap: 8px;  
    }  
  
    button {  
      cursor: pointer;  
      border: 1px solid var(--border);  
      background: var(--bg-card);  
      color: var(--text-main);  
      padding: 8px 12px;  
      border-radius: 8px;  
      font-size: 0.8rem;  
      font-weight: 600;  
      transition: all 0.15s ease;  
    }  
  
    button:hover {  
      background: var(--bg-card-hover);  
    }  
  
    .btn-primary {  
      background: var(--accent);  
      color: #052e16;  
      border-color: var(--accent);  
    }  
  
    .btn-primary:hover {  
      background: #059669;  
      color: #fff;  
    }  
  
    .btn-danger {  
      color: var(--danger);  
      border-color: rgba(239, 68, 68, 0.3);  
    }  
  
    /* KPI Grid */  
    .kpi-grid {  
      display: grid;  
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));  
      gap: 12px;  
      margin-bottom: 20px;  
    }  
  
    .kpi-card {  
      background: var(--bg-card);  
      border: 1px solid var(--border);  
      border-radius: 12px;  
      padding: 14px;  
    }  
  
    .kpi-label {  
      font-size: 0.75rem;  
      color: var(--text-muted);  
      text-transform: uppercase;  
      font-weight: 700;  
      letter-spacing: 0.5px;  
    }  
  
    .kpi-value {  
      font-size: 1.5rem;  
      font-weight: 800;  
      margin-top: 4px;  
      color: var(--text-main);  
    }  
  
    .kpi-sub {  
      font-size: 0.72rem;  
      color: var(--accent);  
      margin-top: 2px;  
    }  
  
    /* Formulario Nuevo Hábito */  
    .add-bar {  
      display: flex;  
      flex-wrap: wrap;  
      gap: 8px;  
      background: var(--bg-card);  
      border: 1px solid var(--border);  
      padding: 12px;  
      border-radius: 12px;  
      margin-bottom: 20px;  
    }  
  
    .add-bar input, .add-bar select {  
      background: var(--bg-main);  
      border: 1px solid var(--border);  
      color: var(--text-main);  
      padding: 8px 12px;  
      border-radius: 8px;  
      font-size: 0.85rem;  
      outline: none;  
    }  
  
    .add-bar input {  
      flex: 1;  
      min-width: 180px;  
    }  
  
    /* Tabla de Hábitos */  
    .card-section {  
      background: var(--bg-card);  
      border: 1px solid var(--border);  
      border-radius: 12px;  
      padding: 16px;  
      margin-bottom: 20px;  
      overflow-x: auto;  
    }  
  
    .section-title {  
      font-size: 0.95rem;  
      font-weight: 700;  
      margin-bottom: 14px;  
      display: flex;  
      justify-content: space-between;  
      align-items: center;  
    }  
  
    table {  
      width: 100%;  
      border-collapse: collapse;  
      min-width: 600px;  
    }  
  
    th, td {  
      padding: 10px 8px;  
      text-align: center;  
      border-bottom: 1px solid var(--border);  
    }  
  
    th:first-child, td:first-child {  
      text-align: left;  
      min-width: 210px;  
    }  
  
    th {  
      font-size: 0.75rem;  
      color: var(--text-muted);  
      text-transform: uppercase;  
    }  
  
    .habit-name {  
      font-weight: 600;  
      font-size: 0.9rem;  
      display: block;  
    }  
  
    .habit-cat {  
      font-size: 0.7rem;  
      color: var(--text-muted);  
      background: var(--bg-main);  
      padding: 2px 8px;  
      border-radius: 4px;  
      display: inline-block;  
      margin-top: 2px;  
    }  
  
    .day-btn {  
      width: 34px;  
      height: 34px;  
      border-radius: 8px;  
      border: 1px solid var(--border);  
      background: var(--bg-main);  
      color: transparent;  
      font-weight: 800;  
      display: inline-flex;  
      align-items: center;  
      justify-content: center;  
      padding: 0;  
    }  
  
    .day-btn.active {  
      background: var(--accent);  
      border-color: var(--accent);  
      color: #052e16;  
    }  
  
    .streak-pill {  
      font-size: 0.8rem;  
      font-weight: 700;  
      color: var(--amber);  
    }  
  
    .progress-wrap {  
      width: 80px;  
      background: var(--bg-main);  
      height: 8px;  
      border-radius: 999px;  
      overflow: hidden;  
      display: inline-block;  
      vertical-align: middle;  
      margin-right: 6px;  
    }  
  
    .progress-fill {  
      height: 100%;  
      background: var(--blue);  
      transition: width 0.25s ease;  
    }  
  
    /* Gráficos Nativos CSS (A prueba de fallos en móvil) */  
    .charts-grid {  
      display: grid;  
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));  
      gap: 16px;  
    }  
  
    .bar-chart {  
      display: flex;  
      align-items: flex-end;  
      justify-content: space-between;  
      height: 160px;  
      padding-top: 24px;  
      gap: 8px;  
    }  
  
    .bar-col {  
      flex: 1;  
      display: flex;  
      flex-direction: column;  
      align-items: center;  
      height: 100%;  
      justify-content: flex-end;  
    }  
  
    .bar-val {  
      font-size: 0.7rem;  
      color: var(--text-muted);  
      margin-bottom: 4px;  
      font-weight: 700;  
    }  
  
    .bar-visual {  
      width: 100%;  
      max-width: 32px;  
      background: var(--accent);  
      border-radius: 6px 6px 0 0;  
      transition: height 0.3s ease;  
      min-height: 4px;  
    }  
  
    .bar-day {  
      font-size: 0.75rem;  
      color: var(--text-muted);  
      margin-top: 6px;  
      font-weight: 600;  
    }  
  
    .rank-row {  
      margin-bottom: 10px;  
    }  
  
    .rank-head {  
      display: flex;  
      justify-content: space-between;  
      font-size: 0.8rem;  
      margin-bottom: 4px;  
    }  
  
    .rank-track {  
      width: 100%;  
      height: 10px;  
      background: var(--bg-main);  
      border-radius: 999px;  
      overflow: hidden;  
    }  
  
    .rank-fill {  
      height: 100%;  
      background: linear-gradient(90deg, #f59e0b, #10b981);  
      border-radius: 999px;  
      transition: width 0.3s ease;  
    }  
  
    .del-btn {  
      padding: 4px 8px;  
      font-size: 0.75rem;  
      border: none;  
      background: transparent;  
      color: var(--text-muted);  
    }  
  
    .del-btn:hover {  
      color: var(--danger);  
    }  
  </style>  
</head>  
<body>  
  <div class="container">  
    <!-- Cabecera -->  
    <div class="header">  
      <div class="brand">  
        <span class="brand-title">⚡ APEXHABIT</span>  
        <span id="saveStatus" class="badge-save">✓ Guardado Local Activo</span>  
      </div>  
      <div class="actions">  
        <button onclick="exportData()">⬇ Exportar JSON</button>  
        <button onclick="document.getElementById('importInput').click()">⬆ Importar JSON</button>  
        <input type="file" id="importInput" style="display:none" accept=".json" onchange="importData(event)" />  
        <button onclick="resetWeek()">Reiniciar Semana</button>  
        <button class="btn-danger" onclick="restoreDefault()">Restaurar Base</button>  
      </div>  
    </div>  
  
    <!-- KPIs -->  
    <div class="kpi-grid">  
      <div class="kpi-card">  
        <div class="kpi-label">Cumplimiento Semanal</div>  
        <div class="kpi-value" id="kpiRate">0%</div>  
        <div class="kpi-sub" id="kpiChecks">0 de 0 completados</div>  
      </div>  
      <div class="kpi-card">  
        <div class="kpi-label">Mejor Racha Activa</div>  
        <div class="kpi-value" id="kpiStreak">0 días</div>  
        <div class="kpi-sub" id="kpiStreakName">-</div>  
      </div>  
      <div class="kpi-card">  
        <div class="kpi-label">Día Más Productivo</div>  
        <div class="kpi-value" id="kpiBestDay">-</div>  
        <div class="kpi-sub" id="kpiBestDayCount">0 hábitos</div>  
      </div>  
      <div class="kpi-card">  
        <div class="kpi-label">Hábitos Activos</div>  
        <div class="kpi-value" id="kpiTotalHabits">0</div>  
        <div class="kpi-sub">En seguimiento</div>  
      </div>  
    </div>  
  
    <!-- Añadir nuevo hábito -->  
    <div class="add-bar">  
      <input type="text" id="habitNameInput" placeholder="Nuevo hábito o meta diaria (ej. Cardio HIIT 20m)..." />  
      <select id="habitCatInput">  
        <option value="Fitness">Fitness</option>  
        <option value="Negocios">Negocios / Finanzas</option>  
        <option value="Estudio">Estudio / USM</option>  
        <option value="Contenido">Creación de Contenido</option>  
        <option value="Mentalidad">Mentalidad</option>  
      </select>  
      <button class="btn-primary" onclick="addHabit()">+ Añadir Meta</button>  
    </div>  
  
    <!-- Matriz Semanal -->  
    <div class="card-section">  
      <div class="section-title">  
        <span>Registro Diario (Lunes a Domingo)</span>  
      </div>  
      <table>  
        <thead>  
          <tr>  
            <th>Hábito / Categoría</th>  
            <th>Lun</th>  
            <th>Mar</th>  
            <th>Mié</th>  
            <th>Jue</th>  
            <th>Vie</th>  
            <th>Sáb</th>  
            <th>Dom</th>  
            <th>Racha</th>  
            <th>Progreso</th>  
            <th></th>  
          </tr>  
        </thead>  
        <tbody id="habitTableBody"></tbody>  
      </table>  
    </div>  
  
    <!-- Gráficos de Rachas y Consistencia -->  
    <div class="charts-grid">  
      <div class="card-section">  
        <div class="section-title">Efectividad por Día (%)</div>  
        <div class="bar-chart" id="dailyBarChart"></div>  
      </div>  
      <div class="card-section">  
        <div class="section-title">Ranking de Rachas Semanales</div>  
        <div id="streakRankContainer"></div>  
      </div>  
    </div>  
  </div>  
  
  <script>  
    const STORAGE_KEY = 'apex_habits_v2_data';  
    const DAYS = ['Lun', 'Mar', 'Mié', 'Jue', 'Vie', 'Sáb', 'Dom'];  
  
    const DEFAULT_HABITS = [  
      { id: 1, name: 'Entrenamiento de fuerza / Gym', cat: 'Fitness', days: [true, true, false, true, true, false, false] },  
      { id: 2, name: 'Bloque de estudio profundo', cat: 'Estudio', days: [true, true, true, true, false, false, false] },  
      { id: 3, name: 'Gestión E-commerce / Finanzas', cat: 'Negocios', days: [true, false, true, true, false, false, false] },  
      { id: 4, name: 'Creación y edición de contenido', cat: 'Contenido', days: [false, true, true, true, false, false, false] },  
      { id: 5, name: 'Análisis de mercado / Lectura', cat: 'Mentalidad', days: [true, true, true, false, false, false, false] }  
    ];  
  
    let habits = [];  
  
    function loadData() {  
      try {  
        const raw = localStorage.getItem(STORAGE_KEY);  
        habits = raw ? JSON.parse(raw) : JSON.parse(JSON.stringify(DEFAULT_HABITS));  
      } catch (e) {  
        habits = JSON.parse(JSON.stringify(DEFAULT_HABITS));  
      }  
      render();  
    }  
  
    function saveData() {  
      const badge = document.getElementById('saveStatus');  
      try {  
        localStorage.setItem(STORAGE_KEY, JSON.stringify(habits));  
        badge.textContent = '✓ Guardado (' + new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit', second:'2-digit'}) + ')';  
      } catch (e) {  
        badge.textContent = '⚠ Memoria restringida (Usa Exportar JSON)';  
      }  
    }  
  
    function getStreak(daysArr) {  
      let current = 0;  
      let max = 0;  
      for (let i = 0; i < daysArr.length; i++) {  
        if (daysArr[i]) {  
          current++;  
          if (current > max) max = current;  
        } else {  
          current = 0;  
        }  
      }  
      return max;  
    }  
  
    function toggleDay(habitId, dayIndex) {  
      const h = habits.find(item => item.id === habitId);  
      if (h) {  
        h.days[dayIndex] = !h.days[dayIndex];  
        saveData();  
        render();  
      }  
    }  
  
    function addHabit() {  
      const input = document.getElementById('habitNameInput');  
      const cat = document.getElementById('habitCatInput').value;  
      const name = input.value.trim();  
      if (!name) return;  
  
      habits.push({  
        id: Date.now(),  
        name: name,  
        cat: cat,  
        days: [false, false, false, false, false, false, false]  
      });  
      input.value = '';  
      saveData();  
      render();  
    }  
  
    function deleteHabit(id) {  
      habits = habits.filter(h => h.id !== id);  
      saveData();  
      render();  
    }  
  
    function resetWeek() {  
      habits.forEach(h => h.days = [false, false, false, false, false, false, false]);  
      saveData();  
      render();  
    }  
  
    function restoreDefault() {  
      habits = JSON.parse(JSON.stringify(DEFAULT_HABITS));  
      saveData();  
      render();  
    }  
  
    function exportData() {  
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(habits, null, 2));  
      const a = document.createElement('a');  
      a.setAttribute("href", dataStr);  
      a.setAttribute("download", "respaldo_apexhabit.json");  
      document.body.appendChild(a);  
      a.click();  
      a.remove();  
    }  
  
    function importData(event) {  
      const file = event.target.files[0];  
      if (!file) return;  
      const reader = new FileReader();  
      reader.onload = function(e) {  
        try {  
          const parsed = JSON.parse(e.target.result);  
          if (Array.isArray(parsed)) {  
            habits = parsed;  
            saveData();  
            render();  
          }  
        } catch (err) {  
          alert('Archivo JSON inválido.');  
        }  
      };  
      reader.readAsText(file);  
    }  
  
    function render() {  
      const tbody = document.getElementById('habitTableBody');  
      tbody.innerHTML = '';  
  
      let totalChecks = 0;  
      const totalPossible = habits.length * 7;  
      let bestStreak = 0;  
      let bestStreakName = 'Ninguna';  
      const dayTotals = [0, 0, 0, 0, 0, 0, 0];  
  
      habits.forEach(h => {  
        const tr = document.createElement('tr');  
        const completedCount = h.days.filter(Boolean).length;  
        totalChecks += completedCount;  
        const pct = Math.round((completedCount / 7) * 100);  
        const streak = getStreak(h.days);  
  
        if (streak > bestStreak) {  
          bestStreak = streak;  
          bestStreakName = h.name;  
        }  
  
        h.days.forEach((val, idx) => {  
          if (val) dayTotals[idx]++;  
        });  
  
        let daysHtml = '';  
        h.days.forEach((done, idx) => {  
          daysHtml += `<td>  
            <button class="day-btn ${done ? 'active' : ''}" onclick="toggleDay(${h.id}, ${idx})">✓</button>  
          </td>`;  
        });  
  
        tr.innerHTML = `  
          <td>  
            <span class="habit-name">${h.name}</span>  
            <span class="habit-cat">${h.cat}</span>  
          </td>  
          ${daysHtml}  
          <td><span class="streak-pill">🔥 ${streak}d</span></td>  
          <td>  
            <div class="progress-wrap"><div class="progress-fill" style="width:${pct}%"></div></div>  
            <span style="font-size:0.75rem">${pct}%</span>  
          </td>  
          <td><button class="del-btn" onclick="deleteHabit(${h.id})">✕</button></td>  
        `;  
        tbody.appendChild(tr);  
      });  
  
      // Actualizar KPIs  
      const overallRate = totalPossible > 0 ? Math.round((totalChecks / totalPossible) * 100) : 0;  
      document.getElementById('kpiRate').textContent = overallRate + '%';  
      document.getElementById('kpiChecks').textContent = `${totalChecks} de ${totalPossible} completados`;  
      document.getElementById('kpiStreak').textContent = `${bestStreak} días`;  
      document.getElementById('kpiStreakName').textContent = bestStreakName;  
      document.getElementById('kpiTotalHabits').textContent = habits.length;  
  
      let maxDayVal = -1;  
      let maxDayIndex = 0;  
      dayTotals.forEach((val, idx) => {  
        if (val > maxDayVal) {  
          maxDayVal = val;  
          maxDayIndex = idx;  
        }  
      });  
      document.getElementById('kpiBestDay').textContent = maxDayVal > 0 ? DAYS[maxDayIndex] : '-';  
      document.getElementById('kpiBestDayCount').textContent = `${maxDayVal > 0 ? maxDayVal : 0} hábitos cumplidos`;  
  
      // Renderizar Gráfico de Barras Diario  
      const barChart = document.getElementById('dailyBarChart');  
      barChart.innerHTML = '';  
      DAYS.forEach((dayName, idx) => {  
        const dayPct = habits.length > 0 ? Math.round((dayTotals[idx] / habits.length) * 100) : 0;  
        const col = document.createElement('div');  
        col.className = 'bar-col';  
        col.innerHTML = `  
          <div class="bar-val">${dayPct}%</div>  
          <div class="bar-visual" style="height: ${Math.max(dayPct, 4)}%"></div>  
          <div class="bar-day">${dayName}</div>  
        `;  
        barChart.appendChild(col);  
      });  
  
      // Renderizar Ranking de Rachas  
      const rankContainer = document.getElementById('streakRankContainer');  
      rankContainer.innerHTML = '';  
      const sorted = [...habits].sort((a, b) => getStreak(b.days) - getStreak(a.days));  
      sorted.forEach(h => {  
        const st = getStreak(h.days);  
        const stPct = Math.round((st / 7) * 100);  
        const row = document.createElement('div');  
        row.className = 'rank-row';  
        row.innerHTML = `  
          <div class="rank-head">  
            <span>${h.name}</span>  
            <strong style="color:#f59e0b">🔥 ${st} / 7 días</strong>  
          </div>  
          <div class="rank-track">  
            <div class="rank-fill" style="width:${stPct}%"></div>  
          </div>  
        `;  
        rankContainer.appendChild(row);  
      });  
    }  
  
    loadData();  
  </script>  
</body>  
</html>  
