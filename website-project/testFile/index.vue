<template>
  <!-- 使用 useVirtual 属性开启虚拟滚动 使用虚拟滚动时，必须要固定表格高度和行高 -->
  <div style="height: 100%;width: 100%;overflow: auto">
    <div style="color:red;">pl-table在线预览，更多玩法请看文档哦，欢迎Star</div>
    <div>
        <el-button @click="clearSelection">清除选中</el-button>
        <el-button @click="setData(200)">变化数据为200条</el-button>
        <el-button @click="setData(1000)">变化数据为1000条</el-button>
        <el-button @click="pagingScrollTopLeft(1000)">滚动到1千位置</el-button>
        <el-button @click="pagingScrollTopLeft(2000)">滚动到2千位置</el-button>
    </div>
    <p style="color: red">我是Y轴虚拟</p>
    <pl-table :datas="data.tableData"
              ref="plTable"
              height="300"
              big-data-checkbox
              fixed-columns-roll
              header-drag-style
              show-summary
              :total-option="[{ label: '地址' }]"
              use-virtual
              :row-height="50">
      <template slot="empty">
        没有查询到符合条件的记录
      </template>
      <pl-table-column type="selection" width="55"/>
      <pl-table-column type="index" width="100" fixed/>
      <!--show-overflow-tooltip属性代表超出则内容部分给出提示框-->
      <pl-table-column
              v-for="item in columns"
              :key="item.id"
              :resizable="item.resizable"
              :show-overflow-tooltip="item.showOverflowTooltip"
              :prop="item.prop"
              :label="item.label"
              :fixed="item.fixed"
              :width="item.width"/>
    </pl-table>
    <p style="margin-top: 20px;color: red">我是X + Y轴同时虚拟</p>
    <plx-table-grid :datas="data.tableData"  height="300" ref="plTable2">
      <plx-table-column type="selection" width="55" fixed="left"/>
      <plx-table-column type="index" width="100" fixed="left"/>
      <plx-table-column
              v-for="item in columns2"
              :key="item.id"
              :resizable="item.resizable"
              :prop="item.prop"
              :label="item.label"
              :fixed="item.fixed"
              :width="item.width"/>
    </plx-table-grid>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        columns: [
          {prop: 'date', label: '日期', width: 120},
          {prop: 'address', label: '地址', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '噜噜噜', width: 230, showOverflowTooltip: true},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '地址', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '挖挖掘机挖掘机挖掘机掘机', width: 100},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '噜噜噜', width: 230, showOverflowTooltip: true},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '地址', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '挖挖掘机挖掘机挖掘机掘机', width: 100},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true},
          {prop: 'address', label: '噜噜噜', width: 230, showOverflowTooltip: true},
          {prop: 'address', label: '娃哈哈', width: 100, showOverflowTooltip: true}
        ],
        columns2: Array.from({ length: 500 }, (_, idx) => ({
          prop: 'address', label: '地址' + idx, width: 200, showOverflow: true, sortable: true, fixed: ''
        })),
        data: {
          tableData:Array.from({ length: 2000 }, (_, idx) => ({
            id: idx + 1,
            date: '2016-05-03',
            name: 1,
            ab: '欢迎使用pl-table',
            address: 1 + idx
          }))
        }
      }
    },
    mounted () {
     },
    methods: {
      clearSelection () {
        this.$refs.plTable.clearSelection()
        this.$refs.plTable2.clearSelection()
      },
      setData (num) {
        this.data.tableData = Array.from({ length: num }, (_, idx) => ({
          id: idx + 1,
          date: '2016-05-03',
          name: 1,
          ab: '欢迎使用pl-table',
          address: 1 + idx
        }))
      },
      pagingScrollTopLeft (val) {
         this.$refs.plTable.pagingScrollTopLeft(val, 0)
      }
    }
  }
</script>
<style>
  body, html {
    overflow: auto;
    margin: 0;
    padding: 10px;
    box-sizing: border-box;
    width: 100%;
    height: 100%;
  }
</style>
