<template>
    <div>
        <el-tabs v-model="activeName" @tab-click="handleClick">
            <el-tab-pane label="我的待办" name="first">
                <div class="m-content">
                    <div>
                        <el-tag type="primary"><b>I</b></el-tag>
                        <h2>今天到期 ({{tableData.length}})</h2>
                        <el-table :data="tableData" style="width: 100%" :show-header="false" >
                            <el-table-column prop="index" label="序号" width="50"></el-table-column>
                            <el-table-column prop="title" label="标题" :show-overflow-tooltip="true" ></el-table-column>
                            <el-table-column prop="status" label="状态" width="120" ></el-table-column>
                            <el-table-column prop="date" label="时间" width="150"></el-table-column>
                        </el-table>
                    </div>
                    <div>
                        <el-tag type="primary"><b>I</b></el-tag>
                        <h2>本周到期 ({{tableData.length}})</h2>
                        <el-table :data="tableData" style="width: 100%" :show-header="false" >
                            <el-table-column prop="index" label="序号" width="50"></el-table-column>
                            <el-table-column prop="title" label="标题" :show-overflow-tooltip="true" ></el-table-column>
                            <el-table-column prop="status" label="状态" width="120" ></el-table-column>
                            <el-table-column prop="date" label="时间" width="150"></el-table-column>
                        </el-table>
                    </div>
                    <div>
                        <el-tag type="primary"><b>I</b></el-tag>
                        <h2>已过期 ({{tableData.length}})</h2>
                        <el-table :data="tableData" style="width: 100%" :show-header="false" >
                            <el-table-column prop="index" label="序号" width="50"></el-table-column>
                            <el-table-column prop="title" label="标题" :show-overflow-tooltip="true" ></el-table-column>
                            <el-table-column prop="status" label="状态" width="120" ></el-table-column>
                            <el-table-column prop="date" label="时间" width="150"></el-table-column>
                        </el-table>
                    </div>
                    <div>
                        <el-tag type="primary"><b>I</b></el-tag>
                        <h2>其他 ({{tableData.length}})</h2>
                        <el-table :data="tableData" style="width: 100%" :show-header="false" >
                            <el-table-column prop="index" label="序号" width="50"></el-table-column>
                            <el-table-column prop="title" label="标题" :show-overflow-tooltip="true" ></el-table-column>
                            <el-table-column prop="status" label="状态" width="120" ></el-table-column>
                            <el-table-column prop="date" label="时间" width="150"></el-table-column>
                        </el-table>
                    </div>
                </div>

            </el-tab-pane>
            <el-tab-pane label="我的已办" name="second">我的已办</el-tab-pane>
            <el-tab-pane label="我的创建" name="third">我的创建</el-tab-pane>
        </el-tabs>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                activeName: 'first',
                tableData: [
                    {'index':'1','title': "移动改变工作项顺序，实现中的工作项可以移动到这个板块中", 'status': '已完成', 'date': '2018-01-11'},
                    {'index':'2','title': "板块排序可以在PC端调整，试试鼠标拖动一个板块", 'status': '已完成', 'date': '2018-01-07'}
                ]
            };
        },
        methods: {
            handleClick(tab, event) {
                console.log(tab, event);
            }
        }
    };
</script>

<style scoped>
    .m-content h2 {
        display: inline-block;
        margin-left: 10px;
    }
    .el-table{margin:30px;}
</style>
