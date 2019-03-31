<template>
  <div>
        <div class="header">
          <div class="info">{{`${paginatedData.quantity} producten`}}</div>
          <div id="header-pagination" class="navigation">
            <Pagination
              container-class="pagination"
              v-model="queryProps.currentPage"
              :page-count="4"
              :click-handler="handlePageClick"
              prev-class="prev-link"
              next-class="next-link"
              active-class="active"
              disabled-class="disabled-link"
              prev-text="<"
              next-text=">"
            />
          </div>
        </div>
        <div class="container">
          <item v-for="data in paginatedData.productsDataList" :key="data.id" :item="data"></item>
        </div>
        <div class="footer">
          <div id="footer-pagination" class="navigation navigation__footer">
            <Pagination
              container-class="pagination"
              v-model="queryProps.currentPage"
              :page-count="4"
              :click-handler="handlePageClick"
              prev-class="prev-link"
              next-class="next-link"
              active-class="active"
              disabled-class="disabled-link"
              prev-text="<"
              next-text=">"
            />
          </div>
        </div>
      </div>
</template>

<script>
import Pagination from 'vuejs-paginate';
import Item from './item.vue';
import { emulatePagination } from '../statics/scripts/helpers.js';

export default {
  name: 'Home',

  components: {
    'item': Item,
    Pagination
  },

  data() {
    return {
      paginatedData: [],
      queryProps: {
        lang: 'nl_NL',
        formula: 'praxis',
        currentPage: 1,
        viewSize: 24,
        categoryCode: 'd1_d271_d273',
        locale: 'nl_NL'
      }
    }
  },

  mounted() {
    this.paginatedData = emulatePagination(this.queryProps);
  },

  methods: {
    handlePageClick(data) {
      this.queryProps.currentPage = data;
      this.paginatedData = emulatePagination(this.queryProps);
    },
  },
}
</script>