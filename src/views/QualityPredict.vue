<template>
<div class='back-pc'>
 <div class="dituImg">
  <div class="sousuo">
    <div class="wenben" v-if="weizhi==='1'">
      <p style="color:#6cefc6;font-size:0.625vw">119.85°E~120.6°E/30.93°N~31.53°N</p>
    </div>
    <div class="wenben" v-if="weizhi==='2'">
      <p style="color:#6cefc6;font-size:0.625vw;margin-left:1vw">87.0°W~87.5°W/41.6°N~42.5°N</p>
    </div>
    <div class="shurukuang">
             <a-form
    layout="inline"     
  >
    <a-form-item>
      <a-select
        v-model:value="aera_id"
        show-search
        placeholder="Select or search an aera"
        style="width: 15.10vw"
        :options="options"
        @change="handleChange"
        allowClear
        
      ></a-select>
    </a-form-item>
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        style="width:5.2vw;background-color:#318DCE"
        @click="handleSearch"
      >
        Search
      </a-button>
    </a-form-item>
    <a-form-item>
      <a-button
        type="primary"
        html-type="submit"
        @click="handleReset"
        style="background-color:#1A4768;width:5.2vw;border-color:#318DCE"
      >
        Reset
      </a-button>
      
    </a-form-item>
    <!-- <a-form-item>
      <Transition>
    <a-input v-model:value="region" 
    placeholder="Region(latitude and longitude)" 
    readonly style="width: 200px;"
    v-show="show"
    ></a-input>
  </Transition>
    </a-form-item> -->
  </a-form>
    </div>
  </div>
</div>
   <div class="bottom-fixed">
    <div class="bottomkuang1">
          <div class="bottomkuang1-1"></div>
          <div class="bottomkuang1-2" v-if="weizhi===''"></div>
          <div class="bottomkuang1-3" v-if="weizhi!==''">
            <div class="wenbenyu"><p>Total phosphorus</p></div>
            <div class="wenbenyu"><p>Total nitrogen</p></div>
            <div class="wenbenyu wenbenyu1"><p>dissolved oxyge</p></div>
            <div class="wenbenyu" style="border:0px; background-color:transparent"></div>
          </div>
    </div>
    <div class="bottomkuang2">
      <div class="bottomkuang2-2" v-if="weizhi===''"></div>
      <TabPage :aera_id ='aera_id' v-show='show'/>
    </div>
  </div> 
</div> 

</template>
<script lang="ts">
//import type { SelectProps } from 'ant-design-vue';
import { notification } from 'ant-design-vue';
import { defineComponent, ref } from 'vue';
import TabPage from './TabPage.vue';
export default defineComponent({
  components:{
    TabPage
  },
  setup() {
    const weizhi = ref('');
    const aera_id = ref('')
    const show = ref(false);
    const region=ref('') 
    const options =([
      { value: '1', label: 'TaiHu' },
      { value: '2', label: 'Lake Illinois' },
  
    ]);
    const handleChange = (value: string) => {
      //console.log(`selected ${value}`);
      show.value = false;
      weizhi.value = '';
      if(value === '1'){
         region.value = '119.85°E~120.6°E/30.93°N~31.53°N';
         weizhi.value = ''
      }
      else{
        region.value = '87.0°W~87.5°W/41.6°N~42.5°N';
        weizhi.value = '';
      }
    };
    const handleSearch = () =>{
      if(aera_id.value=='1' ||aera_id.value=='2' ){
        show.value = true
        if(aera_id.value=='1'){
           weizhi.value = '1'
        }else if(aera_id.value=='2'){
           weizhi.value = '2'
        }
      }
      else{
        notification.open({
        message: 'Please Select or search an aera',
        description:
          '',
      });
      }
    }
    const handleBlur = () => {
      //console.log('blur');
    };
    const handleFocus = () => {
      //console.log('focus');
    };
    const handleReset =() =>{
      aera_id.value = ''
      show.value = false;
      weizhi.value = '';
    }
    // const filterOption = (input: string, option: any) => {
    //   return option.value.toLowerCase().indexOf(input.toLowerCase()) >= 0;
    // };
    return {
      weizhi,
      aera_id,
      handleBlur,
      handleFocus,
      handleChange,
      options,
      show,
     
      handleReset,
      handleSearch,
      region 
    };
  },
});
</script>

<style scoped>
.dituImg {
  position: relative;
   margin:0 auto;
  width: 98%;
  height: 34.81vh;
 background: url('../assets/imgs/ditu.png') no-repeat;
  background-size: 100% 100%;
}
.sousuo {
  position: relative;
  position: absolute;
  bottom:0px;
  left:26.97vw;
  width: 42.86vw;
  height: 10.83vh;
  background: url('../assets/imgs/sousuokuang.png') no-repeat;
  background-size: 100% 100%;
}
.shurukuang {
 position: absolute;
 bottom: 0px;
 left:8.125vw;
}
.wenben {
   position: absolute;
 top: 1.25vh;
 left:14.2vw;
  width: 10.625vw;
  height: 7.777vh;
}
/deep/ .ant-select:not(.ant-select-customize-input) .ant-select-selector {
    background-color: #2c3757;
    border: 1px solid #48a789;
    color:#fff;
}
/* /deep/ .ant-select-selection-placeholder {
      color:#fff;
} */
/deep/  .ant-select-arrow {
  color:#6cefc6
}
.bottom-fixed {
  margin:0 auto;
  margin-top: 2vh;
  width: 98%;
  height: 40vh;
}
.bottomkuang1 {
  float: left;
  display: flex;
 flex-direction: column;
  justify-content: center;
  align-items: center;
  /* position: absolute;
  left:10px;
  bottom: 0px; */
  width: 25%;
  margin-left:10px;
  height: 40vh;
   background: url('../assets/imgs/bottom1.png') no-repeat;
  background-size: 100% 100%;
}
.bottomkuang1-1 {
  width: 180px;
  height: 30px;
  background: url('../assets/imgs/outline.png') no-repeat;
  background-size: 100% 100%;
  margin-top:-10px;
  margin-bottom: 10px;
}
.bottomkuang1-2 {
  width: 200px;
  height: 160px;
  background: url('../assets/imgs/wushuju.png') no-repeat;
  background-size: 100% 100%;
}
.bottomkuang1-3 {
  height: 160px;
  width: 300px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
.bottomkuang2 {
  float: left;
  margin-left:1.5625vw;
  /* position: absolute;
  left:500px;
  bottom: 0px; */
  width: 69.89vw;
  height: 40vh;
   background: url('../assets/imgs/bottom2.png') no-repeat;
  background-size: 100% 100%;
}
.wenbenyu {
  flex-basis: 45%;
  line-height: 32px;
  text-align: center;
  border:1px solid #2AF0FD;
  border-radius: 2px;
  background-color: #2890FA;
  width: 80px;
  margin-left: 10px;
  height: 32px;
  color:#2AF0FD ;
  font-size: 14px;
  font-weight: bold;
}
.wenbenyu1 {
  margin-top:-60px;
}
.bottomkuang2-2 {
  margin-top: 8.77vh;
  margin-left: 23.83vw;
  width: 20.79vw;
  height: 26.22vh;
  background: url('../assets/imgs/wushuju.png') no-repeat;
  background-size: 100% 100%;
}
</style>