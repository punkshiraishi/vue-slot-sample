<template>
  <select
    :class="`[p2 border border-solid-2 border-gray-800]`"
    :name="name"
    @change="onChange"
  >
    <template v-for="(option, index) in options">
      <option
        :key="index"
        :value="option.value"
      >
        {{ option.label }}
      </option>
    </template>
  </select>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator'

interface Option {
  label: string,
  value: string,
}

@Component({})
export default class BaseSelect extends Vue {
  @Prop({ required: true })
  value?: string

  @Prop({ required: true })
  options!: Option[]

  @Watch('options', { immediate: true })
  onInitOptions() {
    this.$emit('input', this.options[0].value)
  }

  onChange(event: Event) {
    const target = event.target as HTMLSelectElement
    this.$emit('input', target.value)
  }

}
</script>

<style scoped lang="scss" >
</style>