# Open Source Maintainer Health

A small Express app for tracking signs of maintainer strain on open source projects, such as slow response times and a growing issue backlog. It is for maintainers and contributors who want a quick burnout-risk check across a few projects.

## Features

- Record a project's response time, open issue count, and contributor count
- Flags burnout risk as `high` when response time is over 7 days or the backlog is over 50 issues
- Returns the risk level immediately when a project is added
- Saves entries to a local `data.json` file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

The server runs on http://localhost:3022. Add a project and list them:

```bash
curl -X POST http://localhost:3022/api/projects \
  -H "Content-Type: application/json" \
  -d '{"name":"my-lib","responseTime":10,"issues":35,"contributors":2}'

curl http://localhost:3022/api/projects
```

## How it works

- `server.js` is an Express server with `POST /api/projects` and `GET /api/projects`. GET returns the 50 most recent entries.
- The risk rule is a fixed threshold in `server.js`; numbers are entered by hand rather than pulled from GitHub.
- Entries are stored in `data.json` in the project folder, which is created on first run and ignored by git.
- `index.html` is served at the root URL but is still a generic placeholder form that is not connected to this API. `utils.js` contains helpers that `server.js` does not use yet.

## Status

Prototype. Manual data entry with a simple threshold rule; the web page is not wired up, and there is no validation or authentication.

## License

MIT, see [LICENSE](LICENSE).
