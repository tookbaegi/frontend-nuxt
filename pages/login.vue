<template>
    <div class="login">
        <div class="title">
            <div class="word">뚝배기</div>
            <div class="word">대신</div>
            <div class="word">퀘스트</div>
        </div>
        <div class="loginBtn">
            <a class="ggsign" @click="ggsign">Google 로 로그인</a>
            <a class="fbsign" href="#" @click="fbsign">Facebook 으로 로그인</a>
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

<style lang="scss" scoped>
  .title {
    margin-top: 89px;
    margin-left:auto;
    margin-right:auto;
    font-size:30px;
    font-weight: 500;
  }
  .word {
    font-size: 40px;
    font-weight:900;
    line-height: 55px;
    color: rgb(42, 42, 42);
  }
.login {
    width: calc(100% - 70px);
    margin-left:auto;
    margin-right: auto;
    .loginBtn {
        margin-top: 194px;
        a {
            color: white;
            display: block;
            background: rgb(229,229,229);
            font-size: 18px;
            text-align: center;
            border-radius: 5px;
            padding: 17px 0;
            letter-spacing: -.9px;
            
            text-decoration: none;
            margin-bottom: 10pt;
        }
        .ggsign {
           background-color: rgb(242, 61, 6);
        }
        .fbsign {
            background-color: rgb(61, 72, 154);
        }
    }
}

</style>
