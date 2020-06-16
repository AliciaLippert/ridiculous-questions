<template>
  <div class="mb-6">
      <img src="@/assets/img/gopher.png">
    <div v-if="show">
      <slot/>
    </div>
  </div>
</template>
