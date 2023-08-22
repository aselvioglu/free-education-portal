<template>
 
 <img class= "logo" src="../assets/fep.jpg" />

<h1> Sign Up </h1>
<div>
<label> Name and Surname: </label>
<input class= "inputStyle" type="text" placeholder="Enter your fullname" />

<label> Email: </label>
<input class= "inputStyle" type="text" placeholder="Enter your email" />
<label> Password: </label>
<input class= "inputStyle" type="text" placeholder="Enter your password" />
<label for="usersType"> Select the user type </label>
<select class= "labelStyle" name="usersType" id="usersType">
  <option value="Apprentice">Apprentice</option>
  <option value="Assistant">Assistant</option>
  <option value="Master">Master</option>
  <option value="Potent">Potent</option>
</select>


</div>


</template>

<script>


export default {


    name: "SignUp"
}

</script>

<style> 

.logo { 
    width: 100px
    
}
.inputStyle {

width:300px;
heigth:80px;
padding-left: 20px;
display: block;
margin-bottom: 30px;
margin-right: auto;
margin-left: auto;
border: 1px solid skyblue;


}

.labelStyle{
width:320px;
heigth:80px;
padding-left: 20px;
display: block;
margin-bottom: 30px;
margin-right: auto;
margin-left: auto;
border: 1px solid skyblue;

}




</style>