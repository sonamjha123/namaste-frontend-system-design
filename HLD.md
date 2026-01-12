# High-Level Design (HLD

- [Things_Know_SystemDesign](#Things_Know_SystemDesign)
- [Overview](#Overview)
- [Instagram_PhotoSharingApp](#Instagram_PhotoSharingApp)
- [Database_Modules_Caching](#Database_Modules_Caching)
- 
## Things_Know_SystemDesign

#### Note : you will get better understanding by work but still learning things is better to understand the system when you get actual work.

**1) Take any course and follow the complete tutorial and then use any AI for case study in detail.
prompt that I used to learn**

#### For HLD:
- **Whenever I ask you any questions to design hld of any system, please tell me all the functional requirements you should have and then non-functional requirements.**
   - Assume we are having millions of users and we need to handle things at scale .
   - Tradeoff between consistency , availability for different usecase for the system..
   - What all microservices do we need and how they communicate with each other .
   - All the api end points which can be exposed to users.
   - Which db can be used and why ?
   - Tradeoff read heavy system for one service , one for write heavy and one service for balance .
   - How Partition, replication, sharing are applied and why?
   - Use caching wherever required .
   - Assume p95 latency should be low .
   - Care about failures, retry and backup strategy .
   - Add monitoring wherever applicable
   - How to Debug when something fails on prod.
   - Use all the fundamentals of hld like client, dns, cdn , load balancer (l4 / l7), app server , message queue , databases , cache (   redis).
   - Then what happens exactly when the client hits any request .

#### For LLD : 
- I will tell you to design any system in upcoming chat , for those system you need to first write story like how end to end things will happen and from there you find the entities here and explain why you choose that entity and then create a relationship between them using uml diagrams  and tell methods and data which you are using there or interfaces or composition etc and then tell which design pattern you are using between different classes and why so ?
- And also ensure most of the solid principle to follow and then give code in javascript ..

Note : you can read any blogs also , and can follow netflix , uber engineering blogs
----------------

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
| Profile management | Followers | Follow / Unfollow users |

---

### 2. Non-Functional Requirements - these are the requirements which does not directly connect but have impact on user experience.

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
### Architecture Design
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
    Server Side
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
```
### Component Architecture

#### Feed Listing
- **FeedList**
  - **Feed**
    - **PostBody**
    - **Caption**
    - **User Details**
    - **Reaction**
    - **Comment**

#### Feed / Post Creation
- **PostCreation**
  - **Upload**
  - **Editing**
  - **Filter**
  - **Caption**
  - **Tagging**
  - **Location**
  - **Image Component**
  - **Video Component**

### Data Model
## 2️⃣ Markdown + ASCII Diagram (Universal Support)

               +-------------+
               |  DataModel  |
               +-------------+
                      |
        ----------------------------------------------------------------
        |               |               |                           |
   
      Post           FeedList  User --> [id, name, profilephotoURL] Media --> [id, type(IMAGE/VIDEO), url]
        |               |
        |               v
        |          +---------+
                  |postId[], totalposts|
                   +---------+
   +----------------+
   |id, caption,createdAt, 
   |updatedAt, userId(who created
   post),mediaId[], caption 
   +----------------+

## API

### 1. Feed List API

#### Endpoint
```

GET /feedList?pageNo=1&pageSize=20

````

#### Request
- **Method:** GET
- **Query Params:**
  - `pageNo` — Page number
  - `pageSize` — Number of items per page

#### Response
```json
{
  "data": {
    "feeds": [],
    "totalPosts": 0,
    "currentPageNumber": 1,
    "currentPageSize": 20
  },
  "error": {}
}
````

---

### 2. Create Post APIs

Post creation can vary based on preferences and use cases.

#### Option 1: Single API

```
POST /createPost
```

* Handles post metadata + media upload together

#### Option 2: Separate APIs

```
POST /upload
POST /createPost
```

* `/upload` → handles media upload
* `/createPost` → creates post using uploaded media reference

---

### 3. Optimisation Strategies

#### 3.1 Asset Optimisation (Images)

1. Use modern image formats (e.g. **WebP**)
2. Implement `srcset` for responsive images
3. Serve assets based on `User-Agent`
4. Consider **DPR** (Device Pixel Ratio)
5. Adapt delivery based on device & network conditions
6. Prefetch images for upcoming content

---

#### 3.2 Feed Optimisation

1. **SSR** for above-the-fold (ATF) content
2. Lazy loading

   * Infinite scroll using **Intersection Observer**
3. Feed virtualization
4. Code splitting
5. Loading shimmer / skeleton UI
6. Preserve feed scroll position
7. Use **Web Workers** for heavy computations
8. Optimistic UI updates

---

### 4. Implementation Details

#### 4.1 Image Editing

* Crop / Resize → **Canvas API**
* Filters → **CSS filters**

---

#### 4.2 File Upload

* HTTP POST with `multipart/form-data`
* Alternative encoding: Base64 (use cautiously)
* Support multi-selection uploads
* File chunking
* Resumable uploads for reliability

---

### Notes

* Prefer separate upload and create APIs for scalability
* Optimise for slow networks and low-end devices
* Ensure backward compatibility for older browsers

### Database_Modules_Caching
## Local Storage vs Session Storage vs Cookies

| Feature            | Local Storage                         | Session Storage                     | Cookies                       |
| ------------------ | ------------------------------------- | ----------------------------------- | ----------------------------- |
| Storage Type       | Browser client-side storage           | Browser client-side storage         | Client–server storage         |
| Data Persistence   | Persists across browser sessions      | Cleared on tab/window close         | Session-based or expiry-based |
| Scope              | Shared across all tabs of same origin | Limited to single tab               | Sent with every HTTP request  |
| Size Limit         | ~5 MB per domain                      | ~5 MB per domain                    | ~4 KB per domain              |
| Performance        | Synchronous (can block main thread)   | Synchronous (can block main thread) | Affects request/response size |
| Data Structure     | Key–value (string only)               | Key–value (string only)             | Key–value (string only)       |
| Server Access      | ❌ Not sent to server                  | ❌ Not sent to server                | ✅ Sent automatically          |
| Security Risks     | Vulnerable to XSS                     | Vulnerable to XSS                   | Vulnerable to XSS & CSRF      |
| Security Controls  | Manual encryption                     | Manual encryption                   | HttpOnly, Secure, SameSite    |
| Expiration Control | Manual                                | Session-based                       | Expiry / Max-Age              |
| Offline Support    | ✅ Yes                                 | ✅ Yes                               | ❌ Limited                     |
| Typical Use Cases  | User preferences, UI state            | Temporary form data                 | Auth, sessions, tracking      |
| When Not to Use    | Sensitive data, tokens                | Large or long-term data             | Large or sensitive payloads   |

---

### Key Takeaway

Local and Session Storage are **frontend-focused**, while Cookies are **network-aware** and suitable for authentication—but must be used carefully.
#### Note: This endpoint logs the user out by instructing the browser to clear cached data, cookies, and client-side storage using the `Clear-Site-Data` header.
After cleanup, it redirects the user to the home page to ensure a clean session state.
```
app.get('/logout', (req, res) =>
{
res.setHeader('Clear-Site-Data', '"cache", "cookies", "storage"')
res.redirect('/');
})
```
Here’s an **optimized, clear, and complete Medium-ready version**. I’ve kept everything you mentioned, corrected phrasing, and added only **essential missing points** (like quota handling and browser support) without bloating it.

---

### IndexedDB (Use Only for Large Datasets)

**What is it?**
IndexedDB is a client-side database for persisting large amounts of structured data in the browser.

**How does it work?**
It is asynchronous and transactional, ensuring operations execute in the correct order. Core APIs include `indexedDB.open()`, `transaction()`, and `objectStore()`.

**Size limit**
Typically **100+ MB**, depending on browser and user permissions—suitable for large datasets (e.g., web chat history).

**Performance**
Asynchronous and non-blocking, designed to efficiently handle large volumes of data.

**Data persistence**
Data persists across browser sessions until explicitly cleared.

**Data structure**
Stores key–value pairs where values can be complex objects, including blobs, files, and images. Supports indexes for faster queries.

**Security considerations**
Data is accessible via JavaScript and vulnerable to XSS. Avoid sensitive data, encrypt when needed, enforce authentication checks, and always clear data on logout.

**When to use**
Large datasets, client-side caching, offline-first applications, and long data history.

**When not to use**
Highly sensitive or security-critical data—forgotten cleanup can become a risk.

**Additional notes**

* Available in **Web Workers**, enabling background data processing
* Supports multiple object stores and multiple entries
* Browser quota can vary and may require user approval
* Libraries like **Dexie.js** simplify usage
* Can be combined with notifications and background sync for advanced use cases

---

#### Key Takeaway

Use IndexedDB only when simpler storage options are insufficient—**it’s powerful, but complexity and security must be handled carefully**.
---------------------

### API Caching

API caching reduces unnecessary network calls by storing and reusing previously fetched responses.

### Popular Libraries

* **React Query** – Cache-first, background revalidation, retry support
* **SWR** – Stale-while-revalidate strategy
* **Axios** – Requires custom or interceptor-based caching
* **Apollo Client** – Built-in normalized caching for GraphQL

---

#### Common Caching Strategies

**Cache First**
Returns data from the cache if available; otherwise, fetches from the network and updates the cache.

**Network Only**
Always fetches data from the network. Cache may be written to, but it is never read.

**Cache and Network**
Returns cached data immediately (if available) and simultaneously fetches fresh data from the network. Updates cache and UI once the request completes.

**Network First (Cache Fallback)**
Fetches data from the network first. If the request fails, cached data is used as a fallback.

**No Cache**
Bypasses the cache entirely—does not read from or write to it. Every request goes to the network.

---

#### Important Notes

* **Network-only** may still write data to the cache depending on implementation
* **No-cache** does not interact with the cache at all
* Strategy choice depends on **latency tolerance, data freshness, and offline support**

---

#### Key Takeaway

Choosing the right API caching strategy is a balance between **performance, consistency, and user experience**.







