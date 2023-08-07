<template>
  <div class="back-pc">
    <!-- <div style="width:100%;padding:0 9.79vw;margin:0 auto"> -->
  <a-form
    layout="inline"
    style="padding: 0.925vh 5vw 0px;margin:0 auto;margin-bottom:0.925vh;font-size:1.04vw"
  >
    <a-form-item label="Type:">
      <a-select
      style="width:14.58vw;height:4.33vh"
      placeholder="Select Type">

      </a-select>
    </a-form-item>
    <a-form-item label="Area:">
      <a-select
      style="width:14.58vw"
      placeholder="Select  Area">
      </a-select>
    </a-form-item>
    <a-form-item label="Theme:">
      <a-input placeholder="Search Theme" style="width:14.58vw;"></a-input>
    </a-form-item>
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        style="width:5.2vw;font-size:1.04vw"
      >
        Search
      </a-button>
    </a-form-item>
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        style="width:5.2vw;font-size:1.04vw"
      >
        Reset
      </a-button>
    </a-form-item>
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        style="width:10.7vw;font-size:1.04vw"
      >
        Publish information
      </a-button>
    </a-form-item>
    

  </a-form>
  <!-- </div> -->
<div style="width:100%;padding:0 20px">
  <div class="tableImg">
      <a-table :columns="columns" :pagination="pagination" :data-source="data"  :bordered='false' style="padding: 2vw;"  > 
    <template #bodyCell="{ column, text }">
      <template v-if="column.dataIndex === 'name'">
        <a>{{ text }}</a>
      </template>
    </template>
  </a-table>
  </div>
</div>
  </div>
 
</template>
<script lang="ts">
import { defineComponent } from 'vue';

const columns = [
  {
    title: 'Index',
    dataIndex: 'Index',
  },
  {
    title: 'Date',
    dataIndex: 'Date',
  },
  {
    title: 'Theme',
    dataIndex: 'Theme',
  },
  {
    title: 'Type',
    dataIndex: 'Type',
  },
  {
    title: 'Area',
    dataIndex: 'Area',
  },
  {
    title: 'Describe',
    dataIndex: 'Describe',
  },
  {
    title: 'Contact information',
    dataIndex: 'Contact',
  },
];

const data = [
  {
    key: '1',
    Index: '1',
    Date: '2023/06/20',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 152xxxx2828'
    
  },
    {
    key: '2',
    Index: '2',
    Date: '2023/06/21',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 138xxxx2828'
    
  },
     {
    key: '3',
    Index: '3',
    Date: '2023/06/22',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 197xxxx6356'
    
  },
     {
    key: '4',
    Index: '4',
    Date: '2023/06/23',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 166xxxx5758'
    
  },
     {
    key: '5',
    Index: '5',
    Date: '2023/06/24',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 188xxxx7700'
    
  },
     {
    key: '6',
    Index: '6',
    Date: '2023/06/25',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 153xxxx9044'
    
  },
     {
    key: '7',
    Index: '7',
    Date: '2023/06/26',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 155xxxx3828'
    
  },
     {
    key: '8',
    Index: '8',
    Date: '2023/06/27',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 138xxxx2000'
    
  },
      {
    key: '9',
    Index: '9',
    Date: '2023/06/21',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 138xxxx2828'
    
  },
     {
    key: '10',
    Index: '10',
    Date: '2023/06/22',
    Theme: 'Low oxygen content',
    Type: 'technical support',
    Area: 'Chaohu Lake',
    Describe: 'Low oxy',
    Contact :'+86 197xxxx6356'
    
  }
];

export default defineComponent({
  setup() {
    return {
      data,
      columns,
       pagination: {
                pageSize: 20 // 每页显示 5 行数据
            },
    };
  },
});
</script>
<style scoped>
th.column-money,
td.column-money {
  text-align: right !important;
}
/deep/ .ant-form-item-label > label {
  color:#07FCFF;
  font-size:1.04vw;
}
/deep/ .ant-select-single .ant-select-selector .ant-select-selection-placeholder {
  font-size:1.04vw;
}
/deep/ .ant-select:not(.ant-select-customize-input) .ant-select-selector {
    background-color: #2c3757;
    border: 1px solid #07FCFF;
}
/* /deep/ .ant-select-selection-placeholder {
      color:#fff;
} */
/deep/  .ant-select-arrow {
  color:#07FCFF
}
/deep/ .ant-input {
background-color: #2c3757;
    border: 1px solid #07FCFF;
}
/deep/ .ant-table-bordered .ant-table-thead > tr > th, .ant-table-bordered .ant-table-tbody > tr > td {
  border: 0px!important;
}
/deep/ .ant-table-bordered .ant-table-tbody > tr > td {
    border-right: 0px!important;
}
.tableImg {
   background: url('../assets/imgs/33.png') no-repeat;
  background-size: 100% 100%;
}
/deep/  .ant-table{
  width: 100%;
  color: #fff;
  height: 60vh;
  background: transparent !important;
}
/deep/ .ant-table-thead > tr > th {
color:#07FCFF;
background-color: transparent;
border-bottom:1px solid #40a8c3;
}
/deep/ .ant-table-tbody > tr >td {
  padding:0px;
  padding-left:15px;
   height: 32px;
   border-bottom:1px solid #40a8c3;
}
/* /deep/ .ant-table-tbody > tr:hover >td:first-child {
 border-left:1px solid #6cefc6;
}
/deep/ .ant-table-tbody > tr:hover >td:last-child {
 border-right:1px solid #6cefc6;
} */
/deep/ .ant-table-tbody > tr:hover >td {
  background-color: transparent!important;
  border-bottom:0px;
  border-top:0px;
}
/deep/ .ant-table-tbody > tr:hover {
  background: url('../assets/imgs/juxing.png') no-repeat;
  background-size: 100% 100%;
}
/deep/ .ant-pagination-next .ant-pagination-item-link {
  background-color: transparent;
 border-color:#07FCFF;
 color:#fff;
}
/deep/ .ant-pagination-prev .ant-pagination-item-link{
 background-color: transparent;
 border-color:#07FCFF;
 color:#fff;
}
/deep/ .ant-pagination-item {
 background-color: transparent;
  border-color:#07FCFF;
}
/deep/ .ant-pagination-item a {
  color:#fff;
}
/deep/ .ant-pagination-jump-next .ant-pagination-item-container .ant-pagination-item-ellipsis {
  color:#fff
}
</style>