# Product

## Register

product

## Users

Independent foreign travelers (backpackers, motorbike riders, small groups) staying at or considering Hoa An Hotel in Cao Bang, Vietnam. They are mid-trip, on a phone, often on hotel wifi or spotty mobile data. Their jobs: check rooms and prices, rent a motorbike, plan the Ban Gioc waterfall trip, catch the right local bus, find food, and build a day-by-day itinerary — then confirm everything over WhatsApp.

Secondary user: the hotel owner/staff maintaining content through the internal tools (editor.html, pick-coords.html, itinerary builder).

## Product Purpose

The guest-services hub for Hoa An Hotel. It exists to (1) win direct bookings via WhatsApp instead of paying OTA commissions, and (2) let guests self-serve travel logistics that reception would otherwise repeat all day (bus routes, motorbike rules, tour options, food spots). Success = WhatsApp conversations started and guests getting practical answers without asking.

## Brand Personality

Adventurous · local · pragmatic. The voice of a knowledgeable local host: direct, concrete, generous with real detail — actual prices in VND, departure times, road conditions, pitfalls to avoid. Warm but never fancy; helpful over polished.

## Anti-references

- **5-star luxury resort aesthetics.** No gold-accent spa minimalism or distant elegance. This is a highland guesthouse; authenticity is the asset.
- **Generic OTA templates (Booking.com-style).** No listing-card walls, discount badges, urgency banners, or star-rating clutter.
- **AI-slop landing patterns.** No gradient text, identical icon-card grids, tiny uppercase tracked eyebrows over every section, or emoji-as-decoration watermarks (some legacy pages still carry these — remove when touched).

## Design Principles

1. **Answer first.** Every page leads with the traveler's question answered (price, time, route, how-to) before any storytelling.
2. **Real place, real photos.** Actual photos of the hotel, roads, buses, and food. Never decorative stock or colored-box placeholders.
3. **Built for the road.** Mobile-first, one-hand reach, fast on weak networks, tap targets ≥44px, readable in bright sunlight (high contrast).
4. **One action per page.** The WhatsApp CTA is the single conversion. Keep it visible; never stack competing CTAs.
5. **Same vocabulary everywhere.** One shared token set and component language across all pages. Tokens currently drift between pages (fonts, orange values, creams) — converge toward one system rather than forking further.

## Accessibility & Inclusion

- Target WCAG 2.1 AA. Body text contrast ≥4.5:1 (watch muted grays on cream backgrounds).
- Preserve and extend the existing patterns from index.html on every page: skip link, `:focus-visible` rings, `prefers-reduced-motion` fallback.
- Plain English for non-native speakers; short sentences, concrete words.
- Touch-first: 44px minimum targets, safe-area insets on mobile.
