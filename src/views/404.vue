<template>
  <div class="http404">
    <div class="http404_icon">
      <img src="@/assets/404_images/404.png" alt="404">
    </div>
    <div class="http404_cont">
      <div class="http404__title">
        {{ message }}
      </div>
      <div class="http404__desc">
        Sorry, we couldn't find the page you were looking for.
      </div>
      <el-button type="primary"><router-link to="/">Back to home</router-link></el-button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Page404',
  computed: {
    message() {
      return 'Ah! Page not found'
    }
  }
}
</script>

<style lang="scss" scoped>
.http404 {
  height: 100%;
  padding: 16px 0;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;

  img {
    height: 180px;
  }

  .http404__title {
    color: #323639;
    font-size: 36px;
    line-height: 40px;
    margin-top: 32px;
  }

  .http404__desc {
    color: #71717A;
    font-size: 18px;
    line-height: 28px;
    margin: 16px 0;
  }

  .http404_cont {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
}
</style>
