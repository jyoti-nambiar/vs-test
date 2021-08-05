<template>
  <div class="container">
    <div class="row">
      <div class="column">
        <div class="card" v-for="pic in picdetails" :key="pic.id">
          <img
            v-bind:src="'https://picsum.photos/id/' + pic.id + '/367/267'"
            alt="picsum-photos"
            @click="showModal(pic)"
          />

          <p>
            <span class="left">{{ pic.author }}</span>
            <span class="right"> #{{ pic.id }}</span>
          </p>
        </div>
      </div>
      <Modal
        v-bind:picdetails="selectedPic"
        v-show="isModalVisible" 
        @close="closeModal"
      />
    </div>
    <Pagination v-bind:prevUrl="prevUrl"
    v-bind:nextUrl="nextUrl"
    />
  </div>
</template>

<script>
import axios from "axios";
import parse from "parse-link-header";
import Modal from "./Modal.vue";
import Pagination from './Pagination.vue';

export default {
  name: "ImageListMain",

  components: {
    Modal,
    Pagination
   
  },

  data() {
    return {
      isModalVisible: false,
      baseUrl: "https://picsum.photos/v2/list",
      nextUrl: '',
      prevUrl: '',
      picdetails: [],
      selectedPic: [],
    };
  },
  created() {
    this.getData(this.baseUrl);
  },
  methods: {
    getData: function(url) {
      axios.get(url).then((response) => {
        this.picdetails = response.data;
        if(parse(response.headers.link).next != null){
        this.nextUrl = parse(response.headers.link).next.url;
        } else{
        
        this.nextUrl = '';
        
        }
        
        if (parse(response.headers.link).prev != null){
         this.prevUrl = parse(response.headers.link).prev.url;
        }
      });
    },

    showModal(pic) {
      this.selectedPic = pic;
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img{
border-radius: 5px;

}

span{
  margin:10px;
  padding:10px;
  border-radius: 9999px;
  background-color: #f1f5f8;
  text-overflow: ellipsis;
}

.column{
display:inline-grid;
grid-template-columns:1fr 1fr 1fr;

 column-gap: 15px;
  row-gap: 15px;

}
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2); 
  padding: 10px;
  background-color: #f1f1f1;
  
}

@media screen and (max-width: 600px) {
  .column {
    grid-template-columns:1fr;

  }
}


</style>