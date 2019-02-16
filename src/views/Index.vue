<template>
    <div class="all">
        <div class="log">
            <img class="log_left" src="../assets/log.png">
            <img class="log_right" :src="photoImg">
        </div>
        <hr>
        <div class="course_list">
            <img class="course_img" src="../assets/jj.jpg"><!--categoryimgurl-->
            <div class="num">
                100人报名  <!--allenrollnum-->
            </div>
            <h4>步步高教育</h4><!--name-->
            <h5>步步高升</h5><!--summary-->
        </div>
    </div>
</template>

<script>
    export default {
        name: "Index",
        data(){
            return{
                photoImg: '',
                courseList: []
            }
        },
        created:function () {
            this.photoImg = localStorage.getItem('photoImg');
            console.log(this.photoImg);
            this.$axios.post('http://jsonplaceholder.typicode.com/posts')//http://192.168.23.10/product/webserver.php?wsfunction=get_categori
                .then((response) => {
                    console.log(response);
                    /*this.courseList.push(response.categories[7]);*/
                })
                .catch((error) => {
                    console.log(error);
                })
        }
    }
</script>

<style scoped>
.all{
    width: 100%;
}
.log{
    width: 90%;
    height: 26px;
    margin: 10px auto;
}
.log_left{
    float: left;
}
.log_right{
    float: right;
}
.course_list{
    position: relative;
    width: 90%;
    margin: 10px auto;
}
.course_img{
    width: 100%;
    height: 220px;
    position: relative;
}
.num{
    width: 100%;
    height: 40px;
    background: black;
    opacity: 0.3;
    position: absolute;
    top: 180px;
    color: white;
    text-indent: 1rem;
    line-height: 40px;
}
h4{
    margin-top: 10px;
}
</style>
