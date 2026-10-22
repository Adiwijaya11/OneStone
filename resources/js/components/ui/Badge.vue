<script setup>
defineProps({
  variant: {
    type: String,
    default: 'gray', // gray, blue, green
  },
});

const variantClasses = {
  gray: 'bg-gray-100 text-gray-700 border-gray-200',
  blue: 'bg-blue-50 text-blue-700 border-blue-200',
  green: 'bg-emerald-50 text-emerald-700 border-emerald-200',
};
</script>

<template>
  <span
    :class="[
      'inline-flex items-center gap-1.5 px-3 py-1 rounded-full text-xs font-medium border',
      variantClasses[variant] || variantClasses.gray,
    ]"
  >
    <slot />
  </span>
</template>
