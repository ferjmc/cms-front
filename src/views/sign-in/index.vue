<template>
    <v-container>
        <div v-show="loading">
            <circular-progress />
        </div>
        <div v-show="!loading">
            <v-form
                ref="form"
                v-model="valid"
                lazy-validation
            >
                <v-text-field
                v-model="signin.email"
                :rules="emailRules"
                label="E-mail"
                required
                ></v-text-field>

                <v-text-field
                v-model="signin.password"
                :counter="20"
                :rules="passwordRules"
                label="Password"
                required
                ></v-text-field>

                <v-btn
                :disabled="!valid"
                color="success"
                class="mr-4"
                @click="validate"
                >
                Sign In
                </v-btn>

                <v-btn
                color="error"
                class="mr-4"
                @click="reset"
                >
                Cancel
                </v-btn>

                <v-btn
                color="warning"
                @click="resetValidation"
                >
                Sign Up
                </v-btn>
            </v-form>
        </div>
    </v-container>
  
</template>

<script>
import { CircularProgress } from "../../components/circular-progress/CircularProgress"
export default ({
    name: "SignIn",
    components: {
        CircularProgress
    },
    data: () => ({
      valid: true,
      signinForm: {
          email: '',
          password: '',
      },
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 6) || 'Password must be at least 6 characters',
      ],
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      loading: false,
      redirect: undefined,
    }),
    methods: {
      validate () {
        this.$refs.form.validate()
      },
      reset () {
        this.$refs.form.reset()
      },
      resetValidation () {
        this.$refs.form.resetValidation()
      },
    },
})
</script>
