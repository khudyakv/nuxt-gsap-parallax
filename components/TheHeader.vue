<template>
  <header class="header">
    <div class="container-fluid">
      <div class="header__grid">

        <div class="header__left">
          <ModuleHeaderMenu />

          <div class="header__social">
            <a href="#" class="header__social-link">
              <img src="@/assets/img/icons/insta.svg" alt="">
            </a>
            <a href="#" class="header__social-link">
              <img src="@/assets/img/icons/medium.svg" alt="">
            </a>
            <a href="#" class="header__social-link">
              <img src="@/assets/img/icons/dribble.svg" alt="">
            </a>
            <a href="#" class="header__social-link">
              <img src="@/assets/img/icons/behance.svg" alt="">
            </a>
          </div>
        </div>

        <div class="header__center">
          <a href="" class="header__logo">
            <img src="@/assets/img/partials/header-logo.svg" alt="Logotype alt" class="header__logo-image" />
          </a>
        </div>
        

        <div class="header__right">
          <nav class="header__links">
            <a href="#" class="header__links-item">Explore</a>
            <a href="#" class="header__links-item">Store</a>
          </nav>
        </div>


      </div>
    </div>
  </header>
</template>

<script>
import { gsap } from "gsap";

export default {
  mounted() {
    this.animateStart();
  },
  methods: {
    animateStart() {
      const tl = gsap.timeline();
      tl.from(".header__nav-toggle", {  duration: 0.5, opacity: 0 })
        .from(".header__social-link", {
          opacity: 0,
          stagger: 0.15, duration: 0.5
        }, "-=0.5")
        .from(".header__logo", {duration: 0.5, opacity: 0 }, "-=0.15")
        .from(".header__links-item", {
          opacity: 0,
          stagger: 0.15, duration: 0.5
        }, "-=0.5")
        
    },
  },
};
</script>


<style lang="scss">
  .header {
    padding: 2.5rem 0;

  z-index: 1;
  position: relative;
    &__grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      align-items: center;
      gap: 1rem;
    }

    &__left {
      display: flex;
      align-items: center;
    }

    &__center {
      display: flex;
      justify-content: center;
    }

    &__right {
      display: flex;
      justify-content: flex-end;
    }

    

    &__social {
      margin-left: 34%;
      display: flex;
      align-items: center;
      &-link {
        color: #fff;
        max-width: 1.25rem;
        max-height: 1.25rem;
        display: flex;
        &:not(&:first-child) {
          margin-left: 1.3rem;
        }
        img {
          max-width: 100%;
          max-height: 100%;
          object-fit: contain;
        }
      }
    }

    &__logo {
      margin-bottom: -2px;
    }

    &__links {
      &-item {
        color: #fff;
        text-decoration: none;
        font-size: 0.875rem;
        &:not(&:first-child) {
          margin-left: 3.75rem;
        }
      }
    }

  }
</style>
