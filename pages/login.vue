<template>
  <v-app>
    <v-main>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title class="flex text-center">Login form</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <v-text-field v-model="email" :rules="emailRules" label="E-mail" required>
                  </v-text-field>
                  <v-text-field v-model="password" :counter="10" :rules="nameRules" label="password" required>
                  </v-text-field>

                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn block :disabled="!valid" color="success" class="mr-4" @click="validate">
                  Validate
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'login',
  data: () => ({
    valid: true,
    password: '',
    nameRules: [
      v => !!v || 'password is required',
      v => (v && v.length <= 10) || 'Name must be less than 10 characters',
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
    select: null,
    items: [
      'Item 1',
      'Item 2',
      'Item 3',
      'Item 4',
    ],
    checkbox: false,
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.$router.push('/')
      }

    },
    login() {
      if (this.email == 'admin@gmail.com' && this.password == '12345678') {
        this.$router.push('/')
      }

    }
  }

};
</script>

<style>
</style>
