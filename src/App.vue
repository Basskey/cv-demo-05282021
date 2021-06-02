<template>
  <div class="layout">
    <div class="wrapper">
      <div class="crumbs">
        Fanler • Рейтинг букмекеров
      </div>
      <h1 class="title">Рейтинг букмекеров <span style="color: #83868A; font-weight: 400">819</span></h1>
      <p class="subtitle">Все букмекерские конторы у нас на сайте имеют подробный обзор плюсов и минусов, экспертную оценку коэффициентов и выбора ставок, а так же информацию о бонусах. Выбрать легальную БК, принимающую ставки на спорт через интернет, также помогут наши независимые рейтинги.</p>

      <div class="content">
        <ul class="content-tabs">
          <li class="content-tabs__tab" v-for="element of mockTabs">
            {{ element }}
            <span style="margin: 0 0 0 4px">21</span>
          </li>
        </ul>

        <div class="content-container">
          <BookmakersTable />
          <Sidebar />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BookmakersTable from "./components/BookmakersTable";
import Sidebar from "./components/Sidebar"

export default {
  name: 'App',
  components: {
    BookmakersTable,
    Sidebar
  },

  data() {
    return {
      mockTabs: ['Футбол', 'Тренды', 'Конкурсы', 'Эксперты о бэттинге', 'Хоккей', 'Баскетбол', 'Теннис', 'Бои'],
      mockData: [
        {
          id: 1,
          logo: 'fonbet',
          bonus: 10000,
          feedbacks: 789,
          complaints: [248, 104, 55],
        },
        {
          id: 2,
          logo: 'xbettery',
          bonus: 10000,
          feedbacks: 789,
          complaints: [248, 104, 55],
        },
        {
          id: 3,
          logo: '1xstavka',
          bonus: 1000,
          feedbacks: 789,
          complaints: [248, 104, 55],
        },
        {
          id: 4,
          logo: 'leonru',
          bonus: 100,
          feedbacks: 789,
          complaints: [248, 104, 55],
        },
        {
          id: 5,
          logo: 'betcity',
          bonus: 1000,
          feedbacks: 789,
          complaints: [248, 104, 55],
        }
      ]
    }
  },

  mounted() {
    console.log(this.mockData)
  }
}
</script>

<style lang="scss">
  @import "assets/styles";
</style>
