<template>
  <div class="company-list">
    <div class="company-list__container">
      <div class="company-list__content">
        <div
          v-for="company in companyRender"
          :key="company.id"
          class="company-list__item"
        >
          <div class="company-list__logo"><img :src="company.picture" /></div>
          <div class="company-list__description">
            <div class="company-list__title">
              {{ company.title }}
            </div>
            <div class="company-list__description">
              {{ company.description_short }}
            </div>
            <div class="company-list__tag-blocks">
              <div
                v-for="tag in company.industries"
                :key="tag.id"
                class="company-list__tag"
              >
                {{ tag.title }}
              </div>
            </div>
          </div>
          <div class="company-list__arrow">
            <fa icon="arrow-right" />
          </div>
        </div>
      </div>
      <Pagination :data="data" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // массив компаний которые попадут в рендер
      renderCompanyList,
      // список компании получаемые с сервера
      getCompanyList: [],
    };
  },
  methods: {
    // Получаем данные со списком компании с сервера
    async getCompanyList() {
      const res = await fetch("http://api-test.duotek.ru/companies");
      const data = await res.json();
      this.getCompanyList = data.data;
    },
  },
  // по рекомендациям nuxt
  asyncData() {
    this.getCompanyList();
  },
};
</script>

<style lang="scss" scoped>
.company-list__container {
  width: 1200px;
  margin: auto;
}
.company-list__content {
  width: 792px;
  margin-top: -120px;
  position: relative;
  margin-bottom: 20px;
}
.company-list__item {
  display: flex;
  width: 792px;
  height: 208px;
  padding: 32px 23px 0px 32px;
}
.company-list__item:hover {
  cursor: pointer;
  background: rgba(3, 9, 83, 0.03);
  .company-list__title {
    color: #ef3e4a;
  }
  .company-list__tag {
    background-color: white;
  }
  .company-list__arrow {
    display: block;
  }
}
.company-list__logo {
  width: 160px;
}
.company-list__description {
  width: 530px;
}
.company-list__title {
  font-size: 24px;
  color: #030953;
  font-weight: bold;
  margin-bottom: 15px;
}
.company-list__description {
  font-size: 14px;
  line-height: 150%;
  color: #333333;
}
.company-list__tag-blocks {
  display: flex;
  margin-top: 16px;
}
.company-list__tag {
  background: #f7f7f7;
  border-radius: 200px;
  height: 32px;
  padding: 5px 13px 5px 13px;
  margin-right: 4px;
  font-size: 14px;
  color: #333333;
}

.company-list__arrow {
  display: none;
  margin-top: 132px;
  color: #ef3e4a;
  width: 47px;
  text-align: right;
}
</style>
