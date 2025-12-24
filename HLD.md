# High-Level Design (HLD

- [Overview](#Overview)
- [Instagram_PhotoSharingApp](#Instagram_PhotoSharingApp)
- 

## Overview
## What is HLD?
High-Level Design (HLD) is a phase in the **Software Development Life Cycle (SDLC)** where the **overall architecture and structure** of a software system are planned and documented.

### Purpose
- Bridges **Requirement Specification** and **Actual Implementation**
- Acts as a **blueprint** for how the system will function
- Defines how different components interact and integrate

---

## Stakeholders Involved
- Client
- Architect
- Designer
- Project Manager
- Stakeholders
- Designers

---

## Key Aspects of HLD
- Requirement Analysis
- System Architecture
- Module / Component Design
- Data Design
- Interfaces & API Schema
- Technology / Tech Choices  

📺 Reference:  
**Cracking Frontend System Design Interview (Episode 2)**  
https://www.youtube.com/playlist?list=PL4CFloQ4GGWICE0Tz6iXKfN3XWkXRlboU

---

## Client Requirements

### Functional vs Non-Functional Requirements (Tabular)

| Category | Functional Requirements | Non-Functional Requirements |
|-------|------------------------|-----------------------------|
| Core | Demand / Supply | Device support (Mobile / Desktop) |
| Modules | User Management | Responsive / Adaptive UI |
|  | Help & Support | Network / Location / Device compatibility |
|  | Payment Gateway | Accessibility (WCAG) |
|  | Pricing & Subscription | Asset Optimization (CSS, JS, Images) |
|  | Product Listing | Performance (FCP, LCP, TTI, Web Vitals) |
|  | Cart Page | CSR / SSR |
|  | Account Management | Authentication & Authorization |
| Features | Business workflows | Security |
|  |  | Caching |
|  |  | Offline Support |
|  |  | Logging & Monitoring |
|  |  | A/B Testing |
|  |  | Testing (Unit / Integration / E2E) |
|  |  | Internationalization & Localization |
|  |  | Versioning |
|  |  | PWA |
|  |  | CI / CD |

---

## Requirement Thinking Levels

### 1. Module-Level Thinking
- User Management
- Help & Support
- Payment Gateway
- Pricing & Subscription
- Product Listing
- Cart Page
- Account Management

### 2. Feature-Level Thinking
- Search
- Listing
- Product Details
- Reviews
- Add to Cart / Wishlist
- Cart List
- Price Breakups
- Add / Remove Products

---

## Scoping & Prioritization

### Functional Scope

| Level | Items |
|-----|------|
| Demand | Core business demand |
| Modules | Product Listing, Cart Page |
| Features | Search, Listing, Product Details, Reviews |
|  | Add to Cart / Wishlist |
|  | Cart List |
|  | Price Breakups |
|  | Add / Remove Products |

---

### Non-Functional Scope

| Category | Considerations |
|-------|---------------|
| Platform | Desktop |
| UI | Responsive |
| Accessibility | Keyboard, Screen readers |
| Performance | FCP, LCP, TTI |
| Rendering | CSR / SSR |
| Optimization | Asset Optimization |
| Caching | Browser / CDN |

---

## Technology Choices

### Frontend Tech Stack
- Library / Framework (React, Vue, Angular)
- State Management (Redux, Zustand, Context API)
- Folder Structure
- Packages & Dependencies
- Specialized APIs
  - Canvas / SVG
  - WebRTC
- Design Systems
- Build Tools
  - Webpack
  - Rollup
  - Parcel

---

## Component Architecture

- Component Hierarchy
- Routing Strategy
- Data Sharing (Props, Context, Store)

---

## Data API & Protocols
### Protocols
- REST
- GraphQL
- SSE
- RPC
### Implementation Details
- Pagination
- Infinite Scrolling
- Debouncing
- Throttling
---
## APIs
```ts
getProductList()
getProductDetails()
```
#### Key Takeaways (Interview Perspective)
- Straightforward problems → Junior-level
- Open-ended problems → Senior-level
- Topic does NOT define interviewer intent
- Never assume requirements — ask clarifying questions
- Drive the interview based on interviewer intent
- System Design ≠ Coding or drawing boxes
- Focus on trade-offs, reasoning, and decisions

## Instagram_PhotoSharingApp
**Reference: https://www.geeksforgeeks.org/system-design/design-instagram-a-system-design-interview-question/**
### 1. Functional Requirements

| Module | Sub-Module | Features |
|------|----------|---------|
| Feed Management | Feed List | View posts in chronological / algorithmic order |
|  | Create Post | Upload / Edit Photos |
|  |  | Apply Filters |
| Reels | Reels List | View short videos |
|  | Create Reels | Upload / Edit Reels |
| Stories | Stories List | View stories |
|  | Create Stories | Upload / Edit Stories |
| Engagement | Likes | Like posts / reels |
|  | Comments | Comment on posts / reels |
| Browse | Discovery | Explore trending content |
| Messaging | Direct Messages | One-to-one & group chat |
| Account Management | User Account | Settings, privacy |
| Profile | Followers | Follow / Unfollow users |

---

### 2. Non-Functional Requirements

| Category | Requirement Description |
|-------|-------------------------|
| Security | Secure APIs, data encryption |
| Device Support | Mobile, Tablet, Desktop |
| Authentication | Login, Signup, Session handling |
| SEO | Public profile discoverability on search engines |
| Accessibility | WCAG compliance |
| Offline Support | Cached feed viewing |
| Testing | Unit, Integration, E2E |
| Internationalization (i18n) | Multi-language support |
| Localization (l10n) | Region-specific formats |
| Deployment | CI/CD, Cloud hosting |

---
```

flowchart LR
    %% Client Side
    subgraph Client
        Storage[Storage\nRedux / Apollo Cache /\nLocalStorage / IndexedDB]
        View[View Layer\nListing & Creation]
        Controller[Controller\nFilters, Editing,\nUploads, Post Processing,\nPost Creation Flow]
        Services[Client Services\nUpload, Post Creation,\nPost List]

        View --> Controller
        Controller --> Services
        Services --> Storage
        Storage --> View
    end

    %% Server Side
    subgraph Server
        APIGW[API Gateway]
        Auth[Auth Service]
        Upload[Upload Service]
        PostCreate[Post Creation Service]
        PostList[Post Listing Service]
        DB[(Database)]

        APIGW --> Auth
        APIGW --> Upload
        APIGW --> PostCreate
        APIGW --> PostList

        Auth --> DB
        Upload --> DB
        PostCreate --> DB
        PostList --> DB
    end

    %% Client to Server
    Services --> APIGW

Just say the word 🚀

