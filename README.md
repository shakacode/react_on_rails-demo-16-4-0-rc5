# React on Rails Pro 16.4.0-rc.5 Demo

This repository is a minimal Rails 8 app that demonstrates React on Rails Pro with:

- Standard React mounting in a Rails view (`react_component`)
- React Server Components (RSC) with streaming (`stream_react_component`)
- Node Renderer based server rendering infrastructure

It is intended as a reference app for anyone evaluating React on Rails and React on Rails Pro.

## Versions Used

- Ruby: `3.3.10`
- Rails: `8.1.2`
- `react_on_rails_pro` gem: `16.4.0.rc.5`
- `react-on-rails-pro` npm package: `16.4.0-rc.5`
- `react-on-rails-pro-node-renderer` npm package: `16.4.0-rc.5`
- React / ReactDOM: `19.0.4`

Note on prerelease version naming:

- RubyGems use `16.4.0.rc.5`
- npm uses `16.4.0-rc.5`

## Quick Start

```bash
bin/setup
bin/dev
```

Then open:

- <http://localhost:3000/hello_world>
- <http://localhost:3000/hello_server>

`bin/setup` is lockfile-safe and uses `npm ci` when `package-lock.json` exists.

## What `bin/dev` Runs

`bin/dev` uses `Procfile.dev` and starts:

- Rails app server (port `3000`)
- Shakapacker dev server
- Server bundle watcher (`SERVER_BUNDLE_ONLY=yes`)
- Node renderer (`client/node-renderer.js`, port `3800`)
- RSC bundle watcher (`RSC_BUNDLE_ONLY=yes`)

This is the easiest way to run the full Pro + RSC development workflow.

## Demo Routes

- `/hello_world`
  - Basic React on Rails integration via `react_component`
  - File: `app/views/hello_world/index.html.erb`
- `/hello_server`
  - Streaming RSC demo via `stream_react_component`
  - Files: `app/controllers/hello_server_controller.rb`, `app/views/hello_server/index.html.erb`

## Key Files

- `config/initializers/react_on_rails_pro.rb`
  - Pro configuration, Node renderer URL/password, RSC settings
- `client/node-renderer.js`
  - Node renderer process config
- `config/webpack/*`
  - Separate client/server/RSC webpack configuration
- `app/javascript/src/HelloServer/*`
  - RSC example components

## Troubleshooting

- Missing `ssr-generated/server-bundle.js`:
  - Run `bin/shakapacker` once, or keep `bin/dev` running.
- `/hello_server` fails with connection refused to `localhost:3800`:
  - Ensure the node renderer is running (`bin/dev` handles this).
- Lockfile changed after setup:
  - Use `bin/setup` (not `npm install`) for consistent installs.

## Learn More

- React on Rails docs:
  - <https://www.shakacode.com/react-on-rails/docs/>
- React on Rails Pro docs:
  - <https://www.shakacode.com/react-on-rails-pro/docs/>
- React Server Components guide (Pro):
  - <https://www.shakacode.com/react-on-rails-pro/docs/react-server-components/>
- Main repo:
  - <https://github.com/shakacode/react_on_rails>
