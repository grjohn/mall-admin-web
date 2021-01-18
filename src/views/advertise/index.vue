<template>
  <div class="app-container">
    <div class="un-handle-layout">
      <div class="layout-title">转化比率</div>
      <div class="un-handle-content">
        <el-row :gutter="20">
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">激活转化</span>
              <span style="float: right" class="color-danger">(65.7%)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">登录转化</span>
              <span style="float: right" class="color-danger">(49.8%)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">付费转化</span>
              <span style="float: right" class="color-danger">(78%)</span>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>

    <div class="un-handle-layout">
    <div class="layout-title">广告转化</div>
    <!-- //  <div style="padding: 10px;border-left:1px solid #DCDFE6"> -->
    <el-date-picker
      style="float: right;z-index: 1"
      size="small"
      v-model="value1"
      type="daterange"
      align="right"
      unlink-panels
      range-separator="至"
      start-placeholder="开始日期"
      end-placeholder="结束日期">
    </el-date-picker>
    <div>
        <ve-funnel :data="adConvert"></ve-funnel>
    </div>
      
    <!-- </div> -->
    </div>

    <!-- <div style="padding: 10px;border-left:1px solid #DCDFE6">
            <el-date-picker
              style="float: right;z-index: 1"
              size="small"
              v-model="orderCountDate"
              type="daterange"
              align="right"
              unlink-panels
              range-separator="至"
              start-placeholder="开始日期"
              end-placeholder="结束日期"
              @change="handleDateChange"
              :picker-options="pickerOptions">
            </el-date-picker>
            <div>
              <ve-histogram :data="resource_uv_data" :settings="resource_uv_settings"></ve-histogram>
            </div>
          </div> -->

    <div class="un-handle-layout">
      <div class="layout-title">付费种类</div>
      <ve-histogram :data="chartData" :settings="chartSettings"></ve-histogram>
    </div>

  </div>
</template>

<script>
  export default {
    data () {
      this.chartSettings = {
        metrics: ['电影票', '演出票', '其它'],
        dimension: ['日期']
      }
      return {
        value1: '',
        adConvert: {
          columns: ['状态', '数值'],
          rows: [
            { '状态': '点击', '数值': 900 },
            { '状态': '激活', '数值': 600 },
            { '状态': '登录', '数值': 300 },
            { '状态': '付费', '数值': 100 }
          ]
        },
        chartData: {
          columns: ['日期', '电影票','演出票', '其它'],
          rows: [
            { '日期': '1/10', '电影票': 139, '演出票': 87, '其它': 68 },
            { '日期': '1/11', '电影票': 353, '演出票': 140, '其它': 134 },
            { '日期': '1/12', '电影票': 292, '演出票': 146, '其它': 132 },
            { '日期': '1/13', '电影票': 172, '演出票': 40, '其它': 24 },
            { '日期': '1/14', '电影票': 379, '演出票': 89, '其它': 56 },
            { '日期': '1/15', '电影票': 299, '演出票': 161, '其它': 132 },
            { '日期': '1/16', '电影票': 379, '演出票': 103, '其它': 72 },
            { '日期': '1/17', '电影票': 459, '演出票': 158, '其它': 87 }
          ]
        }
      }
    },

  }
</script>

<style scoped>
  
  .app-container {
    margin-top: 0px;
    margin-left: 40px;
    margin-right: 40px;
  }

  .address-layout {
  }

  .order-detail {
    margin: 30px 40px -10px 0px;
  }

  .order-detail-row{
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .total-layout {
    margin-top: 20px;
  }

  .total-frame {
    border: 1px solid #DCDFE6;
    padding: 20px;
    height: 100px;
  }

  .total-icon {
    color: #409EFF;
    width: 60px;
    height: 60px;
  }

  .total-title {
    position: relative;
    font-size: 16px;
    color: #909399;
    left: 70px;
    top: -50px;
  }

  .total-value {
    position: relative;
    font-size: 18px;
    color: #606266;
    left: 70px;
    top: -40px;
  }

  .un-handle-layout {
    margin-top: 20px;
    border: 1px solid #DCDFE6;
  }

  .layout-title {
    color: #606266;
    padding: 15px 20px;
    background: #F2F6FC;
    font-weight: bold;
  }

  .un-handle-content {
    padding: 20px 40px;
  }

  .un-handle-item {
    border-bottom: 1px solid #EBEEF5;
    padding: 10px;
  }

  .overview-layout {
    margin-top: 20px;
  }

  .overview-item-value {
    font-size: 24px;
    text-align: center;
  }

  .overview-item-title {
    margin-top: 10px;
    text-align: center;
  }

  .out-border {
    border: 1px solid #DCDFE6;
  }

  .statistics-layout {
    margin-top: 20px;
    border: 1px solid #DCDFE6;
  }
  .mine-layout {
    position: absolute;
    right: 140px;
    top: 107px;
    width: 250px;
    height: 235px;
  }
  .address-content{
    padding: 20px;
    font-size: 18px
  }
</style>