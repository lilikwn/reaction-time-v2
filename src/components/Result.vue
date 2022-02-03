<template>
<div class="result">
    <p>The reaction time is {{time}} ms</p>
    <h2>{{ result }}</h2>
</div>
</template>

<script>
export default {
    props : ["time"],
    data(){
        return({
            result:""
        })
    },
    mounted(){
        if(this.time < 200){
        this.result = "God Hand"
      }else if(this.time < 400){
        this.result = "Fast Hand"
      }else if(this.time < 600){
        this.result = "Normal Hand"
      }else{
        this.result = "Slow Hand"
      }
    }
}
</script>
<style>
    .result p{
        color: #212121;
    }
</style>