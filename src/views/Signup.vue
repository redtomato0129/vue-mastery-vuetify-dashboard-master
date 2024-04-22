<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form ref="signUpForm" v-model="formValidity">
          <v-text-field
            label="Email"
            type="email"
            v-model="email"
            :rules="emailRules"
            required
          />
          <v-autocomplete label="Which browser do you use?" :items="browsers" />
          <v-file-input label="Attach profile picture" />
          <v-text-field label="Birthday" v-model="birthday" readonly />
          <v-date-picker v-model="birthday" />
          <v-checkbox
            label="Agree to terms and conditions"
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            required
          />
          <v-btn
            :disabled="!formValidity"
            class="mr-4"
            color="primary"
            type="submit"
            >Submit</v-btn
          >

          <v-btn class="mr-4" color="success" @click="validateForm"
            >Validate Form</v-btn
          >

          <v-btn class="mr-4" color="warning" @click="resetValidation"
            >Reset Validation</v-btn
          >
          <v-btn color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      browsers: ["Chrome", "Firefox", "Safari", "Edge"],
      birthday: "",
      agreeToTerms: false,
      agreeToTermsRules: [
        (value) => !!value || "You must agree to terms and conditions",
      ],
      email: "",
      emailRules: [
        (value) => !!value || "Email is required",
        (value) => value.indexOf("@") !== 0 || "Email should have a username",
        (value) => value.includes("@") || "Email should have an @ symbol",
        (value) =>
          value.indexOf(".") - value.indexOf("@") > 1 ||
          "Email should contain a valid domain",
        (value) =>
          value.indexOf(".") <= value.length - 3 ||
          "Email should contain a valid domain extension",
      ],
      formValidity: false,
    };
  },
  methods: {
    resetValidation() {
      this.$refs.signUpForm.resetValidation();
    },
    resetForm() {
      this.$refs.signUpForm.reset();
    },
    validateForm() {
      this.$refs.signUpForm.validate();
    },
  },
};
</script>

<style scoped></style>
