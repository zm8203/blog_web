<template>
  <div class="gvb_home_welcome">
    <div class="title">
      早安，{{ store.userInfo.nick_name }}，请开始一天的工作吧
    </div>
    <gvb_weather class="weather"></gvb_weather>
    <div class="statistics">
        <span>
          <span class="icon">
            <IconSwap style="transform: rotate(90deg)"></IconSwap>
          </span>
          在线流量：{{ statisticsData.flow_count }}
        </span>
      <span>
           <span class="icon">
            <IconUserGroup></IconUserGroup>
          </span>
          用户总数：{{ statisticsData.user_count }}
        </span>
      <span>
           <span class="icon">
            <IconBook></IconBook>
          </span>
          文章总数：{{ statisticsData.article_count }}
        </span>
      <span>
           <span class="icon">
            <IconMessage></IconMessage>
          </span>
          群聊消息：{{ statisticsData.chat_group_count }}
        </span>
      <span>
           <span class="icon">
            <IconBulb></IconBulb>
          </span>
          今日登录：{{ statisticsData.now_login_count }}
        </span>
    </div>
    <div class="link">
      <div>
        <span>前端教程：<a
            href="https://www.bilibili.com/video/BV1V94y1Y725">https://www.bilibili.com/video/BV1V94y1Y725</a></span>
      </div>
      <div>
        <span>后端教程：<a
            href="https://www.bilibili.com/video/BV1f24y1G72C">https://www.bilibili.com/video/BV1f24y1G72C</a></span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import {IconMessage, IconSwap, IconBulb, IconUserGroup, IconBook} from "@arco-design/web-vue/es/icon";
import {statisticsApi} from "@/api/data_api";
import type {statisticsType} from "@/api/data_api";
import {reactive} from "vue";
import {useStore} from "@/stores";
import Gvb_weather from "@/components/admin/gvb_weather.vue";

const store = useStore()
const statisticsData = reactive<statisticsType>({
  article_count: 0,
  chat_group_count: 0,
  flow_count: 0,
  message_count: 0,
  now_login_count: 0,
  now_sign_count: 0,
  user_count: 0,
})

async function getData() {
  let res = await statisticsApi()
  Object.assign(statisticsData, res.data)
}

getData()

</script>
<style lang="scss">
.gvb_home_welcome {
  width: 100%;
  background-image: url("/image/电脑场景.png");
  background-repeat: no-repeat;
  background-position: right;
  background-size: 500px;
  background-color: var(--color-bg-1);
  padding: 20px;
  border-radius: 5px;
  color: var(--color-text-2);

  .title {
    font-size: 22px;
    margin-top: 10px;
    font-weight: 400;
    color: var(--color-text-1);
  }

  .weather {
    margin: 20px 0 10px 0;
  }

  .statistics {
    margin: 20px 0 10px 0;
    font-size: 16px;

    > span {
      margin-right: 20px;
    }
  }

  .link {
    margin: 30px 0 20px 0;

    > div {
      margin-bottom: 20px;

      &:last-child {
        margin-bottom: 0;
      }
    }

    a {
      text-decoration: none;
      color: var(--active);
    }
  }
}
</style>