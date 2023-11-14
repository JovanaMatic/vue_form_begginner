<template>
  <div class="main-div">
    <div class="container">
      <slot></slot>
    </div>
  </div>
</template>

<script>

</script>

<style scoped>
  .main-div {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    background-color: #fff;
    min-width: 700px;
    min-height: 200px;
  }
</style>