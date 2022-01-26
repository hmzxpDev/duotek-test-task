<template>
  <div>
    <div class="select">
      <div :class="selectParams.className" class="select__content">
        {{ select }}
      </div>
      <div :class="selectParams.className" class="select__icon">
        <fa
          v-if="select !== selectParams.selectName"
          @click="clearSelect"
          icon="times"
          class="cross"
        />
        <fa
          icon="angle-down"
          :class="angelUpClass()"
          class="select__angel-down"
        />
      </div>
    </div>
    <transition name="fade">
      <div v-if="optionDrop">
        <div
          class="select__option"
          @click="selectOptions(item)"
          v-for="item in selectParams"
          :key="item.id"
        >
          {{ item.title }}
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: ["selectParams"],
  data() {
    return {
      name: "Select",
      select: "",
      selectId: 0,
      optionDrop: false,
    };
  },
  methods: {
    // метод для крестика(который очищает селект)
    clearSelect() {
      this.select = this.selectParams.selectName;
      this.selectId = 0;
    },
    // Анимация стрелки
    angelUpClass() {
      return this.optionDrop
        ? `select__angel-up ${this.selectParams.className}` // для анимации стрелки
        : `${this.selectParams.className}`;
    },
    // При выборе меняется placeholder селектора
    selectOptions(item) {
      this.optionDrop = false;
      this.select = item.title;
      this.selectId = item.id;
    },
    // для закрывания полей options
    hideOptions(event) {
      const regExp = new RegExp(this.selectParams.className);
      // если клик происходит по блокам селектора
      if (
        regExp.test(event.target.className) || // клик по основному блоку селектора
        regExp.test(event.target.className.animVal) || // клик по svg
        regExp.test(event.target.parentElement?.className.animVal) // клик по самой икнонки стрелки
      ) {
        // если options скрыты - открывает их и завершает функцию
        if (!this.optionDrop) {
          this.optionDrop = true;
          return;
        }
        // если options открыты - закрывает их
        else {
          this.optionDrop = false;
        }
      }
      // если клик происходит вне селктора - скрываем селектор
      else {
        this.optionDrop = false;
      }
    },
    // читаем с url данные
    getUrl() {
      if (this.selectParams.selectName == "Вся отрасль") {
        const urlId = this.$route.query.industries;
        if (urlId) {
          let currentValue = this.selectParams.find((item) => item.id == urlId);
          this.select = currentValue.title;
          this.selectId = currentValue.id;
        }
      } else {
        const urlId = this.$route.query.specializations;
        if (urlId) {
          let currentValue = this.selectParams.find((item) => item.id == urlId);
          this.select = currentValue.title;
          this.selectId = currentValue.id;
        }
      }
    },
    // метод для пуша актуальных данных
    routerPush(queryValue) {
      this.$router.push({
        path: "/companies",
        query: queryValue,
      });
    },
    // обновляем роутинг
    routingUpdate() {
      // если селект заполнен
      if (this.select !== this.selectParams.selectName) {
        // если отрасль
        if (this.selectParams.selectName == "Вся отрасль") {
          let payload = { ...this.$route.query, industries: this.selectId };
          this.routerPush(payload);
        }
        // если специализация
        else {
          let payload = {
            ...this.$route.query,
            specializations: this.selectId,
          };
          this.routerPush(payload);
        }
      }
      // если селект пустой
      else {
        // если отрасль
        if (this.selectParams.selectName == "Вся отрасль") {
          let payload = { ...this.$route.query };
          if (payload.industries) delete payload.industries;
          this.routerPush(payload);
        }
        // если специализация
        else {
          let payload = { ...this.$route.query };
          if (payload.specializations) delete payload.specializations;
          this.routerPush(payload);
        }
      }
    },
  },
  watch: {
    selectParams() {
      // получаем из родительского компонента данные
      this.select = this.selectParams.selectName;
      this.options = this.selectParams.options;
      this.getUrl();
    },
    selectId() {
      this.routingUpdate();
    },
  },
  mounted() {
    // получает от родительского компонента значение для placeholder
    this.select = this.selectParams.selectName;
    // при клике передаем в функцию скрытия options - event клика
    document.addEventListener("click", this.hideOptions.bind(this));
  },
  beforeDestroy() {
    document.removeEventListener("click", this.hideOptions.bind(this));
  },
};
</script>

<style lang="scss" scoped>
.select {
  cursor: pointer;
  border: 1px solid #000;
  width: 224px;
  min-height: 40px;
  padding: 6px 12px 6px 12px;
  border: 1px solid #e5e5e5;
  font-size: 14px;
  color: black;
  border-radius: 4px;
  font-weight: 500;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: white;

  &__content {
    width: 160px;
    word-wrap: break-word;
  }

  &__icon {
    display: flex;
    justify-content: flex-end;
    color: #909399;
    font-size: 20px;
    min-width: 37px;
  }

  &__angel-down {
    transition-duration: 0.1s;
    transform: rotate(0deg);
  }

  &__angel-up {
    transition-duration: 0.1s;
    transform: rotate(180deg);
  }

  &__option {
    cursor: pointer;
    border: 1px solid #000;
    width: 224px;
    min-height: 40px;
    padding: 10px 16px 10px 16px;
    border: 1px solid #e5e5e5;
    font-size: 14px;
    color: black;
    border-radius: 4px;
    font-weight: 500;
    background-color: white;
    position: relative;
    z-index: 4;
  }
}
.cross {
  margin-right: 15px;
}

.select__option:hover {
  background-color: rgb(172, 172, 172);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.1s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 1100px) {
  .select {
    width: 98%;
    &__content {
      width: 100%;
    }

    &__option {
      width: 98%;
    }
  }
}
</style>
