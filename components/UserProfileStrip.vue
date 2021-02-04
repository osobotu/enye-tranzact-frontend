<template>
  <div class="user-profile-strip">
    <div class="profile-container">
      <div class="profile-photo-container">
        <div class="profile-photo" :class="{female: (profile.Gender || '').toLowerCase() == `female`}"></div>
      </div>
      <div class="content">
        <div class="options-container" @click="showModal()">
          <i class="fas fa-ellipsis-v"></i>
        </div>
        <div class="question-responses">
          <div class="questions">
            <div class="question">Name</div>
            <div class="question">phone number</div>
            <div class="question">Last login</div>
          </div>
          <div class="divider"></div>
          <div class="responses">
            <div class="response name">{{`${profile.FirstName} ${profile.LastName}`}}</div>
            <div class="response">{{profile.PhoneNumber}}</div>
            <div class="response">{{profile.LastLogin}}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="border-bottom"></div>
  </div>
</template>

<script>
export default {
  props: {
    profile: {
      required: true
    }
  },
  methods: {
    showModal() {
      this.$emit("show-modal");
    }
  }
};
</script>

<style lang="scss">
@import "~assets/styles/variables";
.user-profile-strip {
  --strip-padding: 12px;
  padding: var(--strip-padding) var(--body-padding);
  padding-bottom: 0;
  background: white;
  position: relative;

  .options-container {
    position: absolute;
    top: var(--strip-padding);
    right: var(--body-padding);
    cursor: pointer;
  }
  .border-bottom {
    height: 1px;
    width: 100%;
    margin-top: var(--strip-padding);
    background: #e5e5e5;
  }

  .profile-container {
    --profile-picture-size: 48px;
    display: grid;
    align-items: center;
    gap: 10px;
    grid-template-columns: var(--profile-picture-size) 1fr;
    overflow: hidden;

    @media only screen and (min-width: 375px) {
      --profile-picture-size: 56px;
    }
    .profile-photo-container {
      .profile-photo {
        height: var(--profile-picture-size);
        width: 100%;
        border-radius: 50%;
        background: url("/images/male.jpg");
        background-size: cover;
        background-position: center center;
        background-repeat: no-repeat;
        &.female {
          background-image: url("/images/female.jpg");
        }
      }
    }
  }
}
</style>