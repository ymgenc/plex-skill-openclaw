# 🎬 Plex Standalone CLI Skill

A high-performance, standalone Command-Line Interface (CLI) skill designed for AI agents (like **OpenClaw**) to manage and control a Plex Media Server directly. 

This skill eliminates the need for persistent MCP servers by providing a lightweight, one-shot execution model with secured local caching and robust playback management.

---

## ⚡ Features

- **🚀 Lightning-Fast Search**: Uses a secured local JSON index (stored in the system's temporary directory) for sub-200ms search results across your entire library.
- **🎮 Remote Playback Control**: Direct control for `play`, `pause`, `resume`, and `stop` on specific Plex clients (e.g., Apple TV, Chrome, Smart TVs).
- **🎭 Rich Metadata Search**: Search by movie/show title, actors, directors, or genres instantly.
- **📚 Library Explorer**: Easily browse libraries, active sessions, and "Continue Watching" status.
- **🛡️ Secure & Compliant**: 
  - Declarative metadata for all environment variables and binaries.
  - No `.env` dependency; strictly uses system environment variables.
  - Zero persistent trace in the skill folder (uses OS temp directory for caching).
- **📦 Zero Configuration Setup**: Leveraging **PEP 723** and `uv` for seamless dependency management without manual installations.

---

## 🛠️ Quick Setup

### 1. Requirements
Ensure you have [uv](https://astral.sh/uv) and **Python 3.8+** installed on your system.

### 2. Environment Variables
Provide the following credentials to your environment:
- `PLEX_URL`: Your Plex server address (e.g., `http://192.168.1.50:32400`)
- `PLEX_TOKEN`: Your secret [Plex Authentication Token](https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/)

### 3. Basic Commands

```bash
# Sync your library index (recommended periodically)
uv run scripts/plex_cli.py sync

# Search for a movie or an actor
uv run scripts/plex_cli.py search "Inception"
uv run scripts/plex_cli.py search "Christian Bale"

# Control a playback device
uv run scripts/plex_cli.py play "Apple TV" "The Dark Knight"
uv run scripts/plex_cli.py pause "Apple TV"
```

---

## 🏗️ Project Structure

- `SKILL.md`: Comprehensive guide for AI agents to understand how to use the CLI.
- `metadata.json`: Registry-ready metadata for ClawHub and other agentic platforms.
- `scripts/plex_cli.py`: The core engine powered by `plexapi`.

---

## 🔒 Privacy & Security

This skill respects your privacy. It stores a minimal index of your movie/show titles, genres, and artist names **only** in the system's temporary directory to provide fast search capabilities. Active sessions, playback status, and user data are never cached and are fetched in real-time.

---

## 📜 License
This project is open-source and free to use. Contributions are welcome!
