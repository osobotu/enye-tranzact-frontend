<template>
  <div class="container">
    <navbar-component />
    <section class="main-section">
      <div class="user-details-container" v-for="i in 20" :key="i">
        <user-details />
      </div>
    </section>
  </div>
</template>

<script>
import NavbarComponent from "~/components/NavbarComponent";
import UserDetails from "~/components/UserDetails";

export default {
  components: {
    NavbarComponent,
    UserDetails
  }
};
</script>

<style lang="scss">
@import "~assets/styles/variables";
.main-section {
  padding: 5px var(--body-padding);
  margin-top: 2rem;

  display: grid;
  gap: 10px;
  grid-template-columns: repeat(3, 1fr);

  @media only screen and (min-width: 1024px) {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>