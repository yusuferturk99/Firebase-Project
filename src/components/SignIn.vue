<template>
    <div id="center">
        <input type="email" placeholder="Email" v-model="email">
        <br><br>
        <input type="password" placeholder="Password" v-model="password">
        <br><br>
        <button @click="signin">SignIn</button>
        <p>Need an account? <router-link to="/signup">Signup</router-link></p>
    </div>
</template>

<script>
import firebase from "firebase"

export default {
    name: "SignIn",
    data () {
        return {
            email: "",
            password: "",      
        }
    },
    methods: {
        signin () {
            firebase
            .auth()
            .signInWithEmailAndPassword(this.email, this.password)
            .then(
            user => {
                alert("Your have entered your account!");
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