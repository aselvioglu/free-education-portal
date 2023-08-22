<template>
  <img class="logo" src="../assets/fep.jpg" />

  <h1> Sign Up </h1>
  <div>
    <label> name and surname </label>
    <input class="inputStyle" type="text" placeholder="Enter your fullname" />

    <label> email </label>
    <input class="inputStyle" type="text" placeholder="Enter your email" />

    <label> password </label>
     <button type="button" @click="switchVisibility1">show/hide</button>
<input class="inputStyle" :type="passwordFieldType" v-model="password" placeholder="Enter your password">
   
    <br>

    <label> confirm the password </label> 
    
    <button type="button" @click="switchVisibility2">show/hide</button>
    <input id="confirmedPassword" class="inputStyle" :type="confirmedPasswordFieldType" v-model="confirmedPassword" placeholder="Confirm your password" />
    <span v-if="passwordMatchError" class="error-message">{{ passwordMatchError }}</span>
     
<br>
<label for="usersType"> select the user type </label>
    <select class="labelStyle" name="usersType" id="usersType" v-model="userType" @change="userTypeChanged">
      <option value="Apprentice">Apprentice</option>
      <option value="Potent">Potent</option>
    </select>

    
    <div v-if="userType === 'Potent'" >
  <label>Invitation code for the user Potent</label>
  <input class="inputStyle" type="text" placeholder="Enter the invitation code" />
</div>

<button class="buttonStyle">Submit</button>

  </div>
</template>

<script>
export default {
  name: "SignUp",
  data() {
    return {
      password: "",
      confirmedPassword: "", 
      passwordVisible: false,
      confirmedPasswordVisible: false,
      userType:"Apprentice",
      passwordMatchError: ""
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

  },
};
</script>



<style> .logo {
   width: 100px
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
 }
</style>