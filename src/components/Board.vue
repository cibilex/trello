<template>
<div class="col-xs-5 col-sm-4 col-md-3 board" :class="`bg-${board.bgColor} text-${board.color}`" style="height:85px;" >
  {{board.title}}
</div>
</template>

<script>
export default {
  props:{
    board:{
      type:Object,
      required:true
    }
  },
  setup () {
    return {
    }
  }
}
</script>
