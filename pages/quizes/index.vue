<template>
  <div class="mt-2 w-full">
    <el-tabs class="min-w-max w-full" v-model="activeName">
      <el-tab-pane label="Параметры" name="settings">Параметры</el-tab-pane>
      <el-tab-pane label="Вопросы" name="questions">Вопросы</el-tab-pane>
      <el-tab-pane label="Логика" name="logics">Логика</el-tab-pane>
      <el-tab-pane label="Условия" name="conditions">Условия</el-tab-pane>

      <el-tab-pane label="Респонденты" name="respondents">
        <respondents :data="respondents" />
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import Respondents from '@/components/quizes/respondents/Respondents.vue'

export default {
  name: 'Quizes',

  meta: {
    name: 'Опросы',
  },

  components: {
    Respondents
  },

  data() {
    return {
      activeName: 'respondents',
      respondents: []
    }
  },
}
</script>
