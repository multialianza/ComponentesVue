<template>
  <div id="app" class="app p-3">
    <h1 class="text-center p-3">Cédula de identidad personalizada</h1>
    <div class="container">
      <div class="containerForm">
        <h3 class="text-center">Ingresa los datos</h3>
        <form v-on:submit.prevent="emitirCi"><!--Formulario de datos solicitados-->
          <div><!--Definición de campos-->
            <label for="run">Run:</label>
            <input type="text" name="run" id="run" v-model="run">
          </div>
          <div>
            <label for="nombres">Nombres:</label>
            <input type="text" name="nombres" id="nombres" v-model="nombres">
          </div>
          <div>
            <label for="apellidos">Apellidos:</label>
            <input type="text" name="apellidos" id="apellidos" v-model="apellidos">
          </div>
          <div>
            <label for="nacionalidad">Nacionalidad:</label>
            <input type="text" name="nacionalidad" id="nacionalidad" v-model="nacionalidad">
          </div>
          <div>
            <label for="sexo">Sexo:</label>
            <input type="text" name="sexo" id="sexo" v-model="sexo">
          </div>
          <div>
            <label for="fechaDeNacimiento">Fecha de naciemiento:</label>
            <input type="text" name="fechaDeNacimiento" id="fechaDeNacimiento" v-model="fechaDeNacimiento">
          </div>
          <div>
            <label for="numeroDeDocumento">Numero de documento:</label>
            <input type="text" name="numeroDeDocumento" id="numeroDeDocumento" v-model="numeroDeDocumento">
          </div>
          <div>
            <label for="fechaDeEmision">Fecha de emisión:</label>
            <input type="text" name="fechaDeEmision" id="fechaDeEmision" v-model="fechaDeEmision">
          </div>
          <div>
            <label for="fechaDeVencimiento">Fecha de vencimiento:</label>
            <input type="text" name="fechaDeVencimiento" id="fechaDeVencimiento" v-model="fechaDeVencimiento">
          </div>
          <div>
            <label for="firmaDelTitular">Firma del titular:</label>
            <input type="text" name="firmaDelTitular" id="firmaDelTitular" v-model="firmaDelTitular">
          </div>
          <div>
            <label for="imagen">Imagen:</label>
            <input type="file" name="imagen" id="imagen" @change="cargarImagen">
          </div>
          <div>
            <input type="submit" class="btn btn-info p-2 mt-2" value="Emitir CI"><!--Define botón emitirCi-->
          </div>

        </form>
      </div>
      <div class="carnet">
        <aside>
          <div>
            <span>CEDULA DE INDENTIDAD</span>
            <img width="40" src="/chile_bandera.png" alt="" />
            <!--<img width="40" src="./assets/logo.png" alt="" />-->
          </div>
          <img src="/foto_elon.jpg" alt="" /><!--Se puede comentar linea 65 y descomentar linea 66 y se puede adjuntar otra foto, para el caso en archivos cantinflas se adjunta-->
          <!--<img :src="imagen" alt="foto" class="imgRun" />-->
          <p>Run {{ run }}</p><!--Dato ingresado en formulario por el usuario-->
        </aside>

        <main>
          <header>
            <p>REPUBLICA DE CHILE</p>
            <span>SERVICIO DE REGISTRO CIVIL E IDENTIFICACIÓN</span>
          </header>

          <section><!--Sección que muestra los datos ingresados por el usuario en el formulario-->
            <article>
              <header>APELLIDOS</header>
              <span>{{ apellidos }}</span>
            </article>

            <article>
              <header>NOMBRES</header>
              <span>{{ nombres }}</span>
            </article>

            <div class="grid-2-colums">
              <article>
                <header>NACIONALIDAD</header>
                <span>{{ nacionalidad }}</span>
              </article>

              <article>
                <header>SEXO</header>
                <span>{{ sexo }}</span>
              </article>
            </div>

            <div class="grid-2-colums">
              <article>
                <header>FECHA DE NACIMIENTO</header>
                <span>{{ fechaDeNacimiento }}</span>
              </article>
              <article>
                <header>NÙMERO DOCUMENTO</header>
                <span>{{ numeroDeDocumento }}</span>
              </article>
            </div>

            <div class="grid-2-colums">
              <article>
                <header>FECHA DE EMISIÒN</header>
                <span>{{ fechaDeEmision }}</span>
              </article>

              <article>
                <header>FECHA DE VENCIMIENTO</header>
                <span>{{ fechaDeVencimiento }}</span>
              </article>
            </div>

            <article>
              <header>FIRMA DEL TITULAR</header>
              <span>{{ firmaDelTitular }}</span>
            </article>
          </section>
        </main>
      </div>

    </div>
  </div>

</template>


<script>
export default {
  name: "App",/*Se define un componente App con sus respectivas propiedades*/ 
  data() {
    return {
      run: "",
      apellidos: "",
      nombres: "",
      nacionalidad: "",
      sexo: "",
      fechaDeNacimiento: "",
      numeroDeDocumento: "",
      fechaDeEmision: "",
      fechaDeVencimiento: "",
      firmaDelTitular: "",
      imagen: ""
    };
  },
  components: {},/*Se definen métodos */
  methods: {
    emitirCi: function () {   /*Método emitirCi mostrando mensaje de alerta  y luego llama a otro método limpirFormulario, el que se encarga de limpiar todos los campos de datos del formulario */
      alert(`Su cédula Run ${this.run} fue creada con éxito!!!`)
      this.limpiarFormulario();
    },
    limpiarFormulario() {
    this.run = "";
    this.apellidos = "";
    this.nombres = "";
    this.nacionalidad = "";
    this.sexo = "";
    this.fechaDeNacimiento = "";
    this.numeroDeDocumento = "";
    this.fechaDeEmision = "";
    this.fechaDeVencimiento = "";
    this.firmaDelTitular = "";
    this.imagen = "";
    },
    cargarImagen(event) {   /*Define el método cargarImagen , el que carga una imagen seleccionada por el usuario */
      const file = event.target.files[0];
      const reader = new FileReader();

      reader.onload = e => {
        this.imagen = e.target.result;
      };

      reader.readAsDataURL(file);
    }
  },
/*Finalmente se exporta el componete App para poder ser utilizado en otros componentes de la aplición Vue. */
};
</script>

<style>
/*Estilos de formulario solicitado */
body {
  font-family: sans-serif;
  font-size: 10px;
  background-color: rgb(55, 114, 231);
}
.container {
  display: flex;
  justify-content: space-evenly;
  padding: 50px;
  background-color: rgb(237, 43, 43);
  border-radius: 15px;
}

.containerForm {
  background-color: rgb(124, 147, 222);
  padding: 25px;
  border-radius: 15px;
}

label {
  width: 200px;

}


.carnet {
  width: 500px;
  height: auto;
  background: #cfd2cd;
  border-radius: 20px;
  display: grid;
  grid-template-columns: 30% 1fr;
  padding: 15px;
  box-shadow: 0px 0px 10px 2px black;
}

aside div {
  display: flex;
}

aside>img {
  margin-top: 25px;
  width: 100%;
  height: 70%;
}

aside p {
  text-align: center;
  font-size: 12px;
  font-weight: bold;
}

main {
  padding: 0px 14px;
}

main article {
  margin: 4px 0px;
}

main article header {
  font-weight: bold;
  color: #0235a4;
  font-size: 8px;
}

main header p {
  font-size: 20px;
  margin: 0;
  font-weight: bold;
  color: #0235a4;
}

main header span {
  font-size: 8px;
  color: #399be1;
}

main section {
  margin-top: 10px;
}

main section article span {
  font-size: 13px;
  font-weight: 600;
}

main section .grid-2-colums {
  display: grid;
  grid-template-columns: 50% 50%;
}
</style>
