<template>
  <div class="user-details">
    <div class="content">
      <div class="profile-photo"></div>
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
export default {};
</script>

<style lang="scss">
@import "~assets/styles/variables";

.user-details {
  width: 100%;
  --profile-photo-size: 70px;
  --profile-photo-overflow: 20px;
  --content-padding: 12px;
  padding-left: var(--profile-photo-overflow);

  .content {
    width: 100%;
    background: white;
    border-radius: 5px;
    border: 1px solid rgba($color1, 0.25);
    box-shadow: 0px 2px 10px 3px rgba($color1, 0.2);
    padding: var(--content-padding);
    position: relative;

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
        padding-left: calc( var(--profile-photo-size) - var(--profile-photo-overflow))
    }
  }

  .question-responses {
    display: grid;
    grid-template-columns: max-content 2px 1fr;
    gap: 10px;
    margin-top: 10px;
    margin-bottom: 10px;
    line-height: 25px;
    font-size: 15px;

    .question {
      text-transform: uppercase;
      color: $color1;
    }

    .response {
      color: $color4;
      &.name {
        color: $color3;
      }
    }

    & > .divider {
      width: 1px;
      background: rgba($color1, 0.15);
    }
  }
}
</style>