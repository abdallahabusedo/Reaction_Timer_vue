<template>
   <h2>Reaction time is {{score}} ms</h2>
</template>

<script>
export default {
    data(){
        return{
            score:null,
        }
    },
    props : [
        'score'
    ],
    methods : {
        mounted(){
            this.score= props.score
        }
    }
}
</script>