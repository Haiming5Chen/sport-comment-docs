# API and Database Reference

This document describes the external NBA data endpoints used by the system and the Firestore data structures created during the data ingestion process.

This reference is intended for developers maintaining or extending backend services and frontend features that rely on NBA game and player data.

---

# 1. Overview

The NBA ingestion service retrieves game and player data from the **SportsDataIO API** and writes structured documents to **Firestore**.

## Data Flow

```text
SportsDataIO API
      ↓
Python ingestion script
      ↓
Firestore database
      ↓
Frontend application
```

## Authentication Requirements

The system requires the following credentials:

- `SPORTSDATAIO_KEY` environment variable
- Firebase service account key file
- Firestore access permissions

---

# 2. External API Endpoints

## 2.1 Get Daily Game Scores

### Endpoint

```http
GET https://api.sportsdata.io/v3/nba/scores/json/ScoresBasic/{DATE}?key={API_KEY}
```

### Purpose

Returns NBA games for a specific date, including game status and scores.

### Path Parameter

`{DATE}` format:

```
YYYY-MMM-DD
```

Example:

```
2026-MAR-01
```

### Example Request

```http
GET /v3/nba/scores/json/ScoresBasic/2026-MAR-01?key=YOUR_KEY
```

### Usage in Application

For each returned game:

```
Firestore document:
nbaGames/{gameId}
```

---

## 2.2 Get Final Box Scores (Player Statistics)

### Endpoint

```http
GET https://api.sportsdata.io/v3/nba/stats/json/BoxScoresFinal/{DATE}?key={API_KEY}
```

### Purpose

Returns finalized player statistics for games on a specific date.

### Path Parameter

```
{DATE} → YYYY-MMM-DD
```

### Example Request

```http
GET /v3/nba/stats/json/BoxScoresFinal/2026-MAR-01?key=YOUR_KEY
```

### Usage in Application

Player statistics are written to:

```
nbaGames/{gameId}/players/{playerId}
```

---

# API Authentication Errors

## 401 / 403 Errors

Possible causes:

- Invalid API key
- API key permission problems
- Insufficient SportsDataIO subscription level

### Resolution

- Verify that the API key is valid
- Confirm the subscription plan allows this endpoint
- Ensure the key is correctly set in the environment variables

---

# 3. Database Reference (Firestore)

The system stores sports data in **Firestore collections**.

Each league follows the same collection pattern.

---

## 3.1 Naming Pattern by League

Each league contains three top-level collections:

```
{league}Teams
{league}Players
{league}Games
```

Examples:

```
nbaTeams
nbaPlayers
nbaGames
```

```
nflTeams
nflPlayers
nflGames
```

This structure keeps league data separated and simplifies queries.

---

## 3.2 How Records Connect

The application links records across collections using stable IDs.

```
TeamID   → connects teams, players, and games
GameID   → identifies a game document
PlayerID → identifies a player document
```

### Example Relationships

Games contain:

```
homeTeamId
awayTeamId
```

Players contain:

```
teamId
```

Player game statistics use:

```
gameId
playerId
```

---

## What This Enables

This data model allows the system to:

- Retrieve all games for a specific team
- Retrieve all players belonging to a team
- Retrieve all players who participated in a specific game
