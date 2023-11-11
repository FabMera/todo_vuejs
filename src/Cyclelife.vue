<script>
export default {
    name: "Cyclelife",
    data() {
        return {
            saludo: "Hola desde el ciclo de vida",
        };
    },
    beforeCreate() {
        //Se ejecuta antes de crear la instancia del componente
        console.log("beforeCreate");
    },
    created() {
        //Se ejecuta al crear la instancia del componente
        console.log("created");
    },
    beforeMount() {
        //Se ejecuta antes de insertar el DOM
        console.log("beforeMount");
    },
    mounted() {
        //Se ejecuta al insertar el DOM
        console.log("mounted");
    },
    beforeUpdate() {
        //Se ejecuta al detectar un cambio
        console.log("beforeUpdate");
    },
    updated() {
        //Se ejecuta al actualizar el DOM y recibe los cambios
        console.log("updated");
    },
    beforeDestroy() {
        //Se ejecuta antes de destruir la instancia del componente
        console.log("beforeDestroy");
    },
    destroyed() {
        //Se ejecuta al destruir la instancia del componente
        console.log("destroyed");
    },
    methods: {},
    computed: {},
    components: {},
};
</script>
<template>
    <div></div>
</template>
