<template>
  <header class="bg-white">
    <nav class="navbar navbar-light bg-white p-0">
      <a class="navbar-brand p-0"><img src="@/assets/logo.svg"/></a>
      <ul class="list-inline vertical-align-center m-0">
        <li class="list-inline-item fw-bold">
          <img src="@/assets/user.png" />Khaled Mohammed
        </li>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss">
header {
  padding: 1rem 6rem;
  @media screen and (max-width: 576px) {
    padding: 1rem;
  }
  .navbar-brand {
    img {
      height: 40px;
      vertical-align: middle;
      display: inline-block;
      @media screen and (max-width: 576px) {
        height: 30px;
      }
      @media screen and (max-width: 320px) {
        height: 20px;
      }
    }
  }
  ul {
    li {
      color: #6c6c6c;
      img {
        width: 30px;
        border-radius: 50%;
        margin-right: 5px;
      }
    }
  }
}
</style>

<script>
export default {};
</script>
