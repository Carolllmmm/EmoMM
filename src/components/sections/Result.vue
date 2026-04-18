<script setup>
const tableRows = [
  {
    type: 'group',
    label: 'Open-source Baselines',
  },
  {
    type: 'data',
    model: 'Video-LLaMA2.1-7B-AV',
    overall: { acc: '22.46', f1: '21.33', mae: '0.579' },
    align: { acc: '23.94', f1: '21.12', mae: '0.611' },
    conflict: { acc: '25.84', f1: '20.60', mae: '0.527' },
    missing: { acc: '21.55', f1: '21.52', mae: '0.587' },
  },
  {
    type: 'data',
    model: 'MiniCPM-o 2.6-8B',
    overall: { acc: '26.09', f1: '15.06', mae: '0.781' },
    align: { acc: '27.59', f1: '15.61', mae: '0.723' },
    conflict: { acc: '26.37', f1: '14.47', mae: '0.751' },
    missing: { acc: '25.86', f1: '15.13', mae: '0.794' },
  },
  {
    type: 'data',
    model: 'Video-SALMONN 2-7B',
    overall: { acc: '41.47', f1: '38.30', mae: '0.380' },
    align: { acc: '49.05', f1: '43.94', mae: '0.318' },
    conflict: { acc: '41.25', f1: '37.70', mae: '0.367' },
    missing: { acc: '40.65', f1: '37.78', mae: '0.390' },
  },
  {
    type: 'group',
    label: 'Target Backbones & Ours',
  },
  {
    type: 'data',
    model: 'Qwen2.5-Omni-7B',
    overall: { acc: '44.53', f1: '36.24', mae: '0.384' },
    align: { acc: '52.09', f1: '44.28', mae: '0.270' },
    conflict: { acc: '46.47', f1: '39.76', mae: '0.356' },
    missing: { acc: '43.27', f1: '34.55', mae: '0.403' },
  },
  {
    type: 'data',
    model: '+ CHASE (Ours)',
    highlight: true,
    overall: { acc: '49.96', f1: '39.87', mae: '0.326', accBold: true },
    align: { acc: '53.23', f1: '39.61', mae: '0.256', maeBold: true },
    conflict: { acc: '51.32', f1: '46.47', mae: '0.302' },
    missing: { acc: '49.30', f1: '38.42', mae: '0.339', accBold: true },
  },
  {
    type: 'data',
    model: 'VITA-1.5-8B',
    overall: { acc: '44.48', f1: '43.83', mae: '0.327' },
    align: { acc: '53.05', f1: '53.47', mae: '0.277' },
    conflict: { acc: '47.80', f1: '47.18', mae: '0.319' },
    missing: { acc: '42.80', f1: '41.99', mae: '0.335' },
  },
  {
    type: 'data',
    model: '+ CHASE (Ours)',
    highlight: true,
    overall: { acc: '49.56', f1: '48.44', mae: '0.291', f1Bold: true, maeBold: true },
    align: { acc: '53.82', f1: '54.23', mae: '0.274', accBold: true, f1Bold: true },
    conflict: { acc: '52.96', f1: '51.53', mae: '0.292', accBold: true, f1Bold: true, maeBold: true },
    missing: { acc: '48.34', f1: '47.12', mae: '0.293', f1Bold: true, maeBold: true },
  },
  {
    type: 'group',
    label: 'Closed-source API',
  },
  {
    type: 'data',
    model: 'Gemini 3 Pro',
    overall: { acc: '56.41', f1: '53.58', mae: '0.236' },
    align: { acc: '59.85', f1: '59.07', mae: '0.191' },
    conflict: { acc: '56.23', f1: '51.16', mae: '0.236' },
    missing: { acc: '56.06', f1: '53.47', mae: '0.241' },
  },
];

const metricKeys = ['overall', 'align', 'conflict', 'missing'];

const renderValue = (metric, key) => ({
  value: metric[key],
  bold: Boolean(metric[`${key}Bold`]),
});
</script>

<template>
  <div class="result-page">
    <el-divider />

    <el-row justify="center">
      <el-col :xs="24" :sm="22" :md="20" :lg="18" :xl="18">
        <div class="section-title">Result</div>

        <div class="table-outer">
          <div class="table-wrap">
            <table class="result-table">
              <thead>
                <tr>
                  <th rowspan="2" class="model-header">Model</th>
                  <th colspan="3">EmoMM (Overall)</th>
                  <th colspan="3">EmoMM-Align</th>
                  <th colspan="3">EmoMM-Conflict</th>
                  <th colspan="3">EmoMM-Missing</th>
                </tr>
                <tr>
                  <template v-for="section in 4" :key="section">
                    <th>Acc↑</th>
                    <th>F1↑</th>
                    <th>MAE↓</th>
                  </template>
                </tr>
              </thead>

              <tbody>
                <template v-for="row in tableRows" :key="row.type === 'group' ? row.label : `${row.model}-${row.overall.acc}`">
                  <tr v-if="row.type === 'group'" class="group-row">
                    <td colspan="13">{{ row.label }}</td>
                  </tr>

                  <tr v-else :class="['data-row', { highlight: row.highlight }]">
                    <td class="model-cell">{{ row.model }}</td>
                    <template v-for="metricKey in metricKeys" :key="`${row.model}-${metricKey}`">
                      <td>
                        <span :class="{ strong: renderValue(row[metricKey], 'acc').bold }">
                          {{ renderValue(row[metricKey], 'acc').value }}
                        </span>
                      </td>
                      <td>
                        <span :class="{ strong: renderValue(row[metricKey], 'f1').bold }">
                          {{ renderValue(row[metricKey], 'f1').value }}
                        </span>
                      </td>
                      <td>
                        <span :class="{ strong: renderValue(row[metricKey], 'mae').bold }">
                          {{ renderValue(row[metricKey], 'mae').value }}
                        </span>
                      </td>
                    </template>
                  </tr>
                </template>
              </tbody>
            </table>
          </div>
        </div>

        <p class="caption">
          Table 1: Main results on EmoMM and its subsets. CHASE consistently improves performance across both backbones, with the most significant gains observed in Conflict and Missing subsets.
        </p>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.result-page {
  width: 100%;
}

.section-title {
  margin: 0 0 18px;
  text-align: center;
  font-size: 1.7rem;
  font-weight: 600;
  font-style: italic;
  letter-spacing: 0.01em;
  line-height: 1.2;
  color: #111827;
}

.table-outer {
  width: 100%;
  display: flex;
  justify-content: center;
}

.table-wrap {
  width: fit-content;
  max-width: 100%;
  margin: 0 auto;
  overflow-x: auto;
}

.result-table {
  margin: 0 auto;
  border-collapse: collapse;
  font-size: 15px;
  line-height: 1.45;
  color: #1f2937;
  border-top: 2px solid #111827;
  border-bottom: 2px solid #111827;
}

.result-table th,
.result-table td {
  padding: 10px 12px;
  text-align: center;
  border-bottom: 1px solid #e5e7eb;
  white-space: nowrap;
}

.result-table thead th {
  font-weight: 700;
  color: #0f172a;
}

.result-table thead tr:first-child th {
  padding-top: 12px;
  padding-bottom: 6px;
  border-bottom: 0;
}

.result-table thead tr:last-child th {
  padding-top: 4px;
  padding-bottom: 10px;
  border-bottom: 1.5px solid #94a3b8;
}

.model-header,
.model-cell {
  text-align: left !important;
}

.model-header {
  min-width: 150px;
}

.model-cell {
  font-weight: 500;
}

.group-row td {
  padding: 9px 12px;
  text-align: left;
  font-style: italic;
  color: #64748b;
  background: #ffffff;
  border-top: 1px solid #cbd5e1;
  border-bottom: 0;
}

.data-row.highlight {
  background: #eef6ff;
}

.data-row.highlight .model-cell {
  color: #0f4c81;
  font-weight: 600;
}

.strong {
  font-weight: 700;
}

.caption {
  margin: 14px auto 0;
  width: fit-content;
  max-width: 100%;
  font-size: 16px;
  line-height: 1.7;
  color: #111827;
}

@media (max-width: 768px) {
  .section-title {
    font-size: 1.45rem;
    margin-bottom: 16px;
  }

  .result-table {
    font-size: 14px;
  }

  .result-table th,
  .result-table td {
    padding: 8px 10px;
  }

  .caption {
    font-size: 14px;
  }
}
</style>
