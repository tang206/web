<template>
    <el-container>
  <el-header style="font-size: 40px; background-color: rgb(238, 241, 246)">Quiz后台管理</el-header>
  <el-container>
    
    <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
    <el-menu :default-openeds="['1', '3']">
      <el-submenu index="1">
        <template slot="title">管理选项</template>
        <el-menu-item-group>
          <el-menu-item index="1-1">
            <router-link to="/user">用户管理</router-link>    
        </el-menu-item>
          <el-menu-item index="1-2">
            <router-link to="/question">题目管理</router-link>
          </el-menu-item>
        </el-menu-item-group>
        
      </el-submenu>
      
    </el-menu>
  </el-aside>

    <el-main>
        <el-form :inline="true" :model="formInline" class="demo-form-inline">
  <el-form-item label="题目">
    <el-input v-model="formInline.user" placeholder="请输入题目关键词"></el-input>
  </el-form-item>
  
  <el-form-item>
    <el-button type="primary" @click="onSubmit">查询</el-button>
  </el-form-item>

  <el-form-item>
    <el-button type="success" @click="onAddNewQuestion">添加题目</el-button>
  </el-form-item>
</el-form>

     <el-table
    :data="tableData"
    style="width: 100%">
    <el-table-column
      label="序号"
      width="180">
      <template slot-scope="scope">
        <span style="margin-left: 10px">{{ scope.row.id }}</span>
      </template>
    </el-table-column>
    <el-table-column
      label="题目"
      width="180">
      <template slot-scope="scope">
          <div slot="reference" class="name-wrapper">
            <span style="margin-left: 10px">{{ scope.row.question }}</span>
          </div>
      </template>
    </el-table-column>

    <el-table-column
      label="选项"
      width="260">
      <template slot-scope="scope">
        <span style="margin-left: 10px">{{ scope.row.option }}</span>
      </template>
    </el-table-column>

    <el-table-column
      label="答案"
      width="180">
      <template slot-scope="scope">
        <span style="margin-left: 10px">{{ scope.row.answer }}</span>
      </template>
    </el-table-column>

    <el-table-column label="操作">
      <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">删除</el-button>
      </template>
    </el-table-column>
  </el-table>

    <br />

    <el-pagination
  background
  layout="prev, pager, next"
  :total="1000">
</el-pagination>

    <el-dialog title="添加新题目" :visible.sync="dialogFormVisible">
  <el-form :model="form">
    <el-form-item label="题目" :label-width="formLabelWidth">
      <el-input v-model="form.question" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="选项A" :label-width="formLabelWidth">
      <el-input v-model="form.optionA" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="选项B" :label-width="formLabelWidth">
      <el-input v-model="form.optionB" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="选项C" :label-width="formLabelWidth">
      <el-input v-model="form.optionC" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="选项D" :label-width="formLabelWidth">
      <el-input v-model="form.optionD" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="正确答案" :label-width="formLabelWidth">
      <el-input v-model="form.answer" autocomplete="off"></el-input>
    </el-form-item>
    
  </el-form>
  <div slot="footer" class="dialog-footer">
    <el-button @click="dialogFormVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
  </div>
</el-dialog>
    </el-main>
  </el-container>
</el-container>
</template>

<script>
export default {
    data() {
      return {
        dialogFormVisible: false,

        form: {
          question: '',
          optionA: '',
          optionB: '',
          optionC: '',
          optionD: '',
          answer: '',
        
        },

        formInline: {
          user: '',
          region: ''
        },
        tableData: [{
          id: '1',
          question: '巴黎首都是哪个城市',
          option: '巴黎，巴黎，巴黎，巴黎',
          answer: '巴黎'
        }, {
          id: '2',
          question: '伦敦首都是哪个城市',
          option: '伦敦，伦敦，伦敦，伦敦',
          answer: '伦敦'
         
        }, {
          id: '3',
          question: '纽约是哪个国家的首都',
          option: '纽约，纽约，纽约，纽约',
          answer: '纽约'
        }, {
          id: '4',
          question: '东京是哪个国家的首都',
          option: '东京，东京，东京，东京',
          answer: '东京'
        }]
      }
    },
    methods: {
      onSubmit() {
        console.log('submit!');
      },
      onAddNewQuestion() {
        this.dialogFormVisible = true;
      },
      handleEdit(index, row) {
        console.log(index, row);
      },
      handleDelete(index, row) {
        console.log(index, row);
      }
    }
}
</script>

<style>

    /* .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  } */
 
</style>