<template>
  <div class="flex flex-col items-center max-w-min min-w-max border-r border-gray-400 p-4 min-h-screen gap-y-4">
    <nuxt-link
      to="/quizes"
      exact
      active-class="text-blue-400"
      class="flex flex-col items-center rounded-md hover:text-blue-400 active:bg-blue-200 h-20 text-gray-500 font-medium max-w-min"
    >
      <IconDescription class="fill-current" />
      <span class="ml-1 font-medium whitespace-nowrap text-xs"> Опросы </span>
    </nuxt-link>

    <nuxt-link
      to="/users"
      active-class="text-blue-400"
      class="flex flex-col items-center rounded-md hover:text-blue-400 active:bg-blue-200 h-20 text-gray-500 font-medium max-w-min"
    >
      <IconGroup class="fill-current" />
      <span class="ml-1 font-medium whitespace-nowrap text-xs"> Пользователи </span>
    </nuxt-link>

    <nuxt-link
      to="/blacklists"
      active-class="text-blue-400"
      class="flex flex-col items-center rounded-md hover:text-blue-400 active:bg-blue-200 h-20 text-gray-500 font-medium max-w-min"
    >
      <IconFlag class="fill-current" />
      <span class="ml-1 font-medium whitespace-nowrap text-xs"> Чёрные списки </span>
    </nuxt-link>

    <nuxt-link
      to="/callcenter"
      active-class="text-blue-400"
      class="flex flex-col items-center rounded-md hover:text-blue-400 active:bg-blue-200 h-20 text-gray-500 font-medium max-w-min"
    >
      <IconCall class="fill-current" />
      <span class="ml-1 font-medium whitespace-nowrap text-xs"> Колл-центр </span>
    </nuxt-link>
  </div>
</template>

<script>
import IconDescription from '@/static/description.svg'
import IconCall from '@/static/call.svg'
import IconFlag from '@/static/flag.svg'
import IconGroup from '@/static/group.svg'

export default {
  name: 'SideBar',

  components: {
    IconDescription,
    IconCall,
    IconFlag,
    IconGroup
  },
}
</script>
