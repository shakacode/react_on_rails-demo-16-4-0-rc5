# React on Rails Pro 16.4.0.rc.5 Demo

Sample Rails app generated with:

- `react_on_rails_pro` gem `16.4.0.rc.5`
- `react-on-rails-pro` npm package `16.4.0-rc.5`
- `react-on-rails-pro-node-renderer` npm package `16.4.0-rc.5`
- `react-on-rails-rsc` npm package `19.0.4` (RSC demo support)

## Quick Start

```bash
bundle install
npm install
bundle exec rails db:prepare
bin/shakapacker
bin/dev
```

Then open <http://localhost:3000/hello_world>.

## RSC Example

- Visit <http://localhost:3000/hello_server> for the React Server Components sample.
- React and ReactDOM are pinned to `19.0.4` for RSC compatibility.

## Known Pitfalls

- The generator requires a clean git working tree; commit or stash first.
- If `/hello_world` raises `No such file or directory ... ssr-generated/server-bundle.js`, run `bin/shakapacker`.
- If `/hello_server` is missing generated packs, run `bundle exec rake react_on_rails:generate_packs` and then `bin/shakapacker`.
- If port 3000 is busy, use `bin/dev` with a procfile update or free the existing process first.
- For pre-release versions, gem and npm formats differ:
  - gem: `16.4.0.rc.5`
  - npm: `16.4.0-rc.5`
