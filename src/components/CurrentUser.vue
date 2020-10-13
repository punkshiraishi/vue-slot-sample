<template>
  <span>
    Current User: 
    <slot :[type]="user">
      {{ user.lastName }}
    </slot>
  </span>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

interface User {
  firstName: string,
  lastName: string,
}

@Component({})
export default class CurrentUser extends Vue {
  user: User = {
    firstName: "Miki",
    lastName: "Miyazato",
  }

  @Prop({ default: "user" })
  type!: string
}
</script>
