<template>
    <el-row type="flex" justify="space-between" align="middle" class="header">
        <!-- 头部控制菜单栏的收起展开的图标 -->
        <i class="el-icon-back" @click="handleToggle"></i>
        <div>{{username}} {{identity}}</div>
        <!-- javascript:void(0)让a链接点击不做任何操作，无返回 -->
        <a href="javascript:void(0)" @click="handleLogout">退出</a>
    </el-row>
</template>

<script>

import {mapState} from "vuex";

export default {

    computed: {
        // ... {}
        ...mapState("user",{
            // 下面两种写法都可以获取store的值
            username: "username",
            identity: "identity" //state => state.identity
        })
    },

    methods: {
        handleToggle: function(){
            // 触发菜单展开事件
            this.$emit("onChange");
        },

        handleLogout: function(){
            // 退出操作
            this.$store.dispatch("user/logout", () => {
                this.$router.push("/login")
            })
        },


    }
}
</script>

<style scoped>
    .header{
        height: 60px;
    }

    .el-icon-back{
        cursor: pointer;
    }
</style>
