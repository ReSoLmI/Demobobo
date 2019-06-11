<template>
  <div>
    <el-row>
      <div>
        <div class="header">
          <span style="display:inline-block;line-height:60px;font-size:20px;">001</span>
          <span style="display:inline-block;line-height:60px;font-size:16px;">床 张伟</span>
          <span style="display:inline-block;line-height:60px;font-size:12px;color:#CCC;">9049362</span>
          <span style="display:inline-block;line-height:60px;font-size:12px;color:#CCC;">男</span>
          <span style="display:inline-block;line-height:60px;font-size:12px;color:#CCC;">69岁</span>
          <span
            style="display:inline-block;line-height:12px;width:30px;height:12px;font-size:10px;background:#CCC;color:#fff;border-radius:4px;"
          >01天</span>
          <img
            src="../../static/image/12121/v8.png"
            alt
            style="display:inline-block;position: absolute;top: 22px;left: 300px;"
          >
          <img
            src="../../static/image/12121/4B.png"
            alt
            style="display:inline-block;position: absolute;top: 4px;left: 1000px;"
          >
        </div>
      </div>
      <div>
        <el-table :data="bradenTableData" border style="width: 100%">
          <el-table-column prop="date" label="计划时间" width="150"></el-table-column>
          <el-table-column prop="name" label="执行内容" width="750"></el-table-column>
          <el-table-column prop="tem" label="操作" width="170"></el-table-column>
          <el-table-column prop="bloodpressure" label="时间" width="210">
            <el-time-select
              v-model="value1"
              :picker-options="{start: '08:30',step: '00:15',end: '18:30'}"
              placeholder="选择时间"
            ></el-time-select>
          </el-table-column>
        </el-table>
      </div>
    </el-row>
  </div>
</template>

<script type="text/javascript">
import axios from "axios";
export default {
  data() {
    return {
      contentdata: {},
      baseinfo: {},
      value1: "",
      bradenTableData: [
        {
          date: "09:00",
          name: "测量体温",
          tem: "提交",
          bloodpressure: "3分",
          pulse: "4分"
        },
        {
          date: "11:00",
          name: "冰袋冷敷头部",
          tem: "提交",
          bloodpressure: "轻度受限",
          pulse: "为受损害"
        },
        {
          date: "11:30",
          name: "跌倒/坠床危险因素评估",
          tem: "提交",
          bloodpressure: "偶尔潮湿",
          pulse: "很少潮湿"
        },
        {
          date: "15:30",
          name: "评估病人有无出血情况 ",
          tem: "提交",
          bloodpressure: "偶尔潮湿",
          pulse: "很少潮湿"
        }
      ]
    };
  },

  mounted() {
    axios.get("/api/patient/backlog/query/101").then(res => {
      this.contentdata = res.data.data;
      console.log(this.contentdata);
    });
    axios.get("/api/patients/info ").then(res => {
      console.log(res.data);
    });
  },

  methods: {}
};
</script>



<style type="text/css" lang="scss" scoped>
.header {
  border: 1px solid #c2c2c2;
  height: 60px;
  width: 99%;
  background: #fff;
  display: inline-block;
  span {
    margin-left: 10px;
  }
}
// .el-input__icon {
//   line-height: 28px !important;
// }
</style>
