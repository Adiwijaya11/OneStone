<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary', // primary, secondary, outline, ghost
  },
  size: {
    type: String,
    default: 'md', // sm, md, lg
  },
  href: {
    type: String,
    default: null,
  },
});

const variantClasses = {
  primary:
    'bg-gray-900 hover:bg-black text-white font-medium border border-gray-900 transition-colors',
  secondary:
    'bg-gray-100 hover:bg-gray-200 text-gray-900 font-medium border border-gray-200 transition-colors',
  outline:
    'bg-white hover:bg-gray-50 text-gray-800 font-medium border border-gray-300 hover:border-gray-400 transition-colors',
  ghost:
    'bg-transparent hover:bg-gray-100 text-gray-600 hover:text-gray-900 font-medium transition-colors',
};

const sizeClasses = {
  sm: 'text-xs px-3.5 py-1.5 rounded-lg gap-1.5',
  md: 'text-sm px-4.5 py-2.5 rounded-lg gap-2',
  lg: 'text-base px-6 py-3 rounded-lg gap-2',
};
</script>

<template>
  <component
    :is="href ? 'a' : 'button'"
    :href="href"
    :class="[
      'inline-flex items-center justify-center cursor-pointer select-none transition-all duration-150 active:scale-[0.99] focus:outline-none focus:ring-2 focus:ring-gray-900 focus:ring-offset-2',
      variantClasses[variant] || variantClasses.primary,
      sizeClasses[size] || sizeClasses.md,
    ]"
  >
    <slot />
  </component>
</template>
