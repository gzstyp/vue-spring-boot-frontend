<template>
    <div>
      <h3>我的user组件</h3>
      <table>
        <thead>
          <tr>
            <td style="width:140px;">编号</td>
            <td style="width:160px;">姓名</td>
            <td style="width:140px;">年龄</td>
            <td style="width:140px;">性别</td>
          </tr>
        </thead>
        <tbody>
        <tr v-for="item in users">
          <td>{{item.id}}</td>
          <td>{{item.name}}</td>
          <td>{{item.age}}</td>
          <td>{{item.sex}}</td>
        </tr>
        </tbody>
      </table>
    </div>
</template>

<script>
  import axios from 'axios'
export default {
  name : 'UserView',
  data () {
    return {
      users : {}
    }
  },
  created () {
    var _this = this;
    axios.get('http://127.0.0.1:807/user/all').then(res => {
      return _this.users = res.data.data;
    });
  }
}

</script>

<style scoped>

</style>
<!--
export default function(url, method, params = {}) {
	// 首先判断是get请求还是post请求
	let data = method.toLocaleLowerCase() === 'get' ? 'params' : 'data';
	return axios({
    	method,
    	url,
    	[data]: params // 差异点在于data的值
	}).then((res) => {
    	return Promise.resolve(res.data);
	}).catch((err) => {
    	return Promise.reject(err);
	})
}
-->
