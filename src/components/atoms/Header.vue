<template>
  <header class="header">
    <div class="header__navbar">
      <ul class="header__items">
        <li class="header__item" v-for="(link, index) in links" :key="index">
          <a :href="link.url">
            {{ link.title }}
          </a>          
        </li>
      </ul>
    </div>
  </header>
  <div>

  </div>
</template>

<script>
  export default {
    name: 'Header',
    props: ['links']  
  }
</script>

<style lang="scss">
  .header {
    position: absolute;
    top: 0;
    z-index: 1000;
    width: 100%;
    color: #fff;

    &__navbar,
    &__items  {
      display: flex;
      align-items: center;
    }

    &__navbar {
      height: 60px;
      justify-content: flex-end;
    }

    &__item {
      padding: 0 30px;
      letter-spacing: 0.5px;
      color: rgba(255, 255, 255, 0.7);
      cursor: pointer;
      &:hover {
        color: #fff;
      }
    }
  }
</style>