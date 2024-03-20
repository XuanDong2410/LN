<template>
  <q-tabs
    v-model="tab"
    active-color="orange"
    indicator-color="orange"
    align="left"
    class="ml-3"
  >
    <q-tab name="config" label="config" inline-label class="text-capitalize" />
    <q-tab
      name="information"
      label="Information"
      inline-label
      class="text-capitalize"
    />
    <q-tab
      name="security"
      label="security"
      inline-label
      class="text-capitalize"
    />
  </q-tabs>

  <q-tab-panels v-model="tab" animated>
    <q-tab-panel name="security">
      <div class="text-h5 m-2 opacity-80 text-bold">Password</div>

      <q-list class="mb-5 text-16px">
        <q-item>
          <q-item-section>
            <q-item-label>Mật khẩu hiện tại</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-input
              color="orange"
              rounded
              outlined
              v-model="textPass"
              :dense="false"
            />
          </q-item-section>
        </q-item>
        <q-separator />
        <q-item>
          <q-item-section>
            <q-item-label>Mật khẩu mới</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-input
              color="orange"
              rounded
              outlined
              v-model="textPass"
              :dense="false"
            />
          </q-item-section>
        </q-item>
        <q-separator />

        <q-item>
          <q-item-section>
            <q-item-label>Xác nhận mật khẩu mới</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-input
              color="orange"
              rounded
              outlined
              v-model="textPass"
              :dense="false"
            />
          </q-item-section>
        </q-item>
        <q-separator />
        <q-item>
          <q-item-section></q-item-section>
          <q-item-section side top>
            <q-btn color="orange" label="Update" class="m-3" align="center" />
          </q-item-section>
        </q-item>
      </q-list>
    </q-tab-panel>
    <q-tab-panel name="information">
      <div class="text-h5 m-2 opacity-80 text-bold">Personal Information</div>
      <q-list class="max-w-170">
        <q-item>
          <q-item-section>
            <q-item-label>Name</q-item-label>
          </q-item-section>
          <q-item-section>
            {{ nickname }}
            <q-popup-edit
              v-model="nickname"
              :validate="(val) => val.length > 5"
              v-slot="scope"
            >
              <q-input
                autofocus
                dense
                v-model="scope.value"
                counter
                maxlength="18"
                hint="Name"
                :rules="[
                  (val) => scope.validate(val) || 'More than 5 chars required'
                ]"
              >
                <template #after>
                  <q-btn
                    flat
                    dense
                    color="negative"
                    icon="cancel"
                    @click.stop.prevent="scope.cancel"
                  />

                  <q-btn
                    flat
                    dense
                    color="positive"
                    icon="check_circle"
                    @click.stop.prevent="scope.set"
                    :disable="
                      scope.validate(scope.value) === false ||
                      scope.initialValue === scope.value
                    "
                  />
                </template>
              </q-input>
            </q-popup-edit>
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section>
            <q-item-label>Birth day</q-item-label>
          </q-item-section>
          <q-item-section>
            {{ date }}
            <q-popup-edit v-model="date">
              <q-input
                filled
                v-model="date"
                mask="date"
                :rules="['date']"
                color="orange"
              >
                <template #append>
                  <q-icon name="event" class="cursor-pointer">
                    <q-popup-proxy
                      cover
                      transition-show="scale"
                      transition-hide="scale"
                    >
                      <q-date v-model="date" color="orange">
                        <div class="row items-center justify-end">
                          <q-btn
                            v-close-popup
                            label="Close"
                            color="orange"
                            flat
                          />
                        </div>
                      </q-date>
                    </q-popup-proxy>
                  </q-icon>
                </template>
              </q-input>
            </q-popup-edit>
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section>
            <q-item-label>Gender</q-item-label>
          </q-item-section>
          <q-item-section>
            {{ gender }}
            <q-popup-edit v-model="gender">
              <q-radio v-model="gender" val="Male" label="Male" />
              <q-radio v-model="gender" val="Female" label="Female" />
              <q-radio v-model="gender" val="Other.." label="Other.." />
            </q-popup-edit>
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section>
            <q-item-label>Email</q-item-label>
          </q-item-section>
          <q-item-section>
            {{ email }}
            <q-popup-edit
              v-model="email"
              :validate="(val) => val.length > 5"
              v-slot="scope"
            >
              <q-input
                autofocus
                dense
                v-model="scope.value"
                counter
                maxlength="50"
                hint="Name"
                :rules="[
                  (val) => scope.validate(val) || 'More than 5 chars required'
                ]"
              >
                <template #after>
                  <q-btn
                    flat
                    dense
                    color="negative"
                    icon="cancel"
                    @click.stop.prevent="scope.cancel"
                  />

                  <q-btn
                    flat
                    dense
                    color="positive"
                    icon="check_circle"
                    @click.stop.prevent="scope.set"
                    :disable="
                      scope.validate(scope.value) === false ||
                      scope.initialValue === scope.value
                    "
                  />
                </template>
              </q-input>
            </q-popup-edit>
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section></q-item-section>
          <q-item-section side top>
            <q-btn color="orange" label="Update" class="m-3" align="center" />
          </q-item-section>
        </q-item>
      </q-list>
    </q-tab-panel>
    <q-tab-panel name="config">
      <div class="text-h5 m-2 opacity-80 text-bold">Setting</div>

      <q-list class="mb-5">
        <q-item>
          <q-item-section>
            <q-item-label>Thông báo chương mới</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-toggle
              color="orange"
              false-value="Disagreed"
              true-value="Agreed"
              v-model="NotifyChap"
            />
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section>
            <q-item-label>Thông báo Tương tác</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-toggle
              color="orange"
              false-value="Disagreed"
              true-value="Agreed"
              v-model="NotifyContact"
            />
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section>
            <q-item-label>Sắp xếp truyện Đang đọc theo</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-select
              color="orange"
              transition-show="jump-up"
              transition-hide="jump-up"
              filled
              v-model="model"
              :options="options"
              style="width: 250px"
            />
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section>
            <q-item-label>Sắp xếp truyện Đánh dấu theo</q-item-label>
          </q-item-section>
          <q-item-section>
            <q-select
              color="orange"
              transition-show="jump-up"
              transition-hide="jump-up"
              filled
              v-model="modelTag"
              :options="optionsTag"
              style="width: 250px"
            />
          </q-item-section>
        </q-item>
      </q-list>
      <q-btn
        color="orange"
        label="Update"
        class="absolute-bottom-right right-10 bottom-0"
      />
    </q-tab-panel>
  </q-tab-panels>
</template>

<script lang="ts" setup>
import { ref } from "vue"
const nickname = ref("Đào Xuân Đông")
const date = ref("2003/10/24")
const gender = ref("Male")
const email = ref("daoxuandong7012@gmail.com")
const textPass = ref("")
const tab = ref("config")
const NotifyChap = ref("Agreed")
const NotifyContact = ref("Agreed")
const model = ref("Mới đọc")
const modelTag = ref("Mới đánh dấu")
const options = ["Mới lên chương", "Mới đọc", "Tên truyện"]
const optionsTag = ["Mới đánh dấu", "Mới lên chương", "Tên truyện"]
</script>
