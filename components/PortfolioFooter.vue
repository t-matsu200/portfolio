<template>
  <footer>
    <p> Made with by Takahiro </p>
    <p class="license">
      <small>
        <a href="http://creativecommons.org/licenses/by-nc-nd/3.0/" target="_blank">
          <img src="~/assets/img/create-common.svg">
        </a>
      </small>
    </p>
  </footer>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>

<style scoped>
footer {
  margin-top: 20%;
  padding-bottom: 40px;
  text-align: center;
}

footer p {
  font-size: .75rem;
  line-height: 1.5;
  margin-bottom: 1rem;
}

footer .license img {
  width: 80px;
  height: 26px;
}

@media (min-width: 860px) {

  footer {
    margin-top: 5%;
  }
}

</style>
