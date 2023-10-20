<template>
<body>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Dropdown
          </a>
          <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
            <li><a class="dropdown-item" href="#">Action</a></li>
            <li><a class="dropdown-item" href="#">Another action</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#">Something else here</a></li>
          </ul>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>
  <div id="box">
    <div class="x-btn"><button class="xd-btn" v-bind:class="open_menu_button " @click="showMenuScreen">Pokaż menu</button>
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
      setTimeout(() => {
      this.isOptionScreenVisible = false;
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
  justify-content: left;
  text-align: left;

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
  position: absolute;
  justify-content: left;
}
html {
  background-color: #496886;
}
</style>
