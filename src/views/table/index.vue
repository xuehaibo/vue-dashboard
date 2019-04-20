<template>
  <div class="app-container">
    <!-- <el-table
      v-loading="listLoading"
      :data="list"
      element-loading-text="Loading"
      border
      fit
      highlight-current-row>
      <el-table-column align="center" label="ID" width="95">
        <template slot-scope="scope">
          {{ scope.$index }}
        </template>
      </el-table-column>
      <el-table-column label="Title">
        <template slot-scope="scope">
          {{ scope.row.title }}
        </template>
      </el-table-column>
      <el-table-column label="Author" width="110" align="center">
        <template slot-scope="scope">
          <span>{{ scope.row.author }}</span>
        </template>
      </el-table-column>
      <el-table-column label="Pageviews" width="110" align="center">
        <template slot-scope="scope">
          {{ scope.row.pageviews }}
        </template>
      </el-table-column>
      <el-table-column class-name="status-col" label="Status" width="110" align="center">
        <template slot-scope="scope">
          <el-tag :type="scope.row.status | statusFilter">{{ scope.row.status }}</el-tag>
        </template>
      </el-table-column>
      <el-table-column align="center" prop="created_at" label="Display_time" width="200">
        <template slot-scope="scope">
          <i class="el-icon-time"/>
          <span>{{ scope.row.display_time }}</span>
        </template>
      </el-table-column>
    </el-table> -->
    <el-table
    :data="tableData"
    height="250"
    border
    style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
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
import { getList } from '@/api/table'
import axios from 'axios'

export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        published: 'success',
        draft: 'gray',
        deleted: 'danger'
      }
      return statusMap[status]
    }
  },
  data() {
    return {
      list: null,
      listLoading: true,
      tableData:[
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
        {
          date: '2016-05-03',
          ch: '王小虎',
          pv: '1000',
          uv: '500',
          version: 'v1.1.0'
        },
      ]
    }
  },
  created() {
    this.fetchData()
    // 请求
    // axios.post('',{
    //   date:''
    // }).then((res) => {
    //   console.log(res)
    // }).catch((err) => {
    //   console.log(err)
    // })

  },
  methods: {
    fetchData() {
      this.listLoading = true
      getList(this.listQuery).then(response => {
        this.list = response.data.items
        this.listLoading = false
      })
    }
  }
}
</script>
