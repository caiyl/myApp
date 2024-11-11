<template>
  <view class="index">
    <button @click="changeMessage">{{ msg }}</button>
  </view>
</template>

<script>
import { ref } from 'vue'
import './index.css'

export default {
  setup () {
    const msg = ref('点击我改变消息')

    // 点击按钮时改变消息内容
    const changeMessage = () => {
      msg.value = '消息已改变!'
    }

    return {
      msg,
      changeMessage
    }
  }
}
</script>

<style scoped>
.index {
  text-align: center;
  padding: 20px;
}

button {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #45a049;
}
</style>
