<template>
  <div class="navbar">
    <div class="top">
      <div class="brand">
        <i class="fab fa-opencart"></i>
        <span>Tranzact</span>
      </div>
      <div class="search-box-container">
        <input type="text" class="search-box" placeholder="Search" />
        <i class="fas fa-search"></i>
      </div>
    </div>
    <div class="bottom">
      <div class="filters-container">
        <div class="filter-group">
          <select class="filter-select" @change="filterProfiles(`Gender`)">
            <option value disabled selected hidden>Filter by gender</option>
            <option value="female">FEMALE</option>
            <option value="male">MALE</option>
          </select>
        </div>
        <div class="filter-group">
          <select class="filter-select" @change="filterProfiles(`PaymentMethod`)">
            <option value disabled selected hidden>Filter by payment method</option>
            <option
              :value="paymentMethod.key"
              v-for="paymentMethod in paymentMethods"
              :key="paymentMethod.key"
            >{{paymentMethod.value}}</option>
          </select>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      paymentMethods: [
        {
          key: "cc",
          value: "cc"
        },
        {
          key: "money order",
          value: "money order"
        },
        {
          key: "paypal",
          value: "paypal"
        },
        {
          key: "check",
          value: "check"
        }
      ]
    };
  },
  methods: {
    filterProfiles(filterType) {
      const target = event.target

      if(!target.value) return

      this.$emit('filter-profiles', {key: filterType, value: target.value})
    }
  }
};
</script>

<style lang="scss">
@import "~assets/styles/variables";

.navbar {
  position: sticky;
  top: 0;
  z-index: 10;
  box-shadow: 0px 2px 4px rgba($color1, 0.2);
  .top {
    padding: 0 var(--body-padding);
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 50px;
    background: $color3;
    color: white;

    .brand {
      text-transform: uppercase;
      font-size: 12px;
    }

    .search-box-container {
      height: 30px;
      background: white;
      color: $color1;
      padding: 0 8px;
      display: flex;
      align-items: center;
      border-radius: 3px;

      @media only screen and (min-width: 768px) {
        width: 250px;
      }
      .search-box {
        border: none;
        outline: none;
        background: transparent;
        flex: 1;
      }
    }
  }
  .bottom {
    display: flex;
    align-items: center;
    justify-content: center;
    background: white;
    height: 30px;
        padding: 0 var(--body-padding);
    .filters-container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      height: 100%;

      & > .filter-group {
        flex: 1;
        border-right: 1px solid rgba($color1, 0.5);
        height: 100%;

        &:last-child {
          border-right: none;
        }

        .filter-select {
          background: transparent;
          border: none;
          outline: none;
          flex: 1;
          padding: 0 16px;
          height: 100%;
          font-style: italic;
          color: $color4;
          font-weight: 300;
          font-size: 12px;
        }
      }
    }
  }
}
</style>