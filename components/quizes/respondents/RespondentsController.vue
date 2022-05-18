// На самом деле, объективной необходимости в этой прослойке нет, 
// но если в будущем потребуется, например, добавить кнопку "отключить все условия",
// то такой вариант очень сильно упростит задачу, поскольку мы сможем вызывать
// методы прямо из дочерних компонентов.

<template>
  <div>
    <slot />
  </div>
</template>

<script>
export default {
  name: 'RespondentsController',

  data() {
    return {
      items: []
    }
  },

  created() {
    this.items = this.$slots.default
  }
}
</script>