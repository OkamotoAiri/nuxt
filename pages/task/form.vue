<template>
<div>
    <h2>新規顧客登録</h2>
  <div class="form-wrapper">
    <form action="completed" @submit.prevent="addItem()" >
      <table class="register">
        <tr>
          <th class="register-item">名前</th>
          <th class="register-body">
            <p class="error" v-if="isInValidName">※２文字以上で入力してください</p>
            <input type="text" v-model="userName"></th>
        </tr>
        <tr>
          <th class="register-item">性別</th>
          <th class="register-body">
            <input type="radio" name="gender" value="男" v-model="gender" checked>男
            <input type="radio" name="gender" value="女" v-model="gender">女
          </th>
        </tr>
        <tr>
          <th class="register-item">登録日</th>
          <th class="register-body">
            <p class="error" v-if="isInValidDate">※選択してください</p>
            <input type="date" v-model="date"></th>
        </tr>
        <tr>
          <th class="register-item">ポイント</th>
          <th class="register-body"><input type="number" min="0" v-model="point"></th>
        </tr>
      </table>
      <input type="submit" value="登録" :disabled="isDisabled">
    </form>
  </div>
</div>
</template>

<script>

export default {
    data(){
      return{
      errors:{},
      items: [],
      userName: '',
      gender:'',
      date:'',
      point:'',
      number:''
    }
    },
    watch: {
		  items: {
			handler() {
			  localStorage.setItem('items', JSON.stringify(this.items));
			},
			deep: true
		  },
      // userName(userName){
      //   if (userName){
      //     this.$delete(this.errors, 'userName')
      //   }else{
      //     this.$set(this.errors, "userName", '名前を入力してください')
      //   }
      // }
		},
		mounted() {
		  this.items = JSON.parse(localStorage.getItem('items')) || [];
		},
    methods:{
      addItem() {
        // if (this.userName ==''){
        //     this.error1 = true ;
        //   return false;
        //   }
        let userData = {
          name:this.userName,
          gender:this.gender,
          date:this.date,
          point:this.point,
        }

			this.items.push(userData);
			this.userName = '';
      this.gender ='';
      this.date ='';
      this.point ='';
  
      },
    },
    computed:{
      isInValidName() {
        return this.userName.length < 2
      },
      // isInValidDate() {
      //   return this.date_format(YYYY-MM-DD)
      // },
    }
}

</script>
<style>

.form-wrapper {
  width: 350px;
  margin: 0 auto;
  padding-bottom: 20px 0;
  text-align: center;
}

.register {
  border-collapse: collapse;
  width: 100%;
  margin-bottom: 20px;
}

.register-item,
.register-body {
  font-weight: normal;
  padding:20px;
  border: 1px solid rgb(184, 182, 182);
  text-align:left;
}

.register-item {
  width: 30%;
  background-color: #eee;
}

.register-body {
  width: 70%;
  background-color: #fff;
}

input {
  padding:4px;
}

.error {
  font-size:12px;
  color:red;
}
</style>