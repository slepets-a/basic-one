<template>
    <svg class="remove" version="1.1" viewBox="0 0 53.8 53.8" width="17" height="17" @click="$emit('toggle-remove-status')">
        <g>
            <path
                    d = 'M53 49.5c1 1 1 2.6 0 3.5-.5.5-1.1.7-1.8.7-.6 0-1.3-.2-1.8-.7L26.9 30.4 4.3 53c-.5.5-1.1.7-1.8.7-.6 0-1.3-.2-1.8-.7-1-1-1-2.6 0-3.5l22.6-22.6L.7 4.3c-1-1-1-2.6 0-3.5 1-1 2.6-1 3.5 0l22.6 22.6L49.5.7c1-1 2.6-1 3.5 0 1 1 1 2.6 0 3.5L30.4 26.9 53 49.5z'
                    :fill = 'fill'
            />
        </g>
    </svg>
</template>

<script>
  export default {
    name: 'Checkbox',
    props: [
      'disabled',
      'hover',
      'color1',
      'color2',
      'color3',
    ],
    computed: {
      fill: function () {
        return this.disabled ? this.color3 : this.hover ? this.color1 : this.color2;
      },
    },
  };
</script>

<style lang="scss" scoped>
    .remove {
        display: inline-block;
    }
</style>
