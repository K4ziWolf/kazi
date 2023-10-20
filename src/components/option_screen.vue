<template>
  <div id="option_holder" v-bind:class="option_box_show">
    Opcje
    <div id="Exit_button_box">
      <button id="exit_button" @click="hideOptionScreen">
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
   ". . . Exit_button"
   ". login_username login_username ."
   ". Login_password Login_password ."
   ". . Login_button ."
   ". . . .";
 border: 3px solid black;
 border-radius: 0.7%;
 width: 50%;
 height: 60%;
 background-color: antiquewhite;
 margin-left: 25%;
 margin-right: 20%;
 top: 20%;
}
#login_username_space {
 grid-area: login_username;
}
#exit_button_space {
 grid-area: Exit_button;
 cursor: pointer;
}
#login_password_space {
 grid-area: Login_password;
}
#login_button_space {
 grid-area: Login_button;
}
</style>