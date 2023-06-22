<template>
    <div>
        <header class="site-header" id="mificoencab">
            <div class="container">

                <div class="row">

                    <div class="col-lg-8 col-12 d-flex flex-wrap">
                        <p class="d-flex me-4 mb-0">
                            <i class="bi-geo-alt me-2"></i>
                            <a href="https://goo.gl/maps/YDaNsaeH6fuv5xUi7"> Sena CTPI reginal cauca, Popayan.</a>
                        </p>

                        <p class="d-flex mb-0">
                            <i class="bi-envelope me-2"></i>

                            <a href="mailto:info@company.com">
                                bienestaraprendizctpi@gmail.com
                            </a>
                        </p>
                    </div>

                    <div class="col-lg-3 col-12 ms-auto d-lg-block d-none">
                        <ul class="social-icon">

                            <li class="social-icon-item">
                                <a href="#" class="social-icon-link bi-twitter"></a>
                            </li>

                            <li class="social-icon-item">
                                <a href="https://www.facebook.com/login" class="social-icon-link bi-facebook"></a>
                            </li>
                            <!--ESTAS REDES POR EL MOMENNTO NO HAY
                        <li class="social-icon-item">
                            <a href="#" class="social-icon-link bi-instagram"></a>
                        </li>

                        <li class="social-icon-item">
                            <a href="#" class="social-icon-link bi-youtube"></a>
                        </li>
                        -->
                            <li class="social-icon-item">
                                <a href="https://web.whatsapp.com" class="social-icon-link bi-whatsapp"></a>
                            </li>

                        </ul>
                    </div>

                </div>
            </div>
        </header>

        <nav class="navbar navbar-expand-lg bg-light shadow-lg mb-0 sticky-top fixed-top ">
            <div class="container p-0 ">
                <a class="navbar-brand" href="index.html">
                    <img src="../assets/images/Logo1.png" class="" width="150" id="logonav">
                    <span>

                        <small></small>
                    </span>
                </a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                    aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>




                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav ms-auto">
                        <li class="nav-item ">

                            <router-link to="/" class="nav-link click-scroll ">Inicio</router-link>
                        </li>

                        <li class="nav-item">
                            <router-link to="/" class="nav-link click-scroll" @click="scrollToSection('section_2')"> Quienes
                                Somos</router-link>

                            <!--  <router-link to="/quienessomos" class="nav-link click-scroll">Quienes Somos</router-link> -->
                        </li>

                        <li class="nav-item">

                            <router-link to="/conoceteycuidate" class="nav-link click-scroll">Conocete y
                                cuidate</router-link>

                            <!-- CON ESTA ETIQUETA NAVEGO EN ESCROLL
                        <a class="nav-link click-scroll" href="#section_3">Conocete y cuidate</a>-->
                        </li>

                        <!-- <li class="nav-item">
                        <a class="nav-link " href="#section_aprender">Juegos</a>
                         CON ESTA ETIQUETA NAVEGO EN ESCROLL
                        <a class="nav-link click-scroll" href="#section_4">Juegos</a>
                    </li> -->

                        <li class="nav-item dropdown">
                            <!--class="nav-link click-scroll dropdown-toggle" EN ESTE CLASE QUITO dropdown-toggle PARA QUE NO DEPLIEGUE 
                        ADEMES -->



                            <router-link to="/comentarios" class="nav-link click-scroll">Comentarios</router-link>


                            <!--ESTE DESPLEGABLE EN EL MOMEMNTO NO

                        <ul class="dropdown-menu dropdown-menu-light" aria-labelledby="navbarLightDropdownMenuLink">
                            <li><a class="dropdown-item" href="news.html">Comentarios</a></li>

                            <li><a class="dropdown-item" href="news-detail.html">News Detail</a></li>
                        </ul>
                        -->
                        </li>

                        <li class="nav-item">
                            <router-link to="/agendacita" class="nav-link click-scroll" v-if="(rol == 'Aprendiz')">{{
                                rol }} </router-link>
                            <!-- <router-link to="/agendacita" class="nav-link click-scroll">Agenda tu cita </router-link> -->
                            <!-- <a class="nav-link click-scroll" href="#section_6">Agenda tu cita </a>-->
                        </li>

                        <li class="nav-item">
                            <router-link to="/enfermera" class="nav-link click-scroll" v-if="(rol == 'Enfermera')">{{
                                rol }}</router-link>

                            <!-- <router-link to="/enfermera" class="nav-link click-scroll">Eventos  </router-link> -->

                        </li>
                        <li class="nav-item">
                            <router-link to="/dashboard" class="nav-link click-scroll" v-if="(rol == 'Sicologa')">{{ rol
                            }} </router-link>
                            <!-- <router-link to="/dashboard" class="nav-link click-scroll">Psicologa  </router-link> -->
                            <!-- <a class="nav-link click-scroll" href="#section_6">Agenda tu cita </a>-->
                        </li>

                    </ul>
                    <div>
                        <button   class="btn-bd-primary rounded-4" @click="cerrarSesion">
                            <i class="bi bi-box-arrow-right"></i> Cerrar sesión
                        </button>
                    </div>

                    

                </div>
            </div>
        </nav>


    </div>
</template>
<script>
import Swal from 'sweetalert2';

export default {
   
    name: 'NavComp',
    methods: {
        cerrarSesion() {
            Swal.fire({
                title: 'Cerrar sesión',
                text: '¿Estás seguro de que deseas cerrar sesión?',
                icon: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#3085d6',
                cancelButtonColor: '#d33',
                confirmButtonText: 'Sí, cerrar sesión',
                cancelButtonText: 'Cancelar',
                timer:8000
            }).then((result) => {
                if (result.isConfirmed) {     
                  window.location.href = '/inicio';                
                }
                
            });
        }
    }

    

}



</script>
<style scoped>



.btn-bd-primary {
    font-weight: 600;
    color: #fff;
    background-color: #4BB5E7;
    border-color: #4BB5E7;

}

.btn-bd-primary:hover,
.btn-bd-primary:active {
    color: #fff;
    background-color: #61428f;
    border-color: #61428f;
}

.btn-bd-primary:focus {
    box-shadow: 0 0 0 3px rgba(179, 82, 174, 0.25)
}
</style>