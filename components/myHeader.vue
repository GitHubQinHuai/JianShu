<template>
    <div>
        <nav class="navbar navbar-default nav-fixed-top">
            <div class="width-limit">
                <!--logo-->
                <nuxt-link to="/" class="navLogo">
                    <img src="../assets/img/nav-logo.png" alt="">
                </nuxt-link>
                <!--写文章-->
                <nuxt-link class="btn write-btn" to="/create">
                    <i class="fa fa-edit"></i>
                    写文章
                </nuxt-link>
                <!--如果用户登陆,则显示用户头像-->
                <div style="display: none;" class="user" @mouseleave="userShow = false">
                    <div class="drop-down" @mouseover="userShow = true">
                        <nuxt-link class="avatar" to="/users">
                            <img src="../assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                    </div>
                    <div class="drop-menu" v-show="userShow">
                        <ul>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-user"></i>
                                    我的主页
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-bookmark"></i>
                                    收藏的文章
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-heart"></i>
                                    喜欢的文章
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-cog"></i>
                                    设置
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-sign-out"></i>
                                    退出
                                </nuxt-link>
                            </li>
                        </ul>
                    </div>
                </div>
                <!--登陆注册按钮-->
                <nuxt-link class="btn sign-up" to="/sign-up">注册</nuxt-link>
                <nuxt-link class="btn sign-in" to="/sign-in">登陆</nuxt-link>
                <!--导航-->
                <div class="my-container">
                    <ul class="nav-list">
                        <li class="active">
                            <nuxt-link to="/">
                                <i class="fa fa-compass"></i>
                                <span>发现</span>
                            </nuxt-link>
                        </li>
                        <li>
                            <nuxt-link to="/">
                                <i class="fa fa-book"></i>
                                <span>关注</span>
                            </nuxt-link>
                        </li>
                        <li class="notify" @mouseover="notifyShow = true" @mouseleave="notifyShow = false">
                            <nuxt-link to="/">
                                <i class="fa fa-bell"></i>
                                <span>消息</span>
                            </nuxt-link>
                            <div class="drop-menu" v-show="notifyShow">
                                <ul>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-comment-o"></i>
                                            评论
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-envelope-open-o"></i>
                                            简信
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-upload"></i>
                                            投稿请求
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-heart-o"></i>
                                            喜欢和赞
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/">
                                            <i class="fa fa-user-o"></i>
                                            关注
                                        </nuxt-link>
                                    </li>
                                </ul>
                            </div>
                        </li>
                        <li class="search">
                            <form method="post">
                                <input type="text" placeholder="搜索" @focus="bgShow=true" @blur="bgShow=false">
                                <nuxt-link to="/search" class="search-btn" :class="{active:bgShow}">
                                    <i class="fa fa-search"></i>
                                </nuxt-link>
                            </form>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                userShow:false,
                notifyShow:false,
                bgShow:false
            }
        },
        name: "myHeader"
    }
</script>

<style scoped>
    nav{
        width: 100%;
        height: 56px;
    }
    .navbar{
        padding: 0;
        border-bottom: 1px solid #e7e7e7;
        margin-bottom: 20px;
        background-color: #fff;
    }
    .nav-fixed-top{
        position: fixed;
        top: 0;
        left: 0;
        z-index: 999;
    }
    nav .width-limit{
        min-width: 768px;
        max-width: 1440px;
        width: 100%;
        margin: 0 auto;
    }
    nav .navLogo{
        float: left;
        height: 56px;
        padding: 0;
    }
    nav .navLogo img{
        height: 100%;
    }
    nav .write-btn{
        float: right;
        width: 100px;
        height: 40px;
        margin: 7px 15px 0;
        font-size: 16px;
        line-height: 24px;
        color: #fff!important;
        border-radius: 20px;
        background: #ea6f5a;
    }
    nav .user {
        position: relative;
        float: right;
    }
    nav .user .avatar {
        position: relative;
        width: 40px;
        height: 40px;
        display: block;
        margin: 8px 28px 8px 20px;
    }
    nav .user:hover{
        background-color: #f5f5f5;
    }
    nav .user .avatar::after{
        content: "";
        position: absolute;
        top: 18px;
        right: -14px;
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-top: 6px solid #999;
    }
    nav .user .avatar img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        border: 1px solid #ccc;
    }
    nav .user .drop-menu {
        position: absolute;
        left: 0;
        min-width: 160px;
        border: 1px solid #ccc;
        box-shadow: 0 0 8px rgba(0,0,0,.1);
        font-size: 14px;
    }
    nav .user .drop-menu ul {
        padding: 10px 0;
        margin: 0;
    }
    nav .user .drop-menu ul li a{
        padding:10px 20px;
        /*padding li或者a padding内部元素比较好*/
        display: block;
    }
    nav .user .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    nav .user .drop-menu ul li i {
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
    }
    nav .nav-list {
        margin:0;
        padding:0;
    }
    nav .nav-list::after {
        content: '';
        height: 0;
        display: block;
        visibility: hidden;
        clear: both;
    }
    nav .nav-list>li {
        float: left;
        margin-right: 5px;
    }
    nav .nav-list>li:hover{
        background-color: #f5f5f5;
    }
    nav .nav-list>li>a{
        display: block;
        height: 56px;
        line-height: 56px;
        padding:0 15px;
        font-size: 17px;
        text-align: center;
    }
    nav .nav-list>li a i{
        margin-right: 7px;
        margin-top: 5px;
        font-size: 20px;
    }
    nav .nav-list>li.active{
        color: #ea6f5a;
        background-color: #fff;
    }
    nav .nav-list .notify{
        position: relative;
    }
    nav .nav-list .notify .drop-menu{
        position: absolute;
        z-index: 999;
        left: 0;
        min-width: 160px;
        border: 1px solid #ccc;
        box-shadow: 0 0 8px rgba(0,0,0,.1);
        font-size: 14px;
        background-color: #fff;
    }
    nav .notify .drop-menu ul {
        padding: 10px 0;
        margin: 0;
    }
    nav .notify .drop-menu ul li a{
        padding:10px 20px;
        /*padding li或者a padding内部元素比较好*/
        display: block;
    }
    nav .notify .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    nav .notify .drop-menu ul li i {
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
    }
    nav a.sign-in{
        float: right;
        margin: 8px 6px 0 10px;
        line-height: 24px;
        font-size: 15px;
        color: #969696!important;
    }
    nav a.sign-up:hover{
        background-color: rgba(254,247,246);
    }
    nav a.sign-up{
        float: right;
        width: 80px;
        height: 38px;
        margin: 7px 6px 0 10px;
        line-height: 24px;
        font-size: 15px;
        border: 1px solid #ea6f5a;
        border-radius: 20px;
        color: #ea6f5a!important;
    }
    nav .nav-list .search {
        padding-left: 15px;
    }
    nav .nav-list .search:hover {
        background-color: #fff;
    }
    nav .nav-list .search a.search-btn{
        display: block;
        width: 30px;
        height: 30px;
        position: absolute;
        right: 10px;
        top: 5px;
        text-align: center;
    }
    nav .nav-list .search form a.active{
        background-color: #969696;
        border-radius: 50%;
        color: #fff!important;
    }
    nav .nav-list .search a.search-btn i {
        width: 30px;
        height: 30px;
    }
    nav .nav-list .search form input{
        width: 240px;
        height: 38px;
        border: none;
        background-color: #eee;
        border-radius: 20px;
        padding: 0 30px 0 20px;
        font-size: 15px;
        transition: width .3s ease-in;
    }
    nav .nav-list .search form input:focus{
        width: 320px;
    }
    nav .nav-list .search form{
        margin-top: 9px;
        position: relative;
    }
    @media (max-width: 1440px){
        nav .nav-list>li>a i{
            display: none;
        }
        nav .nav-list .search form input{
            width: 160px;
        }
        nav .nav-list .search form input:focus{
            width: 240px;
        }
    }
    @media (max-width: 1080px){
        nav .nav-list>li>a i{
            display: inline-block;
        }
        nav .nav-list>li>a span{
            display: none;
        }
        nav .nav-list .search form input{
            width: 150px;
        }
        nav .nav-list .search form input:focus{
            width: 150px;
        }
    }
    @media (max-width: 768px){
        nav .nav-list{
            display: none;
        }
    }
</style>