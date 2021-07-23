<template>
  <div role="main" class="scroll-wrap">
    <section class="full-blog">
      <div class="flex-center">
        <div class="inner container">
          <h1>Blog</h1>
          <p>{{ $t('BLOG_H_LABEL') }}</p>
          <p><a href="https://tm200.hatenablog.com/" target="_blank">https://tm200.hatenablog.com</a></p>
        </div>
      </div>
      <div class="arrow-wrap">
        <svg viewBox="0 0 40 20" class="scroll-arrow"><path d="M20,13.8C11.4-1,0,0,0,0l20,20L40,0C40,0,28.6-1,20,13.8z"></path></svg>
      </div>
    </section>
    <section class="about-fav">
      <div class="flex-center">
        <div class="inner container">
          <h1>Vidual Band</h1>
          <p>{{ $t('FAV_V_ROCK') }}</p>
          <Sns :facebookUrl="'https://www.facebook.com/people/the-GazettE-Official/100044227999715/'" :twitterUrl="'https://twitter.com/thegazettestaff'" />
        </div>
      </div>
      <div class="arrow-wrap">
        <svg viewBox="0 0 40 20" class="scroll-arrow"><path d="M20,13.8C11.4-1,0,0,0,0l20,20L40,0C40,0,28.6-1,20,13.8z"></path></svg>
      </div>
    </section>
    <section class="about-systema">
      <div class="flex-center">
        <div class="inner container">
          <h1>Systema</h1>
          <p>{{ $t('ABOUT_LEARN_SYSTEMA') }}</p>
          <p><a href="https://systemashonan.jimdo.com/" target="_blank">https://systemashonan.jimdo.com</a></p>
          <p>{{ $t('ABOUT_SYSTEMA_RUSIAN') }}</p>
          <Sns :facebookUrl="'https://www.facebook.com/systema4476/'" :twitterUrl="'https://twitter.com/systema4476?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor'" />
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import Sns from '~/components/Sns.vue'

@Component({
  components: {
    Sns
  }
})
export default class Works extends Vue {}
</script>

<style scoped>
  .full-blog {
    color: #fff;
    background-size: cover;
    width: 100%;
    height: 100vh;
    position: relative;
    background: #C0C0C0 url(~/assets/img/nyansomware.svg) no-repeat 100% 0;
  }

  .full-blog h1, .about-fav h1, .about-systema h1 {
    text-align: center;
    font-size: 4.375rem;
    margin-bottom: 2%;
    font-family: Sofia,cursive;
  }

  .full-blog a {
    color: chartreuse;
  }

  .about-fav {
    background: #0bd url(~/assets/img/ruins.svg) no-repeat top;
    text-align: center;
    padding-top: 30%;
    width: 100%;
    height: 100vh;
    position: relative;
    color: #fff;
  }

  .about-fav .flex-center {
    height: 48%;
  }

  .about-fav .scroll-arrow {
    fill: antiquewhite;
  }

  .about-systema {
    background: #CCFFFF url(~/assets/img/rosia.svg) no-repeat top;
    text-align: center;
    background-size: cover;
    width: 100%;
    height: 100vh;
    position: relative;
    color: #fff;
  }

  .about-systema a {
    color: khaki;
  }

  @media (min-width: 1080px) {
    .container, .narrow-container {
      padding-right: 0;
      padding-left: 0;
    }
  }

  @media screen and (min-width: 860px) and (-webkit-min-device-pixel-ratio: 0) {
    .full-blog .inner {
      padding: 0 0 0 40vw!important;
    }
  }
</style>
