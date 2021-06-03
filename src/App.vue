<template>
  <div class="layout">
    <div class="wrapper">
      <div class="crumbs">
        Fanler • Рейтинг букмекеров
      </div>

      <Title />

      <div class="sidebar--mobile-static">
        <div class="filters">
          <img width="11" src="../public/img/icon-filters.svg" alt="">
          Фильтры</div>
        <div class="new">
          <img width="15" src="../public/img/icon-new.svg" alt="">
          Новые</div>
      </div>

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
import Title from "./components/Title";
import BookmakersTable from "./components/BookmakersTable";
import Sidebar from "./components/Sidebar"

export default {
  name: 'App',
  components: {
    Title,
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
      ],
      isMobile: true
    }
  },
}
</script>

<style lang="scss">
  @import "assets/styles";

  .sidebar--mobile-static {
    display: flex;
    justify-content: space-between;
    margin: 0 0 24px 0;

    div {
      border: 1px solid #E2E4E8;
      box-sizing: border-box;
      border-radius: 8px;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 140px;
      height: 40px;
      font-size: 18px;
      line-height: 1.78em;

      img {
        margin: 0 10px 0 0;
      }
    }
  }
</style>
