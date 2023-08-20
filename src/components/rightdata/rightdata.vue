<template>
  <div class="rightdata">

    <!-- <div class="footer">
      <svg data-v-a22cce3a xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024">
        <path fill="currentColor"
          d="M480 480V128a32 32 0 0 1 64 0v352h352a32 32 0 1 1 0 64H544v352a32 32 0 1 1-64 0V544H128a32 32 0 0 1 0-64h352z" />
      </svg>
      <input type="text" placeholder="添加任务" v-model="inputValue" @focus="startAnimation" @blur="resetProgress"
        @keyup.enter="handleEnterKey" />
      <div class="jindu">
        <el-progress :percentage="progressValue" color="#1089ff" :show-text="false"
          :stroke-width="borderHeight"></el-progress>
      </div>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'VueRightdata',

  data() {
    return {
      inputValue: "",
      progressValue: 0,
      timer: null,
      borderHeight: 2,
      datelist: []
    };
  },
  methods: {
    startAnimation() {
      clearInterval(this.timer); // 清除之前的计时器
      this.progressValue = 0; // 将进度条重置为0
      this.timer = setInterval(() => {
        if (this.progressValue < 100) {
          this.progressValue += 10; // 每次增加10%
        } else {
          clearInterval(this.timer); // 达到100%后清除计时器
        }
      }, 100);
    },
    resetProgress() {
      clearInterval(this.timer); // 清除计时器
      this.progressValue = 0; // 将进度条重置为0
    },
    handleEnterKey() {
      this.datelist.push(this.datelist);
      this.inputValue = ''; // 清空输入框 
      console.log(this.datelist);
    }
    
  }
};
</script>

<style scoped>
.rightdata {
  margin-top: -20px;
  width: 80%;
  float: right;
}

.footer {
  position: fixed;
  bottom: 12px;
  right: 30px;
  width: 74%;
  height: 50px;
  line-height: 40px;
  background-color: #1c1c1e;
  border-top-left-radius: 6px;
  border-top-right-radius: 6px;
  margin: auto;
}

svg {
  width: 16px;
  height: 16px;
  margin-left: 15px;
  color: aliceblue;
}

input {
  position: relative;
  top: -2.5px;
  width: 73%;
  height: 35px;
  outline: none;
  border: none;
  padding-left: 5px;
  background-color: #1c1c1e;
  color: aliceblue;
  border-radius: 6px;
}

.progress-bar {
  height: 10px;
  background-color: #ccc;
}

</style>