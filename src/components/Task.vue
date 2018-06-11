<template>
    <li class="task">
        <div class="task__content">
            <Checkbox
                class = "complete"
                color1 = '#56d26c'
                color2 = '#3f4d5c'
                color3 = '#fcfefc'
                :checked = 'task.completed'
                @toggle-done-status="$emit('toggle-done-status', task.id)"
            />
            <input
                    autofocus
                    class="task__editable-desc"
                    type="text" v-if="this.isEditable"
                    v-model="message"
                    @keyup.esc="toggleEditStatus"
                    @keyup.enter="$emit('update-task', task.id, message, toggleEditStatus)"
            >
            <span v-else>{{ task.message }}</span>
        </div>
        <div class="task__actions">
            <Star
                    class = "setPriority"
                    color1 = '#ffc868'
                    color2 = '#3f4d5c'
                    :checked = 'task.favorite'
                    @toggle-favorite-status="$emit('toggle-favorite-status', task.id)"
            />
            <Edit
                    class = "edit"
                    color1 = '#56d26c'
                    color2 = '#3f4d5c'
                    @toggle-edit-status="toggleEditStatus"
            />
            <Remove
                    class = "remove"
                    color1 = '#ff5358'
                    color2 = '#3f4d5c'
                    @toggle-remove-status="$emit('toggle-remove-status', task.id)"
            />
        </div>
    </li>
</template>

<script>
import Checkbox from './Checkbox.vue';
import Star from './Star.vue';
import Edit from './Edit.vue';
import Remove from './Remove.vue';
export default {
  name: 'Task',

  components: {
    Checkbox,
    Star,
    Edit,
    Remove,
  },

  props: [
    'task',
  ],

  data: function () {
    return {
      isEditable: false,
      message: 'Loading..',
    }
  },

  mounted: function () {
    this.message = this.task.message;
  },

  methods: {
    toggleEditStatus: function () {
      this.isEditable = !this.isEditable;
    }
  },
};
</script>

<style lang="scss" scoped>
    .task {
        position: relative;
        display: flex;
        align-items: center;
        justify-content: space-between;
        min-height: 61px;
        margin-bottom: 13px;
        padding: 10px 20px;
        background-color: var(--paletteColor12);
        border-radius: 5px;
        box-shadow: 6px 6px 14px var(--rgbaColor1);
        font-size: 20px;
        font-weight: 400;
        color: var(--paletteColor13);

        svg {
            cursor: pointer;
            flex-shrink: 0;
        }

        &__content {
            display: flex;
            align-items: center;
            flex: 0 1 85%;

            & .complete {
                margin-right: 20px;
            }

            span {
                align-items: center;
                display: flex;
                margin-right: 1.9rem;
                overflow: hidden;
                text-overflow: ellipsis;
                line-height: 1;
            }
        }

        &__actions {
            display: flex;

            svg {
                margin-right: .5rem;
            }

            .setPriority,
            .edit {
                margin-right: .5rem;
            }
        }

        &__editable-desc {
            width: 100%;
            height: 42px;
        }
    }
    .completed {
        opacity: .5;
        text-decoration: line-through;
    }
</style>
