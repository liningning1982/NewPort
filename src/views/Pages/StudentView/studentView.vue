<template>
 <el-card class="containner">
    <el-card class="box-card">
      <div class="select-container">
      <el-select v-model="selectedValue" placeholder="案例港区"  class="custom-select">
      <el-option
        v-for="item in options"
        :key="item.value"
        :label="item.label"
        :value="item.value"
      ></el-option>
    </el-select>
    </div>
    </el-card>
    <el-card class="box-card">
    <div>
    <el-tabs v-model="activeTab" @tab-click="handleTabClick" type="border-card">
      <el-tab-pane label="港口规模及设计船型" name="experiment1">
        <div>这是实验1的内容</div>
      </el-tab-pane>
      <el-tab-pane label="气/海象及地质等" name="experiment2">
        <div>这是实验2的内容</div>
      </el-tab-pane>
      <el-tab-pane label="乘潮水位累积频率曲线" name="experiment3">
        <div>这是实验3的内容</div>
      </el-tab-pane>
      <el-tab-pane label="手工仿真" name="experiment4">
        <div>这是实验4的内容</div>
      </el-tab-pane>
      <el-tab-pane label="航道主尺寸" name="experiment5">
        <div>这是实验5的内容</div>
      </el-tab-pane>
      <el-tab-pane label="航道仿真实验" name="experiment6">
        <div>这是实验6的内容
          <div style="text-align:center">
      <iframe width="1200" height="650" allow="fullscreen"
        src="http://120.25.213.148:8888/#/face?ticket=vB5K03JzUsSf65XxEJx5ahYL1hVPOh8iuXTMYZW0u%2BfkwH2E%2FFpDhgtT5d0IajbgrXED4%2FXmlWkUuQTV5a7XzK1Z0AeJAbksTMk7HuhKwYw%3D&token=AAABiLlUu14BAAAAAAABly4%3D.wsVEuNZ26YG%2FPm9rrW6eBOjlPf1%2FC2o%2FprwIgpLkiNX5SUnZjaJefsbzySoj03J3TmUwXztSOWvhE%2BlDqfWZPO3lKvfCpks9Q6Lk2aMgu%2Fw%3D.3Blo05JGhQF%2B0VFkSgGHRMh%2B7It5IUP44OLacgNvCV0%3D"></iframe>
    </div>
    <el-form>
      <el-table :data="tableData" style="width: 100%">
        <el-table-column label="序号" type="index" width="100" align="center">
        </el-table-column>
        <el-table-column prop="numqc" label="numqc" align="center">
          <template #default="scope">
            <el-input v-model="scope.row.numqc" type="text" @change="onChange(scope.$index, scope.row)"></el-input>
          </template>
        </el-table-column>
        <el-table-column prop="numit" label="numit" align="center">
          <template #default="scope">
            <el-input v-model="scope.row.numit" type="text" @change="onChange(scope.$index, scope.row)"></el-input>
          </template>
        </el-table-column>
        <el-table-column prop="qqct1" label="qqct1" align="center">
          <template #default="scope">
            <el-input v-model="scope.row.qqct1" type="text" @change="onChange(scope.$index, scope.row)"></el-input>
          </template>
        </el-table-column>
        <el-table-column prop="qqct2" label="qqct2" align="center">
          <template #default="scope">
            <el-input v-model="scope.row.qqct2" type="text" @change="onChange(scope.$index, scope.row)"></el-input>
          </template>
        </el-table-column>
        <el-table-column prop="bst" label="bst" align="center">
          <template #default="scope">
            <el-input v-model="scope.row.bst" type="text" @change="onChange(scope.$index, scope.row)"></el-input>
          </template>
        </el-table-column>
      </el-table>
      <div style="text-align:center;margin-top:10px">
        <el-button type="info" style="margin-right:20px">暂存结果</el-button>
        <el-button type="success" style="margin-right:20px">提交</el-button>
        <el-button type="warning" style="margin-right:20px">提交报告</el-button>
      </div>
      
    </el-form>
        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
    
  </el-card>
</el-card>
</template>

<script>
export default {
  data() {
    return {
      // 假数据初始化
      tableData: [
        { numqc: '12', numit: '2', qqct1: '1', qqct2: '1', bst: '' },
        // 根据需要增加更多行
      ],
      selectedValue: '', // 用来绑定选中的案例港区
      options: [] // 下拉港区选项的内容
    };
  },
  created() {
    // 生成10个下拉选项
    for (let i = 1; i <= 10; i++) {
      this.options.push({
        value: `港区${i}`,
        label: `港区${i}`
      });
    }
  },
  methods: {
    onChange(index, row) {
      console.log(`Row ${index + 1} changed`, row);
      // 在这里实现数据更新到后台的逻辑
      // 可以使用 axios 或其他 HTTP 库发送更新请求
    },
  },
};
</script>

<style lang="scss" scoped>
.box-card {
  margin: 20px;
  padding: 20px;
}

.select-container {
  display: flex;
  justify-content: center;
}
.custom-select .el-input {
  width: 400px; /* 设置下拉选项框的宽度 */
}
</style>
