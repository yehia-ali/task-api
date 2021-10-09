<template>
  <section>
    <div class="banner">
      <div class="banner-heading">
        <h1 class="heading text-white text-uppercase">
          what our users say about shahry ?
        </h1>
        <button
          type="button"
          class="btn btn-addReview"
          data-bs-toggle="modal"
          data-bs-target="#AddReview"
        >
          Add Review
        </button>
      </div>
    </div>
    <app-popup></app-popup>
  </section>
</template>

<style lang="scss">
.banner {
  height: 80vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.3)),
    url(https://images.unsplash.com/photo-1619335680666-6e861493383d?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxfDB8MXxhbGx8fHx8fHx8fHwxNjIxOTk1NzY4&ixlib=rb-1.2.1&q=80&w=1080&utm_source=unsplash_source&utm_medium=referral&utm_campaign=api-credit);
  background-size: cover;
  background-position: top;
  position: relative;
  .banner-heading {
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: #aaa;
    white-space: nowrap;
    text-align: center;
    .heading {
      display: block;
      font-size: 3.125rem;
      @media screen and (max-width: 576px) {
        font-size: 18px;
      }
    }
  }
  .btn-addReview {
    color: #00b991;
    background: #fff;
    padding: 8px 40px;
    margin-top: 50px;
    transition: all 0.4s;
    &:focus {
      outline: none;
      box-shadow: none;
    }
    &:hover {
      background: #00b991;
      color: #fff;
    }
  }
}
</style>

<script>
import AppPopup from "../components/app-popup.vue";
export default {
  components: {
    AppPopup,
  },
};
</script>
