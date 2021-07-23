<template>
  <p>
    <a :href="twitterUrl">
      <img src="~/assets/img/twitter.png">
    </a>
    <a :href="facebookUrl">
      <img src="~/assets/img/f_logo.png">
    </a>
  </p>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator'

@Component
export default class Sns extends Vue {
  @Prop()
  public facebookUrl!: string

  @Prop()
  public twitterUrl!: string
}
</script>

<style scoped>
  p {
    padding: 4px;
  }

  p a {
    margin-left: 4px;
  }

  p img {
    width: 32px;
    margin-top: 1%;
    opacity: 0.5;
    transition-duration: 0.5s;
  }

  p img:hover {
    transform: scale(1.2);
    transition-duration: 0.5s;
    opacity: 0.6;
  }
</style>
