<template>
  <!-- Bienvenida a la plataforma -->
  <h1 class="mb-1">Bienvenidos a calculadora hecho con Vue.js</h1>
  <br>
  <!-- Formulario realizado con el CDN bootstrap -->
  <div class="container d-flex justify-content-center align-items-center">
    <div class="card shadow-sm p-4 w-100" style="max-width: 500px;">
      <div class="form-field text-center" id="formulario">
        <h3 class="mb-4">Cálculo de Notas</h3>
        <!-- Entrada de la primera nota sumativa -->
        <div class="mb-3 text-start">
          <label for="nota1" class="form-label">Ingrese su nota sumativa 1</label>
          <input type="number" class="form-control" name="nota1" placeholder="Ingrese la nota sumativa 1"
            v-model.number="nota1" min="0" max="100">
        </div>
        <!-- Entrada de la segunda nota sumativa  -->
        <div class="mb-3 text-start">
          <label for="nota2" class="form-label">Ingrese su nota sumativa 2</label>
          <input type="number" class="form-control" name="nota2" placeholder="Ingrese la nota sumativa 2"
            v-model.number="nota2" min="0" max="100">
        </div>
        <!-- Entrada de la tercera nota sumativa  -->
        <div class="mb-3 text-start">
          <label for="nota3" class="form-label">Ingrese su nota sumativa 3</label>
          <input type="number" class="form-control" name="nota3" placeholder="Ingrese la nota sumativa 3"
            v-model.number="nota3" min="0" max="100">
        </div>
        <!-- Entrada de la nota del proyecto final  -->
        <div class="mb-4 text-start">
          <label for="notaPF" class="form-label">Ingrese su nota del proyecto final</label>
          <input type="number" class="form-control" name="notaPF" id="notaPF" v-model.number="notaPF"
            placeholder="Ingrese la nota del proyecto final" min="0" max="100">
        </div>
        <!-- Boton de calculo que se llama desde las etiquetas script -->
        <button type="button" class="btn btn-primary btn-lg" @click="resultado()">Calcular</button>
      </div>
      <!-- Alerta de Error de Bootstrap 5 -->
      <div v-if="esError && mensajeRespuesta" class="alert alert-danger text-start mt-3 mb-0" role="alert">
        {{ mensajeRespuesta }}
      </div>
      <!-- Alerta de Éxito de Bootstrap 5 con el Promedio Final -->
      <div v-if="!esError && mensajeRespuesta" class="alert alert-success text-center mt-3 mb-0" role="alert">
        <p class="m-0 text-muted">Promedio Final Ponderado:</p>
        <h2 class="fw-bold m-0 text-success">{{ mensajeRespuesta }}</h2>
      </div>
    </div>
  </div>
</template>

<script>

/* Funcion calcular que realiza la obtención del valor númerico de las notas y luego 
realiza el calculo de la nota regresando como "calculoInterno"*/
function calcular(nota1, nota2, nota3, notaPF) {
  /**
 Validacion del contenido antes de realizar el calculo 
 */
  if (
    nota1 === null || nota1 === '' || isNaN(nota1) ||
    nota2 === null || nota2 === '' || isNaN(nota2) ||
    nota3 === null || nota3 === '' || isNaN(nota3) ||
    notaPF === null || notaPF === '' || isNaN(notaPF)
  ) {
    return { exito: false, mensaje: "Por favor, complete todas las calificaciones." };
  }
  if (
    nota1 < 0 || nota1 > 100 ||
    nota2 < 0 || nota2 > 100 ||
    nota3 < 0 || nota3 > 100 ||
    notaPF < 0 || notaPF > 100
  ) {
    return { exito: false, mensaje: "Error: Las notas deben estar en un rango de 0 a 100." };
  }
  /*Realizacion del calculo*/
  let calculoInterno = (nota1 * 0.20) + (nota2 * 0.20) + (nota3 * 0.20) + (notaPF * 0.40);
  return { exito: true, mensaje: calculoInterno.toFixed(2) };
}
export default {
  name: 'CalculadoraV',
  /* Se instancia un data para inicializar la variable notaFinal que luego se mostrará en
  el dialogo de resultado */
  data() {
    return {
      nota1: null,
      nota2: null,
      nota3: null,
      notaPF: null,
      esError: false,
      mensajeRespuesta: null
    }
  },
  props: {
    msg: String
  },
  methods: {

    /*Se conecta la función calcular con la variable notaFinal a tráves de un metodo que 
    se nombrará resultado y se ejecutara cuando se realice un click en el botón "Calcular"
    en el formulario */
    resultado() {
      const res = calcular(this.nota1, this.nota2, this.nota3, this.notaPF);

      this.esError = !res.exito;
      this.mensajeRespuesta = res.mensaje;
    }
  }
}
</script>