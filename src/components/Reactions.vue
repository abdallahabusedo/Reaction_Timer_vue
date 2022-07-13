<template>
    <div v-if="showBtn">
        <button @click="stopTimer" class="btnc">Catch me</button>
    </div>
</template>

<script>
export default {
    data(){
        return {
            showBtn : false,
            timer: null,
            reactiontimer: 0,
        }
    },
    props : [
        'delay'
    ],
    methods:{
        startTimer(){
            this.timer= setInterval(() => {
                this.reactiontimer += 10
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end',this.reactiontimer)
            this.showBtn = false
            console.log("this is the reaction timer "+ this.reactiontimer.toString());
        }
    },
    mounted(){
        setTimeout(() => {
        this.showBtn = true 
        this.startTimer()
        }
        ,this.delay);
    }
}
</script>

<style scoped>
   
    .btnc{
        width: 50%;
        height: 150px;
        background: rgb(93, 172, 93);
        border: 1px crimson;
        border-radius: 15px;
        color : white;
        font-size: 50px;
        margin: 10px;  
        text-align: center;
        line-height: 16px;
        cursor: pointer;
        transition: all 0.3s ease;
        
    }
</style>