---
created: 2025-05-01T22:46
updated: 2025-05-10T12:03
---


- [x] focus for 2 hours
- [x] focus for 1 hour and a half
- [x] focus for 1 hour
- [x] focus for 1 hour and a half
- css challenge? entertainment web app on sides/css-challenge - 
- 컴포넌트 쇼케이스 완성

- SEO 블로깅하기? 두시간
- 드래프트 완성


SSE with dashboard 

- 만드는 이유? 이전에 장고 어드민으로 어드민을쓰고 제대로 만들어보지 못했음. 

what to do

- need framework - nextjs template
- need design - find from frontend mentor - use nextAdmin
https://tailadmin.com/blog/stock-market-dashboard-templates

- need thirdparty api - 
https://www.alphavantage.co/support/#api-key
25 requests per day

https://finnhub.io/pricing
- 60 calls / minute


- need core logic - SSE vs websocket
https://www.marketcalls.in/python/sse-vs-websockets-choosing-the-right-tool-for-stock-market-applications.html#:~:text=Here's%20the%20bottom%20line%3A,technologies%20and%20is%20production%2Dready.

https://www.reddit.com/r/webdev/comments/1jwjom7/is_sse_a_fitting_alternative_to_websocket/

- 여기 따르면 sse는 모바일 밧데리를 사정없이 잡아먹는다고 함. duplex antenna?
- SSE는 작은 데이터를 간간히 하는데 적함. 더 자주할려고할때는 웹소켓이라고 함,.. sse는 메시지용으로 하라고

- does it need web worker?
https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications

- need place to deploy - use cloudflare, supabase
 - 웹소켓 혹은 SSE 서버 + nextjs서버여야 함.
https://github.com/vercel/next.js/discussions/14950#discussioncomment-4943465

버셀에 넥스트 올림 -> 웹소켓서버 클라우드플레어

- ci/cd? - consider railway
- chart? - candstick and else

# ✅ MVP Task List: Stock Dashboard

## 🔧 Backend & Real-Time Infrastructure
- [x] Set up real-time data ingestion pipeline
- [x] Implement market data provider integration (e.g., Finnhub, Alpha Vantage)
- [ ] Design efficient TimescaleDB schema for time-series stock data
- [x] Create WebSocket endpoints for live stock updates
- [ ] Implement rate limiting and data throttling
- [ ] Set up data validation and sanitization logic
- [ ] Secure WebSocket connections (WSS, origin checks)

## 🎨 Frontend (React/Next.js)
- [x] Create `useStockData` hook to manage WebSocket connection per symbol
- [x] Build `StockChart` component using TradingView or ECharts
- [x] Implement responsive chart layout (mobile & desktop)
- [ ] Create Watchlist interface with add/remove support
- [ ] Implement caching strategy (e.g., sessionStorage or Redux Toolkit Query)
- [x] Add error boundaries and loading fallbacks
- [x] Optimize component rendering for performance

## 🧩 UI/UX Design Considerations
- [ ] Design clear data hierarchy and visual structure
- [x] Add mobile-first layout and responsive design
- [ ] Implement skeleton loaders for initial loading state
- [ ] Design accessible color schemes and font hierarchy
- [ ] Build alert/notification UI for price triggers or system errors
- [ ] Add chart customization controls (time range, candle/line)

## ⚙️ DevOps Setup
- [ ] Create Docker Compose setup with `timescaledb`, `redis`, and `api` service
- [ ] Configure scalable WebSocket infrastructure (e.g., Nginx + ws)
- [ ] Set up CI/CD pipeline (e.g., GitHub Actions, Railway, or GitLab CI)
- [ ] Implement logging (ELK Stack) and performance monitoring (Prometheus + Grafana)
- [ ] Add auto-scaling and backup policies
- [ ] Enable alerts for service errors and performance thresholds

## 🔐 Cross-Cutting Concerns
- [x] Implement user authentication and session handling
- [ ] Add rate limiting on sensitive API and socket endpoints
- [ ] Encrypt sensitive data at rest and in transit
- [ ] Handle connection pooling and graceful fallback
- [ ] Set up centralized logging and alerting for production

## 🧱 Technical Stack Reference
- Backend: `Node.js` + `TypeScript` + `NestJS`
- DB: `TimescaleDB` (PostgreSQL extension), `Redis` for caching
- WebSockets: `ws` or `Socket.io`
- Frontend: `React`, `Next.js`, `TradingView`, `Tailwind CSS`, `Redux Toolkit`
- Infra: `Docker`, `Kubernetes`, `AWS/GCP`
- Monitoring: `Prometheus`, `Grafana`, `ELK Stack`

## 🚀 Phased Implementation
- [x] Phase 1: Basic Infrastructure Setup
- [x] Phase 2: Real-Time Data Ingestion Pipeline
- [x] Phase 3: Core Frontend Components
- [x] Phase 4: Real-time WebSocket Integration
- [ ] Phase 5: Watchlist & Chart Customization
- [ ] Phase 6: Performance & UX Optimization
- [ ] Phase 7: Production Monitoring & Maintenance
