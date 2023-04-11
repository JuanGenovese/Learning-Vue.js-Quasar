<template>
  <q-page padding>


    <h4 class="text-center text-weight-bolder">Lista</h4>


    <q-form 
      class="row q-col-gutter-md"
      @submit.prevent="procesarFormulario"
      @reset="reset"
      ref="myForm"
    >

      <div class="col-12 col-sm-6">

        <q-input
          label="Producto"
          v-model="producto"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Por favor, escribe algo para continuar']"
          
        />

      </div>


      <div class="col-12 col-sm-6">

        <q-select
          label="Prioridad"
          v-model="seleccion"
          :options="opciones"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Por favor, selecciones un tipo de prioridad para continuar']"
          
        />        
      </div>


      <div class="col-12">
        <q-toggle
          v-model="terminos"
          label="Aceptar los terminos"

        />
      </div>

      
      <div class="col-12">

        <q-btn
          label="submit"
          color="primary"
          type="submit"
        />

        <q-btn
          label="reset"
          v-model="reset"
          color="primary"
          outline
          class="q-ml-sm"
          :ripple="false"
          type="reset"
        />

      </div>

    </q-form>

    <pintar-datos 
      :productos="productos"
    />
    
  </q-page>
</template>



<script>
import {ref} from "vue"
import { useQuasar} from "quasar"
import pintarDatos from "src/components/pintarDatos.vue"
export default {
  components: {pintarDatos},
  setup() {
    const $q = useQuasar()
    const myForm = ref(null)
    const producto = ref(null)
    const seleccion = ref(null)
    const terminos = ref(false)
    const opciones = ["Máxima", "Moderada", "Mínima"]


    const productos = ref([])



    const procesarFormulario = () => {
      console.log("submit funciona correctamente")
      if(terminos.value === false) {
        $q.notify({
          color: "red-5",
          textColor: "white",
          icon: "warning",
          message: "Si usted no está de acuerdo con los terminos, será imposible continuar"
        })
      }
      else {
        $q.notify({
          color: "green-4",
          textColor: "white",
          icon: "cloud_done",
          message: "El producto de guardo correctamente"
        })
      }
      myForm.value.resetValidation()

      productos.value = [...productos.value, {
        producto: producto.value,
        prioridad: seleccion.value
      }]

      reset()
    }



    const reset = () => {
      producto.value = null
      terminos.value = null
      seleccion.value= null
    }



    return {
      producto,
      seleccion,
      terminos,
      opciones,
      procesarFormulario,
      reset,
      myForm,
      productos
    }
  },
}
</script>