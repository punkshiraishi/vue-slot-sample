<template>
  <select
    class="p2 border border-solid-2 border-blue rounded"
    :name="name"
    @change="onChange"
  >
    <template v-for="(option, index) in options">
      <option
        :key="index"
        :value="option.value"
      >
        <slot
          name="label"
          :[type]="option"
        >
          {{ optionLabel(option) }}
        </slot>
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

interface DefaultOption<T> {
  label: string
  value: T
}

@Component({})
export default class BaseSelect<T, U = DefaultOption<T>> extends Vue {
  @Prop({ required: true })
  value?: T

  @Prop({ default: () => [] })
  options!: U[]

  @Prop({ required: true })
  name!: string

  @Prop({ default: 'option' })
  type!: string

  @Prop({ default: () => (option: DefaultOption<T>) => option.label })
  optionLabel!: (option: U) => string

  @Prop({ default: () => (option: DefaultOption<T>) => option.value })
  optionValue!: (option: U) => T

  @Watch('options', { immediate: true })
  onInitOptions() {
    this.$emit('input', this.optionValue(this.options[0]))
  }

  onChange(event: Event) {
    const target = event.target as HTMLSelectElement
    this.$emit('input', target.value)
  }

}
</script>

<style scoped lang="scss" >
</style>