<template>
  <div>
      <router-link :to="{name: 'get.index'}">Get</router-link>
      <router-link :to="{name: 'user.login'}">Login</router-link>
      <router-link :to="{name: 'user.registration'}">registration</router-link>
      <a @click.prevent="logout" href="">Logout</a>
      <router-view></router-view>
  </div>
</template>

<script>
export default {
    name: 'Index',
    methods:{
        logout(){
            axios.get('/logout')
            .then(res => {
                console.log(res);
                this.$router.push({name: 'user.login'})
            })
        }
    }
}
</script>

<style>

</style>