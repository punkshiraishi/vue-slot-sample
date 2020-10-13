<template>
  <button class="p-2 border border-solid border-gray-500 rounded">
    <slot>
      default
    </slot>
  </button>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({})
export default class BaseButton extends Vue {}
</script>

<style scoped lang="scss" >
</style>