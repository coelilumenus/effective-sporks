<template>
  <div>
    <condition-card-type-select
      v-for="(type, i) in value.types"
      :key="'type' + i"
      :value="value.types[i]"
      :index="i + 1"
      @changeType="changeType"
    />

    <div class="flex w-full justify-between items-center">
      <div class="w-full max-w-xs"></div>

      <div class="flex w-full relative top-8">
        <el-button
          class="absolute"
          type="primary"
          plain
          icon="el-icon-plus"
          @click="onAddType"
        >
          Добавить тип
        </el-button>
      </div>
    </div>
  </div>
</template>

<script>
import ConditionCardTypeSelect from './ConditionCardTypeSelect.vue'

export default {
  name: 'ConditionCardStatus',

  components: {
    ConditionCardTypeSelect,
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
        types: ['Активна']
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

    onAddType() {
      this.value.types.push('Активна')
    },
    
    changeType(status, index) {
      this.$set(this.value.types, index, status)
    }
  },
}
</script>
