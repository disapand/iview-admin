<template>
  <div>
      <Tabs>
          <!-- 基本信息页面 -->
        <Tab-pane label="基本信息">
            <Card style="width:680px; margin: 10px auto">
            <p slot="title">基本信息采集</p>
              <Row>
                <Col>
                  <Form :label-width="80" :rules="ruleValidate" ref="formValidate" :model="formValidate">
                    <FormItem label=姓名 prop="name">
                      <Input v-model="formValidate.name" />
                    </FormItem>
                    <FormItem label=手机号 prop="tel">
                      <Input v-model="formValidate.tel" />
                    </FormItem>
                    <FormItem label=身份证号 prop="cardID">
                      <Input v-model="formValidate.cardID" />
                    </FormItem>
                    <FormItem label=性别 prop="sex">
                       <Radio-group v-model="formValidate.sex">
                        <Radio label="男"></Radio>
                        <Radio label="女"></Radio>
                       </Radio-group>
                    </FormItem>
                    <FormItem label=借款类别 prop="sort">
                       <Select clearable v-model="formValidate.sort">
                        <Option  v-for="item in JkList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                      </Select>
                    </FormItem>
                    <FormItem label=学历>
                       <Select clearable v-model="xl">
                        <Option v-for="item in XlList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                      </Select>
                    </FormItem>                   
                    <FormItem label=户籍所在地>
                       <Input v-model="area" />
                    </FormItem>
                    <FormItem label=住宅地址 prop="address">
                       <Input v-model="formValidate.address" />
                    </FormItem>                    
                  <Button type="primary" style="transform: translateX(-50%);margin-left: 50%;">提交</Button>
                  </Form>
                </Col>
              </Row>
            </Card>
        </Tab-pane>

        <!-- 职业信息界面 -->
        <Tab-pane label="职业信息">
          <Card style="width:680px; margin: 10px auto">
            <p slot="title">职业信息采集</p>
              <Row>
                <Col>
                  <Form :label-width="80" :rules="ruleValidate" ref="formValidate" :model="formValidate">
                    <FormItem label=工作单位 prop="gzdw">
                      <Input v-model="formValidate.gzdw"/>
                    </FormItem>
                    <FormItem label=单位性质 prop="dwxz">
                      <Input v-model="formValidate.dwxz" />
                    </FormItem>
                    <FormItem label=所属行业>
                      <Input v-model="sshy" />
                    </FormItem>
                    <FormItem label=任职部门>
                      <Input v-model="rzbm" />
                    </FormItem>
                    <FormItem label=职位>
                      <Input v-model="zw" />
                    </FormItem>
                    <FormItem label=入职时间 prop="rzsj">
                      <DatePicker v-model="formValidate.rzsj" type="date" placeholder="选择入职时间" style="width:100%;"></DatePicker>
                    </FormItem>
                    <FormItem label=单位地址 prop="dwdz">
                      <Input v-model="formValidate.dwdz" />
                    </FormItem>
                    <FormItem label=单位电话 prop="dwdh">
                      <Input v-model="formValidate.dwdh" />
                    </FormItem>
                    <FormItem label=任职薪水 prop="rzxs">
                      <Input v-model="formValidate.rzxs" />
                    </FormItem>
                    <FormItem label=总收入 prop="zsr">
                      <Input v-model="formValidate.zsr" />
                    </FormItem>                                       
                  <Button type="primary" style="transform: translateX(-50%);margin-left: 50%;">提交</Button>
                  </Form>
                </Col>
              </Row>
            </Card>
        </Tab-pane>

        <!-- 联系人采集 -->
        <Tab-pane label="联系人信息">
          <Card style="width:680px; margin: 10px auto">
            <p slot="title">联系人信息采集</p>
              <Row>
                <Col>
                  <Form :label-width="100" :rules="ruleValidate" ref="formValidate" :model="formValidate">
                    <FormItem label=联系人姓名 prop="lxrxm">
                      <Input v-model="formValidate.lxrxm" />
                    </FormItem>
                    <FormItem label=和申请人关系 prop="sqrgx">
                      <Select clearable v-model="formValidate.sqrgx">
                        <Option  v-for="item in sqrgxList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                      </Select>
                    </FormItem>
                    <FormItem label=联系电话 prop="lxrdh">
                      <Input v-model="formValidate.lxrdh" />
                    </FormItem>
                    <FormItem label=身份证号 prop="lxrshzh">
                      <Input v-model="formValidate.lxrsfzh" />
                    </FormItem>
                    <FormItem label=联系人是否知道此贷款 prop="zddk">
                       <Radio-group v-model="formValidate.zddk">
                        <Radio label="是"></Radio>
                        <Radio label="否"></Radio>
                       </Radio-group>
                    </FormItem>
                    
                  <Button type="primary" style="transform: translateX(-50%);margin-left: 50%;">提交</Button>
                  </Form>
                </Col>
              </Row>
            </Card>
        </Tab-pane>

        <!-- 其他信息采集 -->
        <Tab-pane label="其他信息">
          <Card style="width:680px; margin: 10px auto">
            <p slot="title">其他信息采集</p>
              <Row>
                <Col>
                  <Form :label-width="80">
                    <FormItem label=房产类别>
                      <Input v-model="fclb" />
                    </FormItem>
                    <FormItem label=购买时间>
                      <DatePicker v-model="gmsj" type="date" placeholder="选择购买时间" style="width:100%;"></DatePicker>
                    </FormItem>
                    <FormItem label=购买价格>
                      <Input v-model="gmjg" />
                    </FormItem>
                    <FormItem label=购买方式>
                      <Input v-model="gmfs" />
                    </FormItem>
                    <FormItem label=购买地址>
                      <Input v-model="gmdz" />
                    </FormItem>
                    
                  <Button type="primary" style="transform: translateX(-50%);margin-left: 50%;">提交</Button>
                  </Form>
                </Col>
              </Row>
            </Card>
        </Tab-pane>

        <!-- 附件信息采集 -->
        <Tab-pane label="附件信息">
          <Card style="width:680px; margin: 10px auto">
            <p slot="title">附件信息采集</p>
              <Row>
                <Col>
                  <Form :label-width="120">
                    <FormItem label=身份证正面照片>
                      <Upload action="/">
                          <Button type="ghost" icon="ios-cloud-upload-outline">请选择身份证正面照片</Button>
                      </Upload>
                    </FormItem>
                    <FormItem label=身份证反面照片>
                      <Upload action="/">
                          <Button type="ghost" icon="ios-cloud-upload-outline">请选择身份证反面照片</Button>
                      </Upload>
                    </FormItem>
                    <FormItem label=居住证明照片>
                      <Upload action="/">
                          <Button type="ghost" icon="ios-cloud-upload-outline">请选择居住证明照片</Button>
                      </Upload>
                    </FormItem>
                    <FormItem label=车辆信息照片>
                      <Upload action="/">
                          <Button type="ghost" icon="ios-cloud-upload-outline">请选择车辆信息照片</Button>
                      </Upload>
                    </FormItem>
                    
                  <Button type="primary" style="transform: translateX(-50%);margin-left: 50%;">提交</Button>
                  </Form>
                </Col>
              </Row>
            </Card>
        </Tab-pane>
    </Tabs>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      tel: "",
      cardID: "",
      sex: "",
      sort: "",
      address: "",
      gzdw: "",
      dwdz: "",
      dwdh: "",
      rzxs: "",
      lxrxm: "",
      sqrgx: "",
      lxrdh: "",
      lxrsfzh: "",
      zddk: "",
      xl:'',
      sshy: '',
      rzbm: '',
      zw: '',
      xl: '',
      fclb: '',
      gmsj: '',
      gmjg: '',
      gmfs: '',
      gmdz: '',

      formValidate: {
        name: "",
        tel: "",
        cardID: "",
        sex: "",
        sort: "",
        address: "",
        gzdw: "",
        dwdz: "",
        dwdh: "",
        rzxs: "",
        lxrxm: "",
        sqrgx: "",
        lxrdh: "",
        lxrsfzh: "",
        zddk: ""
      },
      XlList: [
        { value: "博士", label: "博士" },
        { value: "硕士", label: "硕士" },
        { value: "本科", label: "本科" },
        { value: "大专", label: "大专" },
        { value: "其他", label: "其他" }
      ],
      JkList: [
        { value: "白领贷", label: "白领贷" },
        { value: "房贷", label: "房贷" },
        { value: "信用贷", label: "信用贷" },
        { value: "精英贷", label: "精英贷" },
        { value: "房产二次抵押贷", label: "房产二次抵押贷" },
        { value: "全款房抵押贷", label: "全款房抵押贷" },
        { value: "税贷", label: "税贷" }
      ],
      sqrgxList: [
        { value: "直系亲属", label: "直系亲属" },
        { value: "朋友", label: "朋友" },
        { value: "同事", label: "同事" },
        { value: "其他", label: "其他" }
      ],
      area: "",
      ruleValidate: {
        name: [{ required: true, message: "请填写姓名", trigger: "blur" }],
        tel: [{ required: true, message: "请填写联系电话", trigger: "blur" }],
        cardID: [
          { required: true, message: "请填写身份证号", trigger: "blur" }
        ],
        sex: [{ required: true, message: "请选择性别", trigger: "blur" }],
        sort: [{ required: true, message: "请选择贷款类别", trigger: "blur" }],
        address: [
          { required: true, message: "请填写住宅地址", trigger: "blur" }
        ],
        gzdw: [{ required: true, message: "请填写工作单位", trigger: "blur" }],
        dwxz: [{ required: true, message: "请填写单位性质", trigger: "blur" }],
        dwdh: [{ required: true, message: "请填写单位电话", trigger: "blur" }],
        dwdz: [{ required: true, message: "请填写单位地址", trigger: "blur" }],
        rzxs: [{ required: true, message: "请填写任职薪水", trigger: "blur" }],
        zsr: [{ required: true, message: "请填写总收入", trigger: "blur" }],
        lxrxm: [
          { required: true, message: "请填写联系人姓名", trigger: "blur" }
        ],
        sqrgx: [
          { required: true, message: "请选择和申请人的关系", trigger: "blur" }
        ],
        lxrdh: [
          { required: true, message: "请填写联系人电话", trigger: "blur" }
        ],
        lxrsfzh: [
          { required: true, message: "请填写联系人身份证号", trigger: "blur" }
        ],
        zddk: [{ required: true, message: "请选择", trigger: "blur" }]
      }
    };
  },
  methods: {
    handleArticletitleBlur() {},
    handleSavePublishTime() {
      this.$Notice.info({
        title: "title",
        desc: "desc"
      });
    }
  }
};
</script>

<style>
.lxrgl {
  margin: 0 auto;
}
</style>
