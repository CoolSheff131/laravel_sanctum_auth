<template>
  <div>
      <input v-model="name" type="name" placeholder="name" class="form-control">
      <input v-model="email" type="email" placeholder="email" class="form-control">
      <input v-model="password" type="password" placeholder="password" class="form-control">
      <input v-model="password_confirmation" type="password" placeholder="password_confirmation" class="form-control">
      <input @click.prevent="register" type="submit" value="register" class="btn btn-primary">
  </div>
</template>

<script>
export default {
name: 'registration',
data(){
    return {
        name: null,
        email:null,
        password: null,
        password_confirmation: null,
    }
},
methods: {
    register(){
        axios.get('/sanctum/csrf-cookie')
        .then( response => {
            axios.post('/register',{email: this.email,password: this.password, name: this.name, password_confirmation: this.password_confirmation})
            .then(res=>{
                localStorage.setItem('x_xsrf_token',res.config.headers['X-XSRF-TOKEN']);
                this.$router.push({name: 'user.personal'})
                
            })
        })
    }
}
}
</script>
 
<style>

</style>