---
layout: post
title: Dev Container Opinions
permalink: /2025/04/01/devcontainer
date: 2025-04-01 14:30:45 +0200
tags:
  - development
---

Happy `rails new` day!

I love getting to start a new Rails app. It's the moment to pick all the dependencies you missed from your most recent in legacy app experience.

For me that's:

✅ PostgreSQL ❌ MongoDB

✅ RSpec ❌ Minitest

✅ Factory Bot ❌ Fixtures

✅ Turbo + Stimulus ❌ API only with SPA

✅ Tailwind ❌ Bootstrap

Docker in production for sure. But in my dev environment? 🤔

I experimented a bit with setting up a DevContainer and decided I'm not into it. I get the arguments to do it. That it's good to have your Development environment as close to Production as possible. That you want someone to have an easy first setup. The thing is that I feel myself having to dance around a different set of limitations.

- DevContianers are propriatory (Microsoft) and require using VS Code or Cursor.
- Customizing my terminal requires an extra layer of configuration.
- The only terminal you can use is the one built into the editor. I only want to use ❤️ iTerm ❤️.
- A docker container constrains the resources used on your machine in development.
- On the last Rails app I worked on, the docker container didn't run well on my machine. I ended up installing it locally anyways. 🤷‍♀️

To me these outweight the speed of setup (which you typically only do once per laptop) and matching the environments.
