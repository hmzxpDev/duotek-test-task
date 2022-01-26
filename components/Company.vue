<template>
  <div class="company">
    <div
      v-for="company in getCompanyInfo"
      :key="company.id"
      class="company__container"
    >
      <nav class="company__navigation-back">
        <nuxt-link to="/companies"><fa icon="arrow-left" /> Компании</nuxt-link>
      </nav>
      <div class="company__title">{{ company.title }}</div>
      <div class="company__content">
        <div class="company__left-side">
          <div class="statistics">
            <div class="statistics__item">
              <div class="statistics__number">{{ company.age }}</div>
              <div v-if="company.age < 4" class="statistics__title">года</div>
              <div class="statistics__title">лет</div>
            </div>
            <div class="statistics__item">
              <div class="statistics__number">{{ company.staff }}</div>
              <div class="statistics__title">человек</div>
            </div>
          </div>
          <div class="company__headding">
            <div class="company__description">
              {{ company.description_short }}
            </div>
            <div class="company__sub-description">
              {{ company.description_full }}
            </div>
          </div>
          <div class="company__tag-body">
            <div
              v-if="company.companySpecializations.length !== 0"
              class="company__tag-title"
            >
              Проектная специализация
            </div>
            <div class="company__tag-content">
              <div
                v-for="tag in companySpecializations"
                :key="tag.id"
                class="company__tag-item"
              >
                {{ tag.title }}
              </div>
            </div>
            <div
              v-if="company.industries.length !== 0"
              class="company__tag-title"
            >
              Технологии
            </div>
            <div class="company__tag-content">
              <div
                v-for="tag in industries"
                :key="tag.id"
                class="company__tag-item"
              >
                {{ tag.title }}
              </div>
            </div>
          </div>
        </div>
        <div class="company__right-side">
          <div class="company__logo">
            <img :src="company.picture" alt="logo" />
          </div>
          <div class="company__contact">
            <span class="company__contact-title">Сайт</span>
            <span class="company__contact-content">{{ company.url }}</span>
          </div>
          <div class="company__contact">
            <span class="company__contact-title">E-mail:</span>
            <span class="company__contact-content">{{
              company.contact_email
            }}</span>
          </div>
          <div class="company__contact">
            <span class="company__contact-title">Телефон</span>
            <span
              v-if="company.contact_phone == null"
              class="company__contact-title"
              >-</span
            >
            <span v-else class="company__contact-content"
              >{{ company.contact_phone[0] }} ({{
                company.contact_phone.slice(1, 4)
              }}) {{ company.contact_phone.slice(4, 7) }}-{{
                company.contact_phone.slice(7, 9)
              }}-{{ company.contact_phone.slice(9, 11) }}
            </span>
          </div>
          <div class="company__contact">
            <span class="company__contact-title">Город</span>
            <span class="company__contact-content">{{
              company.city.title
            }}</span>
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
      getCompanyInfo: [],
      companySpecializations: [],
      industries: [],
    };
  },
  methods: {
    companyFetch(id) {
      fetch(`http://api-test.duotek.ru/companies/info?id=${id}`)
        .then((res) => {
          return res.text();
        })
        .then((res) => {
          return (this.getCompanyInfo = JSON.parse(res));
        });
    },
  },
  watch: {
    getCompanyInfo() {
      const company = this.getCompanyInfo.data;
      this.companySpecializations = company.companySpecializations;
      this.industries = company.industries;
    },
  },
  mounted() {
    this.companyFetch(this.$route.params.id);
  },
};
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
    a {
      color: #030953;
    }
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

  &__tag-body {
    font-weight: 600;
  }

  &__tag-title {
    margin: 30px 0px 26px 0px;
    display: flex;
    flex-wrap: wrap;
  }

  &__tag-content {
    display: flex;
    flex-wrap: wrap;
  }

  &__tag-item {
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
    width: 100%;
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
    margin-right: 20px;
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
