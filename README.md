# Oggy: product case study

> _Live it today, tell it tomorrow._

Oggy is a social iOS app I'm designing and building. This repository documents the **product thinking** behind it: the concept, the rules, and the decisions that shaped them. The code lives in a private repository while the app is in development.

## The concept

During the day you capture moments **live**: photos, short videos and full-screen text, using only the in-app camera, with no uploads from the camera roll. At midnight your day closes. The next day your friends scroll through it with music and a large animated **clock** showing the exact time of each moment. You keep every day forever in your Memories.

## Key product decisions

| Topic | Decision | Why |
|---|---|---|
| Content | Photo, video (max 15 s), full-screen text, **live only** | Authenticity is the product. Curated camera-roll posts are what other apps already do. |
| Timestamps | Exact capture time + time zone, checked by the server against arrival time | The clock is the core experience, so the time has to be trustworthy. |
| End of day | The **author's** midnight, no additions afterwards | A day is a closed story. Each person's day follows their own time zone. |
| Publishing | Only the **next day**, once. In the morning you pick a clock style, remove moments, publish | One deliberate editing step, instead of constant posting pressure during the day. |
| Unpublished days | Stay private in your Memories | Capturing never forces sharing. |
| Visibility | Friends see your day only on the following day, until the next midnight | Content is ephemeral for others and permanent for you. |
| Social graph | Friends only, mutual requests | A small, trusted audience. |
| Tags | On single moments, with consent (accept / reject / remove) | People control what ends up in their own Memories. |
| UI text | No redundant labels: name and date only on the intro screen | Every pixel goes to the content. |

## Experience design

- **Feed:** vertical scroll. Each person opens with an intro screen (name + date), then their moments play automatically while the clock rewinds to 00:00 and runs through the day. Progress bars are **vertical, stacked on the right edge**, one per moment.
- **Clock styles:** the author picks one per day (Newspaper, Poster, Split-flap, iOS), and everyone sees that day in that style. Styles are independent modules with a fixed contract, so adding a style means adding one module and nothing else.
- **Capture:** tap for a photo, hold for a video (a ring fills up to 15 s), "Aa" for full-screen text.

## Privacy and trust by design

- The rule of "who can see what" lives in **one authorization module**, covered by tests.
- Media files are private, served only through short-lived signed links.
- Location metadata (EXIF/GPS) is stripped from every photo and video on the server.
- Deleting your account deletes your data, including local data on the phone.

## Roadmap

1. ✅ iOS feed prototype + server skeleton
2. ✅ Camera and "Today", with real uploads, offline queue and live preview
3. 🟡 Backend: Sign in with Apple, sessions, media processing done · friendships next
4. ✅ Memories, day management, style choice, publishing, real friends feed
5. ⬜ Music (one track across several moments, optional beat-synced cuts)
6. ⬜ Server-side video export of one or more days
7. ⬜ Tags in Memories
8. ⬜ TestFlight with friends

## My role

Product definition (concept, rules and trade-offs above), UX, iOS app (SwiftUI), backend and infrastructure (Postgres, Redis, S3-compatible storage, Docker).
