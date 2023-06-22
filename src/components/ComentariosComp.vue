<template>
  <div class="componente">
    <div class=" row d-flex justify-content-center  ">
      <div class="col-md-8 col-lg-6">
        <div class=" contenedor card shadow-0 border mb-5 pb-5 mt-2 " style="background-color: #f0f2f5;">
          <div class="card-body p-4">
            <div class="form-outline mb-4 d-flex " v-for="comentario in comentarios" :key="comentario.id_Comentarios"  >
              <input type="text" id="addANote" class="form-control" placeholder="Escribe un cometario..." />
              <input type="button" value="Comentario" class="btn btn-outline-primary  btn-xs   mx-1 ">
            </div>
            <div class="card mb-4">
              <div class="card-body">
                <p>Aquí va el comentario del aprendiz</p>
                <div class="d-flex justify-content-between">
                  <div class="d-flex flex-row align-items-center " v-for="comentario in comentarios"
                    v-bind:key="comentario.id_Comentarios">
                    <p class="small mb-0 ms-2">{{ comentario.n_documento }}:{{ comentario.comentario }} </p>
                  </div>
                  <div class="d-flex flex-row align-items-center">
                    <i class="far fa-thumbs-up mx-2 fa-xs text-black" style="margin-top: -0.16rem;"></i>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import axios from "axios";
import Swal from 'sweetalert2';

export default {
  name: 'ComentariosComp',
  data() {
    return {
      usuarios: null,
      comentarios: [],
      newcomen: { comentario: "", n_documento: "" },
      name: null,
    };
  },
  mounted() {
    this.fetchUserData();
    this.getuser();
  },
  methods: {
    fetchUserData() {
      const persona = JSON.parse(localStorage.getItem('persona'));
      if (persona) {
        this.name = persona.n_documento;
        this.usuarios = [persona];
      } else {
        this.name = null;
        this.usuarios = [];
      }
    },
    getuser() {
      axios.get("http://localhost:4000/api/comentario")
        .then(response => {
          this.comentarios = response.data;
        })
        .catch(error => {
          console.log(error);
        });
    },

    postcomentarios() {
      if (!this.newcomen.comentario) {
        Swal.fire({
          icon: "error",
          title: "Oops...",
          text: "Por favor, completa todos los campos.",
        });
        this.getuser();
      } else {
        // Asigna el número de documento a newcomen.n_documento antes de enviarlo al servidor
        this.newcomen.n_documento = this.numeroDocumento;
        axios.post("http://localhost:4000/api/comentario", this.newcomen)
          .then(response => {
            console.log(response.data);
            Swal.fire({
              position: "top-center",
              icon: "success",
              title: "Comentario creado correctamente.",
              showConfirmButton: false,
              timer: 1500,
            });
            this.getuser();
          })
          .catch(error => {
            console.log(error);
            Swal.fire({
              icon: "error",
              title: "Oops...",
              text: "No se pudo crear el comentario correctamente.",
            });
          });
      }
    },

  },

  computed: {
    numeroDocumento() {
      if (this.usuarios && this.usuarios.length > 0) {
        return this.usuarios[0].n_documento;
      }
      return null;
    },
  }

};
</script>

<style scoped>
.componente {
  background: linear-gradient(60deg, #4BB5E7, transparent);
}
</style>