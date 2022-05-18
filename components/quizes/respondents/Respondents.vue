<template>
  <div>
    <respondents-controller>
      <respondents-condition 
        v-for="(condition, i) in 5" 
        :key="`condition-${i}`" 
      />
    </respondents-controller>
  </div>
</template>

<script>
import RespondentsController from './RespondentsController'
import RespondentsCondition from './RespondentsCondition'

export default {
  name: 'Respondents',

  components: {
    RespondentsController,
    RespondentsCondition
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
}
</script>
