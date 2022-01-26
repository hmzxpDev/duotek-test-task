<template>
  <div class="pagination">
    <div
      @click="listIsChange(item)"
      class="pagination__item"
      v-for="item in paginationList"
      :key="item.index"
      :class="{ pagination__item_active: item == currentList }"
    >
      {{ item }}
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"],
  data() {
    return {
      // текущая страница
      currentList: 1,
      // компания которые будут отрисованы
      companyRender: [],
      // зафетченые компании
      getCompanyList: [],
      // лист с пагинацией
      paginationList: [],
    };
  },
  methods: {
    // метод обновляет значение текущего листа пагинации
    listIsChange(item) {
      if (item !== "...") {
        this.currentList = +item;
        // вычисляем актуальные компании для данного листа
        this.companyListRender();

        this.updateUrl();
      }
    },
    updateUrl() {
      if (!this.$route.query.page) {
        const payload = { ...this.$route.query, page: this.currentList };
        this.$router.push({
          path: "/companies",
          query: payload,
        });
      } else {
        const payload = { ...this.$route.query };
        delete payload.page;
        this.$router.push({
          path: "/companies",
          query: payload,
        });
      }
    },
    paginationListComputed() {
      const pagesOnList = 10; // количество листов на странице
      const pagesNum = Math.round(this.getCompanyList.length / pagesOnList);
      // если количество страниц для пагинации > 9 будет появляться ...
      if (pagesNum > 9) {
        // если выбранная страница < 5 ... будет в конце
        if (this.currentList <= 4) {
          this.paginationList = [1, 2, 3, 4, 5, 6, "...", pagesNum];
        }
        // если выбранная страница < 5 < ... будет в конце и в начале
        else if (this.currentList >= 5 && this.currentList + 3 < pagesNum) {
          this.paginationList = [
            1,
            "...",
            this.currentList - 2,
            this.currentList - 1,
            this.currentList,
            this.currentList + 1,
            this.currentList + 2,
            "...",
            pagesNum,
          ];
        } else {
          this.paginationList = [
            1,
            "...",
            pagesNum - 5,
            pagesNum - 4,
            pagesNum - 3,
            pagesNum - 2,
            pagesNum - 1,
            pagesNum,
          ];
        }
      }
      // если страниц меньше 9 отрисует от 1 до 9, без ...
      else {
        this.paginationList = pagesNum;
      }
      this.companyListRender();
    },
    // метод возвращает массив компаний текущего листа
    companyListRender() {
      this.companyRender = this.getCompanyList.slice(
        (this.currentList - 1) * 10,
        (this.currentList - 1) * 10 + 10
      );
      this.$emit("companyListRender", this.companyRender);
    },
    getUrl() {
      const route = this.$route.query;
      console.log(route);
      if (route.page) {
        this.currentList = route.page;
      }
    },
  },
  // следит за асинхронным запросом данных с сервера
  watch: {
    data() {
      this.getCompanyList = this.data;
      // запускаем вычисление листа пагинации
      this.paginationListComputed();
    },
  },
  mounted() {
    this.getUrl();
  },
};
</script>

<style lang="scss" scoped>
.pagination {
  margin: auto;
  width: 9 * 40px;
  height: 40px;
  display: flex;
  margin-top: 20px;
  margin-bottom: 44px;

  &__item {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 40px;
    height: 40px;
    cursor: pointer;
  }
}

.pagination__item_active {
  background: #f7f7f7;
  border-radius: 4px;
  color: #808080;
}
</style>
