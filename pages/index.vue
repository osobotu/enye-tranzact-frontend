<template>
  <div class="container">
    <navbar-component @reset-profile-filters="resetProfileFilters()" @filter-profiles="filterProfiles($event)" />
    <section class="main-section">
      <div
        class="user-details-container d-none d-block-tablet"
        v-for="(displayingProfile, i) in displayingProfiles"
        :key="i"
      >
        <user-details :profile="displayingProfile" />
      </div>
      <div
        class="user-profile-strip-container d-none-tablet"
        v-for="(displayingProfile, i)  in displayingProfiles"
        :key="i"
      >
        <user-profile-strip :profile="displayingProfile" @show-modal="showModal(i)" />
      </div>
    </section>
    <div class="pagination-group-container">
      <pagination-button-group
        @navigate="paginationNavigate($event)"
        :paginationData="paginationData"
      />
    </div>

    <!-- user details modal for mobile -->
    <div class="user-details-modal" :class="{show: showingModal}">
      <user-details
        @close-button-clicked="closeModal()"
        :profile="profilePopup"
        :showCloseButton="true"
      />
    </div>
  </div>
</template>

<script>
import NavbarComponent from "~/components/NavbarComponent";
import UserDetails from "~/components/UserDetails";
import UserProfileStrip from "~/components/UserProfileStrip";
import PaginationButtonGroup from "~/components/PaginationButtonGroup";
import Vue from 'vue';

export default {
  data() {
    return {
      showingModal: false,
      profiles: [],
      profilePopupIndex: 0,
      profileFilters: {},
      paginationData: {
        index: 1,
        perpage: 20,
        isFirstPage: true,
        isLastPage: false,
      }
    };
  },
  async fetch() {
    await this.$axios
      .$get(`https://api.enye.tech/v1/challenge/records`)
      .then(response => {
        this.profiles = response.records.profiles;
      });
  },
  components: {
    NavbarComponent,
    UserDetails,
    PaginationButtonGroup,
    UserProfileStrip
  },
  methods: {
    showModal(i) {
      this.profilePopupIndex = i;
      this.showingModal = true;
    },
    closeModal() {
      this.showingModal = false;
    },
    filterProfiles({key, value}) {
      // this.profileFilters[key] = value

      Vue.set(this.profileFilters, key, value)
    },
    resetProfileFilters(){
      this.profileFilters = {}
    },
    paginationNavigate(val) {
      // val = 1 next,
      // val = 2 last page,
      // val = -1 previous,
      // val = -2 first

      let temp = this.paginationData.index;
      temp = temp + val;

      let tempProfiles = this.profiles.slice();
      const profileFilters = this.profileFilters
      
      if(Object.keys(profileFilters).length > 0){
        for(let key in profileFilters){
          tempProfiles = tempProfiles.filter(el => el[key].toLowerCase() == profileFilters[key].toLowerCase())
        }
      }

      if (Math.abs(val) == 1) {
        if (temp < 1) {
          temp = 1;
        } else if (temp > Math.ceil(tempProfiles.length / 20)) {
          temp = Math.ceil(tempProfiles.length / 20);
        }
      } else {
        if(val < 0){
          temp = 1;
        }else {
          temp = Math.ceil(tempProfiles.length / 20);
        }
      }

      Object.assign(this.paginationData, {
        index: temp,
        isFirstPage: temp == 1,
        isLastPage: temp == Math.ceil(tempProfiles.length / 20)
      });
    },
  },
  computed: {
    profilePopup() {
      return this.displayingProfiles[this.profilePopupIndex];
    },
    displayingProfiles() {
      let profileFilters = this.profileFilters

      let temp = this.profiles.slice();
      
      if(Object.keys(profileFilters).length > 0){
        for(let key in profileFilters){
          temp = temp.filter(el => el[key].toLowerCase() == profileFilters[key].toLowerCase())
        }
      }

      const startIndex =
        (this.paginationData.index - 1) * this.paginationData.perpage;
      const endIndexExclusive = startIndex + this.paginationData.perpage;
      return temp.slice(startIndex, endIndexExclusive);
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