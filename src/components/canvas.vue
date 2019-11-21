<template>
  <div>
      <svg width="250" height="250">
        <slot></slot>
      </svg>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      test: 'tester'
    }
  }
}
</script>
