<template>
  <div class="result-table-wrapper">
    <h2 class="section-title">Experimental Results</h2>

    <div class="table-scroll">
      <table class="result-table">
        <thead>
          <tr>
            <th rowspan="2" class="model-col">Model</th>
            <th colspan="3" class="group-start">EmoMM (Overall)</th>
            <th colspan="3" class="group-start">EmoMM-Align</th>
            <th colspan="3" class="group-start">EmoMM-Conflict</th>
            <th colspan="3" class="group-start">EmoMM-Missing</th>
          </tr>
          <tr>
            <th class="group-start metric">Acc↑</th>
            <th class="metric">F1↑</th>
            <th class="metric">MAE↓</th>

            <th class="group-start metric">Acc↑</th>
            <th class="metric">F1↑</th>
            <th class="metric">MAE↓</th>

            <th class="group-start metric">Acc↑</th>
            <th class="metric">F1↑</th>
            <th class="metric">MAE↓</th>

            <th class="group-start metric">Acc↑</th>
            <th class="metric">F1↑</th>
            <th class="metric">MAE↓</th>
          </tr>
        </thead>

        <tbody>
          <tr class="section-row">
            <td colspan="13">Open-source Baselines</td>
          </tr>
          <tr>
            <td class="model-name">Video-LLaMA2.1-7B-AV</td>
            <td class="group-start">22.46</td><td>21.33</td><td>0.579</td>
            <td class="group-start">23.94</td><td>21.12</td><td>0.611</td>
            <td class="group-start">25.84</td><td>20.60</td><td>0.527</td>
            <td class="group-start">21.55</td><td>21.52</td><td>0.587</td>
          </tr>
          <tr>
            <td class="model-name">MiniCPM-o 2.6-8B</td>
            <td class="group-start">26.09</td><td>15.06</td><td>0.781</td>
            <td class="group-start">27.59</td><td>15.61</td><td>0.723</td>
            <td class="group-start">26.37</td><td>14.47</td><td>0.751</td>
            <td class="group-start">25.86</td><td>15.13</td><td>0.794</td>
          </tr>
          <tr>
            <td class="model-name">Video-SALMONN2-7B</td>
            <td class="group-start">41.47</td><td>38.30</td><td>0.380</td>
            <td class="group-start">49.05</td><td>43.94</td><td>0.318</td>
            <td class="group-start">41.25</td><td>37.70</td><td>0.367</td>
            <td class="group-start">40.65</td><td>37.78</td><td>0.390</td>
          </tr>
          <tr>
            <td class="model-name">Qwen2.5-Omni-7B</td>
            <td class="group-start">44.56</td><td>36.24</td><td>0.384</td>
            <td class="group-start">52.14</td><td>44.28</td><td>0.270</td>
            <td class="group-start">46.47</td><td>39.76</td><td>0.356</td>
            <td class="group-start">43.27</td><td>34.55</td><td>0.403</td>
          </tr>
          <tr>
            <td class="model-name">VITA-1.5-8B</td>
            <td class="group-start">44.50</td><td>43.83</td><td>0.327</td>
            <td class="group-start">53.03</td><td>53.47</td><td>0.277</td>
            <td class="group-start">47.80</td><td>47.18</td><td>0.319</td>
            <td class="group-start">42.80</td><td>41.99</td><td>0.335</td>
          </tr>

          <tr class="section-row">
            <td colspan="13">Closed-source API</td>
          </tr>
          <tr>
            <td class="model-name">Gemini 3 Pro</td>
            <td class="group-start">56.41</td><td>53.58</td><td>0.236</td>
            <td class="group-start">59.85</td><td>59.07</td><td>0.191</td>
            <td class="group-start">56.23</td><td>51.16</td><td>0.236</td>
            <td class="group-start">56.06</td><td>53.47</td><td>0.241</td>
          </tr>
        </tbody>
      </table>
    </div>

    <p class="table-caption">
      Table 1. Main results on EmoMM and its subsets.
    </p>
  </div>
</template>

<script setup>
// no script needed
</script>

<style scoped>
.result-table-wrapper {
  margin: 24px 0;
  width: 100%;
  max-width: 100%;
  overflow-x: hidden;
}

.section-title {
  margin: 0 0 18px 0;
  text-align: center;
  font-size: 3rem;
  font-weight: 700;
  font-style: italic;
  line-height: 1.2;
  letter-spacing: 0.5px;
}

.table-scroll {
  width: 100%;
  max-width: 100%;
  overflow-x: auto;
  overflow-y: hidden;
  display: block;
}

.result-table {
  width: max-content;
  min-width: 100%;
  border-collapse: collapse;
  font-family: "Times New Roman", Times, serif;
  font-size: 15px;
  line-height: 1.4;
  border-top: 2px solid #444;
  border-bottom: 2px solid #444;
  table-layout: auto;
}

.result-table th,
.result-table td {
  padding: 10px 16px;
  border: 1px solid #d9d9d9;
}

.result-table thead th {
  text-align: center;
  font-weight: 700;
  border-bottom: 1px solid #666;
  white-space: nowrap;
}

.result-table tbody td {
  text-align: right;
  white-space: nowrap;
}

.result-table .model-col,
.result-table .model-name {
  text-align: left;
  white-space: nowrap;
}

.result-table .model-col {
  min-width: 300px;
}

.result-table .group-start {
  border-left: 1px solid #999 !important;
}

.result-table .metric {
  min-width: 96px;
}

.section-row td {
  text-align: left !important;
  font-style: italic;
  background: #f7f7f7;
  border-top: 1px solid #ccc;
  font-weight: 500;
}

.table-caption {
  margin-top: 10px;
  font-size: 14px;
  font-style: italic;
}
</style>
