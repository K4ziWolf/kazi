<template>
  <div class="holder-ten1 col-sm-6" id="menu_holder" :class="menu_box_show">
    <div class="pole-exit-btn" id="Exit_menu_button">
      <button class="exit-baton" id="menu_exit_button" @click="hideMenuScreen">x</button>
      <button class="baton" id="poka-login" v-bind:class="open_login_button" @click="showLoginScreen">
        LOGIN
      </button>
      <button id="change_theme_btn" v-bind:class="change_theme_btn" @click="changeTheme">
        Zmiana motywu
      </button>
      <div id="gear_icon_box">
        <img
          v-bind:class="open_option_button"
          src="../assets/gear_icon.png"
          alt="Gear Icon"
          @mouseenter="openOptionButtonEnter"
          @mouseleave="openOptionButtonLeave"
          @click="open_options"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menu_box_show: "show",
      open_option_button: "unanimated",
      change_theme_btn: "bright",
    };
  },
  methods: {
    open_options() {
      this.$emit('option-open');
    },
    changeTheme() {
      if (this.change_theme_btn === 'dark') {
        this.change_theme_btn = 'bright';
      } else {
        this.change_theme_btn = 'dark';
      }
      this.$emit('change-theme');
    },
    hideMenuScreen() {
      this.$emit('hide-menu-screen');
      this.menu_box_show = "hide";
    },
    showLoginScreen() {
      this.menu_box_show = "hide";
      setTimeout(() => {
        this.$emit('show-Login-Screen');
      }, 200);
    },
    openOptionButtonEnter() {
      this.open_option_button = "animated";
    },
    openOptionButtonLeave() {
      this.open_option_button = "unanimated";
    },
  },
};
</script>

<style scoped>
.show {
  animation: show_animation 1s ease-in-out;
}

@keyframes show_animation {
  from {
    opacity: 0;
    transform: translate3d(-40%, 0, 0);
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.hide {
  opacity: 0;
  animation: hide_animation 1s ease-in-out;
}

@keyframes hide_animation {
  from {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
  to {
    opacity: 0;
    transform: translate3d(-40%, 0, 0);
  }
}

#menu_holder {
  background-color: rgb(37, 37, 37) !important;
  position: absolute;
  height: 100vh; /* Ustawienie na 100% wysokości strony */
  display: grid;
  grid-template-columns: 1fr; /* Pasek będzie miał tylko jedną kolumnę */
  gap: 0px;
  grid-template-areas: "Exit_menu_button" "poka-login" "change_theme_btn" "gear_icon_box";
}

.baton {
  background-color: rgb(18, 165, 13);
  display: inline-grid;
  text-decoration: none;
  width: 100%; /* Rozciągnij przycisk na 100% szerokości kontenera */
  height: 50px;
  border-radius: 25px;
  text-align: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  border: none;
  color: white;
  font-weight: bold;
  margin-bottom: 10px; /* Dodaj odstęp między przyciskami */
}

.exit-baton {
  border: none;
  background-color: transparent;
  display: grid;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-weight: bold;
  color: white;
}

/* Pozostałe style bez zmian */

</style>
