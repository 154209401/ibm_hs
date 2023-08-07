<template>

<div class="my-table">

        <div ref="mymodal">
    <a-modal :getContainer='()=>$refs.mymodal' v-model:visible="visible" :footer="null" class="display">
      <div>
          
         <img :src="imgs[currentImgIndex]" alt="1233" class="displayImg">
         

      </div>
     
    </a-modal>
        </div>
    <!-- <a-alert
      message="Outline"
      description="Total phosphorus 、Total nitrogen 、dissolved oxyge"
      type="error"
    /> -->
    <a-table :columns="columns" 
    :data-source="table_data" 
    :pagination="pagination"
    style="padding: 2vw;"
    :bordered="false"   > 
    <template #bodyCell="{ column, text }">
    <template v-if="column.dataIndex === 'name'">
    <a>{{ text }}</a>
    </template>
    </template>
    </a-table>
        
   
    
</div>
</template>

<script lang='ts'>
import { defineComponent, ref} from 'vue';
import {total2} from '@/assets/data/area2/total2'
import {pictureIndex} from '../../util/getUrl'

const table_data = total2;
const visible = ref<boolean>(false);
const picture_title=ref <string>('')





export default defineComponent({
  
  
    setup(){
      const currentImgIndex = ref<number>(4)
      const imgs=[
          require("@/assets/imgs/area2/1Chemicaloxygendemand.png"),

          require("@/assets/imgs/area2/2dissolvedoxyen.png"),

          require("@/assets/imgs/area2/3Dissolvedtotalorganiccarbon.png"),

          require("@/assets/imgs/area2/4PH.png"),

          require("@/assets/imgs/area2/5phosphate.png"),

          require("@/assets/imgs/area2/6silicate.png"),

          require("@/assets/imgs/area2/7Totalnitrogen.png"),

          require("@/assets/imgs/area2/8Totalphosphorus.png"),
        ]
     
      const showPicture = (column: any) => {
            return {
              onClick: () => {
               currentImgIndex.value=pictureIndex(column.key)
                picture_title.value = column.key 
                visible.value = true;
                
                //console.log(currentImgIndex)
                
              }
            };
          }
      
      const columns = [{
    title: 'Record date',
    dataIndex: 'record_date',
  },
  {
    title: 'Chemical oxygen demand',
    dataIndex: 'Chemical oxygen demand',
    customHeaderCell: showPicture
  },
  {
    title: 'Dissolved oxygen',
    dataIndex: 'dissolved oxygen',
    customHeaderCell: showPicture
  },
  {
    title: 'Dissolved total organic carbon',
    dataIndex: 'Dissolved total organic carbon',
    customHeaderCell: showPicture
  },
  {
    title: 'PH',
    dataIndex: 'PH',
    customHeaderCell: showPicture
  },
  {
    title: 'Phosphate',
    dataIndex: 'phosphate',
    customHeaderCell: showPicture
  },
  {
    title: 'Silicate',
    dataIndex: 'silicate',
    customHeaderCell: showPicture
  },
  {
    title: 'Total nitrogen',
    dataIndex: 'Total nitrogen',
    customHeaderCell: showPicture
  },
  {
    title: 'Total phosphorus',
    dataIndex: 'Total phosphorus',
    customHeaderCell: showPicture
  },
]
     
      const showModal = () => {
      visible.value = true;
    }
      
        return{
            table_data,
            columns,
            pagination: {
                pageSize: 6 // 每页显示 5 行数据
            },
            visible,
            showModal,
            picture_title,
            currentImgIndex,
            imgs
            
            
            
           
        }
    }
})

</script>

<style scoped>
/deep/ .ant-modal-content {
    background-color: transparent!important;
}
/deep/ .ant-modal-body {
    padding: 0px!important;

}
/deep/ .ant-table-thead {
   height: 5.18vh;
}
.display{
  width: 100%;
  max-width: 100%;
  max-height: 100%;
  overflow: auto;
}

.displayImg{
  width: 100%;
  height: auto;
  max-width: 100%;
  max-height: 100%;
}
/deep/ .ant-table-bordered .ant-table-thead > tr > th, .ant-table-bordered .ant-table-tbody > tr > td {
  border: 0px!important;
}
/deep/ .ant-table-bordered .ant-table-tbody > tr > td {
    border-right: 0px!important;
}
/deep/  .ant-table{
  width: 100%;
  color: #fff;
  background: transparent !important;
}
/deep/ .ant-table-thead > tr > th, .ant-table-tbody > tr > td {
  padding: 0 0.83vw;
}
/deep/ .ant-pagination-next .ant-pagination-item-link {
  background-color: transparent;
 border-color:#6cefc6;
 color:#fff;
}
/deep/ .ant-pagination-prev .ant-pagination-item-link{
 background-color: transparent;
 border-color:#6cefc6;
 color:#fff;
}
/deep/ .ant-pagination-item {
 background-color: transparent;
  border-color:#6cefc6;
}
/deep/ .ant-pagination-item a {
  color:#fff;
}
/deep/ .ant-pagination-jump-next .ant-pagination-item-container .ant-pagination-item-ellipsis {
  color:#fff
}
/deep/ .ant-table {
  height: 28vh;
}
/deep/ .ant-table-thead > tr > th {
color:#6cefc6;
background-color: transparent;
border-bottom:1px solid #40a8c3;
}
/deep/ .ant-table-tbody > tr >td {
  padding:0px;
  padding-left:0.78vw;
   height: 3.33vh;
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
  background: url('../../assets/imgs/juxing.png') no-repeat;
  background-size: 100% 100%;
}
</style>