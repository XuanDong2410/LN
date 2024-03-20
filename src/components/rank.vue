<template>
  <q-list>
    <q-item class="w-90%" v-for="item in value" :key="item.index">
      <q-item-section class="col-2 mr-1 d-flex justify-center">
        <q-img
          :fit="'fill'"
          :src="item.img"
          class="w-90px h-120px m-auto img-novel"
          :ratio="3 / 4"
        >
          <div class="absolute-top-left d-flex justify-center transparent">
            <q-icon
              v-if="item.index === 1"
              class="size-3em absolute top--1.5 left--1 text-yellow-400"
            >
              <i-ic-sharp-bookmark />
            </q-icon>
            <q-icon
              v-if="item.index === 2"
              class="size-3em absolute top--1.5 left--1 text-orange-400"
            >
              <i-ic-sharp-bookmark />
            </q-icon>
            <q-icon
              v-if="item.index === 3"
              class="size-3em absolute top--1.5 left--1 text-orange-600"
            >
              <i-ic-sharp-bookmark />
            </q-icon>
            <q-icon
              v-if="item.index > 3"
              class="size-3em absolute top--1.5 left--1 text-gray-400"
            >
              <i-ic-sharp-bookmark />
            </q-icon>
            <h6
              class="size-2.5em absolute top-0 left-0 text-center color-white font-semibold"
            >
              {{ item.index }}
            </h6>
          </div>
        </q-img>
      </q-item-section>
      <q-item-section class="col-10 ml-0!Important">
        <q-item-label
          lines="1"
          class="mb-2 text-bold text-15px opacity-90 hover:text-orange-400 hover:cursor-pointer"
        >
          {{ item.name }}
        </q-item-label>
        <q-item-label class="opacity-70 text-13px text-justify my-2" lines="3">
          {{ item.describe }}
        </q-item-label>
        <div class="flex justify-start py-2 opacity-70 text-13px align-middle">
          <q-chip class="bg-white text-caption" align="center">
            <i-mdi-user-edit /> {{ item.author }}
          </q-chip>
          <q-chip square outline class="bg-white b-white">
            <Component :is="icon" />
            {{ item.read }}
          </q-chip>
          <q-chip square outline class="text-orange-400 b-orange-400">
            {{ item.genre }}
          </q-chip>
        </div>
      </q-item-section>
    </q-item>
    <div class="w-100% py-3">
      <q-pagination
        v-model="current"
        :max="data.length / 10"
        direction-links
        color="orange"
        active-design="unelevated"
        active-color="brown"
        active-text-color="orange"
        class="d-flex justify-center"
      />
    </div>
  </q-list>
</template>
<script lang="ts" setup>
const props = defineProps<{
  data: {
    index: number
    name: string
    author: string
    genre: string
    top: number
    read: number
    vote: number
    gift: number
    favorite: number
    discuss: number
    chap: number
    img: string
    describe: string
  }[]
  icon: Component
  react: string
}>()
const current = ref(1)
const value = computed(() => {
  const itemsPerPage = 10
  const startIndex = (current.value - 1) * itemsPerPage
  const endIndex = startIndex + itemsPerPage
  return props.data.slice(startIndex, endIndex)
})

</script>
<style>
.img-novel {
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.3);
}
</style>
