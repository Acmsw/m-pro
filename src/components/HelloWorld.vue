<template>
  <div class="hello">
    <div class="block">
      <el-cascader
        v-model="value"
        :options="options"
        @change="handleChange"
        :props="props"
      ></el-cascader>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        options:[],
        value:"",
        props:{
          value:"bigRegionCode",
          label:"bigRegionName",
          children:"children"
        },
        bigRegion:[
          {
            bigRegionCode:"rs1",
            bigRegionName:"东北",
            smallRegionCode:"",
            smallRegionName:"",
              jsjsjs:""
          },
          {
            bigRegionCode:"rs2",
            bigRegionName:"华北",
            smallRegionCode:"",
            smallRegionName:"",
          },
          {
            bigRegionCode:"rs3",
            bigRegionName:"西北",
            smallRegionCode:"",
            smallRegionName:"",
          },
          {
            bigRegionCode:"rs4",
            bigRegionName:"华东",
            smallRegionCode:"",
            smallRegionName:"",
          },
          {
            bigRegionCode:"rs5",
            bigRegionName:"华中",
            smallRegionCode:"",
            smallRegionName:"",
          },
          {
            bigRegionCode:"rs6",
            bigRegionName:"华南",
            smallRegionCode:"",
            smallRegionName:"",
          }
        ],
        smallRegion:[
          {
            bigRegionCode:"rs1",
            bigRegionName:"东北",
            smallRegionCode:"rs11",
            smallRegionName:"吉林"
          },
          {
            bigRegionCode:"rs1",
            bigRegionName:"东北",
            smallRegionCode:"rs12",
            smallRegionName:"辽宁"
          }
        ],
      }
    },
    mounted(){
      this.initRegion();
    },
    methods: {
      initRegion(){
        this.bigRegion.map(item=>{
          this.$set(item,"bigRegionName",item.bigRegionName);
          this.$set(item,"children",[])
        })
        this.options = this.bigRegion
      },
      handleChange(val) {
        let value = val[0];
         this.options.map(item=>{
           if(item.bigRegionCode == value){
             var smallRegionArr=[];
              this.smallRegion.map(item1=>{
                // console.log(JSON.parse(item1.smallRegionName))
                delete item1.bigRegionCode
                delete item1.bigRegionName
                this.$set(item.children,"smallRegionName",item1.smallRegionName)
                // console.log(item.children)
                return smallRegionArr.push(item1)
              })
             // console.log(smallRegionArr)
             this.$set(item.children,"smallRegionName",smallRegionArr.smallRegionName)
             console.log(item.children);
           }

        })

      }
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
