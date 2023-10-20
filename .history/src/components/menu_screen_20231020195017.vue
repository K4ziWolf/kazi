<template>
    <div class="holder-ten1" id="menu_holder" :class="menu_box_show">
      <div class="pole-exit-btn" id="Exit_menu_button">
        <button class="exit-baton" id="menu_exit_button " @click="hideMenuScreen">x</button>
        <button class="baton" id="poka-login" v-bind:class="open_login_button" @click="showLoginScreen">
          LOGIN
        </button>
      </div>
      <div>
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
        change_theme_btn:"bright",
      };
    },
    methods: {
      open_options(){
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
      }, //emit to event, czyli wysłanie do komponenta rodzica komendy wywołania funckji w tym przypadku hideMenuScreen
      showLoginScreen() {
        this.menu_box_show = "hide";
        setTimeout(() => {
          this.$emit('show-Login-Screen');
        }, 200); //opóźnienie dla dobra animacji chyba tak mi się wydaje dawno temu to pisałem
      },
      openOptionButtonEnter() {
        this.open_option_button = "animated";
      },
      openOptionButtonLeave(){
        this.open_option_button = "unanimated";
      },
    },
  };
  </script>
  <style scoped>  /* scoped dotyczy tylko tego dokumentu */
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

  #menu_holder { /*testy moje do zmiany */
    background-color: rgb(37, 37, 37) !important;
    width: 180px;
    height: 100% !important;
    display: grid;
   position: absolute;
   grid-template-columns: 1fr 1fr;
   grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
   gap: 0px;
   grid-template-areas:
     ". Exit_menu_button"
     " poka-login ."
     ". . .";


  }
  .baton {
    background-color: rgb(18, 165, 13);
    display: inline-grid;
    text-decoration: none;
    width: 130px;
    height: 50px;
    border-radius: 25px;
    text-align: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    border: none;
    justify-content: center;
    align-self: center;
    color: white;
    margin-left: 14%;
    line-height: 50px;
    font-weight: bold;
  }
  .exit-baton {
    border: none;
    background-color: transparent;
    display: grid;

    font-family:Verdana, Geneva, Tahoma, sans-serif;
    font-weight: bold;
    color: white;


  }
  holder-ten1 {
    background-color: rgb(37, 37, 37);
  }
  pole-exit-btn {
    background-color: rgb(37, 37, 37);
  }
  .dark{
    color: rgb(37, 37, 37) !important;
  }
  .bright{

    color: white;
  }
  #gear_icon_box img {
    max-width: 100px;
    cursor: pointer;
  }
  .unanimated{
  animation: back_spin 0.5s;
}
  .animated{
    animation: spin 6s linear infinite;
  }
  @keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
@keyframes back_spin {
  from {
    transform: rotate(360deg); /* Use the actual position you want to rotate back to */
  }
  to {
    transform: rotate(0deg);
  }
 }
  #gear_icon_box{
    height: 30px;
    width: 30px;
  }
  #change_theme_btn{
    border: none;
    background-color: transparent;
    display: grid;

    font-family:Verdana, Geneva, Tahoma, sans-serif;
    font-weight: bold;

   }
  </style>
