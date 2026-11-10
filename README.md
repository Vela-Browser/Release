# Vela

A calm, customizable desktop web browser for Windows, built with [Electron](https://www.electronjs.org/).

Vela lets you make the browser look and feel the way you like, keeps your logins in an encrypted vault, blocks ads, includes an AI assistant, and has optional friends and group chat powered by a small server you can run yourself.

## Features

- **Profiles**: separate browsing for work, home or friends, each with its own picture, banner, bookmarks and history. Profiles can be protected with a password or an authenticator code.
- **Customization**: themes and a custom accent colour, quick looks, corner roundness, spacing, fonts (including any installed font), toolbar icon size, address bar shape, tab styles, page frame, shadows, scrollbars and more.
- **Ad blocker**: built-in blocking to keep pages cleaner and faster.
- **Password manager**: an encrypted vault for saved logins.
- **AI assistant**: ask questions, summarize the page you are reading, and attach images, videos and files.
- **Social**: follow people, become friends when you follow each other, send message requests, chat, react, reply and delete messages ("Delete for me" or "Delete for everyone"), and create group chats with invite links, admins, bans, kicks and timed mutes.
- **Side panels**: bookmarks, history, downloads, passwords, profile, customization and more, without leaving the page.

## Repository layout

| Folder | What it is |
| --- | --- |
| `vela-browser/` | The desktop browser (Electron app) |
| `social-server/` | The optional server behind the Social panel (plain Node.js, no dependencies) |

## Getting started

You need [Node.js](https://nodejs.org/) 18 or newer.

### Run the browser

```bash
cd vela-browser
npm install
npm start
```

### Build the Windows installer

```bash
cd vela-browser
npm install
npm run dist
```

The installer is created in `vela-browser/dist` (for example `Vela Setup 1.3.0.exe`). If the build fails with a symlink or permission error, run the terminal as Administrator or turn on Developer Mode in Windows, then try again.

### Run the social server (optional)

The Social panel needs a server that everyone who wants to chat together connects to.

```bash
cd social-server
node server.js          # http://localhost:3000
node test.js            # runs the full rule checks
```

Then open **Social** in Vela's side panel, enter the server address and create an account. Data is stored in `social-server/data/`. To use it over the internet, run it on a reachable machine behind HTTPS (for example with Caddy or nginx). See [`social-server/README.md`](social-server/README.md) for details and the full list of rules.

## AI assistant setup

The assistant calls an AI provider with an API key. Add your own key in `vela-browser/assistant.js` before building. **Never commit a real key to a public repository.**

## Privacy

- Profiles, bookmarks, history, settings and downloads are stored locally on your computer.
- Saved passwords are kept in an encrypted vault.
- When you use the AI assistant, your message, attached files and (if enabled) the current page's content are sent to the AI provider to produce an answer.
- When you use Social, your account details and messages are stored on the server you connect to. Messages are not end-to-end encrypted.

## Project status

Vela is under active development. Issues and pull requests are welcome.

## License

Add your chosen license here (for example MIT) and include a `LICENSE` file.
