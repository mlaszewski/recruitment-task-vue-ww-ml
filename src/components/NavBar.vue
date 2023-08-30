<template>
  <nav class="nav-bar">
    <div class="nav-bar__container">
      <div class="logo-container">
        <img src="/icons/logo.svg" class="logo" alt="logo" />
      </div>
      <button
          class="hamburger"
          :class="{'hamburger--active': isHamburgerActive}"
          aria-label="Menu"
          @click="() => this.isHamburgerActive = !this.isHamburgerActive"
      >
        <span class="hamburger__container" tabindex="-1">
          <span class="hamburger__bars"></span>
        </span>
      </button>
      <ul
          class="nav-list menu"
          :class="{'hidden': !isHamburgerActive}"
      >
        <li v-for="(item, index) in navItems" :key="index">
          <a
              class="nav-list--element"
              :href="`#${item.tag}`"
          >
            {{item.name.toUpperCase()}}
          </a>
        </li>
        <li>
          <a
              class="nav-list--element"
              :href="`#contact`"
              @click="contactModalHandler"
          >
            KONTAKT
          </a>
        </li>
      </ul>
      <ul
          class="nav-list links"
          :class="{'hidden': !isHamburgerActive}"
      >
        <li v-for="(link, index) in links" class="nav-list--link" :key="index">
          <img :src="`/icons/${link.name}.svg`" class="icon" :alt="link.name" />
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
  export default {
    props: ['contactModalHandler'],
    data() {
      return {
        isHamburgerActive: false,
        navItems: [
          {name: 'start', tag: 'start'},
          {name: 'o mnie', tag: 'about'},
          {name: 'galeria', tag: 'gallery'},
        ],
        links: [
          {name: 'facebook'},
          {name: 'instagram'},
          {name: 'youtube'},
        ]
      }
    }
  }
</script>

<style lang="scss">
  .nav-bar {
    height: 100px;
    width: 100%;
    background: #FFF;
    display: flex;
    position: fixed;
    z-index: 2;
    justify-content: center;
    align-items: center;
    border-bottom: 4px solid $color-accent;
    @media (max-width: $medium) {
      position: fixed;
      height: auto;
      padding: 10px;
      transition: .5s height;

      .hidden{
        display: none;
      }
    }
  }

  .nav-bar__container {
    display: flex;
    width: 100%;
    margin: 0 5vw;
    justify-content: flex-start;

    & *:last-child {
      margin-left: auto;
    }

    @media (max-width: $medium) {
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      gap: 1em;

      & *:last-child {
        margin: 0;
      }
    }
  }

  .logo-container{
    height: 50px;
    margin-right: 30px;
    display: flex;
    justify-content: center;
    align-items: center;

    .logo {
      height: 100%;
    }
  }

  .menu {
    @media (max-width: $medium) {
      flex-direction: column;
      gap: 1.5em;
      margin-bottom: 1.5em;
    }
  }
  .hamburger {
    display: none;
    @media (max-width: $medium) {
      display: block;
      margin: 0;
      padding: 0;
      border: 0;
      background-color: transparent;
      cursor: pointer;

      &:focus {
        & > .hamburger__container {
          box-shadow: 0 0 2px 2px #51a7e8;
        }
      }

      &,
      &__container {
        &:focus {
          outline: none;
        }
      }

      &__container {
        display: flex;
        align-items: center;
        position: relative;
        width: 30px;
        height: 20px;
      }

      &__bars {
        position: absolute;
        width: 30px;
        height: 2px;
        background-color: #000;
        transition: transform 220ms ease-in-out;

        &::before, &::after {
          display: block;
          position: absolute;
          width: 30px;
          height: 2px;
          background-color: #000;
          content: '';
        }

        &::before {
          top: -8px;
          transition: top 100ms 250ms ease-in, transform 220ms ease-in-out;
        }

        &::after {
          bottom: -8px;
          transition: bottom 100ms 250ms ease-in,
          transform 220ms ease-in-out;
        }
      }
    }

    &--active {
      .hamburger__bars {
        transform: rotate(225deg);
        transition: transform 220ms 120ms ease-in-out;

        &::before {
          top: 0;
          transition: top 100ms ease-out;
        }

        &::after {
          bottom: 0;
          transform: rotate(-90deg);
          transition: bottom 100ms ease-out,
          transform 220ms 120ms ease-in-out;
        }
      }
    }
  }

  .nav-list {
    display: flex;
    justify-content: center;
    align-items: center;
    list-style: none;

    .nav-list--element {
      margin-left: 20px;

      font-size: .75em;
      font-weight: 500;
      letter-spacing: 3px;
      color: $color-secondary;
      text-decoration: none;

      padding: 1em 3em;
      border-radius: 1.5em;
      @media (max-width: $medium) {
        margin-left: 0;
      }
    }
    .nav-list--element:hover {
      transition: .5s box-shadow;
      box-shadow: 0 0.4em 0.9em $color-accent--light;
    }
    .nav-list--link {
      margin-left: 20px;
    }
  }

  .nav-list--link:hover .icon {
    cursor: pointer;
    transition: .5s filter;
    filter: invert(1);
  }
</style>