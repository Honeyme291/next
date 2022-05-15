<template style="height: 100%">
 <div>
   <el-container style="height: 100%; border: 1px solid #eee">
     <el-aside width="200px" style="background-color: rgb(238, 241, 246);height: 100%" >
       <el-menu :default-openeds="['1', '3']" background-color="rgb(48,65,86)"
       text-color="#fff" active-text-color="#ffd04b"
                @select="handSelect"
       >
         <div style="height: 100px;line-height: 100px;text-align: center">
           <b>lxx is handsome</b>
         </div>
         <el-submenu index="1">
           <template slot="title"><i class="el-icon-message"></i>导航一</template>
           <el-menu-item-group>
             <template slot="title">分组一</template>
             <el-menu-item index="1-1">选项1</el-menu-item>
             <el-menu-item index="1-2">选项2</el-menu-item>
           </el-menu-item-group>
         </el-submenu>
         <el-submenu index="2">
           <template slot="title"><i class="el-icon-menu"></i>导航二</template>
           <el-menu-item-group>
             <template slot="title">分组一</template>
             <el-menu-item index="2-1">选项1</el-menu-item>
             <el-menu-item index="2-2">选项2</el-menu-item>
           </el-menu-item-group>
           <el-menu-item-group title="分组2">
             <el-menu-item index="2-3">选项3</el-menu-item>
           </el-menu-item-group>
           <el-submenu index="2-4">
             <template slot="title">选项4</template>
             <el-menu-item index="2-4-1">选项4-1</el-menu-item>
           </el-submenu>
         </el-submenu>
         <el-submenu index="3">
           <template slot="title"><i class="el-icon-setting"></i>导航三</template>
           <el-menu-item-group>
             <template slot="title">分组一</template>
             <el-menu-item index="3-1">选项1</el-menu-item>
             <el-menu-item index="3-2">选项2</el-menu-item>
           </el-menu-item-group>
           <el-menu-item-group title="分组2">
             <el-menu-item index="3-3">选项3</el-menu-item>
           </el-menu-item-group>
           <el-submenu index="3-4">
             <template slot="title">选项4</template>
             <el-menu-item index="3-4-1">选项4-1</el-menu-item>
           </el-submenu>
         </el-submenu>
       </el-menu>
     </el-aside>

     <el-container>
       <el-header style=" font-size: 12px;line-height: 60px;display: flex " >
         <div style="flex: 1;font-size: 18px">
           <span class="collapseBtnClass" style="cursor: pointer" @click="collapse"></span>
         </div>
         <el-dropdown style="width: 100px;cursor: pointer">
           <span>王小虎</span><i class="el-icon-arrow-down" style="margin-left: 15px"></i>
           <el-dropdown-menu slot="dropdown">
             <el-dropdown-item>个人信息</el-dropdown-item>
             <el-dropdown-item>退出</el-dropdown-item>
           </el-dropdown-menu>
         </el-dropdown>
       </el-header>

       <el-main>
         <div style="padding: 10px ">
           <el-input style="width: 200px" placeholder="请输入名称" suffix-icon="el-icon-search" v-model="user.name" ></el-input>
           <el-input style="width: 200px" placeholder="请输入邮箱" suffix-icon="el-icon-message" v-model="user.email" ></el-input>
           <el-input style="width: 200px" placeholder="请输入地址" suffix-icon="el-icon-map-location" v-model="user.address" ></el-input>
           <el-button type="primary">搜索</el-button>
         </div>
         <div>
           <el-button type="primary" >新增<i class="el-icon-circle-plus-outline"></i></el-button>
           <el-button type="danger">批量删除<i class="el-icon-remove-outline"></i></el-button>
           <el-button type="primary" >导入<i class="el-icon-circle-plus-outline"></i></el-button>
           <el-button type="primary" >导出<i class="el-icon-remove-outline"></i></el-button>
         </div>
         <el-table :data="tableData" border stripe>
           <el-table-column prop="date" label="日期" width="140">
           </el-table-column>
           <el-table-column prop="name" label="姓名" width="120">
           </el-table-column>
           <el-table-column prop="address" label="地址">
           </el-table-column>
           <el-table-column>
             <template slot-scope="scope">
               <el-button type="warning" >编辑</el-button>
               <el-button type="danger">删除</el-button>
             </template>
           </el-table-column>
         </el-table>
         <div style="padding: 10px">
         <el-pagination
             background
             :page-sizes="[5,10,15,20]"
             :page-size="10"
             layout="total,sizes,prev, pager, next,jumper"
             :total="400">
         </el-pagination>
         </div>
       </el-main>
     </el-container>
   </el-container>
 </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data() {
    const item = {
      date: '2016-05-02',
      name: '王小虎',
      address: '上海市普陀区金沙江路 1518 弄'
    };
    return {
      tableData: Array(10).fill(item),
      collapseBtnClass:'el-icon-s-fold',
      isCollapse:false,
      activeIndex:1,
      user: {
        email: '',
        name: '',
        address:''
      }

    }
  },
  methods:{
    collapse(){

    },
    handSelect(key,keyPath){
      console.log(key,keyPath)
      this.$router.push(key);
    }
  }
}
</script>
