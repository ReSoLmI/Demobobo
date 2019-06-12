<template>
  <div>
    <el-form :model="dayassesmentData" ref="dayassesmentData">
      <el-row>
        <div class="block">
          <el-date-picker
            v-model="value7"
            type="daterange"
            align="right"
            unlink-panels
            range-separator="至"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            :picker-options="pickerOptions3"
          ></el-date-picker>
        </div>
        <ul class="dayassesment-ul">
          <li>当前</li>
          <li>一周</li>
          <li>住院至今</li>
        </ul>
        <div class="dayassesment-div-record">
          <el-button>打印</el-button>
        </div>
      </el-row>
      <el-row>
        <el-table
          :data="nursingrecordTableData"
          :span-method="objectSpanMethod"
          border
          style="width: 100%; margin-top: 20px"
        >
          <el-table-column prop="id" label="ID" width="180"></el-table-column>
          <el-table-column prop="name" label="姓名"></el-table-column>
          <el-table-column prop="amount1" label="数值 1（元）"></el-table-column>
          <el-table-column prop="amount2" label="数值 2（元）"></el-table-column>
          <el-table-column prop="amount3" label="数值 3（元）"></el-table-column>
        </el-table>
      </el-row>
    </el-form>
  </div>
</template>

<script type="text/javascript">
import axios from "axios";
export default {
  data() {
    return {
      dayassesmentData: {},
      pickerOptions3: {
        shortcuts: [
          {
            text: "最近一周",
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit("pick", [start, end]);
            }
          },
          {
            text: "最近一个月",
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
              picker.$emit("pick", [start, end]);
            }
          },
          {
            text: "最近三个月",
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
              picker.$emit("pick", [start, end]);
            }
          }
        ]
      },
      value7: "",

      nursingrecordTableData: [
        {
          id: "12987122",
          name: "王小虎",
          amount1: "234",
          amount2: "3.2",
          amount3: 10
        },
        {
          id: "12987122",
          name: "王小虎",
          amount1: "165",
          amount2: "4.43",
          amount3: 12
        },
        {
          id: "12987122",
          name: "王小虎",
          amount1: "324",
          amount2: "1.9",
          amount3: 9
        },
        {
          id: "12987125",
          name: "王小虎",
          amount1: "621",
          amount2: "2.2",
          amount3: 17
        },
        {
          id: "12987126",
          name: "王小虎",
          amount1: "539",
          amount2: "4.1",
          amount3: 15
        }
      ],
      column_row_offset: {
        id: [3, 1, 1],
        name: [2, 1, 1, 1],
        amount1: [1, 1, 1, 1, 1],
        amount2: [1, 1, 1, 1, 1],
        amount3: [1, 1, 1, 1, 1]
      },
      now_col_row_num: {},
      now_col_offset: {}
    };
  },

  mounted() {
    console.log(333);
  },

  methods: {
    objectSpanMethod({ row, column, rowIndex, columnIndex }) {
      if (!this.now_col_row_num[column.property]) {
        this.now_col_row_num[column.property] = Object.assign(
          [],
          this.column_row_offset[column.property]
        );
        let a = this.now_col_row_num[column.property].shift();
        this.now_col_offset[column.property] = a;
        return {
          rowspan: a,
          colspan: 1
        };
      } else if (rowIndex >= this.now_col_offset[column.property]) {
        let a = this.now_col_row_num[column.property].shift();
        this.now_col_offset[column.property] += a;
        return {
          rowspan: a,
          colspan: 1
        };
      } else {
        return {
          rowspan: 0,
          colspan: 0
        };
      }
    }
  }
};
</script>

<style type="text/css" lang="scss" scoped>
.dayassesment-div-record {
  float: right;
  display: inline-block;
  margin-right: 35px;
}
</style>
