<template>
  <section id="my-section" style="background-color: #496886;">
    <div :class="login_box_show" style="padding: 20px; min-height: 20%;">
      <div id="login_holder" class="btn btn-outline-secondary col-md-8 login-holder" style="width: 60%; margin: 0 auto; max-width: 2000px; min-width: 300px; background-color: rgb(59, 59, 59); border-radius: 20px;box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);;" >
        <div class="form-group">
            <label for="username">
                Nazwa użytkownika
            </label>
            <input id="username" class="form-control" type="text" v-model="username" required style="width: 60%; margin: 0 auto; max-width: 500px; min-width: 200px;" >
        </div>
        <div>
          <div class="form-group">
            <label for="password">
              Hasło
            </label>
            <input id="password" class="form-control" type="password" v-model="password" required style="width: 60%; margin: 0 auto; max-width: 500px; min-width: 200px;">
          </div>
        </div>
        <div class="col-12" style="padding: 15px">
          <button @click="hideLoginScreen" class="btn btn-danger btn-close-login" >
            x
          </button>
          <button @click="login" class="btn btn-primary btn-login-here" style="margin-left: 20px;">
            Zaloguj
          </button>
        </div>
      </div>
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
  border: 3px solid rgba(255, 255, 255, 0.664);
  border-radius: 0.7%;
  width: 100%;
  background-color: rgba(172, 252, 185, 0.534);
  padding: 20px;
  color: white;
  font-weight: bold;

}
.my-section {
  width: 90%;
  height: 100%;
  background-color: #496886;
  position: absolute;
}
.btn-login-here {
  background-color: rgb(41, 163, 4);
  border-color: transparent;
  font-weight: bold;
}
.btn-login-here:hover {
  background-color: rgb(3, 112, 18);
  transition: 0.7s;
  border-color: transparent;
}

.btn-close-login {
  font-weight: bold
  ;
}

</style>
