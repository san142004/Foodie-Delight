# Foodie Delight — Project Context

## Overview

Foodie Delight is a small, browser-based food ordering demo. Visitors can browse a menu, add food to a cart, and preview a receipt at checkout. The site is built with plain HTML, CSS, and JavaScript; there is no build step or backend.

## Project files

| Path | Purpose |
| --- | --- |
| `index.html` | Home page with a hero, popular categories, and three featured foods. |
| `menu.html` | Full menu with category filters for pizza, burgers, and sandwiches. |
| `about.html` | Restaurant story, mission, ingredients, and chefs. |
| `contact.html` | Contact details, opening hours, and a message form. |
| `style.css` | Shared layout, components, cart and receipt modal styles, and responsive rules. |
| `script.js` | Food catalog, menu rendering, cart, checkout, receipt, and contact form behavior. |
| `img/` | Local logo, backgrounds, category images, and food photos. |
| `.vscode/settings.json` | Live Server port set to `5501`. |

Each page includes the same navigation, footer, cart modal, stylesheet, and script. Icons use Font Awesome 6.4.0 from a CDN, so they need an internet connection to load.

## How to run

Open `index.html` in a browser, or serve the folder with a static server such as VS Code Live Server. No package manager, installation, or environment variables are required. If using Live Server, this repository configures port `5501`.

## Current behavior and data

- `foodData` in `script.js` defines six products with an ID, name, dollar price, category, image path, and description. The first three appear on the home page; all six appear on the menu page.
- Menu filter buttons render products from the selected category.
- Cart controls add or remove products and change quantities. The cart is saved in browser `localStorage` under `cart`.
- Checkout stores an order with items, total, and timestamp under `orders`, clears the cart, and shows a receipt preview. The receipt can be downloaded as a text file. The PDF button opens the browser print dialog, where a user can save as PDF.
- Contact form submissions are stored locally under `contactMessages` and show a confirmation alert.

## Implementation notes

- This is a front-end demo: checkout does not take payment or send an order to a restaurant, and contact messages are not emailed. All saved data remains in the current browser's local storage.
- The initial `DOMContentLoaded` handler calls `displayFeaturedFoods()` on every page, but `#featuredFoods` exists only on `index.html`. This causes a JavaScript error on the other pages before that handler attaches its checkout listener. The separate page-specific handlers still initialize their own page features.
- Product data lives in `script.js`. Shared navigation and footer markup are repeated in each HTML page, so update all four pages when changing those sections.

## Quick manual check

Open the home page, add a featured item, and confirm the cart count and total. Use checkout on the home page to preview and download a receipt. Visit the menu page and test each category filter. Reload a page to confirm cart persistence. Submit the contact form and check for its confirmation alert.
