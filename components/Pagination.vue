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
  data() {
    return {
      currentList: 1,
      companyRender: [],
      getComapnyInfo: [],
      paginationList: [],
    };
  },
  methods: {
    // метод обновляет значение текущего листа пагинации
    listIsChange(item) {
      if (item !== "...") {
        this.currentList = +item;
        this.paginationListRender(); // запускаем ререндор листа пагинации
        this.companyListRender(); // запускаем ререндор отрисованного листа
      }
    },
    // метод возвращает массив пагинации
    paginationListRender() {
      const pagesNum = Math.round(this.getComapnyInfo.length / 10);
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
    },
    // метод отрисовывает компании в зависимости от выбраного листа
    companyListRender() {
      this.companyRender = this.getComapnyInfo.slice(
        (this.currentList - 1) * 10,
        (this.currentList - 1) * 10 + 10
      );
    },
  },
  mounted() {
    this.getCompany();
  },
  update() {},
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
}
.pagination__item {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  cursor: pointer;
}
.pagination__item_active {
  background: #f7f7f7;
  border-radius: 4px;
  color: #808080;
}
</style>