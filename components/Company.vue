<template>
  <div class="company">
    <div class="company__container">
      <nav class="company__navigation">
        <fa icon="arrow-left" />
        <p>Компании</p>
      </nav>
      <div class="company__name">Дуотек</div>
      <div class="company__content">
        <div class="company__left-side">
          <div class="company__statistics">
            <div class="company__years">
              <div class="company__number">13</div>
              <div class="company__title">лет</div>
            </div>
            <div class="company__state">
              <div class="company__number">20</div>
              <div class="company__title">человек</div>
            </div>
          </div>
          <div class="company__headding">
            <div class="company__headding-title">
              Российский разработчик IT-решений для бизнеса. Проектирование и
              разработка кастомных IT-решений с индивидуальными требованиями:
              автоматизация, интернет-проекты, мобильные приложения.
            </div>
            <div class="company__headding-content">
              Duotek помогает компаниям и стартапам в России и других странах
              разработать и внедрить IT-решения, учитывающие специфику бизнеса и
              индивидуальные требования. Ключевая компетенция — проектирование и
              управление разработкой кастомных IT-решений и интернет-проектов.
            </div>
          </div>
          <div class="company__tags">
            <div class="company__tag-headding">Проектная специализация</div>
            <div class="company__tag-block">
              <div class="company__tag">Интеграция. Промышленные решения</div>
              <div class="company__tag">
                Интеграция. Проекты для крупного бизнеса
              </div>
              <div class="company__tag">Разработка. CRM-решения</div>
              <div class="company__tag">Разработка. Аналитика</div>
            </div>
            <div class="company__tag-headding">Технологии</div>
            <div class="company__tag-block">
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
.company__container {
  width: 1140px;
  margin: auto;
  margin-top: 44px;
  margin-bottom: 400px;
}
.company__navigation {
  width: 100px;
  height: 21px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px;
  color: #030953;
}
.company__content {
  display: flex;
  justify-content: space-between;
}
.company__left-side {
  width: 845px;
}
.company__right-side {
  width: 260px;
}
.company__name {
  margin-top: 13px;
  font-size: 36px;
  font-weight: 600;
}
.company__statistics {
  display: flex;
}
.company__number {
  font-size: 60px;
  color: #ef3e4a;
}
.company__years {
  display: flex;
}
.company__title {
  font-size: 16px;
  margin-top: 16px;
  color: #333333;
  font-weight: 500;
}
.company__state {
  display: flex;
  margin-left: 20px;
}
.company__headding-title {
  font-size: 18px;
  width: 830px;
  color: #333333;
  font-weight: 500;
}
.company__headding-content {
  margin-top: 24px;
  font-size: 14px;
  font-weight: 500;
  width: 830px;
}
.company__tags {
  .company__tag-headding {
    margin-top: 40px;
    font-size: 18px;
    font-weight: 600;
  }
}
.company__tag-block {
  display: flex;
  flex-wrap: wrap;
}
.company__tag {
  background: #f7f7f7;
  border-radius: 200px;
  padding: 7px 20px 7px 20px;
  margin-right: 4px;
  margin-top: 4px;
  font-size: 14px;
}
.company__logo {
  width: 120px;
  height: 120px;
}
.company__contact {
  margin-top: 16px;
  display: flex;
  flex-direction: column;
}
.company__contact-title {
  color: #808080;
  font-size: 14px;
}
.company__contact-content {
  font-size: 14px;
}
</style>
