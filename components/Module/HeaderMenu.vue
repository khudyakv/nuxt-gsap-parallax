<template>
  <div>
    <div class="header__nav" :class="{ header__nav_opened: opened }">
      <button class="header__nav-toggle" @click="opened = !opened">
        <div></div>
        <div></div>
        <div></div>
      </button>
      <div class="header__nav-window">
        <div class="container-fluid">
          <div class="header__nav-list">
            <a href="#" class="header__nav-item">Home</a>
            <a href="#" class="header__nav-item">Services</a>
            <a href="#" class="header__nav-item">About</a>
            <a href="#" class="header__nav-item">Contacts</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      opened: false,
    };
  },
  methods: {
    toggleMenu() {
      opened = !opened;
      return opened;
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  &__nav {
    z-index: 0;
    mix-blend-mode: difference;

    &-toggle {
      background: transparent;
      border: 0;
      display: block;
      padding: 3px;
      mix-blend-mode: difference;
      div {
        width: 1rem;
        height: 2px;
        border-radius: 3px;
        background: #fff;
        transition: opacity 0.6s ease, transform 0.6s ease;
        &:not(&:last-child) {
          margin-bottom: 3px;
        }
        &:first-child,
        &:last-child {
          width: 50%;
        }
        &:last-child {
          margin-left: auto;
        }
      }
    }

    &-window {
      padding: 9rem 0;
      display: flex;
      align-items: center;
      z-index: -1;
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      color: #000;
      background: #fff;
      transition: transform 0.6s ease;
      transform: translateY(100%);
    }
    &-list {
      display: flex;
      justify-content: space-around;
    }
    &-item {
      display: block;
      position: relative;
      color: #000;
      font-size: 3rem;
      margin-bottom: 2.75rem;
      text-decoration: none;
      animation: none;
      opacity: 0;
      transition: opacity 0.3s ease;
      &::after {
        content: "";
        width: 0%;
        position: absolute;
        top: 100%;
        height: 3px;
        left: 0%;
        background: #000;
        transition: width 0.3s ease;
      }
      &:hover {
        &::after {
          width: 100%;
        }
      }
    }
    &_opened {
      .header__nav-window {
        transform: translateY(0%);
      }
      .header__nav-item {
        animation: fromDown 0.9s ease 1;
        animation-fill-mode: forwards;
        @for $i from 2 to 5 {
          &:nth-child(#{$i}) {
            animation-delay: $i * 0.075s;
          }
        }
      }
      .header__nav-toggle {
        div {
          &:nth-child(1) {
            width: 100%;
            transform: translateY(0.315rem) rotate(45deg);
          }
          &:nth-child(2) {
            opacity: 0;
            transform: translateX(100%);
          }
          &:nth-child(3) {
            width: 100%;
            transform: translateY(-0.315rem) rotate(-45deg);
          }
        }
      }
    }
  }
}

@keyframes fromDown {
  from {
    transform: translateY(30vh);
    opacity: 0;
  }
  to {
    transform: none;
    opacity: 1;
  }
}
</style>
