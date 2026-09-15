<script setup lang="ts">
import { ref, onMounted } from 'vue'
import HolyCard from './components/HolyCard.vue'
import HolyHeader from './components/HolyHeader.vue'
import HolyFooter from './components/HolyFooter.vue'
import HolyTabla from './components/HolyTabla.vue'

onMounted(()=>{
  actualizarImagenes() 
})

const foto1 = ref({
  imagen: '',
  titulo: 'Imágen 1',
  descripcion: 'Fotografía obtenida mediante la API de Picsum.',
  autor: 'Lorem Picsum'
})

const foto2 = ref({
  imagen: '',
  titulo: 'Imágen 2',
  descripcion: 'Fotografía obtenida mediante la API de Picsum.',
  autor: 'Lorem Picsum'
})

const cargando = ref(false)
const mensajeError = ref('')

async function actualizarImagenes() {
  cargando.value = true
  mensajeError.value = ''

  try {
    const paginaAleatoria = Math.floor(Math.random() * 20) + 1
    const respuesta = await fetch(
      `https://picsum.photos/v2/list?pages=${paginaAleatoria}&limit=30`
    )

    if (!respuesta.ok) {
      throw new Error('No de pudo conectar con la API de Picsum')
    }

    const datos = await respuesta.json()

    if (!datos || datos.length < 2) {
      throw new Error('La API no devolvió suficientes imágenes.')
    }

    const indice1 = Math.floor(Math.random() * datos.length)
    let indice2 = Math.floor(Math.random() * datos.length)
    while (indice2 === indice1) {
      indice2 = Math.floor(Math.random() * datos.length)
    }

    const item1 = datos[indice1]
    const item2 = datos[indice2]

    foto1.value = {
      imagen: `https://picsum.photos/id/${item1.id}/400/250`,
      titulo: 'Imágen 1',
      descripcion: 'Fotografía obtenida mediante la API de Picsum.',
      autor: item1.author
    }

    foto2.value = {
      imagen: `https://picsum.photos/id/${item2.id}/400/250`,
      titulo: 'Imágen 2',
      descripcion: 'Fotografía obtenida mediante la API de Picsum',
      autor: item2.author
    }
  } catch (error) {
    mensajeError.value =
      error instanceof Error
      ? error.message
      : 'Ocurrió un error al obtener las imágenes'
  } finally {
    cargando.value = false
  }
}
</script>

<template>
  <v-app>
    <v-main>
      <HolyHeader titulo="HolyPortafolio"/>
      <v-container>
        <v-row>
          <v-col cols="12" md="6">
            <HolyCard
              :imagen="foto1.imagen"
              :titulo="foto1.titulo"
              :descripcion="foto1.descripcion"
              :autor="foto1.autor"
              :cargando="cargando"
            />
          </v-col>
          <v-col cols="12" md="6">
            <HolyCard
              :imagen="foto2.imagen"
              :titulo="foto2.titulo"
              :descripcion="foto2.descripcion"
              :autor="foto2.autor"
              :cargando="cargando"
            />
          </v-col>
        </v-row>
        <v-row justify="center" class="my-4">
          <v-col cols="12" class="text-center">
            <v-btn color="primary" :loading="cargando" :disabled="cargando" @click="actualizarImagenes">
              Actualizar imágenes
            </v-btn>
          </v-col>
        </v-row>
        <HolyTabla/>
        <HolyFooter/>
      </v-container>
    </v-main>
  </v-app>
</template>