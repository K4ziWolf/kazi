<template>
  <section id="my-section" >
  <div id="login_holder" class=" btn btn-outline-secondary" >
      <div class="col-md-6 form-group">
          <label for="username">Nazwa użytkownika</label>
          <input id="username" class="form-control" type="text" v-model="username" required>

      </div>
      <div class="col-md-6">
        <div class="form-group">
          <label for="password">
            Hasło
          </label>
          <input id="password" class="form-control" type="password" v-model="password" required>
        </div>
      </div>
    </div>
      <div class="col-12 ">
        <button @click="hideLoginScreen" class="btn btn-danger">x</button>
        <slot></slot>
        <button @click="login" class="btn btn-primary">Zaloguj</button>
      </div>
    </section>
</template>

<script>
export default {
  data() {
    return {
      login_box_show: "show",
      username: "",
      password: "",
      log_pass: false,
    };
  },
  methods: {
    hideLoginScreen() {
      this.$emit('hideLoginScreen');
      this.login_box_show = "hide";
    },
    login() {
      if (this.log_pass === true) {
        console.log("WOW! Zalogowałeś się");
      } else {
        console.log("Błąd logowania: chujowe hasło");
      }
    },
  },
};
</script>

<style scoped>
.show {
  animation: show_animation 1.5s ease-in-out;
}

@keyframes show_animation {
  from {
    opacity: 0;
    transform: translate3d(0, -40%, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.hide {
  opacity: 0;
  animation: hide_animation 1.5s ease-in-out;
}

@keyframes hide_animation {
  from {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
  to {
    opacity: 0;
    transform: translate3d(0, -40%, 0);
  }
}

#login_holder {
  border: 3px solid black;
  border-radius: 0.7%;
  width: 100%;
  background-color: antiquewhite;
  padding: 20px;

}
.my-section {
  width: 90%;
  height: 100%;
  background-color: #496886;
  position: absolute;
}
.chuj{
  background-color: #496886;
}

</style>
