<template>
  <div class="home">
    <i class="fa-regular fa-comment-dots"></i>
    <h2>HOLA</h2>
    <p>"Esto es 4TUFORO"</p>
    <div id="informacion">
      
        <input type="text" placeholder="Usuario" v-model="usuario">
      

      
        <input type="text" placeholder="Contraseña" v-model="pass">
    </div>

    <button @click="validar" id="sesion">Iniciar Sesion</button>
    <button @click="registro" id="registrar">Crear Cuenta</button>
  </div>
</template>

<script>
import { usuarios } from '/usuarios.js';
export let idUsu = 0
console.log(usuarios);

export default {
  name: 'HomeView',
  data(){
    return{
      usuario: "",
      pass: "",
      Usuarios: usuarios
    }
  },
  methods: {
    validar(){
      console.log(this.Usuarios);
      const Userfound = this.Usuarios.find(usuario => usuario.usuario == this.usuario && usuario.pass == this.pass)
      if(Userfound){
        console.log('Usuario Encontrado');
        const perfilUsu = Userfound
        console.log(perfilUsu);
        this.$route.params.id= perfilUsu.id
        idUsu = perfilUsu.id
        this.$router.push({name: 'categorias'})
      }else{
        this.usuario= "",
        this.pass = ""
      }
    },
    registro(){
      this.$router.push({name: 'about'})
    }
  }
}
</script>

<style lang="sass">
*
  padding: 0
  margin: 0
  box-sizing: border-box

  #informacion
    height: 200px
    width: 80%
    display: flex
    flex-direction: column
    justify-content: space-evenly
    align-items: center
    margin-top: -60px


    input 
      padding: .6rem
      width: 80%
      text-align: center
      color: white
      border: none
      border-bottom: 3px solid  #C2C2C2
      outline: none


  .home
    display: flex
    flex-direction: column
    justify-content: space-around
    align-items: center
    height: 100vh
    width: 100%
    #registrar
      background-color: #813626
      color: white

    #sesion
      background-color: #26813A
      color: white

    i 
      font-size: 70px
      margin-bottom: -30px
      color: white

    h2 
      font-size: 40px
      color: white

    p 
      font-size: 18px
      color: gray
      font-style: italic
      margin-top: -64px

    button
      padding: .5rem  
      width: 150px
      margin-top: -40px

</style>  
