<script setup lang='ts'>
definePageMeta({
  alias: ['/register-Student'],
})
useHead({
  title: 'Student Registration | Tutorly',
})
</script>

<template>
  <div>
    StudentRegForm
    <RegisterForm role-prop="student" />
  </div>
</template>

<style scoped>

</style>
