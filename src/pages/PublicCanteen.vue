<template>
  <div class="q-pa-md">
    <CanteenTitleSection v-bind="canteenData" />
  </div>
  <div class="q-pa-lg">
    <CanteenBasicDetailSection v-bind="canteenData" />
  </div>
  <div class="q-ma-lg">
    <CanteenIntroSection v-bind="canteenData" />
  </div>
  <div class="q-ma-lg">
    <CanteenStallSection v-bind="canteenData" />
  </div>
</template>

<script>
import { defineComponent, ref, getCurrentInstance } from "vue";
import axios from "axios";
import CanteenBasicDetailSection from "components/CanteenPage/CanteenBasicDetailSection";
import CanteenIntroSection from "components/CanteenPage/CanteenIntroSection";
import CanteenTitleSection from "components/CanteenPage/CanteenTitleSection";
import CanteenStallSection from "components/CanteenPage/CanteenStallSection";
import { watch, watchEffect } from 'vue';
import {useRoute} from 'vue-router'

export default defineComponent({
  name: "PublicCanteen",
  components: {
    CanteenStallSection,
    CanteenTitleSection,
    CanteenIntroSection,
    CanteenBasicDetailSection,
  },

  data(){
    return{
      id:""
    }
  },

  // watch:{
  //   "$route":
  //     function(){
  //     this.id=this.$route.query.canteenName
  //     console.log("change",this.$route.query.canteenName)
  //
  //
  //   }
  // },
  setup() {
    // watch(this.$route.query.canteenName,()=>{
    //   //this.canteenid=this.$route.query.id
    //   console.log("change",this.$route.query.canteenName)
    //
    // })
    const route=useRoute();
    const canteenData = ref({});
    // const getCanteenData = async () => {
    //   const response = await axios.get("http://localhost:3000/canteenData");
    //   canteenData.value = response.data;
    //   console.log(canteenData)
    // };
    // getCanteenData();
    //
    watch(()=>route.query,()=>{
      console.log(route.query)
    },{
      immediate:true
    })
    return {
      canteenData,
    };

  },

});
</script>
