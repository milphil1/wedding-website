# Wedding Website PRD — Current Site

**Status:** As-built product requirements for the live prototype  
**Last reviewed:** 28 October 2026  
**Live site:** https://milphil1.github.io/wedding-website/  
**Repository:** https://github.com/milphil1/wedding-website

This document describes the website as it exists today. It replaces the earlier PRD wherever the two differ. Event details are fictional sample content.

## 1. Purpose

Provide guests with a welcoming, mobile-friendly place to find the wedding details, locate the venue, plan a journey, review nearby accommodation, and RSVP. The site is a public, single-page website published with GitHub Pages.

## 2. Audience and goals

### Guests

Guests should be able to:

- Quickly find the date, venue, schedule, dress guidance, parking note, and RSVP deadline.
- Get directions to Dorfold and view its location on an embedded map.
- Estimate a driving journey from their UK postcode or open public-transport directions in Google Maps.
- Review nearby places to stay.
- Submit an RSVP for their group using the embedded Google Form.

### Hosts

Hosts should be able to:

- Receive form responses in the Google Sheet linked to the RSVP form.
- Direct guests to the contact email for questions or RSVP corrections.

## 3. Event information

- **Couple:** Molly and Russell
- **Date:** Saturday, 5 June 2027
- **Venue:** The Walled Garden at Dorfold, Chester Road, Nantwich, Cheshire, CW5 8LD, England
- **Arrival:** Guests are welcome from 4:00 pm and should arrive by 4:30 pm.
- **Food:** 5:30 pm
- **Cake and dancing:** 7:30 pm
- **End:** Midnight
- **Dress guidance:** Garden-party clothing; grass and gravel make flats or block heels practical.
- **Parking:** Limited parking is available on site; guests are encouraged to share a lift where possible.
- **RSVP deadline:** 2 April 2027
- **Contact:** mollyandrussell@gmail.com

## 4. Page structure and behavior

The site is one responsive page with anchor navigation in this order:

1. **Prototype banner:** A static banner at the top of the page, labelled “Prototype.”
2. **Header/navigation:** Couple’s names and links to the page sections. On small screens, navigation collapses behind a menu button.
3. **Hero:** Centered couple’s names, invitation copy, event date, RSVP button, and secondary link to event details. Wildflower and drink photographs sit beside the title on larger screens and below the text on small screens.
4. **Ticker:** A short strip highlighting food, garden flowers, dancing, and guests.
5. **A little note:** Welcome copy and a circular sunset photograph.
6. **A day in the garden:** Venue atmosphere photograph, schedule, dress guidance, and parking information.
7. **Location:** Dorfold address, embedded Google Map, and a link to Google Maps directions.
8. **Getting to the garden:** Postcode-based route tool for car or public transport.
9. **Places to stay nearby:** Four hotel suggestions with approximate distances and links.
10. **RSVP:** Deadline, group guidance, contact details, and embedded Google Form.
11. **Footer:** Date, venue, contact email, and photo note.

### Hero copy

- “Celebrate our wedding!”
- “Time for good food and dancing in the walled garden.”

### Accommodation suggestions

- The Cheshire Cat
- The Crown Hotel
- Premier Inn Crewe (Nantwich)
- Rookery Hall Hotel & Spa

Distances shown are approximate straight-line distances from the venue postcode. Guests should check driving or taxi distances when booking.

## 5. RSVP and data handling

The RSVP section embeds a Google Form. Guests can submit one response for a group of up to four adults total, including the person replying. The site advises that children cannot be accommodated, highlights the 2 April 2027 deadline, and provides the host email for corrections.

The form collects contact details and guest response information, including attendance and dietary needs, and includes a song-request field. The form is linked to a private Google response Sheet. The Google Form controls its questions, validation, and confirmation behavior; the website does not process or store form submissions itself.

The form is published for anyone with its link to respond. The website and RSVP section are public and do not require a password.

### Data-flow and scope notes

- The current implementation does not include a custom RSVP backend.
- The original requirements for one spreadsheet row per guest, group response IDs, custom email confirmations, and custom duplicate-submission handling are not implemented by the website. Google Forms and its linked Sheet determine the response format and any form-level confirmation.
- The private response Sheet must remain private; only the form is public to respondents.

## 6. Travel tool

Guests enter a UK postcode and choose a travel mode.

- **Car:** The browser looks up the postcode with Postcodes.io, then requests a driving route from OSRM. The page displays an approximate journey time and distance to Dorfold. It does not include live traffic.
- **Public transport:** The page opens Google Maps directions in a new tab. Route details and journey time are provided by Google Maps, not displayed as an in-page estimate.
- The page explains that the postcode is sent to these services for the selected route calculation and includes OpenStreetMap/OSRM attribution for driving routes.

The tool depends on the availability of the external postcode, routing, and mapping services.

## 7. Visual and interaction requirements

- Keep the original six-colour palette:
  - Cosmic Latte `#F4F0D0`
  - Crimson Ink `#8D162A`
  - Dusty Rose `#E8AEB1`
  - Neon Pear `#C0B331`
  - Burnt Sienna `#F37221`
  - Arctic Blue `#B8D0E5`
- Use a refined serif for display headings and a readable sans-serif for navigation, body copy, controls, and supporting details.
- Use supplied garden, drinks, and sunset photographs as decorative imagery. They are not presented as verified photographs of the venue or couple.
- Preserve clear contrast, labelled form controls, keyboard-operable navigation, a responsive layout, and comfortable touch targets.
- Keep the hero spacing and image arrangement responsive across desktop, tablet, and mobile.

## 8. Hosting and access

- Host the static page on GitHub Pages from the repository’s `main` branch and root folder.
- Public URL: https://milphil1.github.io/wedding-website/
- The page is intentionally public and carries a visible “Prototype” label.
- The RSVP response Sheet remains private. No Google Sheet credentials are placed in the website code.

## 9. Current acceptance criteria

The current site meets its intended prototype scope when:

- The public page loads and presents the event information in the sections listed above.
- Navigation works by section links on desktop and by the collapsible menu on small screens.
- The venue address, embedded map, and directions link identify Dorfold in Nantwich.
- The route tool accepts a UK postcode and offers car and public-transport options, with the service limitations explained.
- The accommodation cards link to hotel information and directions.
- The RSVP form is embedded, publicly reachable, capped at four adults per group according to its current setup, and linked to the private response Sheet.
- The layout remains readable and usable on mobile.

## 10. Known limitations and future decisions

These items are not requirements of the current prototype unless the hosts request them later:

- Add password protection to the website.
- Replace Google Forms with a custom form or server-side RSVP service.
- Guarantee one response row per guest, response IDs, custom confirmation emails, or custom duplicate detection.
- Display public-transport travel times directly inside the page.
- Use live traffic in driving estimates.
- Validate hotel availability, room rates, or travel times automatically.

Before using the site for a real event, the hosts should confirm the event details, RSVP form questions and access settings, the linked Sheet’s privacy, and image permissions.