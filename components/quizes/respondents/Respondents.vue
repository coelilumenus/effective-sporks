<template>
  <div class="flex flex-col">
    <div class="respondents-controller overflow-y-scroll">
      <respondents-controller v-if="conditions.length">
        <respondents-condition
          v-for="(condition, i) in conditions"
          v-model="conditions[i]"
          :key="condition.type + i"
          :index="i + 1"
          :lastIndex="(i + 1 === conditions.length)"
          @deleteCondition="onDeleteCondition(i)"
        />
      </respondents-controller>
      
      <div class="flex items-center justify-center min-h-full" v-else>
        <div class="font-bold text-lg text-gray-400">Список условий пуст.</div>
      </div>
    </div>

    <div
      class="flex flex-col w-full py-4 text-green-400 border border-gray-200 justify-center items-center cursor-pointer hover:border-green-400 mt-4"
      @click="onAddEmptyCondition"
    >
      <div><IconPlus class="fill-current" /></div>
      <div class="flex flex-col items-center">
        <div>Нажмите, чтобы добавить новое условие выборки.</div>
        <div>Все условия связываются между собой логическим "И".</div>
      </div>
    </div>
    
    <div class="flex justify-between mt-4">
      <el-button plain type="success">Протестировать опрос</el-button>
      <el-button type="success" @click="onSubmit">Далее <i class="el-icon-arrow-right el-icon-right"></i></el-button>
    </div>
  </div>
</template>

<script>
import RespondentsController from './RespondentsController'
import RespondentsCondition from './RespondentsCondition'

import IconPlus from '@/static/add.svg'

export default {
  name: 'Respondents',

  components: {
    RespondentsController,
    RespondentsCondition,
    IconPlus,
  },

  props: {
    data: {
      type: Array,
      default: () => {
        return []
      },
    },
  },

  data() {
    return {
      conditions: this.data,
    }
  },

  methods: {
    async onSubmit() {
      await this.$axios
        .$post('/', this.conditions)
    },
    
    onAddEmptyCondition() {
      this.conditions.push({ type: '' })
    },

    onDeleteCondition(conditionIndex) {
      this.conditions.splice(conditionIndex, 1)
    },
  },
}
</script>

<style scoped lag="scss">
.respondents-controller {
  height: 65vh;
}

.respondents-controller::-webkit-scrollbar {
  width: 5px;
}

.respondents-controller::-webkit-scrollbar-track {
  opacity: 0;
}

.respondents-controller::-webkit-scrollbar-thumb {
  border-radius: 5px;
  background: #60a5fa;
}
</style>
