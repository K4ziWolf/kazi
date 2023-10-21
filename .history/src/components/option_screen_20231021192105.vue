
<template>
  <section id="my-section" style="position: absolute;" v-bind:class="option_box_show">
    <div id='container' style="padding: 20px;" >
      <div class="option-title" id="option_holder"  style="width: 60%; margin: 0 auto; max-width: 2000px; min-width: 300px; background-color: rgb(59, 59, 59); border-radius: 20px;box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19); " >
        <div id="Exit_button_box" class="btn-close-option-box">
          <button id="exit_button" class="btn btn-danger btn-close-option" @click="hideOptionScreen">
            x
          </button>
        </div>
        ym jest Lorem Ipsum?
Lorem Ipsum jest tekstem stosowanym jako przykładowy wypełniacz w przemyśle poligraficznym. Został po raz pierwszy użyty w XV w. przez nieznanego drukarza do wypełnienia tekstem próbnej książki. Pięć wieków później zaczął być używany przemyśle elektronicznym, pozostając praktycznie niezmienionym. Spopularyzował się w latach 60. XX w. wraz z publikacją arkuszy Letrasetu, zawierających fragmenty Lorem Ipsum, a ostatnio z zawierającym różne wersje Lorem Ipsum oprogramowaniem przeznaczonym do realizacji druków na komputerach osobistych, jak Aldus PageMaker

Do czego tego użyć?
Ogólnie znana teza głosi, iż użytkownika może rozpraszać zrozumiała zawartość strony, kiedy ten chce zobaczyć sam jej wygląd. Jedną z mocnych stron używania Lorem Ipsum jest to, że ma wiele różnych „kombinacji” zdań, słów i akapitów, w przeciwieństwie do zwykłego: „tekst, tekst, tekst”, sprawiającego, że wygląda to „zbyt czytelnie” po polsku. Wielu webmasterów i designerów używa Lorem Ipsum jako domyślnego modelu tekstu i wpisanie w internetowej wyszukiwarce ‘lorem ipsum’ spowoduje znalezienie bardzo wielu stron, które wciąż są w budowie. Wiele wersji tekstu ewoluowało i zmieniało się przez lata, czasem przez przypadek, czasem specjalnie (humorystyczne wstawki itd).


Skąd się to wzięło?
W przeciwieństwie do rozpowszechnionych opinii, Lorem Ipsum nie jest tylko przypadkowym tekstem. Ma ono korzenie w klasycznej łacińskiej literaturze z 45 roku przed Chrystusem, czyli ponad 2000 lat temu! Richard McClintock, wykładowca łaciny na uniwersytecie Hampden-Sydney w Virginii, przyjrzał się uważniej jednemu z najbardziej niejasnych słów w Lorem Ipsum – consectetur – i po wielu poszukiwaniach odnalazł niezaprzeczalne źródło: Lorem Ipsum pochodzi z fragmentów (1.10.32 i 1.10.33) „de Finibus Bonorum et Malorum”, czyli „O granicy dobra i zła”, napisanej właśnie w 45 p.n.e. przez Cycerona. Jest to bardzo popularna w czasach renesansu rozprawa na temat etyki. Pierwszy wiersz Lorem Ipsum, „Lorem ipsum dolor sit amet...” pochodzi właśnie z sekcji 1.10.32.

Standardowy blok Lorem Ipsum, używany od XV wieku, jest odtworzony niżej dla zainteresowanych. Fragmenty 1.10.32 i 1.10.33 z „de Finibus Bonorum et Malorum” Cycerona, są odtworzone w dokładnej, oryginalnej formie, wraz z angielsk


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
    this.option_box_show = "hide";
    setTimeout(() => {
      this.$emit('hide-option-screen');
    }, 200);


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
  #option_holder {
  display: grid;
  grid-template-columns: auto 1fr;
  grid-template-rows: auto;
  border: 3px solid rgba(255, 255, 255, 0.664);
  border-radius: 0.7%;
  width: 100%;
  background-color: rgba(172, 252, 185, 0.534);
  padding: 20px;
  color: white;
  font-weight: bold;
}
}
#Exit_button_box {
  grid-column: 2;
  grid-row: 1;
  text-align: right;
}
#exit_button {
  background: none;
  border: none;
  font-size: 20px;
}
#my-section {
  width: 100%;
  height: 100%;
  background-color: #496886;
  position: absolute;
}

</style>
