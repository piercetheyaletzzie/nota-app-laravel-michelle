<template>
    <app-layout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Crear Noticias
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                   <form @submit.prevent="enviar">

                        <label class="block font-medium text-sm text-gray-700">
                            Título
                        </label>

                        <textarea 
                            class="form-input w-full rounded-md shadow-sm"
                            v-model="form.titulo"
                            required
                        ></textarea>

                        <label class="block font-medium text-sm text-gray-700">
                            Categoria
                        </label>

                        <select 
                        class="form-input w-full rounded-md shadow-sm"
                        v-model="form.categoria"
                        required
                        > 
                            <option value="">Seleccionar</option>
                            <option value="Alta">Alta</option>
                            <option value="Media">Media</option>
                            <option value="Baja">Baja</option>
                        </select>

                        <label class="block font-medium text-sm text-gray-700">
                            Contenido
                        </label>

                        <textarea 
                            class="form-input w-full rounded-md shadow-sm"
                            v-model="form.contenido"
                            rows="8"
                            required
                        ></textarea>

                        <button 
                            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md"
                        >Crear</button>
                        
                    </form>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import { defineComponent } from 'vue'
    import AppLayout from '@/Layouts/AppLayout.vue'
    import Welcome from '@/Jetstream/Welcome.vue'

    export default defineComponent({
        components: {
            AppLayout,
            
        },
        data()
        {
            return{
                form: {
                    titulo: '',
                    contenido: '',
                    categoria: ''
                }
            }
        },
        methods: {
            enviar() {
                this.$inertia.post(this.route('nota.store'), this.form)
            }
        }
    })
</script>
