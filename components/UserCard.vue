<!-- eslint-disable no-console -->
<script setup lang='ts'>
import { storeToRefs } from 'pinia'
import { useStudentsStore, useTeachersStore, useUsersStore } from '@/stores/users'
import userAvatar from '@/components/UserAvatar.vue'

const users = useUsersStore()
const teachers = useTeachersStore()
const students = useStudentsStore()

const { fullName, role } = storeToRefs(users)
const { subjects, grades, rating } = storeToRefs(teachers)
const { grade, school, area } = storeToRefs(students)

function starRatingRole() {
  if (role.value === 'student') {
    console.log(role.value)
    return false
  }
  else if (role.value === 'teacher') {
    console.log(role.value)
    return true
  }
}
</script>

<template>
  <div>
    <div v-if="role !== ''" class="card w-80 bg-base-100 shadow-xl mx-8 my-8 border-2 border-gray-700">
      <userAvatar />
      <div class="card-body items-center text-center">
        <h2 class="card-title">
          الاسم: {{ fullName }}
        </h2>
        <div v-if="role === 'teacher'">
          <p>التخصص: <span>{{ subjects.toString() }}</span></p>
          <p>المرحلة: {{ grades.toString() }}</p>
          <p>
            التقييم:
            <NuxtRating :read-only="starRatingRole" :rating-value="rating" />
          </p>
          <div class="card-actions justify-center mt-4">
            <NuxtLink to="/booking" class="btn btn-primary">
              احجز موعد
            </NuxtLink>
          </div>
        </div>
        <div v-if="role === 'student'">
          <p>المرحلة: {{ grade }}</p>
          <p>المدرسة: {{ school }}</p>
          <p>المنطقة: {{ area }}</p>
          <p />
          <div class="card-actions" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
