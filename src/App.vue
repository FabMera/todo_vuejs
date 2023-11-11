<script>
import Cyclelife from './Cyclelife.vue';
import Computed from './computed.vue';

export default {
    name: "App",
    data() {
        return {
            titulo: "GYM VUE",
            tareas: [],
            nuevaTarea: "",
        };
    },
    created() {
        const datosDB = JSON.parse(localStorage.getItem("gym-vue"));
        if (datosDB) {
            this.tareas = datosDB;
        }
    },
    methods: {
        agregarTarea() {
            this.tareas.push({
                nombre: this.nuevaTarea,
                estado: false,
            });
            this.nuevaTarea = "";
            localStorage.setItem("gym-vue", JSON.stringify(this.tareas));
        },
        completarTarea(index) {
            this.tareas[index].estado = true;
            alert("Tarea completada");
            localStorage.setItem("gym-vue", JSON.stringify(this.tareas));
        },
        eliminarTarea(index) {
            this.tareas.splice(index, 1);
            localStorage.setItem("gym-vue", JSON.stringify(this.tareas));
        },
        manejadorEventos(index) {
            //Si el estado es true, elimina la tarea, si es false, la completa.
            if (this.tareas[index].estado) {
                this.eliminarTarea(index);
                alert("Tarea eliminada");
            }
            else {
                this.completarTarea(index);
            }
        },
    },
    components: { Computed, Cyclelife }
};
</script>

<template>
    <div class="container mt-5">
        <h3>{{ titulo }}</h3>
        <input
            v-model="nuevaTarea"
            type="text"
            class="form-control my-3"
            @keyup.enter="agregarTarea"
            placeholder="Agregar Tarea"
        />
        <button class="btn btn-primary" @click="agregarTarea">Agregar</button>

        <div v-if="tareas.length > 0">
            <div class="mt-3">
                <div
                    v-for="(tarea, index) in tareas"
                    class="alert d-flex justify-content-between"
                    role="alert"
                    :class="[tarea.estado ? 'alert-primary' : 'alert-danger']"
                >
                    {{ tarea.nombre }}
                    <button
                        @click="manejadorEventos(index)"
                        class="btn btn-success"
                        :class="[tarea.estado ? 'btn-danger' : 'btn-success']"
                    >
                        {{ tarea.estado ? "eliminar" : "completar" }}
                    </button>
                </div>
            </div>
        </div>
        <p  v-else class="alert alert-danger text-center w-50 mx-auto ">
            No hay Tareas!!
        </p>
    </div>
<hr>
    <Computed />
    <Cyclelife />
</template>
