<template>
  <div>
    <div class="success-wrapper">
      <p>{{ $t('SUCCESS_MSG') }}</p>
      <p>
          <nuxt-link to="/">{{ $t('RETURN') }}</nuxt-link>
      </p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style scoped>
  .success-wrapper {
    max-width: 1000px;
    margin: 0 auto;
    padding-right: 8%;
    padding-left: 8%;
    padding-top: 120px;
  }
</style>
