<template>
    <div class=''>
      <div>
        <h3>异步获取数据见代码</h3>
        <div>
          <el-button type="primary" @click="getData">查询</el-button>
        </div>
        <div>
          结果是：{{result}}
        </div>
        <hr>
        <h3>去空格</h3>
        <!--两个原生去空格-->
        <input type="text" onkeyup="this.value=this.value.replace(/\s+/,'')"><br><br>
        <input type="text" @keyup="qukongge" ref="yuansheng"><br><br>
        <!--el-input去空格-->
        <el-input @keyup.native="qukongge2" v-model="input"></el-input><br><br>
        <el-input @keyup.native="input2 = input2.replace(/\s+/,'')" v-model="input2"></el-input>
      </div>
    </div>
</template>
<script>
  import api from '@/api/apiPath.js'
  export default {
    name: '',
    data () {
      return {
        input: '',
        input2: '',
        result: ''
      }
    },
    created () {
      this.getData()
    },
    methods: {
      getData () {
        this.axios.get(api.TEST).then(response => {
          if (response.data.status === 'ok') {
            console.log(response.data.data)
          }
        })
      },
      qukongge () {
        this.$refs.yuansheng.value = this.$refs.yuansheng.value.replace(/\s+/, '')
      },
      qukongge2 () {
        this.input = this.input.replace(/\s+/, '')
      }
    }
  }
</script>
<style lang="stylus" rel="stylesheet/stylus">

</style>
