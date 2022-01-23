<template>
  <div class="catalog__container">
    <div class="catalog__headding">Каталог компаний</div>
    <div class="search">
      <form class="search__form" @submit.prevent="onSubmit">
        <div class="custom-input">
          <input
            class="custom-input__input"
            placeholder="Поиск по продуктам отрасли"
            type="text"
          />
          <div
            v-bind:style="{
              backgroundImage: 'url(/Catalog-icon/search-icon.svg)',
            }"
            class="custom-input__icon"
          ></div>
        </div>
        <button class="search__button">Найти</button>
      </form>
      <aside class="search__settings">
        <div class="search__industry select-blocks">
          <h4>Отрасль</h4>
          <Select :data="dataIndustry" />
        </div>
        <div class="search__specialization select-blocks">
          <h4>Специализация</h4>
          <Select :data="dataSpecialization" />
        </div>
      </aside>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dataIndustry: {
        selectName: "Вся отрасль",
        className: "select--industry",
      },
      dataSpecialization: {
        selectName: "Все специализации",
        className: "select--specialization",
      },
    };
  },
  methods: {
    onSubmit() {
      console.log("qwe");
    },
  },
};
</script>

<style lang="scss">
.catalog__container {
  margin-top: 75px;
  margin: auto;
  width: 1200px;

  margin-top: 75px;
}
.catalog__headding {
  font-weight: 600;
  font-size: 36px;
  color: #000000;
  margin-bottom: 18px;
}
.search {
  display: flex;
  width: 100%;
  justify-content: space-between;
}
.search__form {
  display: flex;
}
.custom-input {
  width: 665px;
  height: 40px;
}
.custom-input__input {
  width: 665px;
  height: 40px;
  border: 1px solid #e5e5e5;
  padding: 8px 15px 8px 40px;
  position: absolute;
  border-radius: 5px 0px 0px 5px;
  outline: none;
}
.custom-input__icon {
  position: relative;
  width: 24px;
  height: 24px;
  top: 8px;
  left: 10px;
}
.search__button {
  width: 80px;
  height: 40px;
  border-radius: 0px 5px 5px 0px;
  background: #030953;
  color: #fff;
  border: none;
}
.search__settings {
  width: 264px;
  height: 204px;
  background: #f7f7f7;
  padding: 18px 20px 18px 20px;
  font-size: 16px;
}
.select-blocks {
  height: 50%;
  width: 100%;
  h4 {
    margin-bottom: 12px;
  }
}
.search__select {
  width: 224px;
  height: 40px;
  border: 1px solid #e5e5e5;
  outline: none;
  padding: 9px 16px 9px 16px;
  appearance: none;
}
</style>
