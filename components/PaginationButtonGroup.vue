<template>
  <div class="pagination-button-group">
    <div class="previous-x2">
      <i class="fas fa-backward"></i>
    </div>
    <div class="previous">
      <i class="fas fa-caret-left"></i>
    </div>
    <div class="page">2</div>
    <div class="forward">
      <i class="fas fa-caret-right"></i>
    </div>
    <div class="forward-x2">
      <i class="fas fa-forward"></i>
    </div>
  </div>
</template>

<script>
export default {};
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