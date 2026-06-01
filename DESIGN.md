# Kocumo Dashboard — DESIGN.md v2.0
# Google Stitch format — AI Agent Design System
# Panel: panel.kocumo.com — Paperclip Multi-Agent Monitoring Dashboard

---

## 1. Visual Theme & Atmosphere

**Atmosphere:** Karanlık, premium, teknoloji odaklı. Bir uzay gemisi kontrol paneli gibi — veri yoğun ama nefes alan, ciddi ama davetkar.

**Brand:** Aurain Tech / Kocumo. Yapay zeka orkestrasyon platformu.

**Mood keywords:** güvenilir, keskin, modern, profesyonel, hızlı

---

## 2. Color System & Tokens

### Dark Theme (Primary)

| Token | Hex | CSS Var | Usage |
|-------|-----|---------|-------|
| `bg-primary` | `#0a0e17` | `--bg-primary` | Ana arka plan |
| `bg-secondary` | `#111827` | `--bg-secondary` | Kartlar, sidebar |
| `bg-tertiary` | `#1a2332` | `--bg-tertiary` | Hover, aktif öğeler |
| `bg-elevated` | `#1e293b` | `--bg-elevated` | Modal, dropdown |
| `text-primary` | `#f1f5f9` | `--text-primary` | Başlıklar, ana metin |
| `text-secondary` | `#94a3b8` | `--text-secondary` | Alt metin, etiketler |
| `text-muted` | `#64748b` | `--text-muted` | Pasif bilgiler |
| `accent-blue` | `#3b82f6` | `--accent-blue` | Primary CTA, aktif öğe |
| `accent-green` | `#10b981` | `--accent-green` | Başarı, aktif, up |
| `accent-red` | `#ef4444` | `--accent-red` | Hata, down, kritik |
| `accent-amber` | `#f59e0b` | `--accent-amber` | Uyarı, pending |
| `accent-purple` | `#8b5cf6` | `--accent-purple` | AI/agent vurgusu |
| `border` | `#1e293b` | `--border` | Kart/section kenarları |
| `border-light` | `#334155` | `--border-light` | Input kenarları |

**Contrast Ratios (WCAG AA):**
- text-primary on bg-primary: 14.2:1 ✅
- text-secondary on bg-primary: 7.1:1 ✅
- accent-blue on bg-primary: 4.5:1 ✅ (large text)

---

## 3. Typography System

| Level | Font | Size | Weight | Line Height | Usage |
|-------|------|------|--------|-------------|-------|
| H1 | Inter | 28px | 700 | 1.2 | Sayfa başlığı |
| H2 | Inter | 20px | 600 | 1.3 | Kart başlıkları |
| H3 | Inter | 16px | 600 | 1.4 | Section başlıkları |
| Body | Inter | 14px | 400 | 1.5 | Ana metin |
| Body-S | Inter | 13px | 400 | 1.5 | Alt metin |
| Mono | JetBrains Mono | 13px | 400 | 1.6 | Kod, log, değerler |
| Stat | Inter | 32px | 700 | 1.1 | Büyük sayılar (KPI) |

**Font stack:** `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
**Mono stack:** `'JetBrains Mono', 'Fira Code', 'Cascadia Code', monospace`

---

## 4. Component Catalog

### 4.1 Sidebar (sol, fixed, 240px)
- Logo + başlık (KOCUMO)
- Nav itemlar: ikon + etiket + active indicator
- Alt kısım: durum göstergesi + saat
- border-right: 1px solid var(--border)

### 4.2 Stat Card (KPI kartları)
- Arka plan: bg-secondary, border-radius: 12px
- Üst: etiket (text-muted, 13px)
- Orta: büyük sayı (32px, 700, accent-blue)
- Alt: değişim yüzdesi (accent-green/red + oklar)

### 4.3 Data Table (Konteyner/Skills)
- Zebra striping (bg-secondary / bg-tertiary)
- Header: bg-tertiary, text-muted, 12px uppercase
- Row hover: bg-tertiary
- border-radius: 12px, overflow

### 4.4 Status Badge
- Çap: 8px + text
- active → accent-green, idle → accent-amber, error → accent-red

### 4.5 Tab Navigation (üst)
- Yatay sekmeler, alt çizgi aktif göstergesi (accent-blue, 2px)
- İnaktif: text-muted, hover: text-secondary

### 4.6 Bar Chart (CSS-only)
- Yatay bar: bg-tertiary arka plan, accent-blue dolgu
- Label solda, bar sağda
- Animasyonlu genişleme (width transition 600ms ease-out)

### 4.7 Log Box
- bg-secondary, mono font
- Renkli satır başları: [INFO] text-secondary, [WARN] accent-amber, [ERROR] accent-red
- max-height: 300px, overflow-y: auto

### 4.8 Progress Bar
- bg-tertiary track, accent-blue fill
- height: 6px, border-radius: 3px

### 4.9 Refresh Button (header sağ üst)
- ikon + "Yenile" text
- hover: bg-tertiary, active: scale(0.97)

---

## 5. Component State Matrix

| Component | Default | Hover | Active | Disabled | Loading | Error | Focus |
|-----------|---------|-------|--------|----------|---------|-------|-------|
| Nav Item | text-secondary | bg-tertiary, text-primary | accent-blue indicator | opacity: 0.4 | N/A | N/A | ring-2 accent-blue |
| Stat Card | default | translateY(-2px), shadow | N/A | N/A | shimmer animasyonu | N/A | N/A |
| Button | bg-accent, text-white | brightness(1.1) | scale(0.97) | opacity: 0.4 | spinner | bg-accent-red | ring-2 |
| Badge | renkli dot | N/A | N/A | N/A | pulse animasyonu | N/A | N/A |
| Tab | text-muted | text-secondary | text-primary, alt-çizgi | opacity: 0.4 | N/A | N/A | ring-2 |
| Table Row | default | bg-tertiary | N/A | N/A | N/A | border-accent-red | N/A |

---

## 6. Layout & Spacing System

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | 4px | İkon-padding, dot-boşluk |
| `--space-sm` | 8px | İç boşluklar |
| `--space-md` | 16px | Kart padding, eleman arası |
| `--space-lg` | 24px | Section arası |
| `--space-xl` | 32px | Büyük bölüm arası |
| `--space-2xl` | 48px | Sayfa kenar boşluğu |
| `--sidebar-w` | 240px | Sidebar genişliği |
| `--content-max` | 1200px | İçerik max genişlik |
| `--radius-sm` | 6px | Buton, badge |
| `--radius-md` | 12px | Kart, tablo, input |
| `--radius-lg` | 16px | Modal |

---

## 7. Depth & Elevation

| Level | Shadow | Z-Index | Usage |
|-------|--------|---------|-------|
| 0 | none | 0 | Ana içerik |
| 1 | `0 1px 3px rgba(0,0,0,0.4)` | 10 | Kartlar |
| 2 | `0 4px 12px rgba(0,0,0,0.5)` | 20 | Dropdown |
| 3 | `0 8px 24px rgba(0,0,0,0.6)` | 30 | Modal |
| 4 | `0 16px 48px rgba(0,0,0,0.7)` | 40 | Tooltip |
| Sidebar | none | 100 | Fixed sidebar |

---

## 8. Motion & Animation System

| Animation | Duration | Easing | Usage |
|-----------|----------|--------|-------|
| Fade in | 200ms | ease-out | Kart, section görünme |
| Slide in (sidebar) | 250ms | ease-out | Sayfa yüklenme |
| Hover lift | 200ms | ease-out | Kart hover |
| Bar grow | 600ms | ease-out | Chart bar animasyonu |
| Status pulse | 2s infinite | ease-in-out | Canlı durum noktası |
| Tab switch | 150ms | ease-out | Tab geçişleri |
| Spinner | 1s infinite | linear | Loading |

**prefers-reduced-motion:** tüm animasyon süreleri 0ms, sadece opacity geçişleri

---

## 9. Icon System

| Size | Stroke | Usage |
|------|--------|-------|
| 16px | 2 | Badge içi, inline |
| 20px | 2 | Nav item, buton |
| 24px | 1.5 | Header, büyük buton |

**Library:** SVG inline (harici kütüphane yok, diskten tasarruf)

**Icon set (minimal):**
- Dashboard (overview), Server (konteyner), Puzzle (skills), Network (network), FileText (logs)
- RefreshCw, Clock, ArrowUp, ArrowDown, AlertCircle, CheckCircle, XCircle

---

## 10. Accessibility Contract

| Rule | Standard | Implementation |
|------|----------|----------------|
| Color contrast | WCAG AA | Tüm metinler ≥ 4.5:1 |
| Focus visible | WCAG 2.4.7 | :focus-visible ring-2 accent-blue |
| Keyboard nav | Full | Tab, Enter, Escape — tüm etkileşimler |
| ARIA labels | Required | Nav items, buttons, status indicators |
| Screen reader | NVDA/JAWS | aria-live polite for status changes |
| Reduced motion | prefers-reduced-motion | Tüm animasyonlar disable |
| Touch targets | ≥ 44px | Mobil nav itemlar |

---

## 11. Do's and Don'ts

✅ **DO:**
- Kartlarda bg-secondary kullan, border ekle
- Sayıları mono font ile göster
- Durum değişikliklerini renk + ikon ile ilet
- Boşluk bırak, nefes alan tasarım
- Tek sayfa, scroll — sekme yoksa bile akıcı

❌ **DON'T:**
- 3'ten fazla renk aynı anda vurgu için kullanma
- Kart gölgelerini abartma (max 12px blur)
- Uzun tablolarda scroll bırakmayı unutma
- Metin kontrastı 4.5:1 altına düşürme
- JS framework ekleme (pure vanilla)

---

## 12. Responsive Behavior

| Breakpoint | Width | Behavior |
|------------|-------|----------|
| Desktop | ≥ 1024px | Tam sidebar + içerik |
| Tablet | 768-1023px | Sidebar collapsed (ikon-only, 64px) |
| Mobile | < 768px | Sidebar hidden, hamburger menü, stack |

---

## 13. Page Structure (Panel Layout)

```
┌────────────────────────────────────────────────────┐
│ ┌──────────┐  ┌──────────────────────────────────┐ │
│ │ SIDEBAR  │  │  HEADER        [refresh] [clock] │ │
│ │          │  ├──────────────────────────────────┤ │
│ │ KOCUMO   │  │  ┌──────┐ ┌──────┐ ┌──────┐     │ │
│ │          │  │  │STAT 1│ │STAT 2│ │STAT 3│     │ │
│ │ ● Overview│  │  └──────┘ └──────┘ └──────┘     │ │
│ │ ● Container│ │                                  │ │
│ │ ● Skills  │  │  [TABS: Overview|Cont|Skills..] │ │
│ │ ● Network │  │  ┌──────────────────────────┐   │ │
│ │ ● Logs    │  │  │     TAB CONTENT          │   │ │
│ │          │  │  │  (chart / table / list)   │   │ │
│ │ ⚫ Active │  │  └──────────────────────────┘   │ │
│ │ 12:34    │  │                                  │ │
│ └──────────┘  └──────────────────────────────────┘ │
└────────────────────────────────────────────────────┘
```

---

## 14. Code Snippets (CSS Custom Properties)

```css
:root {
  /* Colors */
  --bg-primary: #0a0e17;
  --bg-secondary: #111827;
  --bg-tertiary: #1a2332;
  --bg-elevated: #1e293b;
  --text-primary: #f1f5f9;
  --text-secondary: #94a3b8;
  --text-muted: #64748b;
  --accent-blue: #3b82f6;
  --accent-green: #10b981;
  --accent-red: #ef4444;
  --accent-amber: #f59e0b;
  --accent-purple: #8b5cf6;
  --border: #1e293b;
  --border-light: #334155;
  
  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;
  --sidebar-w: 240px;
  --radius-md: 12px;
  
  /* Typography */
  --font-sans: 'Inter', -apple-system, sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
}

/* Card pattern */
.card {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: var(--space-lg);
  transition: transform 200ms ease-out;
}
.card:hover {
  transform: translateY(-2px);
}

/* Stat number pattern */
.stat-number {
  font-family: var(--font-mono);
  font-size: 32px;
  font-weight: 700;
  color: var(--accent-blue);
}

/* Nav item pattern */
.nav-item {
  color: var(--text-secondary);
  border-radius: 8px;
  transition: all 150ms;
}
.nav-item:hover { background: var(--bg-tertiary); color: var(--text-primary); }
.nav-item.active { color: var(--text-primary); border-left: 3px solid var(--accent-blue); }

/* Bar chart pattern */
.bar-fill {
  background: var(--accent-blue);
  height: 100%;
  border-radius: 3px;
  transition: width 600ms ease-out;
}
```
