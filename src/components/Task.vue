<template>
    <li class="task">
        <div class="task__content">
            <Checkbox
                class = "complete"
                color1 = '#56d26c'
                color2 = '#3f4d5c'
                color3 = '#fcfefc'
                v-bind:checked = false
            />
            <span>Message</span>
        </div>
        <div class="task__actions">
            <Star
                    class = "setPriority"
                    color1 = '#ffc868'
                    color2 = '#3f4d5c'
                    v-bind:checked = false
            />
            <Edit
                    class = "edit"
                    color1 = '#56d26c'
                    color2 = '#3f4d5c'
            />
            <Remove
                    class = "remove"
                    color1 = '#ff5358'
                    color2 = '#3f4d5c'
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
  }
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
    }
    .completed {
        opacity: .5;
        text-decoration: line-through;
    }
</style>
