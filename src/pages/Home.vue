<template>
  <div v-if="isLoading" class="home__loader content-center">
    <div class="lds-roller">
      <div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>
  </div>
  <template v-else>
    <Header :links="linksHeader"/>
    <main class="home__banner content-center animate animate__fadeIn">
      <h1 class="home__banner-title">Piura</h1>
      <div class="home__banner-wave" style="height: 150px; overflow: hidden;" >
        <svg viewBox="0 0 500 150" preserveAspectRatio="none" style="height: 100%; width: 100%;"><path d="M-20.09,101.94 C150.00,150.00 371.56,9.19 505.30,100.95 L500.00,150.00 L0.00,150.00 Z" style="stroke: none; fill: #fff;"></path></svg>
      </div>
      <div class="home__banner-button-scroll">
        <a href="#foods">
          <div class="home__banner-wheel-wrapper">
            <div class="home__banner-wheel"></div>
          </div>
        </a>
      </div>
    </main>
    <section id="foods" class="home__foods content-center">
      <div class="home__foods-content">
        <h2 class="home__foods-title">Gastronomía</h2>
        <p class="home__foods-paragraph">
          Al llegar a Piura, piensas en dos cosas: playas y un buen cebiche frente al mar. Indiscutiblemente la gastronomía norteña tiene un lugar importante entre las comidas fundamentales del Perú.
          Para la mayoría de los peruanos los cebiches piuranos son únicos, el seco de chavelo ni qué hablar, los tamalitos verdes son a pedir de boca, el sudado de cachema y el majao de yuca es riquísimo. Hay realmente una combinación de sabores, donde se aliñan y se cruzan sazones sabrosas.
        </p>        
      </div>
      <div class="home__foods-cards">
        <div class="home__foods-card" v-for="(food, index) in gastronomy" :key="index" >
          <Card :description="food.description" :image="food.image" />
        </div>
      </div>
    </section>
    <section class="home__tourism">
      <h2 class="home__tourism-title">Turismo</h2>
    </section>
  </template> 
  
</template>

<script>
  import Header from '../components/atoms/Header'
  import Card from '../components/atoms/Card'

  export default {
    name: 'Home',
    components: {
      Header,
      Card
    },
    data() {
      return {
        isLoading: true,
        linksHeader: [
          {
            title: 'Gastronomía',
            url: '#foods'
          },
          {
            title: 'Turismo',
            url: '#tourism'
          }
        ],
        gastronomy: [
          {
            title: 'Frito',
            image: 'frito.jpg',
            description: ''
          },
          {
            title: 'Ceviche de caballa',
            image: 'ceviche-de-caballa.jpg',
            description: ''
          },
          {
            title: 'Ronda Criolla',
            image: 'ceviche-de-caballa2.jpg',
            description: ''
          }
        ],
        isScrollFoods: true
      }
    },
    mounted() {
      setTimeout(() => {
        this.isLoading = false;          
        }, 3000);
       
    }
  }
</script>

<style lang="scss">
  .home {    
    &__loader {
      height: 100vh;
    }

    &__banner {
      position: relative;
      height: 100vh;
      min-height: 350px;
      width: 100%;
      background: -webkit-linear-gradient(to right, rgba(0, 34, 62, 0.60), rgba(255, 161, 127, 0.60)), url("../assets/main.jpg");
      background: linear-gradient(to right,  rgba(0, 34, 62, 0.60), rgba(255, 161, 127, 0.60)), url("../assets/main.jpg");
      background-repeat: no-repeat;
      background-size: cover;   
  
      &-title {
        color: #fff;
        text-align: center;
        font: 120px/1 'TeXGyreAdventorBold';
        text-transform: none;
        transform: translate3d(0,0,0);
        animation: text-in-expand 1s cubic-bezier(0.215, 0.610, 0.355, 1.000) both;
      }

      &-wave {
        position: absolute;
        width: 100%;
        bottom: 0;
      }

      &-button-scroll {
        position: absolute;
        bottom: 100px;
        left: 50%;
        transform: translateX(-50%);
        width: 30px;
        height: 48px;
        cursor: pointer;
      }

      &-wheel-wrapper {
        width: 100%;
        height: 100%;
        border: 2px solid #fff;
        border-radius: 15px;
      }

      &-wheel {
        margin: 0 0 0 -2px;
        position: absolute;
        top: 10px;
        left: 50%;
        width: 4px;
        height: 4px;
        background: #fff;
        border-radius: 50%;
        animation: scroll-wheel 1.8s linear 0s infinite normal none;
      }
    }

    &__foods {
      height: 100vh;      

      &-content {
        padding-left: 50px;
        width: 40%;
        min-width: 300px;
      }

      &-title {
        margin-bottom: 20px;
        font-size: 36px;
      }

      &-paragraph {        
        font-size: 18px;
        line-height: 30px;
      }

      &-cards {
        position: relative;
        width: 60%;
        height: 100%;
      }

      &-card {
        position: absolute;
        max-width: 200px;

        &:first-child {
          top: 25%;          
          left: 15%;
          transform: translate(-15%, -25%);
          z-index: 1;
        }

        &:nth-child(2) {
          top: 50%;          
          left: 50%;
          transform: translate(-50%, -50%);
          z-index: 2;
        }

        &:last-child {
          top: 75%;          
          left: 75%;
          transform: translate(-75%, -75%);
          z-index: 3;
        }
      }
    }

    &__tourism {
      &-title {
        text-align: center;
        font-size: 32px;
      }
    }
    
  }

  @keyframes scroll-wheel {
    0% {
      -moz-transform: translate3d(0,0,0);
      -webkit-transform: translate3d(0,0,0);
      transform: translate3d(0,0,0);
      opacity: 1;
    }

    35% {
      -moz-transform: translate3d(0,7px,0);
      -webkit-transform: translate3d(0,7px,0);
      transform: translate3d(0,7px,0);
      opacity: 1;
    }

    50% {
      -moz-transform: translate3d(0,10px,0);
      -webkit-transform: translate3d(0,10px,0);
      transform: translate3d(0,10px,0);
      opacity: 0;
    }

    80% {
      -moz-transform: translate3d(0,0,0);
      -webkit-transform: translate3d(0,0,0);
      transform: translate3d(0,0,0);
      opacity: 0;
    }
  } 
</style>