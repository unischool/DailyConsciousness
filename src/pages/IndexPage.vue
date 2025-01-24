<template>
  <q-page class="merit-demerit-page q-pa-md">
    <!-- 頂部智慧語錄區 -->
    <div class="wisdom-section text-center q-mb-lg">
      <q-card class="wisdom-card bg-brown-1">
        <q-card-section>
          <div class="text-h6">今日智慧語錄</div>
          <div class="text-subtitle1">{{ dailyWisdom }}</div>
        </q-card-section>
      </q-card>
    </div>

    <!-- 主要功過記錄區域 -->
    <div class="row q-col-gutter-md">
      <!-- 左側功德區域 -->
      <div class="col-12 col-md-6">
        <q-card class="merit-card">
          <q-card-section>
            <div class="text-h6 text-positive">功德紀錄</div>
            <q-form @submit="onMeritSubmit" class="q-gutter-md">
              <q-input v-model="meritForm.description" label="善行描述" outlined dense />
              <q-select
                v-model="meritForm.type"
                :options="meritTypes"
                label="善行類型"
                outlined
                dense
              />
              <q-input
                v-model.number="meritForm.value"
                type="number"
                label="功德能量值"
                outlined
                dense
              />
              <q-btn label="記錄功德" type="submit" color="positive" />
            </q-form>
          </q-card-section>
        </q-card>
      </div>

      <!-- 右側過失區域 -->
      <div class="col-12 col-md-6">
        <q-card class="demerit-card">
          <q-card-section>
            <div class="text-h6 text-negative">過失紀錄</div>
            <q-form @submit="onDemeritSubmit" class="q-gutter-md">
              <q-input v-model="demeritForm.description" label="過失描述" outlined dense />
              <q-select
                v-model="demeritForm.type"
                :options="demeritTypes"
                label="過失類型"
                outlined
                dense
              />
              <q-input v-model="demeritForm.improvement" label="改善建議" outlined dense />
              <q-btn label="記錄過失" type="submit" color="negative" />
            </q-form>
          </q-card-section>
        </q-card>
      </div>
    </div>

    <!-- 統計圖表區域 -->
    <div class="row q-col-gutter-md q-mt-md">
      <div class="col-12">
        <q-card>
          <q-card-section>
            <div class="text-h6">修行進度追蹤</div>
            <!-- 這裡可以加入圖表組件 -->
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 每日智慧語錄
const dailyWisdom = ref('勿以善小而不為，勿以惡小而為之。')

// 功德表單數據
const meritForm = ref({
  description: '',
  type: null,
  value: 0,
})

// 過失表單數據
const demeritForm = ref({
  description: '',
  type: null,
  improvement: '',
})

// 功德類型選項
const meritTypes = ['利他行為', '善言善語', '正念修持', '慈悲喜捨', '環境保護']

// 過失類型選項
const demeritTypes = ['不善言語', '負面情緒', '傷害他人', '環境破壞', '放逸懈怠']

// 提交功德記錄
const onMeritSubmit = () => {
  // 實現功德記錄邏輯
  console.log('功德記錄：', meritForm.value)
}

// 提交過失記錄
const onDemeritSubmit = () => {
  // 實現過失記錄邏輯
  console.log('過失記錄：', demeritForm.value)
}
</script>

<style scoped>
.merit-demerit-page {
  background-color: #f5f5dc; /* 牛皮紙背景色 */
}

.wisdom-card {
  background-color: rgba(255, 255, 255, 0.9);
}

.merit-card,
.demerit-card {
  background-color: rgba(255, 255, 255, 0.9);
  transition: all 0.3s ease;
}

.merit-card:hover,
.demerit-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
</style>
