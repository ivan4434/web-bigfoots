<template>
  <div class="fixed w-[100%] h-[5rem] flex flex-row items-center duration-200 z-index-50" :class="{'bg-gray-200':scrollPosition > 100, 'bg-[rgba(0,0,0,0)]':scrollPosition <= 100}">
    <img alt="Vue logo" class="h-[100%]" src="./assets/logo.png">  
    <div class="font-bold text-[1.2rem]">Big Foots Simulator</div>
    <div class="absolute top-[50%] right-[1rem] translate-y-[-50%] flex flex-row justify-center">
      <a href="#download" class="mx-[1rem] font-medium hover:border-b border-black duration-100" :class="{'border-b-2 border-blue-400':false}">Descargar</a>
      <a href="#images" class="mx-[1rem] font-medium hover:border-b border-black duration-100" :class="{'border-b border-blue-400':false}">Imagenes</a>
      <a href="#form" class="mx-[1rem] font-medium hover:border-b border-black duration-100" :class="{'border-b border-blue-400':false}">Formulario</a>
    </div>
  </div>

  <div id="download" class="bg-orange-300 w-[100%] pt-[5rem] flex flex-row items-center">
    <img class="w-[50%]" src="https://lh4.googleusercontent.com/7NGiuwUO2K1TN3zmO1hKwZEP7mc2VWiVJWycJunpwCRsakqvI3o3RePY1487vPK0o1IJLy4SXpd54evLEpw7uNEMxYWga29dDjOsJdZkETFJgfNeJUgk-Bz5ZCzF4Uz_Fw=w992" alt="">
    <div class="w-[50%] flex flex-col items-center justify-center text-center">
      <div class="text-[3rem] font-bold">Big Foots Simulator</div>
      <div>Parrafo de descripcion del juego</div>
      <button @click="openTab('https://uvaes-my.sharepoint.com/:u:/g/personal/daniel_garcia22_estudiantes_uva_es/ERMgPE62p7REpJ4pmbrhzW8BjfWSk-0pA8t-BKXcpzYWpw?e=Ca4qwL')" class="bg-white px-[1rem] py-[.5rem] rounded-full font-medium mt-[.5rem] font-[1.3rem] hover:bg-transparent border-2 hover:border-blue-400 duration-200 hover:text-blue-400 active:text-blue-300 active:border-blue-300">Descargar</button>
    </div>
  </div>

  <div id="images" class="w-[100%] flex flex-col p-[3rem]">
    <div class="font-bold text-[3rem] w-[100%] border-b-2 py-[1rem]">Imágenes</div>
    <div class="flex flex-wrap w-[100%] mt-[1rem] items-center justify-center ">
      <img v-for="(img, index) in images" :src="img" :key="index" @click="currentImage = {active:true, img}" class="w-[30%] m-[.1rem] hover:opacity-[70%] duration-200 cursor-pointer active:opacity-[60%] z-index-0" alt="">
    </div>
  </div>

  <div id="form" class="w-[100%] flex flex-col p-[3rem]">
    <div class="font-bold text-[3rem] w-[100%] border-y-2 py-[1rem]">Formulario</div>
    <iframe class="h-[50rem] mt-[1rem]" src="https://docs.google.com/forms/d/e/1FAIpQLSfisAX8aEhTFmyJKn8mSj9YtngwL9iGlM2wy_WhDh03iBZTCA/viewform?usp=send_form" frameborder="0"></iframe>
  </div>

  <transition>
    <ImageView @close="currentImage = {active:false, img:''}" class = "fixed top-[50%] left-[50%] -translate-x-[50%] -translate-y-[50%]" v-if="currentImage.active" :src="currentImage.img"/>
  </transition>
</template>
<script>
import { ref } from 'vue'
import ImageView from './components/ImageView.vue'


export default {
  name: 'App',
  components: {
    ImageView
  },
  setup:()=>{

    const currentImage = ref({active:false, img:''})

    const images = ref([
      'https://lh4.googleusercontent.com/7NGiuwUO2K1TN3zmO1hKwZEP7mc2VWiVJWycJunpwCRsakqvI3o3RePY1487vPK0o1IJLy4SXpd54evLEpw7uNEMxYWga29dDjOsJdZkETFJgfNeJUgk-Bz5ZCzF4Uz_Fw=w992',
      'https://lh4.googleusercontent.com/7NGiuwUO2K1TN3zmO1hKwZEP7mc2VWiVJWycJunpwCRsakqvI3o3RePY1487vPK0o1IJLy4SXpd54evLEpw7uNEMxYWga29dDjOsJdZkETFJgfNeJUgk-Bz5ZCzF4Uz_Fw=w992',
      'https://lh4.googleusercontent.com/7NGiuwUO2K1TN3zmO1hKwZEP7mc2VWiVJWycJunpwCRsakqvI3o3RePY1487vPK0o1IJLy4SXpd54evLEpw7uNEMxYWga29dDjOsJdZkETFJgfNeJUgk-Bz5ZCzF4Uz_Fw=w992',
      'https://lh4.googleusercontent.com/7NGiuwUO2K1TN3zmO1hKwZEP7mc2VWiVJWycJunpwCRsakqvI3o3RePY1487vPK0o1IJLy4SXpd54evLEpw7uNEMxYWga29dDjOsJdZkETFJgfNeJUgk-Bz5ZCzF4Uz_Fw=w992',
      'https://lh4.googleusercontent.com/7NGiuwUO2K1TN3zmO1hKwZEP7mc2VWiVJWycJunpwCRsakqvI3o3RePY1487vPK0o1IJLy4SXpd54evLEpw7uNEMxYWga29dDjOsJdZkETFJgfNeJUgk-Bz5ZCzF4Uz_Fw=w992',
    ])

    const openTab = (url)=>{
      window.open(url, '_blank').focus()
    }
    
    return { openTab, images, currentImage }
  },  
  data() {
    return {
      windowWidth: window.innerWidth,
      scrollPosition: null
    }
  },

  mounted() {
    this.$nextTick(() => {
      window.addEventListener('resize', this.onResize);
    })

    window.addEventListener('scroll', this.updateScroll);
  },

  beforeUnmount() { 
    window.removeEventListener('resize', this.onResize); 
  },

  methods: {  
    onResize() {
      this.windowWidth = window.innerWidth
    },

    updateScroll() {
      this.scrollPosition = window.scrollY
    }
  }
}
</script>

<style>
  #app{
    font-family: Quicksand;
  }
  *:focus{
    outline: 0;
  }

  .v-enter-active,
  .v-leave-active {
    transition: opacity 0.5s ease;
  }

  .v-enter-from,
  .v-leave-to {
    opacity: 0;
  }
</style>
