<template>
    <div id="icons">
        <i class="fa-regular fa-comment-dots" @click="ir_perfil"></i>
        <i class="fa-solid fa-right-from-bracket" @click="regresar_inicio"></i>
    </div>

    <div id="imagenes" >
  
    <router-link v-for="imagen in tema" :key="imagen.id" :to="{ name: 'detalles', params: { id: imagen.id } }">
        <img :src="imagen.imagen" alt="">
    </router-link>
     
  </div>
</template>

<script>
import { idUsu } from './HomeView.vue'
import { temas } from '/temas.js'

export default {
    data(){
        return{
            tema: temas
        }
    },
    methods: {
        regresar_inicio(){
            this.$router.push({name: 'home'})
        },
        ir_perfil(){
            this.$router.push({name: 'perfil', params: {id: idUsu} })
        }
    }
}
</script>

<style lang="sass">
*
    padding: 0
    margin: 0
    box-sizing: border-box 

    #icons
        height: 10vh
        display: flex
        flex-direction: row
        justify-content: space-around 
        align-items: center
        i 
            font-size: 40px
            color: white
        
    #imagenes
        height: 85vh
        display: flex
        flex-direction: column
        justify-content: space-evenly
        align-items: center
        margin-top: 20px
        img 
            height: 200px
            width: 250px
            
    
</style>