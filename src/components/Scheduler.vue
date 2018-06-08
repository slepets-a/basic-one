<template>
  <div class="scheduler">
    <main class="paper">
      <header class="header">
        <h1 class="title">Task scheduler</h1>
        <input type="text" class="search-input" placeholder="Search..">
      </header>
      <section class="section">

      </section>
      <footer class="footer">

      </footer>
    </main>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .scheduler {
    align-items: center;
    display: flex;
    justify-content: center;
    padding: 3% 7%;
    user-select: none;
  }
  .paper {
    background-color: var(--paletteColor6);
    border-radius: 10px;
    box-shadow: 6px 6px 14px var(--rgbaColor2);
    height: 100%;
    max-width: 1200px;
    padding: 50px 85px;
    width: 100%;

    @media all(max-width: 50rem) {
      padding: 30px 15px;
    }
  }
  .header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 45px;
  }
  .title {
    color: var(--paletteColor5);
    font-size: 32px;
    font-weight: 500;
  }
  .search-input {
    background-color: var(--paletteColor3);
    background-image: url(../assets/search-icon.svg);
    background-position: 95% 50%;
    background-repeat: no-repeat;
    background-size: 18px 18px;
    box-shadow: 6px 6px 14px var(--rgbaColor2);
    color: var(--paletteColor13);
    height: 42px !important;
    width: 215px;
  }
  .section {
    margin-bottom: 31px;
  }
  .footer {
    align-items: center;
    display: flex;
    justify-content: initial;
  }
</style>
