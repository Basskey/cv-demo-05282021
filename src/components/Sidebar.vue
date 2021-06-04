<template>
  <div class="sidebar">
    <h3 class="sidebar-title">Фильтры</h3>

    <div class="filter-section" v-for="filter of filters">
      <h3 class="filter-section__title">{{ filter.title }}</h3>
      <input type="text" placeholder="Поиск..." class="search" v-if="filter.hasSearch" />
      <ul class="filter-list">
        <li>
          <div class="checkbox--mock"></div> {{ filter.items[0] }}
        </li>
        <li>
          <div class="checkbox--mock"></div> {{ filter.items[1] }}
        </li>
        <li>
          <div class="checkbox--mock"></div> {{ filter.items[2] }}
        </li>
        <a class="show-more">Показать ещё</a>
      </ul>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'Sidebar',

    data() {
      return {
        filters: [
          {
            id: 1,
            title: 'Редакция',
            items: ['Ежедневные экспрессы','Суперэкспрессы','Тоталы'],
            isExpanded: true,
            hasSearch: false
          },
          {
            id: 2,
            title: 'Команда',
            items: ['Александр Вишневский','Константин Генич','Кирилл Дементьев'],
            isExpanded: true,
            hasSearch: false
          },
          {
            id: 3,
            title: 'Дата',
            items: ['Сегодня','Завтра','Вчера'],
            isExpanded: true,
            hasSearch: false
          },
          {
            id: 4,
            title: 'Команды',
            items: ['Зенит','Спартак','ЦСК'],
            isExpanded: true,
            hasSearch: false
          },
          {
            id: 5,
            title: 'Матчи',
            items: ['Унион — Байер','Лацио — Рома','Монпелье — Монако'],
            isExpanded: true,
            hasSearch: false
          },
          {
            id: 6,
            title: 'Лиги',
            items: ['Кубок России','Премьер-лига','ЧЕ-2021'],
            isExpanded: true,
            hasSearch: true
          },
          {
            id: 7,
            title: 'Игроки',
            items: ['Лионель Месси','Лионель Месси','Лионель Месси'],
            isExpanded: true,
            hasSearch: true
          },
        ]
      }
    }
  }
</script>

<style lang="scss">
  .sidebar {
    display: none; //mob
    width: 280px;
    border: 2px solid #E2E4E8;
    border-radius: 14px;
    padding: 24px 24px 0;
    flex-shrink: 0;

    &-title {
      display: flex;
      align-items: center;
      font-family: 'Raleway', sans-serif;
      font-style: normal;
      font-weight: bold;
      font-size: 18px;
      line-height: 1.3em;
      letter-spacing: 0.6px;
      font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
      color: #1C1D1F;
      margin: 0 0 24px 0;
      &::before {
        content: '';
        background: #FFF5CF url("/img/icon-filters.svg") no-repeat;
        background-size: contain;
        display: block;
        width: 16px;
        height: 18px;
        margin: 0 20px 0 0;
      }
    }

    .filter-section {

      &.expanded {
        .filter-section--title {
          &::after {
            transform: rotate(180deg);
          }
        }
      }

      &__title {
        font-family: 'Raleway', sans-serif;
        font-style: normal;
        font-weight: 600;
        font-size: 16px;
        line-height: 2em;
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-feature-settings: 'pnum' on, 'lnum' on;
        color: #1C1D1F;
        &::after {
          content: '';
          background:  #FFF5CF url("/img/dropdown-arrow.svg") no-repeat;
          width: 14px;
          height: 8px;
          transition: .3s;
        }
      }

      .search {
        border: 1px solid #E2E4E8;
        box-sizing: border-box;
        border-radius: 80px;
        height: 32px;
        padding: 0 18px 0 40px;
        background: url("/img/icon-search.svg") no-repeat 18px center;
        outline: none;
      }

      .filter-list {
        list-style: none;
        padding: 16px 0;
        border-bottom: 1px solid #E2E4E8;

        li {
          display: flex;
          font-family: 'Raleway', sans-serif;
          font-style: normal;
          font-weight: normal;
          font-size: 14px;
          line-height: 1.7em;
          font-feature-settings: 'pnum' on, 'lnum' on;
          color: #1C1D1F;
          margin: 0 0 8px 0;
        }

        .checkbox--mock {
          border: 2px solid #1C1D1F;
          box-sizing: border-box;
          border-radius: 4px;
          width: 16px;
          height: 16px;
          margin: calc((1.7em - 16px) / 2) 8px 0 0;
          flex-shrink: 0;
        }

        .show-more {
          font-family: 'Raleway', sans-serif;
          font-style: normal;
          font-weight: normal;
          font-size: 14px;
          line-height: 1.7em;
          text-decoration-line: underline;
          font-feature-settings: 'pnum' on, 'lnum' on;
          color: #1C1D1F;
          background: transparent;
          border: none;
        }
      }
    }
  }
</style>
