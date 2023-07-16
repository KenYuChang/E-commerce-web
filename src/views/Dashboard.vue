<template>
  <Navbar></Navbar>
  <div class="container-fluid">
    <router-view />
  </div>
</template>
<script>
import Navbar from '../components/Navbar.vue';
// bug's heere not finished
export default {
  components: {
    Navbar,
  },
  created() {
    const token = document.cookie.replace(/(?:(?:^|.*;\s*)hexToken\s*=\s*([^;]*).*$)|^.*$/, '$1');
    console.log(token);
    // token加入headers
    this.$http.defaults.headers.common.Authorization = token;
    const api = `${process.env.VUE_APP_API}api/currentUser`;
    this.$http.get(api, this.user)
      .then((res) => {
        console.log(res);
      });
  },
};
</script>
