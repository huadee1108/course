<template>
    <div class="container">
        <h4 class="login_text">登录</h4>
        <div class="form-group">
            <input type="text" class="form-control" id="username" placeholder="请输入用户名/学员编号">
            <img src="../assets/username.png">
        </div>
        <div class="form-group">
            <input type="password" class="form-control" id="password" placeholder="请输入密码">
            <img src="../assets/password.png">
            <p v-show="status" class="tips">{{errorMessage}}</p>
        </div>
        <button @click="goIndex" type="button" class="btn btn-success btn-block">登录</button>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data(){
            return{
                status: false,
                loginMessage:{
                    username: '',
                    password: ''
                },
                errorMessage: '',
                photoImg: require( '@/assets/log.png')
            }
        },
        methods:{
            goIndex: function () {
                this.$axios.get('http://jsonplaceholder.typicode.com/posts')//http://192.168.23.10/login/token.php?
                    .then((response) => {
                        console.log(response);
                        /*this.photoImg = response.img;*/
                        localStorage.setItem('photoImg',this.photoImg);
                        this.$router.push({path:'index'});
                    })
                    .catch((error) => {
                        console.log(error);
                        this.status = true;
                        this.errorMessage = "dd";/*error*/
                    })
            }
        }
    }
</script>

<style scoped>
.login_text{
    text-align: center;
    margin-top: 12px;
}
.form-group{
    position: relative;
}
.form-group img{
    position: absolute;
    left: 5px;
    top: 10px;
}
.form-group input{
    text-indent: 1em;
}
.tips{
    color: red;
}
</style>
