<template>
<body>
  <section>
  <div id="container" class="col-md-12">
    <div class="d-flex flex-column text-white" style="background-color: rgb(61, 61, 61) ">
    <div class="x-btn">
      <button class="btn btn-outline-secondary" v-bind:class="open_menu_button " @click="showMenuScreen" >
        Pokaż menu
      </button>
      <menu_screen v-if="isMenuScreenVisible" @hide-menu-screen="hideMenuScreen" @show-login-screen="showLoginScreen" @change-theme="changeTheme" @option-open="optionOpener">
      </menu_screen>

    <div> <!--menu_scree i login_screen odpowiedzialne są za pokazywanie się tych komponentów-->
      <login_screen v-if="isLoginScreenVisible" @hide-login-screen="hideLoginScreen">
      </login_screen>
    </div>
    <option_screen v-if="isOptionScreenVisible" @hide-option-screen="HideOptionScreen">
      </option_screen>
  </div>
  </div>
  </div>
  </section>
</body>
</template>

<script>
import menu_screen from './components/menu_screen.vue';
import login_screen from './components/login_screen.vue';
import option_screen from './components/option_screen.vue';
export default {
  components: {
    menu_screen,
    login_screen,
    option_screen,
  },
  data() {
    return {
      open_menu_button: "show",
      open_login_button: "show",
      isLoginScreenVisible: false,
      isMenuScreenVisible: false,
      changecolor:0,
      isOptionScreenVisible: false,
    };
  },
  methods: {
    optionOpener(){

      this.isOptionScreenVisible = true;
    },
    HideOptionScreen(){
      this.isOptionScreenVisible = false;
      setTimeout(() => {
      this.open_menu_button = "show";

      }, 1000);
    },
    changeTheme() {
        this.changecolor += 1;
      if (this.changecolor % 2 === 0) {
        document.body.style.backgroundColor = 'blue';
      } else {
        document.body.style.backgroundColor = 'red';
      }
    },
    showMenuScreen() { //funkcja pokazująca menu
      this.isMenuScreenVisible = true;
      this.open_menu_button = "hidden";
      this.open_login_button = "show";
    },
    hideMenuScreen() {
      setTimeout(() => { //timeout aby animacja była płynna
        this.open_menu_button = "show";
        this.isMenuScreenVisible = false;
      }, 1200);
    },
    showLoginScreen() {
      this.isLoginScreenVisible = true;
      setTimeout(() => {
      this.isMenuScreenVisible = false;
      }, 1000);
    },
    hideLoginScreen() {
      setTimeout(() => {
        this.open_login_button = "show";
        this.open_menu_button ='show'
        this.isLoginScreenVisible = false;
      }, 1500);
    },
  },
};
</script>

<style>
@import '/src/style.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.show {
  opacity: 1;
  animation: show_button 0.4s;
}
@keyframes show_button {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.hidden {
  animation: hide_button 0.4s;
  opacity: 0;
}
@keyframes hide_button {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
body { /*testy moje do zmiany */
  height: 100%;
  width: 100%;
  background-color: rgb(127, 247, 207);
}
.x-btn {
  background-color: rgb(61, 61, 61);

}
.xd-btn {
  text-decoration: none;
  border: none;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  background-color: #2c3e50;
  border-bottom-left-radius: 25px;
  border-bottom-right-radius: 25px;
  color: white;
  font-weight: bolder;

}
html {
  background-color: #496886;
}
</style>
