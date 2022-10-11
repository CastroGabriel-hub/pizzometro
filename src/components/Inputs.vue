<template>
    <div class="inputs">
        <label>Quantidade de adultos</label>
        <input type="number" placeholder="Digite um valor aqui" v-model="adults"/>

        <label>Quantidade de crianças</label>
        <input type="number" placeholder="Digite um valor aqui" v-model="children"/>

        <button @click="calc(adults, children)">Enviar</button>
        <p>{{ message }}</p>
    </div>
</template>

<script>
    // Considere que uma pizza gigante possui 12 pedaços, uma pizza
    // família 10 e uma pizza convencional 8. Considere também que
    // um adulto come em média 3 pedaços e uma criança 2 pedaços.

    export default {
        name: 'Inputs',

        data() {
            return {
                adults : 0,
                children : 0,
                giant: 12,
                family: 10,
                standard: 8,
                message: '',
            }
        },

        methods : {
            calc(adults, children) {
                
                let slicesNeeded = (adults * 3) + (children * 2);

                let giantAmount = Math.round(slicesNeeded / this.giant);
                let familyAmount = Math.round((slicesNeeded % this.giant) / this.family);
                let standardAmount = Math.round(((slicesNeeded % this.giant) % this.family) / this.standard);

                this.message = `${standardAmount} pizzas tamanho convencional, ${familyAmount} do tamanho familia e ${giantAmount} pizzas do tamanho gigante.` ;
                
            }
        }
    }

</script>

<style>
    .inputs{
        width: 100vw;
        height: 250px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
    }

    .inputs input{
        width: 800px;
        height: 35px;
        padding: 5px;
        border: 2px solid #e6e6e6;
        border-radius: 12px;
    }

    .inputs button{
        width: 150px;
        height: 50px;
        background: #00FF7F;
        border: none;
        border-radius: 12px;
        color: #fff;
        font-size: 20px;
        font-weight: 600;
        cursor: pointer;
    }
</style>