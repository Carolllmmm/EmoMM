<script setup>
import ResultTable from '../ResultTable.vue'
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="16" :xl="16">
        <ResultTable />
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
</style>
