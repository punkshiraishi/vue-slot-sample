<template>
  <div class="flex flex-col border border-solid rounded">
    <div class="bg-gray-300 p-2">
      <slot name="title">
        default title
      </slot>
    </div>
    <div class="p-2">
      <slot name="content">
        default content
      </slot>
    </div>
    <div class="bg-gray-300 p-2">
      <slot name="footer">
        default footer
      </slot>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({})
export default class MessageCard extends Vue {}
</script>
