<template>
  <nav>
    <ul>
      <li>
        <div>
          <img src="@/assets/images/aims.svg" alt="">
        </div>
        <div>任務</div>
      </li>
      <li>
        <div><img src="@/assets/images/home.svg" alt=""></div>
        <div>任務</div>
      </li>
      <li>
        <div><img src="@/assets/images/star-vip.svg" alt=""></div>
        <div>VIP</div>
      </li>
      <li>
        <div><img src="@/assets/images/user.svg" alt=""></div>
        <div>我的</div>
      </li>
    </ul>
  </nav>
</template>

<script>
import aims from '@/assets/images/aims.svg';

export default {
  name: 'Navegation',
  components: {
    aims
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
nav {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 10vh;
}

ul {
  display: flex;
  justify-content: space-between;
  text-align: center;
  color: #717171;
  font-size: 12px;
  padding-top: 15px;
}

li {
  flex: 1 0 25%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

img {
  width: 25px;
}
</style>
