<template>
  <v-row justify="end">
    <v-col cols="12" sm="10" md="8" lg="6">
      <v-card class="mx-auto mt-12" style="max-width: 500px;">
        <v-card-title class="headline">Sign In</v-card-title>
        <v-form ref="form" v-model="valid" :lazy-validation="lazy">
          <v-text-field
            v-model="username"
            :counter="10"
            :rules="nameRules"
            label="UserName"
            required
            outlined
            class="pt-5 pl-6 pr-6"
          ></v-text-field>
          <v-text-field
            v-model="password"
            label="Password"
            required
            outlined
            class="pt-5 pl-6 pr-6"
          ></v-text-field>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              :disabled="!valid"
              color="success"
              class="mr-4"
              @click="validate"
            >
              Sign In
            </v-btn>
          </v-card-actions>
        </v-form>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'signin',
  data: () => ({
    valid: true,
    username: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => (v && v.length <= 10) || 'Username must be less than 10 characters'
    ],
    password: '',
    lazy: false
  }),
  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        alert(this.username)
        this.username = ''
        this.email = ''
        this.password = ''
      }
    }
  }
}
</script>
