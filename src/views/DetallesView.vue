<template>
  <div id="contenedor">
     <div id="iconos">
      <i class="fa-regular fa-comment-dots" @click="ir_categorias"></i>
        <i class="fa-solid fa-right-from-bracket" @click="regresar_inicio"></i>
    </div>
    <div id="imagen">
      <img :src="theme.imagen" alt="">
    </div>
  
    <div id="publicacion">
      <input type="text" v-model="mensage">
      <div id="boton">
        <button @click="comentario">Publicar</button>
      </div>
    </div>
   
     <section id="coments">
      <div v-for="coment in comentarios" :key="coment" class="comentario">
         <div id="usuario">
          <img :src="coment.imagen" alt="">
        </div>
        <div id="coment">
          <h3>{{coment.usuario}}</h3>
          <p>{{coment.comentario}}</p>
        </div>
        
    </div> 
    </section>
   
  </div>
</template>

<script>
import { idUsu } from './HomeView.vue'
console.log(idUsu);
import { temas } from '/temas.js'
import { usuarios } from '/usuarios.js'


export default {
  data(){
    return{
      tema: temas,
      theme: {},
      comentarios: "",
      user: usuarios,
      mensage: ""
    }
  },
  methods: {
    mostrar(){
      const temaID = this.$route.params.id
      const temaFound = this.tema.find(tema=> tema.id == temaID)
      this.theme = temaFound
      this.comentarios = this.theme.comentarios

    },
    comentario(){
      if(this.mensage != ""){
        const usuario = usuarios.find(u => u.id == idUsu)
        console.log(usuario);
        const coment = {
          imagen: usuario.imagen,
          usuario: usuario.nombre,
          comentario: this.mensage
        }
        console.log(coment);
        this.comentarios.push(coment)
        console.log(this.comentarios);
      }
    },
    ir_categorias(){
      this.$router.push({name: 'categorias' })
    },
    regresar_inicio(){
      this.$router.push({name: 'home'})
    }
  },
  mounted(){
    this.mostrar()

  }
}
</script>

<style scoped lang="sass">
*
  padding: 0
  margin: 0
  box-sizing: border-box

#contenedor
  height: 100vh
  width: 100% 
  display: flex
  flex-direction: column
  justify-content: space-between
  align-items: center
  #coments
    width: 100% 
    display: flex
    justify-content: center
    align-items: center
    flex-direction: column
    overflow: scroll
    padding: 1rem
    .comentario
      height: 100px
      width: 90%
      display: flex
      flex-direction: row
      padding: .3rem
      border-top: 3px solid brown
      

      #usuario
        width: 30%
        height: 100%
        display: flex
        justify-content: center
        align-items: center
        img 
          height: 80% 
          width: 80% 
          border-radius: 50%
          margin-right: 10px
      #coment
        height: 100%
        width: 70%
        display: flex
        flex-direction: column
        justify-content: center
        align-items: start
        border-left: 3px solid brown
        

        h3 
          font-size: 20px
          margin-left: 10px
          color: white

        p 
          font-size: 14px
          margin-left: 10px
          color: white
     
  #publicacion
    height: 200px
    width: 85%
    input
      width: 100% 
      height: 60%
      background-color: white
      outline: none
      border: none
    #boton
      height: 40%
      display: flex
      justify-content: end
      align-items: center
      button
        padding: .4rem
        background-color: white
        color: black
        font-weight: bold
  #iconos
    height: 10vh
    width: 100%
    display: flex
    flex-direction: row
    justify-content: space-around
    align-items: center
    margin-bottom: 20px
    i 
      font-size: 40px
      color: white
  #imagen
    border: 1px solid
    width: 65% 
    height: 200px
    margin-bottom: 20px
    img 
      height: 100% 
      width: 100% 
  

</style>