<template>
  <div>
    <app-header> </app-header>
    <app-banner> </app-banner>

    <div class="container-fluid">
      <section>
        <app-reviws></app-reviws>
      </section>
    </div>
  </div>
</template>

<style lang="scss">
.btn-green {
  background: #00b991;
  color: #fff;
  padding: 8px 40px;
  border: 1px solids transparent;
  transition: all 0.4s;
  &:focus {
    outline: none;
    box-shadow: none;
  }
  &:hover {
    color: #00b991;
    background: #fff;
    border: 1px solid #00b991;
  }
}
input,
textarea {
  &.form-control {
    background: #ebf0f2;
    &:focus {
      outline: none;
      box-shadow: none;
    }
  }
}
</style>
<script>
import AppHeader from "../components/app-header";
import AppBanner from "../components/app-banner.vue";
import AppReviws from "../components/app-reviws.vue";

export default {
  components: {
    AppHeader,
    AppBanner,
    AppReviws,
  },
};
</script>
