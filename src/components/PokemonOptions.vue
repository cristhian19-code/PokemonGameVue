<template>
    <ul class="flex justify-center flex-wrap gap-5">
      <li
        v-for="option in options"
        @click="$emit('selection',option.id)"
        :key="option.id"
        class="
          bg-indigo-600
          transition-all
          duration-300
          cursor-pointer
          hover:shadow-md hover:shadow-indigo-600/40
          hover:scale-105
          text-white text-center
          font-bold
          rounded-md
          w-52
          py-3
          my-2
        "
      >
        {{ option.name }}
      </li>
    </ul>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      default: [],
      required: true,
    },
  },
};
</script>

<style scoped>
</style>