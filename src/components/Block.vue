<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        <b>CLICKEAME</b>
    </div>
</template>

<script>
    export default {
        props:['delay'],
        data(){
            return{
                showBlock: false,
                timer: null,
                reactionTime: 0
            }
        },
        mounted(){            
            setTimeout(() => {
                this.showBlock = true     
                this.startTimer()           
            }, this.delay)
        },
        methods:{
            startTimer(){
                this.timer = setInterval(() => {
                    this.reactionTime +=10
                }, +10)
            },
            stopTimer(){
                clearInterval(this.timer)
                this.$emit('end', this.reactionTime)
            }
        }
      /*  updated(){
            console.log('is updated')
        },
        unmounted(){
            console.log('is unmounted')
        }*/
    }
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: blue;
        color: #fff;
        text-align: center;
        padding: 100px 0;
        margin: 40px;
        align-self: center;
        margin-left: auto;
        margin-right: auto;
    }
</style>