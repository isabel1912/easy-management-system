<template>
  <div>
    <i-form inline="">
      <Form>
        <Form-item>
          <i-input :value.sync="dataForm.value" placeholder="请输入..."></i-input>
        </Form-item>
        <Form-item>
          <i-button type="primary">搜索</i-button>
        </Form-item>
        <Form-item>
          <i-button type="error">批量删除</i-button>
        </Form-item>
      </Form>
    </i-form>
    <i-table :columns="columns" :data="productList"></i-table>
  </div>
</template>
<script>
import { getProductData } from '@/api/data'
export default {
  name: 'product',
  data () {
    return {
      dataForm: {
        value: ''
      },
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
  mounted () {
    getProductData().then(res => {
      const { data } = res
      this.productList = data['0'].page.records
      console.log(this.productList)
    })
  },
  activated () {
  },
  methods: {
  }
}
</script>
<style lang="less"></style>
