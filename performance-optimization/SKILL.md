
---
name: performance-optimization
description: A comprehensive guide to diagnosing and improving the performance of web and mobile applications.
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# Performance Optimization

## Overview
This skill provides a structured workflow for identifying, analyzing, and resolving performance bottlenecks in web and mobile applications. Performance is a critical feature that directly impacts user experience, conversion rates, and search engine ranking. A slow application can lead to user frustration, abandonment, and a negative brand perception. This guide covers a wide range of optimization techniques, from front-end rendering and asset loading to back-end code efficiency and infrastructure scaling. By using this skill, you can systematically improve your application's speed, responsiveness, and resource consumption, leading to a better user experience and improved business metrics.
_"

## When to Use This Skill
This skill is essential in the following scenarios:

- **Slow Page Load Times:** When users report that your website or web application is taking too long to load.
- **High Bounce Rates:** If you observe a high percentage of users leaving your site after viewing only one page, which can be a symptom of poor performance.
- **Poor Mobile Performance:** When the mobile version of your application is sluggish, unresponsive, or consumes excessive battery.
- **Negative User Feedback:** When you receive direct complaints about the speed and responsiveness of your application.
- **Pre-launch Performance Audit:** Before launching a new application or a major feature, to ensure it meets performance standards.
- **Post-launch Performance Monitoring:** To continuously monitor and improve the performance of a live application.
- **High Server Costs:** If your infrastructure costs are escalating, optimizing performance can lead to more efficient resource utilization and cost savings.
- **Improving SEO Ranking:** Search engines like Google use page speed as a ranking factor, so improving performance can boost your search visibility.

## Core Capabilities

### 1. Performance Auditing & Analysis
This skill enables you to conduct comprehensive performance audits to identify bottlenecks.

- **Utilizing Browser Developer Tools:** Leverage the built-in developer tools in Chrome, Firefox, and Safari to analyze network requests, rendering performance, and memory usage.
- **Leveraging Lighthouse:** Use Google's open-source, automated tool for improving the quality of web pages. Lighthouse audits for performance, accessibility, progressive web apps, SEO, and more.
- **WebPageTest:** Perform in-depth performance analysis from multiple locations around the world, using real browsers and at real consumer connection speeds.
- **Profiling JavaScript Execution:** Identify and optimize slow-running JavaScript functions using the performance profiler in browser developer tools.

### 2. Front-End Optimization
Optimize the client-side of your application for a faster, smoother user experience.

- **Rendering Path Optimization:** Understand and optimize the critical rendering path to display content to users as quickly as possible.
- **Asset Optimization:**
    - **Image Compression:** Compress images without sacrificing quality using tools like ImageOptim or online services.
    - **CSS & JavaScript Minification:** Remove unnecessary characters from CSS and JavaScript files to reduce their size.
    - **Code Splitting:** Break down large JavaScript bundles into smaller chunks that are loaded on demand.
- **Caching Strategies:** Implement effective caching strategies using HTTP headers (e.g., `Cache-Control`, `Expires`) and service workers.
- **Lazy Loading:** Defer the loading of off-screen images and other non-critical assets until they are needed.

### 3. Back-End Optimization
Improve the performance of your server-side code and database interactions.

- **Database Query Optimization:** Analyze and optimize slow-running database queries. Use techniques like indexing, query rewriting, and connection pooling.
- **Code Efficiency:** Profile your back-end code to find and refactor inefficient algorithms and data structures.
- **API Performance:** Optimize the performance of your APIs by using efficient data serialization formats (e.g., Protocol Buffers), implementing pagination, and caching API responses.
- **Asynchronous Processing:** Use background jobs and message queues to offload long-running tasks from the main request-response cycle.

### 4. Infrastructure & Scaling
Configure your infrastructure for optimal performance and scalability.

- **Content Delivery Network (CDN):** Use a CDN to cache static assets closer to your users, reducing latency.
- **Load Balancing:** Distribute incoming traffic across multiple servers to prevent any single server from becoming a bottleneck.
- **Server Configuration:** Fine-tune your web server (e.g., Nginx, Apache) and application server configurations for optimal performance.
- **Cloud-Native Scaling:** Leverage auto-scaling features of cloud providers to automatically adjust your capacity based on traffic.

### 5. Mobile-Specific Optimization
Address the unique performance challenges of mobile applications.

- **Network Usage:** Minimize network requests and data usage to accommodate for slower and less reliable mobile networks.
- **Battery Consumption:** Optimize your code to reduce CPU usage and minimize battery drain.
- **UI Responsiveness:** Ensure a smooth and responsive user interface by offloading long-running tasks from the main UI thread.
- **App Start-up Time:** Reduce the time it takes for your mobile app to launch by optimizing your initialization code and deferring non-essential tasks.

"'_
_"

## Step-by-Step Workflow

### Phase 1: Audit and Identify Bottlenecks

1.  **Define Performance Goals:**
    *   Establish clear and measurable performance metrics. Use frameworks like RAIL (Response, Animation, Idle, Load) to set targets.
    *   **Load:** Aim for a meaningful paint within 1 second.
    *   **Response:** Respond to user input in under 100ms.
    *   **Animation:** Produce a frame in 16ms (for 60fps).
    *   **Idle:** Maximize idle time to increase the likelihood of the page responding quickly to user input.

2.  **Run an Initial Audit:**
    *   Use **Google Lighthouse** to get a baseline performance score and a list of actionable recommendations.
        ```bash
        # Run Lighthouse from the command line
        lighthouse https://your-website.com --view
        ```
    *   Use **WebPageTest** to get a detailed waterfall chart of your site's loading behavior from different locations and connection speeds.

3.  **Analyze the Results:**
    *   **Identify the Critical Rendering Path:** Analyze the waterfall chart to understand which resources are blocking the initial render of the page.
    *   **Find Large Assets:** Look for unoptimized images, large JavaScript bundles, and other oversized files.
    *   **Pinpoint Slow API Calls:** Use the Network tab in browser developer tools to identify API requests that are taking a long time to complete.
    *   **Profile JavaScript Execution:** Use the Performance tab in Chrome DevTools to record and analyze JavaScript execution. Look for long-running functions and areas for optimization.

### Phase 2: Implement Front-End Optimizations

1.  **Optimize the Critical Rendering Path:**
    *   **Minify and Defer CSS:** Minify your CSS files and consider using techniques like critical CSS to inline the styles needed for the initial viewport.
    *   **Asynchronously Load JavaScript:** Use the `async` or `defer` attributes on your `<script>` tags to prevent JavaScript from blocking the parser.

2.  **Optimize Assets:**
    *   **Compress Images:** Use a tool like `imagemin` or an online service to compress all your images.
        ```javascript
        // Example using imagemin with gulp
        const gulp = require('gulp');
        const imagemin = require('gulp-imagemin');

        gulp.task('images', () =>
            gulp.src('src/images/*')
                .pipe(imagemin())
                .pipe(gulp.dest('dist/images'))
        );
        ```
    *   **Minify CSS and JavaScript:** Use tools like `terser` for JavaScript and `cssnano` for CSS.
    *   **Enable Text Compression:** Configure your server to use Gzip or Brotli to compress text-based assets (HTML, CSS, JavaScript).

3.  **Implement Caching:**
    *   **Set `Cache-Control` headers:** Configure your server to send appropriate `Cache-Control` headers for different types of resources.
        ```nginx
        # Nginx configuration for caching static assets
        location ~* \.(?:jpg|jpeg|gif|png|ico|css|js)$ {
            expires 365d;
            add_header Cache-Control "public";
        }
        ```
    *   **Use a Service Worker:** Implement a service worker to cache assets and API responses, enabling offline access and faster repeat visits.

### Phase 3: Implement Back-End Optimizations

1.  **Optimize Database Queries:**
    *   **Identify Slow Queries:** Use your database's slow query log or a performance monitoring tool to find inefficient queries.
    *   **Add Indexes:** Ensure that your database tables are properly indexed, especially for columns used in `WHERE` clauses and `JOIN`s.
    *   **Use a Query Analyzer:** Use a tool like `EXPLAIN` in SQL to understand how your database is executing a query and identify opportunities for optimization.

2.  **Improve Code Efficiency:**
    *   **Profile Your Code:** Use a profiler (e.g., cProfile for Python, Xdebug for PHP) to identify performance hotspots in your code.
    *   **Use Efficient Data Structures and Algorithms:** Choose the right data structures and algorithms for the task at hand.
    *   **Cache Expensive Operations:** Cache the results of computationally expensive functions or database queries.

3.  **Scale Your Infrastructure:**
    *   **Implement a CDN:** Use a CDN like Cloudflare or AWS CloudFront to serve static assets.
    *   **Use a Load Balancer:** If you have multiple servers, use a load balancer to distribute traffic evenly.
    *   **Consider Serverless:** For certain workloads, serverless architectures can provide automatic scaling and cost savings.

### Phase 4: Monitor and Iterate

1.  **Set Up Performance Monitoring:**
    *   Use a tool like **Sentry**, **New Relic**, or **Datadog** to continuously monitor your application's performance in production.
    *   Set up alerts to be notified of performance regressions.

2.  **Establish a Performance Budget:**
    *   A performance budget is a set of limits on metrics that affect site performance (e.g., total image size, number of HTTP requests).
    *   Integrate performance budget checks into your CI/CD pipeline to prevent regressions.

3.  **Regularly Re-audit:**
    *   Schedule regular performance audits to proactively identify and address new bottlenecks as your application evolves.

"'_
## Best Practices

- **Prioritize the User Experience:** Always focus on optimizations that have the most significant impact on the user-perceived performance.
- **Measure, Don't Guess:** Base your optimization efforts on data and measurements, not on assumptions.
- **Optimize for Mobile First:** Given the prevalence of mobile browsing, it's crucial to prioritize performance on mobile devices.
- **Automate Performance Testing:** Integrate performance testing into your development workflow to catch regressions early.
- **Consider the Network:** Be mindful of network latency and bandwidth constraints, especially for users on mobile networks.
- **Keep it Simple:** Avoid premature optimization and complex solutions when a simpler approach will suffice.
- **Stay Up-to-Date:** The landscape of web and mobile performance is constantly evolving. Stay informed about new technologies and best practices.

## Examples

### Example 1: Lazy Loading Images

Here's a simple implementation of lazy loading for images using the `IntersectionObserver` API.

```html
<img data-src="image.jpg" alt="An example image" class="lazy-load">
```

```javascript
document.addEventListener("DOMContentLoaded", function() {
  var lazyImages = [].slice.call(document.querySelectorAll("img.lazy-load"));

  if ("IntersectionObserver" in window) {
    let lazyImageObserver = new IntersectionObserver(function(entries, observer) {
      entries.forEach(function(entry) {
        if (entry.isIntersecting) {
          let lazyImage = entry.target;
          lazyImage.src = lazyImage.dataset.src;
          lazyImage.classList.remove("lazy-load");
          lazyImageObserver.unobserve(lazyImage);
        }
      });
    });

    lazyImages.forEach(function(lazyImage) {
      lazyImageObserver.observe(lazyImage);
    });
  } else {
    // Fallback for browsers that don't support IntersectionObserver
    // ...
  }
});
```

### Example 2: Caching with a Service Worker

This example shows a basic service worker that caches static assets.

```javascript
// service-worker.js
const CACHE_NAME = 'static-cache-v1';
const FILES_TO_CACHE = [
  '/',
  '/index.html',
  '/styles.css',
  '/app.js',
  '/images/logo.png'
];

self.addEventListener('install', (evt) => {
  evt.waitUntil(
      caches.open(CACHE_NAME).then((cache) => {
        console.log('[ServiceWorker] Pre-caching offline page');
        return cache.addAll(FILES_TO_CACHE);
      })
  );
});

self.addEventListener('fetch', (evt) => {
  evt.respondWith(
      caches.match(evt.request).then((response) => {
        return response || fetch(evt.request);
      })
  );
});
```

### Example 3: Critical CSS

An example of how to inline critical CSS for faster rendering.

```html
<html>
<head>
  <style>
    /* Inlined critical CSS */
    body { font-family: sans-serif; }
    .header { background-color: #333; color: #fff; }
  </style>
  <link rel="stylesheet" href="styles.css" media="print" onload="this.media='all'">
</head>
<body>
  <!-- Page content -->
</body>
</html>
```
## References

- [Google Web Fundamentals: Performance](https://developers.google.com/web/fundamentals/performance/)
- [MDN Web Docs: Web Performance](https://developer.mozilla.org/en-US/docs/Web/Performance)
- [WebPageTest](https://www.webpagetest.org/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)
- [High Performance Browser Networking by Ilya Grigorik](https://hpbn.co/)
- [Sentry Performance Monitoring](https://sentry.io/for/performance/)
- [New Relic APM](https://newrelic.com/platform/application-performance-monitoring)

### Example 4: Back-End Caching with Redis

Here is an example of how to cache database query results in a Node.js application using Redis.

```javascript
const express = require('express');
const redis = require('redis');
const { promisify } = require('util');

const app = express();
const client = redis.createClient();
const getAsync = promisify(client.get).bind(client);

app.get('/products/:id', async (req, res) => {
  try {
    const { id } = req.params;
    const cachedProduct = await getAsync(`product:${id}`);

    if (cachedProduct) {
      console.log('Serving from cache');
      return res.json(JSON.parse(cachedProduct));
    }

    console.log('Serving from DB');
    const product = await getProductFromDatabase(id); // Assume this function fetches from DB
    client.setex(`product:${id}`, 3600, JSON.stringify(product)); // Cache for 1 hour

    res.json(product);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

function getProductFromDatabase(id) {
  // Simulate a slow database query
  return new Promise(resolve => {
    setTimeout(() => {
      resolve({ id, name: `Product ${id}`, price: Math.random() * 100 });
    }, 2000);
  });
}

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

## Advanced Topics

### Tree Shaking

Tree shaking is a term commonly used in the context of JavaScript bundlers like Webpack or Rollup. It refers to the process of eliminating dead code, or unused modules, from the final bundle. For tree shaking to work, you must be using ES2015 module syntax (`import` and `export`).

```javascript
// utils.js
export function a() { return 'a'; }
export function b() { return 'b'; }

// main.js
import { a } from './utils.js';

console.log(a());
```

When you bundle `main.js`, a tree-shaking-enabled bundler will analyze the code and see that `b` is never used, so it will be excluded from the final output, resulting in a smaller bundle size.

### Connection Pooling

Database connections are expensive to create. Connection pooling is a technique used to maintain a cache of database connections that can be reused, rather than creating a new connection for every request. This can significantly improve the performance of database-intensive applications.

Most database drivers and ORMs provide built-in support for connection pooling. Here is a conceptual example using Node.js and PostgreSQL:

```javascript
const { Pool } = require('pg');

const pool = new Pool({
  user: 'dbuser',
  host: 'database.server.com',
  database: 'mydb',
  password: 'secretpassword',
  port: 3211,
});

async function query(text, params) {
  const start = Date.now();
  const res = await pool.query(text, params);
  const duration = Date.now() - start;
  console.log('executed query', { text, duration, rows: res.rowCount });
  return res;
}
```

By using the `pool.query` method, you are borrowing a connection from the pool and returning it when the query is complete, which is much more efficient than creating a new connection each time.
