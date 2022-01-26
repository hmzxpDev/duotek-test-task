<template>
  <div class="search">
    <div class="search__container">
      <div class="search__title">Каталог компаний</div>
      <div class="search__block">
        <form class="search-form" @submit.prevent="onSubmit">
          <div class="search-form__body">
            <input
              v-model="inputValue"
              class="search-form__input"
              placeholder="Поиск по продуктам отрасли"
              type="text"
            />
            <div
              v-bind:style="{
                backgroundImage: 'url(/Catalog-icon/search-icon.svg)',
              }"
              class="search-form__icon"
            ></div>
          </div>
          <button class="search-form__button">Найти</button>
        </form>
        <aside class="search__settings">
          <div class="search__select">
            <h4>Отрасль</h4>
            <Select :selectParams="getIndustry" />
          </div>
          <div class="search__select">
            <h4>Специализация</h4>
            <Select :selectParams="getSpecialization" />
          </div>
        </aside>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // значение текстового поля
      inputValue: "",
      // получаем с сервера данные для селектора отрослей
      getIndustry: {},
      // получаем с сервера данные для селектора специализации
      getSpecialization: {},
    };
  },
  methods: {
    // запрос данных с сервера
    async fetchCompanyList() {
      const res = await fetch("http://api-test.duotek.ru/definitions?");
      const data = await res.json();
      // создаем обьект отрасли
      this.getIndustry = data.Industry;
      this.getIndustry.selectName = "Вся отрасль";
      this.getIndustry.className = "select--industry";
      // создаем обьект специализации
      this.getSpecialization = data.CompanySpecialization;
      this.getSpecialization.selectName = "Все специализации";
      this.getSpecialization.className = "select--specialization";
    },

    // отправка формы
    onSubmit() {
      // если инпут не пустой пушим в url данные
      if (this.inputValue) {
        const payload = { ...this.$route.query, search: this.inputValue };
        this.$router.push({
          path: "/companies",
          query: payload,
        });
      }
      // если пустой то удаляем оттуда их
      else {
        const payload = { ...this.$route.query };
        delete payload.search;
        this.$router.push({
          path: "/companies",
          query: payload,
        });
      }
    },
    // получаем данные из url
    getUrl() {
      this.inputValue = this.$route.query.search;
    },
  },
  mounted() {
    this.fetchCompanyList();
    this.getUrl();
  },
};
</script>

<style lang="scss">
.search {
  &__container {
    margin-top: 75px;
    margin: auto;
    max-width: 1200px;
    margin-top: 75px;
  }

  &__title {
    font-weight: 600;
    font-size: 36px;
    color: #000000;
    margin-bottom: 18px;
  }

  &__block {
    display: flex;
    width: 100%;
    justify-content: space-between;
  }

  &__settings {
    width: 264px;
    height: 204px;
    background: #f7f7f7;
    padding: 18px 20px 18px 20px;
    font-size: 16px;
  }

  &__select {
    height: 50%;
    width: 100%;
    h4 {
      margin-bottom: 12px;
    }
  }
}
.search-form {
  display: flex;
  &__body {
    width: 665px;
    height: 40px;
  }

  &__input {
    width: 665px;
    height: 40px;
    border: 1px solid #e5e5e5;
    padding: 8px 15px 8px 40px;
    position: absolute;
    border-radius: 5px 0px 0px 5px;
    outline: none;
  }

  &__icon {
    position: relative;
    width: 24px;
    height: 24px;
    top: 8px;
    left: 10px;
  }

  &__button {
    width: 80px;
    height: 40px;
    border-radius: 0px 5px 5px 0px;
    background: #030953;
    color: #fff;
    border-top: none;
    border-left: none;
  }
}
</style>
