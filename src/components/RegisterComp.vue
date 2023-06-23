<template>
  <div>
    <div class="modal fade" id="modalregistro" data-bs-keyboard="false" tabindex="-1"
      aria-labelledby="staticBackdropLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="staticBackdropLabel"></h5>
            <!-- <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>-->
          </div>
          <!--INGRESO CODIGO DE REGISTRO EN ESTE DIV -->
          <div class="modal-body">
            <link href="css/bootstrap.min.css" rel="stylesheet">
            <!-- Custom styles for this template -->
            <link href="css/signin.css" rel="stylesheet">
            <body class="text-center">
              <main class="form-signin w-100 m-auto text-center shadow-lg p-3 mb-5">
                <form @submit.prevent=postRegister()>
                  <img class="mb-4" src="@/assets/images/Logo1.png" alt="" width="100" height="67">
                  <h1 class="h3 mb-3 fw-normal">Registro</h1>
                  <div class="form-floating">
                    <input type="text" class="form-control rounded-4 mb-1" id="nombre" placeholder="Nombres"
                      v-model="persona.nombre" required>
                    <label for="floatingInput" class="color-form">Nombres</label>
                  </div>
                  <div class="form-floating  ">
                    <input type="text" class="form-control rounded-4 mb-1" id="apellido" placeholder="Apellidos"
                      v-model="persona.apellido" required>
                    <label for="floatingInput" class="color-form">Apellidos</label>
                  </div>
                  <div class="form-floating ">
                    <select class=" color-form form-select pt-1 rounded-4 mb-1 " id="tipo_documento"
                      v-model.lazy="persona.tipo_documento" required>
                      <option disabled value="">Tipo documento</option>
                      <option value="Tarjeta de Identidad">Tarjeta de Identidad</option>
                      <option value="Cedula de Ciudadania">Cedula de Ciudadanía</option>
                      <option value="Cedula de Extranjeria">Cedula de Extrenjeria</option>
                    </select>
                  </div>
                  <div class="form-floating">
                    <input type="text" class="form-control rounded-4 mb-1" id="numerdocu" name="numerdocu"
                      placeholder="Numero de documento" v-model="persona.n_documento" required>
                    <label for="floatingInput" class="color-form">Numero de documento</label>
                  </div>
                  <div class="form-floating">
                    <input type="text" class="form-control rounded-4 mb-1" id="n_ficha" placeholder="n_ficha"
                      v-model="persona.n_ficha" required>
                    <label for="floatingInput " class="color-form">Ficha</label>
                  </div>
                  <div class="form-floating">
                    <input type="number" class="form-control rounded-4 mb-1" id="telefono" v-model="persona.telefono"
                      required>
                    <label for="floatingPassword" class="color-form">Telefono</label>
                  </div>
                  <div class="form-floating">
                    <input type="email" class="form-control rounded-4 mb-1" id="email" placeholder="Correo"
                      v-model="persona.email" required>
                    <label for="email" class="color-form">Correo Electronico</label>
                  </div>
                  <div class="form-floating">
                    <input type="password" class="form-control rounded-4 mb-1" id="contraseña" placeholder="Contraseña"
                      v-model="persona.contrasena" required>
                    <label for="password" class="color-form">Contraseña</label>
                  </div>
                  <div class="form-floating ">
                    <select class=" color-form form-select pt-1 rounded-4 mb-1 " id="rol" v-model.lazy="persona.rol"
                      required>
                      <option disabled value="">Seleccione Rol</option>
                      <option value="Aprendiz">Aprendiz</option>
                    </select>
                  </div>
                  <br>
                  <div>
                    <button type="submit" href="/register"
                      class="w-100 btn btn-lg btn-bd-primary mb-2">Registrarse</button>
                    <button href="/login" class="w-100 btn btn-lg btn-bd-primary">Cancelar</button>
                  </div>
                </form>
                <p class="mt-5 mb-3 text-muted">&copy; Sintapujos 2023</p>
              </main>
            </body>
          </div>
        </div>
        <!--TERMINA CODIGO DE REGISTRO-->
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
          <!-- <button type="button" class="btn btn-primary">Understood</button>-->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Cookies from 'js-cookie'
import Swal from 'sweetalert2';
import axios from 'axios';
export default {
  name: 'RegisterComp',
  data() {
    return {

      persona:{
        nombre:'',
      apellido:'',
      tipo_documento:'',
      n_documento:'',
      n_ficha:'',
      telefono:'',
      email:'',
      rol:'',
      contrasena:''
      }
    }
  },
  methods: {
    postRegister() {
      console.log(this.persona)
      axios.post('http://localhost:4000/persona', this.persona)
        .then((response) => {
          if (response.data.code === 204) {
            Cookies.set('token', response.data.token)
            // this.$router.push('/inicio')
            this.$router.push('/login')
            // eslint-disable-next-line
            $(this.$refs.loginModal).modal('hide')
          }
          Swal.fire({
            position: 'center',
            icon: response.data.icon,
            message: response.data.message,
            showConfirmButton: false,
            timer: 1500
          })
        })
    }
  }
}
</script>


<style scoped>
.color-form {
  color: #20a754;
}

.btn-bd-primary {
  font-weight: 600;
  color: #fff;
  background-color: #52b357;
  border-color: #20a754;
}

.btn-bd-primary:hover,
.btn-bd-primary:active {
  color: #fff;
  background-color: #61428f;
  border-color: #61428f;
}

.btn-bd-primary:focus {
  box-shadow: 0 0 0 3px rgba(121, 82, 179, 0.25)
}


.bd-placeholder-img {
  font-size: 1.125rem;
  text-anchor: middle;
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
}

@media (min-width: 768px) {
  .bd-placeholder-img-lg {
    font-size: 3.5rem;
  }
}

.b-example-divider {
  height: 3rem;
  background-color: rgba(0, 0, 0, .1);
  border: solid rgba(0, 0, 0, .15);
  border-width: 1px 0;
  box-shadow: inset 0 .5em 1.5em rgba(0, 0, 0, .1), inset 0 .125em .5em rgba(0, 0, 0, .15);
}
</style>