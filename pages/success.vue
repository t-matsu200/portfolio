<template>
  <div>
    <p>{{ $t('SUCCESS_MSG') }}</p>
    <p>
        <nuxt-link to="/">{{ $t('RETURN') }}</nuxt-link>
    </p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style scoped>
</style>
