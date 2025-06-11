# Dashboard Web – Tech Avaluation

Dashboard web moderna para visualização de métricas financeiras, histórico de pagamentos, transações e navegação lateral, com suporte a tema escuro/claro e gráficos dinâmicos.

---

## Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Estrutura de Pastas](#estrutura-de-pastas)
- [Componentes Principais](#componentes-principais)
- [Tema Escuro/Claro](#tema-escuroclaro)
- [Gráficos](#gráficos)
- [Responsividade](#responsividade)
- [Como Rodar o Projeto](#como-rodar-o-projeto)
- [Dependências](#dependências)
- [Customização](#customização)
- [Boas Práticas](#boas-práticas)

---

## Visão Geral

Este projeto é um dashboard financeiro desenvolvido em Vue 3 (Quasar), com foco em experiência visual, responsividade e facilidade de customização. Permite acompanhar ganhos, perdas, histórico de pagamentos e transações, com gráficos interativos e alternância de tema.

---

## Funcionalidades

- **Sidebar** com navegação e ícones.
- **Cards de Métricas** (ganhos/perdas) com gráficos de linha.
- **Histórico de Pagamentos** com gráfico detalhado e seleção de período.
- **Histórico de Transações** com lista de usuários e empresas.
- **Tema escuro/claro** com toggle.
- **Responsividade** para desktop, tablet e mobile.

---

## Estrutura de Pastas

```
src/
  components/
    MiniLineChart.vue
    ThemeToggle.vue
    PieChart.vue (opcional)
  pages/
    DashboardPage.vue
  assets/
    (imagens, ícones, etc)
main.js
App.vue
```

---

## Componentes Principais

### DashboardPage.vue

- Página principal do dashboard.
- Contém sidebar, header, cards de métricas, histórico de pagamentos e transações.
- Usa os componentes `MiniLineChart` e `ThemeToggle`.

### MiniLineChart.vue

- Wrapper para gráficos de linha usando [vue-chartjs](https://vue-chartjs.org/).
- Recebe `chartData` e `chartOptions` como props.

### ThemeToggle.vue

- Componente para alternar entre tema escuro e claro.
- Salva a preferência no `localStorage` e aplica a classe no `<body>`.

### PieChart.vue (opcional)

- Componente para gráficos circulares (pie/donut), caso queira usar em cards de distribuição.

---

## Tema Escuro/Claro

- O tema é alternado via `ThemeToggle.vue`.
- A classe `dark-theme` é adicionada ao `<body>`.
- Estilos específicos para o tema escuro são definidos no CSS usando o seletor `body.dark-theme`.

---

## Gráficos

- Utiliza [vue-chartjs](https://vue-chartjs.org/) e [Chart.js](https://www.chartjs.org/).
- Os dados dos gráficos são definidos no `<script setup>` de cada página/componente.
- O gráfico de histórico de pagamentos é detalhado, com labels para cada dia do mês e tooltips customizados.

---

## Responsividade

- Layout flexível com media queries para diferentes larguras de tela.
- Sidebar vira drawer em telas pequenas.
- Cards e conteúdo se adaptam para mobile.

---

## Como Rodar o Projeto

1. **Instale as dependências:**

   ```bash
   yarn
   # ou
   npm install
   ```

2. **Rode o projeto em modo desenvolvimento:**

   ```bash
   quasar dev
   ```

3. **Acesse no navegador:**

   ```
   http://localhost:5173/
   ```

4. **Build para produção:**

   ```bash
   quasar build
   ```

5. **Lint e format:**
   ```bash
   yarn lint
   yarn format
   # ou
   npm run lint
   npm run format
   ```

---

## Dependências

- [Vue 3](https://vuejs.org/)
- [Quasar Framework](https://quasar.dev/)
- [vue-chartjs](https://vue-chartjs.org/)
- [chart.js](https://www.chartjs.org/)

---

## Customização

- **Cores:** Altere as cores principais nas classes CSS para personalizar o visual.
- **Dados:** Os dados dos gráficos e listas podem ser alterados diretamente nos arrays do `<script setup>`.
- **Sidebar:** Adicione ou remova itens de navegação conforme necessário.
- **Cards:** Crie novos cards de métricas ou gráficos conforme a necessidade do seu negócio.

---

## Boas Práticas

- **Componentize** sempre que possível para facilitar manutenção.
- **Use props** para passar dados dinâmicos para os gráficos.
- **Prefira CSS scoped** para evitar conflitos de estilo.
- **Mantenha os dados dos gráficos e listas em arrays/objetos** para fácil atualização.
- **Adapte o layout para mobile** usando media queries.
- **Salve a preferência de tema** no localStorage para melhor experiência do usuário.
- **Documente** novos componentes e funcionalidades para facilitar o onboarding de outros desenvolvedores.

---

## Exemplo de Uso de Gráfico

```vue
<MiniLineChart
  :chartData="detailedPaymentChartData"
  :chartOptions="detailedPaymentChartOptions"
  style="height: 220px; width: 100%; margin-top: 8px"
/>
```

---

## Contato

Dúvidas ou sugestões? Entre em contato com o time de desenvolvimento.

---

**Este projeto é um ponto de partida para dashboards modernos e customizáveis em Vue/Quasar. Sinta-se à vontade para evoluir conforme as necessidades do seu produto!**
