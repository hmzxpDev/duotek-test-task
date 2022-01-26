<template>
  <header class="header" :class="versionBackground">
    <div class="header__container">
      <div class="header__name">
        <div class="header__logo" :class="versionLogo">L</div>
        <div class="header__logo-title" :class="verisonLogoTitle">Logo</div>
      </div>
      <div class="header__burger-menu">
        <span></span>
      </div>
      <div class="header__nav-menu">
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
      </div>
      <div class="header__nav-menu header__auth">
        <nuxt-link to="/auth" :class="versionLink" class="header__link-item"
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
    };
  },
  methods: {
    styleRender() {
      if (this.headerStyle === "light") {
        this.versionBackground = "header--light-version";
        this.versionLogo = "header__logo--light-version";
        this.verisonLogoTitle = "header__logo-title--light-version";
        this.versionLink = "header__link-item--light-version";
      }
      if (this.headerStyle === "dark") {
        this.versionBackground = "header--dark-version";
        this.versionLogo = "header__logo--dark-version";
        this.verisonLogoTitle = "header__logo-title--dark-version";
        this.versionLink = "header__link-item--dark-version";
      }
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
  &__nav-menu {
    max-width: 500px;
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
.header__link-item:hover {
  opacity: 0.3;
}
.nuxt-link-active {
  opacity: 0.3;
}

.header__link-item--active {
  opacity: 0.3;
}
</style>
