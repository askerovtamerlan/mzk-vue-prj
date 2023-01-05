<template>
  <div class="b-block">
    <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style lang="sass" scoped>
.b-block
  background-color: $light
  padding: clamp(17px, 5%, 30px) clamp(20px, 5%, 60px)
  border: 1px solid $border
  border-radius: 15px
</style>
