<script setup lang="ts">
import MyTooltip from './components/MyTooltip.vue'
import MyButton from './components/MyButton.vue'
</script>

<template>
  <main>
    <h1>Hello!</h1>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias, accusamus odio,
      optio illo fugiat a enim nulla porro, fuga illum eos perspiciatis! At eligendi tempore
      fugit <MyTooltip>
        <template #content>
          <span tabindex="0" class="focusable">tenetur placeat</span>
        </template>
        <template #tooltip-content>LA GROSSE TOOLTIP</template>
      </MyTooltip>
      et maxime.
    </p>

      <MyButton>Just another button</MyButton>
  </main>
</template>

<style scoped>
.focusable:focus-visible,
.focusable:focus-within {
  outline: 1px dashed red;
}
</style>
