<template>
    <div class="sign">
        <!--logo-->
        <div class="logo">
            <!--a链接用来向后端发送请求 以后前段都用<nuxt-link>代替-->
            <nuxt-link to="/">
                <img src="../assets/img/logo.png" alt="">
            </nuxt-link>
        </div>
        <!--登录的表单-->
        <div class="main">
            <div class="title">
                <h4>
                    <nuxt-link to="/sign-in" class="active" >登录</nuxt-link>
                    <b>·</b>
                    <nuxt-link to="/sign-out">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-form">
                <form method="post">
                    <div class="input-prepend">
                        <input type="text" value="" name="" placeholder="手机号或邮箱" class="top-radius">
                        <i class="fa fa-user"></i>
                    </div>
                    <div class="input-prepend">
                        <input type="text" value="" name="" placeholder="密码" class="bottom-radius">
                        <i class="fa fa-lock"></i>
                     </div>
                    <div class="remember">
                    <input type="checkbox">&nbsp;&nbsp;
                    <span>记住我</span>
                </div>
                    <div class="help">
                        <nuxt-link to="/help">登录遇到问题？</nuxt-link>
                    </div>
                    <input class="btn btn-primary" type="button" value="登录">
                </form>
                <div class="more-sign">
                    <p>社交账号登录</p>
                    <ul>
                        <li class="weibo"><a href="#"><i class="fa fa-weibo"></i></a></li>
                        <li class="weixin"><a href="#"><i class="fa fa-weixin"></i></a></li>
                        <li class="qq"><a href="#"><i class="fa fa-qq"></i></a></li>
                        <li class="other"><a href="#">其他</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import 'assets/css/sign.css'
    import NuxtLink from "../.nuxt/components/nuxt-link";
//    import '~/assets/css/sign.css' 或者使用这种写法

    export default{
        components: {NuxtLink},
        layout:'sign',//指明当前所使用的默认模板layout文件夹下的sign.vue
        head(){
            return{
                title:'登录-简书',
                meta:[
                    {hide:'description',name:'description',content:'登录页面'}
                ]
            }
        }
    }
</script>