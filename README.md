Perfetto, ho integrato i tornei e rinominato le epiche in inglese come richiesto. La struttura rimane granulare e orientata ai task.

---

### **Epic: v0.1 - "The Green Felt"**
*Obiettivo: Lanciare un'esperienza di gioco impeccabile per la Briscola, con le fondamenta social e competitive pronte.*

*   **Feature: [Auth] Platform Access**
    *   **[CGB-001] Task:** [DB] Create `users` table.
    *   **[CGB-002] Task:** [API] Implement `POST /api/auth/register` endpoint.
    *   **[CGB-003] Task:** [API] Implement `POST /api/auth/login` endpoint (JWT).
    *   **[CGB-004] Task:** [API] Create auth middleware for protected endpoints.
    *   **[CGB-005] Task:** [UI] Build Login page with form and error handling.
    *   **[CGB-006] Task:** [UI] Build Registration page with form and validation.
    *   **[CGB-007] Task:** [Leptos] Implement global state for authenticated user.

*   **Feature: [Core-Briscola] Functional Briscola Match**
    *   **[CGB-008] Task:** [Engine-Hardcoded] Define Rust structs for `Card`, `Deck`, `PlayerHand`, `GameState`.
    *   **[CGB-009] Task:** [Engine-Hardcoded] Implement card dealing logic.
    *   **[CGB-010] Task:** [Engine-Hardcoded] Implement single-hand logic (who plays, who wins).
    *   **[CGB-011] Task:** [Engine-Hardcoded] Implement end-of-game point calculation.
    *   **[CGB-012] Task:** [API] Create `POST /api/games/create` endpoint.
    *   **[CGB-013] Task:** [API] Create `POST /api/games/{id}/join` endpoint.

*   **Feature: [Real-time] Live Game Interface**
    *   **[CGB-014] Task:** [WebSocket] Create a WebSocket Actor in Actix for the game session.
    *   **[CGB-015] Task:** [WebSocket] Define WebSocket message protocol (e.g., `PlayCard`, `GameStateUpdate`).
    *   **[CGB-016] Task:** [UI] Build `<GameBoard>` component.
    *   **[CGB-017] Task:** [UI] Build `<Card>` component with click handling and visual states.
    *   **[CGB-018] Task:** [UI] Connect `<GameBoard>` to WebSocket for state rendering.
    *   **[CGB-019] Task:** [UI] Implement "play card" action sending via WebSocket.

---

### **Epic: v0.5 - "The Duelist's Circle"**
*Obiettivo: Trasformare il sito da un semplice gioco a una community viva con classifiche, tornei e interazioni sociali.*

*   **Feature: [Social] Friends Management**
    *   **[CGB-020] Task:** [DB] Create `friendships` table.
    *   **[CGB-021] Task:** [API] Endpoints for send/accept/decline/remove friend requests.
    *   **[CGB-022] Task:** [API] Endpoint `GET /api/friends` to list friends and their status.
    *   **[CGB-023] Task:** [UI] Build "Friends" page with tabs for list, pending requests, and user search.
    *   **[CGB-024] Task:** [UI] Add "Invite Friend" button to game lobbies.

*   **Feature: [Competitive] ELO Matchmaking & Leaderboards**
    *   **[CGB-025] Task:** [DB] Add `elo` column to `users` table.
    *   **[CGB-026] Task:** [Engine-Hardcoded] Implement ELO calculation function.
    *   **[CGB-027] Task:** [Core] Create an in-memory matchmaking queue for ranked games.
    *   **[CGB-028] Task:** [UI] Add "Ranked" / "Casual" mode selector in the lobby.
    *   **[CGB-029] Task:** [UI] Build "Leaderboard" page showing top 100 players.

*   **Feature: [Competitive] Tournaments**
    *   **[CGB-030] Task:** [DB] Design and create tables for `tournaments`, `tournament_participants`, and `matches`.
    *   **[CGB-031] Task:** [API] Endpoints for creating, listing, and joining tournaments.
    *   **[CGB-032] Task:** [Core] Implement a simple single-elimination bracket generation logic.
    *   **[CGB-033] Task:** [Core] Logic to automatically advance winners to the next round.
    *   **[CGB-034] Task:** [UI] Build tournament list page.
    *   **[CGB-035] Task:** [UI] Build a visual tournament bracket view.

*   **Feature: [UI] User Profile & Stats**
    *   **[CGB-036] Task:** [DB] Create `user_stats` table (`user_id`, `wins`, `losses`, etc.).
    *   **[CGB-037] Task:** [API] Endpoint `GET /api/users/{username}` for public data and stats.
    *   **[CGB-038] Task:** [UI] Build the user profile page showing avatar, ELO, stats, and match history.

---

### **Epic: v1.0 - "Tales from the Table"**
*Obiettivo: Arricchire l'esperienza di gioco con funzionalità avanzate che aumentano il coinvolgimento e la rigiocabilità.*

*   **Feature: [Player-XP] Game Replays**
    *   **[CGB-039] Task:** [DB] Create `game_replays` table to store the sequence of actions.
    *   **[CGB-040] Task:** [Engine-Hardcoded] Modify the engine to log every valid action to the DB.
    *   **[CGB-041] Task:** [API] Endpoint `GET /api/replays/{id}` to fetch replay data.
    *   **[CGB-042] Task:** [UI] Build a "Replay Player" UI.
    *   **[CGB-043] Task:** [UI] Add replay list to the user's match history.

*   **Feature: [Player-XP] Spectator Mode**
    *   **[CGB-044] Task:** [WebSocket] Allow read-only connections to the game session actor.
    *   **[CGB-045] Task:** [API] Endpoint to get a list of spectatable live games.
    *   **[CGB-046] Task:** [UI] Add a "Spectate" button next to ongoing games.

*   **Feature: [Player-XP] In-Game Chat**
    *   **[CGB-047] Task:** [WebSocket] Add a `ChatMessage` to the WebSocket protocol.
    *   **[CGB-048] Task:** [Engine-Hardcoded] Forward chat messages to players in the same room.
    *   **[CGB-049] Task:** [UI] Add a simple chat UI to the game overlay.

*   **Feature: [Player-XP] Achievements System**
    *   **[CGB-050] Task:** [DB] Create `achievements` (definitions) and `user_achievements` (unlocks) tables.
    *   **[CGB-051] Task:** [Engine-Hardcoded] Add "hooks" to the game logic that emit events.
    *   **[CGB-052] Task:** [Core] Create an "Achievement Service" to listen for events and unlock achievements.
    *   **[CGB-053] Task:** [UI] Build "Achievements" page in the user profile.
    *   **[CGB-054] Task:** [UI] Implement on-screen "toast" notifications for unlocks.

---

### **Epic: v2.0 - "The Artificer's Forge"**
*Obiettivo: Rilasciare il Card Game Builder, trasformando gli utenti da giocatori a creatori.*

*   **Feature: [Engine-Core] Agnostic Game Engine (TCA)**
    *   **[CGB-055] Task:** [DB] Design and create the final schema for `rules` using JSONB (Trigger, Conditions, Actions).
    *   **[CGB-056] Task:** [Engine] Implement the DSL parser using `pest`.
    *   **[CGB-057] Task:** [Engine] Implement the translator from `pest`'s AST to JSONB.
    *   **[CGB-058] Task:** [Engine] Create the "Rule Interpreter" that executes logic from the JSONB.
    *   **[CGB-059] Task:** [Engine] Replace the hard-coded engine with the new interpreter.

*   **Feature: [Engine-Core] Dynamic Game Board Management**
    *   **[CGB-060] Task:** [DB] Design and create the `zones` table with `properties` and `layout` JSONB fields.
    *   **[CGB-061] Task:** [Engine] The engine must load zone definitions at the start of a match.
    *   **[CGB-062] Task:** [UI] Refactor `<GameBoard>` to dynamically render zones using CSS absolute positioning.

*   **Feature: [Builder] Creation Interface**
    *   **[CGB-063] Task:** [UI] Build "My Games" creator dashboard.
    *   **[CGB-064] Task:** [UI] Develop the visual Zone Editor (drag-and-drop on a canvas).
    *   **[CGB-065] Task:** [UI] Develop the Card and Card Template Editor.
    *   **[CGB-066] Task:** [UI] Integrate Monaco Editor for the rules DSL.
    *   **[CGB-067] Task:** [API] Create all CRUD endpoints for `games`, `cards`, `rules`, and `zones`.

*   **Feature: [Core] Deck Builder & Game Versioning**
    *   **[CGB-068] Task:** [DB] Add versioning support to the `games` table schema.
    *   **[CGB-069] Task:** [DB] Create `decks` and `deck_cards` tables.
    *   **[CGB-070] Task:** [UI] Build the Deck Builder interface for games that require it.
    *   **[CGB-071] Task:** [UI] Build the Public Game Library to browse community-created games.

*   **Feature: [Dogfooding] Full Briscola Migration**
    *   **[CGB-072] Task:** [Content] Use the complete Builder to recreate Briscola as a community game.
    *   **[CGB-073] Task:** [Test] Verify that the custom-built Briscola behaves identically to the original hard-coded version.
