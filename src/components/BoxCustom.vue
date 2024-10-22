<template>
  <section class="box-main">
    <div class="box-custom">
      <label>Color de fondo</label>
      <input v-model="bgColor" type="text" />
      <label>Color de texto</label>
      <input v-model="textColor" type="text" />
      <div class="checkbox">
        <label>Mostrar texto</label>
        <input  type="checkBox" v-model="showText" />
      </div>
      <label>Borde</label>
      <input v-model="border" type="range" min="0" max="120" />
      <label>Contenido textual</label>
      <textarea v-model="text"></textarea>
      <label>Tipografía</label>
      <select v-model="fontSelected">
        <option disabled value="">Seleciona una fuente</option>
        <option v-for="typography in font" :value="typography" :key="typography">{{typography}}</option>
      </select>
      <div class="checkbox">
        <label>Opacidad</label>
        <input v-model="opacity" type="checkBox" />
      </div>
      <label>Tamaño de letra</label>
      <div class="inputRadio">
        <input v-model="fontSize" type="radio" value="pequeño"/>Pequeño
        <input v-model="fontSize" type="radio" value="mediano"/>Mediano
        <input v-model="fontSize" type="radio" value="grande"/>Grande
      </div>
    </div>
    <div
      id="box-rendering"
      :class="fontSize"
      :style="{
        backgroundColor: bgColor,
        color: textColor,
        borderRadius: `${border}px`,
        opacity: opacity ? 0.5 : 1,
        fontSize,
        fontFamily: fontSelected,

      }"
    >
      <p v-show="showText">
        {{ text }}
      </p>
    </div>
  </section>
</template>

<script>
export default {
  name: "BoxCustom",
  data() {
    return {
      bgColor: "",
      textColor: "",
      showText: false,
      border: 0,
      text: "",
      font: ["cursive", "sans-serif", "serif", "monospace"],
      fontSelected: "",
      opacity: false,
      fontSize: "mediano",

    };
  },
};
</script>

<style scoped>
.box-main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  gap: 20px;
}
.box-custom {
  display: flex;
  flex-direction: column;
  gap: 10px;
  background-color: cadetblue;
  padding: 20px;
}
.checkbox {
  display: flex;
  gap: 10px;
  align-items: center;
}
#box-rendering {
  height: 200px;
  width: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
  padding: 20px;
  
}
.pequeño {
  font-size: 15px;
}
.mediano {
  font-size: 25px;
}
.grande {
  font-size:35px;
}
</style>
