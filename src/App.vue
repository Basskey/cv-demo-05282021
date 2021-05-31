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
          <div class="table">
            <div class="table__row table__header">
              <div class="table-cell">Букмекер</div>
              <div class="table-cell">Бонус</div>
              <div class="table-cell">Отзывы</div>
              <div class="table-cell">Жалобы</div>
            </div>

            <div class="table__row" v-for="bookmaker of mockData">
              <div class="table-cell table-cell--logo">
                <div class="cell-number">{{bookmaker.id}}</div>
                <div>
                  <img :src="'/img/logos/' + bookmaker.logo + '.svg'" class="bookmaker-logo">
                  <span>FONBET</span>
                </div>
              </div>

              <div class="table-cell table-cell--bonus">
                <img :src="'/img/gift.svg'" alt="" class="gift-img">
                {{ bookmaker.bonus }} &#8381;
              </div>

              <div class="table-cell table-cell--has-border table-cell--feedbacks">
                <img :src="'/img/message.svg'" alt="" class="message-img">
                {{ bookmaker.feedbacks }}
              </div>

              <div class="table-cell table-cell--has-border table-cell--complaints">
                <span class="success">{{ bookmaker.complaints[0] }}</span>
                <span class="neutral">&nbsp;/&nbsp;{{ bookmaker.complaints[1] }}&nbsp;/&nbsp;</span>
                <span class="fail">{{ bookmaker.complaints[2] }}</span>
              </div>

              <div class="table-cell table-cell--cta">
                <span class="btn--cta">Играть</span>
                <div class="dropdown-trigger">
                  <img :src="'/img/dropdown-arrow.svg'" alt="" class="message-img">
                </div>
              </div>
            </div>

          </div>
          <div class="sidebar">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {

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
