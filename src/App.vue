<script setup lang="ts">
import {
  BottomTabBar,
  GlassPanel,
  IdentityBadge,
  InlineError,
  LianButton,
  LocationChip,
  TagChip,
  ToastHost,
  TopBar,
  TrustBadge,
  TypeChip,
  useToast
} from "./ui";

const toast = useToast();

const tabs = [
  { key: "feed", label: "首页", icon: "⌂" },
  { key: "map", label: "探索", icon: "⌖" },
  { key: "messages", label: "消息", icon: "✉" },
  { key: "profile", label: "我的", icon: "○" }
];

function showPublishSuccess() {
  toast.success("发布成功，已关联到「三食堂」。");
}

function showDraftWarning() {
  toast.warning("AI 暂时无法整理，你可以先保存草稿，稍后重新生成。");
}

function showPublishError() {
  toast.error("发布失败，草稿已保存，可以稍后重试。");
}
</script>

<template>
  <main class="vue-shell" aria-labelledby="vue-shell-title">
    <div class="vue-shell__grid">
      <GlassPanel class="vue-shell__hero">
        <p class="vue-shell__eyebrow">LIAN UI Architecture</p>
        <h1 id="vue-shell-title">Vue UI feedback runtime</h1>
        <p class="vue-shell__summary">
          ToastHost and useToast() are now available as the first runtime feedback boundary before legacy alert/prompt replacement.
        </p>
        <div class="vue-shell__row">
          <LianButton variant="primary" @click="showPublishSuccess">发布成功</LianButton>
          <LianButton variant="tonal" @click="showDraftWarning">AI 提醒</LianButton>
          <LianButton variant="danger" @click="showPublishError">发布失败</LianButton>
        </div>
      </GlassPanel>

      <section class="vue-shell__section">
        <h2>Cards, chips and trust</h2>
        <GlassPanel class="vue-shell__sample-card">
          <div class="vue-shell__row">
            <TypeChip type="experience" icon="✓">经验</TypeChip>
            <LocationChip>三食堂</LocationChip>
            <TrustBadge tone="confirmed">已确认</TrustBadge>
            <TagChip tag="校园晚饭" />
          </div>
          <h3 class="vue-shell__sample-title">三食堂二楼哪家适合晚饭便宜吃饱？</h3>
          <p class="vue-shell__summary">
            卡片保持统一底色，类型依靠 chip、图标、状态和内容结构区分，颜色只做辅助提示。
          </p>
          <div class="vue-shell__sample-meta">
            <IdentityBadge avatar-text="蓝" label="小蓝鲸" meta="饭堂观察员" />
            <span>12 分钟前 · 18 评论 · 已沉淀到地点页</span>
          </div>
        </GlassPanel>
      </section>

      <section class="vue-shell__section">
        <h2>Feedback</h2>
        <InlineError>标签只能包含文字、数字、下划线或连字符，最多 5 个。</InlineError>
      </section>

      <section class="vue-shell__section">
        <h2>Navigation</h2>
        <TopBar title="探索" subtitle="地点组织沉淀，地图负责定位" />
        <BottomTabBar :items="tabs" active-key="feed" />
      </section>
    </div>
  </main>
  <ToastHost />
</template>
