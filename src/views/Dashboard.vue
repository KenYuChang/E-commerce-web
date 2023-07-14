<template>
    Dashboard
</template>
<script>
// bug's heere not finished
export default {
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
