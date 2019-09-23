<template>
  <div>
    <Modal
      title="普通的Modal对话框标题"
      v-model="modalVisible"
      @on-ok="ok"
      @on-cancel="cancel">
      <i-form :label-width="80">
        <i-form :model="dataForm" :label-width="150">
          <Form-item label="产品名称" prop="name">
            <i-input :value.sync="dataForm.name" :maxlength="30" placeholder="产品名称"></i-input>
          </Form-item>
          <Form-item label="产品型号" prop="producttype">
            <i-input :value.sync="dataForm.producttype" :maxlength="30" placeholder="产品型号"></i-input>
          </Form-item>
          <Form-item label="厂商ID" prop="firmid">
            <i-select :model.sync="dataForm.firmid" placeholder="厂商ID">
              <i-option value="" label="请选择"></i-option>
<!--              <i-option-->
<!--                v-for="item in dataItem.dictManufacturer"-->
<!--                :value="item.code"-->
<!--                :label="item.value"></i-option>-->
            </i-select>
          </Form-item>
          <Form-item label="所属行业" prop="industry">
            <i-select :model.sync="dataForm.industry" placeholder="所属行业">
              <i-option value="" label="请选择"></i-option>
<!--              <i-option-->
<!--                v-for="item in dataItem.dictProtocol"-->
<!--                :value="item.code"-->
<!--                :label="item.value"></i-option>-->
            </i-select>
          </Form-item>
          <Form-item label="设备类型" prop="devicetype">
            <i-input :value.sync="dataForm.devicetype" :maxlength="30" placeholder="设备类型"></i-input>
          </Form-item>
          <Form-item label="接入应用层协议类型" prop="agreenmenttype">
            <i-select :model.sync="dataForm.agreenmenttype" placeholder="接入应用层协议类型">
              <i-option value="" label="请选择"></i-option>
<!--              <i-option-->
<!--                v-for="item in dataItem.dictIndustry"-->
<!--                :value="item.code"-->
<!--                :label="item.value"></i-option>-->
            </i-select>
          </Form-item>
          <Form-item label="产品图片">
            <Upload action="//jsonplaceholder.typicode.com/posts/">
              <i-button type="primary" icon="ios-cloud-upload-outline">上传文件</i-button>
            </Upload>
          </Form-item>
        </i-form>
      </i-form>
    </Modal>
  </div>
</template>
<script>
export default {
  data () {
    return {
      modalVisible: true,
      dataForm: {
        name: '',
        producttype: '',
        firmid: '',
        industry: '',
        devicetype: '',
        agreenmenttype: '',
        picUrl: '',
        status: 1
      }
    }
  },
  methods: {
    ok () {
      this.$Message.info('点击了确定')
    },
    cancel () {
      this.$Message.info('点击了取消')
    }
  }
}
</script>
