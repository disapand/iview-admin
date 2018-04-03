<template>
  <div>
    <Card>
      <Input v-model="search" placeholder="请输入搜索内容..." style="width:200px"/>
      <Button type="primary" @click="css">
        <Icon type="search"></Icon>&nbsp;搜索
        </Button>
      <a id="hrefToExportTable" style="postion: absolute;left: -10px;top: -10px;width: 0px;height: 0px;"></a>
      <Button type="ghost" style="float:right"><router-link to="jkrtj">添加借款人</router-link></Button>
      <Button type="primary" style="float:right;margin:0 20px;" @click="exprotToExcel">导出EXCEL</Button>
    </Card>
  <Table stripe :columns="col" :data="data" ref="tableExcel"></Table>
   <Page :total="20" show-elevator show-sizer></Page>
  </div>
</template>

<script>
// import {table2csvData, csvColumns} from './data/table2csv.js';
// import {table2excelData, excelColumns} from './data/table2excel.js';
import table2excel from '@/libs/table2excel.js';
export default {
  data() {
    return {
      col: [
        {
          title: "编号",
          key: "id",
          sortable: true,
        },
        {
          title: "借款人",
          key: "name",
          sortable: true,
        },
        {
          title: "借款类型",
          key: "addr"
        },
        {
          title: "借款序号",
          key: "sort",
          sortable: true,
        },
        {
          title: "借款金额",
          key: "xl",
          sortable: true,
        },
        {
          title: "借款时间",
          key: "gzdw"
        },
        {
          title: "到期时间",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "借款期限",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "已还利息",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "总利息",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "利率",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "手续费",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "是否已还",
          key: "tjsj",
          sortable: true,
        },
        {
          title: "还款方式",
          key: "tjsj",
          sortable: true,
        },
      ],
      data: [
        {
          id: "1",
          name: "张三",
          addr: "陕西省汉中市汉台区七里街道办事处",
          sort: "白领贷款",
          xl: "大专",
          gzdw: "陕西力源仪器设备检测",
          tjsj: "2016-10-03",
          
        },
        {
          id: "2",
          name: "李四",
          addr: "陕西省汉中市汉台区七里街道办事处",
          sort: "2016-10-03",
          xl: "2016-10-03",
          gzdw: "2016-10-03",
          tjsj: "2016-10-03",
        },
        {
          id: "3",
          name: "王五",
          addr: "陕西省汉中市汉台区七里街道办事处",
          sort: "2016-10-03",
          xl: "2016-10-03",
          gzdw: "2016-10-03",
          tjsj: "2016-10-03",
        },
      ]
    };
  }, 

  // 页面的方法
  methods:{
    css(){
      this.$Message.info('测试的提示信息');
    },
    exprotToExcel(){
      table2excel.transform(this.$refs.tableExcel, 'hrefToExportTable', 'excelFileName');
    }
  },
};
</script>

<style>

</style>
