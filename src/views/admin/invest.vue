<template>
  <div class="flex flex-wrap">
    <div class="w-full px-4">
      <div
        class="relative flex flex-col min-w-0 break-words bg-white w-full mb-6 shadow-lg rounded"
      >
        <checkout />
      </div>
    </div>
  </div>
</template>
<script>
import Checkout from "../../components/Cards/checkin.vue";
export default {
  components: {
    Checkout,
  },
};
</script>
