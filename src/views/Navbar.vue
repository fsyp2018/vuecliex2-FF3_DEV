<template>
  <div>
    <nav class="navbar navbar-dark fixed-top flex-md-nowrap p-0 shadow bg-secondary" style="border:3px #AAAAAA ridge;border-radius:10px;">
      <router-link to="/">
      <a class="bg-secondary ml-5" href="#"><img src="../assets/img/logo.png" alt="" srcset="" style="width:85px;"></a>
      </router-link>
      <ul class="navbar-nav px-3">
        <li class="nav-item text-nowrap">
          <a class="nav-link" href="#" @click.prevent="signout">登出</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Navbar',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    signout () {
      const api = `${process.env.VUE_APP_API}/logout`
      const vm = this
      this.$http.post(api).then((response) => {
        console.log(response.data)
        if (response.data.success) {
          vm.$router.push('/')
        }
      })
    }
  }
}
</script>
