<template>
  <div class="flex flex-col space-y-5 m-5">
    <div class="flex flex-row space-x-2">
      <BaseButton />
      <BaseButton>test</BaseButton>
    </div>
    <div class="flex flex-row space-x-2">
      <MessageCard />
      <MessageCard>
        <template #title>
          custom title
        </template>
        <template #content>
          custom content
        </template>
        <template #footer>
          custom footer
        </template>
      </MessageCard>
    </div>
    <div class="flex flex-col space-2-2">
      <CurrentUser />
      <CurrentUser type="info">
        <template #default="{ info }">
          {{ info.firstName }}
        </template>
      </CurrentUser>
    </div>
    <div class="flex flex-col space-2-2">
      <BaseSelect
        v-model="fruitName"
        :options="fruits"
        name="fruit"
      />
      selected value = {{ fruitName }}
      <BaseSelect
        v-model="countryName"
        :options="countries"
        type="country"
        name="test"
      >
        <template #label="{ country }">
          <div class="flex justify-between bg-blue">
            {{ `${country.label} count is ${country.count}` }}
          </div>
        </template>
      </BaseSelect>
      selected value = {{ countryName }}
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import BaseButton from './BaseButton.vue';
import BaseSelect from './BaseSelect.vue';
import CurrentUser from './CurrentUser.vue';
import MessageCard from './MessageCard.vue';
@Component({
  components: {
    BaseButton,
    MessageCard,
    CurrentUser,
    BaseSelect,
  }
})
export default class DemoPage extends Vue {
  fruitName = ''
  fruits = [
    {
      label: "apple",
      value: "1",
    },
    {
      label: "orange",
      value: "2",
    }
  ]

  countryName = ''
  countries = [
    {
      label: "japan",
      value: 1,
      count: 100,
    },
    {
      label: "korea",
      value: 2,
      count: 200,
    },
    {
      label: "china",
      value: 3,
      count: 500,
    },
  ]
  @Prop() private msg!: string;
}
</script>