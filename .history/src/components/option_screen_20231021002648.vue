<template>
  <div class="option-title" id="option_holder" v-bind:class="option_box_show" >
    Opcje
    <div id="Exit_button_box" class="btn-close-login-box">
      <button id="exit_button" class="btn btn-danger btn-close-login" @click="hideOptionScreen">
        x
      </button>

    </div>
  </div>
</template>


<script>
export default {
 data() {
   return {
    option_box_show:"show",
   };
 },
 methods: {
  hideOptionScreen() {
      this.$emit('hide-option-screen');
      this.option_box_show = "hide";
    },
 },
};
</script>
<style scoped> /*przekopiuj z tego co wczoraj robiłeś*/
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
#option_holder {
  display: grid;
  position: absolute;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
  gap: 5px 5px;
  grid-template-areas:
    ". Exit_button_Settings"
    ". . . ."
    ". . . ."
    ". . . ."
    ". . . .";
  border: 3px solid black;
  border-radius: 0.7%;
  width: 50%;
  height: 60%;
  background-color: rgb(27, 77, 124);
  margin-left: 25%;
  margin-right: 20%;
  top: 20%;
  justify-content: center;
  text-align: center;
}
#login_username_space {
  grid-area: login_username;
}
#Exit_button_Settings { /* Zaktualizowana linia: zmiana identyfikatora na nazwę klasy */
  display: flex; /* Zaktualizowana linia: użyj flexbox */
  justify-content: flex-end; /* Zaktualizowana linia: przesuń na prawą stronę */
  cursor: pointer;
}
#login_password_space {
  grid-area: Login_password;
}
#login_button_space {
  grid-area: Login_button;
}
.btn-close-login {
  position: absolute;
  display: flex;
  justify-content: flex-end;
}
.btn-close-login-box {
  position: fixed;
  justify-content: flex-end; /* Zaktualizowana linia: przesuń zawartość na prawą stronę */
  display: flex;
  justify-content: flex-start;
}
.option-title {
  text-align: center;
  display: inline;
  justify-content: center;
  align-self: center;
  margin-left: 50%;
  margin-right: 50%;
}
</style>