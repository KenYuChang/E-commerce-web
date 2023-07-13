<template>
    <div class="container mt-5">
      <form class="row justify-content-center"
        @submit.prevent="signin">
        <div class="col-md-6">
          <h1 class="h3 mb-3 font-weight-normal">請先登入</h1>
          <div class="mb-2">
            <label for="inputAccount" class="sr-only">Account</label>
            <input
              type="account"
              id="inputAccount"
              class="form-control"
              placeholder="Account"
              required
              autofocus
              v-model="user.account"
            />
          </div>
          <div class="mb-2">
            <label for="inputPassword" class="sr-only">Password</label>
            <input
              type="password"
              id="inputPassword"
              class="form-control"
              placeholder="Password"
              required
              v-model="user.password"
            />
          </div>
          <div class="text-end mt-4">
            <button class="btn btn-lg btn-primary btn-block" type="submit">登入</button>
          </div>
        </div>
      </form>
    </div>
</template>
<script>
export default {
  data() {
    return {
      user: {
        account: '',
        password: '',
      },
    };
  },
  methods: {
    signin() {
      const api = `${process.env.VUE_APP_API}api/users/signin`;
      console.log(api);
      this.$http.post(api, this.user)
        .then((res) => {
          console.log(res);
        });
    },
  },
};
</script>
