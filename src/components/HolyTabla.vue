<script setup>
const habilidades = [
    { habilidad: 'Programación en C', nivel: 'Avanzado', anios: 3},
    { habilidad: 'Programación en Java', nivel: 'Intermedio', anios: 2},
    { habilidad: 'Programación en Arduino', nivel: 'Avanzado', anios: 2},
    { habilidad: 'Diseño en Multisim', nivel: 'Intermedio', anios: 2},
    { habilidad: 'Manejo de Git', nivel: 'Primario', anios: 3}
]
</script>

<template>
    <v-container>
        <h2 class ="text-h5 mb-4">Habilidades Técnicas</h2>

        <v-table class="elevation-1">
            <thead>
                <tr>
                    <th class="text-left">Habilidad</th>
                    <th class="text-left">Nivel de dominio</th>
                    <th class="text-left">Años de experiencia</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in habilidades" :key="item.habilidad">
                    <td>{{ item.habilidad }}</td>
                    <td>{{ item.nivel }}</td>
                    <td>{{ item.anios }}</td>
                </tr>
            </tbody>
        </v-table>
    </v-container>
</template>