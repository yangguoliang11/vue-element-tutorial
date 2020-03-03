<template>
  <div class="hello">
    <h1>{{ msg.split("").reverse().join(",") }}</h1>
    <h1>{{ cal }}</h1>
    <h2>{{ msg | strtoupper }}</h2>
    <h2>{{ msg | indexof }}</h2>
    <h2>{{ msg | search }}</h2>
    <h2>{{ msg | substr }}</h2>
    <h2>{{ msg | substring }}</h2>
    <h2>{{ msg | slice }}</h2>
    <h2>{{ msg | replace }}</h2>
    <h2>{{ msg | replaceAll }}</h2>
    <h2>{{ msg | match }}</h2>
    <ul>
      <li v-bind:class="{'class1':use}">
        <a @click="link2">
          链接到hello2
        </a>
      </li>
    </ul>
    <div v-html="message"></div>
    <div v-show="show">22222222222222</div>
    <div v-if="show">333333333</div>
    <div v-else-if="show2">555555555555</div>
    <div v-else-if="show3">6666666666</div>
    <div v-else>333333333</div>
    <ul v-for="site in sites" :key="site.id">
      <li>{{site.name}}</li>
    </ul>
    <el-container style="height: 500px; border: 1px solid #eee">
    <el-form>
      <el-input v-model="keep"></el-input>
      <el-button v-on:click.prevent='submit2'>111</el-button>
      <el-button @click='submit2'>33333333</el-button>
      <el-button @dblclick='submit2'>4444444444</el-button>

      <el-button @click="addcounter">{{counter}}</el-button>
      <el-input @keyup.space="addcounter2" v-model="counter"></el-input>
      <el-radio v-model="radio1" border  label="Google">Google</el-radio>
      <el-radio v-model="radio1" border  label="Baidu">Baidu</el-radio>
      <h2>当前选择:{{radio1}}</h2>
    </el-form>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      use: false,
      show: false,
      show2: false,
      show3: true,
      keep: '123',
      counter: 12,
      radio1: 'Google',
      sites: [
        {
          id: '1111',
          name: 'guoliang'
        },
        {
          id: '2222222222',
          name: 'guoliang2'
        }
      ],
      msg: 'Welcome to Your Vue.js App',
      message: '<h1>1111111111111</h1>'
    }
  },
  mounted () {
    this.test()
  },
  watch: {
    keep: function (val) {
      this.message = val
    }
  },
  computed: {
    cal: function () {
      return this.msg.split('').reverse().join(',')
    }
  },
  filters: {
    strtoupper: function (value) {
      return value.toUpperCase()
    },
    indexof: function (value) {
      return value.indexOf('o') + value.lastIndexOf('o')
    },
    search: function (value) {
      return value.search('o')
    },
    substring: function (value) {
      // substring(start, end)
      return value.substring(3, 5)
    },
    substr: function (value) {
      // substr(start, length)只有这个是长度
      return value.substr(3, 5)
    },
    slice: function (value) {
      // slice(start, end)
      return value.slice(3, 5)
    },
    replace: function (value) {
      // slice(start, end)
      return value.replace('o', '00000000000000000')
    },
    replaceAll: function (value) {
      // slice(start, end)
      return value.replace(/o/g, '00000000000000000')
    },
    match: function (value) {
      // slice(start, end)
      return typeof (value.match(/o/g))
    }
  },
  methods: {
    addcounter: function (event) {
      // this这里是Vue实例
      alert(this.counter + 1)
      // event是DOM结构
      if (event) {
        alert(event.target.tagName)
        alert(event.target.localName)
      }
    },
    addcounter2: function () {
      // this这里是Vue实例
      this.counter += 1
    },
    test: function () {
      // alert(1111)
      console.log(this.$el)
      // 所有的元素
      console.log(this.$components)
      console.log(this.$router)
      console.log(this.$template)
    },
    link: function () {
      this.$router.push({ name: 'HelloWorld1' })
    },
    link2: function () {
      this.$router.push({ name: 'HelloWorld2' })
    },
    submit2: function () {
      console.log(111111111111111)
      alert(1111111111)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
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
.class1 a{
  color:blueviolet;
  font-size:70px;
}
</style>
