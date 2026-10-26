# Open Source Maintainer Health

Small prototypes for tracking the health of open source projects. Each part is a standalone Express server with a static `index.html` page and stores its data in a local `data.json` file.

## Parts

- Repo root: OSSHealth. Log a project's response time, open issues, and contributor count, and get a burnout risk rating. Runs on port 3022.
- `sustain/`: Sustain. Log project health checks (response time, backlog, contributors, last update) and see burnout risk per project. Runs on port 3011.
- `githhealthdash/`: GitHub Project Health Dashboard. Track repos by name, language, stars, and last update. Runs on port 3021.

## Running

Each part has its own `package.json`. Run it from its own folder, since the server serves files from the current directory.

```bash
npm install && npm start
```

```bash
cd sustain && npm install && npm start
```

```bash
cd githhealthdash && npm install && npm start
```

## License

MIT, see [LICENSE](LICENSE).
