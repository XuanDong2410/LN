<template>
  <q-card class="my-card mt-10 p-5">
    <q-card-section class="row items-center q-pb-none">
      <div class="text-h6">Báo cáo truyện</div>
      <q-btn
        icon="close"
        class="absolute-top-right"
        side
        round
        dense
        v-close-popup
      />
    </q-card-section>
    <q-separator />

    <q-list>
      <q-item tag="label" v-ripple>
        <q-item-section avatar>
          <q-radio v-model="color" val="teal" color="teal" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Nội dung khiêu dâm</q-item-label>
        </q-item-section>
      </q-item>

      <q-item tag="label" v-ripple>
        <q-item-section avatar>
          <q-radio v-model="color" val="orange" color="orange" />
        </q-item-section>
        <q-item-section>
          <q-item-label
            >Nội dung liên quan tới chính trị, tôn giáo</q-item-label
          >
        </q-item-section>
      </q-item>

      <q-item tag="label" v-ripple>
        <q-item-section avatar top>
          <q-radio v-model="color" val="duplicate" color="cyan" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Nội dung đã đăng, bị trùng</q-item-label>
        </q-item-section>
      </q-item>
      <q-item tag="label" v-ripple>
        <q-item-section avatar top>
          <q-radio v-model="color" val="other" color="black" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Vấn đề khác</q-item-label>
        </q-item-section>
      </q-item>
    </q-list>

    <!-- <div class="q-px-sm q-mt-sm">
      Your selection is: <strong>{{ color }}</strong>
    </div> -->
    <q-input
      v-model="textInput"
      type="textarea"
      label="Thông tin muốn báo cáo"
    />
    <q-separator />
    <q-card-actions align="center">
      <q-btn
        v-close-popup
        flat
        class="bg-orange-500 text-white text-bold w-80%"
        label="Reposts"
      />
    </q-card-actions>
  </q-card>
</template>
<script lang="ts" setup>
import { ref } from "vue"
const color = ref("cyan")
const textInput = ref("")
</script>
