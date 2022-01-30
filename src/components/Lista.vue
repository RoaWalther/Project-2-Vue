<template>
<div>
    <ul class="list-group">
    <li v-for="(fruta,index) of arrayOrder" :key='fruta'
    class="list-group-item d-flex justify-content-between align-items-center">
        {{fruta.nombre}}
        <span class="badge bg-primary rounded-pill"  @click="aumentar(index)">{{fruta.cantidad}}</span>
        
    </li>
    </ul>
    <button class="btn bg-danger btn-block mt-5" @click="reiniciar">Reiniciar</button>
</div>
    
</template>

<script>
import {mapState,mapMutations} from 'vuex';
export default {
    name: 'Lista',
    computed:{
        ...mapState(['frutas']),
        arrayOrder(){
            return this.frutas.sort((a,b)=> b.cantidad-a.cantidad) //ordena de mayor a menor
        }
    },
    methods:{
        ...mapMutations(['aumentar', 'reiniciar'])
    }
}
</script>
