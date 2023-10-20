<template>
  <section id="my-section" >
    <div class="option-title" id="option_holder" v-bind:class="option_box_show" style="width: 60%; margin: 0 auto; max-width: 2000px; min-width: 300px; background-color: rgb(59, 59, 59); border-radius: 20px;box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);;" >
    Opcje
    <div id="Exit_button_box" class="btn-close-login-box">
      <button id="exit_button" class="btn btn-danger btn-close-login" @click="hideOptionScreen">
        x
      </button>
    </div>
  </div>
  </section>
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
#option_holder {
  border: 3px solid rgba(255, 255, 255, 0.664);
  border-radius: 0.7%;
  width: 100%;
  background-color: rgba(172, 252, 185, 0.534);
  padding: 20px;
  color: white;
  font-weight: bold;

}
#my-section {
  width: 100%;
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
