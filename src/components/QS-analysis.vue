<!-- <template>
  <div class="data-container">
    <template v-if="!isError">
      <span class="back" @click="goBack()">&lt; 返回</span>
      <h2>{{qsItem.title}}</h2>
    </template>

    <el-col :span="12">
      <h5>数据分析方法</h5>
      <el-menu
        default-active="2"
        class="el-menu-vertical-demo"
        @open="handleOpen"
        @close="handleClose">
        <el-submenu index="1">
          <template slot="title">
            <i class="el-icon-location"></i>
            <span>导航一</span>
          </template>
          <el-menu-item-group>
            <template slot="title">分组一</template>
            <el-menu-item index="1-1">选项1</el-menu-item>
            <el-menu-item index="1-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="1-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="1-4">
            <template slot="title">选项4</template>
            <el-menu-item index="1-4-1">选项1</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-menu-item index="2">
          <i class="el-icon-menu"></i>
          <span slot="title">导航二</span>
        </el-menu-item>
        <el-menu-item index="3" disabled>
          <i class="el-icon-document"></i>
          <span slot="title">导航三</span>
        </el-menu-item>
        <el-menu-item index="4">
          <i class="el-icon-setting"></i>
          <span slot="title">导航四</span>
        </el-menu-item>
      </el-menu>
    </el-col>

    <div class="error" v-if="isError">
      404 Not Found
    </div>
  </div>
</template>

<script src="echarts.min.js"></script>
<script>

import echarts from 'echarts/lib/echarts'
import 'echarts/lib/chart/pie'
import 'echarts/lib/component/tooltip'
import 'echarts/lib/component/toolbox'
/**
 * A module that define qs-data router view
 */
  export default {
    name: 'qsData',
    data() {
      return {
        qsItem: {},
        qsList: [],
        isError: false,
        chartData: [],
        chartNum: [],
        qsChoose: []
      }
    },
    created() {
      this.fetchData()
    },
    mounted() {
      
    },
    methods: {
      fetchData() {
        var that = this;
        $.ajax({  
            type:"get",//type可以为post也可以为get  
            url: "../list/",  
            data:{
            },//这行不能省略，如果没有数据向后台提交也要写成data:{}的形式  
            dataType:"json",//这里要注意如果后台返回的数据不是json格式，那么就会进入到error:function(data){}中  
            async: false,
            success:function(value){ 
              that.qsList = value
              console.log(that.qsList)
              let i = 0;
              for (let length = that.qsList.length; i < length; i++) {
                if (that.qsList[i].num == that.$route.params.num) {
                  that.qsItem = that.qsList[i]
                  break
                }
              }
              if (i === that.qsList.length) that.isError = true                           
            },  
            error:function(value){ 
                alert("问卷数据显示出现错误");  
            } 
        })
      },
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      goBack() {
        this.$router.push({path:'/'})
      }
    }
  } 
</script>

<style>

</style> -->