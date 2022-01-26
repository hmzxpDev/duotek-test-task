<template>
  <header class="header" :class="versionBackground">
    <div class="header__container">
      <div class="header__name">
        <div class="header__logo" :class="versionLogo">L</div>
        <div class="header__logo-title" :class="verisonLogoTitle">Logo</div>
      </div>
      <div
        class="header__burger-menu"
        :class="burgerMenuStyle()"
        @click="openBurgerMenu"
      >
        <span></span>
        <span></span>
        <span></span>
      </div>
      <div
        class="header__nav-menu"
        :class="{ 'header__nav-menu--active': bugerMenuOpen }"
      >
        <nuxt-link to="/tenders" :class="versionLink" class="header__link-item"
          >Тендеры</nuxt-link
        >
        <nuxt-link
          to="/companies"
          :class="versionLink"
          class="header__link-item"
          >Компании</nuxt-link
        >
        <nuxt-link to="/products" :class="versionLink" class="header__link-item"
          >Продукты</nuxt-link
        >
        <nuxt-link to="/cases" :class="versionLink" class="header__link-item"
          >Кейсы</nuxt-link
        >
        <nuxt-link to="/blocks" :class="versionLink" class="header__link-item"
          >Блог</nuxt-link
        >
        <nuxt-link
          to="/auth"
          :class="versionLink"
          class="header__link-item header__auth"
          >Вход и регистрация</nuxt-link
        >
      </div>
    </div>
  </header>
</template>

<script>
export default {
  props: ["headerStyle"],
  data() {
    return {
      versionBackground: "",
      versionLink: "",
      versionLogo: "",
      verisonLogoTitle: "",
      versionBurgerMenu: "",
      bugerMenuOpen: false,
    };
  },
  methods: {
    styleRender() {
      if (this.headerStyle === "light") {
        this.versionBackground = "header--light-version";
        this.versionLogo = "header__logo--light-version";
        this.verisonLogoTitle = "header__logo-title--light-version";
        this.versionLink = "header__link-item--light-version";
        this.versionBurgerMenu = "header__burger-menu--light-verison";
      }
      if (this.headerStyle === "dark") {
        this.versionBackground = "header--dark-version";
        this.versionLogo = "header__logo--dark-version";
        this.verisonLogoTitle = "header__logo-title--dark-version";
        this.versionLink = "header__link-item--dark-version";
        this.versionBurgerMenu = "header__burger-menu--dark-verison";
      }
    },
    openBurgerMenu() {
      if (document.body.style.overflow === "hidden") {
        document.body.style.overflow = "scroll";
      } else {
        document.body.style.overflow = "hidden";
      }
      this.bugerMenuOpen = !this.bugerMenuOpen;
    },
    burgerMenuStyle() {
      return this.bugerMenuOpen
        ? `header__burger-menu--active ${this.versionBurgerMenu}`
        : `${this.versionBurgerMenu}`;
    },
  },
  mounted() {
    this.styleRender();
  },
};
</script>

<style lang="scss">
.header {
  width: 100%;
  border-bottom: 1px solid #f2f2f2;
  height: 100px;

  &__container {
    height: 100%;
    max-width: 1200px;
    margin: auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__name {
    display: flex;
  }

  &__logo {
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    font-size: 40px;
    font-weight: bold;
  }

  &__logo-title {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-left: 8px;
    font-weight: bold;
    font-size: 33px;
  }

  &__burger-menu {
    display: none;
  }
  &__auth {
    margin-left: 174px;
  }
  &__nav-menu {
    a {
      margin-left: 40px;
    }
    display: flex;
    justify-content: space-between;
  }

  &__link-item {
    text-decoration: none;
    font-size: 16px;
    font-weight: 600;
  }
}
.header--light-version {
  background-color: white;
}
.header--dark-version {
  background: #030953;
}
.header__burger-menu--light-verison {
  span {
    background: #030953;
  }
}

.header__burger-menu--dark-verison {
  span {
    background: white;
  }
}
.header__logo--light-version {
  background-color: #030953;
  color: white;
}
.header__logo--dark-version {
  background-color: white;
}
.header__logo--title_light-version {
  color: #030953;
}
.header__logo-title--dark-version {
  color: white;
}
.header__link-item--light-version {
  color: #030953;
}
.header__link-item--dark-version {
  color: white;
}
.nuxt-link-active {
  opacity: 0.3;
}

.header__link-item--active {
  opacity: 0.3;
}

@media (max-width: 1100px) {
  .header {
    &__name {
      z-index: 4;
      margin-left: 20px;
    }

    &__burger-menu {
      margin-right: 20px;
      z-index: 4;
      width: 40px;
      height: 30px;
      display: flex;
      justify-content: space-between;
      flex-direction: column;
      span {
        height: 4px;
        width: 100%;
      }
    }

    &__burger-menu--active {
      overflow: hidden;
      position: relative;
      justify-content: center;
      span {
        transition-duration: 0.3s;
        position: absolute;
        transform: rotate(45deg);
      }
      span:nth-child(2) {
        display: none;
      }
      span:nth-child(3) {
        transform: rotate(-45deg);
      }
    }

    &__nav-menu {
      display: none;
      margin-left: 0;
    }

    &__nav-menu--active {
      margin-top: 100px;
      padding: 47px 0px 40px 0px;
      display: flex;
      flex-direction: column;
      a {
        color: #030953;
        display: flex;
        justify-content: center;
        margin-left: 0px;
      }
      a:last-child {
        padding-top: 30px;
        border-top: 1px solid #f2f2f2;
        margin-top: 48px;
      }
      background-color: white;
      top: 0;
      z-index: 3;
      position: fixed;
      width: 100vw;
      height: 90vh;
    }
  }
}
</style>
