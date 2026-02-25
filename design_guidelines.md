# Hotel Operations Management System - Design Guidelines

## Design Approach

**Selected Approach:** Design System (Material Design) with modern dashboard patterns inspired by Linear, Notion, and enterprise SaaS tools

**Rationale:** This is a data-dense, utility-focused operations management system requiring efficiency, clarity, and professional aesthetics. Material Design's strong visual feedback and component library paired with modern dashboard patterns will ensure optimal usability for hotel staff across devices.

---

## Typography

**Font Families:**
- Primary: Inter (via Google Fonts) - clean, highly legible for data
- Monospace: JetBrains Mono - for codes, IDs, stock numbers

**Hierarchy:**
- Page Titles: text-3xl font-bold (30px)
- Section Headers: text-2xl font-semibold (24px)
- Card Titles: text-lg font-semibold (18px)
- Body Text: text-base font-normal (16px)
- Labels/Metadata: text-sm font-medium (14px)
- Helper Text: text-xs (12px)

---

## Layout System

**Spacing Primitives:** Use Tailwind units of 2, 4, 6, and 8 exclusively
- Tight spacing: p-2, gap-2
- Standard spacing: p-4, gap-4, m-4
- Section spacing: p-6, gap-6
- Major sections: p-8, gap-8

**Grid System:**
- Main content: max-w-7xl mx-auto
- Dashboard cards: grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6
- Forms: max-w-2xl single column for data entry efficiency
- Tables: Full width with horizontal scroll on mobile

---

## Core Layouts

### 1. Global Navigation
**Sidebar Navigation** (persistent, collapsible on mobile)
- Width: w-64 desktop, full-width mobile drawer
- Sections organized by: Dashboard, Departments, Articles, Operations (Prélèvements/Casse/Retours), Inventory, Reports, Settings
- Active state: Subtle background with left border accent
- Department submenu with icons for each outlet

### 2. Dashboard Layouts
**Global Dashboard:**
- Top: KPI cards in 4-column grid (stock status, alerts, monthly casse, consumption trends)
- Middle: Alert feed (urgent/warning/info states) with dismissible cards
- Bottom: Recent activity timeline and quick actions

**Department Dashboards:**
- Header with department selector dropdown
- 3-column metric cards (current stock value, casse rate %, prélèvements this month)
- Stock status table with visual indicators
- Consumption chart (bar/line chart showing trends)

### 3. QR Code Interface (Mobile/Tablet Optimized)
**Scanner View:**
- Full-screen camera viewport
- Floating scanner frame in center
- Bottom sheet with quick action buttons after scan
- Article details card slides up: image, name, current stock, department
- Quick action buttons: Prélèvement / Casse / Retour (large touch targets, min h-12)

---

## Component Library

### Navigation Components
**Sidebar:**
- Hierarchical menu with expand/collapse
- Icons from Heroicons (outline style)
- Badge indicators for alerts/notifications

**Breadcrumbs:**
- Text-sm with separator arrows
- Last item in regular weight, others subdued

### Data Display

**Stat Cards:**
- Rounded corners (rounded-lg)
- Shadow (shadow-sm)
- Padding p-6
- Value: text-3xl font-bold
- Label: text-sm
- Icon in top-right corner

**Tables:**
- Striped rows for readability
- Fixed header on scroll
- Action column (right-aligned) with icon buttons
- Responsive: cards on mobile, table on desktop
- Sort indicators in headers
- Pagination controls at bottom

**Alert Cards:**
- Border-left accent (4px) indicating severity
- Icon + title + description + timestamp
- Dismiss button (top-right)
- Stack vertically with gap-4

### Forms & Inputs

**Input Fields:**
- Height h-10 for text inputs
- Labels above inputs (text-sm font-medium mb-2)
- Placeholder text subdued
- Focus state with ring
- Error states with text-sm helper text below

**Select Dropdowns:**
- Height h-10
- Chevron icon right-aligned
- Search functionality for long lists (departments, articles)

**Buttons:**
- Primary: px-4 py-2 rounded-md font-medium
- Secondary: outline variant
- Icon buttons: p-2 rounded-md (square)
- Large touch targets for mobile: min-h-12 px-6

**Date Pickers:**
- Inline calendar with month/year navigation
- Today button for quick selection

### Article Cards
- Image thumbnail (aspect-square, rounded-lg)
- Title text-lg font-semibold
- Department badge below title
- Stock level with progress bar
- QR code icon button (top-right)
- Grid display: 2-3 columns on desktop, 1 on mobile

### Modal Dialogs
- Centered on screen
- Max-width max-w-2xl
- Header with title and close button
- Content area with scroll if needed
- Footer with action buttons (right-aligned)
- Backdrop overlay

---

## Specialized Interfaces

### Inventory Management Screen
- Department selector at top
- Split view: System Stock (left) | Physical Count (right)
- Écart column auto-calculated
- Adjustment input with justification textarea
- Submit inventory button (sticky bottom on mobile)

### Prélèvement/Casse/Retour Forms
**Quick Entry Mode:**
- Horizontal stepper: Select Department → Select Article → Enter Quantity → Add Reason
- Large, scannable article list with search
- Number pad for quantity entry on tablet
- Reason dropdown with "Other" free text option
- Submit button (prominent, full-width on mobile)

### Analytics Page
- Date range selector (top-right)
- Tabbed interface: Consumption / Casse / Trends
- Charts using Recharts library: bar charts for comparisons, line charts for trends
- Top 10 lists: Most Consumed / Most Broken articles with thumbnail images
- Export button (top-right)

---

## Responsive Behavior

**Mobile (< 768px):**
- Hamburger menu for navigation
- Single-column layouts
- Cards stack vertically
- Tables convert to stacked cards
- Touch-optimized buttons (min 44x44px)
- Bottom navigation for key actions

**Tablet (768px - 1024px):**
- 2-column grids for dashboards
- Side drawer navigation (swipeable)
- Optimized QR scanner interface
- Landscape mode for inventory entry (split-screen)

**Desktop (> 1024px):**
- Persistent sidebar navigation
- 3-4 column dashboard grids
- Data tables with advanced filtering
- Hover states for interactive elements

---

## Images

**No large hero images** - this is an operations management tool, not a marketing site.

**Article Images:**
- Product/item thumbnails throughout (96x96px on mobile, 128x128px on desktop)
- Placeholder image icon for items without photos
- Image upload interface in article management (drag-drop zone)

**Icons:**
- Heroicons library (CDN) throughout
- Department icons in navigation
- Status indicators (alert-triangle, check-circle, info)
- Action icons (trash, edit, eye, qr-code)

---

## Animation Guidelines

**Minimal, purposeful animations only:**
- Sidebar slide transition (300ms ease)
- Modal fade in/out (200ms)
- Alert dismiss slide (250ms)
- No hover animations on data tables
- No scroll-triggered animations
- Loading spinners for async operations only

---

This design ensures a professional, efficient interface optimized for rapid data entry, clear information hierarchy, and seamless operation across hotel departments and devices.