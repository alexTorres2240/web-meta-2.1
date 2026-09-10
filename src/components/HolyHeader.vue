<script setup>
defineProps({
    logo: {
        type: String,
        default: 'https://picsum.photos/id/1025/100/100'
    },
    titulo: {
        type: String,
        default: 'HolyPortafolio'
    }
})</script>

<template>
    <v-app-bar color="primary" elevation="2">
        <v-avatar class="ml-3" size="40">
            <v-img :src="logo" alt="Logo" cover></v-img>
        </v-avatar>
    </v-app-bar>
    
    <v-app-bar class="ml-2">
        {{ titulo }}
    </v-app-bar>

    <v-spacer></v-spacer>
</template>