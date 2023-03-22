<template>
<div class="block" v-if="showBlock" @click="stopTimer">
    Click Me!
</div>
</template>

<script>
export default{
props:['delay'],
data(){
    return{
      showBlock:false,
      timer:null,
      reactionTime:0
    }
},
mounted(){
    console.log("mounted")
    setTimeout(() => {
        this.showBlock=true
        this.startTimer()
    },this.delay);
},
methods:{
    startTimer(){
        this.timer=setInterval(() => {
            this.reactionTime+=10
        }, 10);

    },
    stopTimer(){
     clearInterval(this.timer)
     console.log(this.reactionTime)
     this.$emit('end',this.reactionTime)
    }
}
// updated(){
//     console.log("component updated!")
// },
// unmounted(){
//     console.log("component unMounted!")
// }
}
</script>

<style>

.block{
    width:350px;
    padding:100px 0;
    background: #e57373;
    text-align: center;
    color:snow;
    border-radius: 20px;
    margin: 40px auto;
}
</style>