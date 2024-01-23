<template>
    <div id="icons">
        <i class="fa-regular fa-comment-dots" @click="ir_detalles"></i>
        <i class="fa-solid fa-right-from-bracket" @click="regresar_inicio"></i>
    </div>
  <div>
    <div id="perfil_image">
      <img :src="user.imagen" alt="">
    </div>
    <h2>{{user.nombre}}</h2>
    <h3>{{user.apellido}}</h3>
    <p>{{user.descripcion}}</p>

  </div>
</template>

<script>
import { usuarios } from '/usuarios.js';
import {idUsu} from '../views/HomeView.vue'

console.log(idUsu);

export default {
    data(){
      return {
        usuarios: usuarios,
        user: ""
      }
    },
    methods:{
      mostrar(){
        const user = usuarios.find(user => user.id === idUsu)
        this.user = user
      },
      regresar_inicio(){
            this.$router.push({name: 'home'})
        },
      ir_detalles(){
            this.$router.push({name: 'categorias'})
        }
    },
    mounted() {
      this.mostrar()
    }

    }

</script>

<style lang="sass">
*
  padding: 0
  margin: 0
  box-sizing: border-box
  #icons
    i 
     font-size: 40px
  div
    height: 100vh
    display: flex
    flex-direction: column
    justify-content: center
    align-items: center
    text-align: center

    h3 
      color: white
      margin-bottom: 15px

    h2 
      color: white 
      margin-bottom: 15px

    p 
      color: white
      width: 70%


    #perfil_image
      height: 30%
      width: 60%
      border-radius: 50%
      margin-bottom: 20px

      img
        height: 100% 
        width: 90%
        border-radius: 50%

    


      

</style>