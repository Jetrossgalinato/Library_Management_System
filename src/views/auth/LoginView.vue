<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginForm from '@/components/auth/LoginForm.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-container fluid
        ><v-row>
          <v-col cols="12" md="3" class="mx-auto pt-16"
            ><v-card class="mx-auto" elevation="23">
              <v-card-title class="text-center">
                <v-img class="mx-auto pt-5" src="/images/logo.png" width="20%"></v-img>
                <h3 class="font-weight-bold">LIBRARY</h3>
         
                <p class="text-body-1"></p>
              </v-card-title>

              <v-card-text class="bg-surface-dark pt-4">
                <LoginForm></LoginForm>
                <v-divider class="my-5"></v-divider>

                <h5 class="text-center">
                  For Concerns and Inquiries kindly message on
                  <RouterLink class="text-deep-green-darken-1" to="/register"
                    >MasaoLMS Facebook Page</RouterLink
                  >
                </h5>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </template>
  </AppLayout>
</template>
