<template>
  <header>
    <nav v-bind:class="{'nav-open': menuText === menus[1]}" role="navigation">
      <div class="logo-button">
        <nuxt-link to="/" v-if="$i18n.locale === 'ja'" class=""><img width="40" height="40" src="~/assets/img/logo.png"></nuxt-link>
        <nuxt-link to="/en/" v-else-if="$i18n.locale === 'en'" class=""><img width="40" height="40" src="~/assets/img/logo.png"></nuxt-link>
        <button class="menu-button" @click="navonClick">{{ menuText }}</button>
      </div>
      <ul>
        <li>
          <nuxt-link to="/about" v-if="$i18n.locale === 'ja'" class="">About</nuxt-link>
          <nuxt-link to="/en/about" v-else-if="$i18n.locale === 'en'" class="">About</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/works" v-if="$i18n.locale === 'ja'" class="">Works</nuxt-link>
          <nuxt-link to="/en/works" v-else-if="$i18n.locale === 'en'" class="">Works</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/contact" v-if="$i18n.locale === 'ja'" class="">Contact</nuxt-link>
          <nuxt-link to="/en/contact" v-else-if="$i18n.locale === 'en'" class="">Contact</nuxt-link>
        </li>
        <li class="li-lang">
          <a @click="$i18n.locale = $i18n.locale === 'en' ? 'ja' : 'en'">{{ $i18n.locale === 'en' ? 'Japanese' : 'English' }}</a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component
export default class PortfolioHeader extends Vue {

  private menus = ['Menu', 'Close']
  public menuText: string = this.menus[0]

  public navonClick(): void {
    this.menuText = this.menuText === this.menus[0] ? this.menus[1] : this.menus[0]
  }
}
</script>

<style scoped>
nav {
  background: hsla(0,0%,100%,.8);
  padding: 20px 0 5px;
  position: fixed;
  z-index: 9997;
  width: 100%;
  -webkit-backdrop-filter: blur(5px);
  backdrop-filter: blur(5px);
  height: 73px;
  transition: .5s ease-in-out;
}

nav ul {
  display: none;
  text-align: center;
  font-size: 2.25rem;
}

nav li {
  margin: 5px 0;
}

nav .li-lang {
  width: auto;
}

nav ul a {
  padding: 5px;
  color: #333;
  font-family: Sofia,cursive;
}

nav li a {
  position: relative;
  display: inline-block;
  transition: .3s;
}

nav li a:after {
  position: absolute;
  bottom: 0;
  left: 50%;
  content: "";
  width: 0;
  height: 1px;
  background-color: #08a;
  transition: .3s;
  transform: translateX(-50%);
}

nav li a:hover:after {
  width: 100%;
}

nav.nav-open {
  height: 100%;
  background: hsla(0,0%,100%,.8);
  z-index: 9997;
}

nav.nav-open ul {
  display: block;
  -webkit-animation: nav-items 1s ease-in-out forwards;
  animation: nav-items 1s ease-in-out forwards;
}

nav.nav-open ul a {
  font-size: 2.25rem;
}

@-webkit-keyframes
nav-items {
  0%{opacity:0} to{opacity:1; margin-top:5%}
}

@keyframes
nav-items {
  0%{opacity:0} to {opacity:1; margin-top:5%}
}

nav .logo-button {
  display: flex;
  justify-content: center;
}

.menu-button {
  border-radius: 5px;
  border: 1px solid #333;
  padding: 0 1rem;
  height: 2rem;
  margin: 5px 0 0 10px;
  background: 0 0;
  font-family: Sofia,cursive;
  transition: .3s;
  cursor: pointer;
}

@media (min-width: 1080px) {
  nav {
    padding: 40px 0 10px 45%;
    justify-content: flex-start;
  }
}

@media (min-width: 860px) {
  nav {
    padding: 40px 0 10px;
    justify-content: center;
    height: auto;
  }

  nav a {
    font-size: 1.125rem;
  }

  nav ul {
    margin: 0 0 0 15px;
    font-size: 1rem;
  }

  nav, nav ul {
    display: flex;
  }

  .menu-button {
    display: none;
  }

  nav li {
    margin: 0 10px;
  }

  nav .li-lang {
    width: 78px;
  }
}

</style>
