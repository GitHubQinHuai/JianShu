<template>
    <div>
        <div id="comment-list" class="comment-list">
            <!--提交的留言表单-->
            <form class="new-comment">
                <nuxt-link class="avatar" to="/u/123">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea placeholder="写下你的评论" @focus="send = true" v-model="value"></textarea>
                <transition :duration="200" name="fade">
                    <div class="write-function-block clearfix" v-if="send">
                        <div class="emoji-model-wrap">
                            <a href="javascript:void(0)" class="emoji" @click="showEmoji = !showEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                <transition :duration="200" name="fade">
                            <div v-if="showEmoji" class="emoji-model arrow-up">
                                <vue-emoji @select="selectEmoji"></vue-emoji>
                            </div>
                </transition>
                    </div>
                        <div class="hint">
                            CTRL+ENTER发表
                        </div>
                        <a href="javascript:void(0)" class="btn-send" @click="sendDate">发送</a>
                        <a href="javascript:void (0)" class="cancel" @click="send = false">取消</a>
                    </div>
                </transition>
            </form>
            <!--留言的列表-->
            <div id="normal-comment-list" class="normal-comment-list">
                <!--留言的排序-->
                <div class="top-title">
                    <span>25条评论</span>
                    <a class="author-only" href="javascript:void(0)">只看作者</a>
                    <div class="pull-right">
                        <a class="active" href="javascript:void(0)">按喜欢排序</a>
                        <a  href="javascript:void(0)">按时间正序</a>
                        <a href="javascript:void(0)">按时间倒叙</a>
                    </div>
                </div>
                <!--留言的正文-->
                <div class="comment-placeholer" style="display: none">
                    <div class="author">
                        <div class="avatar"></div>
                        <div class="info">
                            <div class="name"></div>
                            <div class="meta"></div>
                        </div>
                    </div>
                    <div class="title" ></div>
                    <div class="title animated-delay"></div>
                     <div class="tool-group">
                                <i class="fa fa-thumbs-up"></i>
                            <div class="zan"></div>
                                    <i class="fa fa-comment"></i>
                            <div class="zan"></div>
                    </div>
                </div>
                <div :id=" 'comment-' + comment.id" v-for="(comment,index) in comments"  class="comment">
                    <div class="comment-content">
                        <div class="author">
                            <nuxt-link class="avatar" to="/u/123">
                                <img src="comment.user.avatar" alt="">
                            </nuxt-link>
                            <div class="info">
                                <nuxt-link class="name" to="/u/123">
                                    {{comment.user.nick_name}}
                                </nuxt-link>
                                <div class="meta">
                                    <span>
                                        {{comment.floor}}楼.
                                        {{comment.create_at | formateDate}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div class="comment-wrap">
                            <p>{{comment.complied_content}}</p>
                            <div class="tool-group">
                                <a href="javascript:void(0)">
                                    <i class="fa fa-thumbs-o-up"></i>
                                    <span>{{comment.like_count}}人点赞</span>
                                </a>
                                <a href="javascript:void(0)">
                                    <i class="fa fa-comment-o"></i>
                                    <span>回复</span>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div v-if="comment.children.length != 0" class="sub-commit-list">
                        <div v-for="(subComment,index) in comment.children" :id="'comment-' +　subComment.id" class="sub-comment" >
                            <p>
                                <nuxt-link to="/u/123">
                                    {{subComment.user.nick_name}}
                                </nuxt-link>:
                                    <span v-html="subComment.complied_content"></span>
                            </p>
                            <div class="sub-tool-group">
                                <span>{{subComment.create_at | formateDate}}</span>
                                <a href="javascript:void(0)">
                                    <i class="fa fa-comment-o"></i>
                                    <span>回复</span>
                                </a>
                            </div>
                        </div>
                        <div class="more-comment">
                            <a href="javascript:void(0)" class="add-comment-btn">
                                <i class="fa fa-pencil"></i>
                                <span>添加新评论</span>
                            </a>
                        </div>
                    </div>
                    <!--显示表单-->
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import vueEmoji from '../components/VueEmoji'
    export default {
        name:'MyComment',
        data(){
            return{
                send:false,
                showEmoji:false,
                value:'',
                comments:[
                    {
                        id:19935725,
                        floor:2,
                        liked:true,
                        like_count:20,
                        note_id:245684,
                        user_id:445785,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:4258888,
                            is_auther:false,
                            nick_name:'测试用户',
                            badge:null,
                        },
                        create_at:'2018-02-02T07:42:56.000+08:00',
                        children_count:2,
                        complied_content:'写得真的好！即使读上千遍我也不会厌倦！',
                        children:[
                            {
                                id:1258763,
                                user_id:5369741,
                                user:{
                                    id:78542136,
                                    nick_name:'二级评论用户',
                                },
                                parent_id:19935725,
                                create_at: '2018-02-02T07:41:35.000+08:00',
                                complied_content: '这个好，没必要纠缠，好男人就爱，渣男就踹',
                            },
                            {
                                id:1258764,
                                user_id:5369742,
                                user:{
                                    id:78542137,
                                    nick_name:'二级评论用户二号',
                                },
                                parent_id:19935725,
                                create_at: '2018-02-02T07:41:35.000+08:00',
                                complied_content: '相爱就惜缘，不能爱就放手吧。学学古人，优雅地转身，一别两宽，各自安好吧',
                            },
                        ]
                    },
                    {
                        id:19935724,
                        floor:3,
                        liked:true,
                        like_count:20,
                        note_id:245685,
                        user_id:445786,
                        user:{
                            avatar:'/default-avatar.jpg',
                            id:4258889,
                            is_auther:false,
                            nick_name:'测试用户二号',
                            badge:null,
                        },
                        create_at:'2018-02-02T07:42:56.000+08:00',
                        children_count:1,
                        complied_content:'写得真的好！即使读上千遍我也不会厌倦！',
                        children:[
                            {
                                id:1258763,
                                user_id:5369741,
                                user:{
                                    id:78542137,
                                    nick_name:'一级二号的二级评论用户',
                                },
                                parent_id:19935724,
                                create_at: '2018-02-02T07:41:35.000+08:00',
                                complied_content: '这个好，没必要纠缠，好男人就爱，渣男就踹',
                            },
                        ]
                    }
                ]
            }
        },
        components:{
            vueEmoji
        },
        methods:{
            selectEmoji:function (code) {
                this.showEmoji = false;
                this.value += code;
            },
            sendDate:function () {
                console.log('发送value的值给后台')
            }
        }
    }
</script>
<style>
    .fade-enter-active,.fade-leave-active {
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s
    }
    .fade-enter,.fade-leave-to {
        opacity: 0;
        transform: translate3d(0,-5%,0);
        -webkit-transform: translate3d(0,-5%,0);
        transition: .3s;
        -webkit-transition: .3s
    }
    .note .post .comment-list{
        padding-top: 20px;
    }
    .note .post .comment-list .new-comment{
        position: relative;
        margin-left: 48px;
        margin-bottom: 20px;
    }
    .note .post .comment-list .avatar{
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;
    }
    .note .post .comment-list .new-comment .avatar{
        position: absolute;
        left: -48px;
    }
    .note .post .comment-list .new-comment textarea {
        width: 100%;
        height: 80px;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 4px;
        display: inline-block;
        vertical-align: top;
        outline-style: none;
        font-size: 13px;
        resize: none;
        background: #f8f8f8;
    }
    .note .post .comment-list .new-comment .emoji-model-wrap {
        position: relative;
    }
    .note .post .comment-list .new-comment .emoji {
        float: left;
        margin-top: 14px;
    }
    .note .post .comment-list .new-comment .emoji i{
        font-size: 25px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .emoji i:hover {
        color: #333;
    }
    .note .post .comment-list .new-comment .hint{
        float: left;
        margin: 20px 0 0 20px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .cancel{
        float: right;
        font-size: 16px;
        margin: 18px 30px 0 0 ;
        color: #969696 !important;
    }
    .note .post .comment-list .new-comment .cancel:hover{
        color: #333 !important;
    }
    .note .post .comment-list .new-comment .btn-send {
        float: right;
        width: 78px;
        padding: 8px 18px;
        margin: 10px 0 ;
        background: #42c02e;
        border-radius: 20px;
        color: #fff !important;
        text-align: center;
        box-shadow: none;
    }
    .note .post .comment-list .new-comment .btn-send:hover{
        background: #3db952;
    }
    .note .post .comment-list .new-comment .emoji-model-wrap .emoji-model {
        position: absolute;
        top: 50px;
        left: -48px;
        width: 402px;
        height: 208px;
        padding: 10px;
        border: 1px solid #dcdcdc;
        border-radius: 4px;
        box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        background: #fff;
        transform: translated3d(0,-50%.0) rotate(45deg);
    }
    .arrow-up:after{
        content: "";
        display: inline-block;
        border-left: 1px solid #d9d9d9;
        border-top: 1px solid #d9d9d9;
        position: absolute;
        left: 53px;
        top: -1px;
        width: 10px;
        height: 10px;
        background: #fff;
        transform: translate3d(0,-50%,0) rotate(45deg);
    }
    .note .post .comment-list .normal-comment-list {
        margin-top: 30px;
    }
    .note .post .comment-list .top-title{
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .top-title span {
        font-size: 17px;
        font-weight: 700;
    }
    .note .post .comment-list .top-title .author-only {
        font-size: 12px;
        padding: 4px 8px;
        border:1px solid #e1e1e1;
        border-radius: 12px;
        color: #969696 !important;
        margin-left: 10px;
    }
    .note .post .comment-list .top-title .pull-right a {
        margin-left: 10px;
        font-size: 12px;
        color: #969696 !important;
    }
    .note .post .comment-list .top-title .pull-right a.active{
        color: #333 !important;
    }
    .note .post .comment-list .comment {
        padding: 20px 0 30px 0 ;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .comment .author {
        margin-bottom: 15px;
    }
    .note .post .comment-list .info{
        display: block;
        vertical-align: middle;
    }
    .note .post .comment-list .info .name {
        font-size: 15px;
    }
    .note .post .comment-list .info .meta {
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .comment .p {
        font-size: 16px;
        margin:  10px 0 ;
        line-height: 1.5;
        word-break: break-word !important;
    }
    .note .post .comment-list .comment .tool-group a {
        color: #969696 !important;
        margin-right: 10px;
    }
    .note .post .comment-list .comment .tool-group a i {
        font-size: 18px;
        margin-right: 5px;
    }
    .note .post .comment-list .comment .tool-group a span {
        font-size: 14px;
    }
    .note .post .comment-list .sub-commit-list {
        border-left: 2px solid #d9d9d9;
        margin-top: 20px;
        padding: 5px 0 5px 20px;
    }
    .note .post .comment-list .sub-comment {
        padding-bottom: 15px;
        margin-bottom: 15px;
        border-bottom: 1px dashed #f0f0f0;
    }
    .note .post .comment-list .sub-comment p {
        font-size: 14px;
        line-height: 1.5;
        margin-bottom: 5px;
    }
    .note .post .comment-list .sub-comment p a {
        color:#3194d0 !important; ;
    }
    .note .post .comment-list .sub-tool-group {
        font-size: 12px;
        color: #969696;
    }
    .note .post .comment-list .sub-tool-group a {
        margin-left: 10px;
    }
    .note .post .comment-list .sub-tool-group a i{
        margin-right: 5px;
    }
    .note .post .comment-list .more-comment {
        font-size: 14px;
        color: #969696;
    }
    .note .post .comment-list .more-comment a:hover {
        color: #333 !important;
    }
    .note .post .comment-list .more-comment i {
        margin-right: 5px;
    }
</style>