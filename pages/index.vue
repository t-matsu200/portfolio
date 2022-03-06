<template>
  <div>
    <div class="home-wrapper flexbox">
      <div class="pc-box">
      </div>
      <section>
        <h1>Web Developer</h1>
        <h2>Takahiro</h2>
        <p>
          {{ $t('ADDRESS_INFO') }}
          <span v-if="$i18n.locale === 'en'"> {{ new Date().getFullYear() - 2017 }}{{ $t('ENGINEER_HISTORY') }}</span>
          <span v-else>{{ $t('ENGINEER_HISTORY') }} {{ new Date().getFullYear() - 2017 }}年</span>
        </p>
        <p>{{ $t('QUALIFICATION') }}</p>
        <p>{{ $t('LICENSE_LABEL') }}<br>{{ $t('CC_BY_NC_ND') }}</p>
      </section>
    </div>
    <PortfolioFooter />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style scoped>
  .home-wrapper {
    max-width: 1000px;
    margin: 0 auto;
    padding-right: 8%;
    padding-left: 8%;
    padding-top: 120px;
  }

  .home-wrapper section {
    padding: 8vh 0 0;
  }

  .home-wrapper h1, .home-wrapper h2 {
    font-family: Sofia,cursive;
  }

  .home-wrapper h1 {
    font-size: 1.5rem;
    margin-bottom: -10px;
  }

  .home-wrapper h2 {
    font-size: 4rem;
  }

  .pc-box {
    display: none;
  }

  p {
    margin-bottom: 1rem;
  }

  @media (min-width: 860px) {
    .flexbox {
      display: flex;
    }

    .home-wrapper section {
      padding-right: 5%;
      margin-left: -3%;
      flex: 1;
    }

    .pc-box {
      background: 0 0;
      display: block;
      padding: 0;
      transform: scale(.7);
      transition: 1s;
      flex: 1;
      background: url(~/assets/img/computer.svg) no-repeat;
      width: 100%;
      height: 419px;
    }
  }

  @media (min-width: 1080px) {
    .home-wrapper {
      padding-right: 0;
      padding-left: 0;
    }

    .home-wrapper section {
      padding-left: 4%;
    }

    .home-wrapper h1 {
      font-size: 2.25rem;
      margin-bottom: -10px;
    }

    .home-wrapper h2 {
      font-size: 5.313rem;
    }

    .pc-box {
      padding: 3vh 3vh 0 0;
      transform: scale(1);
      margin-top: 48px;
    }
  }
</style>
