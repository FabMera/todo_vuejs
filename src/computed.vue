<script>
export default {
    data() {
        return {
            mensaje: "Hola desde computed",
            contador: 0,
        };
    },
    computed: {
        invertido() {
            return this.mensaje.split("").reverse().join("");
        },
        color() {
            return {
                "bg-success": this.contador <= 10,
                "bg-warning": this.contador > 10 && this.contador < 20,
                "bg-danger": this.contador >= 20,
            };
        },
    },
};
</script>

<template>
    <div class="container">
        <input
            class="form-control"
            type="text"
            v-model="mensaje"
            placeholder="Ingrese una palabra o frase "
        />
        <h3 class="m-3">Palabra invertida :{{ invertido }}</h3>

        <button class="btn btn-primary m-2" @click="contador++">+</button>
        <button class="btn btn-danger m-2" @click="contador--">-</button>
        <hr />
        <div
            class="progress"
            role="progressbar"
            aria-label="Example with label"
            aria-valuenow="25"
            aria-valuemin="0"
            aria-valuemax="100"
        >
            <div
                :class="color"
                class="progress-bar"
                :style="{ width: contador + '%' }"
            >
                {{ contador }}%
            </div>
        </div>
        <h3 class="mt-2">{{ contador }}</h3>
    </div>
</template>
