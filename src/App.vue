<template>
  <v-app>
    <v-main>
<v-row>
<v-col>
<div class="image-container"  @mouseup="mouseDown"  @mousemove="mouseMove" ><svg viewBox="0 0 500 500"  ref="svgroot" width="500px" height="500px"  xmlns="http://www.w3.org/2000/svg">
  

  <!-- If you do not specify the stroke
       color the line will not be visible -->
</svg>
</div> 
</v-col>
<v-col>
  <v-icon @click="insertLine" class="object-button" >mdi-edit</v-icon>
<div>{{dataString}}</div>  
</v-col>
</v-row> 
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
    return :{
      currentStatus:0,
      dataString:'',
    }
  }),
methods:{
insertLine()
{
console.log("mouse insert")
this.dataString = "koords x1:"  + this.$refs.svgroot.lastElementChild.attributes.x1
                   +  " x2:" + this.$refs.svgroot.lastElementChild.attributes.x2
                   " y1:" + this.$refs.svgroot.lastElementChild.attributes.y1
                   " y2:" + this.$refs.svgroot.lastElementChild.attributes.y2
},

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
  border-style:solid;
}
.object-button{
 border-width: 5px;
  border-style:solid;
}


</style>