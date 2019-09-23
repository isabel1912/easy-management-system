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
          render: (h, params) => {
            return h('div', [
              h('Button', {
                props: {
                  type: 'primary'
                },
                style: {
                  marginRight: '2px'
                },
                on: {
                  click: () => {
                    this.show(params.index)
                  }
                }
              }, '查看'),
              h('Button', {
                props: {
                  type: 'error'
                },
                on: {
                  click: () => {
                    this.remove(params.index)
                  }
                }
              }, '删除'),
              h('span', this.userStatus(params.row.status))
            ])
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
  },
  methods: {
    userStatus (val) {
      if (val === 1) {
        return '正常'
      }
    }
  }
}
</script>
<style lang="less"></style>
