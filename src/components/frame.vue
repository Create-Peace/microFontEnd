<template>
    <div class="frame">
        <el-dialog :visible.sync="dialogVisible" append-to-body width="800px" top="10vh">
            <el-table :data="tableData">
            <el-table-column
                prop="date"
                label="日期"
                width="180">
            </el-table-column>
            <el-table-column
                prop="name"
                label="姓名"
                width="180">
            </el-table-column>
            <el-table-column
                prop="address"
                label="地址">
            </el-table-column>
        </el-table>
        <span slot="footer" class="dialog-footer">
            <el-button @click="dialogVisible = false">取 消</el-button>
            <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
        </span>
        </el-dialog>
    </div>
</template>
<script>
    import { Table, TableColumn, Dialog } from 'element-ui'
    export default {
        name: 'frame',
        props: {
            dialogFlag: {
                type: Boolean,
                default: false
            }
        },
        data () {
            return {
                tableData: [{
                    date: '2016-05-02',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-04',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1517 弄'
                }, {
                    date: '2016-05-01',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1519 弄'
                }, {
                    date: '2016-05-03',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1516 弄'
                }]
            }
        },
        computed: {
            dialogVisible: {
                get: function () {
                    return this.dialogFlag
                },
                set: function (newVal) {
                    console.log('12312313')
                    this.$emit('CloseFrame')
                }
            }
        },
        component: {
            ElTable: Table,
            ELColumn: TableColumn,
            ElDialog: Dialog
        },
        methods: {
            closeDialog () {
                this.dialogVisible = false
            }
        }
    }
</script>
<style>
@import 'https://unpkg.com/element-ui/lib/theme-chalk/index.css';
</style>
