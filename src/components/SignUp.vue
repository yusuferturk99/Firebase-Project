<template>
    <div id="center">
        <input type="email" placeholder="Email" v-model="email">
        <br><br>
        <input type="password" placeholder="Password" v-model="password">
        <br><br>
        <button @click="SignUp">Sign Up</button>
        <p>Have an account? <router-link to="/signin">Sign In</router-link></p>
    </div>
</template>

<script>
import firebase from "firebase"

export default {
    name: "SignUp",
    data () {
        return {
            email: "",
            password: "",      
        }
    },
    methods: {
        SignUp () {
            firebase
            .auth()
            .createUserWithEmailAndPassword(this.email, this.password)
            .then(
            user => {
                alert("Your account has been created!");
                console.log(user.data);
            },
            err => {
                alert(err);
            });
        }
    }
}
</script>

<style scoped>
#center{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%)
}
</style>