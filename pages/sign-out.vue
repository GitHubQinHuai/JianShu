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
                    <nuxt-link to="/sign-in">登录</nuxt-link>
                    <b>·</b>
                    <nuxt-link to="/sign-out"  class="active">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-form">
                <form method="post">
                <div class="input-prepend">
                    <input type="text" value="" name="" placeholder="你的昵称" class="top-radius">
                    <i class="fa fa-user"></i>
                </div>
                <div class="input-prepend">
                    <input type="text" value="" name="" placeholder="手机号"">
                    <i class="fa fa-phone"></i>
                </div>
                <div class="input-prepend ssm">
                    <input type="text" placeholder="手机验证码">
                    <i class="fa fa-shield"></i>
                    <a class="send-ssm btn btn-success">发送验证码</a>
                </div>
                <div class="input-prepend">
                    <input type="text" value="" name="" placeholder="设置密码" class="bottom-radius">
                    <i class="fa fa-lock"></i>
                </div>
                    <input class="btn btn-success sign-up-btn" type="button" value="注册">
                    <p class="sign-up-msg">点击注册即表示您同意并愿意遵守简书<br>用户协议和隐私政策</p>
                </form>
                <div class="more-sign">
                    <p>社交账号登录</p>
                    <ul>
                        <li class="weixin"><a href="#"><i class="fa fa-weixin"></i></a></li>
                        <li class="qq"><a href="#"><i class="fa fa-qq"></i></a></li>

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