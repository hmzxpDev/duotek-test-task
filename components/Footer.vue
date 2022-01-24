<template>
  <div class="footer">
    <div class="footer__container">
      <div class="footer__nav-menu">
        <div class="footer__column">
          <div to="#" class="footer__row-title">Тендеры</div>
          <nuxt-link to="#" class="footer__row footer__row--blue">
            Добавить тендер
          </nuxt-link>
          <nuxt-link to="#" class="footer__row">Каталог тендеров</nuxt-link>
          <nuxt-link to="#" class="footer__row">Работа с клиентами</nuxt-link>
          <nuxt-link to="#" class="footer__row">Управление проектами</nuxt-link>
          <nuxt-link to="#" class="footer__row">Маркетинг</nuxt-link>
          <nuxt-link to="#" class="footer__row">Финансы</nuxt-link>
          <nuxt-link to="#" class="footer__row">Управлением бизнесом</nuxt-link>
        </div>
        <div class="footer__column">
          <div class="footer__row-title">Компании</div>
          <nuxt-link class="footer__row footer__row--red">
            Добавить компанию
          </nuxt-link>
          <nuxt-link to="#" class="footer__row">Рейтинги</nuxt-link>
          <nuxt-link to="#" class="footer__row"
            >Отраслевая специализация</nuxt-link
          >
          <nuxt-link to="#" class="footer__row">Интеграторы</nuxt-link>
          <nuxt-link to="#" class="footer__row"
            >Решения для бизнеса крепеж</nuxt-link
          >
          <nuxt-link to="#" class="footer__row">Разработка сайтов</nuxt-link>
          <nuxt-link to="#" class="footer__row">Мобильные приложения</nuxt-link>
          <nuxt-link to="#" class="footer__row">Онлайн-реклама</nuxt-link>
          <nuxt-link to="#" class="footer__row">Контент</nuxt-link>
        </div>
        <div class="footer__column">
          <div class="footer__row-title">Продукты</div>
          <nuxt-link to="#" class="footer__row">Рейтинги</nuxt-link>
          <nuxt-link to="#" class="footer__row">По отраслям</nuxt-link>
          <nuxt-link to="#" class="footer__row">Работа с клиентами</nuxt-link>
          <nuxt-link to="#" class="footer__row">Управление проектами</nuxt-link>
          <nuxt-link to="#" class="footer__row">Маркетинг</nuxt-link>
          <nuxt-link to="#" class="footer__row">Финансы</nuxt-link>
          <nuxt-link to="#" class="footer__row">Управление бизнесом</nuxt-link>
        </div>
        <div class="footer__column">
          <div class="footer__row-title">Кейсы</div>
          <nuxt-link to="#" class="footer__row"
            >Автоматизация сантехников</nuxt-link
          >
          <nuxt-link to="#" class="footer__row"
            >Автоматизация клининга</nuxt-link
          >
          <nuxt-link to="#" class="footer__row">Автоматизация СТО</nuxt-link>
          <nuxt-link to="#" class="footer__row"
            >Автоматизация сантехников</nuxt-link
          >
          <nuxt-link to="#" class="footer__row"
            >Автоматизация клининга</nuxt-link
          >
          <nuxt-link to="#" class="footer__row">Автоматизация СТО</nuxt-link>
        </div>
      </div>
      <div class="footer__other">
        <div class="footer__social">
          <div class="footer__social-item">
            <img src="/social/facebook.svg" alt="social" />
          </div>
          <div class="footer__social-item">
            <img src="/social/vk.svg" alt="social" />
          </div>
          <div class="footer__social-item">
            <img src="/social/youtube.svg" alt="social" />
          </div>
        </div>
        <div class="footer__about-project">
          <div class="footer__about-project-item">О проекте</div>
          <div class="footer__about-project-item">
            Пользовательское соглашение
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.footer {
  height: 600px;
  &__container {
    width: 1200px;
    margin: auto;
    height: 400px;
    margin-top: 80px;
    padding: 0px 30px 0px 30px;
  }

  &__nav-menu {
    display: flex;
    justify-content: space-between;
  }

  &__row-title {
    font-size: 16px;
    color: #000000;
    font-weight: 500;
  }

  &__row {
    margin-top: 16px;
    font-size: 14px;
    cursor: pointer;
    &--blue {
      width: 152px;
      height: 32px;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #030953;
      border-radius: 4px;
      color: white;
    }

    &--red {
      width: 190px;
      height: 32px;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #ef3e4a;
      border-radius: 4px;
      color: white;
    }
  }

  &__other {
    display: flex;
    justify-content: space-between;
    margin-top: 26px;
  }

  &__social {
    display: flex;
  }

  &__social-item {
    margin-right: 20px;
  }

  &__about-project {
    display: flex;
  }

  &__about-project-item {
    margin-right: 20px;
    font-size: 12px;
    color: #808080;
  }
}
</style>
