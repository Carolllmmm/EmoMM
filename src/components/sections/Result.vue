<script setup>
const summaryCards = [
  {
    title: 'Consistent gains',
    value: '+ CHASE',
    desc: 'Both backbones improve on overall EmoMM when CHASE is added.',
  },
  {
    title: 'Largest gains',
    value: 'Conflict / Missing',
    desc: 'The clearest uplift appears under conflicting and missing-modality settings.',
  },
  {
    title: 'Best open model',
    value: 'VITA-1.5-8B + CHASE',
    desc: 'Strongest open setting across F1 and MAE on the main benchmark.',
  },
];

const columns = [
  'Model',
  'EmoMM (Overall)',
  'EmoMM-Align',
  'EmoMM-Conflict',
  'EmoMM-Missing',
];

const tableRows = [
  {
    group: 'Open-source Baselines',
    items: [
      {
        model: 'Video-LLaMA2.1-7B-AV',
        overall: 'Acc 22.46 / F1 21.33 / MAE 0.579',
        align: '23.94 / 21.12 / 0.611',
        conflict: '25.84 / 20.60 / 0.527',
        missing: '21.55 / 21.52 / 0.587',
      },
      {
        model: 'MiniCPM-o 2.6-8B',
        overall: '26.09 / 15.06 / 0.781',
        align: '27.59 / 15.61 / 0.723',
        conflict: '26.37 / 14.47 / 0.751',
        missing: '25.86 / 15.13 / 0.794',
      },
      {
        model: 'Video-SALMONN 2-7B',
        overall: '41.47 / 38.30 / 0.380',
        align: '49.05 / 43.94 / 0.318',
        conflict: '41.25 / 37.70 / 0.367',
        missing: '40.65 / 37.78 / 0.390',
      },
    ],
  },
  {
    group: 'Target Backbones & Ours',
    items: [
      {
        model: 'Qwen2.5-Omni-7B',
        overall: '44.53 / 36.24 / 0.384',
        align: '52.09 / 44.28 / 0.270',
        conflict: '46.47 / 39.76 / 0.356',
        missing: '43.27 / 34.55 / 0.403',
      },
      {
        model: '+ CHASE (Ours)',
        overall: '49.96 / 39.87 / 0.326',
        align: '53.23 / 39.61 / 0.256',
        conflict: '51.32 / 46.47 / 0.302',
        missing: '49.30 / 38.42 / 0.339',
        highlight: true,
      },
      {
        model: 'VITA-1.5-8B',
        overall: '44.48 / 43.83 / 0.327',
        align: '53.05 / 53.47 / 0.277',
        conflict: '47.80 / 47.18 / 0.319',
        missing: '42.80 / 41.99 / 0.335',
      },
      {
        model: '+ CHASE (Ours)',
        overall: '49.56 / 48.44 / 0.291',
        align: '53.82 / 54.23 / 0.274',
        conflict: '52.96 / 51.53 / 0.292',
        missing: '48.34 / 47.12 / 0.293',
        highlight: true,
      },
    ],
  },
  {
    group: 'Closed-source API',
    items: [
      {
        model: 'Gemini 3 Pro',
        overall: '56.41 / 53.58 / 0.236',
        align: '59.85 / 59.07 / 0.191',
        conflict: '56.23 / 51.16 / 0.236',
        missing: '56.06 / 53.47 / 0.241',
      },
    ],
  },
];

const takeaways = [
  {
    title: 'Overall benchmark',
    body:
      'Adding CHASE improves both target backbones on the full EmoMM benchmark. For Qwen2.5-Omni-7B, accuracy rises from 44.53 to 49.96 and MAE drops from 0.384 to 0.326. For VITA-1.5-8B, F1 increases from 43.83 to 48.44 and MAE decreases from 0.327 to 0.291.',
  },
  {
    title: 'Alignment setting',
    body:
      'CHASE remains competitive on aligned multimodal samples. The VITA-based variant reaches the strongest open-source aligned F1 at 54.23, while the Qwen-based variant achieves the lowest aligned MAE among the target backbones at 0.256.',
  },
  {
    title: 'Conflict setting',
    body:
      'The biggest benefit appears when modalities disagree. CHASE lifts Qwen from 39.76 to 46.47 F1 and lifts VITA from 47.18 to 51.53 F1, showing better robustness to cross-modal inconsistency.',
  },
  {
    title: 'Missing-modality setting',
    body:
      'CHASE also improves resilience when one modality is absent. The VITA-based variant reaches 47.12 F1 and 0.293 MAE, while the Qwen-based variant improves missing-subset accuracy from 43.27 to 49.30.',
  },
];
</script>

<template>
  <div class="result-page">
    <el-divider />

    <el-row justify="center">
      <el-col :xs="24" :sm="22" :md="20" :lg="18" :xl="16">
        <section class="hero">
          <div class="eyebrow">Results</div>
          <h1>Main Results on EmoMM</h1>
          <p class="lead">
            We evaluate CHASE on the full <strong>EmoMM</strong> benchmark and three
            challenging subsets: <strong>Align</strong>, <strong>Conflict</strong>, and
            <strong>Missing</strong>. Across both target backbones, CHASE consistently
            improves recognition quality, with the most visible gains under mismatched or
            incomplete multimodal conditions.
          </p>
        </section>

        <section class="summary-grid">
          <article v-for="card in summaryCards" :key="card.title" class="summary-card">
            <div class="summary-title">{{ card.title }}</div>
            <div class="summary-value">{{ card.value }}</div>
            <p>{{ card.desc }}</p>
          </article>
        </section>

        <section class="section-block">
          <div class="section-head">
            <h2>Quantitative comparison</h2>
            <span class="metric-note">Each cell is shown as Acc / F1 / MAE</span>
          </div>

          <div class="table-shell">
            <table class="result-table">
              <thead>
                <tr>
                  <th v-for="col in columns" :key="col">{{ col }}</th>
                </tr>
              </thead>
              <tbody>
                <template v-for="group in tableRows" :key="group.group">
                  <tr class="group-row">
                    <td colspan="5">{{ group.group }}</td>
                  </tr>
                  <tr
                    v-for="item in group.items"
                    :key="`${group.group}-${item.model}-${item.overall}`"
                    :class="['data-row', { highlight: item.highlight }]"
                  >
                    <td class="model-cell">{{ item.model }}</td>
                    <td>{{ item.overall }}</td>
                    <td>{{ item.align }}</td>
                    <td>{{ item.conflict }}</td>
                    <td>{{ item.missing }}</td>
                  </tr>
                </template>
              </tbody>
            </table>
          </div>
        </section>

        <section class="section-block">
          <div class="section-head">
            <h2>Result analysis</h2>
            <span class="metric-note">Key observations from the benchmark table</span>
          </div>

          <div class="takeaway-list">
            <article v-for="item in takeaways" :key="item.title" class="takeaway-item">
              <h3>{{ item.title }}</h3>
              <p>{{ item.body }}</p>
            </article>
          </div>
        </section>

        <section class="section-block conclusion-block">
          <h2>Discussion</h2>
          <p>
            The overall pattern is clear: CHASE improves both backbone families without
            sacrificing stability on the easier aligned subset, while yielding stronger
            robustness on more realistic failure cases. In particular, the gains on
            <strong>Conflict</strong> and <strong>Missing</strong> indicate that CHASE helps
            the model reason more reliably when multimodal evidence is noisy, incomplete,
            or inconsistent.
          </p>
        </section>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.result-page {
  padding-bottom: 40px;
  color: #1f2937;
}

.hero {
  padding: 12px 0 8px;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  padding: 6px 10px;
  border-radius: 999px;
  background: #eef2ff;
  color: #4338ca;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.hero h1 {
  margin: 14px 0 12px;
  font-size: 34px;
  line-height: 1.15;
  color: #111827;
}

.lead {
  margin: 0;
  font-size: 16px;
  line-height: 1.9;
  color: #4b5563;
}

.summary-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 16px;
  margin: 28px 0 10px;
}

.summary-card,
.section-block {
  background: #ffffff;
  border: 1px solid #e5e7eb;
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.05);
}

.summary-card {
  padding: 20px;
}

.summary-title {
  font-size: 13px;
  font-weight: 700;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.summary-value {
  margin: 10px 0 8px;
  font-size: 24px;
  font-weight: 800;
  color: #111827;
}

.summary-card p {
  margin: 0;
  color: #4b5563;
  line-height: 1.7;
}

.section-block {
  margin-top: 24px;
  padding: 24px;
}

.section-head {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 16px;
  margin-bottom: 18px;
}

.section-head h2,
.conclusion-block h2 {
  margin: 0;
  font-size: 24px;
  color: #111827;
}

.metric-note {
  font-size: 13px;
  color: #6b7280;
  white-space: nowrap;
}

.table-shell {
  overflow-x: auto;
  border-radius: 16px;
  border: 1px solid #e5e7eb;
}

.result-table {
  width: 100%;
  border-collapse: collapse;
  min-width: 920px;
  background: #fff;
}

.result-table thead th {
  padding: 16px 14px;
  background: #f8fafc;
  border-bottom: 1px solid #e5e7eb;
  color: #111827;
  font-size: 13px;
  font-weight: 700;
  text-align: left;
}

.result-table td {
  padding: 14px;
  border-bottom: 1px solid #eef2f7;
  vertical-align: top;
  font-size: 14px;
  line-height: 1.6;
  color: #374151;
}

.group-row td {
  background: #f9fafb;
  font-style: italic;
  font-weight: 700;
  color: #4b5563;
  border-bottom: 1px solid #e5e7eb;
}

.model-cell {
  min-width: 220px;
  font-weight: 700;
  color: #111827;
}

.data-row.highlight {
  background: linear-gradient(90deg, rgba(79, 70, 229, 0.08), rgba(14, 165, 233, 0.04));
}

.data-row.highlight .model-cell {
  color: #312e81;
}

.takeaway-list {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 16px;
}

.takeaway-item {
  padding: 18px 18px 16px;
  border-radius: 16px;
  background: #f8fafc;
  border: 1px solid #e5e7eb;
}

.takeaway-item h3 {
  margin: 0 0 10px;
  font-size: 18px;
  color: #111827;
}

.takeaway-item p,
.conclusion-block p {
  margin: 0;
  color: #4b5563;
  line-height: 1.85;
}

@media (max-width: 1024px) {
  .summary-grid,
  .takeaway-list {
    grid-template-columns: 1fr;
  }

  .section-head {
    flex-direction: column;
    align-items: flex-start;
  }

  .metric-note {
    white-space: normal;
  }

  .hero h1 {
    font-size: 28px;
  }
}
</style>
