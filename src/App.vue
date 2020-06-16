<template>
  <main class="bg-blue-100 h-screen w-screen overflow-hidden flex">
    <div class="flex-grow">
      <preview/>
    </div>
  
  </main>
</template>

<script>
import Preview from '@/components/Preview.vue'

export default {
  components: {
    Preview
  }
}
</script>
