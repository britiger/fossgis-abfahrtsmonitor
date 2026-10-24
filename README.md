# FOSSGIS Abfahrtsmonitor

FOSSGIS live schedule displayed in the classic German train station departure display style.
Forked from https://github.com/tifa365/c3-abfahrtsmonitor for implement special needs for FOSSGIS.
<img width="1899" height="823" alt="CleanShot 2026-01-23 at 20 30 31" src="https://github.com/user-attachments/assets/79466644-d8b0-4c1b-979d-7bf29477aa0b" />

## Usage

Open `index.html` directly in a browser. No build steps required.

### URL Parameters

- `?only-day=<n>` - Show single day (0-indexed)
- `?only-track=<name>` - Filter by track (e.g., `SCI`, `Security`)
- `?only-room=<room>` - Filter by room (substring match)
- `?gen-delay=1` - Generate random delay for talks
- `?dev=<1|0>` - force view(`1`) or filter(`0`) old talks, based on local urls (localhost and 127.0.0.1) `dev` is `1`
- `?addDays=<days>` - Use old conference data, you can made a shift
- `?dayIndexStart=<0|1>` - Set day numbering of first day (Default: 1)

Parameters can be combined: `?only-day=1&only-track=SEC`

## Data Mapping

| Bahnhofstafel | CCC Schedule |
|---------------|--------------|
| Zeit (Time) | Talk start time |
| Zugnummer (Train ID) | Track code + talk ID (e.g., "SCI 12345") |
| Nach (Destination) | Talk title |
| Sprecher/Raum (Via) | Speakers, room name, end time |
| Gleis (Platform) | Room abbreviation |

## Styling

Uses the classic blue/yellow train station departure board colors:
- Navy blue (#000080) background
- Yellow (#FFFF00) headers
- White text on blue for departures
- Blue text on white for time cells

## Configuration and Data Sources

You can configure URLs, rooms and other functions in `config.js`. This configuration can be shared with https://github.com/gislars/fossgis-fahrplan-druck/

| Config value/function | description |
|-----------------------|-------------|
| `scheduleUrl`         | URL to current schedule from pretalx, fetch live |
| `scheduleUrlPrint`    | URL/File of printed schedule to calculate differences between to show cancaled |
| `pretixFreeUrl`       | URL to API for free space in e.g. Workshops |
| `widgetUrl`           | calculated from `scheduleUrl` or widget URL from pretalx |
