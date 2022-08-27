<template>
    <p>Tiempo de reaccion: {{puntuacion}}ms</p>
    <p class="rank">{{rank}}</p>
</template>

<script>
    export default {
        props: ['puntuacion'],
        data(){
            return{
                rank: null
            }
        },
        mounted(){
            if(this.puntuacion < 250) {
                this.rank = 'Eres un MazzPro!'
            }
            else if(this.puntuacion < 400){
                this.rank = 'Bien, pero puedes mejorar'
            }else{
                this.rank = 'Mi abuelita podria hacerlo mas rapido XD'
            }

        }
    }
</script>

<style scoped>
.rank{
    font-size: 1.4em;
    color: rgb(0, 0, 177);
    font-weight: bold;
}

</style>