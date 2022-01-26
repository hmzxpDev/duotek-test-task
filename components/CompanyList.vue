<template>
  <main>
    <Search />
    <div class="company-list">
      <div class="company-list__container">
        <div class="company-list__content">
          <div v-if="companyListRender.length === 0">
            Нет элементов в массиве? Ну и элементов на странице тоже не будет!
          </div>
          <nuxt-link
            v-for="company in companyListRender"
            :key="company.id"
            :to="'companies/' + company.id"
          >
            <div class="company-list__item">
              <div class="company-list__logo">
                <img :src="company.picture" />
              </div>
              <div class="company-list__description">
                <div class="company-list__title">
                  {{ company.title }}
                </div>
                <div class="company-list__description">
                  {{ company.description_short }}
                </div>
                <div class="company-list__tag-body">
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
          </nuxt-link>
        </div>
        <Pagination
          :data="companyToPagination"
          @companyListRender="renderFromPagination"
        />
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      // список компании получаемые с сервера
      getCompanyList: [],
      // массив компаний которые попадут в рендер
      companyListRender: [],
      inputValue: "",
      selectIndustryValue: "",
      selectSpecializationValue: "",
      companyToPagination: [],
    };
  },
  methods: {
    // Получаем список компаний с сервера
    async fetchCompanyList() {
      const res = await fetch("http://api-test.duotek.ru/companies");
      const data = await res.json();
      this.getCompanyList = data.data;
      this.filter();
    },
    // метод отсеивает с учетом условий из search и select
    filter() {
      let arr = this.getCompanyList;
      if (this.inputValue) {
        const regExp = new RegExp(`^${this.inputValue}`, "i");
        arr = arr.filter((item) => regExp.test(item.title));
      }
      if (this.selectIndustryValue) {
        arr = arr.filter((item) => {
          if (
            item.industries.find((item) => item.id == this.selectIndustryValue)
          ) {
            return true;
          }
        });
      }
      if (this.selectSpecializationValue) {
        arr = arr.filter((item) => {
          if (
            item.companySpecializations.find(
              (item) => item.id == this.selectSpecializationValue
            )
          ) {
            return true;
          }
        });
      }
      this.companyToPagination = arr;
    },
    // отрисовываем элементы полученные из pagination
    renderFromPagination(data) {
      this.companyListRender = data;
    },
    // получаем данные из url
    getUrl() {
      const route = this.$route.query;
      this.inputValue = route.search;
      this.selectIndustryValue = +route.industries;
      this.selectSpecializationValue = +route.specializations;
    },
  },

  mounted() {
    this.getUrl();
    this.fetchCompanyList();
  },
  watch: {
    $route() {
      this.getUrl();
      this.filter();
    },
  },
};
</script>

<style lang="scss" scoped>
.company-list {
  &__container {
    width: 1200px;
    margin: auto;
  }

  &__content {
    width: 792px;
    margin-top: -120px;
    position: relative;
    margin-bottom: 20px;
  }

  &__item {
    display: flex;
    width: 792px;
    height: 208px;
    padding: 32px 23px 0px 32px;
  }

  &__logo {
    width: 160px;
    img {
      max-width: 80%;
      max-height: 80%;
    }
  }

  &__description {
    width: 530px;
    font-size: 14px;
    line-height: 150%;
    color: #333333;
  }

  &__title {
    font-size: 24px;
    color: #030953;
    font-weight: bold;
    margin-bottom: 15px;
  }

  &__tag-body {
    display: flex;
    margin-top: 16px;
  }

  &__tag {
    background: #f7f7f7;
    border-radius: 200px;
    height: 32px;
    padding: 5px 13px 5px 13px;
    margin-right: 4px;
    font-size: 14px;
    color: #333333;
  }

  &__arrow {
    display: none;
    margin-top: 132px;
    color: #ef3e4a;
    width: 47px;
    text-align: right;
  }
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
</style>
