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
        <div class="logo-wrapper">
          <img :src="'/img/logos/' + bookmaker.logo + '.svg'" class="bookmaker-logo">
          <span>FONBET</span>
        </div>
      </div>

      <div class="table-cell table-cell--bonus">
        <img :src="'/img/gift.svg'" alt="" class="gift-img">
        {{ bookmaker.bonus }} &#8381;
      </div>

      <div class="table-cell table-cell--has-border table-cell--feedbacks">
        <span class="mobile-title">Отзывы</span>
        <img :src="'/img/message.svg'" alt="" class="message-img">
        {{ bookmaker.feedbacks }}
      </div>

      <div class="table-cell table-cell--has-border table-cell--complaints">
        <span class="mobile-title">Жалобы</span>
        <span class="success">{{ bookmaker.complaints[0] }}</span>
        <span class="neutral">&nbsp;/&nbsp;{{ bookmaker.complaints[1] }}&nbsp;/&nbsp;</span>
        <span class="fail">{{ bookmaker.complaints[2] }}</span>
      </div>

      <div class="table-cell table-cell--cta">
        <span class="btn btn--cta">Играть</span>
        <span class="btn btn--overview">Обзор</span>
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
            isActive: true,
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
    width: 100%;

    &__row {
      display: grid;

      grid-template-areas:
        "logo bonus"
        "feedbacks feedbacks"
        "complaints complaints"
        "details details"
        "cta cta";
      column-gap: 4px;
      grid-template-columns: auto 130px; // 152px 130px 91px 139px 150px;
      padding: 24px 0;
      &:not(:last-child) {
        border-bottom: 1px solid #E2E4E8;
      }
      &:first-child {
        border-bottom: transparent;
      }

      &:nth-child(2) { //mobile
        padding: 0 0 24px;
      }
    }

    &__header {
      padding: 0;
      display: none;

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
      align-items: center;
      font-weight: 700;
      font-size: 14px;
      line-height: 1.43em;
      letter-spacing: 0.6px;
      font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
      color: #1C1D1F;
      border-radius: 8px;
      margin: 0 0 8px 0;

      &--logo {
        font-size: 14px;
        line-height: 24px;
        grid-area: logo;

        .cell-number {
          width: 16px;
          height: 16px;
          border-radius: 4px;
          display: flex;
          justify-content: center;
          align-items: center;
          background: #1C1D1F;
          color: #FFFFFF;
          flex-shrink: 0;
          margin: 0 16px 0 0;
          align-self: flex-start;
        }

        .logo-wrapper {
          display: flex;
          flex-direction: column;
        }

        .bookmaker-logo {
          width: 96px;
        }
      }

      &--bonus {
        background: #FFF5CF;
        grid-area: bonus;
        justify-content: center;

        .gift-img {
          margin: 0 8px 0 0;
        }
      }

      &--feedbacks {
        grid-area: feedbacks;


        .message-img {
          display: none;
        }
      }

      &--feedbacks,
      &--complaints {
        padding: 0 0 0 32px; //mob
        justify-content: flex-start; //mob
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
        //padding: 0 0 0 30px; //0 0 0 12
        padding: 0 0 0 14px;
        justify-content: flex-end;

        .btn {
          display: flex;
          justify-content: center;
          align-items: center;
          height: 48px;
          border-radius: 8px;
          color: #FFFFFF;
          font-family: 'Raleway', sans-serif;
          font-style: normal;
          font-weight: 700;
          font-size: 16px;
          line-height: 1.5em;
          letter-spacing: 0.6px;
          font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
          padding: 12px 20px;
        }

        .btn--cta {
          background: #E95836;
          margin: 0 8px 0 0; // 0 4 0 0
        }

        .btn--overview {
          background: #1C1D1F;
          margin: 0 8px 0 0;
        }
      }

      .cta {
        display: flex;
        flex-wrap: wrap;
        .info {
          order: -1;
          width: 100%;
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
          height: 48px;
          border-top: 1px solid #E2E4E8;
          border-bottom: 1px solid #E2E4E8;
          display: flex;
          align-items: center;
          justify-content: space-between;
        }

        .comparison-container {
          display: flex;
          justify-content: space-between;
          flex-direction: column;

          .comparison-list {
            width: 100%;
            list-style: none;
            margin: 0;
            padding: 16px 0;
            &:last-of-type {
              border-top: 1px solid #E2E4E8;;
            }

            &__title {
              display: flex;
              align-items: center;
              white-space: pre-wrap;
              font-size: 15px;
              line-height: 1.73em;
              margin: 0 0 8px;
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
              //font-size: 14px;
              //line-height: 1.7em;
              font-size: 12px;
              line-height: 1.8em;
              font-feature-settings: 'pnum' on, 'lnum' on;
              color: #1C1D1F;
              padding: 0 0 0 12px; //0 0 0 5
              margin: 0;
              &:not(:last-child) {
                margin: 0 0 10px 0;
              }

              &::before {
                content: '• ';
                white-space: pre-wrap;
              }
            }
          }
        }

        .bonuses {

          .bonus {
            flex-direction: column;
            justify-content: center;
            align-items: center;
            display: flex;
            padding: 56px 16px 24px;
            background:  #FFF5CF url("/img/gift.svg") no-repeat;
            background-position: center 16px;
            border-radius: 8px;
            margin: 0 0 16px 0;
            &:last-of-type {
              margin: 0 0 16px 0;
            }

            &:not(:first-child) {
              display: none;
            }

            span {
              margin: 0 0 16px;
              font-weight: 900;
            }

            .bonus-cta {
              width: 174px;
              height: 48px;
              padding: 12px 20px;
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
          align-items: flex-start;
          justify-content: center;
          flex-direction: column;
          border: 1px solid #E2E4E8;
          border-radius: 8px;
          padding: 16px;
          margin: 0 0 32px 0;

          span {
            font-weight: 700;
            margin: 0 0 8px;
          }

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
            display: none;
          }

          .read-btn {
            display: none;
          }

          .info {
            font-style: normal;
            font-weight: normal;
            font-size: 14px;
            line-height: 1.7em;
            font-feature-settings: 'pnum' on, 'lnum' on;
            color: #1C1D1F;
            display: flex;
            letter-spacing: 0;
            &:hover,
            &:active {
              color: #1C1D1F;
            }
            &::before {
              content: '';
              background: url("/img/icon-info.svg") no-repeat center;
              background-size: contain;
              width: 14px;
              height: 1.7em;
              margin: 0 10px 0 0;
              display: block;
              flex-shrink: 0;
            }
          }
        }
      }

      .mobile-title {
        margin: 0 16px 0 0;
      }

      .dropdown-trigger {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 48px;
        height: 48px;
        border-radius: 8px;
        background: #F3F6F9;
        flex-shrink: 0;
      }
    }
  }

  @media screen and (min-width: 768px) {
    .table {
      //margin: 0 40px 0 0;

      &__row {
        grid-template-areas:
          "logo bonus feedbacks complaints cta"
          "details details details details details";
        grid-template-columns: 152px 130px 91px 139px auto; //auto = 150px
        &:nth-child(2) {
          padding: 24px 0;
        }
      }

      &__header {
        display: grid;
      }

      &-cell {
        justify-content: center;
        margin: 0 4px 0 0;
        flex-shrink: 0;

        &--logo {

          .cell-number {
            width: 24px;
            height: 24px;
            border-radius: 8px;
            margin: 4px 16px 0 0;
          }
        }

        &--feedbacks {
          .message-img {
            width: 20px;
            margin: 0 10px 0 0;
            display: block;
          }
        }

        &--complaints {
          span {
            flex-shrink: 0;
            font-weight: 700;
          }
        }

        &--feedbacks,
        &--complaints {
          padding: 16px 14px;
          justify-content: flex-start; //mob

          .mobile-title {
            display: none;
          }
        }

        &--has-border {
          border: 1px solid #E2E4E8;
          border-radius: 8px;
        }

        &--cta {
          justify-content: flex-end;
          .btn {
            &--overview {
              display: none;
            }
          }
        }

        &--details {
          .mobile-selector {
            border: none;
          }

          .comparison-container {
            flex-direction: row;
            margin: 0 0 24px;

            .comparison-list {
              width: calc(100% / 3);
              list-style: none;
              margin: 0;
              padding: 0 16px;
              &:not(:last-of-type) {
                border-right: 1px solid #E2E4E8;
              }
              &:last-of-type {
                border: none;
              }

              &__title {
                font-size: 20px;
                line-height: 1.6em;
                &::before {
                  height: 1.65em;
                }
              }

              li {
                font-size: 14px;
                line-height: 1.7em;
                letter-spacing: 0;
                &:not(:last-child) {
                  margin: 0 0 20px 0;
                }
              }
            }
          }

          .bonuses {

            .bonus {
              flex-direction: row;
              justify-content: space-between;
              align-items: center;
              height: 56px;
              background-position: 16px;
              padding: 4px 4px 4px 56px;
              &:not(:first-child) {
                display: flex;
              }

              span {
                margin: 0;
              }
            }
          }

          .note {
            flex-direction: row;
            align-items: center;
            justify-content: space-between;
            height: 72px;
            padding: 16px 24px 16px 56px;
            background: url("/img/icon-note.svg") no-repeat 16px center;

            span {
              margin: 0 20px 0 0;
            }
          }

          .cta {
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
              font-style: normal;
              font-weight: bold;
              font-size: 16px;
              line-height: 1.5em;
              letter-spacing: 0.6px;
              font-feature-settings: 'pnum' on, 'lnum' on, 'liga' off;
              margin: 0 auto 0 8px;
            }

            .info {
              align-items: center;
              order: unset;
              width: auto;
            }
          }
        }
      }
    }
  }

  @media screen and (min-width: 1280px) {
    .table {
      margin: 0 40px 0 0;
    }
  }
</style>
