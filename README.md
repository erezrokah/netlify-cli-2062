# netlify/cli#2062

This repository reproduces an issue in [netlify/cli#2062](https://github.com/netlify/cli/issues/2062)

To try locally, first run `npm install`

## Scenario: Parcel bundler has multiple entry files **[fail]**

- Set `netlify.toml` to use `npm run dev:all` command:

```toml
# netlify.toml
[dev]
  command = "npm run dev:all"
```

- Run `npm start`
- Should see index.html contents at <http://localhost:8888>
- Should see styleguide.html contents at <http://localhost:8888/styleguide>
- Should see index.html contents at <http://localhost:8888/some-path> -- this fails!

## Scenario: Parcel bundler has a single entry file **[pass]**

- Set `netlify.toml` to use `npm run dev:app` command:

```toml
# netlify.toml
[dev]
  command = "npm run dev:app"
```

- Run `npm start`
- Should see index.html contents at <http://localhost:8888>
- Should see index.html contents at <http://localhost:8888/some-path>
