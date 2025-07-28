# 第五章：技術SEO調整

## AI時代的技術基礎

### 爬蟲優化的新重要性

在AI概覽時代，確保您的內容被正確爬取和理解變得比以往任何時候都更重要。

**爬蟲優化檢查清單**：
- [ ] robots.txt 正確配置
- [ ] XML 網站地圖更新且準確
- [ ] 爬蟲預算優化
- [ ] 孤立頁面消除
- [ ] 重複內容處理
- [ ] JavaScript 渲染優化

### 網站架構優化

**理想的網站結構**：

```
首頁
├── 主要類別1
│   ├── 子類別1.1
│   │   ├── 詳細頁面
│   │   └── 相關內容
│   └── 子類別1.2
├── 主要類別2
│   ├── 子類別2.1
│   └── 子類別2.2
└── 資源中心
    ├── 指南
    ├── 工具
    └── 術語表
```

**URL結構最佳實踐**：
```
好的範例：
https://example.com/seo/technical-seo/site-speed
https://example.com/guides/ai-overviews-optimization

避免：
https://example.com/p?id=12345
https://example.com/2024/03/20/post-title
```

## 結構化數據深度實施

### 進階架構實施

**1. 組織架構（完整版）**：
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "公司名稱",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "sameAs": [
    "https://facebook.com/company",
    "https://twitter.com/company",
    "https://linkedin.com/company/company"
  ],
  "contactPoint": [{
    "@type": "ContactPoint",
    "telephone": "+886-2-1234-5678",
    "contactType": "customer service",
    "areaServed": "TW",
    "availableLanguage": ["zh-TW", "en"]
  }],
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "街道地址",
    "addressLocality": "城市",
    "addressRegion": "地區",
    "postalCode": "郵遞區號",
    "addressCountry": "TW"
  }
}
```

**2. 網頁架構與麵包屑**：
```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "頁面標題",
  "description": "頁面描述",
  "breadcrumb": {
    "@type": "BreadcrumbList",
    "itemListElement": [{
      "@type": "ListItem",
      "position": 1,
      "name": "首頁",
      "item": "https://example.com"
    },{
      "@type": "ListItem",
      "position": 2,
      "name": "SEO",
      "item": "https://example.com/seo"
    },{
      "@type": "ListItem",
      "position": 3,
      "name": "技術SEO",
      "item": "https://example.com/seo/technical-seo"
    }]
  }
}
```

**3. 內容標記策略**：
```html
<!-- 文章with作者 -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://example.com/article"
  },
  "headline": "文章標題",
  "image": [
    "https://example.com/image-1x1.jpg",
    "https://example.com/image-4x3.jpg",
    "https://example.com/image-16x9.jpg"
  ],
  "datePublished": "2024-01-15T08:00:00+08:00",
  "dateModified": "2024-03-20T09:00:00+08:00",
  "author": {
    "@type": "Person",
    "name": "作者姓名",
    "url": "https://example.com/author/name"
  },
  "publisher": {
    "@type": "Organization",
    "name": "發布者名稱",
    "logo": {
      "@type": "ImageObject",
      "url": "https://example.com/logo.png"
    }
  },
  "description": "文章摘要"
}
</script>
```

### 動態架構生成

**JavaScript架構注入**：
```javascript
// 動態FAQ架構生成器
function generateFAQSchema(faqs) {
  const schema = {
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": faqs.map(faq => ({
      "@type": "Question",
      "name": faq.question,
      "acceptedAnswer": {
        "@type": "Answer",
        "text": faq.answer
      }
    }))
  };
  
  const script = document.createElement('script');
  script.type = 'application/ld+json';
  script.text = JSON.stringify(schema);
  document.head.appendChild(script);
}
```

## 核心網頁指標優化

### 最大內容繪製（LCP）優化

**優化策略**：

1. **圖片優化**
   ```html
   <!-- 響應式圖片with WebP -->
   <picture>
     <source srcset="image.webp" type="image/webp">
     <source srcset="image.jpg" type="image/jpeg">
     <img src="image.jpg" alt="描述" loading="lazy" 
          width="800" height="600">
   </picture>
   ```

2. **關鍵CSS內聯**
   ```html
   <style>
     /* 關鍵CSS內聯 */
     body { margin: 0; font-family: sans-serif; }
     .header { background: #fff; height: 60px; }
     /* ... */
   </style>
   <link rel="preload" href="style.css" as="style">
   <link rel="stylesheet" href="style.css">
   ```

3. **預連接關鍵資源**
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link rel="dns-prefetch" href="https://cdn.example.com">
   <link rel="preload" href="/font.woff2" as="font" crossorigin>
   ```

### 首次輸入延遲（FID）優化

**JavaScript優化技巧**：

```javascript
// 1. 代碼分割
import(/* webpackChunkName: "heavy-feature" */ './heavyFeature')
  .then(module => {
    module.init();
  });

// 2. 延遲非關鍵JavaScript
if ('requestIdleCallback' in window) {
  requestIdleCallback(() => {
    // 非關鍵初始化
  });
} else {
  setTimeout(() => {
    // 降級處理
  }, 1);
}

// 3. Web Workers用於繁重計算
const worker = new Worker('heavy-computation.js');
worker.postMessage({cmd: 'calculate', data: bigData});
```

### 累積佈局偏移（CLS）優化

**防止佈局偏移**：

```css
/* 1. 為圖片預留空間 */
.image-container {
  aspect-ratio: 16 / 9;
  background: #f0f0f0;
}

/* 2. 字體加載優化 */
@font-face {
  font-family: 'CustomFont';
  src: url('font.woff2') format('woff2');
  font-display: swap;
}

/* 3. 廣告和嵌入內容 */
.ad-container {
  min-height: 250px;
  background: #f5f5f5;
}
```

## 移動優化策略

### Progressive Web App (PWA) 實施

**Service Worker基礎**：
```javascript
// sw.js
const CACHE_NAME = 'v1';
const urlsToCache = [
  '/',
  '/styles/main.css',
  '/script/main.js'
];

self.addEventListener('install', event => {
  event.waitUntil(
    caches.open(CACHE_NAME)
      .then(cache => cache.addAll(urlsToCache))
  );
});

self.addEventListener('fetch', event => {
  event.respondWith(
    caches.match(event.request)
      .then(response => response || fetch(event.request))
  );
});
```

**Web App Manifest**：
```json
{
  "name": "AI時代SEO指南",
  "short_name": "SEO指南",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#000000",
  "background_color": "#ffffff",
  "icons": [
    {
      "src": "/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "/icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
```

### AMP替代方案

**現代移動優化方法**：

1. **Critical CSS**
   ```javascript
   // 提取關鍵CSS
   const critical = require('critical');
   
   critical.generate({
     inline: true,
     base: 'dist/',
     src: 'index.html',
     dest: 'index-critical.html',
     width: 375,
     height: 667
   });
   ```

2. **Resource Hints**
   ```html
   <!-- 預加載關鍵資源 -->
   <link rel="preload" as="script" href="critical.js">
   <link rel="preload" as="style" href="critical.css">
   
   <!-- 預取下一頁資源 -->
   <link rel="prefetch" href="/next-page.html">
   <link rel="dns-prefetch" href="//api.example.com">
   ```

## 國際化SEO

### Hreflang實施

**完整的hreflang設置**：
```html
<!-- HTML頭部 -->
<link rel="alternate" hreflang="zh-TW" href="https://example.com/tw/">
<link rel="alternate" hreflang="zh-CN" href="https://example.com/cn/">
<link rel="alternate" hreflang="en" href="https://example.com/en/">
<link rel="alternate" hreflang="x-default" href="https://example.com/">
```

**XML網站地圖中的hreflang**：
```xml
<url>
  <loc>https://example.com/tw/page</loc>
  <xhtml:link rel="alternate" hreflang="zh-CN" 
              href="https://example.com/cn/page"/>
  <xhtml:link rel="alternate" hreflang="en" 
              href="https://example.com/en/page"/>
  <xhtml:link rel="alternate" hreflang="zh-TW" 
              href="https://example.com/tw/page"/>
</url>
```

## 安全性優化

### HTTPS和安全頭部

**安全頭部配置**：
```nginx
# Nginx配置
add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-Content-Type-Options "nosniff" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline' https://www.google-analytics.com; style-src 'self' 'unsafe-inline';" always;
```

### 結構化的錯誤處理

**自定義錯誤頁面**：
```html
<!-- 404.html -->
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <title>找不到頁面 - 404</title>
  <meta name="robots" content="noindex, follow">
</head>
<body>
  <h1>找不到您要的頁面</h1>
  <p>建議您可以：</p>
  <ul>
    <li><a href="/">返回首頁</a></li>
    <li><a href="/search">使用搜尋功能</a></li>
    <li><a href="/sitemap">查看網站地圖</a></li>
  </ul>
  <script>
    // 追蹤404錯誤
    gtag('event', 'error', {
      'error_type': '404',
      'page_location': window.location.href
    });
  </script>
</body>
</html>
```

## 日誌文件分析

### 爬蟲行為分析

**日誌分析腳本**：
```python
import re
from collections import Counter
from datetime import datetime

def analyze_bot_behavior(log_file):
    bot_patterns = {
        'googlebot': r'Googlebot',
        'bingbot': r'bingbot',
        'baiduspider': r'Baiduspider'
    }
    
    bot_stats = {bot: Counter() for bot in bot_patterns}
    
    with open(log_file, 'r') as f:
        for line in f:
            for bot_name, pattern in bot_patterns.items():
                if re.search(pattern, line, re.I):
                    # 提取URL
                    url_match = re.search(r'"GET\s+(\S+)\s+HTTP', line)
                    if url_match:
                        url = url_match.group(1)
                        bot_stats[bot_name][url] += 1
    
    return bot_stats
```

## 性能監控設置

### Real User Monitoring (RUM)

**自定義RUM實施**：
```javascript
// 性能監控腳本
(function() {
  // 收集性能數據
  window.addEventListener('load', function() {
    setTimeout(function() {
      const perfData = performance.timing;
      const pageLoadTime = perfData.loadEventEnd - perfData.navigationStart;
      const dns = perfData.domainLookupEnd - perfData.domainLookupStart;
      const tcp = perfData.connectEnd - perfData.connectStart;
      const ttfb = perfData.responseStart - perfData.navigationStart;
      
      // 發送到分析服務
      if (typeof gtag !== 'undefined') {
        gtag('event', 'performance', {
          'page_load_time': pageLoadTime,
          'dns_time': dns,
          'tcp_time': tcp,
          'ttfb': ttfb,
          'page_path': window.location.pathname
        });
      }
    }, 0);
  });
  
  // Core Web Vitals
  if ('PerformanceObserver' in window) {
    // CLS
    let clsValue = 0;
    const clsObserver = new PerformanceObserver((list) => {
      for (const entry of list.getEntries()) {
        if (!entry.hadRecentInput) {
          clsValue += entry.value;
        }
      }
    });
    clsObserver.observe({type: 'layout-shift', buffered: true});
    
    // LCP
    const lcpObserver = new PerformanceObserver((list) => {
      const entries = list.getEntries();
      const lastEntry = entries[entries.length - 1];
      gtag('event', 'web_vitals', {
        'metric_name': 'LCP',
        'metric_value': lastEntry.renderTime || lastEntry.loadTime
      });
    });
    lcpObserver.observe({type: 'largest-contentful-paint', buffered: true});
  }
})();
```

## 自動化測試

### 技術SEO自動化測試套件

**Puppeteer測試腳本**：
```javascript
const puppeteer = require('puppeteer');

async function technicalSEOAudit(url) {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  
  const results = {
    url: url,
    timestamp: new Date().toISOString(),
    issues: []
  };
  
  try {
    await page.goto(url, {waitUntil: 'networkidle2'});
    
    // 檢查標題
    const title = await page.title();
    if (!title || title.length < 30 || title.length > 60) {
      results.issues.push({
        type: 'title',
        severity: 'high',
        message: `標題長度不理想: ${title.length}字符`
      });
    }
    
    // 檢查meta描述
    const metaDescription = await page.$eval(
      'meta[name="description"]',
      el => el.content
    ).catch(() => null);
    
    if (!metaDescription || metaDescription.length < 120 || metaDescription.length > 160) {
      results.issues.push({
        type: 'meta_description',
        severity: 'medium',
        message: '元描述長度不理想或缺失'
      });
    }
    
    // 檢查結構化數據
    const structuredData = await page.evaluate(() => {
      const scripts = Array.from(document.querySelectorAll('script[type="application/ld+json"]'));
      return scripts.map(s => {
        try {
          return JSON.parse(s.textContent);
        } catch(e) {
          return {error: e.message};
        }
      });
    });
    
    if (structuredData.length === 0) {
      results.issues.push({
        type: 'structured_data',
        severity: 'high',
        message: '未發現結構化數據'
      });
    }
    
    // 檢查頁面速度
    const metrics = await page.metrics();
    console.log('頁面指標:', metrics);
    
  } catch (error) {
    results.error = error.message;
  } finally {
    await browser.close();
  }
  
  return results;
}

// 批量測試
async function auditSitemap(sitemapUrl) {
  // 獲取並解析sitemap
  // 對每個URL運行審計
  // 生成報告
}
```

## 關鍵要點

1. **結構化數據是必須的** - 完整實施所有相關架構類型
2. **性能直接影響排名** - Core Web Vitals是排名因素
3. **移動優先不是選項** - 所有優化必須移動優先
4. **安全性影響信任** - HTTPS和安全頭部是基礎
5. **自動化確保一致性** - 建立自動化測試和監控

---

*下一章：[第六章 - 案例研究與實例](chapter-06-case-studies.md)*