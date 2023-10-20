<template>
    <div class="holder-ten1" id="menu_holder" :class="menu_box_show">
      <div class="pole-exit-btn" id="Exit_menu_button">
        <button class="exit-baton" id="menu_exit_button " @click="hideMenuScreen">x</button>
        <button class="baton" id="poka-login" v-bind:class="open_login_button" @click="showLoginScreen">
          LOGIN
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        menu_box_show: "show",
        open_login_button: "show",
        isMenuScreenVisible: false, // zmienna która definiuje czy komponent jest widoczyny
      };
    },
    methods: {
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
  </style>
  