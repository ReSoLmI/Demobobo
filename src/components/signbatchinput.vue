<template>
  <div>
    <div style="height:50px;border:1px solid #ccc;">
      <div style="display:inline-block;margin-top:11px;margin-left:14px;">
        <div
          style="display:inline-block;width:80px;height:25px; font-size:14px;line-height:25px;text-align:center;border:1px solid #ccc"
        >成人</div>
        <div
          style="display:inline-block;width:80px;height:25px; font-size:14px;line-height:25px;text-align:center;background:#666;border:1px solid #ccc;position:relative;left:-6px;color:#fff;"
        >新生儿</div>
      </div>

      <div style="display:inline-block;margin-top:11px;margin-left:214px;">
        <div
          style="display:inline-block;width:60px;height:25px; font-size:14px;line-height:25px;text-align:center;border:1px solid #ccc;"
        >2</div>
        <div
          style="display:inline-block;width:60px;height:25px; font-size:14px;line-height:25px;text-align:center;border:1px solid #ccc"
        >6</div>
        <div
          style="display:inline-block;width:60px;height:25px; font-size:14px;line-height:25px;text-align:center;border:1px solid #ccc"
        >
          10
          <img
            src="../../static/image/12121/icon.png"
            alt
            style="position:absolute;left:576px;top:13px;"
          >
        </div>
        <div
          style="display:inline-block;width:60px;height:25px; font-size:14px;line-height:25px;text-align:center;border:1px solid #ccc"
        >14</div>
        <div
          style="display:inline-block;width:60px;height:25px; font-size:14px;line-height:25px;text-align:center;border:1px solid #ccc"
        >18</div>
        <div
          style="display:inline-block;width:60px;height:25px; font-size:14px;line-height:25px;text-align:center;background:#666;border:1px solid #ccc;color:#fff;"
        >22</div>
        <select
          class="sign-input-select"
          style="width:160px;height:26px;margin-left:40px;position:relative;left:-40px;top:-2px;"
        >
          <option value="volv">2019-06-15</option>
          <option value="saab">2019-06-14</option>
          <option value="opel">2019-06-13</option>
          <option value="audi">2019-06-12</option>
          <option value="audi">2019-06-11</option>
          <option value="audi">2019-06-10</option>
        </select>
        <div style="display:inline-block;color:#00f;font-size:14px;margin-left:100px">导出Excel</div>
      </div>
    </div>
    <div class="signbatchinput">
      <div class="signbatchinput-left" style="display:inline-block;position:relative;top:-163px;">
        <ul style="width:300px;height:800px">
          <li>全部 待测 我的患者</li>
          <li>全部</li>
          <li>全部</li>
          <li>全部</li>
          <li>全部</li>
          <li>全部</li>
          <li>全部</li>
          <li>全部</li>
        </ul>
      </div>
      <div
        class="signbatchinput-right"
        style="display:inline-block;width:950px;position: relative;left: -53px;"
      >
        <el-table
          :data="tableSignBatchInputData"
          height="530"
          class="table"
          :header-cell-style="{
        'height':'48px',
        'color':'#000',
        'font-size':'12px',
        'font-weight':'300',
        'background':'#eee'
        }"
        >
          <el-table-column prop="number" label="体温(℃)" width="70px"></el-table-column>
          <el-table-column prop="name" label="脉搏(次/分)" width="90px"></el-table-column>
          <el-table-column prop="sex" label="心率(次/分)" width="90px"></el-table-column>
          <el-table-column prop="age" label="呼吸(次/分)" width="90px"></el-table-column>
          <el-table-column prop="mrn" label="血压(mmHg)" width="90px"></el-table-column>
          <el-table-column prop="history" label="大便(次/日)" width="90px"></el-table-column>
          <el-table-column prop="time" label="小便(ml)" width="70px"></el-table-column>
          <el-table-column prop="doctor" label="身高(cm)" width="70px"></el-table-column>
          <el-table-column prop="level" label="体重(kg)" width="70px"></el-table-column>
          <el-table-column prop="diagnose" label="药物过敏" width="80px"></el-table-column>
          <el-table-column prop="food" label="入水量(ml)" width="70px"></el-table-column>
          <el-table-column prop="insurance" label="其他" width="40px">
            <!-- <el-button
              type="text"
              size="mini"
              style="border：none"
              class="btn"
              @click="showDetail"
            >执行明细</el-button>-->
          </el-table-column>
          <el-table-column prop="food" label="总出量(ml)" width="70px"></el-table-column>
        </el-table>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
import axios from "axios";
export default {
  data() {
    return {
      tableSignBatchInputData: []
      // tableSignBatchInputData: [
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "破伤风抗毒素注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   },
      //   {
      //     number: "6824738 R",
      //     name: "5%葡萄糖注射液",
      //     sex: "西药",
      //     age: "250ml",
      //     mrn: "250",
      //     history: "ml/瓶",
      //     time: "长期",
      //     doctor: "静滴",
      //     level: "BID",
      //     diagnose: "2019-06-12  10:00",
      //     food: "2018-03-12  10:00",
      //     insurance: "执行明细"
      //   }
      // ]
    };
  },

  mounted() {},

  methods: {
    showDetail() {}
  }
};
</script>



<style type="text/css" lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
}
.signbatchinput {
  width: 99%;
  height: 900px;
  margin-top: 20px;
  border: 1px solid #ccc;
}
.signbatchinput-left {
  ul {
    li {
      height: 48px;
      width: 250px;
      border: 1px solid #ccc;
    }
  }
}
</style>
