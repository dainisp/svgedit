<template>
  <v-app>
    <v-main>
    <div class="image-container"  @mousedown="mouseDown"  @mousemove="mouseMove" ><svg viewBox="0 0 500 500"  ref="svgroot" width="500px" height="500px"  xmlns="http://www.w3.org/2000/svg">
  

  <!-- If you do not specify the stroke
       color the line will not be visible -->
</svg>
</div>  
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
    return :{
      currentStatus:0
    }
  }),
methods:{

mouseMove(event)
{
//console.log(event)
if(this.currentStatus ===1){
this.$refs.svgroot.childNodes[0].setAttribute('x2',event.clientX)
this.$refs.svgroot.childNodes[0].setAttribute('y2',event.clientY)
}
},

mouseDown(event){
  if(this.currentStatus ===1)
  {
this.$refs.svgroot.childNodes[0].setAttribute('x2',event.clientX)
this.$refs.svgroot.childNodes[0].setAttribute('y2',event.clientY)
this.currentStatus = 0
  }else
  {
let element = document.createElement('line')
element.setAttribute('x1',event.clientX)
element.setAttribute('x2',event.clientX)
element.setAttribute('y1',event.clientY)
element.setAttribute('y2',event.clientY)
element.setAttribute('stroke','black')
  this.currentStatus===1
  this.$refs.svgroot.appendChild(element)
  }
}


}


}
</script>
<style>

.image-container{
  width:500px;
  height: 500px;
  border-width: 5px;
}
</style>