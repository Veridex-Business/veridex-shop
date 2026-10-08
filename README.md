# Veridex Prints — shop page (first draft)

This folder is a one-page shop website. Open `index.html` in any web browser to see it.

- `index.html` — the whole page (text, colours and layout all in this one file)
- `images/` — the pictures. The `.svg` files in there are placeholders that say "Your photo here".
- `preview-desktop.png`, `preview-mobile.png` — screenshots of the draft

To edit, open `index.html` in a plain text editor (for example VS Code or Notepad), make the change, save, and refresh the browser.

## Not live yet

The page isn't selling anything yet. Prices show `€—` and every Buy button is greyed out and says "Coming soon". Keep it like that until the **Terms of sale, Returns & refunds and Privacy** pages are written.

## 1. Change the shop name (and email, Instagram, maker details)

"Veridex Prints" is only a placeholder. Near the top of `index.html` there's a block marked **SHOP SETTINGS: EDIT HERE**:

```js
window.SHOP = {
  name: "Veridex Prints",
  email: "hello@example.com",
  instagram: "veridexprints",
  makerName: "[Maker name]",
  makerAddress: "[Street, Town, County, Eircode], Ireland",
  salesOpen: false
};
```

Change the text inside the quotes and save. The page fills these into the logo, page title, contact section and footer.
Tip: also search the file for `Veridex Prints`, `hello@example.com` and `veridexprints` and replace those too. That way the right name still shows if a browser has scripts turned off, and in Google search results.

Once the real details are in, remove the small yellow "PLACEHOLDER", "TO DO" and "CONFIRM…" labels (search for `class="ph"`).

The maker name and postal address in the footer are needed for EU product-safety labelling. Use the business's real trading name and address.

## 2. Swap in your photos

1. Take or pick a photo for each product. Landscape photos (4:3) work best for products. Portrait photos (4:5) work best for the big top-of-page photo.
2. Copy them into the `images/` folder, e.g. `images/topper-name.jpg`.
3. In `index.html`, find the matching line and change the file name, e.g.
   `src="images/topper-name.svg"` → `src="images/topper-name.jpg"`.
4. Update the `alt="..."` text next to it so it describes the photo (this is for screen readers and Google).

| Placeholder file | Where it shows |
|---|---|
| `images/hero.svg` | Big photo at the top |
| `images/topper-name.svg` | Name cake topper card |
| `images/topper-age.svg` | Age / number topper card |
| `images/topper-birthday.svg` | Happy Birthday topper card |
| `images/topper-wedding.svg` | Wedding / Mr & Mrs card |
| `images/cupcake-set.svg` | Cupcake toppers set card |
| `images/other-prints.svg` | Other 3D prints card |

Photos are shown in their true colours, with no filter. Keep photos under about 500 KB each so the page loads quickly. Exporting at about 1200 px wide is plenty.

## 3. Set prices and product details

Each product is an `<article class="panel card">` block, with a comment above it like `<!-- CARD 1: Name cake topper -->`. In each one:

- **Price:** change `€—` to the price, e.g. `€12`. You can delete the `<small>PRICE COMING SOON</small>` part, or change it to something like `<small>FROM</small>`.
- **Size and other specs:** replace `[—]` in the spec rows with real numbers.
- **Text:** edit the title (`<h3>`) and description.
- Leave the pink "Single use. Remove before eating." note on every cake topper card.

To add another product, copy a whole `<article> … </article>` block and edit the copy. To remove one, delete its block.

Colours: the colour dots are in the "Colours & materials" section. Edit the names and the colour codes (e.g. `#ff8fc7`) to match the filament you actually have.

## 4. Paste Stripe payment links (only when you're ready to sell)

1. In Stripe, create a **Payment Link** for each product. It looks like `https://buy.stripe.com/...`.
2. In `index.html`, find that product's Buy button. It looks like this:
   ```html
   <button class="btn btn-pink buy" type="button" data-stripe-link="" disabled aria-disabled="true">Coming soon</button>
   ```
   Paste the link between the empty quotes: `data-stripe-link="https://buy.stripe.com/..."`.
   Leave everything else as it is.
3. When the Terms, Returns and Privacy pages are done and linked in the footer, set `salesOpen: true` in the SHOP SETTINGS block.

Buttons that have a link then turn into "Buy now" and go to Stripe. Buttons with no link stay "Coming soon".

## 5. Terms, Returns and Privacy links

In the footer, the three links point to `#` for now. When the pages exist (e.g. `terms.html`, `returns.html`, `privacy.html` in this folder), change `href="#"` to the page name and remove the "TO DO" labels.

## Other notes

- Add `?static` to the end of the address (e.g. `index.html?static`) to turn off the scroll animations. This is handy for screenshots.
- The page loads its fonts (Google Fonts) and icons (lucide) from the internet, so it needs a connection to look right.
- "Food-safe PLA": keep a copy of your filament maker's food-contact statement for the exact filament you use, to back up this claim.
- The original HALFTONE template file wasn't available when this draft was made. The look was rebuilt in the same style: paper colours, Fraunces and Manrope fonts, the pink "misprint" words and the stacking sections.
