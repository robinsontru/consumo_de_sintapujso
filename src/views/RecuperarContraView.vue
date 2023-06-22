<template>
     <div class="contprincipal" id="pruebas">
        <nav class="navbar navbar-expand-lg bg-light shadow-lg mb-0 sticky-top fixed-top ">
            <div class="container p-0 ">
                <a class="navbar-brand" href="index.html">
                    <img src="../assets/images/Logo1.png" class="" width="150" height="60" id="logonav">

                </a>
            </div>
        </nav>
        <main>

            <div class="divrecuperar">
                <div class="cont1">
                    <div class="headerh4">
                        <h4 class="titulo1">Recuperar contraseña</h4>
                    </div>
                    <hr size="2px" color="black" />
                    <div class="bodycont">
                        <p class="texto1">Ingresa tu correo electrónico para el reestablecimiento de la contraseña.</p>
                        <input class="inputemail" type="email" placeholder="email">
                    </div>
                    <hr size="2px" color="black" />
                    <div class="footercont">
                        <RouterLink to="/" class="btn btn-secondary mx-1">Cancelar </Routerlink>
                        <Routerlink to="" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#modalcodigo">
                            Enviar</Routerlink>
                    </div>

                    <!--inserto modal-->
                    <div class="contenedormodal1">
                        <div class="modal" tabindex="-1" id="modalcodigo">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <h4 class="titulomodal1">Ingresa el código de seguridad</h4>
                                    </div>
                                    <div class="modal-body">
                                        <p class="textcodigo">Comprueba si recibiste un correo electrónico con tu código de 6 dígitos.</p>
                                        <input type="text" class="inputcodigo" placeholder="Ingresa el código">
                                        <p class="textcodigo">Escribe tu nueva contraseña.</p>
                                        <input type="password" class="inputcodigo">
                                       
                                    </div>
                                    <div class="modal-footer">
                                        <button type="button" class="btn btn-secondary"
                                            data-bs-dismiss="modal">Cancelar</button>
                                        <button type="button" class="btn btn-primary">Aceptar</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </main>
    </div>
</template>

<script>
export default {
    name: 'RecuperarContraView',
}
</script>

<style scoped>
.divrecuperar {
    width: 100%;
    display: grid;
    height: 90vh;
    place-content: center;
    background-color: rgb(219, 236, 251)
}

.navbar {
    height: 10vh;
}

.cont1 {
    border-right-color: black;
    border-radius: 10px;
    height: 50vh;
    background-color: rgb(249, 250, 250);
}

.headerh4 .titulo1 {
    font-size: 20px;
    text-align: left;
    margin: 5px;
    padding: 10px;

}

.bodycont {
    text-align: left;
    padding-left: 10px;
    margin: 15px 10px 10px 10px;
    height: 20vh;
}

.texto1 {
    color: #000;

}

.inputemail {
    width: 95%;
    height: 8vh;
    border-color: rgb(202, 201, 201);
    border-radius: 10px;
}

.footercont {
    height: 20vh;
    text-align: right;
    padding: 10px 10px 10px 10px;
    margin: 8px;
}

button {
    margin-inline-end: 7px;

}

 .titulomodal1{
    font-size: 20px;
    text-align: left;
   
}
.modal-body {
    text-align: left; 
    padding-left: 10px;
   
}

.modal-body .textcodigo{
    color: #000;
    padding: 4px 1px 2px 1px; 
    margin: 3px; 
}

.modal-body .inputcodigo{
    border-radius: 10px;
    width: 50%;
    height: 7vh;
    margin: 5px; 
   

}


</style>