<template>
  <div>
    <el-card class="box-card">
      <div slot="header">
        <i
          :class="{'el-icon-arrow-up' : expanded,'el-icon-arrow-down' : !expanded }"
          @click="handleChange"
        ></i>
        <span>Loyalty Info</span>
      </div>
      <div v-loading="loading" v-show="expanded">Loyalty Info</div>
    </el-card>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import _ from "lodash";
export default {
  data() {
    return {
      expanded: false,
      loading: false
    };
  },
  methods: {
    handleChange(val) {
      this.expanded = !this.expanded;
      this.$store.dispatch("resizeClient");
    }
  },
  computed: {},
  watch: {
    interaction: function(val) {
      this.$store.dispatch("resizeClient");
    }
  }
};
</script>
