<template>
  <div>
    <i-table :columns="columns" :data="datalist"></i-table>
  </div>
</template>
<script>
import { getUserlistData } from '@/api/data'

export default {
  data () {
    return {
      datalist: [],
      columns: [
        {
          title: 'ID',
          key: 'createUserId'
        },
        {
          title: '用户名',
          key: 'username'
        },
        {
          title: '邮箱',
          key: 'email'
        },
        {
          title: '手机号',
          key: 'mobile'
        },
        {
          title: '状态',
          key: 'status'
        },
        {
          title: '创建时间',
          key: 'createTime'
        },
        {
          title: '操作',
          key: 'action',
          width: 150,
          align: 'center',
          render (row, column, index) {
            return `<i-button type="primary">查看</i-button> <i-button type="error">删除</i-button>`
          }
        }
      ]
    }
  },
  mounted () {
    getUserlistData().then(res => {
      const { data } = res
      console.log(data)
      this.datalist = data['0'].page.list
    })
  }
}
</script>
<style lang="less"></style>
