<template>
  <div>
    <i-form inline="">
      <Form>
        <Form-item>
          <i-input :value.sync="dataForm.value" placeholder="请输入..."></i-input>
        </Form-item>
        <Form-item>
          <i-button type="primary" @click="testClick()">搜索</i-button>
        </Form-item>
        <Form-item>
          <i-button type="error">批量删除</i-button>
        </Form-item>
        <Form-item>
          <i-button type="primary" @click="addOrUpdateHandle">新增</i-button>
        </Form-item>
      </Form>
    </i-form>
    <i-table :columns="columns" :data="productList"></i-table>
    <add-or-update v-if="dialogVisible"  ref="addOrUpdate"></add-or-update>
  </div>
</template>
<script>
import { getProductData } from '@/api/data'
import AddOrUpdate from './product-add-or-update'
export default {
  name: 'product',
  data () {
    return {
      dialogVisible: false,
      dataForm: {},
      columns: [
        {
          title: '产品名称',
          key: 'productName'
        },
        {
          title: '产品型号',
          key: 'model'
        },
        {
          title: '设备类型',
          key: 'deviceType'
        },
        {
          title: '创建时间',
          key: 'createTime'
        }
      ],
      productList: []
    }
  },
  components: {
    AddOrUpdate
  },
  mounted () {
    getProductData().then(res => {
      const { data } = res
      this.productList = data['0'].page.records
    })
  },
  activated () {},
  methods: {
    // 新增
    addOrUpdateHandle () {
      this.$nextTick(() => { this.dialogVisible = true })
    },
    testClick () {
      // test1:function init() {
      //   console.log(1)
      // },
      // test2:function init() {
      //   console.log(2)
      // }
    }
  }
}
</script>
<style lang="less"></style>
