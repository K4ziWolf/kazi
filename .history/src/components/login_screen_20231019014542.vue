<template>
    <div id="login_holder" :class="login_box_show">
      <div id="login_username_space">
        <input placeholder="Nazwa użytkownika" type="text" v-model="username" required>
      </div>
      <div id="login_password_space">
        <input placeholder="Hasło" type="password" v-model="password" required>
      </div>
      <div id="Exit_button">
        <button id="login_password_space" @click="hideLoginScreen"> x
          <login_screen v-if="  isLoginScreenVisible">
    </login_screen>
      </button>
        <slot></slot>  <!--jak coś dawid to pole jest to
          przeniesienie pól <login_screen> z App.vue aby to jako tako działało-->
        </div>
        <button id="login_button_space" @click="login">Zaloguj</button>
      </div>
  
  
  </template>
  
  
  <script>
  export default {
   data() {
     return {
       login_box_show: "show",
       username: "",
       password: "",
       log_pass: false,
     };
   },
   methods: {
    hideLoginScreen() {
        this.$emit('hideLoginScreen'); //$emit = wysłanie eventu do folderu
        // nadrzędnego który uruchomi funckję "hideLoginScreen"
        this.login_box_show="hide";
      },
     login() {
       // Sprawdź, czy hasło jest poprawne
       if (this.log_pass === true) {
         // logika dla Wojtka
         console.log("WOW! Zalogowałeś się");
         // Tutaj możesz wykonać przekierowanie lub inne działania po zalogowaniu
       } else {
         console.log("Błąd logowania: chujowe hasło");
       }
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
  
  #login_holder {
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