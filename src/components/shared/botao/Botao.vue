<template>
    <button @click="disparaAcao()" :class="estiloDoBotao" :type="tipo">{{ rotulo }}</button>
</template>

<script>
export default {
    props: ['tipo', 'rotulo', 'confirmacao', 'estilo'],

    methods:{
        disparaAcao(){
            if(this.confirmacao){
                if(confirm("Apagar foto")){
                    this.$emit('botaoAtivado');
                }   
                return;
            }
            this.$emit('botaoAtivado');

            
        }
    },

    computed: {
        estiloDoBotao(){
            if(this.estilo == 'padrao'){
                return 'botao botao-padrao'
            }
            if(this.estilo == 'perigo'){
                return 'botao botao-perigo'
            }
        }
    }
}
</script>

<style>
    .botao {
        display: inline-block;
        padding: 10px;
        border-radius: 3px;
        margin: 10px;
        font-size: 1.2em;
    }

    .botao:hover{
        background-color: brown;
    }

    .botao:active{
        background-color: antiquewhite;
    }

    .botao-perigo {
        background: firebrick;
        color: white;
    }

    .botao-padrao {
        background: darkcyan;
        color: white;
    }

</style>