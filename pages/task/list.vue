<template>
  <section class="container">
    <h2>顧客一覧</h2>

    <!-- <div class="Filter">
      <button class="button">全て</button>
      <button class="button">会員</button>
      <button class="button">退会済み</button>
    </div> -->
    <table class="Lists" rules="rows">
      <thead>
        <tr>
          <th>No</th>
          <th>名前</th>
          <th>性別</th>
          <th>登録日時</th>
          <th>Pt</th>
          <th>詳細</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in items" :key="index">
          <td>{{ ( index + 1 ) }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.gender }}</td>
          <td>{{ item.date }}</td>
          <td>{{ item.point }}</td>
          <td><button class="button" @click="deleteItem(index)">削除</button></td>
        </tr>
      </tbody>
    </table>
  </section>
</template>

<script>
export default {
    data(){
      return{
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
			handler: function() {
			  localStorage.setItem('items', JSON.stringify(this.items));
			},
			deep: true
		  }
		},
		mounted: function() {
		  this.items = JSON.parse(localStorage.getItem('items')) || [];
		},
    methods:{
      addItem: function() {
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
      deleteItem:function(index){
			if (confirm('この項目を削除しますか？')){
				this.items.splice(index,1);
			}
		},
}
}

</script>



<style>

.container {
  text-align: center;
}

.Lists {
  margin:15px auto;
}

th {
  padding:20px;
  background-color: #fff;
}

tbody td{
  padding:10px 20px;
}
</style>