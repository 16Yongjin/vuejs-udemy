<template>
<div>
    <h1> Success </h1>
    <a href="/user_info">Go to user information </a>
    <button @click="logOut"> LogOut </button>

    <p>{{ name }}</p>
    <img :src="photo">
</div>
</template>

<script>
import firebase from 'firebase'
export default {
    data() {
        return {
            name: '',
            photo: '',
            user: {}
        }
    },
    created() {
        this.user = firebase.auth().currentUser;
        console.log(this.user);
        if (this.user) {
            this.name = this.user.displayName;
            this.photo = this.user.photoURL;
        }
    },
    methods: {
        logOut() {
            firebase.auth().signOut();
        }
    }
}
</script>

<style scoped>

</style>