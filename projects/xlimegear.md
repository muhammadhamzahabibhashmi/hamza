# XLIME GEAR

**Status:** design prototype, not deployed
**Repository:** private
**Role:** UI design, design system, prototype packaging

![XLIME GEAR custom jersey builder](../assets/screenshots/xlimegear-jersey-builder.png)

## What it covers

XLIME GEAR is a custom football kit brand. Teams design their own strip, order in bulk, and it gets made. The prototype runs that whole journey across thirteen screens.

The storefront side is home, shop all in two layouts, and the football kit detail page. Customisation is the builder. Ordering covers cart, checkout, two versions of team bulk orders and the team request form. Then there's a customer account, and an admin pair for the order list and an individual order.

It's design and front end rather than a running application. The screens are real HTML sitting on a working set of tokens, built so a client could sign the direction off before anybody wired it to a database.

## The builder

This is the part that sells the product, so it got the most attention.

It moves through four stages, kit then colours then crest then details, with progress visible the whole way and a large view of the current configuration filling the left of the screen. Colour selection separates the primary from the trim and accents, because for a team those are two different arguments and merging them into one palette makes both of them harder to have. The crest is an upload with formats and size limit stated before you try, rather than after you've failed.

The last step is where this stops behaving like a normal shop. The button says Review & Quote, not Add to cart. Kit for a club gets priced against quantity, print, how complicated the crest is and when they need it, so the builder finishes by sending a quote request with the unit count attached. Stock items over on the ordinary shop side keep a real cart and checkout.

## The system underneath

Dark, high contrast, and one acid green doing all of the signalling. Condensed display type for headings against a neutral sans for everything else, which is most of what gives it the sports feel without needing decoration on top.

Colours are defined as semantic tokens, surface and surface elevated and surface container and on-surface and primary container and the rest, extended into the Tailwind config rather than written inline. The admin screens and the storefront therefore share one definition, and moving the accent moves it across all thirteen at once.

## Getting it to the client

The client needed to look at thirteen screens, and asking them to install Node in order to do that was never going to happen.

So what got delivered is one HTML file. A landing page, a card per screen, and a viewer that runs each original page live inside a device frame instead of showing a picture of it. Every source file sits embedded whole next to its screenshot. Nothing stripped, nothing minified, nothing rewritten to make it fit.

A script does the embedding, and a second pass decodes each embedded page back out and byte-compares it against the file it came from before the thing counts as finished. All thirteen matched. Then it gets rendered and clicked through, which is how two problems in the shell itself turned up: long filenames pushing out of their cards, and the device frames losing their proportions inside a flex container.

## Stack

HTML · Tailwind · semantic design tokens · Barlow Condensed, Manrope and Space Grotesk · Material Symbols · Node.js packaging and verification script
