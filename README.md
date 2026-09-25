# Green Island Guide (proof of concept)

A GPS-triggered audio tour of Green Island (Wunyami), Great Barrier Reef.
11 narrated boardwalk stops in English, Chinese and Japanese, a flora and fauna
field guide, island activities and visitor information.

**Live demo:** https://quicksilver-digital.github.io/green-island-guide/

- Open it on a phone and choose **Start tour with GPS** on the island, or
  **Try the demo walk** anywhere for a simulated walk.
- Narration uses the device's built-in voice. A production app would use
  recorded voiceover.
- Some content is draft and marked as such in the app, including the Wunyami
  stop, which is a placeholder pending work with Gunggandji Traditional Owners.

Content: Queensland Parks and Wildlife Service, green-island.com.au.
Map data © OpenStreetMap contributors (ODbL).

## Editing content

Open **https://quicksilver-digital.github.io/green-island-guide/admin/** and choose
**Sign In Using Access Token**. You need a GitHub token with write access to this
repo (see below). Each save is a commit to `main`; the live site updates about a
minute later.

What's editable: the tour stops (titles, narration in three languages, optional
recorded audio per language, photo, map position, "look for" species), flora and
fauna entries, map places, activities, the Info tab, the welcome text and
acknowledgement, and the stop trigger radius.

**Token:** GitHub → Settings → Developer settings → Fine-grained tokens → Generate.
Resource owner *Quicksilver-Digital*, repository access *Only select repositories →
green-island-guide*, permission **Contents: Read and write**. Nothing else.

## How it fits together

- `index.html`: the app. It loads `content/*.json` at runtime and has a copy of the
  content baked in for offline use.
- `content/`: everything the CMS edits.
- `media/`: uploaded photos and audio.
- `admin/`: Sveltia CMS 0.221.0 (MIT), vendored and pinned, with a Content Security
  Policy that only allows GitHub's API and the CMS's own pinned resources.

No build step or workflows run in this repo.
