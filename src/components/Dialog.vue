//Dialog.vue
<template>
  <div class="dialog">
    <el-dialog
      title="添加资金信息"
      :visible.sync="dialog.show"
      :close-on-click-modal="false"
      :close-on-press-escape="false"
      :modal-append-to-body="false"
    >
      <div class="form">
        <el-form  ref="form" :model="formData" :rules="rules" label-width="120px" style="margin:10px;width:auto;">
          <el-form-item label="收支类型：">
            <el-select v-model="formData.type" placeholder="收支类型:">
              <el-option
                v-for="(formtype,index) in format_type_list"
                :key="index"
                :label="formtype"
                :value="formtype"
              ></el-option>
            </el-select>
          </el-form-item>
          <el-form-item prop="describe" label="收支描述:">
            <el-input type="describe" v-model="formData.describe"></el-input>
          </el-form-item>
          <el-form-item prop="income" label="收入:">
            <el-input type="income" v-model="formData.income"></el-input>
          </el-form-item>
          <el-form-item prop="expend" label="支出:">
            <el-input type="expend" v-model="formData.expend"></el-input>
          </el-form-item>
          <el-form-item prop="cash" label="账户现金:">
            <el-input type="cash" v-model="formData.cash"></el-input>
          </el-form-item>
          <el-form-item prop="remark" label="备注:">
            <el-input type="textarea" v-model="formData.remark"></el-input>
          </el-form-item>
          <el-form-item class="text_right">
            <el-button @click="dialog.show=false">取消</el-button>
            <el-button type="primary" @click="onSubmit('form')">提交</el-button>
          </el-form-item>
        </el-form>
      </div>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: "dialog",
  data() {
    return {
      formData: {
        type: "",
        describe: "",
        income: "",
        expend: "",
        cash: "",
        remark: ""
        // id: ""
      },
      rules: {
        describe: [
          {
            requied: true,
            message: "收支描述不能为空",
            trigger: "blur"
          }
        ],
        income: [{ requied: true, message: "收入不能为空", trigger: "blur" }],
        expend: [{ requied: true, message: "支出不能为空", trigger: "blur" }],
        cash: [{ requied: true, message: "账户不能为空", trigger: "blur" }]
      },
      format_type_list: [
        "提现",
        "提现手续费",
        "充值",
        "优惠券",
        "充值礼券",
        "转账"
      ]
    };
  },
  props: {
    dialog: Object
  },
  methods: {
      onSubmit(form){
          this.$refs[form].validate(valid=>{
              if(valid){
                  this.$axios.post("/api/profiles/add",this.formData)
                  .then(res=>{
                    //   添加成功
                    this.$message({
                        message:"数据添加成功",
                        type:'success'
                        })
                  });

                //   隐藏对话框
                this.dialog.show = false;

                // 自动刷新
                this.$emit('update');
              }
          })
      }

  }
};
</script>

<style>
</style>