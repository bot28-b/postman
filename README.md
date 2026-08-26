# QA Learning API — Postman Tutorial

Learn **API testing with Postman**. No local setup — push to GitHub and share the URLs.

## Live URLs (after push to GitHub)

| Resource | URL |
|----------|-----|
| **Documentation** | https://bot28-b.github.io/postman/ |
| **CRUD API** | https://my-json-server.typicode.com/bot28-b/postman |
| **Health check** | https://bot28-b.github.io/postman/health.json |

## One-time setup (repo owner)

1. Push this repo to GitHub (**public** repo required for free CRUD API)
2. **Settings → Pages → Source:** GitHub Actions
3. Push to `main` — docs deploy automatically

## For learners (Postman)

1. **Import** → download from [postman/](postman/) folder:
   - `QA-Learning-API.postman_collection.json`
   - `QA-Learning-API.postman_environment.json`
2. Select **QA Learning API - Live (GitHub)** environment
3. Run **Health Check (GitHub Pages)** → 200 OK
4. Run **Get All Users** → JSON array returned

That's it. No npm, no local server.

## How it works

| Part | Host | Purpose |
|------|------|---------|
| `docs/` | **GitHub Pages** | Tutorial site + health.json |
| `db.json` | **my-json-server** | Live CRUD API (reads from your GitHub repo) |
| httpbin.org | Public service | Headers, auth, status codes, delay (in collection) |

The CRUD API at `my-json-server.typicode.com/bot28-b/postman` automatically serves data from `db.json` in this repo. After you push changes, wait 1–2 minutes for sync.

## Postman collection covers

1. **GET** — list, by ID, 404
2. **POST** — create user, JSON body echo
3. **PUT & PATCH** — full and partial updates
4. **DELETE** — remove user
5. **Query params** — filter, sort, pagination
6. **Headers** — custom header echo
7. **Authentication** — Bearer token valid / 401
8. **Status codes** — 200, 201, 400, 404, 500
9. **Performance** — response time with delay

## API endpoints

**Base URL:** `https://my-json-server.typicode.com/bot28-b/postman`

```
GET    /users                      List users
GET    /users/1                    Get user
POST   /users                      Create user
PUT    /users/1                    Replace user
PATCH  /users/1                    Partial update
DELETE /users/:id                  Delete user
GET    /products                   List products
GET    /products?category=electronics   Filter
GET    /users?_page=1&_limit=2     Pagination
GET    /orders                     List orders
```

## Project structure

```
postman/
├── db.json              # API data (my-json-server reads this)
├── docs/                # GitHub Pages site
├── postman/             # Import these into Postman
│   ├── QA-Learning-API.postman_collection.json
│   └── QA-Learning-API.postman_environment.json
└── .github/workflows/   # Auto-deploy docs
```

## License

MIT — free for learning and training.
