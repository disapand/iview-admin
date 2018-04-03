<template>
  <div>
      <Card style="width:680px; margin: 10px auto">
            <p slot="title">借款添加</p>
              <Row>
                <Col>
                  <Form :label-width="80" :rules="ruleValidate" ref="formValidate" :model="formValidate">
                    <FormItem label=借款人 prop="name">
                      <Select clearable v-model="formValidate.sort" filterable>
                        <Option  v-for="item in jkrList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                      </Select>
                    </FormItem>
                    <FormItem label=借款类别 prop="sort">
                       <Select clearable v-model="formValidate.sort">
                        <Option  v-for="item in JkList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                      </Select>
                    </FormItem>
                    <FormItem label=借款期限 prop="jkqx">
                       <Row>
                           <Col span="20">
                           <Select clearable v-model="formValidate.jkqx">
                            <Option  v-for="item in jkqxList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                            </Select>
                            </Col>
                            <Col span="4" style="padding-left:10px;">个月
                            </Col>
                       </Row>
                    </FormItem>
                    <FormItem label=借款金额>
                       <Row>
                           <Col span="14">
                            <Input v-model="jkje" placeholder="请输入借款金额"/> 
                           </Col>
                           <Col span="10" style="padding-left:10px">
                            <span>金额(大写):{{ jkje }}</span>   
                           </Col>
                       </Row>
                    </FormItem>                   
                    <FormItem label=利率>
                       <Row>
                           <Col span="14">
                            <Input v-model="ll" placeholder="利率"/> 
                           </Col>
                           <Col span="10" style="padding-left:10px">
                            <span>%</span>   
                           </Col>
                       </Row>
                    </FormItem>
                    <FormItem label=手续费>
                       <Row>
                           <Col span="14">
                            <Input v-model="sxf" placeholder="手续费"/> 
                           </Col>
                           <Col span="10" style="padding-left:10px">
                            <span>%</span>   
                           </Col>
                       </Row>
                    </FormItem>
                    <FormItem label=借款时间>
                      <DatePicker v-model="jksj" type="date" placeholder="选择借款时间" style="width:100%;"></DatePicker>
                    </FormItem>
                    <FormItem label=还款方式 prop="hkfs">
                       <Select clearable v-model="formValidate.hkfs">
                            <Option  v-for="item in hkfsList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                            </Select>
                    </FormItem>                    
                  <Button type="primary" style="transform: translateX(-50%);margin-left: 50%;">提交</Button>
                  </Form>
                </Col>
              </Row>
            </Card>
  </div>
</template>
<script>
export default {
  data() {
    return {
      jkje: "",
      ll:'',
      sxf:'',
      jksj:'',
      jkrList: [
        {
          value: "张三",
          label: "张三"
        },
        {
          value: "李四",
          label: "李四"
        },
        {
          value: "李斯",
          label: "李斯"
        }
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
      jkqxList: [
        {
          value: "0.5",
          label: "0.5"
        },
        {
          value: "1",
          label: "1"
        },
        {
          value: "2",
          label: "2"
        },
        {
          value: "3",
          label: "3"
        },
        {
          value: "4",
          label: "4"
        },
        {
          value: "5",
          label: "5"
        },
        {
          value: "6",
          label: "6"
        },
        {
          value: "7",
          label: "7"
        },
        {
          value: "8",
          label: "8"
        },
        {
          value: "9",
          label: "9"
        },
        {
          value: "10",
          label: "10"
        },
        {
          value: "11",
          label: "11"
        },
        {
          value: "12",
          label: "12"
        }
      ],
      hkfsList:[
          {
              value:'付息还本',
              label:'付息还本',
          },
          {
              value:'到期本息',
              label:'到期本息',
          },
      ],
      formValidate: {},
      ruleValidate: {}
    };
  },
  computed:{

  },
};
</script>
