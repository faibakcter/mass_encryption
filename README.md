## djparser

parse dj setlists from various formats

### install

```
npm install djparser
```

### usage

```javascript
const { parse } = require('djparser')

const setlist = parse(`
01. Artist - Track Name [Label]
02. Another Artist - Another Track
03. 128 BPM - Banging Tune (Original Mix)
`)

console.log(setlist)
// [
//   { pos: 1, artist: 'Artist', track: 'Track Name', label: 'Label' },
//   { pos: 2, artist: 'Another Artist', track: 'Another Track' },
//   { pos: 3, bpm: 128, track: 'Banging Tune', mix: 'Original Mix' }
// ]
```

### supported formats

- tracklist format (numbered)
- rekordbox export (xml)
- serato history (csv)
- traktor nml files

```javascript
// from rekordbox xml
const tracks = parse.rekordbox('playlist.xml')

// from serato csv
const tracks = parse.serato('history.csv')
```

### export

```javascript
const { export } = require('djparser')

export.markdown(tracks)
// outputs markdown table

export.reddit(tracks)
// reddit-friendly format

export.m3u(tracks, '/music/path/')
// m3u playlist
```

### cli

```bash
djparser convert setlist.txt --format markdown > output.md
djparser validate setlist.txt
djparser stats setlist.txt  # bpm analysis, key detection
```

MIT
