<template>

<p>Reaction-Time: {{ score }} ms</p>
<p class="rank">{{ rank }}</p>
</template>
<script>
export default{
    props:['score'],
    data(){
        return{
rank:null
        }
    },
    mounted(){
if(this.score<580){
    this.rank="Awesome, Rapidly Flexes!"
}
else if(this.score<1080){
    this.rank="You are doing well!"
}
else{
    this.rank="Good Job!"
}
    }
}
</script>

<style>
.rank{
    font-size: 1.5em;
    color:rgb(40, 50, 44);
    font-weight: bold;
}
</style>