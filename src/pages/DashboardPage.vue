<template>
  <div class="dashboard-layout">
    <button class="hamburger" @click="showSidebar = !showSidebar">
      <span></span>
      <span></span>
      <span></span>
    </button>

    <div v-if="showSidebar" class="sidebar-overlay" @click="showSidebar = false"></div>
    <aside class="sidebar" :class="{ open: showSidebar }">
      <div class="logo">Pagamentos</div>
      <nav>
        <ul>
          <li class="active"><span class="icon">🏠</span> Home</li>
          <li><span class="icon">📄</span> Contratos</li>
          <li><span class="icon">📁</span> Documentos</li>
          <li><span class="icon">🧾</span> Finanças</li>
          <li><span class="icon">💳</span> Transações</li>
          <li><span class="icon">🛡️</span> Seguro</li>
          <li><span class="icon">💳</span> Cartões</li>
        </ul>
      </nav>
      <ThemeToggle style="margin: 24px 0 0 24px" />
    </aside>
    <main class="dashboard-main">
      <header class="dashboard-header">
        <div>
          <h2>Saudações, António</h2>
          <p class="subtitle">Acompanhe as tuas transações e tuas finanças de um modo prático</p>
        </div>
        <button class="action-btn">Realizar transação</button>
      </header>
      <section class="metrics-cards">
        <div class="metric-card positive">
          <div class="metric-content">
            <div class="metric-info">
              <div class="metric-title">Ganhos Mensais</div>
              <div class="metric-value">$8,127.<span class="decimal">90</span></div>
              <div class="metric-trend">
                <span class="trend-up">+24%</span>
                <span class="trend-label">vs último mês</span>
              </div>
            </div>
            <MiniLineChart
              :chartData="positiveChartData"
              :chartOptions="miniChartOptions"
              style="height: 40px; width: 80px; margin-left: 12px"
            />
          </div>
        </div>

        <div class="metric-card negative">
          <div class="metric-content">
            <div class="metric-info">
              <div class="metric-title">Perdas mensais</div>
              <div class="metric-value">$8,127.<span class="decimal">90</span></div>
              <div class="metric-trend">
                <span class="trend-up">+24%</span>
                <span class="trend-label">vs último mês</span>
              </div>
            </div>
            <MiniLineChart
              :chartData="negativeChartData"
              :chartOptions="miniChartOptions"
              style="height: 40px; width: 80px; margin-left: 12px"
            />
          </div>
        </div>
      </section>
      <section class="dashboard-content">
        <div class="payment-history card">
          <div class="card-title">Histórico de Pagamentos</div>
          <div class="payment-value">$12,135.<span class="decimal">69</span></div>
          <div class="trend-up">+23% <span class="trend-label">vs último mês</span></div>
          <MiniLineChart
            :chartData="detailedPaymentChartData"
            :chartOptions="detailedPaymentChartOptions"
            style="height: 400px; width: 100%; margin-top: 12px"
          />
        </div>
        <div class="transaction-history card">
          <div class="card-title">Histórico de Transações</div>
          <ul class="transaction-list">
            <li v-for="user in users" :key="user.name">
              <span class="avatar">{{ user.initials }}</span>
              <span class="user-info">
                <span class="user-name">{{ user.name }}</span>
                <span class="user-desc">{{ user.desc }}</span>
              </span>
            </li>
          </ul>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'
import ThemeToggle from '../components/ThemeToggle.vue'
import MiniLineChart from '../components/MiniLineChart.vue'

const showSidebar = ref(false)

const positiveChartData = {
  labels: ['', '', '', '', '', ''],
  datasets: [
    {
      data: [2, 4, 3, 6, 5, 8],
      borderColor: '#22c55e',
      backgroundColor: 'rgba(34,197,94,0.12)',
      tension: 0.4,
      fill: true,
      pointRadius: 0,
      borderWidth: 2,
    },
  ],
}

const negativeChartData = {
  labels: ['', '', '', '', '', ''],
  datasets: [
    {
      data: [7, 6, 5, 4, 3, 2],
      borderColor: '#ef4444',
      backgroundColor: 'rgba(239,68,68,0.10)',
      tension: 0.4,
      fill: true,
      pointRadius: 0,
      borderWidth: 2,
    },
  ],
}

const miniChartOptions = {
  responsive: true,
  plugins: { legend: { display: false }, tooltip: { enabled: false } },
  scales: { x: { display: false }, y: { display: false } },
}

const users = [
  { initials: 'CF', name: 'Carlos Fernando', desc: 'Louis Vuitton' },
  { initials: 'EH', name: 'Esthr Hugo', desc: 'Starbucks' },
  { initials: 'WW', name: 'Wilson Walale', desc: 'Sony' },
  { initials: 'BS', name: 'Bruno Simões', desc: 'IBM' },
  { initials: 'RE', name: 'Raquel Elias', desc: 'Disney' },
  { initials: 'DR', name: 'Débora Ramos', desc: 'The Walt Disney Co.' },
]

const detailedPaymentChartData = {
  labels: [
    '01',
    '02',
    '03',
    '04',
    '05',
    '06',
    '07',
    '08',
    '09',
    '10',
    '11',
    '12',
    '13',
    '14',
    '15',
    '16',
    '17',
    '18',
    '19',
    '20',
    '21',
    '22',
    '23',
    '24',
    '25',
    '26',
    '27',
    '28',
    '29',
    '30',
  ],
  datasets: [
    {
      label: 'Pagamentos',
      data: [
        1200, 900, 1500, 800, 1700, 1600, 1400, 2000, 1800, 1700, 2100, 1900, 2200, 1700, 1600,
        2300, 2100, 2000, 2500, 2400, 2300, 2600, 2200, 2100, 2700, 2500, 2400, 2800, 2600, 2500,
      ],
      borderColor: '#38e6b0',
      backgroundColor: 'rgba(56,230,176,0.15)',
      tension: 0.4,
      fill: true,
      pointRadius: 2,
      borderWidth: 2,
    },
  ],
}

const detailedPaymentChartOptions = {
  responsive: true,
  plugins: {
    legend: { display: false },
    tooltip: { enabled: true },
  },
  scales: {
    x: {
      display: true,
      title: { display: true, text: 'Dia do mês' },
      grid: { display: false },
    },
    y: {
      display: true,
      title: { display: true, text: 'Valor (R$)' },
      grid: { color: '#e5e7eb' },
    },
  },
}

watch(showSidebar, (val) => {
  if (val) {
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = ''
  }
})
</script>

<style scoped>
.dashboard-layout {
  display: flex;
  min-height: 100vh;
  background: linear-gradient(120deg, #f6f8fa 60%, #e6f9f3 100%);
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

.hamburger {
  display: none;
  position: fixed;
  top: 18px;
  right: 18px;
  z-index: 1001;
  width: 38px;
  height: 38px;
  background: #fff;
  border: none;
  border-radius: 8px;
  box-shadow: 0 2px 8px 0 rgba(56, 230, 176, 0.1);
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 5px;
  cursor: pointer;
  padding: 6px;
  transition: background 0.2s;
}
.hamburger span {
  display: block;
  width: 22px;
  height: 3px;
  background: #38e6b0;
  border-radius: 2px;
  margin: 3px 0;
  transition: all 0.3s;
}

.sidebar-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.18);
  z-index: 999;
  display: block;
}

.sidebar {
  width: 220px;
  background: #fff;
  border-right: 1px solid #e5e7eb;
  display: flex;
  flex-direction: column;
  padding: 32px 0 16px 0;
  min-height: 100vh;
  box-shadow: 2px 0 16px 0 rgba(56, 230, 176, 0.06);
  transition:
    width 0.3s,
    transform 0.3s;
  z-index: 1000;
}

.logo {
  font-weight: bold;
  font-size: 1.4rem;
  color: #38e6b0;
  padding: 0 32px 32px 32px;
  letter-spacing: 1px;
  text-shadow: 0 2px 8px #e6f9f3;
}

.sidebar nav ul {
  list-style: none;
  padding: 0 0 0 16px;
  margin: 0;
}

.sidebar nav li {
  display: flex;
  align-items: center;
  padding: 12px 16px;
  color: #64748b;
  border-radius: 10px 0 0 10px;
  margin-bottom: 6px;
  cursor: pointer;
  transition:
    background 0.2s,
    color 0.2s,
    font-weight 0.2s;
  font-size: 1.05rem;
  font-weight: 500;
}

.sidebar nav li.active,
.sidebar nav li:hover {
  background: #e6f9f3;
  color: #38e6b0;
  font-weight: 700;
  box-shadow: 0 2px 8px 0 rgba(56, 230, 176, 0.08);
}

.icon {
  margin-right: 12px;
  font-size: 1.15em;
}

.dashboard-main {
  flex: 1;
  padding: 40px 40px 32px 40px;
  min-width: 0;
  display: flex;
  flex-direction: column;
}

.dashboard-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 32px;
  gap: 16px;
}

.dashboard-header h2 {
  margin: 0;
  font-size: 2.1rem;
  color: #222;
  font-weight: 800;
  letter-spacing: 0.5px;
}

.subtitle {
  color: #64748b;
  font-size: 1.13rem;
  margin-top: 4px;
}

.action-btn {
  background: linear-gradient(90deg, #38e6b0 60%, #2fd39e 100%);
  color: #fff;
  border: none;
  border-radius: 10px;
  padding: 13px 28px;
  font-size: 1.08rem;
  font-weight: 700;
  cursor: pointer;
  box-shadow: 0 2px 8px 0 rgba(56, 230, 176, 0.1);
  transition:
    background 0.2s,
    transform 0.2s;
}
.action-btn:hover {
  background: linear-gradient(90deg, #2fd39e 60%, #38e6b0 100%);
  transform: translateY(-2px) scale(1.03);
}

.metrics-cards {
  display: flex;
  gap: 12px;
  margin-bottom: 32px;
  flex-wrap: wrap;
  justify-content: flex-start;
}

.metric-card {
  background: #fff;
  border-radius: 18px;
  box-shadow: 0 2px 16px 0 rgba(31, 38, 135, 0.09);
  padding: 14px 80px;
  min-width: 240px;
  flex: 1 1 180px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  transition:
    box-shadow 0.2s,
    transform 0.2s;
}

.metric-content {
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
}
.metric-info {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  flex: 1;
}

.metric-title,
.metric-value,
.metric-trend {
  text-align: left;
  width: 90%;
}

.metric-card:hover {
  box-shadow: 0 4px 24px 0 rgba(56, 230, 176, 0.13);
  transform: translateY(-2px) scale(1.09);
}

.metric-title {
  color: #64748b;
  font-size: 1.07rem;
  margin-bottom: 8px;
  font-weight: 600;
}

.metric-value {
  font-size: 2.3rem;
  font-weight: 800;
  color: #222;
  margin-bottom: 8px;
  letter-spacing: 0.5px;
}

.metric-value .decimal {
  font-size: 1.2rem;
  color: #b0b8c1;
}

.metric-trend {
  display: flex;
  align-items: center;
  gap: 8px;
}

.trend-up {
  color: #22c55e;
  background: #e6f9f3;
  border-radius: 8px;
  padding: 2px 10px;
  font-size: 1rem;
  font-weight: 700;
}

.trend-down {
  color: #ef4444;
  background: #fbeaea;
  border-radius: 8px;
  padding: 2px 10px;
  font-size: 1rem;
  font-weight: 700;
}

.trend-label {
  color: #64748b;
  font-size: 0.98rem;
}

.dashboard-content {
  display: flex;
  gap: 24px;
  flex-wrap: wrap;
}

.card {
  background: #fff;
  border-radius: 18px;
  box-shadow: 0 2px 16px 0 rgba(31, 38, 135, 0.09);
  padding: 28px 36px;
  flex: 1 1 340px;
  min-width: 260px;
  display: flex;
  flex-direction: column;
  margin-bottom: 24px;
  transition:
    box-shadow 0.2s,
    transform 0.2s;
}
.card:hover {
  box-shadow: 0 4px 24px 0 rgba(56, 230, 176, 0.13);
  transform: translateY(-2px) scale(1.09);
}

.payment-history .card-title,
.transaction-history .card-title {
  font-size: 1.13rem;
  color: #222;
  font-weight: 700;
  margin-bottom: 12px;
  letter-spacing: 0.2px;
}

.payment-value {
  font-size: 1.35rem;
  font-weight: 700;
  color: #222;
  margin-bottom: 8px;
}

.payment-value .decimal {
  font-size: 1rem;
  color: #b0b8c1;
}

.graph-img {
  width: 100%;
  max-width: 400px;
  margin-top: 18px;
  border-radius: 12px;
  background: #e6f9f3;
}

.transaction-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.transaction-list li {
  display: flex;
  align-items: center;
  margin-bottom: 16px;
  border-bottom: 1px solid #f1f5f9;
  padding-bottom: 10px;
  transition: background 0.2s;
}
.transaction-list li:last-child {
  border-bottom: none;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: linear-gradient(135deg, #38e6b0 60%, #2fd39e 100%);
  color: #fff;
  font-weight: 700;
  font-size: 1.15rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 14px;
  box-shadow: 0 2px 8px 0 rgba(56, 230, 176, 0.1);
}

.user-info {
  display: flex;
  flex-direction: column;
}

.user-name {
  font-weight: 700;
  color: #222;
  font-size: 1.05rem;
}

.user-desc {
  color: #64748b;
  font-size: 0.97rem;
}

@media (max-width: 1100px) {
  .dashboard-content {
    flex-direction: column;
    gap: 18px;
  }
  .metrics-cards {
    flex-direction: column;
    gap: 18px;
  }
}

@media (max-width: 900px) {
  .hamburger {
    display: flex;
  }
  .sidebar {
    position: fixed;
    top: 0;
    right: 0;
    left: auto;
    height: 100vh;
    width: 220px;
    background: #fff;
    box-shadow: -2px 0 16px 0 rgba(56, 230, 176, 0.1);
    transform: translateX(100%);
    transition: transform 0.3s;
    z-index: 1000;
    border-radius: 0 0 0 0;
    border-bottom: none;
    border-right: none;
    flex-direction: column;
    padding-top: 48px;
  }
  .sidebar.open {
    transform: translateX(0);
  }
  .dashboard-layout {
    flex-direction: column;
  }
  .logo {
    padding: 16px;
    font-size: 1.15rem;
  }
  .sidebar nav ul {
    display: flex;
    flex-direction: column;
    padding: 0 8px;
  }
  .sidebar nav li {
    border-radius: 8px;
    margin: 0 4px;
    padding: 10px 10px;
    font-size: 0.98rem;
  }
  .settings {
    display: none;
  }
  .dashboard-main {
    padding: 18px 2vw;
  }
  .metrics-cards {
    flex-direction: column;
    gap: 16px;
    padding: 0;
  }
  .card,
  .metric-card {
    min-width: 0;
    width: 100%;
    box-sizing: border-box;
  }
}

@media (max-width: 600px) {
  .dashboard-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
  }
  .dashboard-header h2 {
    font-size: 1.1rem;
  }
  .dashboard-main {
    padding: 10px 2vw;
  }
  .metrics-cards {
    flex-direction: column;
    gap: 10px;
    margin-bottom: 18px;
    padding: 0;
  }
  .dashboard-content {
    gap: 10px;
  }
  .card,
  .metric-card {
    padding: 12px 6px;
    border-radius: 10px;
    min-width: 0;
    width: 100%;
    box-sizing: border-box;
  }
  .logo {
    font-size: 1rem;
    padding: 10px;
  }
  .sidebar nav li {
    font-size: 0.93rem;
    padding: 8px 6px;
  }
  .avatar {
    width: 32px;
    height: 32px;
    font-size: 1rem;
    margin-right: 8px;
  }
  .payment-value {
    font-size: 1.1rem;
  }
}

@media (max-width: 400px) {
  .logo {
    font-size: 0.95rem;
    padding: 6px;
  }
  .sidebar nav li {
    font-size: 0.85rem;
    padding: 6px 2px;
  }
}

body.dark-theme {
  background: #181a20;
}

body.dark-theme .dashboard-layout {
  background: linear-gradient(120deg, #23272f 60%, #181a20 100%);
}

body.dark-theme .sidebar {
  background: #23272f;
  border-right: 1px solid #23272f;
  box-shadow: 2px 0 16px 0 rgba(56, 230, 176, 0.02);
}

body.dark-theme .logo {
  color: #38e6b0;
  text-shadow: 0 2px 8px #23272f;
}

body.dark-theme .sidebar nav li,
body.dark-theme .sidebar nav li.active,
body.dark-theme .sidebar nav li:hover {
  color: #b0b8c1;
  background: none;
  box-shadow: none;
}

body.dark-theme .sidebar nav li.active,
body.dark-theme .sidebar nav li:hover {
  background: #23272f;
  color: #38e6b0;
}

body.dark-theme .dashboard-main {
  background: transparent;
}

body.dark-theme .card,
body.dark-theme .metric-card {
  background: #23272f;
  color: #f1f5f9;
  box-shadow: 0 2px 16px 0 rgba(31, 38, 135, 0.03);
}

body.dark-theme .dashboard-header h2,
body.dark-theme .card-title,
body.dark-theme .user-name,
body.dark-theme .metric-value,
body.dark-theme .payment-value {
  color: #f1f5f9;
}

body.dark-theme .subtitle,
body.dark-theme .user-desc,
body.dark-theme .trend-label {
  color: #b0b8c1;
}

body.dark-theme .action-btn {
  background: linear-gradient(90deg, #38e6b0 60%, #2fd39e 100%);
  color: #181a20;
}

body.dark-theme .avatar {
  background: linear-gradient(135deg, #38e6b0 60%, #2fd39e 100%);
  color: #181a20;
}

body.dark-theme .graph-img {
  background: #23272f;
}
.transaction-history.card {
  max-width: 340px;
  min-width: 220px;
  flex: 1 1 220px;
  padding: 24px 18px;
}
.metric-card.positive {
  border-left: 3px solid #22c55e;
  border: solid #22c55e;
}

.metric-card.negative {
  border-left: 3px solid #ef4444;
  border: solid #ef4444;
}
</style>
