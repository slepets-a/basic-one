<template>
    <svg class="checkbox" version="1.1" viewBox="0 0 27 27" width="25" height="25" @click="$emit('toggle-done-status')">
        <g>
            <circle
                    cx = '12.5'
                    cy = '12.5'
                    v-bind:fill = 'fill'
                    height = '25'
                    r = '12.5'
                    v-bind:stroke = 'color1'
                    strokeWidth = '0'
                    x = '1'
                    y = '1'
            />
            <polyline
                    fill = 'none'
                    points = '6,12.5 11,18 20,7'
                    v-bind:stroke = 'checkBoxFill'
                    strokeWidth = '2'
            />
        </g>
    </svg>
</template>

<script>
  export default {
    name: 'Checkbox',
    props: [
      'checked',
      'color1',
      'color2',
      'color3',
    ],
    computed: {
      fill: function () {
        return this.checked ? this.color1 : this.color2;
      },
      checkBoxFill: function () {
        return this.checked ? this.color3 : this.color2;
      }
    },
  };
</script>

<style lang="scss" scoped>
    .checkbox {
        display: inline-block;
    }
</style>
