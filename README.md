# Gratitude Jar

**AppADay Day 158** | Category I, Interactive | Claude API: Yes

Live: https://augustineiacopelli.github.io/appaday-158-gratitude-jar/
Portfolio: https://augustineiacopelli.github.io/appaday/

Gratitude Jar is a place to drop short notes of thanks, 140 characters each, as often as you like. Each slip tumbles into a glass jar on screen. When the seventh slip lands, you can close the jar with your own reflection, and with an API key, Claude also reads the whole jar and answer with one warm, specific sentence naming the common thread that runs through it. The app works fully without a key.

## How it works

Type a slip and drop it in the jar. A live counter tracks the 140 character limit, and there is no daily limit: add as many slips as the day gives you, and a line under the entry shows how many you have added today. Dates are computed from local date parts, so they stay correct across time zones and daylight saving changes.

The jar is an inline SVG with seven stacked slots. Each slip lands with its own seeded tilt, falls in through the mouth of the jar with a short keyframe animation, and fades in instead when the device asks for reduced motion. Tap a slip, or focus it and press Enter, to read its full text and date.

The streak at the top counts consecutive days with at least one slip across the current jar, the queue, and every past jar. It counts back from today, or from yesterday if today has no slip yet, so the streak does not break before you have had the chance to write.

## The reflection

When the seventh slip finishes falling and an API key is saved, the app asks Claude (the Haiku tier from the portfolio config.json) for a single sentence. If the request fails, the jar stays full and a Retry button appears with the reason, and that waiting state survives a reload. Without a key, the full jar offers a box for your own reflection of up to 280 characters, left blank if you prefer, and a Begin a New Jar button; with a key, the same option sits under Retry as Begin a New Jar without Claude. Slips written while the jar waits go to a queue, and the button reads Save for the next jar.

Once Claude's reflection arrives, an optional box under it lets you add your own reflection beside it. Begin a New Jar then archives the jar with both reflections and its completion date and starts a fresh jar seeded from the queue.

## Past jars and settings

The jar button in the header opens Past jars, newest first. Each entry shows its date range, Claude's reflection, and your own reflection when you wrote one, and expands to show its seven slips.

The gear opens settings: your Anthropic API key with a show and hide toggle, an optional name that is sent to Claude with your slips, JSON export and validated import, and an erase option. Import and erase confirm in an in-app dialog.

## Data

Slips live in this browser's localStorage under `appaday-158-gratitude` as a versioned object holding the current jar, the queue, the archive, and the pending reflection state. The API key and name are stored under their own keys and are never included in an export. The key is sent only to the Anthropic API.

## Stack

One self-contained `index.html` in plain HTML, CSS, and vanilla JavaScript, with Fraunces and Caveat from Google Fonts. No libraries and no build step.
