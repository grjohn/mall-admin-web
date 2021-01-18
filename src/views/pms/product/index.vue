<template> 
  <div class="statistics-layout">
      <div class="layout-title">电影票订单情况</div>
      <el-row :gutter="24" class="font-medium">
        <el-col :span="6" >
          <div style="padding-left: 100px;padding-top: 60px">
            <img :src="img_home_order" class="total-icon">
            <div class="total-title">今日订单总数</div>
            <div class="total-value">103242</div>
          </div>
        </el-col>
        
        
        <el-col :span="6">
          <div style="padding-left: 100px;padding-top: 60px">
            <img :src="img_home_today_amount" class="total-icon">
            <div class="total-title">今日订单总额</div>
            <div class="total-value">￥6954392.00</div>
          </div>
        </el-col>
        <el-col :span="6">
          <div style="padding-left: 100px;padding-top: 60px">
            <img :src="img_home_order" class="total-icon">
            <div class="total-title">昨日订单总数</div>
            <div class="total-value">92311</div>
          </div>
        </el-col>
        <el-col :span="6">
          <div style="padding-left: 100px;padding-top: 60px">
            <img :src="img_home_today_amount" class="total-icon">
            <div class="total-title">昨日订单总额</div>
            <div class="total-value">￥5813458.00</div>
          </div>
        </el-col>
      </el-row>
      <div class="un-handle-content">
        <el-row :gutter="20">
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">电影票订单</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">电影票订单金额</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">演出票访问量</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
        </el-row>
        <el-row :gutter="20">
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">演出票订单</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">演出票订单金额</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">演出票访问量</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
        </el-row>
        <el-row :gutter="20">
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">大礼包订单</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">大礼包订单金额</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
          <el-col :span="8">
            <div class="un-handle-item">
              <span class="font-medium">大礼包访问量</span>
              <span style="float: right" class="color-danger">(10)</span>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>
</template>
<script>

  import {str2Date} from '@/utils/date';
  import img_home_order from '@/assets/images/home_order.png';
  import img_home_today_amount from '@/assets/images/home_today_amount.png';
  import img_home_yesterday_amount from '@/assets/images/home_yesterday_amount.png';
  const DATA_FROM_BACKEND = {
    columns: ['date', 'orderCount','orderAmount'],
    rows: [
      {date: '2020-11-01', orderCount: 10, orderAmount: 1093},
      {date: '2020-11-02', orderCount: 20, orderAmount: 2230},
      {date: '2020-11-03', orderCount: 33, orderAmount: 3623},
      {date: '2020-11-04', orderCount: 50, orderAmount: 6423},
      {date: '2020-11-05', orderCount: 80, orderAmount: 8492},
      {date: '2020-11-06', orderCount: 60, orderAmount: 6293},
      {date: '2020-11-07', orderCount: 20, orderAmount: 2293},
      {date: '2020-11-08', orderCount: 60, orderAmount: 6293},
      {date: '2020-11-09', orderCount: 50, orderAmount: 5293},
      {date: '2020-11-10', orderCount: 30, orderAmount: 3293},
      {date: '2020-11-11', orderCount: 20, orderAmount: 2293},
      {date: '2020-11-12', orderCount: 80, orderAmount: 8293},
      {date: '2020-11-13', orderCount: 100, orderAmount: 10293},
      {date: '2020-11-14', orderCount: 10, orderAmount: 1293},
      {date: '2020-11-15', orderCount: 40, orderAmount: 4293}
    ]
  };
  export default {
    name: 'home',
    data() {
      this.resource_uv_settings = {
        stack: { '用户': ['APP访问', 'H5插件访问','微信访问'] }
      }
      return {
        pickerOptions: {
          shortcuts: [{
            text: '最近一周',
            onClick(picker) {
              const end = new Date();
              let start = new Date();
              start.setFullYear(2020);
              start.setMonth(11);
              start.setDate(3);
              end.setTime(start.getTime() + 3600 * 1000 * 24 * 7);
              picker.$emit('pick', [start, end]);
            }
          }, {
            text: '最近一月',
            onClick(picker) {
              const end = new Date();
              let start = new Date();
              start.setFullYear(2020);
              start.setMonth(10);
              start.setDate(10);
              end.setTime(start.getTime() + 3600 * 1000 * 24 * 30);
              picker.$emit('pick', [start, end]);
            }
          }]
        },
        orderCountDate: '',
        resource_uv_data: {
          columns: ['小时', 'APP访问', 'H5插件访问','微信访问'],
          rows: [
            { '小时': '0-1', 'APP访问': 12210, 'H5插件访问': 1220, '微信访问': 1110 },
            { '小时': '1-2', 'APP访问': 9740, 'H5插件访问': 970, '微信访问': 800 },
            { '小时': '2-3', 'APP访问': 8780, 'H5插件访问': 780, '微信访问': 900 },
            { '小时': '3-4', 'APP访问': 5000, 'H5插件访问': 500, '微信访问': 250 },
            { '小时': '4-5', 'APP访问': 3790, 'H5插件访问': 920, '微信访问': 450 },
            { '小时': '5-6', 'APP访问': 320, 'H5插件访问': 30, '微信访问': 60 },
            { '小时': '6-7', 'APP访问': 920, 'H5插件访问': 20, '微信访问': 140 },
            { '小时': '7-8', 'APP访问': 720, 'H5插件访问': 70, '微信访问': 220 },
            { '小时': '8-9', 'APP访问': 3230, 'H5插件访问': 340, '微信访问': 120 },
            { '小时': '9-10', 'APP访问': 27920, 'H5插件访问': 3430, '微信访问': 450 },
            { '小时': '10-11', 'APP访问': 37920, 'H5插件访问': 3000, '微信访问': 560 },
            { '小时': '11-12', 'APP访问': 47920, 'H5插件访问': 4770, '微信访问': 607 },
            { '小时': '12-13', 'APP访问': 47920, 'H5插件访问': 460, '微信访问': 340 },
            { '小时': '13-14', 'APP访问': 57920, 'H5插件访问': 990, '微信访问': 1560 },
            { '小时': '14-15', 'APP访问': 27920, 'H5插件访问': 270, '微信访问': 1660 },
            { '小时': '15-16', 'APP访问': 37920, 'H5插件访问': 3490, '微信访问': 1440 },
            { '小时': '16-17', 'APP访问': 37920, 'H5插件访问': 3920, '微信访问': 1890 },
            { '小时': '17-18', 'APP访问': 27920, 'H5插件访问': 1920, '微信访问': 1340 },
            { '小时': '18-19', 'APP访问': 47920, 'H5插件访问': 3420, '微信访问': 4130 },
            { '小时': '19-20', 'APP访问': 57920, 'H5插件访问': 14920, '微信访问': 4650 },
            { '小时': '20-21', 'APP访问': 12920, 'H5插件访问': 1230, '微信访问': 1203 },
            { '小时': '21-22', 'APP访问': 13920, 'H5插件访问': 2420, '微信访问': 809 },
            { '小时': '22-23', 'APP访问': 12920, 'H5插件访问': 2340, '微信访问': 1607 },
            { '小时': '23-24', 'APP访问': 15230, 'H5插件访问': 1230, '微信访问': 870 }
          ]
        },
        chartSettings: {
          xAxisType: 'time',
          area:true,
          axisSite: { right: ['orderAmount']},
        labelMap: {'orderCount': '订单数量', 'orderAmount': '订单金额'}},
        chartData: {
          columns: [],
          rows: []
        },
        loading: false,
        dataEmpty: false,
        img_home_order,
        img_home_today_amount,
        img_home_yesterday_amount
      }
    },
    created(){
      this.initOrderCountDate();
      this.getData();
    },
    methods:{
      handleDateChange(){
        this.getData();
      },
      initOrderCountDate(){
        let start = new Date();
        start.setFullYear(2020);
        start.setMonth(11);
        start.setDate(10);
        const end = new Date();
        end.setTime(start.getTime());
        this.orderCountDate=[start,end];
      },
      getData(){
        setTimeout(() => {
          this.chartData = {
            columns: ['date', 'orderCount','orderAmount'],
            rows: []
          };
          for(let i=0;i<DATA_FROM_BACKEND.rows.length;i++){
            let item=DATA_FROM_BACKEND.rows[i];
            let currDate=str2Date(item.date);
            let start=this.orderCountDate[0];
            let end=this.orderCountDate[1];
            if(currDate.getTime()>=start.getTime()&&currDate.getTime()<=end.getTime()){
              this.chartData.rows.push(item);
            }
          }
          this.dataEmpty = false;
          this.loading = false
        }, 1000)
      }
    }
  }
</script>
<style scoped>
  .app-container {
    margin-top: 40px;
    margin-left: 120px;
    margin-right: 120px;
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


