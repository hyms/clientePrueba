<template>
  <div>
    <b-table striped hover :items="items">
      <template #cell(avatar)="data">
        <img :src="data.value"  alt="image">
      </template>
    </b-table>
    <b-pagination
        v-model="currentPage"
        :total-rows="total"
        :per-page="perPage"
        aria-controls="my-table"
    ></b-pagination>
  </div>
</template>

<script>
const axios = require('axios');
export default {
  data() {
    return {
      items: [],
      perPage: 1,
      total: 1,
      currentPage: 1,
    }
  },
  methods:{
    getData(page){
      axios.get('https://reqres.in/api/users?page='+page).then(({data}) => {
        this.items = data.data;
        this.currentPage =page;
        this.perPage = data.per_page;
        this.total = data.total;
      }).catch((ex) => {
        console.log(ex);
      })
    },
    chageData(){
      this.getData(this.currentPage);
    }
  },
  created() {
    this.getData(1);
  },
  computed: {
    rows() {
      return this.items.length
    }
  }
}
</script>