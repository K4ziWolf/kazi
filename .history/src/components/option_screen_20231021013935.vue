
<template>
  <section id="my-section" style="position: absolute;">
    <div id="container">
      <div class="option-title" id="option_holder" v-bind:class="option_box_show">
        <!-- Przycisk zamknięcia w prawym górnym rogu -->
        <div id="Exit_button_box" class="btn-close-option-box">
          <button id="exit_button" class="btn btn-danger btn-close-option" @click="hideOptionScreen">
            x
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
</script><style scoped>
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

#option_holder {
  border: 3px solid rgba(255, 255, 255, 0.664);
  border-radius: 0.7%;
  width: 100%;
  background-color: rgba(172, 252, 185, 0.534);
  padding: 20px;
  color: white;
  font-weight: bold;
  position: relative; /* Dodane, aby przycisk był pozycjonowany w obrębie "option_holder" */
}

#Exit_button_box {
  position: absolute;
  top: 10px;
  right: 10px;
}

#my-section {
  width: 100%;
  height: 100%;
  background-color: #496886;
  position: absolute;
}
</style>