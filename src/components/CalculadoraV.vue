<template>
  <!-- Bienvenida a la plataforma -->
  <h1 class="mb-1">Bienvenidos a calculadora hecho con Vue.js</h1>
  <!-- Formulario realizado con el CDN bootstrap -->
  <div class="container d-flex justify-content-center align-items-center" style="min-height: 100vh;">
    <div class="card shadow-sm p-4 w-100" style="max-width: 500px;">
      <div class="form-field text-center" id="formulario">
        <h3 class="mb-4">Cálculo de Notas</h3>
        <!-- Entrada de la primera nota sumativa -->
        <div class="mb-3 text-start">
          <label for="nota1" class="form-label">Ingrese su nota sumativa 1</label>
          <input type="number" class="form-control" name="nota1" id="nota1" placeholder="Ingrese la nota sumativa 1">
        </div>
        <!-- Entrada de la segunda nota sumativa  -->
        <div class="mb-3 text-start">
          <label for="nota2" class="form-label">Ingrese su nota sumativa 2</label>
          <input type="number" class="form-control" name="nota2" id="nota2" placeholder="Ingrese la nota sumativa 2">
        </div>
        <!-- Entrada de la tercera nota sumativa  -->
        <div class="mb-3 text-start">
          <label for="nota3" class="form-label">Ingrese su nota sumativa 3</label>
          <input type="number" class="form-control" name="nota3" id="nota3" placeholder="Ingrese la nota sumativa 3">
        </div>
        <!-- Entrada de la nota del proyecto final  -->
        <div class="mb-4 text-start">
          <label for="notaPF" class="form-label">Ingrese su nota del proyecto final</label>
          <input type="number" class="form-control" name="notaPF" id="notaPF"
            placeholder="Ingrese la nota del proyecto final">
        </div>
        <!-- Boton de calculo que se llama desde las etiquetas script -->
        <button type="submit" class="btn btn-primary w-100" commandfor="invokerDialog" command="show-modal"
          @click="resultado">Calcular</button>
      </div>
      <!-- Dialogo (conocido anteriormente como modal) para mostrar el resultado del calculo -->
      <dialog class="dialog rounded p-3 border-0 shadow" id="invokerDialog">
        <div class="dialog-header d-flex justify-content-between align-items-center mb-3">
          <h4 class="dialog-title m-0">Resultado</h4>
          <button type="button" class="btn-close" commandfor="invokerDialog" command="close"
            aria-label="Close"></button>
        </div>
        <!-- Revelacion del resultado final de la nota desde las etiquetas script -->
        <div class="dialog-body mb-4">
          <p class="m-0">Su nota final es: <strong>{{ notaFinal }}</strong></p>
        </div>
        <div class="dialog-footer text-end">
          <button type="button" class="btn btn-secondary" commandfor="invokerDialog" command="close">Cerrar</button>
        </div>
      </dialog>

    </div>
  </div>
</template>

<script>
/* Funcion calcular que realiza la obtención del valor númerico de las notas y luego 
realiza el calculo de la nota regresando como "calculoInterno"*/
function calcular() {
  let nota1 = Number(document.getElementById("nota1").value)
  let nota2 = Number(document.getElementById("nota2").value)
  let nota3 = Number(document.getElementById("nota3").value)
  let notaPF = Number(document.getElementById("notaPF").value)
  let calculoInterno = (nota1 * 0.20) + (nota2 * 0.20) + (nota3 * 0.20) + (notaPF * 0.40)
  return calculoInterno
}
export default {
  name: 'CalculadoraV',
  /* Se instancia un data para inicializar la variable notaFinal que luego se mostrará en
  el dialogo de resultado */
  data() {
    return {
      notaFinal: 0
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
      this.notaFinal = calcular();
    }
  }
}
</script>