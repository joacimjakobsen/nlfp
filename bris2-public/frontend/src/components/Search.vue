<template>  
  <div class="grid-layout">
    <div class="top">
      <search-box
        placeholder="Søk her etter tall og statistikk" 
        initialSearch="">
      </search-box>
      <br>
      <b-col cols="2" offset="5">
        <b-btn @click="resetFilters" class="reset btn-light">
          <i class="fa fa-minus-circle"></i>
          Nullstill søk og filter
        </b-btn>
      </b-col>
    </div>
    <div class="center">
      <div v-show="isOpen">
        <b-btn
          @click="toggle"
          class="hide-filters btn-light"
        >
          Skjul filter
          <i class="fa fa-chevron-up"></i>
        </b-btn>
        <hr class="hide-hr">
        <div 
          v-for="(filterDefinition, key) in filterDefinitons" 
          :key="key"
        >        
          <filter-section 
            :title="filterDefinition.title"
            :filterDefinitons="filterDefinition.filters"
            :resetFilter="reset"
            :isOpen="true"
            @filterUpdate="updateFilters">
          </filter-section>
        </div>
        <hr>
      </div>
      <div v-show="!isOpen">
        <b-btn
          @click="toggle"
          class="show-filters btn-light"
        >
          Vis filter
          <i class="fa fa-chevron-down"></i>
        </b-btn>
        <hr class="show-hr">
      </div>
      <br>
      <search-result
        :hits="hits"
        :total="total"
      >
      </search-result>
    </div>
    <div class="bottom">

    </div>
  </div>
</template>

<script>
import SearchBox from './SearchBox';
import FilterSection from './filter/FilterSection';
import SearchResult from './SearchResult';
import FilterDefinitions from '../elastic/filter/filterDefinition';
import Query from '../elastic/query';
import ElasticClient from '../elastic/elasticClient';

let filterDefinitions = new FilterDefinitions();
let updateResult = function(that, response) {
  let result = response ? response.hits : { hits: null, total: 0 };
  that.total = result.total;
  that.hits = result.hits;
};

export default {
  name: 'Search',
  components: { SearchBox, FilterSection, SearchResult },
  data() {
    return {
      filterDefinitons: filterDefinitions,
      query: new Query(),
      client: new ElasticClient(),
      size: 10,
      total: 0,
      reset: 0,
      hits: [],
      isOpen: true
    };
  },
  methods: {
    updateFilters(filter) {
      this.query.updateFilters(filter);
      let that = this;
      this.client.search(this.query, this.size, this, updateResult);
    },
    resetFilters() {
      this.reset++;
      this.query.resetFilters();
      let that = this;
      this.client.search(this.query, this.size, this, updateResult);
    },
    toggle() {
      this.isOpen = !this.isOpen;
    }
  },
  mounted() {
    let that = this;
    this.client.search(this.query, this.size, this, updateResult);
  }
};
</script>

<style scoped lang="scss">
@import '../assets/main';
.grid-layout {
  grid-template-columns: 1fr 3fr 4fr 3fr 1fr;
}
h4 {
  text-align: center;
}
hr {
  border: none;
  border-top: 2px solid $gray-500;
  height: 2px;
}
.bottom {
  height: 200px;
}
.hide-hr {
  margin-top: -3px;
}
.show-hr {
  margin-top: -40px;
  margin-bottom: 40px;
}
.hide-filters {
  background-color: $white;
  border: 0;
  border-top: 2px solid $gray-500;
  border-left: 2px solid $gray-500;
  border-right: 2px solid $gray-500;
  border-bottom: 2px solid $white;
  border-radius: 0;
  margin-left: 100px;
}
.show-filters {
  background-color: $white;
  border: 0;
  border-top: 2px solid $white;
  border-left: 2px solid $gray-500;
  border-right: 2px solid $gray-500;
  border-bottom: 2px solid $gray-500;
  border-radius: 0;
  margin-left: 100px;
}
.hide-filters:active {
  border-color: $gray-500 !important;
}
.hide-filters:focus {
  box-shadow: 0 0 0 0 $gray-500 !important;
}
.show-filters:active {
  border-color: $gray-500 !important;
}
.show-filters:focus {
  box-shadow: 0 0 0 0 $gray-500 !important;
}
.reset {
  background-color: $white;
}
</style>
