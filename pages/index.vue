<template>
  <div class="container">
    <navbar-component />
    <section class="main-section">
      <div class="user-details-container d-none d-block-tablet" v-for="i in 20" :key="i">
        <user-details />
      </div>
      <div class="user-profile-strip-container d-none-tablet" v-for="i in 20" :key="i">
        <user-profile-strip @show-modal="showModal()" />
      </div>
    </section>
    <div class="pagination-group-container">
      <pagination-button-group />
    </div>

    <!-- user details modal for mobile -->
    <div class="user-details-modal" :class="{show: showingModal}">
      <user-details @close-button-clicked="closeModal()" :showCloseButton="true" />
    </div>
  </div>
</template>

<script>
import NavbarComponent from "~/components/NavbarComponent";
import UserDetails from "~/components/UserDetails";
import UserProfileStrip from "~/components/UserProfileStrip";
import PaginationButtonGroup from "~/components/PaginationButtonGroup";

export default {
  data() {
    return {
      showingModal: false
    };
  },
  components: {
    NavbarComponent,
    UserDetails,
    PaginationButtonGroup,
    UserProfileStrip
  },
  methods: {
    showModal() {
      this.showingModal = true;
    },
    closeModal() {
      this.showingModal = false;
    }
  }
};
</script>

<style lang="scss">
@import "~assets/styles/variables";
.main-section {
  margin-bottom: 100px;

  @media only screen and (min-width: 768px) {
    margin-top: 2rem;
    padding: 5px var(--body-padding);
    grid-template-columns: repeat(1, minmax(0px, 1fr));
    display: grid;
    column-gap: 10px;
    row-gap: 40px;
  }

  @media only screen and (min-width: 1024px) {
    grid-template-columns: repeat(2, minmax(0px, 1fr));
  }

  @media only screen and (min-width: 1400px) {
    grid-template-columns: repeat(3, minmax(0px, 1fr));
  }
}

.pagination-group-container {
  position: fixed;
  bottom: 32px;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

@keyframes show-modal {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.user-details-modal {
  position: fixed;
  top: 100px;
  z-index: 11;
  right: var(--body-padding);
  max-width: calc(100vw - var(--body-padding) * 2);
  display: none;
  &.show {
    display: block;
    animation-name: show-modal;
    animation-duration: 0.5s;
  }
}
</style>