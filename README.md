<div align="center">

<img src="media/threads-icon.png" width="128" alt="Threads">

# Threads

[![Raycast Store](https://img.shields.io/badge/Raycast-Store-FF6363?style=flat-square&logo=raycast&logoColor=white)](https://www.raycast.com/chrismessina/threads)
[![Licence MIT](https://img.shields.io/badge/Licence-MIT-22C55E?style=flat-square)](LICENSE)
[![Follow @chrismessina](https://img.shields.io/github/followers/chrismessina?label=Follow%20chrismessina&style=social)](https://github.com/chrismessina)
[![Stars](https://img.shields.io/github/stars/chrismessina/raycast-threads?style=social)](https://github.com/chrismessina/raycast-threads/stargazers)

**Post to Threads, jump straight to any feed, and download media from a post — without leaving Raycast.**

[Features](#features) • [Requirements](#requirements) • [Quick Start](#quick-start) • [Usage](#usage) • [Development](#development)

</div>

---

## Features

- **Download media from any post** — images, videos, and voice posts, saved straight to your Downloads folder. Carousels download every item.
- **Paste any Threads link** — a canonical post URL, one with tracking parameters, or a `threads.com/share/…` short link. They all resolve.
- **Files are named correctly** — the extension reads the format the server actually sent rather than trusting the URL, so an image that is really WebP does not land as a broken `.jpg`.
- **Nothing is ever overwritten** — a download whose name is already taken saves alongside as `name (1).ext`, and a half-finished download can never be mistaken for a complete one.
- **Optional format conversion** — keep the original, or convert images to JPEG or PNG on the way in.
- **Post and navigate** — compose a post, follow an account, open a profile, search, and jump to any of your feeds or activity tabs.

---

## Requirements

- [Raycast](https://www.raycast.com/) installed
- macOS, for the optional **Image Format** conversion only. Everything else works on macOS and Windows alike.

---

## Quick Start

1. Copy a Threads post link — from the share sheet, the address bar, or a `/share/` link someone sent you.
2. Open Raycast and search for **"Download Threads Media"**.
3. Paste the link. The media lands in your Downloads folder, or wherever you point **Media Download Path**.

---

## Usage

### Commands

| Command | Mode | Description |
| --- | --- | --- |
| Download Threads Media | `no-view` | Download images, videos, and voice posts from a post URL |
| Start a New Thread | `view` | Compose a post in a form, with an optional link |
| Quick Post | `no-view` | Post straight from the Raycast bar |
| Quick Follow | `no-view` | Follow an account by username |
| View Profile | `no-view` | Open a profile |
| Search | `no-view` | Search Threads by keyword or hashtag, sorted by top or recent |
| My Feeds | `no-view` | Open For You, Following, Liked, or Saved |
| Activity | `no-view` | Open any activity tab — replies, mentions, quotes, reposts, and more |
| Insights | `no-view` | View account insights over 7, 14, 30, or 90 days |

### Actions

| Action | Shortcut | Description |
| --- | --- | --- |
| Show in Finder | `⌘ O` | Reveal a completed download |
| Copy Path | `⌘ ⇧ C` | Copy the saved file's path |
| Copy Error | `⌘ ⇧ C` | Copy the details of a failure, for a bug report |

### Preferences

| Preference | Values | Default |
| --- | --- | --- |
| Debug Logging | on / off | off |
| Media Download Path | a folder | `~/Downloads` |
| Image Format | Original / JPEG / PNG | Original |

**Media Download Path** and **Image Format** are preferences of the *Download Threads Media*
command — expand it in the extension's settings to find them.

---

## Development

### Project Structure

```
raycast-threads/
├── src/
│   ├── download-thread-media.tsx   # the one command that does real work
│   ├── new-thread.tsx              # compose form
│   ├── *.tsx                       # URL-builder commands
│   └── lib/
│       ├── threads-post.ts         # resolves a link to its media
│       ├── media-files.ts          # paths, conversion, extensions
│       ├── download-media.ts       # streams a download to disk
│       └── *.test.ts               # vitest, colocated
├── assets/                         # extension icon (runtime)
├── media/                          # README images
├── metadata/                       # Store screenshots
├── package.json
└── tsconfig.json
```

### Scripts

| Script | Description |
| --- | --- |
| `npm run dev` | Start in development mode with hot reload |
| `npm run build` | Build for production |
| `npm run lint` | Run Raycast ESLint config |
| `npm run fix-lint` | Auto-fix lint issues |
| `npm test` | Run the test suite — no network |
| `npm run test:live` | Resolve real posts against threads.com |
| `npm run publish` | Publish to the Raycast Store |

### Clone & Run

```sh
git clone https://github.com/chrismessina/raycast-threads.git
cd raycast-threads
npm install
npm run dev
```

See [AGENTS.md](AGENTS.md) for how media resolution works and why it is shaped the way it is.

---

## Tech Stack

| Package | Role |
| --- | --- |
| `@raycast/api` | Raycast extension primitives |
| `@chrismessina/raycast-kit` | Failure toasts with a Copy Error action, byte formatting, plurals |
| `@chrismessina/raycast-logger` | Structured logging behind the Debug Logging preference |

---

MIT © [Chris Messina](https://github.com/chrismessina)
