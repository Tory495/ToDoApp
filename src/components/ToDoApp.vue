<template>
  <form class="form-control mb-2">
    <div class="mb-3">
      <label for="headerInput" class="form-label">Заголовок</label>
      <input type="text" class="form-control" id="headerInput" placeholder="Введите заголовок..." v-model.trim="header">
    </div>
    <div class="mb-3">
      <label for="infoTextArea" class="form-label">Информация</label>
      <textarea class="form-control" id="infoTextArea" rows="3" placeholder="Введите информацию..."
                v-model.trim="info"></textarea>
    </div>
    <button type="submit" class="btn btn-primary" @click.prevent="listItemAdd">Добавить</button>
  </form>
  <h2 class="text-center">Задачи</h2>
  <transition-group name="list" tag="div">
    <div v-for="item in list" :key="item.id">
      <div class="card mb-2">
        <div class="card-body">
          <h5 class="card-title">{{ `${item.id}) ${item.header}` }}</h5>
          <p class="card-text">{{ item.info }}</p>
        </div>
      </div>
    </div>
  </transition-group>

</template>

<script>
export default {
  name: "ToDoApp",
  data() {
    return {
      list: [],
      header: "",
      info: "",
      id: 1
    }
  },
  methods: {
    listItemAdd() {
      this.list.push({id: this.id++, header: this.header, info: this.info})
    },
  }
}
</script>

<style scoped>
.list-item {
  display: inline-block;
  margin-right: 10px;
}

.list-enter-active,
.list-leave-active {
  transition: all 1s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>