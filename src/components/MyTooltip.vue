<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from 'vue'

const wrapper = ref()
const showTooltip = ref(false)

const handleMouseEnter = () => {
  showTooltip.value = true
}

const handleMouseLeave = () => {
  showTooltip.value = false
}

const handleFocusIn = () => {
  showTooltip.value = true
}

const handleFocusOut = () => {
  showTooltip.value = false
}

onMounted(() => {
  wrapper.value.addEventListener('focusin', handleFocusIn)
  wrapper.value.addEventListener('mouseenter', handleMouseEnter)
  wrapper.value.addEventListener('focusout', handleFocusOut)
  wrapper.value.addEventListener('mouseleave', handleMouseLeave)
})

onBeforeUnmount(() => {
  wrapper.value.removeEventListener('focusin', handleFocusIn)
  wrapper.value.removeEventListener('mouseenter', handleMouseEnter)
  wrapper.value.removeEventListener('focusout', handleFocusOut)
  wrapper.value.removeEventListener('mouseleave', handleMouseLeave)
})
</script>

<template>
  <span>
    <span ref="wrapper" class="wrapper">
      <slot name="content" />
    </span>
    <div :hidden="!showTooltip">
      <slot name="tooltip-content">
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eligendi asperiores blanditiis
        reprehenderit ratione. Saepe consectetur iusto repellendus repellat! Cupiditate praesentium
        quasi sequi quae quas ipsam impedit quam et, iste amet?
      </slot>
    </div>
  </span>
</template>
