<template>
  <div class="gvb_logo">
    <img src="/image/logo.png" alt="">
    <div class="logo_head">
      <div>枫枫知道</div>
      <div>fengfengzhidao</div>
    </div>
  </div>
</template>

<style lang="scss">
.gvb_logo {
  height: 90px;
  display: flex;
  padding: 20px;
  align-items: center;
  border-bottom: 1px solid var(--bg);
  transition: all .3s;

  img {
    width: 60px;
    height: 60px;
    transition: all .3s;
  }

  .logo_head {
    margin-left: 20px;
    transition: all .3s;
    transform: scale(1);
    transform-origin: left;

    > div:nth-child(1) {
      font-size: 22px;
      font-weight: 600;
      margin-bottom: 2px;
    }

    > div:nth-child(2) {
      font-size: 12px;
    }
  }
}

.collapsed {
  .gvb_logo {
    padding: 2px;

    img {
      width: 42px;
      height: 42px;
    }

    .logo_head {
      transform: scale(0);
    }
  }
}
</style>