<!--登录页面没有组件和其他页面通用-->
<template>
    <div class="login-wrap">
        <div class="ms-header-bar">
            <span class="ms-header-bar-left"></span>
            <span class="ms-header-bar-right"></span>
        </div>
        <div class="ms-title ms-title-bg"></div>
        <div class="ms-login">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="0px" class="demo-ruleForm">
                <el-form-item prop="username">
                    <el-input v-model="ruleForm.username" placeholder="请输入用户名"></el-input>
                </el-form-item>
                <el-form-item prop="password">
                    <el-input type="password" placeholder="请输入密码" v-model="ruleForm.password" @keyup.enter.native="submitForm('ruleForm')"></el-input>
                </el-form-item>
                <div class="login-btn">
                    <el-button type="primary" @click="submitForm('ruleForm')">登录</el-button>
                </div>
                <!--<p style="font-size:12px;line-height:30px;color:#999;">Tips : 用户名和密码随便填。</p>-->
            </el-form>
        </div>
        <div class="copyright">Copyright © 广东银信金融服务中心,All rights reserved.</div>
    </div>
</template>

<script>
    export default {
        data: function(){
            return {
                ruleForm: {
                    username: '',
                    password: ''
                },
                rules: {
                    username: [
                        { required: true, message: '用户名不能为空', trigger: 'blur' }
                    ],
                    password: [
                        { required: true, message: '登录密码不能为空', trigger: 'blur' }
                    ]
                }
            }
        },
        methods: {
            submitForm(formName) {
                const self = this;
                self.$refs[formName].validate((valid) => {
                    if (valid) {
                        localStorage.setItem('ms_username',self.ruleForm.username);
                        self.$router.push('/readme');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            }
        }
    }
</script>

<style scoped>
    .login-wrap{
        position: relative;
        width:100%;
        height:100%;
        background: url("./../../../static/img/login-bg.png") no-repeat;
    }
    .ms-header-bar{
        width:100%;
        height:36px;
        background: #fff;
        padding:3px 5px;
    }
    .ms-header-bar-left{
        float: left;
        width:160px;
        height: 30px;
        background: url("./../../../static/img/nav-gdrc-logo.png") no-repeat;
    }
    .ms-header-bar-right{
        float: right;
        width:70px;
        height: 30px;
        background: url("./../../../static/img/nav-inthink-logo.png") no-repeat;
    }
    .ms-title{
        position: absolute;
        top:-65%;
        right:0;
        left:0;
        bottom:0;
        width:600px;
        height:100px;
        margin: auto;
        text-align: center;

    }
    .ms-title-bg{
        background: url("./../../../static/img/index-slogan.png") no-repeat;
    }
    .ms-login{
        position: absolute;
        left:50%;
        top:60%;
        width:300px;
        height:160px;
        margin:-150px 0 0 -190px;
        padding:40px;
        border-radius: 5px;
        background: #fff;
        border: 1px solid #99d9f6;
        -webkit-border-radius: 4px;
        -moz-border-radius: 4px;
        border-radius: 4px;
    }
    .login-btn{
        text-align: center;
    }
    .login-btn button{
        width:100%;
        height:36px;
    }
    .copyright{
        position: absolute;
        bottom: 10%;
        width:100%;
        text-align: center;
    }
</style>
