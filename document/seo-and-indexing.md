# SEO & Search Engine Indexing Guide

This guide covers how the site's SEO and indexing are configured and the exact steps you need to take to submit your site (`https://harinikeshr.dev`) to Google and Bing.

---

## 1. What Has Been Configured in Code

1. **Custom Domain & Base URL:**
   - Base URL is set to `https://harinikeshr.dev/`.
   - All canonical links (`<link rel="canonical">`) and OpenGraph/Twitter URLs point to your custom domain.

2. **Robots.txt (`mysite/layouts/robots.txt`):**
   - Configured to allow all search engine crawlers (`Allow: /`).
   - Declares the sitemap location: `https://harinikeshr.dev/sitemap.xml`.

3. **XML Sitemap (`https://harinikeshr.dev/sitemap.xml`):**
   - Generated automatically with all published pages, articles, talks, and projects.
   - Low-value taxonomy pages are excluded to prevent duplicate or thin-content penalties.

4. **Structured Data (Schema.org / JSON-LD):**
   - **Homepage:** `WebSite` and `Person` schema with description and linked profiles.
   - **Articles & Posts:** `Article` schema with author, datePublished, dateModified, and tags.
   - **Breadcrumbs:** Structured breadcrumbs list.

5. **OpenGraph & Twitter Card Metadata:**
   - Meta title, description, and keywords configured.
   - Social preview image set to your profile photo (`images/profile_speaker_image.png`).
   - Author profile identity linked via `<link rel="me">` for LinkedIn and GitHub.

6. **In-Site Search Index (`index.json`):**
   - Fuse.js search index automatically built on every build for instantaneous client-side search.

---

## 2. What You Need To Do (Action Checklist)

### Step 1: Submit to Google Search Console (Crucial for Google Indexing)

1. Go to [Google Search Console](https://search.google.com/search-console).
2. Sign in with your Google account.
3. Click **Add Property**.
4. You will see two options:
   - **Option A (Recommended) — Domain verification:**
     - Enter `harinikeshr.dev`.
     - Google will give you a **TXT record** (e.g. `google-site-verification=XXXXX`).
     - Go to your domain registrar / DNS provider (Namecheap, Cloudflare, GoDaddy, Google Domains, etc.).
     - Add a `TXT` record at root (`@`) with the verification value.
     - Click **Verify** in Google Search Console.
   - **Option B — URL prefix verification:**
     - Enter `https://harinikeshr.dev/`.
     - Choose **HTML tag** method.
     - Copy the code inside `content="XXXXX"`.
     - Open `mysite/config/_default/params.toml` and paste it:
       ```toml
       [verification]
         google = "YOUR_VERIFICATION_CODE"
       ```
     - Commit and push to `main`. After GitHub Actions completes, click **Verify**.

### Step 2: Submit Your Sitemap to Google

Once verified in Google Search Console:
1. In the left sidebar, click **Sitemaps** (under *Indexing*).
2. Under "Add a new sitemap", enter:
   ```
   sitemap.xml
   ```
3. Click **Submit**.
4. Google will report "Success" and begin discovering and indexing all your pages.

### Step 3: Request Immediate Indexing for Your Homepage

1. In the top search bar of Google Search Console, type `https://harinikeshr.dev/` and press Enter.
2. Click **Request Indexing**.
3. (Optional) Repeat for key milestone pages like `/experience/`, `/community/`, or `/projects/`.

---

### Step 4: Submit to Bing Webmaster Tools

1. Go to [Bing Webmaster Tools](https://www.bing.com/webmasters).
2. Sign in with your Microsoft or Google account.
3. You can choose **Import from Google Search Console** (simplest 1-click import!).
4. Alternatively, add `https://harinikeshr.dev/` manually:
   - Copy the verification code and paste it in `mysite/config/_default/params.toml`:
     ```toml
     [verification]
       bing = "YOUR_BING_VERIFICATION_CODE"
     ```
   - Commit & push, then click **Verify**.
5. Go to **Sitemaps** in Bing and submit `https://harinikeshr.dev/sitemap.xml`.

---

## 3. SEO Maintenance Best Practices

When adding new posts or content:
1. **Title:** Keep page titles concise and descriptive (e.g. `<Title> @ <Organization>`).
2. **Description:** Always add a 1-2 sentence `description` in your markdown front matter. Search engines use this as the snippet.
3. **Tags:** Add 3-6 relevant tags (e.g., `["java", "spring-boot", "ai", "community"]`).
4. **Feature Image:** Add `featureimage: "images/..."` in front matter so social media platforms display an attractive preview card when your article is shared.
