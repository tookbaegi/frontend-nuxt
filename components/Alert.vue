<template>
    <div class="alert-box">
        <section class="alert-full">
            <div class="alert-message">
                <h1>{{ message }}</h1>
                <h3>{{ sub }}</h3>
            </div>
            <div class="alert-button">
                <a href="#" class="btn">알겠습니다</a>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    props: ['message', 'sub'],
    data() {
        return {
            message: this.message,
            sub: this.sub
        }
    }
}
</script>


<style lang="scss">
.alert-box {
    width: 90%;
    height: 45vh;
    background: #fff;
    position: fixed;
    top:50%;
    left:50%;
    transform: translate(-50%, -50%);

    display: flex;
    justify-content: center;
    align-items: center;

    box-shadow: 0px 0px 18px -2px rgba(87,87,87,0.66);
    .alert-message {
        text-align: center;
        h1 {
            color: rgb(138, 137, 137);
            font-size: 30px;
            letter-spacing: -1.5px;
            margin-bottom: 14px;
        }
        h3 {
            font-size: 15px;
            letter-spacing: -.75px;
            color: rgb(199,199,199);
        }
        margin-bottom: 40px;
    }
    .alert-button {
        text-align: center;
        padding: 20px 0;
        .btn {
            padding: 20px 90px;
            background: rgb(299, 299, 299);
            font-size: 20px;
            letter-spacing: -1px;
            width: 100%;
        }
    }
    .alert-full {
        display: block;
    }
}
</style>
