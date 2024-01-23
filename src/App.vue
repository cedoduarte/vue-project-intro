<template>
  <h1>Hola a todos</h1>
  <h2>{{ saludo.toUpperCase() }}</h2>
  {{ botonHTML }}
  <span v-html="botonHTML"></span>
  <p v-bind:style="color">TEST</p>
  <a :href="web">Google</a>
  {{ 2*9 }}
  <h2 :style="`color: ${ahorros >= 200 ? 'green' : 'red'}`">$ {{ ahorros }}</h2>
  <h2 :class="ahorros >= 200 ? 'conFondo' : 'sinFondo'">$ {{ ahorros }}</h2>
  <p v-if="puntajeCrediticio >= 900">Cliente excelente</p>
  <p v-else-if="puntajeCrediticio >= 700">Cliente regular</p>
  <p v-else>Cliente pésimo</p>

  <p v-show="puntajeCrediticio >= 900">TEST</p>

  <ul>
    <li v-for="(item, index) in letras" :key="index">{{ item }}</li>
  </ul>

  <p>
    Listado de números del 1 al 10
    <span v-for="numero in 10" :key="numero">{{ numero }}-</span>
  </p>

  {{ letras }}
  {{ {name:"Joel"} }}

  Deletrear mi nombre:
  <ul>
    <li v-for="(letra, index) in 'Carlos'" :key="index">{{ letra }}</li>
  </ul>

  <div v-for="(valor, propiedad, index) in user" :key="index">
    {{ valor }} - {{ propiedad }} - {{ index }}
  </div>

  <div>
    <h1>Cuestionaro</h1>
    <hr />
    <div v-for="(question, questionIndex) in preguntasProgramacion" :key="questionIndex">
      <h4>{{ questionIndex+1 }}. {{ question.pregunta }}</h4>
      <div v-for="(option, optionIndex) in question.opciones" :key="optionIndex">
        <p v-if="question.respuestaCorrecta === option">✅{{ option }}</p>
        <p v-else>❌{{ option }}</p>
      </div>
    </div>
  </div>

  <button @click.right.prevent="console.log('OK')">Enviar</button>
  <input @blur="console.log('OK')" type="text">

  <h2>Ahorros: ${{ fondoAhorro }}</h2>
  {{ status }}
  <button @click="deposita(100)">Depositar $100</button>
  <button @click="status = !status">Cambiar status</button>
</template>

<script setup lang="ts">
import { ref } from "vue";

const fondoAhorro = ref<number>(500);
const status = ref<boolean>(false);

const deposita = (cantidad: number) => {
  fondoAhorro.value += cantidad;
  console.log(fondoAhorro);
}

const saludo = "Hola a todos, suscribanse";
const botonHTML = "<button>Enviar</button>";
const color = "color: red; background: black";
const web = "http://google.com";
const ahorros = 1500;
const puntajeCrediticio = 900;
const letras = ["a","b","c"];
const user = {
  name: "Carlos",
  edad: 29,
  confianza: true
};
var preguntasProgramacion = [
  {
    pregunta: "¿Cuál de las siguientes palabras clave se utiliza para declarar una variable en JavaScript?",
    opciones: ["variable", "var", "declare", "let"],
    respuestaCorrecta: "var"
  },
  {
    pregunta: "¿Qué tipo de lenguaje de programación es JavaScript?",
    opciones: ["Lenguaje de programación de bajo nivel", "Lenguaje de programación de alto nivel", "Lenguaje ensamblador", "Lenguaje de máquina"],
    respuestaCorrecta: "Lenguaje de programación de alto nivel"
  },
  {
    pregunta: "¿Cuál es la función de 'console.log()' en JavaScript?",
    opciones: ["Mostrar un mensaje de alerta", "Imprimir en la consola del navegador", "Ejecutar una función", "Crear un bucle"],
    respuestaCorrecta: "Imprimir en la consola del navegador"
  },
  {
    pregunta: "¿Qué significa CSS en el desarrollo web?",
    opciones: ["Cascading Style Sheet", "Central Style Sheet", "Computer Style Sheet", "Creative Style Sheet"],
    respuestaCorrecta: "Cascading Style Sheet"
  },
  {
    pregunta: "En programación, ¿qué es un 'if'?",
    opciones: ["Un bucle", "Una función", "Una declaración condicional", "Un operador aritmético"],
    respuestaCorrecta: "Una declaración condicional"
  },
  {
    pregunta: "¿Cuál es el símbolo de asignación en JavaScript?",
    opciones: ["=", "==", "===", "+="],
    respuestaCorrecta: "="
  },
  {
    pregunta: "¿Cuál de las siguientes no es una variable en JavaScript?",
    opciones: ["let", "const", "log", "var"],
    respuestaCorrecta: "log"
  },
  {
    pregunta: "¿Qué hace el método 'addEventListener' en JavaScript?",
    opciones: ["Añade un evento a un elemento", "Elimina un evento de un elemento", "Crea un nuevo elemento", "Cambia el estilo de un elemento"],
    respuestaCorrecta: "Añade un evento a un elemento"
  },
  {
    pregunta: "¿Cuál es el propósito de 'git' en el desarrollo de software?",
    opciones: ["Gestionar bases de datos", "Control de versiones", "Compilar código", "Diseñar interfaces de usuario"],
    respuestaCorrecta: "Control de versiones"
  },
  {
    pregunta: "En programación, ¿qué es una 'API'?",
    opciones: ["Aplicación de Programación de Interfaz", "Asociación de Programadores Internacionales", "Arquitectura de Programación Integrada", "Interfaz de Programación de Aplicaciones"],
    respuestaCorrecta: "Interfaz de Programación de Aplicaciones"
  }
];
</script>

<style scoped>
.sinFondo {
  color: red;
}

.conFondo {
  color: green;
}
</style>
