<template>
  <div class="dashboard-editor-container">
    <github-corner class="github-corner" />

    <panel-group @handleSetLineChartData="handleSetLineChartData" />

    <div class="buttons">
      <el-button type="primary" @click="handleButtonClick1">学生1</el-button>
      <el-button type="success" @click="handleButtonClick2">学生2</el-button>
    </div>
    <el-row style="background:#fff;padding:16px 16px 0;margin-bottom:32px;">
      <line-chart :chart-data="lineChartData" />
    </el-row>

    <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <raddar-chart :raddar-chart-data="raddarChartData" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <pie-chart :chart-data="pieChartData" />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <bar-chart :bar-chart-data="barChartData" />
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="8">
      <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 12}" :xl="{span: 12}" style="padding-right:8px;margin-bottom:30px;">
        <transaction-table />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <todo-list />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <box-card />
      </el-col>
    </el-row>

  </div></template>

<script>
import GithubCorner from '@/components/GithubCorner'
import PanelGroup from './components/PanelGroup'
import LineChart from './components/LineChart' // 折线图

// import ButtonTest from './components/ButtonTest'

import RaddarChart from './components/RaddarChart'
import PieChart from './components/PieChart'
import BarChart from './components/BarChart'
import TransactionTable from './components/TransactionTable'
import TodoList from './components/TodoList'
import BoxCard from './components/BoxCard'

const lineChartData = {
  newVisitis: {
    expectedData: [100, 120, 161, 134, 105, 160, 165],
    actualData: [120, 82, 91, 154, 162, 140, 145]
  },
  messages: {
    expectedData: [200, 192, 120, 144, 160, 130, 140],
    actualData: [180, 160, 151, 106, 145, 150, 130]
  },
  purchases: {
    expectedData: [80, 100, 121, 104, 105, 90, 100],
    actualData: [120, 90, 100, 138, 142, 130, 130]
  },
  shoppings: {
    expectedData: [130, 140, 141, 142, 145, 150, 160],
    actualData: [120, 82, 91, 154, 162, 140, 130]
  }
}
const animationDuration = 6000

export default {
  name: 'DashboardAdmin',
  components: {
    GithubCorner,
    PanelGroup,
    LineChart,
    // ButtonTest,
    RaddarChart,
    PieChart,
    BarChart,
    TransactionTable,
    TodoList,
    BoxCard
  },
  // 写死默认数据
  data() {
    return {
      lineChartData: lineChartData.newVisitis,
      pieChartData: [
        { value: 320, name: 'Industries' },
        { value: 240, name: 'Technology' },
        { value: 149, name: 'Forex' },
        { value: 100, name: 'Gold' },
        { value: 59, name: 'Forecasts' }
      ],
      barChartData: {
        series: [{
          name: 'pageA',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [79, 52, 200, 334, 390, 330, 220],
          animationDuration
        }, {
          name: 'pageB',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [80, 52, 200, 334, 390, 330, 220],
          animationDuration
        }, {
          name: 'pageC',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [30, 52, 200, 334, 390, 330, 220],
          animationDuration
        }
        ]
      },
      raddarChartData: {
        data: [
          {
            value: [5000, 8000, 12000, 11000, 15000, 14000],
            name: 'Allocated Budget'
          },
          {
            value: [4000, 9000, 15000, 15000, 13000, 11000],
            name: 'Expected Spending'
          },
          {
            value: [5500, 11000, 12000, 15000, 12000, 12000],
            name: 'Actual Spending'
          }
        ]
      }
    }
  },
  methods: {
    handleSetLineChartData(type) {
      this.lineChartData = lineChartData[type]
    },
    // 写死点击按钮修改的数据
    handleButtonClick1() {
      this.$message('按钮1 被点击了')
      this.handleSetLineChartData('purchases')
      this.pieChartData = [
        { value: 120, name: 'Industries' },
        { value: 340, name: 'Technology' },
        { value: 249, name: 'Forex' },
        { value: 300, name: 'Gold' },
        { value: 70, name: 'Forecasts' }
      ]
      this.barChartData = {
        series: [{
          name: 'pageA',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [100, 52, 200, 334, 390, 330, 220],
          animationDuration: this.animationDuration
        }, {
          name: 'pageB',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [80, 52, 220, 334, 390, 330, 220],
          animationDuration: this.animationDuration
        }, {
          name: 'pageC',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [100, 52, 250, 334, 390, 330, 220],
          animationDuration: this.animationDuration
        }
        ]
      }
      this.raddarChartData = {
        data: [
          {
            value: [1100, 7000, 12000, 11000, 15000, 14000],
            name: 'Allocated Budget'
          },
          {
            value: [1400, 9000, 15000, 15000, 13000, 11000],
            name: 'Expected Spending'
          },
          {
            value: [1500, 11000, 12000, 15000, 12000, 12000],
            name: 'Actual Spending'
          }
        ]
      }
    },
    handleButtonClick2() {
      this.$message('按钮2 被点击了')
      this.handleSetLineChartData('messages')
      this.pieChartData = [
        { value: 120, name: 'Industries' },
        { value: 540, name: 'Technology' },
        { value: 249, name: 'Forex' },
        { value: 200, name: 'Gold' },
        { value: 70, name: 'Forecasts' }
      ]
      this.barChartData = {
        series: [{
          name: 'pageA',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [200, 52, 200, 334, 390, 330, 220],
          animationDuration: this.animationDuration
        }, {
          name: 'pageB',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [200, 52, 220, 334, 390, 330, 220],
          animationDuration: this.animationDuration
        }, {
          name: 'pageD',
          type: 'bar',
          stack: 'vistors',
          barWidth: '60%',
          data: [200, 52, 250, 334, 390, 330, 220],
          animationDuration: this.animationDuration
        }
        ]
      }
      this.raddarChartData = {
        data: [
          {
            value: [1100, 11000, 12000, 11000, 15000, 14000],
            name: 'Allocated Budget'
          },
          {
            value: [1400, 11000, 15000, 15000, 13000, 11000],
            name: 'Expected Spending'
          },
          {
            value: [11500, 11000, 12000, 15000, 12000, 12000],
            name: 'Actual Spending'
          }
        ]
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }

  .buttons{
    display: flex;
    gap: 10px;
  }
}

@media (max-width:1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>
