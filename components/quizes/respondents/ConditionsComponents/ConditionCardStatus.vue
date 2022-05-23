<template>
  <div>
    <condition-card-status-select
      v-for="(status, i) in value.statuses"
      :key="'status' + i"
      :value="value.statuses[i]"
      :index="i + 1"
      @changeStatus="changeStatus"
    />

    <div class="flex w-full justify-between items-center">
      <div class="w-full max-w-xs"></div>

      <div class="flex w-full relative top-8">
        <el-button
          class="absolute"
          type="primary"
          plain
          icon="el-icon-plus"
          @click="onAddStatus"
        >
          Добавить статус
        </el-button>
      </div>
    </div>
  </div>
</template>

<script>
import ConditionCardStatusSelect from './ConditionCardStatusSelect.vue'

export default {
  name: 'ConditionCardStatus',

  components: {
    ConditionCardStatusSelect,
  },

  model: {
    prop: 'value',
    event: 'change',
  },

  props: {
    value: {
      type: Object,
    },
  },

  data() {
    return {
      defaultData: {
        statuses: ['Gold']
      },
    }
  },

  computed: {
    isDataCorrect() {
      if (!this.value.data) return false

      return Object.keys(this.value.data).every((property) => {
        return this.defaultData.hasOwnProperty(property)
      })
    },
  },

  created() {
    if (!this.isValueCorrect) {
      this.initDefaultData()
    }
  },

  methods: {
    initDefaultData() {
      this.$emit('initDefaultData', this.defaultData)
    },

    onAddStatus() {
      this.value.statuses.push('Gold')
    },
    
    changeStatus(status, index) {
      this.$set(this.value.statuses, index, status)
    }
  },
}
</script>
