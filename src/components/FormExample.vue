<template>
    <form mx-2>
      <v-text-field
        v-model="state.name"
        :error-messages="v$.name.$errors.map(e => e.$message)"
        :counter="10"
        label="Name"
        required
        @input="v$.name.$touch"
        @blur="v$.name.$touch"
      ></v-text-field>
  
      <v-text-field
        v-model="state.email"
        :error-messages="v$.email.$errors.map(e => e.$message)"
        label="E-mail"
        required
        @input="v$.email.$touch"
        @blur="v$.email.$touch"
      ></v-text-field>
  
      <v-select
        v-model="state.select"
        :items="items"
        :error-messages="v$.select.$errors.map(e => e.$message)"
        label="Item"
        required
        @change="v$.select.$touch"
        @blur="v$.select.$touch"
      ></v-select>
  
      <v-checkbox
        v-model="state.checkbox"
        :error-messages="v$.checkbox.$errors.map(e => e.$message)"
        label="Do you agree?"
        required
        @change="v$.checkbox.$touch"
        @blur="v$.checkbox.$touch"
      ></v-checkbox>
  
      <v-btn
        class="me-4"
        @click="v$.$validate"
        color="secondary"
      >
        submit
      </v-btn>
      <v-btn @click="clear">
        clear
      </v-btn>
    </form>
  </template>
  <script lang="ts">
  
  import { reactive, ref } from 'vue'
  import { useVuelidate } from '@vuelidate/core'
  import { email, required } from '@vuelidate/validators'

  interface FormState {
    name:any,
    email:any,
    select:any,
    checkbox:any,
    items?:any
  }

  export default {
    setup () {
      const initialState:FormState = {
        name: '',
        email: '',
        select: null,
        checkbox: null,
        
      }

      const state:FormState = reactive({
        ...initialState,
      })

      const items = ref([
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
      ])

      const rules:FormState = {
        name: { required },
        email: { required, email },
        select: { required },
        items: { required },
        checkbox: {  },
      }

      const v$ = useVuelidate(rules, {...state})

      function clear () {
        v$.value.$reset()

        for (const [key, value] of Object.entries(initialState)) {
          state[key as keyof FormState] = value
        }
        
      }

      return { state, items, clear, v$ }
    },
  }
</script>