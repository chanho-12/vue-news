<template>
    <div>
        <user-profile :info="userInfo">
            <div slot='username'>{{ userInfo.id}}
            <span slot='time'>{{ 'Joined '+ userInfo.created }} , </span>
            <span slot="karma">{{ userInfo.karma}}</span>
            </div>
        </user-profile>
        <!-- <p>user : {{ userInfo.id }}</p>
        <p>karma : {{ userInfo.karma }}</p>
        <p>created : {{ userInfo.created }}</p> -->

    </div>
</template>

<script>
import UserProfile from '../components/UserProfile.vue'
//import axios from 'axios';
export default {

    components:{
        UserProfile,  
    },
    computed:{
        userInfo(){
            return this.$store.state.user;
        }
    },
    created(){
        console.log(this.$route.params.id);
        const userName = this.$route.params.id;
        //axios.get(`https://api.hmpwa.com/v0/user/${userName}.json`);
        this.$store.dispatch('FETCH_USER', userName);
    }
}
</script>

<style>

</style>