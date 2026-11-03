[SH.png]

# StreamHata

**An open-source streaming ecosystem built for streamers, by a developer who wanted something better.**

**Current version:** `0.1.0-alpha`  
**Status:** Active Development  
**Platform:** Windows / Linux (support varies by component)  
**Website:** https://streamhata.rdpctd.dev

---

## What is StreamHata?

StreamHata is an open-source, all-in-one streaming management ecosystem designed to bring essential streaming tools, integrations, automation, monitoring, and community features into one platform.

Instead of switching between multiple websites, applications, dashboards, and bots, StreamHata aims to provide a unified environment where streamers can manage their broadcasts, interact with their communities, monitor their systems, and organize gaming activities.

What started as a simple Twitch authentication integration has gradually evolved into a much larger software ecosystem.

And yes, it is currently developed and maintained by a single developer.

## Key Features

### Streaming & OBS Integration

- OBS Studio integration
- Broadcast launch and management
- OBS scene interaction
- Browser-source widgets and overlays
- Real-time communication between the desktop client and backend
- Streaming-related automation

**In development:**
- Full OBS scene visualization
- Drag-and-drop scene editing
- Advanced OBS controls

### Twitch Integration

- Twitch OAuth authentication
- Channel points information
- Viewer watch streak tracking
- Chat overlays
- Twitch-related statistics
- Account integration management

### Steam Integration

- Steam account authentication
- Game library synchronization
- Playtime information
- Achievements
- Inventory information
- Game-related metadata

### Donations & Alerts

Integrations with:

- DonationAlerts
- DonateStream

The goal is to provide a centralized environment for donation-related events and streaming interactions.

### Telegram Integration

StreamHata includes a Telegram bot supporting:

- Private messages
- Channel interactions
- Custom commands
- `/start` and `/music` commands
- Stream-related notifications
- Issue reporting and bug-tracking workflows

### Gaming Database

StreamHata includes a gaming database containing more than **200,000 games**.

Game information may include:

- Titles and descriptions
- Release dates
- Platforms
- Publishers
- Ratings
- Screenshots
- External resources

Data is aggregated through integrations with services including IGDB, RAWG, and MobyGames.

Additional information can be retrieved and cached when required.

### Interactive Widgets

StreamHata provides interactive widgets for broadcasts and gaming events, including:

- Random wheel
- Countdown timer
- 3D dice
- Coin toss
- Browser-based overlays

Some widgets use WebGL and require compatible browser rendering capabilities.

### Desktop Application

The desktop application is built with **Tauri, Rust, and a web-based frontend**.

Features include:

- Native desktop integration
- System tray functionality
- Local credential storage through the operating system's keychain
- Real-time updates using WebSocket and Server-Sent Events
- Streaming controls
- System monitoring

Windows alpha builds are currently unsigned.

### Hardware & System Monitoring

StreamHata includes a desktop monitoring system designed to help streamers understand what is happening with their computers during broadcasts.

Available metrics depend on operating system and hardware support and may include:

- CPU utilization and temperature
- GPU utilization and temperature
- Memory usage
- Disk health and storage information
- Fan speeds
- Network statistics
- Streaming performance indicators
- Dropped frames

**Privacy:** Desktop hardware monitoring information is intended to remain local rather than being transmitted to StreamHata servers.

### Issue Tracking & Service Status

StreamHata provides tools for tracking application issues and infrastructure availability.

Features include:

- Issue submission
- Telegram-based bug reporting
- User issue history
- Log attachment options
- Service status page
- Incident classification
- Infrastructure monitoring

Example incident codes:

| Code | Description |
|---|---|
| LG-0100 | Twitch temporarily unavailable |
| U-0100 | Planned downtime |
| SYS-100 | Planned system upgrade |
| UP-0 | Temporary service unavailability |
| TW | Twitch-side incident |
| H | API stress or excessive request load |

## Planned Features

StreamHata is actively evolving. Planned capabilities include:

### StreamHata Messenger

A communication system for streamers, including:

- Direct messaging
- Streamer connections
- Group conversations
- External messaging integrations
- Twitch messaging interoperability
- Optional message encryption

### Multi-Account Support

Manage multiple connected accounts across supported platforms, including Twitch, Steam, and donation services.

### Plugin & SDK Ecosystem

A developer-friendly extension system intended to support:

- Custom integrations
- Third-party extensions
- Community-developed tools
- Streamer automation
- External service connections

### AI Integration

Future integration with **V3ritas AI**, an independently developed AI project.

Potential capabilities include:

- Voice-assisted interaction
- Intelligent search
- Contextual assistance
- Automated troubleshooting

### Gaming Events

StreamHata is also intended to support advanced gaming events, including custom rules, participant management, interactive mechanics, and event administration.

---

## Technology Stack

StreamHata combines multiple technologies depending on the responsibilities of each component.

| Component | Technology |
|---|---|
| Backend | Go |
| Frontend | Angular |
| UI Framework | Taiga UI |
| Desktop | Tauri / Rust |
| OBS Plugin | C++ / Qt |
| Database | PostgreSQL |
| Secrets Management | OpenBao |
| Metrics | Prometheus |
| Logs | Loki |
| Dashboards | Grafana |
| Real-time Communication | WebSocket / SSE |
| External Integrations | REST APIs / OAuth |

## Architecture

StreamHata uses a distributed infrastructure with separation between its major components.

```text
                StreamHata Ecosystem
                         |
           +-------------+-------------+
           |                           |
      Desktop Client              Web Frontend
      Tauri + Rust                Angular
           |                           |
           +-------------+-------------+
                         |
                    Go Backend
                         |
          +--------------+--------------+
          |              |              |
      PostgreSQL       OpenBao      Integrations
          |                             |
     Data Storage              Twitch / Steam
                               Donations / Telegram

                 Observability
                       |
              Prometheus + Loki
                       |
                    Grafana
```

The infrastructure is designed to support independent deployment and monitoring of core services.

## Security

Security is an important part of StreamHata's development.

The architecture includes:

- OAuth-based authentication for supported services
- Operating-system keychain integration
- Centralized secrets management with OpenBao
- Separation of application components
- Protected backend-to-database communication
- API rate limiting
- Service monitoring and incident tracking

Additional security improvements are planned.

**Important:** StreamHata is currently alpha software. Security-sensitive deployments should be evaluated carefully, and no alpha release should be assumed production-ready without appropriate testing.

## Open Source Philosophy

StreamHata is developed around a few principles:

**Useful features first.** Features should solve real problems for streamers.

**Transparency.** Bugs, limitations, and known issues should be documented rather than hidden.

**Extensibility.** Developers should be able to contribute integrations and build tools around the ecosystem.

**User control.** Streamers should have control over their integrations, accounts, and workflows.

**Continuous improvement.** Stable functionality matters more than claiming that everything is finished.

## Current Development Status

**StreamHata 0.1.0-alpha**

The project is in active alpha development.

Some components are functional, while others are experimental, incomplete, or still being designed.

Expect:

- Breaking changes
- Unfinished features
- Platform-specific limitations
- Bugs
- Frequent updates
- Changes to APIs and configuration

Alpha does not mean feature-complete.

It means development is underway and the software is available for early experimentation.

## Known Limitations

### OBS Browser Source on Linux

Some Linux environments may experience DNS or network-related issues after OBS has been running for approximately 10–15 minutes with the Chromium-based browser-source plugin.

The issue is under investigation.

### Windows Application Signing

Current Windows alpha builds may be distributed without a code-signing certificate.

Operating systems may display warnings when launching unsigned builds.

### Third-Party APIs

Some features depend on external services and their APIs.

Availability, authentication behavior, rate limits, and supported functionality may change independently of StreamHata.

## Contributing

Contributions are welcome.

You can help by:

- Reporting reproducible bugs
- Suggesting useful features
- Improving documentation
- Testing alpha releases
- Contributing code
- Reviewing integrations
- Helping investigate platform-specific issues

Please review the repository's contribution guidelines and existing issues before submitting major changes.

## Bug Reports

When reporting an issue, please provide:

1. Operating system and version
2. StreamHata version
3. Steps to reproduce
4. Expected behavior
5. Actual behavior
6. Relevant logs, if available

Never include access tokens, passwords, API secrets, or other sensitive information in public reports.

## Project Links

**Website:** https://streamhata.rdpctd.dev

**Developer:** [p7x-dev](https://github.com/p7x-dev)

**Status:** Alpha

## Final Words

StreamHata was not originally intended to become a large ecosystem.

It started with a relatively simple idea: make streaming management more convenient.

Over time, that idea expanded into desktop software, backend services, OBS integration, system monitoring, gaming tools, community features, and a growing infrastructure.

The project continues to evolve.

Built by one developer. Designed for streamers. Open to contributors.

**StreamHata — More than just streaming.**
