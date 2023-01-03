<script>
  import { MDBCard, MDBCardHeader, MDBCardBody, MDBCardTitle, MDBCardText, MDBBtn } from "mdb-vue-ui-kit";
  export default {
    components: {
      MDBCard,
      MDBCardHeader,
      MDBCardBody,
      MDBCardTitle,
      MDBCardText,
      MDBBtn
    }
    ,data () {
      return {
        arrData : [],
        total : '',
        greaterthan :''
      }
    },mounted(){
      const data = [
          {
            id:1,
            nama: 'Bakso',
            harga : 12000
          },{
            id:2,
            nama: 'Seblak',
            harga : 15000
          }, {
            id:1,
            nama: 'Cilor',
            harga : 13000
          }
    ]
      this.arrData = data
      const sum = data.reduce((a, b) => a + b.harga, 0);
      this.total = sum
      
    },methods:{
         sort(price){
          if(price == 0)
          {
            const data = [
                  {
                    id:1,
                    nama: 'Bakso',
                    harga : 12000
                  },{
                    id:2,
                    nama: 'Seblak',
                    harga : 15000
                  }, {
                    id:3,
                    nama: 'Cilor',
                    harga : 13000
                  }
            ]
            var filteredArray = data.filter(function(e) { return e.harga > price })
            this.arrData = filteredArray
            this.recalculate(this.arrData)
          }

          var filteredArray = this.arrData.filter(function(e) { return e.harga > price })
          this.arrData = filteredArray
          this.recalculate(this.arrData)
        },
        recalculate(arr){
          const sum = arr.reduce((a, b) => a + b.harga, 0);
          this.total = sum
        }
    }
  };
 
</script>

<template>
  <div>
  <div class="container">
  <div v-for="data in arrData" :key="data.id" >
    <MDBCard text="center">
      <MDBCardHeader>{{ data.nama }}</MDBCardHeader>
      <MDBCardBody>
        <MDBCardTitle>{{data.harga}}</MDBCardTitle>
      </MDBCardBody>
  </MDBCard>

</div>
</div>
<hr>
<h1>Total : {{ total }}</h1>
<div>

  <input type="number" v-model="greaterthan" id="">
  <MDBBtn color="primary" class="mb-3" @click="sort(greaterthan)">
    Sort by Price
  </MDBBtn>
</div>
</div>
</template>

<style scoped>
.container {
  display: flex;
}
</style>
