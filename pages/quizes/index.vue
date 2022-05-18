<template>
  <div>
    <el-tabs v-model="activeName" @tab-click="handleClick">
      <el-tab-pane label="Параметры" name="settings">Параметры</el-tab-pane>
      <el-tab-pane label="Вопросы" name="questions">Вопросы</el-tab-pane>
      <el-tab-pane label="Логика" name="logics">Логика</el-tab-pane>
      <el-tab-pane label="Условия" name="conditions">Условия</el-tab-pane>
      <el-tab-pane label="Респонденты" name="respondents">Респонденты</el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
export default {
  name: 'Quizes',

  meta: {
    name: 'Опросы',
  },

  data() {
    return {
      activeName: 'respondents',
    }
  },
}
</script>
