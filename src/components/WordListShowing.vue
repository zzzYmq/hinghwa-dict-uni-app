<template>
  <view class="cu-list">
    <view
      v-for="(item,index) in wordList"
      :key="index"
      class="padding cu-item"
    >
      <view
        class="flex align-center "
        style="width: 100%;"
      >
        <view
          style="width: 75%;"
        >
          <view class="text-xl text-bold">
            {{ item.word }}
          </view>
          <view>
            <view class="text-lg">
              {{ item.standard_pinyin }}
            </view>
            <view class="text-lg text-gray">
              {{ item.standard_ipa }}
            </view>
          </view>
          <view class="definition">
            {{ item.definition }}
          </view>
        </view>
        <view class="margin-right margin-bottom">
          <button
            type="link"
            class="cu-btn bg-blue shadow"
          >
            <view @tap="toWordPage(item.id)">
              更多
              <view type="double-right" />
            </view>
          </button>
        </view>
      </view>
    </view>
    <view
      v-if="wordList.length === 0"
      class="text-center margin"
    >
      <text class="text-lg text-gray">
        --- 暂无数据 ---
      </text>
    </view>
  </view>
</template>

<script>
import { toWordPage } from '@/routers/word';

export default {
  name: 'WordListShowing',
  props: {
    wordList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      toWordPage,
    };
  },
};
</script>

<style scoped>
.definition{
  overflow: hidden;
  -webkit-line-clamp: 2;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-box-orient: vertical;
}
</style>
