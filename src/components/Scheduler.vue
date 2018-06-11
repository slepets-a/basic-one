<template>
  <div class="scheduler">
    <main class="paper">
      <header class="header">
        <h1 class="title">Task scheduler</h1>
        <input v-model="tasksFilter" type="text" class="search-input" placeholder="Search.." >
      </header>
      <section class="section">
        <form class="new-task__form">
          <input v-model="description" type="text" class="new-task__input" placeholder="New task description" @keyup.enter="addTask">
          <button class="new-task__add-button" @click.prevent.stop="addTask">Add task</button>
        </form>
        <div>
          <ul class="tasks__list">
            <Task
                    v-for="task in filteredTasks"
                    :key="task.id"
                    :task="task"
                    @toggle-done-status="toggleDoneStatus"
                    @toggle-favorite-status="toggleFavoriteStatus"
                    @toggle-remove-status="toggleRemoveStatus"
                    @update-task="updateTask"
            />
          </ul>
        </div>
      </section>
      <footer class="footer" @click="checkAllTasksDone">
        <div class="done-tasks__checkbox">
          <svg version="1.1" viewBox="0 0 27 27" style="width: 25px; height: 25px; display: block;">
            <g>
              <circle cx="12.5"
                      cy="12.5"
                      :fill="allTasksDoneCheckbox"
                      height="25"
                      r="12.5"
                      stroke="#56d26c"
                      stroke-width="0"
                      x="1"
                      y="1"
              >
              </circle>
              <polyline fill="none"
                        points="6,12.5 11,18 20,7"
                        stroke="#3f4d5c"
                        stroke-width="2"
              >
              </polyline>
            </g>
          </svg>
        </div>
        <span class="done-tasks__description">
          All tasks done
        </span>
      </footer>
    </main>
  </div>
</template>

<script>
  import Task from './Task.vue';
  export default {
    name: 'HelloWorld',

    components: {
      Task,
    },

    props: {
      msg: String,
    },

    data: function () {
      return {
        tasks: [
          {
            "id": "xjh",
            "message": "Успешно пройти React-интенсив компании Lectrum",
            "completed": false,
            "favorite": true
          },
          {
            "id": "xjr",
            "message": "Взять автограф у Джареда Лето",
            "completed": false,
            "favorite": false
          },
          {
            "id": "xrh",
            "message": "Зарегестрировать бабушку в Твиче",
            "completed": false,
            "favorite": false
          },
          {
            "id": "rjh",
            "message": "Записать собаку на груминг",
            "completed": false,
            "favorite": false
          },
          {
            "id": "xph",
            "message": "Научиться играть на барабанах",
            "completed": true,
            "favorite": false
          }
        ],
        description: '',
        tasksFilter: '',
      }
    },

    computed: {
      allTasksDoneCheckbox: function () {
        return this.areTasksDone() ? '#56d26c' : '#3f4d5c';
      },

      filteredTasks: function () {
        return this.tasks.filter(({ message }) => message.toLowerCase().includes(this.tasksFilter));
      }
    },

    methods: {
      addTask: function () {
        if (this.description) {
          this.tasks.push({
            completed: false,
            created: Date.now(),
            favorite: false,
            id: Math.random(),
            message: this.description,
            modified: null,
          });
          this.description = '';
        }
      },

      updateTask: function (id, message, cb) {
        this.tasks = this.tasks.map((task) => task.id === id ? {...task, message: message } : task);
        if (cb) {
          cb();
        }
      },

      toggleDoneStatus: function (id) {
        this.tasks = this.tasks.map((task) => task.id === id ? {...task, completed: !task.completed} : task);
      },

      toggleFavoriteStatus: function (id) {
        this.tasks = this.tasks.map((task) => task.id === id ? {...task, favorite: !task.favorite} : task);
      },

      toggleRemoveStatus: function (id) {
        this.tasks = this.tasks.filter((task) => task.id !== id );
      },

      checkAllTasksDone: function () {
        this.tasks = this.tasks.map((task) => ({...task, completed: true}));
      },

      areTasksDone: function () {
        return this.tasks.every(task => task.completed);
      },
    },
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
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

    @media (max-width: 50rem) {
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
    margin: 0;
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

  .new-task {

    &__form {
      display: flex;
      justify-content: space-between;
      margin: 0 0 18px;
    }

    &__input {
      margin-right: 22px;
      min-width: 215px;
      width: 100%;
    }

    &__add-button {
      background-color: var(--paletteColor15);
      background-image: url(../assets/plus-icon.svg);
      background-position: 6% 50%;
      background-repeat: no-repeat;
      background-size: 18px 18px;
      border: 0;
      border-radius: 5px;
      color: var(--paletteColor2);
      cursor: pointer;
      font-size: 18px;
      height: 42px;
      min-width: 215px;
      padding-left: 25px;
      transition: background-color .3s ease-in-out;

      &:hover {
        background-color: var(--paletteColor14);
      }
    }
  }

  .tasks {

    &__list {
      min-height: 370px;
      max-height: 370px;
      overflow: auto;
      padding: 0;
    }
  }

  .footer {
    align-items: center;
    display: flex;
    justify-content: initial;
  }
  .done-tasks {

    &__checkbox {
      display: inline-block;
      width: 25px;
      height: 25px;
      cursor: pointer;
      margin: 0 20px;
    }

    &__description {
      color: var(--paletteColor3);
      font-size: 20px;
      vertical-align: top;
    }
  }
</style>
