<template>
  <div class="hello">
    <el-row :gutter="0">
      <el-col :xs="24" :sm="12" :md="8" :lg="6" :xl="4">
        <div class="grid-content">
          <el-upload action="#" :auto-upload="false" :show-file-list="false"
              :on-change="handleChange">            
            <img class="el-upload-list__item-thumbnail center-block"
              v-if="dialogImageUrl" :src="dialogImageUrl" alt="">
          </el-upload>
        </div>
      </el-col> 
      <!-- <el-col :xs="{span:24, offset:0}" :sm="12" :md="8" :lg="6" :xl="4"><div class="grid-content bg-purple"></div></el-col> -->
      <el-col :xs="24" :sm="12" :md="8" :lg="6" :xl="4">
        <div class="grid-content bg-purple-light">
          <el-upload action="#" :auto-upload="false" :show-file-list="false"
              :on-change="handleChange">            
            <img class="el-upload-list__item-thumbnail center-block"
              v-if="dialogImageUrl" :src="dialogImageUrl" alt="">
          </el-upload>
        </div>
      </el-col>
      <el-col :xs="24" :sm="12" :md="8" :lg="6" :xl="4">
        <div class="grid-content bg-purple">
          <el-upload action="#" :auto-upload="false" :show-file-list="false"
              :on-change="handleChange">            
            <img class="el-upload-list__item-thumbnail center-block"
              v-if="dialogImageUrl" :src="dialogImageUrl" alt="">
          </el-upload>
        </div>
      </el-col>
      <el-col :xs="24" :sm="12" :md="8" :lg="6" :xl="4">
        <div class="grid-content bg-purple-light">
          <el-upload action="#" :auto-upload="false" :show-file-list="false"
              :on-change="handleChange">            
            <img class="el-upload-list__item-thumbnail center-block"
              v-if="dialogImageUrl" :src="dialogImageUrl" alt="">
          </el-upload>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        dialogImageUrl: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg',
        dialogVisible: false,
        disabled: false
      };
    },
    methods: {
      handleRemove(file) {
        return this.$confirm(`确定移除 ${ file.name }？`);
      },
      handlePictureCardPreview(file) {
        this.dialogImageUrl = file.url;
        this.dialogVisible = true;
      },
      handleDownload(file) {
        console.log(file);
      },
      handleChange(file, fileList) {
        this.dialogImageUrl = URL.createObjectURL(file.raw);
        console.log(file.raw)
      }
    }
  }
</script>

<style>
  img {
    max-width: 100%; height-width: 100%; margin: 1px;
    border-radius: 10px; border: solid 1px #FF00FF;
  }
  /*.el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }*/
  .grid-content {
    border-radius: 4px red;
  }
</style>