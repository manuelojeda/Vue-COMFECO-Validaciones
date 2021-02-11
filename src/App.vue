<template>
  <form @submit.prevent="miSubmit">
    <p>
      Nombre
    </p>
    <input v-model="nombre" type="text" />

    <p>
      Nick
    </p>
    <input v-model="nick" type="text" />

    <div v-if="validaciones.nombre.$invalid">
      El campo <b>Nombre</b> es requerido
    </div>
    <div v-if="validaciones.nick.$invalid">
      El campo <b>Nick</b> es requerido
    </div>

    <button type="submit">
      Guardar
    </button>
  </form>
  <!-- <input type="email" v-model="miVariable" required>

  <div v-if="validaciones.miVariable.$silentErrors.length > 0">
    <div
      v-for="(error, index) in validaciones.miVariable.$silentErrors"
      :key="index"
    >
      {{ error.$message }}
    </div>
  </div> -->

  <!-- <p>
    {{ miVariable }}
  </p> -->
  <!-- <p>
    {{ error }}
  </p>
  <p>
    {{ mensajeError }}
  </p>
  <p>
    {{ errorNumero }}
  </p>
  <p>
    {{ mensajeErrorNumero }}
  </p> -->
</template>

<script>
import useVuelidate from '@vuelidate/core'
import { required, email } from '@vuelidate/validators'

export default {
  name: 'App',
  setup () {
    return { validaciones: useVuelidate() }
  },
  data () {
    return {
      nombre: null,
      nick: null,
      // miVariable: null,
      // mensajeError: null,
      // error: false,
      // mensajeErrorNumero: null,
      // errorNumero: false
    }
  },
  watch: {
    // miVariable (value) {
    //   const regex = new RegExp('^\\d+$')

    //   if (regex.test(value)) {
    //     this.mensajeErrorNumero = 'Este campo no acepta números'
    //     this.errorNumero = true
    //   } else {
    //     this.mensajeErrorNumero = null
    //     this.errorNumero = false
    //   }

    //   if (!value) {
    //     this.mensajeError = 'Este campo es requerido'
    //     this.error = true
    //   } else {
    //     this.mensajeError = null
    //     this.error = false
    //   }
    // }
  },
  validations () {
    return {
      // miVariable: {
      //   required,
      //   email,
      // },
      nombre: {
        required,
      },
      nick: {
        required,
      },
    }
  },
  methods: {
    miSubmit () {
      if (this.validaciones.$invalid) {
        alert('El formulario es error')
        return null
      }
      console.log('Estoy aquí')
    }
  }
}
</script>
