<template>
  <div class="header">
    <div class="wrapper--logo">
      <h1>MAZ</h1>
    </div>
    <div class="wrapper--link">
      <p>پروژه ها</p>
      <p>درباره ی من</p>
      <p>ارتباط با من</p>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 50px;
  height: 80px;
  width: 90%;
  .wrapper--link {
    display: flex;
    p {
      margin-left: 10px;
    }
  }
}
</style>