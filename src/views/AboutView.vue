<template>
  <div>
    <i class="fa-regular fa-comment-dots"></i>
    <input type="text" placeholder="Nombre" v-model="nombre">
    <input type="text" placeholder="Apellidos" v-model="apellido">
    <input type="text" placeholder="Usuario" v-model="usuario">
    <input type="text" placeholder="Contraseña" v-model="pass">
    <input type="text" placeholder="URl imagen" v-model="imagen">
    <input type="text" placeholder="Descripcion" v-model="descripcion">

    <button  @click="detalles">Crear Cuenta</button>
    <button @click="inicio" id="volver">Volver</button>
  </div>
</template>

<script>
import { usuarios } from '/usuarios.js'

export default {
  name: 'RegistroView',
  data(){
    return{
      Usuarios: usuarios,
      nombre: "",
      apellido: "",
      descripcion: "",
      usuario: "",
      pass: "",
      imagen: ""
    }
  },
  methods: {
    detalles(){
      const objeto = {
        id: usuarios.length+1,
        usuario: this.usuario,
        pass: this.pass,
        nombre: this.nombre,
        apellido: this.apellido,
        descripcion: this.descripcion,
        imagen: this.imagen
    }
    
    usuarios.push(objeto)
    this.$router.push({name: 'home'})
    },
    inicio(){
      this.$router.push({name: 'home'})
    }
  }
}
</script>

<style lang="sass">
*
  padding: 0
  margin: 0
  box-sizing: border-box

  div 
    height: 90vh
    width: 100%
    display: flex
    flex-direction: column
    justify-content: space-around
    align-items: center

    i 
      font-size: 70px
      color: white
    button 
      background-color: #813626
      color: white
      padding: .4rem
      width: 130px
    #volver
      padding: .4rem
      width: 130px
      background-color: #26813A


    input
      padding: .4rem
      border: none
      outline: none
      border-bottom: 3px solid #C2C2C2
      text-align: center
      color: white
      width: 200px
</style>
