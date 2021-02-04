<template>
  <div class="user-details">
    <div class="content">
      <div class="profile-photo"></div>
      <div class='close-button' @click="$emit(`close-button-clicked`)" v-show="showCloseButton"><i class="fas fa-times"></i></div>
      <div class="top">
        <div class="question-responses">
          <div class="questions">
            <div class="question">Name</div>
            <div class="question">Phone Number</div>
            <div class="question">Email</div>
            <div class="question">Username</div>
            <div class="question">Gender</div>
          </div>
          <div class="divider"></div>
          <div class="responses">
            <div class="response name">Oyinbo David</div>
            <div class="response">871-032-9564</div>
            <div class="response">byyQsZq@qGMgXDA.com</div>
            <div class="response">gIRpuhV</div>
            <div class="response">Female</div>
          </div>
        </div>
      </div>
      <div class="divider"></div>
      <div class="bottom">
        <div class="question-responses">
          <div class="questions">
            <div class="question">Domain Name</div>
            <div class="question">Payment Method</div>
            <div class="question">Mac Address</div>
            <div class="question">Last Login</div>
            <div class="question">LONG, LAT</div>
            <div class="question">Credit card number</div>
            <div class="question">credit card type</div>
            <div class="question">url</div>
          </div>
          <div class="divider"></div>
          <div class="responses">
            <div class="response">XfcAioj.org</div>
            <div class="response">paypal</div>
            <div class="response">34:62:89:02:64:89</div>
            <div class="response">1976-08-12 01:06:24</div>
            <div class="response">(40.2845, -170.1942)</div>
            <div class="response">372699563278638</div>
            <div class="response">American Express</div>
            <div class="response">https://www.VYwmvdX.info/</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    showCloseButton: {
      default: false
    }
  }
};
</script>

<style lang="scss">
@import "~assets/styles/variables";

.user-details {
  width: 100%;
  --profile-photo-size: 70px;
  --profile-photo-overflow: 20px;
  --content-padding: 16px;
  padding-left: var(--profile-photo-overflow);

  .content {
    width: 100%;
    background: white;
    border-radius: 5px;
    border: 1px solid rgba($color1, 0.25);
    box-shadow: 0px 2px 10px 3px rgba($color1, 0.2);
    padding: var(--content-padding);
    position: relative;

    & > .close-button {
      color: red;
      font-size: 16px;
      position: absolute;
      top: var(--content-padding);
      right: var(--content-padding);
    }

    & > .profile-photo {
      position: absolute;
      top: var(--content-padding);
      left: calc(-1 * var(--profile-photo-overflow));
      height: var(--profile-photo-size);
      width: var(--profile-photo-size);

      border-radius: 50%;
      background: url("/images/male.jpg");
      background-position: center center;
      background-size: cover;
      background-repeat: no-repeat;
      border: 1px solid rgba($color1, 0.35);
    }
    & > .divider {
      height: 1px;
      background: rgba($color1, 0.15);
      width: 100%;
    }

    .top {
        padding-left: calc( var(--profile-photo-size) - var(--profile-photo-overflow));
        margin: 22px 0;
    }
    .bottom {
        margin: 22px 0;
    }
  }

  
}
</style>