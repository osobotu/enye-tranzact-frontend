<template>
  <div class="user-details">
    <div class="content">
      <div class="profile-photo" :class="{female: (profile.Gender || '').toLowerCase() == `female`}"></div>
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
            <div class="response name">{{`${profile.FirstName} ${profile.LastName}`}}</div>
            <div class="response">{{profile.PhoneNumber}}</div>
            <div class="response">{{profile.Email}}</div>
            <div class="response">{{profile.UserName}}</div>
            <div class="response">{{profile.Gender}}</div>
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
            <div class="response">{{profile.DomainName}}</div>
            <div class="response">{{profile.PaymentMethod}}</div>
            <div class="response">{{profile.MacAddress}}</div>
            <div class="response">{{profile.LastLogin}}</div>
            <div class="response">({{profile.Longitude}}, {{profile.Latitude}})</div>
            <div class="response">{{profile.CreditCardNumber}}</div>
            <div class="response">{{profile.CreditCardType}}</div>
            <div class="response">{{profile.URL}}</div>
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
    },
    profile: {
      required: true,
      default: {}
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

      &.female {
        background-image: url("/images/female.jpg");
      }
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