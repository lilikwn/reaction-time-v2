<template>
  <div v-if="showBlock" @click="stopTimer" class="block">
      <p>Click Me</p>
  </div>
</template>

<script>
export default {
    props : ['delay'],
    data(){
        return({
            showBlock : false,
            reactionTime : 0,
        })
    },
    methods : {
        startTimer(){
            setInterval(()=>{
                this.reactionTime += 10;
            }, 10)
        },
        stopTimer(){
            clearInterval();
            this.$emit('end', this.reactionTime);
            this.showBlock = false;
        }
    },
    mounted(){
        setTimeout(()=>{
            this.startTimer();
            this.showBlock = true;
        }, this.delay)
    }
}
</script>

<style>
    .block{
        color: #E8EAF6;
        margin: 30px auto;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid;
        width: 400px;
        height: 150px;
        border-radius: 20px;
        background-color: #3F51B5;
    }
</style>