<script setup>

  import {ref} from "vue";

  let queryInput = ref ("")
  let tableData = ref ([
      {
    date: '2016-05-03',
    name: 'Tom',
    state: 'California',
    city: 'Los Angeles',
    address: 'No. 189, Grove St, Los Angeles',
    zip: 'CA 90036',
    tag: 'Home',
  },
    {
      date: '2016-05-02',
      name: 'Tom',
      state: 'California',
      city: 'Los Angeles',
      address: 'No. 189, Grove St, Los Angeles',
      zip: 'CA 90036',
      tag: 'Office',
    },
    {
      date: '2016-05-04',
      name: 'Tom',
      state: 'California',
      city: 'Los Angeles',
      address: 'No. 189, Grove St, Los Angeles',
      zip: 'CA 90036',
      tag: 'Home',
    },
    {
      date: '2016-05-01',
      name: 'Tom',
      state: 'California',
      city: 'Los Angeles',
      address: 'No. 189, Grove St, Los Angeles',
      zip: 'CA 90036',
      tag: 'Office',
    }])
  let multipleSelection = ref ([])
  let dialogFormVisible = ref(false)
  let tableForm = ref (
      {
        name:'',
        email:"",
        address:""
      }
  )
const handleRowClick = () => {
    console.log('click')
}

  const handleSelectionChange = (val) => {
    multipleSelection.value = val
    console.log(val)
  }

  const handleAdd = () =>{
    dialogFormVisible.value = true
  }

</script>

<template>
  <div class="table-box">
    <!-- title   -->
    <div class="title">
      <h2> Easy demo</h2>
    </div>
<!-- query   -->
    <div class="query-box">
<!-- input-->
      <el-input v-model="queryInput" style="width: 240px" placeholder="请输入姓名搜索" />
<!-- button-->
      <el-button type="primary" @click="handleAdd">增加</el-button>
    </div>
    <div>

    </div>
    <el-table
        border
        ref="multipleTableRef"
        :data="tableData"
        style="width: 100%"
        @selection-change="handleSelectionChange"
    >
      <el-table-column type="selection" width="55" />
      <el-table-column fixed prop="date" label="Date" width="150" />
      <el-table-column prop="name" label="Name" width="120" />
      <el-table-column prop="state" label="State" width="120" />
      <el-table-column prop="city" label="City" width="120" />
      <el-table-column prop="address" label="Address" width="600" />
      <el-table-column prop="zip" label="Zip" width="120" />
      <el-table-column fixed="right" label="Operations" width="120">
        <template #default>
          <el-button link type="primary" size="small" @click="handleRowClick">Detail</el-button>
          <el-button link type="primary" size="small">Edit</el-button>
        </template>
      </el-table-column>
    </el-table>

<!--dialog-->
    <el-dialog v-model="dialogFormVisible" title="Shipping address" width="500">
      <el-form :model="tableForm">
        <el-form-item label="请输入姓名" :label-width="60">
          <el-input v-model="tableForm.name" autocomplete="off" />
        </el-form-item>
        <el-form-item label="请输入邮箱" :label-width="60">
          <el-input v-model="tableForm.email" autocomplete="off" />
        </el-form-item>
        <el-form-item label="请输入地址" :label-width="60">
          <el-input v-model="tableForm.address" autocomplete="off" />
        </el-form-item>
      </el-form>
      <template #footer>
        <div class="dialog-footer">
          <el-button type="primary" @click="dialogFormVisible = false">
            确认
          </el-button>
        </div>
      </template>
    </el-dialog>
  </div>
</template>

<style scoped>
.table-box{
  width:800px;
  position: absolute;
  top: 30%;
  left: 30%;
  treansform: translate(-50%,-50%);
}
.title{
  text-algin:center;
}
.query-box{
  display: flex;
  justify-content: space-between;
}
.el-input{
  width:
}
</style>
