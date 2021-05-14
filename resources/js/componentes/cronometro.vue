<template>
    <div >
        <h1>{{saludo}}</h1>
        {{ minutos }} : {{ segundos }} : {{ decimas }}
        <button @click="parar_arrancar"> {{stop}} </button>
        valor de nombre {{nombre }}
    </div>
</template>

<script>
export default {
    name: "cronometro",
    props:['nombre'],
    data() {
        return {
            minutos: 0,
            segundos: 0,
            decimas: 0,
            saludo:"",
            stop :"Parar",
            funcionando: true,
        }
    },
    created() {
        console.log("Se ha creado el componente");
    },
    mounted() {
        console.log("Estoy montado");
        this.saludo="hola";
        setInterval( ()=> {
            if (this.funcionando==true) {
                this.decimas++;
                if (this.decimas == 10) {
                    this.segundos++;
                    this.decimas = 0;
                    if (this.segundos == 60) {
                        this.segundos = 0;
                        this.minutos++;
                        if (this.minutos == 60)
                            this.minutos = 0;
                    }
                }
            }
        }, 100);
    },
    methods:{
        parar_arrancar:function (){
            if (this.funcionando==true) {
                this.funcionando = false;
                this.stop="Arrancar";
            }else{
                this.funcionando = true;
                this.stop="Parar";
            }


        }
    }
}
</script>

<style scoped>

</style>
