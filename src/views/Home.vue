<template>
  <div class="hello col" :style="{background: bg}">
    <h1>{{ msg }}</h1>
    <div class="butbox row">
      <!-- <button
       >
       开始
      </button> -->
      <el-button
       class="but"
       @click="butStart"
       type="primary"
       :disabled="!disabled"
      >
      开始
      </el-button>
      <el-button 
        class="but"
        @click="butEnd"
        type="primary"
        :disabled="disabled"
      >
      结束
      </el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }, 
  data () {
    return{
     startTime: NaN, 
     waitTime: false, 
     bg: '#e6e6e6',
     disabled: true,
    }
  }, 
  methods: {
    butStart () {
      this.disabled =  !this.disabled
      this.waitTime = true
      setTimeout(() => {
          if(this.waitTime){
            this.startTime = Number(new Date())
            const r = Math.floor(Math.random() * 256)
            const g = Math.floor(Math.random() * 256)
            const b = Math.floor(Math.random() * 256)
            this.bg = `rgb(${r},${g},${b})`
          }
          }, Math.random() * 1000 + 1000)
    }, 
    butEnd () {
      this.waitTime = false
      if(this.startTime){
        this.disabled =  !this.disabled
        let endtime = (Number(new Date()) - this.startTime) / 1000
        this.$alert(
            endtime + 's', '你的反应时间是', {confirmButtonText: '确定', center: true})
        this.bg = '#e6e6e6'
        this.startTime = NaN
      }else{
         this.$alert(
            '你点早了', 
            '大熊帝', 
            {
              confirmButtonText: '再试一次', 
              center: true
            }
          )
          this.disabled =  !this.disabled
      }
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.hello{
  padding-top: 10vh;
  width: 100vw;
  height: 90vh;
  align-items: center;
}
.butbox{
  width: 20rem;
  padding: 1rem;
  margin-top: 10rem;
  justify-content: space-between;
  .but{
    width: 8rem;
    height: 3rem;
  }
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
