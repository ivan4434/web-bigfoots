<template>
  <div class="w-[100%] h-[100%] bg-[rgba(255,255,255,.7)] p-[3rem] flex flex-col items-center justify-center">
    <button @click="close" class="text-[2rem] absolute top-[1rem] right-[1rem] hover:opacity-[70%] active:opacity-[60%] duration-200"><i class="fa-regular fa-xmark"></i></button>
    <img :src="src" class="w-[70%]">
  </div>
</template>

<script>
export default {
  name: 'ImageView',
  props: {
    src:String
  },
  setup: (props, context)=>{
    const close = ()=>{
      context.emit("close")
    }

    return { close }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
