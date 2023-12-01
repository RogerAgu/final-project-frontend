<script setup>
  import { ref } from 'vue'
  import { faker } from '@faker-js/faker'

  import useAPI from '@/composables/useAPI'
  //const { getDepartment } = useAPI()

  const selectCard = () => {
    console.log(`${props.employee.name} selected`)
  }

  const props = defineProps({
    holaday: {
      type: Object,
      required: true,
      default: () => {
        return {
          holadayId: '123',
          holadayName: 'Christmas',
          countryName: 'USA',
           holadayDate: 'Dec 2',
          image: 'https://www.example.com'
        }
      },
    },
  })


</script>

<template>
   <RouterLink v-if="props.holaday.holadayId" :to="`/api/holaday/${props.holaday.holadayId}`">
  <div class="card" @click="selectCard">
    <div class="card-image">
      <img :src="props.holaday.image" alt="" srcset="" />
    </div>
    <div class="card-details">
      <p class="card-details-name font-poppins">{{ props.holaday.holadayName }}</p>

    </div>
  </div>
  </RouterLink>
</template>

<style scoped lang="postcss">
  .card {
    @apply cursor-pointer overflow-hidden rounded-md bg-slate-100 p-8 shadow-md transition-transform duration-300 hover:scale-110 hover:shadow-2xl hover:shadow-slate-900;
    &-image {
      img {
        @apply mx-auto rounded-full object-contain;
      }
    }
    &-details {
      @apply flex flex-col gap-2  pt-6 text-center;
      &-name {
        @apply text-3xl font-thin  tracking-wider text-slate-800;
      }
      &-job {
        @apply -mt-2 text-xs font-bold text-yellow-700;
      }
      &-quote {
        @apply pt-4 text-lg italic text-slate-800;
      }
    }
  }
</style>