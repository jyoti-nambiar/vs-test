<template>
  <div class="pagination-div">
    <button :disabled = "pageNumber <= 1" v-on:click="paginationFunction(prevUrl,'prev')">Prev</button>
    <span>{{ pageNumber }}</span>
    <button :disabled ="nextUrl.length == 0 && pageNumber>1" v-on:click="paginationFunction(nextUrl,'next')">Next</button>
  </div>
</template>

<script>
export default {
  name: "Pagination",
  props: ["prevUrl", "nextUrl"],
  
  data() {
    return {
      pageNumber: 1,

    };
  },
  methods: {
    paginationFunction: function(url,buttonAction) {
      if(buttonAction =='prev')
        this.pageNumber-= 1;
      if(buttonAction == 'next')
        this.pageNumber+= 1;
      console.log("inside pagination", url);
      this.$parent.getData(url);
    },
  },
};
</script>

<style scoped>
.pagination-div {
  display: flex;
  justify-content: center;
  align-content: center;
  margin-top: 15px;
}

button,
span {
  margin: 10px;
  padding: 10px;
}
</style>
