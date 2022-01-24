<template>
  <div class="company">
    <div class="company__container">
      <nav class="company__navigation-back">
        <fa icon="arrow-left" />
        <p>Компании</p>
      </nav>
      <div class="company__title">Дуотек</div>
      <div class="company__content">
        <div class="company__left-side">
          <div class="statistics">
            <div class="statistics__item">
              <div class="statistics__number">13</div>
              <div class="statistics__title">лет</div>
            </div>
            <div class="statistics__item">
              <div class="statistics__number">20</div>
              <div class="statistics__title">человек</div>
            </div>
          </div>
          <div class="company__headding">
            <div class="company__description">
              Российский разработчик IT-решений для бизнеса. Проектирование и
              разработка кастомных IT-решений с индивидуальными требованиями:
              автоматизация, интернет-проекты, мобильные приложения.
            </div>
            <div class="company__sub-description">
              Duotek помогает компаниям и стартапам в России и других странах
              разработать и внедрить IT-решения, учитывающие специфику бизнеса и
              индивидуальные требования. Ключевая компетенция — проектирование и
              управление разработкой кастомных IT-решений и интернет-проектов.
            </div>
          </div>
          <div class="company__tags">
            <div class="company__tag-title">Проектная специализация</div>
            <div class="company__tag-item">
              <div class="company__tag">Интеграция. Промышленные решения</div>
              <div class="company__tag">
                Интеграция. Проекты для крупного бизнеса
              </div>
              <div class="company__tag">Разработка. CRM-решения</div>
              <div class="company__tag">Разработка. Аналитика</div>
            </div>
            <div class="company__tag-title">Технологии</div>
            <div class="company__tag-item">
              <div class="company__tag">Компьютерное зрение</div>
              <div class="company__tag">Распознавание образов</div>
              <div class="company__tag">Распозавание документов</div>
            </div>
          </div>
        </div>
        <div class="company__right-side">
          <div class="company__logo">LOGO</div>
          <div class="company__contact">
            <span class="company__contact-title">Сайт</span>
            <span class="company__contact-content">www.duotek.ru</span>
          </div>
          <div class="company__contact">
            <span class="company__contact-title">E-mail:</span>
            <span class="company__contact-content">info@duotek.ru</span>
          </div>
          <div class="company__contact">
            <span class="company__contact-title">Телефон</span>
            <span class="company__contact-content">(495) 2345-67-89</span>
          </div>
          <div class="company__contact">
            <span class="company__contact-title">Офис</span>
            <span class="company__contact-content"
              >Новодмитровская ул. 2к.2, 16 этаж, офис 1</span
            >
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
.company {
  &__container {
    width: 1140px;
    margin: auto;
    margin-top: 44px;
    margin-bottom: 400px;
  }

  &__navigation-back {
    width: 100px;
    height: 21px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 14px;
    color: #030953;
  }

  &__title {
    margin-top: 13px;
    font-size: 36px;
    font-weight: 600;
  }

  &__content {
    display: flex;
    justify-content: space-between;
  }

  &__left-side {
    width: 845px;
  }

  &__description {
    font-size: 18px;
    width: 830px;
    color: #333333;
    font-weight: 500;
  }

  &__sub-description {
    margin-top: 24px;
    font-size: 14px;
    font-weight: 500;
    width: 830px;
  }

  &__tag-title {
    display: flex;
    flex-wrap: wrap;
  }

  &__tag-item {
    display: flex;
  }

  &__tag {
    background: #f7f7f7;
    border-radius: 200px;
    padding: 7px 20px 7px 20px;
    margin-right: 4px;
    margin-top: 4px;
    font-size: 14px;
  }

  &__right-side {
    width: 260px;
  }

  &__logo {
    width: 120px;
    height: 120px;
  }

  &__contact {
    margin-top: 16px;
    display: flex;
    flex-direction: column;
  }

  &__contact-title {
    color: #808080;
    font-size: 14px;
  }

  &__contact-content {
    font-size: 14px;
  }
}
.statistics {
  display: flex;
  &__item {
    display: flex;
    margin-left: 20px;
  }

  &__number {
    font-size: 60px;
    color: #ef3e4a;
  }

  &__title {
    font-size: 16px;
    margin-top: 16px;
    color: #333333;
    font-weight: 500;
  }
}
</style>
