<template>
  <div class="auth-wrapper auth-v1">
    <div class="auth-inner">
      <v-card class="auth-card">
        <!-- logo -->
        <v-card-title class="d-flex align-center justify-center py-7">
          <router-link to="/" class="d-flex align-center">
            <v-img :src="require('@/assets/images/logos/logo.svg')" max-height="30px" max-width="30px" alt="logo"
              contain class="me-3 "></v-img>

            <h2 class="text-2xl font-weight-semibold">
              Mapshot
            </h2>
          </router-link>
        </v-card-title>


        <!-- login form -->
        <v-card-text>
          <v-form @submit="hello">
            <v-text-field v-model="email" outlined label="Email" placeholder="john@example.com" hide-details
              class="mb-3"></v-text-field>

            <v-text-field v-model="password" outlined :type="isPasswordVisible ? 'text' : 'password'" label="Password"
              placeholder="············" :append-icon="isPasswordVisible ? icons.mdiEyeOffOutline : icons.mdiEyeOutline"
              hide-details @click:append="isPasswordVisible = !isPasswordVisible"></v-text-field>


            <v-btn block color="primary" class="mt-6" type="submit">
              Login
            </v-btn>
          </v-form>
        </v-card-text>

      </v-card>
    </div>

    <!-- background triangle shape  -->
    <img class="auth-mask-bg" height="173"
      :src="require(`@/assets/images/misc/mask-${$vuetify.theme.dark ? 'dark' : 'light'}.png`)">

    <!-- tree -->
    <v-img class="auth-tree" width="247" height="185" src="@/assets/images/misc/tree.png"></v-img>

    <!-- tree  -->
    <v-img class="auth-tree-3" width="377" height="289" src="@/assets/images/misc/tree-3.png"></v-img>
  </div>
</template>

<script>
// eslint-disable-next-line object-curly-newline
import { mdiFacebook, mdiTwitter, mdiGithub, mdiGoogle, mdiEyeOutline, mdiEyeOffOutline } from '@mdi/js'
import { ref } from '@vue/composition-api'

export default {
  setup() {
    const isPasswordVisible = ref(false)
    const email = ref('')
    const password = ref('')

    return {
      isPasswordVisible,
      email,
      password,

      icons: {
        mdiEyeOutline,
        mdiEyeOffOutline,
      },
    }
  },

  methods: {
    hello(e) {
      e.preventDefault();
      console.log("hello");
    }
  }
}
</script>

<style lang="scss">
@import '~@/plugins/vuetify/default-preset/preset/pages/auth.scss';
</style>
