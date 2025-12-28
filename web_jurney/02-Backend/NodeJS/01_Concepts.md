```dataviewjs
const tasks = dv.current().file.tasks;
const total = tasks.length;
const done = tasks.where(t => t.completed).length;
const progress = total > 0 ? Math.round((done / total) * 100) : 0;

dv.paragraph(`**Node.js Progress • ${done}/${total} (${progress}%)**`);

const barHtml = `
<div style="
  background: #f0f0f0;
  height: 24px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: inset 0 1px 3px rgba(0,0,0,0.1);
  margin: 10px 0;">
  <div style="
    height: 100%;
    width: ${progress}%;
    background: linear-gradient(to right, #38bdf8, #22c55e);
    border-radius: 12px;
    box-shadow: 0 0 10px rgba(56, 189, 248, 0.5);
    transition: width 0.6s ease;">
  </div>
</div>`;

dv.el("div", barHtml);
```
---
## 1️⃣ Introduction to Node.js
- [ ] What is Node.js
- [ ] Node.js vs Browser JS
- [ ] How Node.js works (V8 + libuv)
- [ ] Use cases of Node.js
- [ ] Node.js architecture
- [ ] Event-driven programming

## 2️⃣ Environment & Setup
- [ ] Install Node.js
- [ ] Node version management (nvm)
- [ ] npm vs yarn vs pnpm
- [ ] Initialize project (npm init)
- [ ] package.json explained
- [ ] node_modules explained
- [ ] .gitignore for Node

## 3️⃣ Running Node Programs
- [ ] node file.js
- [ ] REPL mode
- [ ] Debugging Node apps
- [ ] nodemon
- [ ] Environment variables
- [ ] process object

## 4️⃣ Modules in Node
- [ ] CommonJS (require, module.exports)
- [ ] ES Modules in Node
- [ ] Import vs require
- [ ] Built-in modules
- [ ] Creating custom modules
- [ ] Module caching

## 5️⃣ Core Node APIs
- [ ] fs (file system)
- [ ] path
- [ ] os
- [ ] url
- [ ] crypto
- [ ] events
- [ ] stream
- [ ] buffer

## 6️⃣ Async in Node
- [ ] Callback-based APIs
- [ ] Promisified APIs
- [ ] util.promisify()
- [ ] async/await in Node
- [ ] Error handling async code
- [ ] Unhandled promise rejections

## 7️⃣ Event Loop & Concurrency
- [ ] Event loop phases
- [ ] Microtasks vs macrotasks
- [ ] Timers
- [ ] Thread pool (libuv)
- [ ] Blocking vs non-blocking code

## 8️⃣ HTTP & Networking
- [ ] http module
- [ ] Create HTTP server
- [ ] Handle requests & responses
- [ ] Routing manually
- [ ] Serving static files
- [ ] REST API basics

## 9️⃣ Express.js
- [ ] What is Express
- [ ] Create Express server
- [ ] Routing
- [ ] Middleware concept
- [ ] Built-in middleware
- [ ] Custom middleware
- [ ] Error middleware
- [ ] Request lifecycle

## 🔟 RESTful APIs
- [ ] REST principles
- [ ] CRUD operations
- [ ] Status codes
- [ ] Request headers & body
- [ ] Pagination
- [ ] Filtering & sorting

## 1️⃣1️⃣ Validation & Security
- [ ] Input validation
- [ ] express-validator / zod
- [ ] CORS
- [ ] Helmet
- [ ] Rate limiting
- [ ] Preventing XSS & CSRF

## 1️⃣2️⃣ Authentication & Authorization
- [ ] Authentication vs authorization
- [ ] JWT
- [ ] Cookies vs tokens
- [ ] Password hashing (bcrypt)
- [ ] Refresh tokens
- [ ] Role-based access

## 1️⃣3️⃣ Databases
- [ ] SQL vs NoSQL
- [ ] MongoDB basics
- [ ] Mongoose
- [ ] PostgreSQL / MySQL
- [ ] Prisma / Sequelize
- [ ] Migrations

## 1️⃣4️⃣ File Uploads & Storage
- [ ] Multipart/form-data
- [ ] Multer
- [ ] Image uploads
- [ ] Cloud storage (S3, Cloudinary)

## 1️⃣5️⃣ Testing
- [ ] Unit vs integration testing
- [ ] Jest
- [ ] Supertest
- [ ] Mocking
- [ ] Coverage reports

## 1️⃣6️⃣ Logging & Monitoring
- [ ] console vs logging libraries
- [ ] Winston / Pino
- [ ] Log levels
- [ ] Error tracking (Sentry)

## 1️⃣7️⃣ Performance & Optimization
- [ ] Caching (Redis)
- [ ] Compression
- [ ] Clustering
- [ ] Load balancing
- [ ] Memory leaks

## 1️⃣8️⃣ Deployment
- [ ] Build vs runtime
- [ ] Environment configs
- [ ] PM2
- [ ] Docker basics
- [ ] Deploy to VPS / cloud
- [ ] CI/CD basics

## 1️⃣9️⃣ Advanced Topics
- [ ] Worker threads
- [ ] Streams in depth
- [ ] Message queues (RabbitMQ, Kafka)
- [ ] GraphQL
- [ ] WebSockets

## 2️⃣0️⃣ Real Projects
- [ ] REST API project
- [ ] Auth system
- [ ] File upload service
- [ ] Chat app
- [ ] Payment integration
- [ ] Microservices dem