<template>
    <img class="logo" src="../assets/jep.png"/>

  <h1> Sign Up </h1>
  <div>
    <label for="nameSurname"> name and surname </label>
    <input id ="nameSurname" class="inputStyle" type="text" v-model="nameSurname" placeholder="Enter your fullname" />

    <label for ="email"> email </label>
    <input id="email" class="inputStyle" type="text" v-model="email" placeholder="Enter your email" />

    <label for ="password"> password </label>
    <button type="button" @click="switchVisibility1">show/hide</button>
    <input id="password" class="inputStyle" :type="passwordFieldType" v-model="password" placeholder="Enter your password">

    <br>

    <label for="confirmedPassword"> confirm the password </label>

    <button type="button" @click="switchVisibility2">show/hide</button>
    <input id="confirmedPassword" class="inputStyle" :type="confirmedPasswordFieldType" v-model="confirmedPassword"
      placeholder="Confirm your password" />
    <span v-if="passwordMatchError" class="error-message">{{ passwordMatchError }}</span>

    <br>
    <label for="usersType"> select the user type </label>
    <select class="labelStyle" name="usersType" id="usersType" v-model="userType" @change="userTypeChanged">
      <option value="Apprentice">Apprentice</option>
      <option value="Potent">Potent</option>
    </select>


    <div v-if="userType === 'Potent'">
      <label>Invitation code for the user Potent</label>
      <input class="inputStyle" type="text" v-model="invitationCode" placeholder="Enter the invitation code" />
    </div>

    <button class="buttonStyle" :disabled="!passwordsMatch" v-on:click="signUp">Sign Up</button>

  </div>
</template>

<script>
import axios from "axios"
export default {
  name: "SignUp",
  data() {
    return {
      nameSurname: "",
      email: "",
      password: "",
      confirmedPassword: "",
      passwordVisible: false,
      confirmedPasswordVisible: false,
      userType: "Apprentice",
      passwordMatchError: "",
      invitationCode: ""
    };
  },
  computed: {
    passwordsMatch() {
      return this.password === this.confirmedPassword;
    },
    passwordFieldType() {
      return this.passwordVisible ? "text" : "password";
    },
    confirmedPasswordFieldType() {
      return this.confirmedPasswordVisible ? "text" : "password";
    },
  },
  watch: {
    passwordsMatch(value) {
      if (!value) {
        this.passwordMatchError = "Passwords do not match.";
      } else {
        this.passwordMatchError = "";
      }
    }
  },

  methods: {
    switchVisibility1() {
      this.passwordVisible = !this.passwordVisible;
    },
    switchVisibility2() {
      this.confirmedPasswordVisible = !this.confirmedPasswordVisible;
    },
    userTypeChanged() {
      if (this.userType === "Potent") {
        // Perform actions when userType changes to "Potent"
      }


    },

    async signUp() {
  let result;

  const headers = {
    "Access-Control-Allow-Origin": "*",
    "Accept": "application/json",
    "Content-Type": "application/json",
  };

  const requestData = {
    nameSurname: this.nameSurname,
    email: this.email,
    password: this.password,
    confirmedPassword: this.confirmedPassword,
    userType: this.userType,
    invitationCode: this.invitationCode
  };

  try {
    result = await axios.post("http://localhost:5500/signup", requestData, { headers });
    console.warn(result);

    if (result.status === 201) {
      alert('You have successfully signed up!');
    } else {
      alert('Sign-up failed. Please check the console for details.');
    }
  } catch (error) {
    console.error('An error occurred:', error);
    alert('Sign-up failed. Please check the console for details.');
  }
},



  },
};
</script>



<style>
 .logo {
   height:224px;
 }

 .inputStyle {

   width: 300px;
   height: 40px;
   padding-left: 20px;
   display: block;
   margin-bottom: 30px;
   margin-right: auto;
   margin-left: auto;
   border: 1px solid skyblue;
   font-weight: 900;


 }

 .labelStyle {
   width: 320px;
   height: 40px;
   padding-left: 20px;
   display: block;
   margin-bottom: 30px;
   margin-right: auto;
   margin-left: auto;
   border: 1px solid skyblue;
   background-color: rgb(235, 233, 231);

 }

 .buttonStyle {
   width: 100px;
   height: 40px;
   padding-left: 10px;
   display: block;
   margin-bottom: 30px;
   margin-right: auto;
   margin-left: auto;
   border: 1px solid skyblue;
   cursor: pointer;
 }</style>