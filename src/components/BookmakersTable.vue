<template>

  <div class="table">
    <div class="table__row table__header">
      <div class="table-cell">Букмекер</div>
      <div class="table-cell">Бонус</div>
      <div class="table-cell">Отзывы</div>
      <div class="table-cell">Жалобы</div>
    </div>

    <div class="table__row"
         v-for="bookmaker of mockData">
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
        <div class="dropdown-trigger" v-on:click="bookmaker.isActive = !bookmaker.isActive">
          <img :src="'/img/dropdown-arrow.svg'" alt="" class="message-img">
        </div>
      </div>

      <div class="table-cell table-cell--details"
           v-bind:class="{ active: bookmaker.isActive }">
        <div class="mobile-selector">
          <span>На мобильных</span>
        </div>
        <div class="comparison-container">
          <ul class="comparison-list">
            <h3 class="comparison-list__title comparison-list__title--plus">Плюсы <span>5</span></h3>
            <li>Приветственный бонус и высокие коэффициенты</li>
            <li>Приветственный бонус</li>
            <li>Приветственный бонус</li>
            <li>Приветственный бонус</li>
          </ul>
          <ul class="comparison-list">
            <h3 class="comparison-list__title comparison-list__title--minus">Минусы <span>5</span></h3>
            <li>Приветственный бонус</li>
            <li>Приветственный бонус</li>
            <li>Приветственный бонус</li>
          </ul>
          <ul class="comparison-list">
            <h3 class="comparison-list__title comparison-list__title--rating">Место в рейтингах</h3>
            <li>Народный</li>
            <li>Надёжность</li>
            <li>Коэффициенты</li>
            <li>Выбор ставок</li>
            <li>Сервис LIVE</li>
          </ul>
        </div>
        <div class="bonuses">
          <div class="bonus">
            <span>Страховка до 10 000 рублей</span>
            <button class="bonus-cta">Получить бонус</button>
          </div>
          <div class="bonus">
            <span>Кешбэк до 15 000 рублей</span>
            <button class="bonus-cta">Получить бонус</button>
          </div>
          <div class="bonus">
            <span>Эксклюзивный бонус за депозит до 8 000 рублей</span>
            <button class="bonus-cta">Получить бонус</button>
          </div>
        </div>
        <div class="note">
          <span>Данный букмекер сотрудничает с Fanler в решении спорных ситуаций</span>
          <a class="note-link" href="">Добавить жалобу</a>
        </div>
        <div class="cta">
          <button class="cta-btn">Начать играть</button>
          <button class="read-btn">Читать обзор</button>
          <a class="info" href="#">Как зарегистрироваться у букмекера BetCity</a>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'BookmakersTable',
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
            isActive: false,
          },
          {
            id: 2,
            logo: 'xbettery',
            bonus: 10000,
            feedbacks: 789,
            complaints: [248, 104, 55],
            isActive: false,
          },
          {
            id: 3,
            logo: '1xstavka',
            bonus: 1000,
            feedbacks: 789,
            complaints: [248, 104, 55],
            isActive: false,
          },
          {
            id: 4,
            logo: 'leonru',
            bonus: 100,
            feedbacks: 789,
            complaints: [248, 104, 55],
            isActive: false,
          },
          {
            id: 5,
            logo: 'betcity',
            bonus: 1000,
            feedbacks: 789,
            complaints: [248, 104, 55],
            isActive: false,
          }
        ]
      }
    },
  }
</script>

<style lang="scss">
  .table {
    margin: 0 40px 0 0;
    width: 100%;

    &__row {
      display: grid;
      grid-template-areas:
        "logo bonus feedbacks complaints cta"
        "details details details details details";
      column-gap: 4px;
      grid-template-columns: 152px 130px 91px 139px 150px;
      padding: 24px 0;
      &:not(:last-child) {
        border-bottom: 1px solid #E2E4E8;
      }
      &:first-child {
        border-bottom: transparent;
      }
    }

    &__header {
      padding: 0;

      .table-cell {
        font-size: 14px;
        line-height: 1.7em;
        font-weight: normal;
        font-family: 'Raleway', sans-serif;
        font-feature-settings: 'pnum' on, 'lnum' on;
        color: #000000;
        justify-content: flex-start;
      }
    }

    &-cell {
      display: flex;
      justify-content: center;
      align-items: center;
      font-weight: 700;
      font-size: 14px;
      line-height: 1.43em;
      letter-spacing: 0.6px;
      font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
      color: #1C1D1F;
      border-radius: 8px;

      &--has-border {
        border: 1px solid #E2E4E8;
        border-radius: 8px;
      }

      &--logo {
        font-size: 14px;
        line-height: 24px;
        grid-area: logo;

        .cell-number {
          width: 24px;
          height: 24px;
          display: flex;
          justify-content: center;
          align-items: center;
          border-radius: 8px;
          background: #1C1D1F;
          color: #FFFFFF;
          flex-shrink: 0;
          margin: 0 16px 0 0;
          align-self: flex-start;
        }

        .bookmaker-logo {
          width: 96px;
        }
      }

      &--bonus {
        background: #FFF5CF;
        grid-area: bonus;

        .gift-img {
          margin: 0 8px 0 0;
        }
      }

      &--feedbacks {
        grid-area: feedbacks;

        .message-img {
          width: 20px;
          margin: 0 10px 0 0;
        }
      }

      &--complaints {
        grid-area: complaints;

        .success {
          color: #77BE40;
        }

        .neutral {
          color: #83868A;
          white-space: pre-wrap;
        }

        .fail {
          color: #E73D50;
        }
      }

      &--cta {
        grid-area: cta;

        padding: 0 0 0 12px;

        .btn--cta {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 98px;
          height: 48px;
          background: #E95836;
          border-radius: 8px;
          margin: 0 4px 0 0;
          color: #FFFFFF;
          font-family: 'Raleway', sans-serif;
          font-style: normal;
          font-weight: 700;
          font-size: 16px;
          line-height: 1.5em;
          letter-spacing: 0.6px;
          font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
        }
      }

      &--details {
        grid-area: details;
        flex-wrap: wrap;
        display: none;

        &.active {
          display: block;
        }

        .mobile-selector {
          width: 100%;
        }

        .comparison-container {
          display: flex;
          justify-content: space-between;

          .comparison-list {
            width: calc(100% / 3);
            list-style: none;
            padding: 0 16px;
            &:not(:last-of-type) {
              border-right: 1px solid #E2E4E8;
            }

            &__title {
              display: flex;
              align-items: center;
              white-space: pre-wrap;
              &::before {
                content: '';
                background-size: contain;
                display: block;
                width: 14px;
                height: 1.6em;
                margin: 0 9px 0 0;
                flex-shrink: 0;
                align-self: flex-start;
              }

              &--plus::before {
                background: url("/img/icon-plus.svg") no-repeat center;
              }

              &--minus::before {
                background: url("/img/icon-minus.svg") no-repeat center;
              }

              &--rating::before {
                background: url("/img/icon-rating.svg") no-repeat center;
              }

              span {
                color: #83868A;
                font-weight: 400;
              }
            }

            li {
              display: flex;
              font-family: 'Raleway', sans-serif;
              font-style: normal;
              font-weight: normal;
              font-size: 14px;
              line-height: 1.7em;
              font-feature-settings: 'pnum' on, 'lnum' on;
              color: #1C1D1F;
              padding: 0 0 0 5px;
              &::before {
                content: '• ';
                white-space: pre-wrap;
              }

              &:not(last-child) {
                margin: 0 0 20px 0;
              }
            }
          }
        }

        .bonuses {

          .bonus {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 56px;
            background:  #FFF5CF url("/img/gift.svg") no-repeat;
            background-position: 16px;
            border-radius: 8px;
            padding: 4px 4px 4px 56px;
            margin: 0 0 8px 0;
            &:last-of-type {
              margin: 0 0 16px 0;
            }

            .bonus-cta {
              width: 174px;
              height: 48px;
              background: #1C1D1F;
              border: none;
              border-radius: 8px;
              display: flex;
              align-items: center;
              justify-content: center;
              font-family: 'Raleway', sans-serif;
              font-style: normal;
              font-weight: bold;
              font-size: 16px;
              line-height: 1.5em;
              letter-spacing: 0.6px;
              font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
              color: #FFFFFF;
              text-decoration: none;
            }
          }
        }

        .note {
          display: flex;
          align-items: center;
          justify-content: center;
          height: 72px;
          border: 1px solid #E2E4E8;
          border-radius: 8px;
          padding: 16px 16px 16px 56px;
          background: url("/img/icon-note.svg") no-repeat 16px center;
          margin: 0 0 32px 0;

          &-link {
            display: block;
            flex-shrink: 0;
            font-family: 'Raleway', sans-serif;
            font-style: normal;
            font-weight: normal;
            font-size: 16px;
            line-height: 2em;
            text-decoration-line: underline;
            font-feature-settings: 'pnum' on, 'lnum' on;
            color: #1C1D1F;
            &:hover,
            &:active {
              color: #1C1D1F;
            }
          }
        }

        .cta {
          display: flex;

          &-btn {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 159px;
            height: 48px;
            background: #E95836;
            border-radius: 8px;
            border: none;
            color: #FFFFFF;
            font-family: 'Raleway', sans-serif;
            font-style: normal;
            font-weight: bold;
            font-size: 16px;
            line-height: 1.5em;
            letter-spacing: 0.6px;
            font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
          }

          .read-btn {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 159px;
            height: 48px;
            background: #F3F6F9;
            border-radius: 8px;
            border: none;
            color: #1C1D1F;
            font-family: 'Raleway', sans-serif;
            font-style: normal;
            font-weight: bold;
            font-size: 16px;
            line-height: 1.5em;
            letter-spacing: 0.6px;
            font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
            margin: 0 auto 0 8px;
          }

          .info {
            font-family: 'Raleway', sans-serif;
            font-style: normal;
            font-weight: normal;
            font-size: 14px;
            line-height: 1.7em;
            font-feature-settings: 'pnum' on, 'lnum' on;
            color: #1C1D1F;
            display: flex;
            align-items: center;
            &:hover,
            &:active {
              color: #1C1D1F;
            }
            &::before {
              content: '';
              background: url("/img/icon-info.svg") no-repeat center;
              background-size: contain;
              width: 14px;
              height: 15px;
              margin: 0 10px 0 0;
              display: block;
            }
          }
        }
      }

      .dropdown-trigger {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 48px;
        height: 48px;
        border-radius: 8px;
        background: #F3F6F9;
      }
    }
  }
</style>
