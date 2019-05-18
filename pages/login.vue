<template>
    <div class="login">
        <h1>뚝배기대신퀘스트</h1>
        <div class="loginBtn">
            <a href="#" style="margin-top: 260px;">구글로 연동하기</a>
            <a href="#">페이스북으로 연동하기</a>
        </div>
    </div>
</template>

<script>
export default {
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
