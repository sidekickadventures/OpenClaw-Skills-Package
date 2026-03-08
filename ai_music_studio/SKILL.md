OpenClaw Skill: AI Music Studio

**Purpose:**
Enable the bot to run a fully autonomous AI music studio that handles recording vocals, generating beats, importing audio, mixing, and exporting WAV/MP3, with minimal user interaction.

---

### 1️⃣ Workflow Overview
1.  **Command Reception:** User sends command (via chat or UI).
2.  **Queueing:** OpenClaw bot receives command and pushes it into the AI Command Queue.
3.  **Sequential Execution:**
    *   `/record vocals` → **VocalClaw**
    *   `/generate beat` → **BeatClaw**
    *   `/import audio` → **ImportClaw**
    *   `/mix` → **StudioClaw**
    *   `/export wav/mp3` → **ExportClaw**
4.  **Execution:** Studio Front-End executes all actions in-browser.
5.  **Multi-track Storage:** Session stores all tracks, mixing automatically.
6.  **Delivery:** Export & Delivery sends final track (WAV/MP3) to user automatically.

---

### 2️⃣ Command List

| Command | Action |
| :--- | :--- |
| `recordVocals` | Records vocal input, stores in session |
| `generateBeat` | Generates beat and stores as a track |
| `importAudio` | Imports WAV, MP3, M4A file into session |
| `mixTracks` | Combines all tracks, normalizes audio |
| `exportWav` | Exports merged track as WAV |
| `exportMP3` | Exports merged track as MP3 |
| `exportStems` | (Future) Exports individual track stems |
| `exportProject` | (Future) Exports full project session |

---

### 3️⃣ AI Command Queue Example
```javascript
// Example automated session
aiCommand({action:'recordVocals', name:'Verse1'});
aiCommand({action:'generateBeat', name:'Beat1'});
aiCommand({action:'importAudio', file: userFile, name:'SampleLoop'});
aiCommand({action:'mixTracks'});
aiCommand({action:'exportWav', filename:'final_song.wav'});
aiCommand({action:'exportMP3', filename:'final_song.mp3'});
```
*   **Sequential Logic:** Queue ensures commands run in order automatically.
*   **Result Persistence:** Front-end executes each task and stores results in Multi-Track Session.
*   **Auto-Delivery:** Exports trigger download for the user.

---

### 4️⃣ Session Handling
*   **Persistence:** Tracks are persisted in memory or IndexedDB.
*   **Resumption:** Allows resuming the session if user leaves and returns.
*   **Labeling:** Each track is labeled for easy identification (Vocals, Beat, ImportedAudio).

---

### 5️⃣ Front-End Modules Controlled by Bot

| Module | Functionality |
| :--- | :--- |
| **VocalClaw** | Records user vocals |
| **BeatClaw** | Generates beat patterns |
| **ImportClaw** | Imports audio files (WAV/MP3/M4A) |
| **StudioClaw** | Mixes all tracks into single buffer |
| **ExportClaw** | Exports final WAV/MP3, optionally stems/project |
| **Session** | Stores multi-track session and persists audio buffers |

---

### 6️⃣ User Experience
1.  User initiates session.
2.  Bot runs command queue autonomously.
3.  User may monitor or intervene via simple commands.
4.  Final audio is delivered automatically as download.

---

### 7️⃣ Optional Future Upgrades
*   Export individual stems or full project files.
*   MP3 compression (integrated via lamejs).
*   Blockchain minting for WAV/MP3 as Bitcoin Ordinals or Tezos NFTs.
*   Collaborative multi-user session control.

---

### ✅ Behavior Rules for the Bot
*   **Autonomy First:** User interaction should be optional.
*   **Sequential Reliability:** Use the queue system to ensure tasks don't overlap.
*   **Cross-Platform Ready:** Designed for deployment on desktop, Android, iOS, and messaging platforms (Telegram/Discord).
