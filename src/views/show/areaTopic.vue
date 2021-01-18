<template>
  <div class="app-container">
   
    <div class="overview-layout">
      <el-row :gutter="24">
        <el-col :span="8">
          <div class="out-border">
            <div class="layout-title">订单地图</div>
            <div style="padding: 40px">
            <ve-map :data="chartData"></ve-map>   
            </div>
          </div>
        </el-col>

        <el-col :span="8">
          <div class="out-border">
            <div class="layout-title">热力地图</div>
            <div style="padding: 40px">
              
            <ve-heatmap :data="heatChartData" :settings="heatChartSettings"></ve-heatmap>
            
            </div>
          </div>
        </el-col>

        <el-col :span="8">
          <div class="out-border">
            <div class="layout-title">省份订单量排名</div>
            <div style="padding: 40px">
            <el-date-picker
              style="float: right;z-index: 1;padding: 20px"
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
            <ve-ring :data="ringChartData" :settings="ringChartSettings" style="padding-top: 40px"></ve-ring>
            
            </div>
           
          </div>
        </el-col>
        
      </el-row>
    </div>

  </div>
</template>

<script>
  export default {
    data () {
      this.chartSettings = {
        metrics: ['电影票', '演出票', '其它'],
        dimension: ['日期']
      };
      this.ringChartSettings = {
        limitShowNum: 5
      };
      this.heatChartSettings = {
        position: 'china',
        type: 'map',
        geo: {
          label: {
            emphasis: {
              show: false
            }
          },
          itemStyle: {
            normal: {
              areaColor: '#323c48',
              borderColor: '#111'
            },
            emphasis: {
              areaColor: '#2a333d'
            }
          }
        }
      };
      return {
        chartData: {
          columns: ['位置', '演出数量', '订单量', '订单金额'],
          rows: [
            { '位置': '吉林', '演出数量': 45, '订单量': 123, '订单金额': 92134 },
            { '位置': '北京', '演出数量': 36, '订单量': 2129, '订单金额': 292342 },
            { '位置': '上海', '演出数量': 35, '订单量': 1243, '订单金额': 94234 },
            { '位置': '浙江', '演出数量': 24, '订单量': 5123, '订单金额': 29234 }
          ]
        },
        ringChartData: {
          columns: ['日期', '订单量'],
          rows: [
            { '日期': '北京', '订单量': 1393 },
            { '日期': '上海', '订单量': 3530 },
            { '日期': '杭州', '订单量': 2923 },
            { '日期': '郑州', '订单量': 2923 },
            { '日期': '济南', '订单量': 2923 },
            { '日期': '重庆', '订单量': 2923 },
            { '日期': '南京', '订单量': 2923 },
            { '日期': '苏州', '订单量': 2923 },
            { '日期': '安徽', '订单量': 2923 },
            { '日期': '厦门', '订单量': 2923 },
            { '日期': '广西', '订单量': 2923 },
            { '日期': '石家庄', '订单量': 2923 },
            { '日期': '武汉', '订单量': 2923 },
            { '日期': '长沙', '订单量': 2923 },
            { '日期': '成都', '订单量': 1723 },
            { '日期': '广州', '订单量': 3792 },
            { '日期': '深圳', '订单量': 4593 }
          ]
        },
        heatChartData: {
          columns: ['lat', 'lng', '人数'],
          rows: [
            { 'lat': 115.892151, 'lng': 28.676493, '人数': 1000 },
            { 'lat': 117.000923, 'lng': 36.675807, '人数': 400 },
            { 'lat': 113.665412, 'lng': 34.757975, '人数': 800 },
            { 'lat': 114.298572, 'lng': 30.584355, '人数': 200 },
            { 'lat': 112.982279, 'lng': 28.19409, '人数': 100 },
            { 'lat': 113.280637, 'lng': 23.125178, '人数': 300 },
            { 'lat': 110.33119, 'lng': 20.031971, '人数': 800 },
            { 'lat': 104.065735, 'lng': 30.659462, '人数': 700 },
            { 'lat': 108.948024, 'lng': 34.263161, '人数': 300 },
            { 'lat': 103.823557, 'lng': 36.058039, '人数': 500 }
          ]
        }
      }
    }
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