<script setup>
import { reactive } from 'vue';

    const estado = reactive({
        numero1: 0,
        numero2: 0,
        operacao: '',
    })
    
    const alteraNumero1 = (evento) => {
        estado.numero1 = parseInt(evento.target.value);
    }
    
    const alteraNumero2 = (evento) => {
        estado.numero2 = parseInt(evento.target.value);
    }
    
    const calculoSoma = () => {
        const {numero1,numero2} = estado;
        return numero1 + numero2
    }
    const calculaSubtracao = () => {
        const {numero1,numero2} = estado;
        return numero1 - numero2
    }
    const calculaMultiplicacao = () => {
        const {numero1,numero2} = estado;
        return numero1 * numero2
    }
    const calculaDivisao = () => {
        const {numero1,numero2} = estado;
        return numero1 / numero2
    }


    const calculadora = () => {
        const {operacao} = estado;

        switch (operacao){
            case 'somar':
                return calculoSoma();
            case 'subtrair':
                return calculaSubtracao();
            case 'multiplicar':
                return calculaMultiplicacao();
            case 'dividir':
                return calculaDivisao()            
        }
    }

</script>

<template>
    <div class="campo-numerico  fs-1 fw-bold">
            {{ calculadora() }}
    </div>
    <form @submit.prevent="estado.operacao">
        <div class="row">
            <div class="col-md-6">
                    <input @keyup="alteraNumero1" class="campo-numerico fs-4" type="text"  placeholder="Digite um numero" required/>
            </div>
            <div class="col-md-6">
                <input @keyup="alteraNumero2" class="campo-numerico fs-4" type="text"  placeholder="Digite um numero" required />
            </div>
        </div>
        <div class="col-md-2">
            <select class="form-select form-select-sm mt-5" @change="evento => estado.operacao = evento.target.value">
                <option selected>Escolha uma Operação</option>
                <option value='somar'>+</option>
                <option value="subtrair">-</option>
                <option value="multiplicar">*</option>
                <option value="dividir">/</option> 
            </select>
        </div>

</form>
</template>
<style scoped>
.campo-numerico {
    width: 100%;
    padding: 1em 0.5em 0.1em 0.3em;
    margin-top: 5px;
    text-align: center;
}

input, select{
    border-color: #000;
}


</style>