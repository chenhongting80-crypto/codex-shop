<script setup>
import { ref } from "vue";

const quickInfo = [
  { label: "营业时间", value: "周二至周日 17:30-23:00" },
  { label: "人均", value: "¥188 · 可选品酒搭配" },
  { label: "地址", value: "梧桐路 118 号一层" },
];

const dishes = [
  {
    meta: "主菜 · 明火",
    name: "炭烤桂花鸭胸",
    description: "低温熟成鸭胸，桂花米醋汁，配烤根茎菜和一点山椒油。",
    price: "¥168",
    featured: true,
  },
  {
    meta: "前菜 · 鲜味",
    name: "青柠腌海鲈鱼",
    description: "薄切海鲈鱼、青柠、紫苏和脆米，入口清爽明亮。",
    price: "¥96",
  },
  {
    meta: "面食 · 手作",
    name: "黑松露菌菇宽面",
    description: "手切宽面裹住菌菇奶油汁，最后刨上熟成奶酪。",
    price: "¥128",
  },
  {
    meta: "甜点 · 温热",
    name: "烤梨米布丁",
    description: "香草米布丁、焦糖烤梨、榛子碎和一点海盐。",
    price: "¥68",
  },
];

const spaceStats = [
  { value: "32", label: "个晚餐座位" },
  { value: "8", label: "席开放厨房吧台" },
  { value: "40+", label: "款小产区酒单" },
];

const visitDetails = [
  { label: "电话", href: "tel:021-5556-0818", text: "021-5556-0818" },
  { label: "地铁", text: "2 号线梧桐路站 3 号口步行 5 分钟" },
  { label: "停车", text: "街对面梧桐里地下车库，凭小票减免 2 小时" },
];

const partyOptions = ["2 位", "3-4 位", "5-6 位", "包场咨询"];
const reservationSent = ref(false);

function submitReservation() {
  reservationSent.value = true;
}
</script>

<template>
  <header class="site-header" aria-label="主导航">
    <a class="brand" href="#top" aria-label="槿食首页">
      <span class="brand-mark">槿</span>
      <span>槿食</span>
    </a>
    <nav class="nav-links" aria-label="页面导航">
      <a href="#menu">菜单</a>
      <a href="#space">空间</a>
      <a href="#visit">到店</a>
    </nav>
    <a class="header-action" href="#reserve">预订</a>
  </header>

  <main id="top">
    <section class="hero" aria-label="餐馆首页首屏">
      <img
        class="hero-image"
        src="/assets/restaurant-hero.png"
        alt="温暖灯光下的现代餐馆与当季菜品"
      />
      <div class="hero-shade" aria-hidden="true"></div>
      <div class="hero-content">
        <p class="eyebrow">Seasonal Table · Shanghai Style</p>
        <h1>把今晚留给一桌好菜</h1>
        <p class="hero-copy">
          热汤咕嘟，小菜满桌，烤盘上升起刚好的香气。和喜欢的人围坐一晚，像走进首尔巷口那间温暖小馆。
        </p>
        <div class="hero-actions">
          <a class="primary-button" href="#reserve">
            <span aria-hidden="true">↗</span>
            预订位置
          </a>
          <a class="secondary-button" href="#menu">
            <span aria-hidden="true">☰</span>
            查看菜单
          </a>
        </div>
      </div>
    </section>

    <section class="quick-info" aria-label="餐馆快速信息">
      <div v-for="item in quickInfo" :key="item.label">
        <span>{{ item.label }}</span>
        <strong>{{ item.value }}</strong>
      </div>
    </section>

    <section class="section intro-section">
      <div class="section-heading">
        <p class="eyebrow">This Week</p>
        <h2>本周值得点</h2>
      </div>
      <p class="section-lede">
        菜单每周微调，保留几道常客会想念的味道，也给应季食材留出舞台。
      </p>
    </section>

    <section id="menu" class="menu-grid" aria-label="推荐菜单">
      <article
        v-for="dish in dishes"
        :key="dish.name"
        class="dish-card"
        :class="{ 'featured-dish': dish.featured }"
      >
        <div class="dish-meta">{{ dish.meta }}</div>
        <h3>{{ dish.name }}</h3>
        <p>{{ dish.description }}</p>
        <span>{{ dish.price }}</span>
      </article>
    </section>

    <section id="space" class="space-section" aria-label="用餐空间">
      <div class="space-copy">
        <p class="eyebrow">Dining Room</p>
        <h2>舒服的距离，刚好的热闹</h2>
        <p>
          开放厨房在餐厅中央，适合看见一顿饭如何被完成。靠窗位适合两人晚餐，长桌留给朋友聚会，吧台则更适合临时起意的一杯酒。
        </p>
      </div>
      <div class="space-panel">
        <div v-for="stat in spaceStats" :key="stat.label">
          <strong>{{ stat.value }}</strong>
          <span>{{ stat.label }}</span>
        </div>
      </div>
    </section>

    <section id="visit" class="visit-section" aria-label="到店信息">
      <div class="visit-block">
        <h2>今晚到店</h2>
        <p>建议提前预订。若临时到访，吧台座位会在 18:00 后按现场顺序安排。</p>
      </div>
      <div class="visit-details">
        <div v-for="detail in visitDetails" :key="detail.label">
          <span>{{ detail.label }}</span>
          <a v-if="detail.href" :href="detail.href">{{ detail.text }}</a>
          <p v-else>{{ detail.text }}</p>
        </div>
      </div>
    </section>

    <section id="reserve" class="reserve-section" aria-label="预订区域">
      <div>
        <p class="eyebrow">Reservation</p>
        <h2>预订一顿不赶时间的晚餐</h2>
      </div>
      <form class="reserve-form" @submit.prevent="submitReservation">
        <label>
          日期
          <input type="date" name="date" />
        </label>
        <label>
          人数
          <select name="party">
            <option v-for="option in partyOptions" :key="option">
              {{ option }}
            </option>
          </select>
        </label>
        <label>
          手机
          <input type="tel" name="phone" placeholder="用于确认预订" />
        </label>
        <button type="submit">
          {{ reservationSent ? "已收到预订" : "发送预订" }}
        </button>
      </form>
    </section>
  </main>
</template>
