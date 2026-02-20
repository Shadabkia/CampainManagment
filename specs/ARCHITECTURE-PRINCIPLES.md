# Architecture Principles

**Project:** Iran People's Party Election Campaign Management Web Application  
**Version:** 1.1  
**Document Purpose:** Defines the architectural principles and technical constraints that guide design and implementation decisions across the platform.

---

## 1. Technology Stack

| Layer | Technology | Rationale |
|-------|------------|-----------|
| Frontend | React.js + Tailwind CSS | Component-based UI with utility-first responsive design |
| Backend | Nest.js | Modular, TypeScript-native framework with strong API and WebSocket support |
| Authentication | JWT + OTP | Stateless auth with mobile/email verification |
| Real-time | WebSocket | Messaging, notifications, live updates |
| Database | PostgreSQL or MySQL | Relational data with ACID guarantees |
| Cache | Redis | Session, rate limiting, real-time data |
| File Storage | Local or S3 | Scalable media and document storage |

---

## 2. Responsive & Accessibility

- **Mobile-first:** All layouts and interactions are designed for mobile first, then enhanced for tablet and desktop.
- **Mobile suitability:** The app must behave as a native-like experience on mobile devices, including proper handling of the device back button (Android hardware back, in-app navigation history) so users can navigate back through app routes without unexpected exits or broken flows.
- **Tailwind breakpoints:** Support for 320px through 4K viewports.
- **Touch-friendly:** Touch targets and gestures suitable for mobile users.
- **Low-bandwidth:** Performance optimizations for constrained networks.
- **PWA-ready:** Offline-capable design and service worker support.

---

## 3. Authentication & Authorization

- **Invitation-only registration:** New users require a referral code or invitation link.
- **Multi-channel verification:** Mobile number and email OTP verification.
- **Flexible login:** OTP-based and password-based login, plus "Forgot Password" flow.
- **JWT with refresh tokens:** Stateless, secure sessions with token rotation.
- **RBAC:** Role-based access control (admin, section manager, user) enforced across APIs and UI.

---

## 4. API & Communication

- **RESTful APIs:** Standard HTTP verbs, clear resource naming, predictable URL structure.
- **WebSocket for real-time:** Used for messaging, notifications, and live updates.
- **Structured contracts:** APIs define clear request/response shapes and error formats.

---

## 5. Security

- **Encryption:** Data encrypted at rest and in transit (TLS).
- **Input validation:** All inputs validated and sanitized before processing.
- **Rate limiting:** Protection against abuse and DoS.
- **Secure file uploads:** Validation of types, size, and content.
- **Session management:** Secure, expiry-based session handling.
- **Compliance:** GDPR and relevant data-protection considerations.

---

## 6. Performance & Reliability

| Metric | Target | Scope |
|--------|--------|--------|
| Page load time | < 3 seconds | First meaningful paint |
| Real-time notification delay | < 2 seconds | From event to client |
| Uptime | 99.9% | Production availability |

- **Concurrent user scaling:** Architecture supports horizontal scaling.
- **Caching:** Redis for frequent reads and session data.
- **Analytics and logging:** Centralized logging for monitoring and debugging.

---

## 7. Data & Integration

- **Geolocation:** Used for location-based tasks and attendance verification.
- **Email & SMS:** External services for OTP and notifications.
- **File handling:** Upload, storage, and retrieval for documents and media.

---

## 8. Phased Delivery

- **Phase 1 (Core):** Authentication, profiles, communication center, task management, dashboard, admin panel.
- **Phase 2 (Enhanced):** Financial contributions, referrals, gamification, video center, document management, working groups.
- **Phase 3 (Advanced):** Messaging, discussion groups, online meetings, project-based crowdfunding.

Architecture and infrastructure decisions must support all phases without breaking prior functionality.

---

## 9. Modularity & Extensibility

- **Section-based structure:** Admin panel and task flows organized by sections and managers.
- **Task type extensibility:** New task types can be added with clear workflows (opinion, research, event, referral, etc.).
- **Working groups:** Support for group creation, hierarchies, and sub-groups.

---

## 10. Spec-Driven Development

- The `specs/` folder is the **source of truth** for behavior, contracts, and intent.
- Architecture and implementation must align with specs; changes to behavior require spec updates.
- Specs describe *what* and *why*; implementation details live in code and architecture docs.

---

*This document should be updated whenever architectural principles or technical constraints change.*
