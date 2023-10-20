
<template>
  <section id="my-section" style="position: absolute;">
    <div id='container'>
      <div class="option-title" id="option_holder" v-bind:class="option_box_show" style="width: 60%; margin: 0 auto; max-width: 2000px; min-width: 300px; background-color: rgb(59, 59, 59); border-radius: 20px;box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);" >
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
</script>option_holder