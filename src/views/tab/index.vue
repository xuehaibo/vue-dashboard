<template>
  <div class="tab-container" style="height:100%;">
    <!-- <el-tag>mounted times ：{{ createdTimes }}</el-tag> -->
    <!-- <el-alert :closable="false" style="width:200px;display:inline-block;vertical-align: middle;margin-left:30px;" title="Tab with keep-alive" type="success" /> -->
    <!-- <el-tabs v-model="activeName" style="margin-top:15px;" type="border-card">
      <el-tab-pane v-for="item in tabMapOptions" :key="item.key" :label="item.label" :name="item.key">
        <keep-alive>
          <tab-pane v-if="activeName==item.key" :type="item.key" @create="showCreatedTimes" />
        </keep-alive>
      </el-tab-pane>
    </el-tabs> -->
     <el-date-picker
      v-model="searchData.selectDate"
      format="yyyy-MM-dd"
      value-format="yyyy-MM-dd"
      type="date"
      placeholder="选择日期">

    </el-date-picker>
    
    <el-select v-model="searchData.selectCh" placeholder="请选择">
      <el-option
        v-for="item in chList"
        :key="item.value"
        :label="item.label"
        :value="item.value">
      </el-option>
    </el-select>
     <el-button type="info" @click="searchTable">查询</el-button>

        <el-table
    :data="tableInfo"
    :default-sort = "{prop: 'date', order: 'descending'}"
    border
    style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        sortable
        width="180">
      </el-table-column>
      <el-table-column
        prop="ch"
        label="渠道"
        width="180">
      </el-table-column>
      <el-table-column
        prop="pv"
        label="pv">
      </el-table-column>
      <el-table-column
        prop="uv"
        label="uv">
      </el-table-column>
      <el-table-column
        prop="version"
        label="版本">
      </el-table-column>
  </el-table>
  </div>
</template>

<script>
import tabPane from './components/TabPane';
import { search } from '@/api/user'
export default {
  name: 'Tab',
  components: { tabPane },
  data() {
    return {
      tabMapOptions: [
        { label: 'China', key: 'CN' },
        { label: 'USA', key: 'US' },
        { label: 'Japan', key: 'JP' },
        { label: 'Eurozone', key: 'EU' }
      ],
      activeName: 'CN',
      createdTimes: 0,
      tableInfo:[
        {
          date: '2016-05-03',
          ch: '王小虎',
          pv: '1000',
          uv: '500',
          version: 'v1.1.0'
        },
        {
          date: '2016-05-04',
          ch: '王小虎',
          pv: '1000',
          uv: '500',
          version: 'v1.1.0'
        },
        {
          date: '2016-05-05',
          ch: '王小虎',
          pv: '1000',
          uv: '500',
          version: 'v1.1.0'
        },
        {
          date: '2016-05-03',
          ch: '王小虎',
          pv: '1000',
          uv: '500',
          version: 'v1.1.0'
        },
        {
          date: '2016-05-03',
          ch: '王小虎',
          pv: '1000',
          uv: '500',
          version: 'v1.1.0'
        },
      ],
      chList: [
        {
          value: 'huawei',
          label: '华为'
        },
        {
          value: 'xiaomi',
          label: '小米'
        },
        {
          value: 'apple',
          label: '苹果'
        },
      ],
      searchData:{
        selectDate:new Date(),
        selectCh:'华为'
      },
      loginForm: {
        username: 'admin',
        password: '111111'
      },
    }
  },
  created(){
    let today = new Date();
    // this.searchData
  },
  methods: {
    showCreatedTimes() {
      this.createdTimes = this.createdTimes + 1
    },
    searchTable(){
      let searchInfo = this.searchData;
      console.log('searchInfo',searchInfo);
      // axios.post('/search/ajaxSearch',{
      //   ch:searchInfo.selectCh,
      //   date:searchInfo.selectCh
      // }).then((res) => {
      //   this.tableInfo = rea.data;
      // });
      // this.$store.dispatch('user/login', this.searchData)
      // .then(() => {
      //   // this.$router.push({ path: this.redirect || '/' })
      //   // this.loading = false
      // })
      // .catch(() => {
      //   // this.loading = false
      // })
      // this.$store.dispatch('user/login', this.loginForm)
      // .then(() => {
      //   this.$router.push({ path: this.redirect || '/' })
      //   this.loading = false
      // })
      // .catch(() => {
      //   this.loading = false
      // })
      search().then((res)=>{
        
      }).catch((err) => {

      })
    }
  }
}
</script>

<style scoped>
  .tab-container {
    margin: 30px;
  }
</style>
