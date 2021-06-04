<template>
  <div class="title-container">
    <a class="go-back"></a>
    <h1 class="title">
      Рейтинг букмекеров <span style="color: #83868A; font-weight: 400">819</span>
    </h1>

    <p class="subtitle collapsed">Все букмекерские конторы у нас на сайте имеют подробный обзор плюсов и минусов, экспертную
      оценку коэффициентов и выбора ставок, а так же информацию о бонусах. Выбрать легальную БК, принимающую ставки на
      спорт через интернет, также помогут наши независимые рейтинги.</p>
  </div>
</template>

<script>
  export default {
    name: 'Title',
  }
</script>

<style lang="scss">

  .title-container {
    display: flex;
    flex-direction: column;
    padding: 0 0 0 36px;
    position: relative;
  }

  .title {
    font-family: 'Montserrat', sans-serif;
    font-style: normal;
    font-weight: 900;
    font-size: 24px;
    line-height: 1.6em;
    letter-spacing: 0.7px;
    color: #1C1D1F;
    margin: 0 0 10px;
  }

  //h1 {
  //  font-size: 44px;
  //  margin: 32px 0 8px 0;
  //}

  .go-back {
    background: url("/img/icon-goback.svg") no-repeat center;
    width: 1.7em;
    height: 1.7em;
    font-size: 24px;
    display: block;
    position: absolute;
    top: 0;
    left: -10px;
  }

  .subtitle {
    font-family: 'Raleway', sans-serif;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 1.7em;
    font-feature-settings: 'pnum' on, 'lnum' on;
    color: #1C1D1F;
    margin: 0 0 16px; // 0 0 40
    overflow: hidden;
    position: relative;

    &.collapsed {
      height: calc(1.7em * 3);
      &::after { //temporal
        content: '... читать полностью';
        text-decoration: underline;
        position: absolute;
        bottom: 0;
        right: 0;
        background: #FFFFFF;
      }
    }
  }
</style>
