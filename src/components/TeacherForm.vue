<template>
<section>
<h3>Añadir profesor</h3>
<div>
<div>
    <label for="nombre">Nombre</label>
<input type="text" v-model="teacher.teacherName">
</div>
<div>
    <label for="apellidos">apellidos</label>
<input type="text" v-model="teacher.surname">
</div>
<div>
    <label for="DNI">DNI</label>
<input type="text" v-model="teacher.dni">
</div>
<div>
    <label for="Materias">Materias</label>
<input type="text" v-model="subject">
<button @click="handleSubject()">Agregar</button>
</div>
<div>
    <ul>
    <li v-for="(elm, index) in teacher.subjects" :key="index">{{ elm }}</li>
    </ul>
</div>
<input type="checkbox" v-model="teacher.doc">Documentacion agregada
<button @click="handleAddTeacher()">Agregar</button>
</div>
</section>
<section>
    <h3>Lista de profesores</h3>
    <table>
    <tr>
        <th>Nombre</th>
        <th>Apellidos</th>
        <th>DNI</th>
        <th>Materias</th>
        <th>Documentacion</th>
    </tr>
    <tr v-for="elm in teachers" :key="elm.dni">
        <th>{{ elm.teacherName }}</th>
        <th>{{ elm.surname }}</th>
        <th>{{ elm.dni }}</th>
        <th>
            <ul>
            <li v-for="(item, index) in elm.subjects" :key="index">{{ item }}</li>
            </ul>
        </th>
        <th v-if="elm.doc">Entregado</th>
        <th v-else>No Entregado</th>
    </tr>
</table>
</section>
</template>

<script setup>
import {ref} from 'vue'

let teacher = ref({
teacherName: '',
surname: '',
dni: '',
subjects: [],
doc: false
})

let teachers = ref([])

let subject = ref('')

const handleSubject = () => {
teacher.value.subjects.push(subject.value)
subject.value = ''
}

const handleAddTeacher = () => {
teachers.value.push({
    teacherName: teacher.value.teacherName,
    surname: teacher.value.surname,
    dni: teacher.value.dni,
    subjects: teacher.value.subjects,
    doc: teacher.value.doc
})
teacher.value.teacherName = ''
teacher.value.surname = ''
teacher.value.dni = ''
teacher.value.subjects = ''
teacher.value.doc = ''
}
</script>

<style scoped>

</style>
