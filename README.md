# ⚡️ Sveltick

Welcome to **Sveltick**! This is a super lightweight 🦋 and fun performance-tracking library for your Svelte apps. Track important performance metrics like:

## 🚀 New Version 1.2.0
- Added performance alerts for all metrics (FCP, LCP, TTI, CLS, Component Render Times)
- Customizable thresholds for alerts

## 📊 Metrics to check

- **First Contentful Paint** ⚡️
- **Time to Interactive** 🕒
- **Component Render Time** 🔧
- **Largest Contentful Paint** 📏
- **Cumulative Layout Shift** 📊

## 🚀 Installation

Install **Sveltick** via npm:

```bash
npm install sveltick
```

Install **Sveltick** via yarn:

```bash
yarn add sveltick
```

## 🔥 Quick Start
Import **Sveltick** into your Svelte app and start tracking your app's performance!

Tracking `⚡️First Contentful Paint`, 🕒`Time to Interactive`, 📏`Largest Contentful Paint` & `📊 Cumulative Layout Shift`
```svelte
<script>
  import { onMount } from 'svelte';
  import { trackFirstContentfulPaint, trackTimeToInteractive, trackLargestContentfulPaint, trackCumulativeLayoutShift } from 'sveltick';

  onMount(() => {
    // Track metrics
    trackFirstContentfulPaint();
    trackTimeToInteractive();
    trackLargestContentfulPaint();
    trackCumulativeLayoutShift();
  });
</script>
```

## 🔧 Tracking `Component` Render Times

```svelte
  import { onMount } from 'svelte';
  import { trackComponentRender } from 'sveltick';

  onMount(() => {
    const renderTime = performance.now();  // Measure render time
    trackComponentRender('YourComponent', renderTime);  // Track component render
  });
```

## 🛠 Performance Report
You can access all performance metrics at any point using:

```svelte
import { getPerformanceMetrics } from 'sveltick';

const metrics = getPerformanceMetrics();
console.log(metrics); // Output your performance metrics 🧐
```

## 📈 Tracking **all reports** at once (`🔧components` + `⚡️FCP`, `🕒TTI`, `📏LCP` & `📊CLS`)

```svelte
  import { onMount } from 'svelte';
  import { getPerformanceMetrics } from 'sveltick';

  onMount(async () => {
    const metrics = await getPerformanceMetrics();
    console.log('Performance Metrics (including component renders):', metrics);
  });
```

## ⚠️ Checking for all performance with custom threshold alerts
```svelte
  import { onMount } from 'svelte';
  import { getPerformanceMetrics, checkPerformanceAlerts } from 'sveltick';

  onMount(async () => {
    const metrics = await getPerformanceMetrics();
    console.log('Updated Performance Metrics:', metrics);

    // Check for any performance alerts with custom thresholds
    checkPerformanceAlerts({
      fcp: 1800,  // Custom threshold for FCP
      lcp: 2300,  // Custom threshold for LCP
      tti: 2800,  // Custom threshold for TTI
      cls: 0.15,  // Custom threshold for CLS
      componentRenderTime: 400 // Custom threshold for component render time
    });
  });
```

## 📜 License
MIT ©️ Adam Stadnik