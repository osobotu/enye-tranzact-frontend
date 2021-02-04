<template>
  <div class="pagination-button-group">
    <div :class="{muted: paginationData.isFirstPage}" class="previous-x2" @click="paginationNavigate(-2)">
      <i class="fas fa-backward"></i>
    </div>
    <div :class="{muted: paginationData.isFirstPage}" class="previous" @click="paginationNavigate(-1)">
      <i class="fas fa-caret-left"></i>
    </div>
    <div class="page">{{paginationData.index}}</div>
    <div :class="{muted: paginationData.isLastPage}" class="forward" @click="paginationNavigate(1)">
      <i class="fas fa-caret-right"></i>
    </div>
    <div :class="{muted: paginationData.isLastPage}" class="forward-x2" @click="paginationNavigate(2)">
      <i class="fas fa-forward"></i>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    paginationData:{
      required: true
    }
  },
  methods: {
    paginationNavigate(val){
      // val = 1 next,
      // val = 2 last page, 
      // val = -1 previous, 
      // val = -2 first
      this.$emit("navigate", val)
    }
  }
};
</script>

<style lang="scss">
@import "~assets/styles/variables";
.pagination-button-group {
  display: inline-flex;
  background: white;
  border-radius: 5px;
  height: 30px;
  align-items: center;
  justify-content: center;
  padding: 0 16px;
  box-shadow: 0px -2px 10px rgba($color1, 0.25);
  border: 1px solid rgba($color1, 0.4);
  i {
    cursor: pointer;
    padding: 8px;
  }
  .page {
    color: $color4;
  }

  .previous-x2,
  .forward-x2,
  .forward,
  .previous{
    &.muted {
      color: grey;
    }
  }


  .previous-x2,
  .forward-x2 {
    // flex: 2;
    width: 50px;
  }

  .forward,
  .previous {
    // flex: 1;
    width: 30px;
  }
  .forward,
  .forward-x2 {
    display: inline-flex;
    justify-content: flex-end;
  }
}
</style>