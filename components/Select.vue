<template>
  <div>
    <div class="select" :class="data.className">
      {{ select }}
      <fa
        icon="angle-down"
        :class="angelUpClass()"
        class="select__angel-down"
      />
    </div>
    <transition name="fade">
      <div v-if="optionDrop">
        <div
          class="select__option"
          @click="selectOptions(item)"
          v-for="item in options"
          :key="item.id"
        >
          {{ item.name }}
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: ["data"],
  data() {
    return {
      name: "Select",
      select: "Выберите значение",
      optionDrop: false,
      options: [
        { id: 1, name: 1 },
        { id: 2, name: 2 },
        { id: 3, name: 3 },
        { id: 4, name: 4 },
        { id: 5, name: 5 },
        { id: 6, name: 2 },
        { id: 7, name: 1 },
        { id: 8, name: 3 },
        { id: 9, name: 4 },
        { id: 10, name: 123 },
      ],
    };
  },
  methods: {
    angelUpClass() {
      // для уникального класса компонента select
      return this.optionDrop
        ? `select__angel-up ${this.data.className}` // для анимации стрелки
        : `${this.data.className}`;
    },
    selectOptions(item) {
      // При выборе меняется placeholder селектора
      this.optionDrop = false;
      this.select = item.name;
    },
    hideOptions(event) {
      const regExp = new RegExp(this.data.className);
      // если клик происходит по блокам селектора
      if (
        regExp.test(event.target.className) || // клик по основному блоку селектора
        regExp.test(event.target.className.animVal) || // клик по svg
        regExp.test(event.target.parentElement.className.animVal) // клик по самой икнонки стрелки
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
  },
  mounted() {
    // получает от родительского компонента значение для placeholder
    this.select = this.data.selectName;
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
  height: 40px;
  padding: 10px 16px 10px 16px;
  border: 1px solid #e5e5e5;
  font-size: 14px;
  color: black;
  border-radius: 4px;
  font-weight: 500;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: white;
}
.select__option {
  cursor: pointer;
  border: 1px solid #000;
  width: 224px;
  height: 40px;
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
.select__option:hover {
  background-color: rgb(172, 172, 172);
}
.select__angel-down {
  transition-duration: 0.1s;
  transform: rotate(0deg);
  font-size: 25px;
  color: #909399;
}
.select__angel-up {
  transition-duration: 0.1s;
  transform: rotate(180deg);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.1s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
