# Define Room website

A one-page website for **Define Room**, a digital marketing studio offering SEO, social media content, video editing, graphic design, websites, AI automation workflows, tracking and website audits.

The page is built to turn visitors into leads. Its main offer is a **free website audit**, requested through a short form that emails the request to the owner's Gmail.

It is plain HTML, CSS and JavaScript in a single file. There is no build step, framework or server code.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole website: content, styles and scripts |
| `logo.svg` | Full logo (mark + "define room" wordmark) for light backgrounds |
| `logo-on-dark.svg` | Full logo with white wordmark, for dark backgrounds |
| `logo-mark.svg` | The square mark on its own (social avatars, app icons) |
| `favicon.ico` | Browser tab icon (16, 32, 48 px) |
| `favicon.svg` | Sharp browser tab icon for modern browsers |
| `apple-touch-icon.png` | iPhone / iPad home screen icon (180 px) |
| `icon-192.png`, `icon-512.png` | Android home screen icons |
| `site.webmanifest` | Tells phones the site's name, icons and colours |
| `robots.txt` | Tells search engines and AI crawlers they may read the site |
| `llms.txt` | A plain-text summary of the business, services and prices for AI assistants |
| `_headers` | Caching rules Netlify applies to each file |
| `README.md` | This file |

Keep all files in the same folder. `index.html` links to the icons by file name.

## Page structure

The section order follows a conversion funnel: promise, proof, problem, offer, objections, then action.

1. **Navigation.** Logo, section links and a "Free audit" button. On phones the links move into a ☰ menu.
2. **Hero.** Headline "Get found, get followed, get booked." with the main call to action ("Get my free website audit"), plus the 1.8M+ Instagram views proof.
3. **Tools bar.** A scrolling row of the tools used (Google Search Console, GA4, Tag Manager, Meta Ads, Figma, Webflow, n8n and others).
4. **Problems and fixes.** Six common customer problems, each matched to a service.
5. **Services.** All eight services with "from" prices. Rows show a preview card on hover.
6. **Process.** Three steps: free audit, 30-day plan, ship and report.
7. **Pricing.** Three monthly plans, with Growth highlighted as "Most chosen".
8. **Testimonials and proof.** Three quotes, the 1.8M+ views banner and an FAQ.
9. **Lead form.** The free audit request form.
10. **Footer.** Contact email, links and copyright.

On phones a "Get my free website audit" button stays pinned to the bottom of the screen after the hero.

## Brand

**Logo.** A lime rounded square with four viewfinder corners framing a solid block, meaning "defining the room". The wordmark is lowercase **define** (bold) room (regular), set in Urbanist.

**Colours**

| Name | Hex | Use |
| --- | --- | --- |
| Lime | `#E3F25C` | Accent, hero panel, highlights |
| Ink | `#16181A` | Text, dark sections, buttons |
| White | `#FFFFFF` | Main page canvas |
| Soft | `#F4F4F1` | Cards and form background |
| Mist | `#EBEBE8` | Outer page frame |
| Clay | `#B8805A` | Secondary accent |
| Glacier | `#9FC4D6` | Secondary accent |

**Fonts** (Google Fonts): Urbanist for headings and body text, DM Mono for small labels and prices.

## Pricing

Prices are in INR, excluding GST and ad spend. They are estimates of typical Indian agency rates, not researched figures, so adjust them to suit.

**Monthly plans** (month to month, cancel with 30 days' notice)

- Starter: ₹14,999 / month
- Growth: ₹34,999 / month (highlighted)
- Scale: ₹69,999 / month

**Single services (starting prices)**

| Service | From |
| --- | --- |
| SEO | ₹12,999 / month |
| Social media content | ₹17,999 / month |
| Video editing | ₹1,499 per reel |
| Graphic design | ₹7,999 |
| Website design and build | ₹24,999 |
| AI automation workflows | ₹9,999 per workflow |
| Tracking and analytics | ₹7,999 |
| Website audit | ₹4,999 (first audit free) |

To change a price, search `index.html` for the old amount (for example `₹34,999`) and replace it.

## Search engines and AI assistants

The page carries structured data (schema markup) in a `<script type="application/ld+json">` block in the `<head>`. It describes:

- the business (`Organization` and `ProfessionalService`): name, description, email, logo and areas served
- each of the eight services with its starting price in INR
- the three monthly plans with their prices and what they include
- the FAQ (`FAQPage`)
- the website and page (`WebSite`, `WebPage`)

**When you change a price, a plan or an FAQ answer, change it in three places:** the visible page, the schema block in `index.html`, and `llms.txt`. Search engines can penalise structured data that doesn't match the page.

There are no reviews or star ratings in the schema on purpose. Add them only once there are real client reviews shown on the page.

To check the markup after deploying, paste the live address into [Google's Rich Results Test](https://search.google.com/test/rich-results) and the [Schema Markup Validator](https://validator.schema.org).

## Lead form

The form sends requests through **[Web3Forms](https://web3forms.com)**, a free form service. Requests arrive by email with the subject **"New Define room lead"**. Pressing reply in Gmail goes straight to the visitor.

The access key is set near the bottom of `index.html` in the line starting `var WEB3FORMS_KEY=`. It isn't repeated here. To use a different inbox, create a new key at web3forms.com with that email and replace the value.

### Spam and bot protection

- **hCaptcha.** An "I am human" check, loaded by the Web3Forms script.
- **Hidden trap fields.** Two invisible fields that people never see but bots tend to fill in.
- **Speed check.** A submission within 4 seconds of the page loading is treated as a bot.
- **Quiet blocking.** Bots caught by the trap fields or the speed check see a normal "thank you" but nothing is sent.
- **Field checks.**
  - **Name:** letters only, no links, no random keyboard mashing.
  - **Email:** must be a valid address and not from a throwaway service such as mailinator. Common typos (for example `gmail.conm` or `gmial.com`) show a "Did you mean …@gmail.com?" button.
  - **Website or Instagram:** optional and forgiving. It accepts a website, an @handle, an Instagram link or an email.
- **Rate limit.** One request per minute and three per hour from the same browser.

## Testing

The form behaves differently depending on how the page is opened.

| How it's opened | What happens |
| --- | --- |
| Double-clicking `index.html` on your computer (address starts with `file://`) | **Test mode.** The captcha is hidden and nothing is sent. Pressing Send checks the fields and shows "Not sent: test mode". |
| `localhost` or `127.0.0.1` | Test mode, same as above |
| A real website address (for example `yourname.netlify.app`) | Live. The captcha appears and requests are emailed. |

hCaptcha only works on a real website address, which is why test mode exists. If you see "invalid-data" in the captcha box, the page isn't on a hosted address.

The claude.ai preview can't load the captcha, so its form shows "The security check didn't load". Use the hosted site for real tests.

## Deploying with Netlify Drop (free)

1. Go to **app.netlify.com/drop** and sign up or log in (Gmail works).
2. Drag the whole **Define room** folder onto the page.
3. Netlify gives you a link such as `random-name.netlify.app`. Open it.
4. Fill in the form and press **Send me the audit**. The request should arrive in Gmail. Check the spam folder the first time.
5. Optional: in Netlify's site settings, rename the site or connect your own domain.

To update the site later, drag the folder onto the same site's **Deploys** page in Netlify.

## Still to do

- [ ] **Turn on hCaptcha in Web3Forms.** At app.web3forms.com, open the form's settings and set hCaptcha as the spam protection. This stops anyone getting round the captcha by sending data straight to Web3Forms.
- [ ] **Replace the sample testimonials.** The three quotes are placeholders and are marked "Sample: replace with a real client quote" on the page. Swap in real client quotes, names and businesses, then delete those labels.
- [ ] **Review prices and terms.** Check the plan prices, single-service prices and the month-to-month, 30-day notice terms against how you actually work.
- [ ] **Send one live test** from the hosted site and confirm it reaches Gmail.
- [ ] Optional: connect a custom domain and set up Google Search Console and GA4 for the live site.
- [ ] **After the domain is live:** add a canonical link, `og:url`, a 1200×630 share image (`og:image`), a `sitemap.xml` and the `Sitemap:` line in `robots.txt`, and make the schema URLs absolute.
- [ ] **Add social profiles** (Instagram and others) to the schema's `sameAs` list so Google and AI assistants can link the brand to them.
