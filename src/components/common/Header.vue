<template>
    <div class="header">
        <div class="logo">广东银信金融服务中心<i class="el-icon-menu" @click="showMenu"></i></div>
        <img class="header-logo" src="../../../static/img/logo.png" alt="">

        <div class="user-info">
            <el-dropdown trigger="click" @command="handleCommand">
                <span class="el-dropdown-link">
                    <img class="user-logo" src="../../../static/img/img.jpg">
                    {{username}}
                </span>
                <el-dropdown-menu slot="dropdown">
                    <el-dropdown-item command="loginout">退出</el-dropdown-item>
                </el-dropdown-menu>
            </el-dropdown>
        </div>
    </div>
</template>
<script>
    import bus from "../../bus.js"

    export default {
        data() {
            return {
                name: 'gdrcu',
                slidermenu: 0
            }
        },
        computed: {
            username() {
                let username = localStorage.getItem('ms_username');
                return username ? username : this.name;
            }
        },
        methods: {
            handleCommand(command) {
                if (command == 'loginout') {
                    localStorage.removeItem('ms_username');
                    this.$router.push('/login');
                }
            },
            showMenu: function () {
                this.slidermenu++;
                bus.$emit('slidermenu',this.slidermenu);
            }
        }
    }
</script>
<style scoped>
    .header {
        position: relative;
        box-sizing: border-box;
        width: 100%;
        height: 40px;
        font-size: 14px;
        line-height: 40px;
        color: #fff;
    }

    .header .logo {
        float: left;
        width: 250px;
        text-align: center;
        position: relative;
    }

    .user-info {
        float: right;
        padding-right: 50px;
        font-size: 16px;
        color: #fff;
    }

    .user-info .el-dropdown-link {
        position: relative;
        display: inline-block;
        padding-left: 50px;
        color: #fff;
        cursor: pointer;
        vertical-align: middle;
    }

    .user-info .user-logo {
        position: absolute;
        left: 0;
        top: 5px;
        width: 30px;
        height: 30px;
        border-radius: 50%;
    }

    .el-dropdown-menu__item {
        text-align: center;
    }

    .header-logo {
        position: absolute;
        left: 20px;
        top: 8px;
        width: 30px;
        /*height: 30px;*/
        border-radius: 50%;
    }

    .el-icon-menu {
        position: absolute;
        right: 15px;
        top: 13px;
    }
</style>
