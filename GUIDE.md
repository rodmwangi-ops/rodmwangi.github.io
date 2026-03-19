# Rod's Guide to Maintaining This Site

This guide is for you. It explains how every part of the site works, how to update it, and what you need to know about the code. No prior coding experience assumed.

---

## How Websites Work (The 30-Second Version)

Your portfolio is made of files that a browser reads and displays. There are three types of files that matter:

**HTML files** (.html) are the *structure* of the page. They tell the browser what content exists and in what order. Think of HTML as the blueprint of a building: it says "there's a heading here, a paragraph there, an image over there." If you open index.html in a text editor, you'll see tags like `<h1>`, `<p>`, `<img>` which are instructions the browser follows.

**CSS** (Cascading Style Sheets) is the *appearance*. It controls colors, fonts, spacing, and layout. In your site, all the CSS lives inside the `<style>` tag at the top of index.html. CSS uses a pattern: you name a thing (like `.hero`), then list how it should look inside curly braces `{ }`. When you see `color: #4A6741;` that's saying "this text should be this shade of green."

**JavaScript** (.js) is the *behavior*. It makes things interactive: animations on scroll, loading writing pieces from files, the mobile menu toggle. In your site, all JavaScript lives inside the `<script>` tag at the bottom of index.html.

**JSON files** (.json) are structured *data*. Your writings.json is a list of writing pieces with their titles, dates, and file names. JSON is like a neatly organized address book. It uses square brackets `[ ]` for lists and curly braces `{ }` for individual entries.

**Markdown files** (.md) are *plain text with simple formatting*. Your writing pieces are in Markdown. A heading starts with `#`. Bold text uses `**bold**`. Paragraphs are separated by blank lines. This file you're reading right now is Markdown.

---

## File Structure

```
your-repo/
  index.html            Main portfolio page
  writing.html          Writing section page
  Rod_Parsley_Mwangi_CV.pdf   Your downloadable CV
  GUIDE.md              This file (your reference)
  README.md             GitHub repo description
  images/               All photos and images
    hero-farm.jpg         Hero background (onion field, Kajiado)
    rod-farm.jpg          You laying drip irrigation
    rod-speaking.jpg      B&W speaking photo (podium)
    rod-presenting.jpg    Front-facing speaking photo
    farm-panorama.jpg     Wide farm overview
    farm-seedlings.jpg    Onion seedling rows
    farm-golden.jpg       Golden hour farm shot
    farm-greens.jpg       Leafy greens/diverse crops
    farm-early.jpg        Early stage drip setup
    onion-harvest.jpg     Harvested red onions
    church-keys.jpg       Keyboard/church volunteer
    cert-best-speaker.jpg NKMAU certificate
    cert-electoral.jpg    Electoral Commission certificate
  writings/             Writing pieces
    writings.json         Master list of all writing
    cautious-optimist.md  
    trip-home.md          
    without-fear.md       
    dear-mr-ms-a.md       
    china-africa.md       
```

---

## How to Update Specific Things

### Change Text on the Main Page

1. Open `index.html` in any text editor (VS Code, Notepad, GitHub's editor)
2. Search for the text you want to change
3. The file has big comment blocks like `<!-- HERO -->` that mark each section
4. Edit the text between the HTML tags
5. Save and commit

Example: To change your tagline, find:
```html
<p class="hero-tagline">I take systems that don't work for people...</p>
```
Change the text between `>` and `</p>`.

### Add a New Project/Work Entry

1. Open `index.html`
2. Find the `<!-- WORK / PROJECTS -->` section
3. Copy one of the existing `work-card` blocks
4. Paste it where you want it to appear
5. Change the title, description, type, tags

Here's a blank template you can copy:
```html
<div class="work-card accent-green reveal">
    <div class="work-type type-green">YOUR CATEGORY</div>
    <h3>Your Project Title</h3>
    <p>Description of what you did and why it matters.</p>
    <div class="work-tags">
        <span class="tag tag-green">Tag 1</span>
        <span class="tag tag-green">Tag 2</span>
    </div>
</div>
```

For farm/tech projects, use `accent-earth`, `type-earth`, and `tag-earth` instead of the green versions.

### Add a New Writing Piece

This is the easiest update because it uses the JSON + Markdown system:

1. Write your piece and save it as a `.md` file in the `writings/` folder
   (e.g., `writings/my-new-piece.md`)

2. Open `writings/writings.json` and add a new entry:
```json
{
    "id": "my-new-piece",
    "title": "The Title of Your Piece",
    "genre": "Essay",
    "date": "2026",
    "context": "Written for...",
    "excerpt": "The first line or a teaser...",
    "file": "my-new-piece.md",
    "format": "prose"
}
```
Put a comma after the previous entry's closing `}` before adding yours.

3. Optionally, add a preview card on the main page in the writing section (index.html). Find the `writing-grid` and copy one of the `wp-card` blocks.

**format** can be `"prose"` (normal paragraphs) or `"verse"` (poetry, preserves line breaks).

### Change a Photo

1. Resize your new photo to a reasonable web size (1200-1920px wide for landscapes, 800px wide for portraits)
2. Save it in the `images/` folder
3. In index.html, find the `src="images/old-name.jpg"` and change it to your new file name

For the hero background, find this line:
```css
background: url('images/hero-farm.jpg') center/cover no-repeat;
```
Change `hero-farm.jpg` to your new image name.

### Add a New Video

Find the media section and copy one `media-card` block. The key things to change:
- The YouTube URL in the `href`
- The thumbnail URL: replace the video ID in `img.youtube.com/vi/VIDEO_ID/hqdefault.jpg`
- The title and description

### Update Your CV

Replace the `Rod_Parsley_Mwangi_CV.pdf` file with your updated version. Keep the same file name, or change it in both places it's referenced in index.html (search for the filename).

### Change Colors

All colors are defined at the very top of the CSS in `index.html` inside `:root { }`. Each variable has a comment explaining what it's used for. Change a value there and it updates everywhere on the site.

### Update Education (When UW Enrollment is Confirmed)

Find the education section. The UW card has class `edu-upcoming`. When you enroll, you can:
- Remove the `edu-badge` element (the "Fall 2026" tag)
- Remove the `edu-upcoming` class
- Add graduation details to the `.details` line

---

## Design Philosophy

The site is built around your identity: connecting things that aren't supposed to go together. The design choices reflect this:

**Colors come from the land.** The palette is derived from your Kajiado farm photos: soil black, onion-shoot green, dry-grass amber, parchment white. These aren't arbitrary design choices; they ground the site in the place where your work happens.

**Typography is editorial.** Cormorant Garamond (the serif heading font) comes from magazine and literary design. DM Sans (the body font) is clean and modern. Together they say: this person writes carefully and thinks clearly.

**Photography does the heavy lifting.** The hero is a full-width farm landscape, not a headshot. The photo strip shows the farm across seasons. This immediately signals that your story is different from the typical policy researcher's.

**Green = policy/research work. Brown/earth = farm/tech/building work.** This color coding runs through the tags, labels, and accents. It's subtle but it reinforces the two worlds your work spans.

**No em dashes.** Anywhere. Ever.

---

## Deploying to GitHub Pages

1. Create a repository on GitHub (e.g., `rodmwangi.github.io`)
2. Push all these files to the `main` branch
3. Go to Settings > Pages > Source: Deploy from branch > `main` > `/ (root)`
4. Your site will be live at `https://rodmwangi.github.io`

### Adding a Custom Domain

1. Buy a domain (e.g., rodmwangi.com) from Porkbun, Namecheap, or Cloudflare
2. In your domain registrar, add these DNS records:
   - A record: `185.199.108.153`
   - A record: `185.199.109.153`
   - A record: `185.199.110.153`
   - A record: `185.199.111.153`
   - CNAME record: `www` pointing to `rodmwangi.github.io`
3. In your GitHub repo, go to Settings > Pages > Custom domain
4. Type your domain and save
5. Check "Enforce HTTPS"

GitHub will create a `CNAME` file in your repo automatically.

---

## Common Coding Patterns You'll See

**HTML tags** come in pairs: `<h1>text</h1>`. The first is the opening tag, the second (with `/`) is the closing tag. Everything between them is the content.

**CSS classes** are labels you put on HTML elements. `class="work-card accent-green"` means this element has two classes. In the CSS, `.work-card` defines how all work cards look, and `.accent-green` adds the green accent.

**CSS variables** are reusable values. `var(--shoot)` means "use the value defined in --shoot." This is why changing a color in `:root` updates it everywhere.

**The reveal animation** works by: (1) elements start invisible (opacity: 0, shifted down 20px), (2) JavaScript watches for them to enter the viewport, (3) when they do, it adds the class "visible" which triggers the CSS transition to opacity: 1 and no shift.

**The writing page** loads writings.json to build the list, then when you click a piece, it fetches the .md file and converts it to HTML. This means you never have to edit writing.html to add new pieces.

---

## Things to Add Later

- **Blog posts**: The writings system already supports dated entries. You could add a "blog" section that shows recent pieces sorted by date.
- **Farm photo gallery**: A dedicated page with all farm photos, organized by season.
- **Project case studies**: Individual pages for major projects (like the GBA+ study) with deeper detail.
- **Screenshot/demo section**: When you have sanitized screenshots of the Farm PWA and AI chatbot.
- **RSS feed**: If you start blogging regularly, an RSS feed lets people subscribe.

---

## Getting Help

If something breaks:
1. Check that all file names match exactly (capitalization matters)
2. Make sure JSON entries have commas between them (but not after the last one)
3. Open your browser's developer tools (F12) and check the Console tab for errors
4. Compare your changes against the original file to spot what's different

If you're stuck, you know where to find me.
