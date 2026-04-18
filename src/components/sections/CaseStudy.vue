<script setup>
import { ref } from 'vue'

const activeTab = ref('0')

const CASES = [
  {
    id: 'CMU-MOSI:2018:0018_0h-zjBukYpk_19',
    combo: 'TAV', dataset: 'CMU-MOSI', bucket: 'Conflict',
    gt: 'WN', baseline: 'P', chase: 'WN',
    eta: 0.600, tau: 0.700, topk: 4,
    layers: [
      { l: 13, s: true,  p: 0.959, b: [0.7436, 0.2319, 0.0245], a: [0.7069, 0.2470, 0.0461] },
      { l: 14, s: true,  p: 0.960, b: [0.7244, 0.2152, 0.0605], a: [0.6847, 0.2330, 0.0823] },
      { l: 15, s: true,  p: 0.960, b: [0.7234, 0.2501, 0.0265], a: [0.6824, 0.2685, 0.0491] },
      { l: 16, s: true,  p: 0.959, b: [0.6921, 0.2814, 0.0264], a: [0.6508, 0.2999, 0.0493] },
      { l: 17, s: true,  p: 0.958, b: [0.8324, 0.1584, 0.0092], a: [0.7875, 0.1802, 0.0323] },
      { l: 18, s: true,  p: 0.958, b: [0.8138, 0.1778, 0.0084], a: [0.7655, 0.2029, 0.0316] },
      { l: 19, s: true,  p: 0.956, b: [0.7822, 0.1692, 0.0130], a: [0.7350, 0.1925, 0.0368] },
      { l: 20, s: true,  p: 0.954, b: [0.7853, 0.1620, 0.0170], a: [0.7364, 0.1876, 0.0403] },
      { l: 21, s: true,  p: 0.952, b: [0.8555, 0.1356, 0.0089], a: [0.8039, 0.1633, 0.0328] },
      { l: 22, s: true,  p: 0.952, b: [0.8095, 0.1722, 0.0182], a: [0.7603, 0.1977, 0.0420] },
      { l: 23, s: true,  p: 0.951, b: [0.8656, 0.1231, 0.0113], a: [0.8130, 0.1509, 0.0361] },
      { l: 24, s: true,  p: 0.951, b: [0.7886, 0.1982, 0.0132], a: [0.7386, 0.2234, 0.0380] },
      { l: 25, s: true,  p: 0.951, b: [0.7886, 0.1814, 0.0300], a: [0.7392, 0.2057, 0.0550] },
      { l: 26, s: true,  p: 0.950, b: [0.7032, 0.2842, 0.0126], a: [0.6582, 0.3047, 0.0370] },
      { l: 27, s: true,  p: 0.949, b: [0.8177, 0.1696, 0.0127], a: [0.7670, 0.1952, 0.0378] },
      { l: 28, s: true,  p: 0.948, b: [0.7707, 0.1375, 0.0204], a: [0.7200, 0.1626, 0.0460] },
    ],
  },
  {
    id: 'CH-SIMSv2:1566:1566_aqgy5_0008_2',
    combo: 'TV', dataset: 'CH-SIMSv2', bucket: 'Missing',
    gt: 'WN', baseline: 'N', chase: 'WN',
    eta: 0.600, tau: 0.700, topk: 4,
    layers: [
      { l: 13, s: true,  p: 0.765, b: [0.9809, 0.0000, 0.0191], a: [0.9347, 0.0000, 0.0653] },
      { l: 14, s: true,  p: 0.776, b: [0.9792, 0.0000, 0.0208], a: [0.9331, 0.0000, 0.0669] },
      { l: 15, s: true,  p: 0.776, b: [0.9779, 0.0000, 0.0221], a: [0.9327, 0.0000, 0.0673] },
      { l: 16, s: true,  p: 0.787, b: [0.9733, 0.0000, 0.0267], a: [0.9255, 0.0000, 0.0745] },
      { l: 17, s: true,  p: 0.792, b: [0.9861, 0.0000, 0.0139], a: [0.9389, 0.0000, 0.0611] },
      { l: 18, s: true,  p: 0.789, b: [0.9914, 0.0000, 0.0086], a: [0.9452, 0.0000, 0.0548] },
      { l: 19, s: true,  p: 0.772, b: [0.9927, 0.0000, 0.0073], a: [0.9484, 0.0000, 0.0516] },
      { l: 20, s: true,  p: 0.800, b: [0.9518, 0.0000, 0.0124], a: [0.9043, 0.0000, 0.0599] },
      { l: 21, s: true,  p: 0.804, b: [0.9895, 0.0000, 0.0105], a: [0.9415, 0.0000, 0.0585] },
      { l: 22, s: true,  p: 0.806, b: [0.9889, 0.0000, 0.0111], a: [0.9414, 0.0000, 0.0586] },
      { l: 23, s: true,  p: 0.800, b: [0.9959, 0.0000, 0.0041], a: [0.9496, 0.0000, 0.0504] },
      { l: 24, s: true,  p: 0.771, b: [0.9934, 0.0000, 0.0066], a: [0.9492, 0.0000, 0.0508] },
      { l: 25, s: true,  p: 0.764, b: [0.9930, 0.0000, 0.0070], a: [0.9495, 0.0000, 0.0505] },
      { l: 26, s: true,  p: 0.736, b: [0.9641, 0.0000, 0.0359], a: [0.9216, 0.0000, 0.0784] },
      { l: 27, s: true,  p: 0.741, b: [0.9944, 0.0000, 0.0056], a: [0.9542, 0.0000, 0.0458] },
      { l: 28, s: false, p: 0.678, b: [0.9181, 0.0000, 0.0104], a: [0.8836, 0.0000, 0.0450] },
    ],
  },
  {
    id: 'CMU-MOSI:3560:1560_Qr1Ca94K55A_1',
    combo: 'AV', dataset: 'CMU-MOSI', bucket: 'Missing',
    gt: 'P', baseline: 'N', chase: 'P',
    eta: 0.450, tau: 0.800, topk: 2,
    layers: [
      { l: 13, s: true, p: 0.958, b: [0.0000, 0.8918, 0.1082], a: [0.0000, 0.8794, 0.1206] },
      { l: 14, s: true, p: 0.959, b: [0.0000, 0.8497, 0.1503], a: [0.0000, 0.8372, 0.1628] },
      { l: 15, s: true, p: 0.959, b: [0.0000, 0.9107, 0.0893], a: [0.0000, 0.8979, 0.1021] },
      { l: 16, s: true, p: 0.960, b: [0.0000, 0.9529, 0.0471], a: [0.0000, 0.9392, 0.0608] },
      { l: 17, s: true, p: 0.959, b: [0.0000, 0.9558, 0.0442], a: [0.0000, 0.9423, 0.0577] },
      { l: 18, s: true, p: 0.959, b: [0.0000, 0.9692, 0.0308], a: [0.0000, 0.9557, 0.0443] },
      { l: 19, s: true, p: 0.960, b: [0.0000, 0.9348, 0.0295], a: [0.0000, 0.9210, 0.0433] },
      { l: 20, s: true, p: 0.961, b: [0.0000, 0.9018, 0.0625], a: [0.0000, 0.8881, 0.0762] },
      { l: 21, s: true, p: 0.961, b: [0.0000, 0.9763, 0.0237], a: [0.0000, 0.9628, 0.0372] },
      { l: 22, s: true, p: 0.962, b: [0.0000, 0.9657, 0.0343], a: [0.0000, 0.9522, 0.0478] },
      { l: 23, s: true, p: 0.962, b: [0.0000, 0.9732, 0.0268], a: [0.0000, 0.9598, 0.0402] },
      { l: 24, s: true, p: 0.963, b: [0.0000, 0.9625, 0.0375], a: [0.0000, 0.9488, 0.0512] },
      { l: 25, s: true, p: 0.964, b: [0.0000, 0.9391, 0.0609], a: [0.0000, 0.9254, 0.0746] },
      { l: 26, s: true, p: 0.963, b: [0.0000, 0.9652, 0.0348], a: [0.0000, 0.9515, 0.0485] },
      { l: 27, s: true, p: 0.960, b: [0.0000, 0.9542, 0.0458], a: [0.0000, 0.9406, 0.0594] },
      { l: 28, s: true, p: 0.961, b: [0.0000, 0.8664, 0.0622], a: [0.0000, 0.8523, 0.0763] },
    ],
  },
  {
    id: 'CMU-MOSI:3380:1380_Nzq88NnDkEk_1',
    combo: 'TA', dataset: 'CMU-MOSI', bucket: 'Missing',
    gt: 'WN', baseline: 'P', chase: 'WN',
    eta: 0.600, tau: 0.700, topk: 4,
    layers: [
      { l: 13, s: true, p: 0.912, b: [0.7375, 0.2625, 0.0000], a: [0.7054, 0.2946, 0.0000] },
      { l: 14, s: true, p: 0.899, b: [0.6935, 0.3065, 0.0000], a: [0.6614, 0.3386, 0.0000] },
      { l: 15, s: true, p: 0.889, b: [0.7215, 0.2785, 0.0000], a: [0.6893, 0.3107, 0.0000] },
      { l: 16, s: true, p: 0.892, b: [0.6978, 0.3022, 0.0000], a: [0.6648, 0.3352, 0.0000] },
      { l: 17, s: true, p: 0.888, b: [0.8109, 0.1891, 0.0000], a: [0.7759, 0.2241, 0.0000] },
      { l: 18, s: true, p: 0.887, b: [0.7908, 0.2092, 0.0000], a: [0.7531, 0.2469, 0.0000] },
      { l: 19, s: true, p: 0.876, b: [0.7837, 0.1806, 0.0000], a: [0.7467, 0.2176, 0.0000] },
      { l: 20, s: true, p: 0.874, b: [0.7141, 0.2501, 0.0000], a: [0.6766, 0.2877, 0.0000] },
      { l: 21, s: true, p: 0.865, b: [0.7958, 0.2042, 0.0000], a: [0.7582, 0.2418, 0.0000] },
      { l: 22, s: true, p: 0.868, b: [0.7833, 0.2167, 0.0000], a: [0.7467, 0.2533, 0.0000] },
      { l: 23, s: true, p: 0.859, b: [0.8133, 0.1867, 0.0000], a: [0.7773, 0.2227, 0.0000] },
      { l: 24, s: true, p: 0.867, b: [0.7382, 0.2618, 0.0000], a: [0.7046, 0.2954, 0.0000] },
      { l: 25, s: true, p: 0.868, b: [0.6879, 0.3121, 0.0000], a: [0.6576, 0.3424, 0.0000] },
      { l: 26, s: true, p: 0.869, b: [0.6713, 0.3287, 0.0000], a: [0.6411, 0.3589, 0.0000] },
      { l: 27, s: true, p: 0.865, b: [0.7444, 0.2556, 0.0000], a: [0.7116, 0.2884, 0.0000] },
      { l: 28, s: true, p: 0.870, b: [0.6686, 0.2599, 0.0000], a: [0.6652, 0.3007, 0.0000] },
    ],
  },
]

const tabLabels = [
  '① Conflict Case (TAV) ',
  '② Missing Case (TV) ',
  '③ Missing Case (AV) ',
  '④ Missing Case (TA) ',
]

const comboBadgeClass = {
  TAV: 'badge-tav',
  TV:  'badge-tv',
  AV:  'badge-av',
  TA:  'badge-ta',
}

function norm(t, a, v) {
  const s = t + a + v || 1
  return [t / s, a / s, v / s]
}

function pct(v) {
  return (v * 100).toFixed(1) + '%'
}

function barSegments(t, a, v) {
  const [tn, an, vn] = norm(t, a, v)
  return { t: tn, a: an, v: vn, tip: `T=${pct(tn)} A=${pct(an)} V=${pct(vn)}` }
}
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
        <h1 class="section-title">Case Study</h1>
        <p class="section-desc">
          Four representative samples showing attention budget reallocation before and after
          CHASE steering. All four cases flip from incorrect to correct prediction.
          Asterisk (*) marks layers where conflict probability exceeds threshold (p ≥ τ).
        </p>

        <div class="legend">
          <span class="legend-item"><span class="lsq t-before"></span>T before</span>
          <span class="legend-item"><span class="lsq a-before"></span>A before</span>
          <span class="legend-item"><span class="lsq v-before"></span>V before</span>
          <span class="legend-sep"></span>
          <span class="legend-item"><span class="lsq t-after"></span>T after</span>
          <span class="legend-item"><span class="lsq a-after"></span>A after</span>
          <span class="legend-item"><span class="lsq v-after"></span>V after</span>
        </div>

        <el-tabs v-model="activeTab" class="case-tabs">
          <el-tab-pane
            v-for="(c, ci) in CASES"
            :key="ci"
            :label="tabLabels[ci]"
            :name="String(ci)"
          >
            <div class="case-panel">
              <div class="case-meta">
                <span :class="['combo-badge', comboBadgeClass[c.combo]]">{{ c.combo }}</span>
                <span class="meta-text">{{ c.dataset }}</span>
                <span class="meta-bucket">{{ c.bucket }}</span>
                <span class="meta-text">η={{ c.eta }} &nbsp; τ={{ c.tau }} &nbsp; top-k={{ c.topk }}</span>
              </div>

              <div class="sample-id">{{ c.id }}</div>

              <div class="pred-box">
                <span class="pred-label">Prediction</span>
                <span class="tag-wrong">baseline</span>
                <span class="pred-wrong">{{ c.baseline }}</span>
                <span class="pred-arrow">→</span>
                <span class="tag-right">CHASE</span>
                <span class="pred-right">{{ c.chase }}</span>
                <span class="pred-gt">(GT: {{ c.gt }})</span>
                <span class="pred-result">wrong → right ✓</span>
              </div>

              <div class="bar-grid-wrap">
                <div class="bar-grid">
                  <div class="col-header"></div>
                  <div class="col-header">before steering</div>
                  <div class="col-header">after steering</div>

                  <template v-for="row in c.layers" :key="row.l">
                    <div :class="['layer-label', { steered: row.s }]">
                      L{{ row.l }}{{ row.s ? '*' : '' }}
                    </div>

                    <div class="bar-wrap" :title="barSegments(row.b[0], row.b[1], row.b[2]).tip">
                      <div class="seg t-before" :style="{ width: (norm(row.b[0], row.b[1], row.b[2])[0] * 100).toFixed(2) + '%' }"></div>
                      <div class="seg a-before" :style="{ width: (norm(row.b[0], row.b[1], row.b[2])[1] * 100).toFixed(2) + '%' }"></div>
                      <div class="seg v-before" :style="{ width: (norm(row.b[0], row.b[1], row.b[2])[2] * 100).toFixed(2) + '%' }"></div>
                    </div>

                    <div class="bar-wrap" :title="barSegments(row.a[0], row.a[1], row.a[2]).tip">
                      <div class="seg t-after" :style="{ width: (norm(row.a[0], row.a[1], row.a[2])[0] * 100).toFixed(2) + '%' }"></div>
                      <div class="seg a-after" :style="{ width: (norm(row.a[0], row.a[1], row.a[2])[1] * 100).toFixed(2) + '%' }"></div>
                      <div class="seg v-after" :style="{ width: (norm(row.a[0], row.a[1], row.a[2])[2] * 100).toFixed(2) + '%' }"></div>
                    </div>
                  </template>
                </div>
              </div>
            </div>
          </el-tab-pane>
        </el-tabs>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.section-title {
  margin: 0 0 1rem;
  font-size: 1.5rem;
  font-weight: 600;
  text-align: center;
}

.section-desc {
  margin: 0 0 1.25rem;
  font-size: 0.92rem;
  color: #606266;
  line-height: 1.7;
  text-align: center;
}

.legend {
  width: 100%;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 12px;
  align-items: center;
  margin-bottom: 1rem;
  font-size: 12px;
  color: #606266;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 5px;
}

.legend-sep {
  width: 1px;
  height: 14px;
  background: #dcdfe6;
  margin: 0 4px;
}

.lsq {
  width: 10px;
  height: 10px;
  border-radius: 2px;
  flex-shrink: 0;
}

.case-tabs {
  width: 100%;
}

.case-tabs :deep(.el-tabs__header) {
  margin-bottom: 16px;
}

.case-tabs :deep(.el-tabs__nav-wrap) {
  justify-content: center;
}

.case-tabs :deep(.el-tabs__nav-scroll) {
  display: flex;
  justify-content: center;
}

.case-tabs :deep(.el-tabs__nav) {
  margin: 0 auto;
}

.case-tabs :deep(.el-tabs__item) {
  font-size: 13px;
}

.case-panel {
  width: 100%;
  max-width: 100%;
  box-sizing: border-box;
}

.case-meta {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 10px;
  margin-bottom: 6px;
  font-size: 12px;
}

.combo-badge {
  font-size: 11px;
  font-weight: 600;
  padding: 2px 8px;
  border-radius: 4px;
}

.badge-tav { background: #E6F1FB; color: #0C447C; }
.badge-tv  { background: #EAF3DE; color: #27500A; }
.badge-av  { background: #FAEEDA; color: #633806; }
.badge-ta  { background: #EEEDFE; color: #3C3489; }

.meta-text  { color: #606266; }
.meta-bucket {
  font-size: 11px;
  padding: 1px 7px;
  background: #f4f4f5;
  border-radius: 4px;
  color: #909399;
}

.sample-id {
  font-size: 11px;
  color: #909399;
  margin-bottom: 10px;
  font-family: monospace;
  overflow-wrap: anywhere;
}

.pred-box {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 8px;
  padding: 8px 14px;
  background: #f5f7fa;
  border-radius: 8px;
  margin-bottom: 14px;
  font-size: 13px;
}

.pred-label { color: #909399; font-size: 12px; }

.tag-wrong {
  font-size: 10px;
  background: #FCEBEB;
  color: #791F1F;
  padding: 1px 6px;
  border-radius: 3px;
}

.tag-right {
  font-size: 10px;
  background: #EAF3DE;
  color: #27500A;
  padding: 1px 6px;
  border-radius: 3px;
}

.pred-wrong {
  color: #c0392b;
  font-weight: 600;
  text-decoration: line-through;
  opacity: 0.7;
}

.pred-right {
  color: #27ae60;
  font-weight: 600;
}

.pred-arrow { color: #909399; font-size: 16px; }
.pred-gt    { font-size: 12px; color: #909399; }

.pred-result {
  margin-left: auto;
  font-size: 12px;
  font-weight: 500;
  background: #EAF3DE;
  color: #27500A;
  padding: 2px 10px;
  border-radius: 4px;
}

.bar-grid-wrap {
  width: 100%;
  overflow-x: auto;
}

.bar-grid {
  width: 100%;
  min-width: 0;
  display: grid;
  grid-template-columns: 42px minmax(0, 1fr) minmax(0, 1fr);
  gap: 4px 10px;
  align-items: center;
}

.col-header {
  font-size: 11px;
  color: #909399;
  text-align: center;
  padding-bottom: 4px;
}

.layer-label {
  font-size: 11px;
  color: #909399;
  text-align: right;
  white-space: nowrap;
}

.layer-label.steered {
  color: #303133;
  font-weight: 600;
}

.bar-wrap {
  width: 100%;
  min-width: 0;
  height: 13px;
  display: flex;
  border-radius: 3px;
  overflow: hidden;
}

.seg { height: 100%; transition: width 0.2s; }

.t-before { background: #85B7EB; }
.a-before { background: #5DCAA5; }
.v-before { background: #EF9F27; }
.t-after  { background: #378ADD; }
.a-after  { background: #1D9E75; }
.v-after  { background: #BA7517; }

@media (max-width: 768px) {
  .section-title {
    font-size: 1.35rem;
  }

  .section-desc {
    font-size: 0.86rem;
  }

  .pred-result {
    margin-left: 0;
  }

  .bar-grid {
    grid-template-columns: 38px minmax(0, 1fr) minmax(0, 1fr);
    gap: 4px 8px;
  }
}
</style>
