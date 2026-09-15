<script setup>
defineProps({
    nombre: {
        type: String,
        default: 'Alejandro Torres Villalobos'
    },
    matricula: {
        type: String,
        default: '1190585'
    },
    contacto: {
        type: String,
        default: "alejandro.torres.villalobos@uabc.edu.mx"
    }
})

const fecha = new Date().toLocaleDateString()
</script>

<template>
    <v-footer color="primary">
        <v-container>
            <v-row align-content="center" justify="space-between">
                <v-col cols="12" md="4" class="text-center text-md-left">
                    <span class="text-h6">{{ nombre }}</span>
                </v-col>
                <v-col cols="12" md="4" class="text-center text-md-left">
                    <span class="text-h6">{{ matricula }}</span>
                </v-col>
                <v-col cols="12" md="4" class="text-center text-md-left">
                    <span class="text-h6">{{ contacto }}</span>
                </v-col>
                <v-col cols="12" md="4" class="text-center text-md-left">
                    <span class="text-h6">{{ fecha }}</span>
                </v-col>
            </v-row>
        </v-container>
    </v-footer>
</template>