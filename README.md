# EVE Online zKillboard Stats Matrix

This is a powerful, client-side tool for EVE Online players, recruiters, and fleet commanders to fetch and display character kill statistics in a detailed, matrix-style view. It's a single, self-contained HTML file that requires no installation or backend—just open it in your browser.

The tool aggregates data from both the **zKillboard API** and the official **EVE Online ESI API** to provide a comprehensive overview of pilot activity over time.

<img width="1425" height="565" alt="image" src="https://github.com/user-attachments/assets/34c3d786-813c-4e1c-8159-d5a7262223c6" />

## ✨ Features

- **Multi-Character Fetching**: Input a list of character names to fetch stats for all of them in one go.
- **Dynamic Data Matrix**: Displays character kills per month in a clear and easy-to-read table.
- **Corporation Data**: Automatically fetches and displays the corporation logo and name for each character.
- **Interactive Filtering**:
    - **Filter by Year**: A dropdown allows you to view stats for a specific year or all time.
    - **Live Name Search**: Instantly filter the table by typing in a character's name.
- **Activity Tracking**:
    - **Inactive Player Flagging**: Automatically highlights players who have had zero kills in the last two visible months.
    - **Hide Inactive**: A checkbox to quickly hide all flagged inactive players from the view.
- **Custom Highlighting**:
    - Visually mark all cells with kill counts below a threshold that you can set.
    - A color picker allows you to choose the exact highlight color you want.
- **Discord-Friendly Export**:
    - A "Copy for Discord" button formats the entire visible table into a monospaced, perfectly aligned text block that you can paste directly into Discord chats.
- **API-Friendly**:
    - Includes a built-in 1-second delay between API requests to respect zKillboard's rate limits and prevent getting blocked.
    - Caches corporation data to minimize redundant ESI calls when multiple characters are in the same corporation.

## 🚀 How to Use

1.  **Download:** Download the `index.html` file from this repository.
2.  **Open:** Open the file in any modern web browser (like Chrome, Firefox, or Edge).
3.  **Input Names:** Paste the list of EVE Online character names you want to check into the text area, with one name per line.
4.  **Fetch Stats:** Click the "Fetch Stats" button and wait for the tool to gather all the data.
5.  **Analyze & Filter:** Use the interactive controls to filter, highlight, and analyze the data as needed.

## 🔧 How It Works

The application is written entirely in vanilla JavaScript, HTML, and CSS and runs in your browser. The workflow is as follows:

1.  **Name Resolution**: The list of character names is sent to the ESI `/universe/ids/` endpoint to get unique character IDs.
2.  **Character & Corp Data**: For each character ID, the tool makes two more ESI calls:
    - It hits the `/characters/{id}/` endpoint to find the `corporation_id`.
    - It then hits the `/corporations/{id}/` endpoint to get the corporation name and logo URL. (This data is cached to avoid repeated lookups for the same corp).
3.  **Kill Statistics**: With the character ID, it calls the zKillboard API (`/api/stats/characterID/{id}/`) to get the kill data, broken down by month.
4.  **Render Table**: The application dynamically builds the HTML table with all the fetched data.
5.  **Interactive Filtering**: All filtering and highlighting is done client-side, making it instantaneous without needing to re-fetch any data.

---

This project is a standalone tool and is not affiliated with CCP Games or zKillboard.
