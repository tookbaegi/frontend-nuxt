<template>
    <div class="login">
        <h1>뚝배기대신퀘스트</h1>
        <div class="loginBtn">
            <a href="#" style="margin-top: 260px;" @click="ggsign">구글로 연동하기</a>
            <a href="#" @click="fbsign">페이스북으로 연동하기</a>
        </div>
    </div>
</template>

<script>
import firebase from 'firebase'
import axios from 'axios'
var provider
var vm = this

export default {
    created () {
    var config = {
    apiKey: "AIzaSyCwil_eOFCyLdrZ2BBX_3uzK3h5pzmWKgY",
    authDomain: "ttukbaegi-bd2a7.firebaseapp.com",
    databaseURL: "https://ttukbaegi-bd2a7.firebaseio.com",
    projectId: "ttukbaegi-bd2a7",
    storageBucket: "ttukbaegi-bd2a7.appspot.com",
    messagingSenderId: "1092540131180",
    appId: "1:1092540131180:web:26de1ac2d13dd805"  
    }

        firebase.initializeApp(config)        

        // provider = new firebase.auth.FacebookAuthProvider();
    },
    methods: {
        fbsign () {
             provider = new firebase.auth.FacebookAuthProvider();
            this.auth()
        },
        ggsign () {
            provider = new firebase.auth.GoogleAuthProvider();
            this.auth()
        },
        auth () {
            firebase.auth().signInWithPopup(provider)
            .then(function(result) {
                let data = result.additionalUserInfo
                console.log('result', result)
                let body = {
                    name: data.profile.name,
                    email: data.profile.email,
                    type: data.providerId,
                    token: result.user.uid                    
                }
            axios.post('https://ttukbaegi.herokuapp.com/api/users', body)
            .then((response) => {
                    console.log('회원가입', response)
                    window.localStorage.setItem('user', JSON.stringify(response.data.user))
                    if(response.data.new){
                        window.$nuxt.$router.push({'path': 'main'})
                    }
                    else{
                        window.$nuxt.$router.push({'name': 'main'})
                    }
                })
            })
            .catch(function(error) {
                console.log(error)
            });
        }
    }
}
</script>

<style lang="scss">
.login {
    padding: 37px;
    h1 {
        font-size: 30px;
        text-align: center;
        letter-spacing: -1.5px;
        margin-top: 130px;
    }
    .loginBtn {
        a {
            color: #000;
            display: block;
            background: rgb(229,229,229);
            font-size: 18px;
            text-align: center;
            border-radius: 5px;
            padding: 23px 0;
            letter-spacing: -.9px;
            
            text-decoration: none;
            margin-bottom: 10pt;
        }
    }
}
</style>
