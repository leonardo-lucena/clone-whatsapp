<template>
    <div class="row" :class="my ? 'justify-end':'justify-start'">
        <div class="message row justify-between items-center q-py-sm q-px-md q-ma-md"
        :class="my ? 'my':'other'">
            <div class="text">
                {{  text  }}
            </div>
            <span>{{ hour }}</span>
        </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Message',
  props: ['text', 'hour', 'my']
})
</script>

<style lang="scss" scoped>
.message {
  width: 280px;
  height: auto;
  border-radius: 22px;

  span {
    color: $font-grey;
  }
  .text{
    width: 200px;
  }
}

.my {
    background-color: $my-message;
}

.other {
    background-color: $other-message;
}
</style>
