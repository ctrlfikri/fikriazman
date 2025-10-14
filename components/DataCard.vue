<template>
  <section ref="statsSection" class="w-full bg-black text-white py-16 sm:py-20 lg:py-24">
    <div class="max-w-6xl mx-auto px-6 lg:px-8">
      <div class="grid grid-cols-1 sm:grid-cols-3 gap-12 text-center">
        
        <!-- Stat 1 -->
        <div>
          <div class="text-5xl font-bold mb-2">{{ displayYears }}+</div>
          <p class="text-gray-400 text-sm uppercase tracking-wide">
            Years in Graphic Design Industry
          </p>
        </div>

        <!-- Stat 2 -->
        <div>
          <div class="text-5xl font-bold mb-2">{{ displayDesigns }}+</div>
          <p class="text-gray-400 text-sm uppercase tracking-wide">
            Designs Created
          </p>
        </div>

        <!-- Stat 3 -->
        <div>
          <div class="text-5xl font-bold mb-2">{{ displayEngagement }}%</div>
          <p class="text-gray-400 text-sm uppercase tracking-wide">
            TikTok Engagement Rate (CTRLPC)
          </p>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue'

const statsSection = ref(null)

// Reactive display values - start with 0
const displayYears = ref(0)
const displayDesigns = ref(0)
const displayEngagement = ref(0)

const hasAnimated = ref(false)

// Target values
const yearsTarget = 2
const designsTarget = 300
const engagementTarget = 13

onMounted(async () => {
  await nextTick()

  const section = statsSection.value
  if (!section) return

  // Check if already in view
  const checkIfInView = () => {
    const rect = section.getBoundingClientRect()
    const isInView = rect.top < window.innerHeight && rect.bottom >= 0
    
    if (isInView && !hasAnimated.value) {
      startCount()
      hasAnimated.value = true
      return true
    }
    return false
  }

  // Check immediately
  if (checkIfInView()) return

  // Set up observer for when scrolling
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting && !hasAnimated.value) {
          startCount()
          hasAnimated.value = true
          observer.disconnect()
        }
      })
    },
    { threshold: 0.3 }
  )

  observer.observe(section)
})

function easeOutQuad(t) {
  return t * (2 - t)
}

function animateValue(refValue, target, duration, decimals = 0) {
  const startTime = performance.now()

  function update(currentTime) {
    const elapsed = currentTime - startTime
    const progress = easeOutQuad(Math.min(elapsed / duration, 1))
    const value = progress * target

    if (decimals > 0) {
      refValue.value = parseFloat(value.toFixed(decimals))
    } else {
      refValue.value = Math.floor(value)
    }

    if (progress < 1) {
      requestAnimationFrame(update)
    } else {
      // Ensure final value is exact
      if (decimals > 0) {
        refValue.value = parseFloat(target.toFixed(decimals))
      } else {
        refValue.value = target
      }
    }
  }

  requestAnimationFrame(update)
}

function startCount() {
  animateValue(displayYears, yearsTarget, 1200, 0)
  animateValue(displayDesigns, designsTarget, 1500, 0)
  animateValue(displayEngagement, engagementTarget, 1200, 1)
}
</script>

<style scoped>
section {
  overflow: hidden;
}
</style>