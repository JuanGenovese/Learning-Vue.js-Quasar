<template>
  <div class="fullscreen bg-grey-10 text-white text-center q-pa-md flex flex-center">
    <div>
      <div style="font-size: 20vh">
        Página incorrecta...
      
      </div>

      <div class="text-h2" style="opacity:.7">
        click en el botón para ir al inicio:
      </div>

      <q-btn
        class="q-mt-xl"
        color="white"
        text-color="grey-10"
        unelevated
        to="/"
        label="Inicio"
        no-caps
      />
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ErrorNotFound'
})
</script>
