<template>
  <div class="profile">
    <base-dialog
      :dialogVisible.sync="dialogVisible"
      :title="title">
      <div>用户编号：{{ruleForm.id}}</div>
      <div>用户性别：{{ruleForm.sex}}</div>
      <div>用户备注：{{ruleForm.count}}</div>
    </base-dialog>
    <div class="profile-header">
      <base-table :dataList="dataList" :titleList="titleList">
        <template v-slot:id="slotProps">
          <h1>
            {{slotProps.row.id}}
          </h1>
        </template>
      </base-table>
    </div>
  </div>
</template>

<script>
import BaseTable from '@/components/baseTable/baseTable'
import BaseDialog from '@/components/baseDialog/baseDialog'

export default {
  components: {
    BaseTable,
    BaseDialog
  },
  data () {
    return {
      dataList: [],
      title: '修改提醒',
      dialogVisible: false,
      ruleForm: {
        id: '',
        sex: 0,
        count: ''
      }
    }
  },
  created () {
    let list = []
    for (let i = 1; i < 100; i++) {
      list.push({
        id: i,
        sex: Math.random() > 0.5 ? 0 : 1,
        count: 100 + i
      })
    }
    this.dataList = list
    this.titleList = [
      {
        key: 'id',
        text: '用户编号'
      },
      {
        key: 'sex',
        text: '用户性别',
        filter: (item) => {
          return item.sex ? '男' : '女'
        }
      },
      {
        key: 'count',
        text: '用户备注'
      },
      {
        key: 'html',
        text: '操作',
        width: 150,
        render (h, column) {
          let handlerClick = () => {
            this.handleDelete(column)
          }
          return <el-button on-click={handlerClick}>删除</el-button>
        },
      }
    ]
  },
  methods: {
    // 删除
    handleDelete (item) {
      this.title = '删除提醒'
      this.dialogVisible = true
      this.ruleForm = item
    }
  }
}
</script>

<style lang="less">
.profile {
  background: #fff;
  border-radius: 5px;
  padding: 10px;
}
.link {
  color: #0a844b;
  font-weight: 800;
  margin-right: 10px;
}
.link-add {
  padding: 10px;
  font-size: 18px;
  display: inline-block;
  background: rgba(1,126,102,0.08);
  margin-bottom: 10px;
}
.top {
  display: none;
  position: fixed;
  bottom: 0;
  right: 0;
  background: #7a6e6e;
  font-size: 20px;
  padding: 10px;
  color: #fff;
}
</style>
