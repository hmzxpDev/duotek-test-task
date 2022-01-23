<template>
  <div class="footer">
    <div class="footer__container">
      <div class="footer__nav-menu">
        <div class="footer__column">
          <div class="footer__row-title">Тендеры</div>
          <div class="footer__row footer__row_tender-custom">
            Добавить тендер
          </div>
          <div class="footer__row">Каталог тендеров</div>
          <div class="footer__row">Работа с клиентами</div>
          <div class="footer__row">Управление проектами</div>
          <div class="footer__row">Маркетинг</div>
          <div class="footer__row">Финансы</div>
          <div class="footer__row">Управлением бизнесом</div>
        </div>
        <div class="footer__column">
          <div class="footer__row-title">Компании</div>
          <div class="footer__row footer__row_company-custom">
            Добавить компанию
          </div>
          <div class="footer__row">Рейтинги</div>
          <div class="footer__row">Отраслевая специализация</div>
          <div class="footer__row">Интеграторы</div>
          <div class="footer__row">Решения для бизнеса крепеж</div>
          <div class="footer__row">Разработка сайтов</div>
          <div class="footer__row">Мобильные приложения</div>
          <div class="footer__row">Онлайн-реклама</div>
          <div class="footer__row">Контент</div>
        </div>
        <div class="footer__column">
          <div class="footer__row-title">Продукты</div>
          <div class="footer__row">Рейтинги</div>
          <div class="footer__row">По отраслям</div>
          <div class="footer__row">Работа с клиентами</div>
          <div class="footer__row">Управление проектами</div>
          <div class="footer__row">Маркетинг</div>
          <div class="footer__row">Финансы</div>
          <div class="footer__row">Управление бизнесом</div>
        </div>
        <div class="footer__column">
          <div class="footer__row-title">Кейсы</div>
          <div class="footer__row">Автоматизация сантехников</div>
          <div class="footer__row">Автоматизация клининга</div>
          <div class="footer__row">Автоматизация СТО</div>
          <div class="footer__row">Автоматизация сантехников</div>
          <div class="footer__row">Автоматизация клининга</div>
          <div class="footer__row">Автоматизация СТО</div>
        </div>
      </div>
      <div class="footer__links">
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

<style>
.footer {
  height: 600px;
}
.footer__container {
  width: 1200px;
  margin: auto;
  height: 400px;
  margin-top: 80px;
  padding: 0px 30px 0px 30px;
}
.footer__nav-menu {
  display: flex;
  justify-content: space-between;
}
.footer__row-title {
  font-size: 16px;
  color: #000000;
  font-weight: 500;
}
.footer__row {
  margin-top: 16px;
  font-size: 14px;
  cursor: pointer;
}
.footer__row_tender-custom {
  width: 152px;
  height: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #030953;
  border-radius: 4px;
  color: white;
}
.footer__row_company-custom {
  width: 190px;
  height: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ef3e4a;
  border-radius: 4px;
  color: white;
}
.footer__links {
  display: flex;
  justify-content: space-between;
  margin-top: 26px;
}
.footer__social {
  display: flex;
}
.footer__social-item {
  margin-right: 20px;
}
.footer__about-project {
  display: flex;
}
.footer__about-project-item {
  margin-right: 20px;
  font-size: 12px;
  color: #808080;
}
</style>
