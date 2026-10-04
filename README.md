# Sporewise

Phone-friendly UK mushroom guide prototype.

Live app: https://colachen520-png.github.io/sporewise-uk-mushroom-guide/

## What is here

- Eight high-value UK species, including edible candidates and dangerous lookalikes.
- Plain-English field clues: cap, underside, stem base, habitat and season.
- Search, source links, Wikimedia Commons reference photos and a camera/photo upload flow.
- A safety boundary: the photo flow is explicitly a guided comparison prototype, not an edible/poisonous verdict.
- Installable PWA shell with a small offline cache. Reference images still need a network connection unless we later bundle licensed local copies.

## Evidence base

- Natural History Museum, [UK species data](https://www.nhm.ac.uk/our-science/data/uk-species.html).
- Fungi of Great Britain and Ireland, [species accounts and checklists](https://fungi.myspecies.info/).
- Woodland Trust, [Deathcap](https://www.woodlandtrust.org.uk/trees-woods-and-wildlife/fungi-and-lichens/deathcap/) and [Fly agaric](https://www.woodlandtrust.org.uk/trees-woods-and-wildlife/fungi-and-lichens/fly-agaric/).
- RHS, [garden fungi and poisoning guidance](https://www.rhs.org.uk/biodiversity/nuisance-fungi).
- Mushroom poisoning review, [open access at PMC7868946](https://pmc.ncbi.nlm.nih.gov/articles/PMC7868946/), plus the newer review literature linked from its references.
- UK poison-centre retrospective study: [NPIS exposures 2013–2022](https://orca.cardiff.ac.uk/id/eprint/179633/).
- Reference images are sourced from [Wikimedia Commons](https://commons.wikimedia.org/); before production, record each image's individual licence and attribution in the database.

## What is not solved yet

1. There is no trained UK-specific visual model yet. The current upload flow accepts a real photo and creates a comparison shortlist, but it does not analyse pixels.
2. Eight species is not a UK database. A useful next dataset needs taxonomic coverage, regional occurrence, season, habitat, lookalikes, expert-reviewed labels and multiple views per specimen.
3. Photo-only edibility classification is unsafe. The model should be allowed to say “unknown / stop” often, and should return dangerous lookalikes rather than a single confident guess.
4. Photo licensing and expert validation need a production workflow. Wikimedia is a good starting point, not a substitute for checking each image licence.
5. The app needs a local expert escalation path, such as a UK fungus group or mycological society, before it is used for foraging decisions.

## Run locally

```bash
python3 -m http.server 8765
```

Open the live HTTPS app above, or run locally with `http://127.0.0.1:8765/` for development. HTTPS enables the most reliable camera permissions and “Add to Home Screen” behaviour.

## Load it on your phone now

1. Connect the phone and computer to the same Wi‑Fi network.
2. On the phone, open `http://192.168.1.158:8765/index.html`.
3. Use the browser menu and choose **Add to Home Screen** or **Install app**.

The current computer is serving the app on that address. If it stops working later, restart the server with:

```bash
python3 -m http.server 8765 --bind 0.0.0.0
```

The page is responsive at phone widths, and the photo control uses the phone camera/file picker. For a permanent app icon and more reliable camera permissions outside your home network, the next step is deploying the same files to an HTTPS host such as GitHub Pages, Cloudflare Pages or Netlify.
