<template>
  <header class="header">
    <nav class="inner">
      <router-link to="/" exact>
        <img class="logo" src="../assets/logo-48.png" alt="logo">
      </router-link>
      <router-link to="/create">New</router-link>

      <a class="auth" v-if="userId" @click="logout()">Logout</a>
      <router-link class="auth" v-else to="/login">Login</router-link>

    </nav>
</header>
</template>

<script>
  import { GC_USER_ID, GC_AUTH_TOKEN } from '../constants/settings'
  
  export default {
    name: 'AppHeader',
    computed: {
      userId () {
        return this.$root.$data.userId
      }
    },
    methods: {
      logout () {
        localStorage.removeItem(GC_USER_ID)
        localStorage.removeItem(GC_AUTH_TOKEN)
        this.$root.$data.userId = localStorage.getItem(GC_USER_ID)
      }
    }
  }
</script>

<style lang="stylus">
.header
  background-color #ff6600
  position fixed
  z-index 999
  height 55px
  top 0
  left 0
  right 0
  .inner
    max-width 800px
    box-sizing border-box
    margin 0px auto
    padding 15px 5px
  a
    color rgba(255, 255, 255, .8)
    line-height 24px
    transition color .15s ease
    display inline-block
    vertical-align middle
    font-weight 300
    letter-spacing .075em
    margin-right 1.8em
    &:hover
      color #fff
    &.router-link-active
      color #fff
      font-weight 400
    &:nth-child(6)
      margin-right 0
  .auth
    color #fff
    font-size .9em
    margin 0
    float right

.logo
  width 24px
  margin-right 10px
  display inline-block
  vertical-align middle

</style>
