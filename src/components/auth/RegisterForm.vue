<script setup>
import {
  requiredValidator,
  emailValidator,
  passwordValidator,
  confirmedValidator
} from '@/utils/validators'
import { ref } from 'vue'

const visible = ref(false)
const confirmvisible = ref(false)
const refVForm = ref()

const formDataDefault = {
  firstname: '',
  lastname: '',
  email: '',
  password: '',
  confirm_password: ''
}
const formData = ref({
  ...formDataDefault
})
const onSubmit = () => {
  alert(formData.value.email)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onSubmit()
  })
}
</script>
<template>
  <v-form ref="refVForm" @submit.prevent>
    <v-row>
      <v-col cols="12" md="6">
        <v-text-field
          v-model="formData.firstname"
          label="Firstname"
          variant="outlined"
          :rules="[requiredValidator]"
        ></v-text-field>
      </v-col>
      <v-col cols="12" md="6">
        <v-text-field
          v-model="formData.lastname"
          label="Lastname"
          variant="outlined"
          :rules="[requiredValidator]"
        ></v-text-field>
      </v-col>
      <v-col cols="12">
        <v-text-field
          v-model="formData.email"
          label="E-mail"
          prepend-inner-icon="mdi-email"
          variant="outlined"
          :rules="[requiredValidator, emailValidator]"
        ></v-text-field>
      </v-col>
      <v-col cols="12">
        <v-text-field
          v-model="formData.password"
          label="Password"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
          :rules="[requiredValidator, passwordValidator]"
        ></v-text-field>
      </v-col>
      <v-col cols="12">
        <v-text-field
          v-model="formData.confirm_password"
          label="Confirm Password"
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          prepend-inner-icon="mdi-lock-check"
          variant="outlined"
          @click:append-inner="confirmvisible = !confirmvisible"
          :rules="[
            requiredValidator,
            confirmedValidator(formData.password, formData.confirm_password)
          ]"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-btn class="mt-2" type="submit" block color="#F7971D" prepend-icon="mdi-account-plus">
      Register
    </v-btn>
  </v-form>
</template>
