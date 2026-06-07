<script setup lang="ts">
import type { IndexCollectionItem } from "@nuxt/content";

const { footer, global } = useAppConfig();

defineProps<{
  page: IndexCollectionItem;
}>();

const defaultSkills = [
  "Brand Strategist",
  "Systems Developer",
  "Forex Trader",
  "Digital Media Specialist",
];
</script>

<template>
  <div class="portfolio-wrapper">
    <section class="hero-section">
      <!-- LEFT: Text -->
      <div class="hero-text">
        <Motion
          :initial="{ opacity: 0, y: 20, filter: 'blur(10px)' }"
          :animate="{ opacity: 1, y: 0, filter: 'blur(0px)' }"
          :transition="{ duration: 0.6, delay: 0.1 }"
        >
          <h2 class="hello-heading">Hello<span class="accent-dot">.</span></h2>
        </Motion>
        <Motion
          :initial="{ opacity: 0, y: 20, filter: 'blur(10px)' }"
          :animate="{ opacity: 1, y: 0, filter: 'blur(0px)' }"
          :transition="{ duration: 0.6, delay: 0.2 }"
        >
          <p class="sub-heading">
            <span class="red-line desktop-only" />
            I'm Cassim Assedi
          </p>
        </Motion>
        <Motion
          :initial="{ opacity: 0, y: 20, filter: 'blur(10px)' }"
          :animate="{ opacity: 1, y: 0, filter: 'blur(0px)' }"
          :transition="{ duration: 0.6, delay: 0.3 }"
        >
          <h2 class="role-heading">
            Digital Media Specialist, and Systems Developer
          </h2>
        </Motion>
        <Motion
          :initial="{ opacity: 0, y: 20, filter: 'blur(10px)' }"
          :animate="{ opacity: 1, y: 0, filter: 'blur(0px)' }"
          :transition="{ duration: 0.6, delay: 0.45 }"
        >
          <div class="cta-group">
            <UButton
              v-bind="page.hero?.links?.[0]"
              label="Got a project?"
              class="btn-primary-red rounded-full"
              size="lg"
            />
            <UButton
              label="About me"
              color="neutral"
              variant="outline"
              size="lg"
              v-bind="page.hero?.links?.[1]"
              class="btn-outline-white rounded-full"
            />
          </div>
        </Motion>
      </div>
      <!-- RIGHT: Photo with decoration -->
      <Motion
        class="hero-image-wrapper"
        :initial="{ opacity: 0, scale: 0.95, filter: 'blur(10px)' }"
        :animate="{ opacity: 1, scale: 1, filter: 'blur(0px)' }"
        :transition="{ duration: 0.7, delay: 0.2 }"
      >
        <NuxtImg
          :src="global.picture?.light ?? '/hero/hero.png'"
          :alt="global.picture?.alt ?? 'cassim assedi profile picture'"
          class="profile-photo"
          width="300"
          height="400"
        />
      </Motion>
    </section>
    <!-- SKILLS MARQUEE -->
    <div class="marquee-bar">
      <UMarquee pause-on-hover class="[--duration:35s]">
        <span
          v-for="(skill, i) in page.hero?.skills ?? defaultSkills"
          :key="i"
          class="skill-tag"
        >
          {{ skill }}
        </span>
      </UMarquee>
    </div>
  </div>
</template>

<style scoped>
/* ── Base ─────────────────────────────────────────────────── */
.portfolio-wrapper {
  min-height: 100vh;
  /* background: #0d0d14; */
  background: transparent;
  color: #fff;
  display: flex;
  flex-direction: column;
  font-family: "Segoe UI", system-ui, sans-serif;
  overflow: hidden;
}

/* ── Navbar ───────────────────────────────────────────────── */
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 60px;
  position: relative;
  z-index: 50;
}

.logo {
  font-size: 1.05rem;
  font-weight: 700;
  letter-spacing: 0.02em;
  color: #fff;
}

.mobile-hamburger {
  display: none;
}

/* ── Mobile menu ──────────────────────────────────────────── */
.mobile-nav-menu {
  display: flex;
  flex-direction: column;
  background: #161622;
  padding: 8px 16px 16px;
  z-index: 40;
}

.mobile-nav-item {
  justify-content: flex-start !important;
  font-size: 1rem;
  padding: 10px 8px;
}

/* slide transition */
.slide-enter-active,
.slide-leave-active {
  transition:
    max-height 0.3s ease,
    opacity 0.3s ease;
  max-height: 300px;
}
.slide-enter-from,
.slide-leave-to {
  max-height: 0;
  opacity: 0;
}

/* ── Hero Section ─────────────────────────────────────────── */
.hero-section {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 40px 60px 0;
  gap: 40px;
}

/* LEFT text */
.hero-text {
  flex: 1;
  max-width: 520px;
}

.hello-heading {
  font-size: clamp(2.4rem, 5vw, 3.4rem);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 10px;
}

.accent-dot {
  color: #7d6ee7;
}

.sub-heading {
  display: flex;
  align-items: center;
  gap: 14px;
  color: #ccc;
  font-size: 1.1rem;
  margin-bottom: 8px;
}

.red-line {
  display: inline-block;
  width: 40px;
  height: 2px;
  background: #7d6ee7;
  flex-shrink: 0;
}

.role-heading {
  font-size: clamp(1.7rem, 3vw, 1.5rem);
  font-weight: 800;
  line-height: 1.15;
  margin-bottom: 36px;
}

.cta-group {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

/* Override UButton colours */
.btn-primary-red {
  background: #7d6ee7 !important;
  color: #fff !important;
  border: none !important;
}

.btn-outline-white {
  border-color: #fff !important;
  color: #fff !important;
}

/* RIGHT photo */
.hero-image-wrapper {
  position: relative;
  width: 400px;
  height: 460px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.profile-photo {
  position: relative;
  z-index: 2;
  width: 280px;
  height: 390px;
  object-fit: cover;
  object-position: top center;
  border-radius: 4px;
  -webkit-mask-image: linear-gradient(to bottom, black 72%, transparent 100%);
  mask-image: linear-gradient(to bottom, black 72%, transparent 100%);
}

/* ── Marquee bar ──────────────────────────────────────────── */
.marquee-bar {
  background: #161622;
  padding: 16px 0;
  margin-top: auto;
}

.skill-tag {
  color: #777;
  font-size: 0.85rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  padding: 0 48px;
}

/* ── Mobile ───────────────────────────────────────────────── */
@media (max-width: 768px) {
  .desktop-nav {
    display: none;
  }
  .mobile-hamburger {
    display: flex;
  }

  .navbar {
    padding: 18px 20px;
  }

  .hero-section {
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 28px 20px 0;
    gap: 0;
  }

  .hero-text {
    max-width: 100%;
    order: 1;
  }

  .sub-heading {
    justify-content: center;
  }
  .desktop-only {
    display: none !important;
  }

  .cta-group {
    justify-content: center;
    margin-bottom: 28px;
  }

  .hero-image-wrapper {
    order: 2;
    width: 100%;
    height: 360px;
  }

  .profile-photo {
    width: 220px;
    height: 300px;
  }

  .bracket {
    font-size: 3.5rem;
  }
  .bracket-left {
    left: 24px;
  }
  .bracket-right {
    right: 24px;
  }
}
</style>
