MARQUEE SOUND - COMING SOON PAGE
================================

A single static placeholder page. No scripts, no dependencies, no build step.
Set up for GitHub Pages with the custom domain www.marqueesound.ca.

FILES
-----
index.html    The entire page (HTML + CSS are inline).
logo.png      The Marquee Sound logo, copied from the old site archive.
favicon.ico   The old site's favicon, copied from the old site archive.
CNAME         Tells GitHub Pages the custom domain is www.marqueesound.ca.
.nojekyll     Tells GitHub Pages to serve the files as-is (no Jekyll build).

To preview locally, just double-click index.html. It works offline.


WHAT TO EDIT
------------
Open index.html in any text editor:

  - Status line: search for "Website under construction".
  - Footer lead-in: search for "Find us on socials".
  - Social links: search for "instagram.com", "facebook.com" and
    "twitter.com" inside the three <a href="..."> tags.
  - Email address: search for "mailto:" in the footer.
  - Copyright year: search for "2026" in the footer.
  - Colours and fonts: the :root block near the top of the <style>
    section.
  - Canonical / link-preview URLs: search for "marqueesound.ca" in the
    <head>. Update these if the domain ever changes.

To use a different logo, replace logo.png with another transparent PNG
of the same name. Keep the filename or update the <img src="logo.png">.
If you use a different image, update the og:image:width and
og:image:height values in the <head> to match.


PUBLISH ON GITHUB PAGES
-----------------------
1. The repository already exists and is empty:
   https://github.com/MarqueeSound/marqueesound.ca
   It is public, so GitHub Pages is available on the free plan.

2. Upload every file in this folder to the repository root:
   index.html, logo.png, favicon.ico, CNAME, .nojekyll.
   On github.com use "Add file > Upload files", drag them in, then
   "Commit changes". The files must sit at the root, not in a subfolder.
   If your file browser hides .nojekyll, enable "show hidden files".

   Command-line alternative instead of the web upload, run from this
   folder after creating the empty repository:

     git init -b main
     git add .
     git commit -m "Add coming soon page"
     git remote add origin https://github.com/MarqueeSound/marqueesound.ca.git
     git push -u origin main

   If git is not installed, use the web upload above.

3. In the repository: Settings > Pages.
   - Source: "Deploy from a branch"
   - Branch: "main", folder "/ (root)"
   - Save. Wait for the "Your site is live" message.

4. Check the temporary URL first:
   https://marqueesound.github.io/marqueesound.ca/
   It should look identical to the local preview.

5. Add the custom domain:
   - On the same Pages screen, under "Custom domain", enter
     www.marqueesound.ca and click Save.
   - The CNAME file already contains this value; keep them identical.
   - Wait for the DNS check to pass, then tick "Enforce HTTPS".
     The certificate can take from a few minutes up to an hour.

6. Point easyDNS at GitHub. In easyDNS: MANAGE > DNS SETTINGS, then use
   the Modular Editor or the New DNS Editor.

   First delete any existing A or CNAME records for "@" and "www" that
   point at Squarespace or another host, then add:

     Host   Type    Value
     @      A       185.199.108.153
     @      A       185.199.109.153
     @      A       185.199.110.153
     @      A       185.199.111.153
     www    CNAME   marqueesound.github.io

   Optional IPv6 records (recommended by GitHub):

     @      AAAA    2606:50c0:8000::153
     @      AAAA    2606:50c0:8001::153
     @      AAAA    2606:50c0:8002::153
     @      AAAA    2606:50c0:8003::153

   Notes:
   - The CNAME value is marqueesound.github.io, with no repository
     name, no "www", and no trailing slash.
   - easyDNS uses "@" for the bare domain.
   - Do not create a CNAME at "@"; use the four A records above.
   - If the old records have a long TTL, lower it a day before the
     switch so the change propagates faster.

7. Wait for DNS to propagate (often minutes, up to 24-48 hours), then
   test in a private/incognito window:

     https://www.marqueesound.ca
     https://marqueesound.ca    (should redirect to www)
     http:// versions            (should redirect to https)

8. Only after the new page is confirmed live on the domain, cancel the
   Squarespace subscription.


CHECKING THE DNS
----------------
From a terminal:

  nslookup www.marqueesound.ca
  nslookup marqueesound.ca

Or use https://dnschecker.org and query A and CNAME records from
several locations. www should resolve through marqueesound.github.io,
and the bare domain should return the four GitHub IPs.


TROUBLESHOOTING
---------------
- 404 at the github.io URL: confirm index.html is at the repository
  root and Pages is set to branch "main", folder "/ (root)".
- "Domain's DNS record could not be retrieved": wait a few minutes and
  re-check. Remove conflicting A/CNAME records for @ and www.
- Certificate not ready: wait up to an hour after the DNS check passes,
  then toggle "Enforce HTTPS" again.
- Site loads at github.io but not the custom domain: the CNAME file and
  the custom domain setting must match exactly.
- Email still works: marqueesoundstudios@gmail.com is a Gmail account,
  so cancelling Squarespace does not affect it. It is linked in the
  footer.
- Mailto link does nothing: the visitor's device needs a default mail
  app. The in-app preview cannot launch external apps.


The original site archive in marqueesound-archive/ was not modified.
