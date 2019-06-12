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
    <div class="signbatchinput" style="display:flex;">
      <div class="signbatchinput-left" style="width:200px;height:800px;">
        <ul style>
          <li style="background:#fff;">
            <el-menu
              :default-active="activeIndex"
              class="el-menu-demo"
              mode="horizontal"
              @select="handleSelect"
              style="display:inline-block;"
            >
              <el-menu-item index="1" style="font-weight:600">全部</el-menu-item>
              <el-menu-item index="2" style="font-weight:600">待测</el-menu-item>
            </el-menu>
            <input
              type="radio"
              style="display:inline-block;position:relative;top:-18px;margin-left:-4px;"
            >
            <span
              style="display:inline-block;position:relative;top:-20px;font-size:12px;margin-left:-6px;"
            >我的患者</span>
          </li>
          <li>
            <span
              style="display:inline-block;background:#f00;font-size:10px;height:48px;line-height:48px;"
            >满</span>
            <span style="font-size:12px;margin-left:20px;color:#FF55D6">003</span>
            <span style="font-size:12px;margin-left:30px">王大大</span>
          </li>
          <li>
            <span style="font-size:12px;margin-left:37px;color:#00f;line-height:48px;">007</span>
            <span style="font-size:12px;margin-left:30px;line-height:48px;">王丽清</span>
          </li>
          <li>
            <span
              style="display:inline-block;background:#f00;font-size:10px;height:48px;line-height:48px;"
            >满</span>
            <span style="font-size:12px;margin-left:20px;color:#FF55D6">010</span>
            <span style="font-size:12px;margin-left:30px">陈荣泰</span>
          </li>
          <li>
            <span style="font-size:12px;margin-left:37px;color:#FF55D6;line-height:48px;">011</span>
            <span style="font-size:12px;margin-left:30px;line-height:48px;">宿吉涵</span>
          </li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
          <li></li>
        </ul>
      </div>
      <div class="signbatchinput-right" style="height:800px;flex:1;">
        <el-table
          :data="tableSignBatchInputData"
          height="800px"
          class="table"
          border
          :header-cell-style="{
        'height':'48px',
        'color':'#000',
        'font-size':'12px',
        'font-weight':'300',
        'background':'#eee'
        }"
        >
          <el-table-column prop="number" label="体温(℃)" width="90px"></el-table-column>
          <el-table-column prop="name" label="脉搏(次/分)" width="106px"></el-table-column>
          <el-table-column prop="sex" label="心率(次/分)" width="100px"></el-table-column>
          <el-table-column prop="age" label="呼吸(次/分)" width="90px"></el-table-column>
          <el-table-column prop="mrn" label="血压(mmHg)" width="100px"></el-table-column>
          <el-table-column prop="history" label="大便(次/日)" width="90px"></el-table-column>
          <el-table-column prop="time" label="小便(ml)" width="70px"></el-table-column>
          <el-table-column prop="doctor" label="身高(cm)" width="70px"></el-table-column>
          <el-table-column prop="level" label="体重(kg)" width="70px"></el-table-column>
          <el-table-column prop="diagnose" label="药物过敏" width="80px"></el-table-column>
          <el-table-column prop="food" label="入水量(ml)" width="80px"></el-table-column>
          <el-table-column prop="insurance" label="其他" width="50px"></el-table-column>
          <el-table-column prop="food" label="总出量(ml)" width="80px"></el-table-column>
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
      activeIndex: "1",
      tableSignBatchInputData: [],
      tableSignBatchInputData: [
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        ,
        {
          number: "口温 37.5",
          name: "75",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "待测",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "待测",
          name: "待测",
          sex: "",
          age: "",
          mrn: "98/121",
          history: "",
          time: "待测",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "",
          name: "",
          sex: "25",
          age: "待测",
          mrn: "98/121",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        },
        {
          number: "耳温  373",
          name: "待测",
          sex: "",
          age: "",
          mrn: "",
          history: "",
          time: "",
          doctor: "",
          level: "",
          diagnose: "",
          food: "",
          insurance: ""
        }
      ]
    };
  },

  mounted() {},

  methods: {
    showDetail() {},
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  }
};
</script>



<style type="text/css" lang="scss" >
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
      // width: 250px;
      border-bottom: 1px solid #ccc;
      // border-right: 1px solid #ccc;
    }
  }
  // li:nth-of-type(odd) {
  //   background: #effafe;
  // }
}
.el-menu-item {
  padding: 0 10px;
  line-height: 51px;
}
.el-menu--horizontal > .el-menu-item {
  height: 48px;
  line-height: 48px;
}
.el-menu--horizontal > .el-menu-item.is-active {
  border-bottom: 4px solid #409eff;
  color: #303133;
}
// li:nth-child(1) {
//   background: #fff;
// }

.el-table__row {
  height: 49px;
}
</style>
