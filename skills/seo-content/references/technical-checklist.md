# Technical checklist for a small new site

The basics that matter at 1–20 pages, in the order to check them, plus how answer engines tend to pick sources and how to measure with small numbers. Read this in steps 8–10. Most items take minutes. Google's own Search Central docs are the source of truth; check them when something here looks out of date.

Whoever runs the site (often the technical cofounder) can do this in an afternoon. Mark each item done, fix, or `[NEED: access]`.

## 1. Can search engines find and index it? (fix first)

| Check | How | Pass |
|---|---|---|
| Search Console set up | Add the domain property and verify it | Verified, owner has access |
| Pages not blocked | Open `/robots.txt`; look for `Disallow: /` | Nothing important disallowed |
| No leftover noindex | View source or use URL Inspection on each page | No `noindex` on pages meant to rank |
| Sitemap | `/sitemap.xml` lists every page meant to rank, and only those; submit it in Search Console | Submitted, no errors |
| Indexed | URL Inspection on each new page; request indexing once | "URL is on Google" or a reason you can act on |
| Content visible without scripts | URL Inspection's rendered view, or view source on JS-heavy sites | The main text is there |
| One version of the site | http → https, and www or non-www, each redirecting to one | One canonical address |
| Staging site hidden | Staging or preview URLs are password-protected or noindexed | Not in search results |

## 2. Each page

| Check | Pass |
|---|---|
| Title | Unique, phrase near the front, about 50–60 characters |
| Meta description | Unique, about 140–160 characters, says what the page answers |
| H1 | Exactly one, matches what the page is about |
| Headings | H2s and H3s in order, each one a real section, not styling |
| URL | Short, lowercase, words from the phrase, hyphens |
| Images | Descriptive file names and alt text; compressed |
| Author | Founder's name on the page, linked to the founder experience page |
| Date | Published or last-updated date on pages with facts that change |
| Links | At least one internal link in and one out to a related page; link text says where it goes |

## 3. Speed and mobile basics

- Run the page through PageSpeed Insights (free). Google publishes "good" thresholds for its Core Web Vitals; at the time of writing they are roughly: largest content shown within 2.5 seconds, responses to taps within 200 milliseconds, and layout shift under 0.1. Verify the current numbers before quoting them.
- Usual fixes at this size: compress and size images, set image width and height, cut third-party scripts you don't use (chat widgets, extra analytics), load one or two font files, not six.
- Google indexes the mobile version of a page. Check every page on a phone: readable text, tappable buttons, no sideways scrolling.
- Don't spend a week chasing a perfect score. Fix what's red, then write.

## 4. Structured data, only where it applies

Structured data describes the page to search engines. It doesn't make a page rank, and it's only worth adding where it matches something real.

| Type | Use when | Skip when |
|---|---|---|
| Organization | Homepage: company name, logo, site URL | Never skip; it takes minutes |
| Article (with author and date) | Problem pages, how-tos, the founder page | Pages that aren't articles |
| BreadcrumbList | The site actually shows breadcrumbs | It doesn't |
| SoftwareApplication or Product | A live product with a real public price | Waitlist or "contact us" pricing |
| Review or rating markup | Never on reviews you wrote or collected on your own page for yourself | Always, at this stage |
| FAQ or how-to markup | Check Google's current docs first: it has narrowed which sites get these rich results, and most small sites won't see them | Default |

Validate with Google's Rich Results Test, which renders the page. A plain fetch of the HTML can miss markup added by scripts.

## 5. Answer engines and AI search

Describe this to the founder cautiously. How each engine chooses sources changes often and isn't fully published.

What appears to help, and is good practice anyway:
- A direct answer to the page's question in the first paragraph, in plain words.
- A real, named author with experience the page shows.
- Sources cited for any fact that isn't the founder's own.
- The company described the same way everywhere it appears: site, LinkedIn, directories, founder bios. Same buyer, same one-liner as company.md.
- Clear headings that match the questions buyers ask, and tables where a comparison is the answer.

What to be careful about:
- No special file or markup is a confirmed requirement for appearing in AI answers. Google says its AI features rest on its normal search systems. Proposals like `llms.txt` are optional experiments.
- Some AI tools use their own crawlers. Blocking them in `robots.txt` can keep the site out of their answers. Check each vendor's current docs for which crawler does what before blocking or allowing.
- Don't write separate pages "for AI". Write for the buyer; the same page serves both.
- Don't report "we're cited in ChatGPT" from one test. Answers vary by run, wording and day.

## 6. Measurement at small numbers

| Stage | Where | What to write down monthly |
|---|---|---|
| Impressions | Search Console, Performance report, filtered by page | Count per page, and the top queries it showed for |
| Clicks | Same report | Count per page |
| Average position | Same report | Rough guide only; it moves a lot with few impressions |
| Organic signups | "How did you find us?" on the signup or waitlist form, plus the landing page if your tool records it | Count, with the page if known |

- Counts, not rates, until each page has a few hundred impressions a month.
- Look at the queries a page actually shows for. If they differ from the phrase in the brief, the brief was wrong or the page is better aimed elsewhere; re-brief, don't stuff.
- A page earns its place by bringing the right reader, not traffic. Ten impressions from managing partners beat a thousand from students.
- Review monthly. Daily checking at these numbers is noise.
