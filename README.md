# Yahoo Fantasy MCP

A personal, noncommercial, self-hosted analytics integration for **Yahoo Fantasy Basketball** and **Yahoo Fantasy Football**.

> **Status:** Planning / API access requested. This repository describes a proposed project; the integration is not implemented yet and is not affiliated with or endorsed by Yahoo.

## Purpose

The goal is to securely retrieve fantasy league data and make it available for personal analysis, including through an optional AI assistant using the Model Context Protocol (MCP). The initial integration will be **read-only**: it will not submit lineup changes, add or drop players, or execute trades.

## Planned capabilities

- Discover the authenticated user's fantasy leagues and read league scoring, roster, and transaction settings.
- Retrieve team rosters, standings, schedules, matchups, and available players.
- Retrieve relevant player statistics and transaction history, subject to the data and permissions exposed by Yahoo's API.
- Analyze fantasy basketball head-to-head category matchups, roster strengths, and waiver candidates.
- Analyze fantasy football matchups, roster decisions, and waiver candidates according to league settings.
- Provide a secure MCP interface for asking questions about league data. Forecasts or projections, if added, will be identified separately from Yahoo's historical/statistical data.

## Intended use and audience

This is a hobby project for **one individual user** and their own Yahoo Fantasy leagues. It is not a commercial service, a public fantasy platform, or a product offered to other users.

The application is intended to run in Docker on a privately managed home server. Any remote interface will require authentication; no public anonymous access to league data is planned.

## Proposed architecture

```text
Personal AI client (optional)
          |
   Authenticated MCP endpoint
          |
   Self-hosted fantasy service
          |
   Yahoo Fantasy Sports API
       (OAuth 2.0)
```

A small internal API may also provide a consolidated read-only fantasy context for personal tools.

## Security and responsible API use

- Authenticate through Yahoo's supported OAuth flow.
- Keep access and refresh tokens in private server-side configuration or protected storage; never commit them to this repository.
- Request only necessary permissions and data.
- Cache appropriate API responses and respect applicable rate limits and platform policies.
- Restrict access to the service and avoid publishing private league or account information.
- Follow Yahoo's developer terms, attribution requirements, and any conditions attached to API approval.

## Development roadmap

1. Obtain and verify Yahoo Fantasy Sports API access.
2. Implement OAuth authorization and secure token handling.
3. Add league discovery, settings, teams, rosters, and matchup retrieval.
4. Implement basketball nine-category matchup analysis and waiver evaluation.
5. Add football-specific analysis using the same authentication and data layer.
6. Expose authenticated, read-only MCP tools and document local deployment.

## Project status

No Yahoo API credentials or tokens are included. Implementation and supported endpoints depend on approval and the capabilities available under the current Yahoo developer program.

## References

- [Yahoo Fantasy Sports Developer Documentation](https://sports.yahoo.com/developer/docs/)
- [Yahoo Fantasy Sports API Access](https://sports.yahoo.com/developer/access/)

## Disclaimer

Yahoo and Yahoo Fantasy Sports are trademarks of their respective owners. This independent personal project is not affiliated with, sponsored by, or endorsed by Yahoo.
