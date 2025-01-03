<template>
  <div>
    <li>
      <NuxtLink :to="path"
        class="block py-2 px-3 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent"
        :class="isActive ? 'text-blue-700' : 'text-gray-900'">
        {{ name }}</NuxtLink>
    </li>
  </div>
</template>

<script setup>
const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  path: {
    type: String,
    required: true
  },
})

const route = useRoute()

const isActive = computed(() => route.path === props.path)

watch(route, () => {
  isActive.value = route.path === props.path
})
</script>