# Image Casting & Ad Formats — regional accuracy, layout, commerce

> **What this is.** nano-banana-prompter casting and commercial work. Read when the market matters: ethnicity-accurate casting, Gulf/MENA/South Asia/SEA, ad layout and in-image copy, product and apparel framing.

> **Bundle of 15 source files, 174,358 bytes.** Sections are the original skill files verbatim, in the order listed below. Each begins with a `<!-- FILE: path -->` marker — split on those markers to reconstruct the mountable skill tree byte-for-byte (see `19-SKILL-MANIFEST.md`).

## Contents

| # | Source file | Bytes |
|---|---|---|
| 1 | `nano-banana-prompter/references/global_ethnicity_casting.md` | 20,752 |
| 2 | `nano-banana-prompter/references/uae_gulf_casting_and_ugc.md` | 16,914 |
| 3 | `nano-banana-prompter/references/mena_casting.md` | 10,576 |
| 4 | `nano-banana-prompter/references/south_asia_casting.md` | 14,408 |
| 5 | `nano-banana-prompter/references/southeast_asia_casting.md` | 9,668 |
| 6 | `nano-banana-prompter/references/pakistan_ads_and_directors.md` | 23,011 |
| 7 | `nano-banana-prompter/references/recent_ad_trends_and_directors.md` | 7,556 |
| 8 | `nano-banana-prompter/references/creative_posts_copy_type_layout.md` | 21,647 |
| 9 | `nano-banana-prompter/references/commercial_framing_and_set_design.md` | 13,951 |
| 10 | `nano-banana-prompter/references/styling_and_set_design.md` | 3,694 |
| 11 | `nano-banana-prompter/references/apparel_and_beauty.md` | 4,511 |
| 12 | `nano-banana-prompter/references/streetwear_and_genz.md` | 3,449 |
| 13 | `nano-banana-prompter/references/football_and_fifa_frames.md` | 13,863 |
| 14 | `nano-banana-prompter/references/closeups_and_interviews.md` | 4,294 |
| 15 | `nano-banana-prompter/references/campaign_and_specialist_genres.md` | 6,064 |

---

<!-- ═══════ FILE: nano-banana-prompter/references/global_ethnicity_casting.md ═══════ -->

# Nano Banana — global ethnicity casting: skin, hair, features & dress by region

How to cast believable people of ANY ethnicity — modern-day and heritage — without the model's stereotype defaults. Companion to `references/uae_gulf_casting_and_ugc.md` (the deep UAE/GCC module; the five-casting-axes rule is defined there and applies to every region here). The realism stack (`references/realism_and_ugc.md`) and age table still apply to every face on this page.

> **Field-validated (Round 9, `field_findings.md`):** the five-axes system, tone-lock + deep-skin lighting craft (Tamil and agbada tests held deep tone with specular life, zero ash), per-subject enumeration + *"no two faces alike"* (Seoul trio, Dubai crowd), and heritage-dress accuracy all confirmed live on Pro. Open item: the coily-hair anti-loosening close (test frame failed to render — rerun pending).

---

## What the model does when you don't specify

Documented, repeatable biases across text-to-image systems — Nano Banana is better calibrated than older diffusion models but the training-data gravity pulls the same directions:

| Default bias | What it looks like |
|---|---|
| **White/Western default** | neutral prompts ("a successful person", "a doctor") skew white, male, Western business dress |
| **Skin lightening** | darker-skinned subjects drift lighter across generations and under bright/warm lighting; "Black woman with braids" returns caramel complexions and loosened hair |
| **Hair straightening** | coily/kinky textures rendered as waves; chemically-straightened default; protective styles genericized |
| **One-face homogenization** | every member of an ethnicity gets the same face, tone, and grooming (the "same face" tell) |
| **Costume-ification** | ethnicity triggers heritage dress regardless of context — sari for "Indian office worker", poncho for "Mexican engineer" |
| **Westernizing feature drift** | East Asian and other features nudged toward Euro norms across edit chains |

**Counter-moves, applied everywhere:**
1. Specify the five casting axes independently (skin tone / features / hair / wardrobe / context).
2. **Tone lock:** name tone + undertone once, then on every warm-light or bright frame add *"preserve the true deep skin tone under this light — do not lighten."* On every edit turn of a dark-skinned subject, restate the tone; lightening drift compounds across turns.
3. **Hair by texture, not ethnicity:** name the texture/style directly (chart below).
4. **Modern by default:** everyday contemporary dress unless the brief is heritage/celebration — then name the exact garment and occasion.
5. **Vary within a cast:** two subjects of the same ethnicity get different tones, faces, builds, grooming — say so: *"no two faces alike."*
6. **Restate the full identity block on every variant and regeneration.** Attributes slip between runs of the same prompt (a "full white beard" became stubble across variants in Round 9) — variants are not free; each generation needs the complete spec.

---

## The skin-tone system (all regions)

Ethnicity words are not skin-tone instructions. Use a three-part spec: **descriptor + undertone + lighting isolation.**

**Descriptor menu** (light→deep): porcelain, fair ivory, light beige, light olive, golden beige, warm olive, golden tan, medium tan, caramel, warm bronze, deep bronze, rich brown, deep brown, espresso, ebony, blue-black deep umber.

**Undertones:** cool/rosy, neutral, warm/golden, olive/green-leaning, red-leaning. The Monk Skin Tone scale (MST 1–10) is a useful anchor for series consistency: *"deep brown, MST 8, warm undertone, base tone constant across all frames."*

### Lighting melanin-rich skin (craft, not just fairness)

Deep skin is a different lighting problem, and the model's default exposure is calibrated for light skin. For MST 7–10 subjects:

- **Expose for the face**, not the background — *"exposure set for her deep brown skin, background allowed to blow out slightly."*
- **Specular life:** deep skin reads through its highlights — *"soft specular sheen on the cheekbones, forehead and nose bridge catching the key."* Matte-flat rendering reads ashy/grey — the #1 deep-skin AI tell. Add *"no ashy or greyed skin, rich warm depth in the shadows."*
- **Bounce/fill has a colour:** *"warm bounce filling the shadow side"* — deep skin swallows weak fill.
- **Backgrounds separate by tone contrast**, not brightness — mid-tone backgrounds, rim light on hair and shoulders.

### Hair texture chart — name it directly

| Texture | Write |
|---|---|
| Straight (1) | *thick straight black hair / fine straight blonde* |
| Wavy (2) | *loose S-waves* |
| Curly (3a–3c) | *defined springy curls / tight corkscrew curls* |
| Coily (4a–4c) | *tightly coiled 4C hair, dense afro texture, visible shrinkage* |
| Protective & styled | *box braids / knotless braids with beads / cornrows in straight-backs / mid-length locs / twist-out / TWA (teeny-weeny afro) / silk press / low fade with waves and a sharp line-up / durag / headwrap tied high* |

For coily textures and protective styles, close with *"authentic 4C texture, no loosened or straightened curls"* — the loosening drift is confirmed across models.

---

## Region modules

Each module: the model's default → skin/feature/hair language → modern register → named heritage dress (deliberate, occasioned) → one paste-ready block.

### South Asia (India · Pakistan · Bangladesh · Sri Lanka · Nepal)

**Deep module:** `references/south_asia_casting.md` — India cast by region (the NW–South tone cline, Bengali olive undertone, the East-Asian-featured Northeast), Pakistan's ethnic map and its different daily-dress system (shalwar kameez as national wear), markers with meaning (bindi/sindoor/dastar rules), regional saris, lawn culture, and the India/Pakistan cross-contamination failure modes. The summary below is the quick version; go to the deep file for any India or Pakistan brief.

**Default trap:** one pan-"Indian" face; sari/kurta on office briefs; fairness bias (media-driven lightening); Pakistan rendered as "India lite" with the wrong markers.
**Spectrum:** wheatish/golden beige (north) through warm tan and caramel to deep brown (south, Sri Lanka); state it — *"deep brown skin with warm undertone"* for a Tamil or Sri Lankan subject resists the lightening pull. Hair mostly thick and straight-to-wavy black; men's grooming from clean-shaven to full beard + moustache registers.
**Modern:** kurta over jeans, cotton salwar kameez as daily wear, sari draped for office in some professions, or fully western — pick one.
**Heritage (named, occasioned):** sari (name the drape — Nivi, Bengali, Kerala **mundum neriyatum**), salwar kameez + **dupatta**, lehenga choli + heavy gold (weddings), sherwani + churidar (grooms), dhoti / **veshti** / **mundu** / lungi (regional men's), Anarkali suit. Markers with meaning — use only in context: **bindi** and **sindoor** (married Hindu women), **dastar turban = Sikh men specifically** (never a generic "Indian turban"), mehndi for celebrations.
> *"A Tamil software engineer in her late 20s, deep brown skin with warm undertone — preserve the tone under office light — thick black hair in a low braid, small gold stud earrings, wearing a teal cotton kurta over slim jeans, laughing at a colleague's desk in a Bangalore office."*

### East Asia (China · Japan · Korea)

**Default trap:** the "same face" — near-identical pale-skinned young women; Westernized eye/nose drift across edits; garment mixing (a qipao on a "Japanese" brief).
**Spectrum:** fair-cool through golden beige to medium tan; state monolid or double eyelid explicitly if it matters, plus face shape, brow style, and age markers. Vary faces: *"distinct individual faces, different ages and builds."*
**Modern registers differ by country:** Seoul (tone-on-tone minimalism, clean layering), Tokyo (street-fashion tribes, workwear, denim craft), Shanghai/Chengdu (bold contemporary luxury + streetwear). For realism, skip the "glass skin" ideal — apply the standard anti-plastic stack.
**Heritage (never mix countries):** China — **qipao/cheongsam**, **hanfu** (dynastic, specify era), Tang jacket; Japan — **kimono** with **obi** (formal; furisode for young women), casual cotton **yukata** (summer festivals); Korea — **hanbok** (women's **jeogori** jacket + full **chima** skirt; men's jeogori + **baji**).
> *"Three friends at a Seoul street-food stall at night, all Korean, distinct faces — one round-faced with a monolid and short bleached hair, one with a longer face, double eyelids and glasses, one older with visible smile lines — golden-beige to medium-tan skin tones, puffer jackets and tone-on-tone layers, steam rising, mixed neon and tungsten light."*

### Southeast Asia (Philippines · Indonesia · Malaysia · Thailand · Vietnam)

**Default trap:** rendered as East Asian-pale or as generic "island" imagery; models under-know these populations.
**Spectrum:** golden tan through warm bronze to deep tan — *"morena golden-tan skin"* is the natural register for a Filipina subject; Indonesian/Malay similar range; state it or the model lightens. Hair thick, straight-to-wavy black.
**Modern:** fully contemporary urban — Manila streetwear, Jakarta modest-fashion (a **tudung/hijab** styled with modern layers is everyday for many Malay/Indonesian women — a style choice to state, not a default to assume), Bangkok fashion-forward.
**Heritage:** Philippines — **barong tagalog** (sheer embroidered formal shirt, worn untucked) and the butterfly-sleeve **terno**; Indonesia/Malaysia — **batik** shirts (formal Fridays are real), **kebaya**, **baju kurung** (women) / **baju melayu + songkok** (men, Eid); Thailand — **chut thai**; Vietnam — **áo dài** (Tet, weddings, graduations).
> *"A Filipina nurse in her 30s on a break, golden-tan morena skin with visible pores — keep the tone under the fluorescent light — thick black hair in a bun, navy scrubs, phone in hand mid-video-call, hospital corridor bokeh behind, front camera at arm's length, 9:16."*

### Sub-Saharan Africa (West · East · Horn · Southern)

**Default trap:** one undifferentiated "African" — plus wealth-poverty clichés (thatched huts behind businessmen) and safari backdrops.
**Spectrum:** the widest on earth — caramel through rich brown to blue-black ebony; the Horn (Ethiopian, Somali, Eritrean) often warm bronze-to-deep brown with its own feature signatures. Use the deep-skin lighting craft above on every frame.
**Modern:** Lagos tech-office, Nairobi startup, Accra creative scene, Joburg corporate — contemporary dress, and West African tailoring culture means **ankara/wax-print** shirts and dresses ARE modern everyday-to-smart wear, not costume.
**Heritage (name the culture, not the continent):** West — **agbada** (grand flowing robe, Yoruba/Hausa men, weddings/status), **boubou**, **dashiki**, **kente** (Ghana — occasion cloth: graduations, weddings), **gele** head-tie (Nigerian women, events), **kufi/fila** caps; East — **kitenge/kanga** prints, Maasai **shuka** (Maasai specifically, never generic "Kenyan"); Horn — Ethiopian **habesha kemis** + white **netela** shawl, Somali **dirac** / men's **macawis**; Southern — Xhosa **umbhaco**, Zulu **isicholo**, Sotho **shweshwe** prints and blankets, Ndebele beadwork.
> *"A Nigerian groom at a Lagos wedding, deep brown skin with warm undertone and a soft specular sheen on the cheekbones — expose for his skin, no ashy grey — short 4C hair with a sharp line-up, full embroidered sky-blue agbada with a matching fila cap, gold wristwatch, laughing mid-dance, warm tungsten event lighting, confetti motion-blurred around him."*

### Black diaspora (African American · Afro-Caribbean · Black British)

**Default trap:** complexion lightening + hair loosening (confirmed dataset bias), and context stereotyping (athlete/entertainer/street defaults). Cast the full range — surgeons, professors, dads at soccer practice, fintech founders.
**Skin & hair:** full MST spectrum; name the style from the hair chart (box braids, knotless, cornrows, locs, twist-out, afro, silk press, fade + waves, durag at home) and add the anti-loosening close. Restate tone on every edit turn.
**Modern registers:** Atlanta luxury-street, NY corporate, London roadman vs city-boy vs church-Sunday tailoring, Caribbean carnival ONLY for carnival briefs.
> *"A Black American pediatrician in her 40s, rich espresso skin with neutral undertone — preserve the deep tone under the clinic light, no ashy cast — shoulder-length locs pulled back, minimal gold jewelry, white coat over a printed blouse, crouched to a child patient's eye level, soft window key camera-left, her right cheek in shadow. Authentic 4C texture at the hairline, no loosened curls."*

### MENA beyond the Gulf (Levant · Egypt · Maghreb · Iran · Turkey)

Deep Gulf module: `references/uae_gulf_casting_and_ugc.md`. The rest of the region is NOT the Gulf:
- **Levantine** (Lebanese, Syrian, Jordanian, Palestinian): lighter-olive-to-tan spectrum, overwhelmingly modern dress; Beirut is a fashion capital register. The **keffiyeh** carries specific national/political meaning — deliberate choice only.
- **Egypt:** Cairo urban modern; the **galabeya** is real daily wear in rural/older contexts, costume elsewhere.
- **Maghreb** (Morocco, Algeria, Tunisia): **djellaba** (hooded, both sexes, genuinely everyday for many), women's **caftan/takchita** (celebrations); Amazigh/Berber facial tattoos on elder women only, never invented on the young.
- **Iran:** Persian features and their own spectrum; women's street style = **manteau** + loosely draped **rusari** headscarf (a distinct look — not a Gulf shayla, not a pinned hijab); strong grooming/beauty culture.
- **Turkey:** Mediterranean-to-Anatolian spectrum, fully European-modern dress registers in cities; headscarf styles specific (silk square, pinned under chin) where briefed.

### Latin America

**Default trap:** one "Latina" template (light-tan, wavy dark hair, curvy) and sombrero/poncho costume defaults. Reality: mestizo, Indigenous, Afro-Latino, Euro-descended, Asian-Latino — AND country matters (a Buenos Aires cast skews European; Brazil is one of the most mixed populations on earth; Guatemala and Bolivia have Indigenous majorities/pluralities).
**Spectrum & hair:** fair-olive through caramel to deep brown; every hair texture exists — specify.
**Modern:** CDMX creative scene, São Paulo streetwear, Bogotá corporate, Miami-diaspora gloss — name the city register.
**Heritage (specific, occasioned):** Mexico — **charro** suit, **china poblana**, **rebozo** shawl, regional; Guatemala/southern Mexico — Maya **huipil** + **corte** (living daily dress for many Maya women — accurate in context); Andes — **pollera** skirts, **chullo**, poncho (real highland wear, not a Mexico default); Brazil — Bahia's **baiana** whites (Afro-Brazilian religious/cultural specificity).
> *"A Brazilian product designer in São Paulo, Afro-Brazilian, warm bronze skin — keep the tone true under the studio light — defined 3C curls in a high puff, gold hoops, oversized blazer over a graphic tee, sketching at a standing desk, window key camera-right with her left side in shadow."*

### Europe (yes, specify it too)

"European" is also a spectrum the model flattens to one default: Mediterranean (olive skin, dark hair — Italian, Greek, Spanish, Portuguese), Nordic (cool-fair, light eyes), Slavic (broad cheekbones, fair-to-medium), Celtic (pale, freckled, red-to-brown hair), Balkan, and every modern European city is itself multi-ethnic — a "real" London, Paris, or Berlin street casts far wider than white-European. Folk dress (dirndl/lederhosen, kilt, **vyshyvanka**, Sámi **gákti** — see Indigenous below) is festival/heritage wear only.

### Central Asia & the Caucasus

Kazakh, Kyrgyz, Uzbek, Tajik faces blend Turkic/East-Asian and Persian signatures the model barely knows — describe directly (*"Kazakh man, medium-tan skin, broad cheekbones, dark epicanthic-fold eyes"*). Heritage: **chapan** robe, **tubeteika/kalpak** caps, ikat patterns (Uzbek). Caucasus (Georgian, Armenian): dark-haired Mediterranean-adjacent spectrum; **chokha** for ceremony.

### Indigenous peoples — the high-caution zone

The strongest costume-ification and sacred-item risk. Rules:
- **Contemporary first.** Most Indigenous people wear modern dress daily. *"A Diné (Navajo) high-school science teacher in a flannel shirt and turquoise ring"* is accurate representation; a war bonnet on him is not.
- **Name the nation** — Diné, Lakota, Cree, Haida — never "Native American" as a visual style. Regalia is ceremonial and nation-specific; the **war bonnet is an earned honor** in specific Plains nations — do not generate it as decoration.
- **Māori:** **tā moko** facial tattoos are earned/genealogical — never invent moko on a face; the **korowai** cloak is honor-wear. Contemporary Māori + a pounamu (greenstone) pendant is safe and real.
- **Aboriginal Australian:** enormous internal diversity; ceremonial body paint and specific dot-painting styles are owned by communities — contemporary casting unless working with community guidance.
- **Inuit / Sámi:** **parka/amauti** and **gákti** are living functional-and-identity dress — accurate in-context; the gákti's colors/patterns encode family/region, so keep it generic-respectful or research the brief.

### Mixed heritage

Underspecified mixed prompts collapse to one parent's stereotype. State both heritages AND the concrete blend: *"a woman of Nigerian-Japanese heritage — deep golden-tan skin, loosely coiled 3C black hair, monolid eyes, freckles across the nose."* The trait list does the work; the heritage label alone doesn't.

### Religious dress ≠ ethnicity (cross-cutting)

Hijab (many styles — Gulf shayla ≠ Turkish pin ≠ Iranian rusari ≠ Malay tudung ≠ West-African headwrap), Sikh **dastar**, Jewish **kippah**/Orthodox dress, nun's habit, Buddhist monk robes — all are specific choices to brief deliberately, never defaults triggered by an ethnicity word.

---

## Failure modes & fixes (global)

| Symptom | Fix |
|---|---|
| **Skin lightens across edits / under warm light** | Restate tone every turn + *"preserve the true deep skin tone, do not lighten"* on every graded frame |
| **Ashy/grey deep skin** | Expose for the face, add specular sheen language, warm bounce fill, *"rich warm depth in the shadows"* |
| **Coily hair renders loose/straightened** | Name the texture/style exactly + *"authentic 4C texture, no loosened or straightened curls"* |
| **Same-face cast** | Per-subject feature enumeration + *"distinct individual faces, no two alike, different ages and builds"* |
| **Costume default on a modern brief** | State contemporary wardrobe explicitly; move heritage dress behind a named occasion |
| **Mixed-country garments** (qipao on a Japanese brief, Saudi collar on a kandura) | Use the named garment for the named country from the module tables |
| **Sacred/earned items as decoration** (war bonnet, tā moko, bindi-as-fashion on non-Hindu casting) | Contemporary casting; regalia only for its own ceremony, named nation, briefed context |
| **Ethnicity-as-features shortcut ("Asian eyes", "African hair")** | Replace with describable traits: eyelid type, hair texture, tone + undertone |
| **Westernizing drift on East Asian faces across turns** | Identity block first every turn, enumerate the eyelid/face-shape markers, re-anchor with reference every 3–4 turns |
| **One "Latina"/"Indian"/"African" template** | Pick the country → the region within it → the specific tone/hair/register from that module |
| **Background crowds monochrome** | Cast crowds to the real city (London/Toronto/Dubai/São Paulo streets are visibly multi-ethnic) |

---

## Quick build order for any ethnicity brief

1. **Country + community**, not continent ("Yoruba Nigerian", not "African").
2. **Tone + undertone** (+ MST anchor for series) and the tone-lock clause.
3. **Features enumerated** (eyes, brows, nose, face shape, age markers) — this is also the identity-lock block.
4. **Hair by texture/style name** + anti-loosening close where relevant.
5. **Wardrobe: modern register by default**; heritage garment by name + occasion when briefed.
6. **Grooming/beauty register** stated (clean-shaven vs beard; glam vs no-makeup).
7. **Context that isn't the stereotype** — profession and setting cast against the default.
8. Then the standard realism stack: skin cues, sourced light (with deep-skin craft if MST 7+), capture medium, micro-imperfection.


<!-- ═══════ FILE: nano-banana-prompter/references/uae_gulf_casting_and_ugc.md ═══════ -->

# Nano Banana — ethnicity casting, UAE/Gulf accuracy & Khaleeji UGC

How to cast real-looking people of specific ethnicities — with a deep module on the UAE/GCC market — and how to shoot UGC that reads as *made in Dubai*, not "generic Arab stock photo." Applies to Nano Banana 2 (iteration) and Nano Banana Pro (hero frames + Arabic typography). Builds on `references/realism_and_ugc.md` (the four-layer realism stack and UGC five-stack still apply to every frame here) and `references/text_rendering.md` (Arabic RTL rules). For every other region and ethnicity — the global module system, skin-tone/hair systems, and deep-skin lighting craft — see `references/global_ethnicity_casting.md`.

---

## The problem: the "generic Arab" prior

Research on text-to-image models documents heavy **racial homogenization** of Middle Eastern subjects: nearly all men rendered bearded, brown-skinned, and in traditional attire *regardless of context*; women rendered with near-identical skin tones and default veiling; "wealthy person, Middle East" → man posed in front of an ancient mosque. Gemini-stack models are better calibrated than older diffusion models, but the prior pulls the same direction. Leave ethnicity vague and the model hands you the stereotype composite: one skin tone, one beard, one keffiyeh, a mosque or a dune.

**The counter-move is always the same: specify each axis independently.** Nationality ≠ ethnicity ≠ skin tone ≠ wardrobe ≠ religiosity. "An Arab man" is a non-instruction. "An Emirati man in his late 20s, warm golden-tan skin, clean-shaven, in a collarless white kandura, laughing at his phone in a mall food court" is a casting call.

> **Field-validated (Round 9, `field_findings.md`):** the mixed-cast Dubai crowd (anti-homogenization), shayla-style specification (loose drape with hair visible rendered exactly — no auto-veiling), and kandura/turban-ghutra accuracy all confirmed live on Pro. Caveat: crowd/retail frames invent semi-legible Arabic and misspelled brand signage — add *"no readable text"* or quote exact native-checked copy.

### The five independent casting axes

| Axis | Never write | Write instead |
|---|---|---|
| **Skin tone** | "Arab skin", "brown" | a concrete descriptor + undertone: *warm olive, golden tan, deep bronze, light olive with neutral undertone, rich brown with warm undertone* |
| **Features** | ethnicity as a feature shortcut | the actual features: brow weight, eye shape/colour, nose bridge, lip fullness, hair texture (*thick straight black hair, loose dark curls, coily*) |
| **Wardrobe** | "traditional clothes" | the named garment for the named country (tables below) — or explicitly modern dress |
| **Grooming** | (model defaults to full beard) | state it: *clean-shaven / stubble / short sharp-lined beard / groomed moustache* |
| **Context** | (model defaults to mosque/desert) | the real scene: office, gym, mall, cafeteria, apartment |

Skin tone words are coarse buckets — "brown" spans half of humanity. Pair tone + undertone, and keep the base tone constant across a series while letting *lighting* vary (state "preserve true skin tone" on warm-light frames, or the grade will re-tan the subject).

**Identity-lock note:** for recurring characters of any ethnicity, the fixed-marker list in `references/identity_lock_and_filmmaking.md` matters *more*, not less — ethnicity averaging across edit turns is a documented drift mode. Put the identity block (with skin tone + feature enumeration) FIRST, scene block after, every turn.

---

## Casting the UAE accurately — the demographic reality

The UAE is ~11–12% Emirati nationals and ~88% expatriate: South Asians are the largest bloc (~60%+ combined — Indian ~38%, Pakistani ~17%, Bangladeshi ~7%), then Filipino (~6%), Iranian, Egyptian, Levantine Arab, East/West African, East Asian, Western. Over 200 nationalities. This matters for realism: **a "real" Dubai crowd scene is one of the most visibly multi-ethnic frames on earth.** An all-Khaleeji mall, gym, or street reads as wrong to anyone who lives there — unless the brief is a Nationals-only setting (a majlis, an Emirati wedding, a government office scene).

| Scene | Believable background cast |
|---|---|
| Dubai Mall / JBR / Marina walk | fully mixed — South Asian families, Filipino groups, Gulf nationals in kandura/abaya, European tourists, East African, East Asian |
| Cafeteria / karak spot | predominantly South Asian + Emirati regulars; male-skewing |
| DIFC / office | mixed professional: Levantine, South Asian, Western, Emirati in kandura |
| Majlis, Emirati wedding, National Day | Emirati/Khaleeji casting, traditional dress correct per tables below |
| Construction / logistics | predominantly South Asian male workforce |
| Salon / beauty / clinic content | Filipina and Arab staff extremely common; clientele mixed |

Also true of the UAE gender skew (roughly 2:1 male overall) — a metro carriage or labour-area street that's mostly men is accurate; a Khaleeji family setting is not.

---

## Emirati & Gulf national dress — get the country right

The #1 credibility failure in AI "Gulf" imagery is **mixing national dress signatures across countries**. The garments look similar at a glance; locals clock the difference instantly.

### Men

| Country | Robe | Signature details | Headwear |
|---|---|---|---|
| **UAE (Emirati)** | white **kandura** | **collarless**, long twisted **tassel (farukhah/tarboosh)** hanging from the neckline, discreet matching sleeve embroidery | **white ghutra** + black **agal**; younger men often wrap it turban-style (**hamdaniyah**, no agal); red-check shemagh worn but less canonical |
| Saudi Arabia | white **thobe** | **two-button collar**, shirt-style cuffs, slimmer cut | **red-and-white shemagh** + agal (white ghutra also worn) |
| Kuwait | **dishdasha** | one-button, no tassel; darker shades in winter | ghutra + agal |
| Oman | **dishdasha** | tassel at the **side** of the collar, often embroidered | embroidered **kuma** cap or **msar** turban — **no agal** |
| Qatar/Bahrain | thobe close to Saudi | subtle cut differences | ghutra/shemagh + agal |

Layers and details that sell an Emirati man: a white **ghafiya** prayer cap under the ghutra, plain white **faneela** vest beneath the kandura, leather **na'al** sandals (no socks), and for ceremony/weddings/dignitaries only, the gold-trimmed **bisht** cloak over the kandura. Kanduras are kept *crisp* — pressed, brilliant white (beige/grey/lavender in winter) — an ironed, immaculate kandura is realism, not over-styling. **Do not** put an agal on a turban-wrapped ghutra, a Saudi collar on a "kandura," or a bisht on a casual scene.

> **Paste-ready Emirati male block:** *"An Emirati man in his early 30s, warm golden-tan skin, short black hair, neatly-trimmed short beard with sharp lines, wearing a crisp collarless white kandura with the long twisted farukhah tassel at the neckline, a white ghutra folded over his head held by a black agal, leather sandals."*

### Women

| Element | What's accurate |
|---|---|
| **Abaya** | long, **loose, flowing** black over-garment (crepe drapes best) worn *over* clothes — modern cuts include open-front abayas over jeans/dress, embroidery, and non-black shades (greys, browns, nudes) common among younger Emiratis. Never render it bodycon-tight. |
| **Shayla** | the Gulf headscarf — a long rectangular scarf draped over the head and shoulder. Styles genuinely vary: loosely draped with some hair visible at the front (very common among young Emiratis), or pinned for full coverage. **State the style; don't let the model default.** |
| **Jalabiya/kaftan** | colourful embroidered house dress — home, family gatherings, Ramadan evenings |
| **Niqab** | worn by some women by choice — not a default; specify only if the brief calls for it |
| **Battoulah (Gulf burqa)** | the metallic-sheen fabric face mask — **older generation** and heritage contexts only |
| Finishing | gold jewellery (bangles, statement rings), fresh henna on hands for celebrations, designer handbag + sneakers or heels under the abaya, oud fragrance implied by context (bakhoor burner in frame) |

The **Khaleeji beauty register** (for glam/beauty briefs): bold sculpted brows, winged liner, contoured warm-toned base, glossy nude-mauve lip, voluminous blow-dry or sleek middle part under a loose shayla. For UGC keep it in check — a no-makeup UGC frame uses the standard anti-plastic skin stack instead, and reads *more* local-authentic, not less.

**Skin-tone spectrum:** the Khaleeji population is genuinely wide — fair olive through golden tan to deep brown (Afro-Emirati, Baloch, and Persian-coast heritage are all part of the national fabric). Rendering every Emirati one shade of "tan" is the homogenization tell. Pick a specific tone per subject and vary it across a cast.

---

## Khaleeji / UAE UGC — how it actually looks

Everything in the UGC five-stack (`references/realism_and_ugc.md`) applies. On top of it, five local layers separate *Dubai UGC* from *US UGC with a filter*:

**1 — Environment logic (the AC world).** UAE life happens indoors 9 months a year: bright cool-white LED interiors, glass, marble, mall light. Exteriors are either *harsh bleached midday* (hard top sun, squinting, deep shadows, heat shimmer on asphalt) or the *golden-to-blue-hour* window when people actually go out. Nobody lounges on an outdoor terrace at 2pm in August — climate mismatch is an instant local tell. Condensation on a cold drink outdoors, sunglasses, tinted car windows: all free realism.

**2 — The local clutter ledger.** Swap the Western clutter list for the local one: a **karak chai paper cup**, a plastic water bottle, a mall carrier bag, a **Salik tag on the windshield**, prayer beads (misbaha) on the console, a **bakhoor/oud burner**, dates on a small plate, **gahwa** in a dallah with tiny finjan cups, food-delivery bags, an untangled phone-charger on a marble counter. 3–6 named objects, same rule as the master ledger.

**3 — Settings that read as UAE without a landmark.** Marina/JBR promenade, mall food court, a **cafeteria karak window at night** (fluorescent sign, plastic stools), a majlis (floor cushions along the walls, carpet, gahwa set), a high-floor apartment with floor-to-ceiling windows and haze over the skyline, a valet drop-off, desert dunes at golden hour, a super-clean gym. Use the Burj/skyline sparingly — the landmark-hero shot is the tourist-board cliché, not UGC.

**4 — Cultural calendar & register.** Ramadan (iftar spreads, suhoor, lantern + crescent dressing, dates + laban), Eid (new outfits, gifts, family), UAE National Day (flag colours), Friday family gathering. The commercial register is **aspirational-but-grounded**: quality visible in the details (watch, bag, car interior) without the gold-and-supercar cartoon — unless the brief is explicitly the flex genre. Compliance defaults for GCC marketing content: no alcohol, no pork, no couple PDA, modest hemlines/necklines on local casting, avoid visible tattoos on Khaleeji-cast talent, right hand for eating/serving frames.

**5 — Language.** Any in-image text: Arabic + English bilingual is native to the market (Arabic first or given equal weight). Khaleeji Arabic and Egyptian/Levantine Arabic are different registers — get real copy from a native speaker; never let the model improvise Arabic. Render Arabic on **Nano Banana Pro**, state **right-to-left layout**, and quote the exact string (`references/text_rendering.md`).

### Model routing for this work

- **Nano Banana 2** — casting/skin-tone iteration, UGC volume variants, background-crowd tests (cheap, <2 s).
- **Nano Banana Pro** — hero frames, any Arabic typography (RTL fidelity needs the Pro text engine), 4K finals, and web-search-grounded frames (e.g. current Ramadan dates, live weather for a "today in Dubai" post).

---

## Worked frames (paste-ready)

**Emirati male UGC selfie — cafeteria karak run.**
> *"A young Emirati man taking a front-camera selfie at night outside a small cafeteria window, phone at arm's length, no mirror in frame, 9:16, slight HDR push, mild over-sharpening. Warm golden-tan skin with visible pores and a faint T-zone sheen, short sharp-lined beard, white ghutra wrapped turban-style without an agal, crisp white collarless kandura with the twisted tassel at the neckline. Mixed light: harsh fluorescent from the cafeteria sign fighting warm sodium street light, no fill, uneven exposure. He's mid-grin, eyes just off the lens, holding a paper cup of karak chai; behind him plastic stools, a menu board with Arabic and English text slightly out of focus, a parked white Land Cruiser at the edge of frame. Not staged, not retouched, casual close-friends story vibe. A photograph, not a painting."*

**Emirati woman UGC — coffee-shop table shot.**
> *"A phone photo shot from across a café table, 4:5, slight HDR push. An Emirati woman in her mid-20s, light olive skin with visible pores and faint redness on the cheekbones, minimal makeup with groomed bold brows, a black shayla draped loosely with a little hair visible at the front, an open-front greige abaya over a white tee. She's laughing mid-sentence, eyes off the lens, hand with fresh henna resting near an iced Spanish latte with condensation. On the table: her phone face-down, a car key, a half-eaten date on a small plate. Bright cool mall-adjacent interior light from big windows camera-right, her left side in soft shadow. Not staged, not retouched, no beauty filter, no smoothing. A photograph, not a painting."*

**Mixed-cast Dubai scene — the anti-homogenization frame.**
> *"A candid phone photo inside a bright Dubai mall food court, 9:16, slight HDR push, handheld tilt. Foreground: a South Asian family sharing biryani. Mid-frame: two young Emirati men in white kanduras and turban-wrapped ghutras walking past with karak cups; a Filipina friend group taking a group selfie; a European couple with shopping bags. Every subject a distinct skin tone and build — light olive, golden tan, deep brown, fair — no two faces alike. Cool even retail lighting with warm food-stall spill camera-left, slight motion blur on passers-by, cleaning trolley at the edge of frame. Not staged, not a photoshoot. A photograph, not a painting."*

**Majlis frame — Nationals-only setting done right.**
> *"A relaxed evening majlis: three Emirati men seated on floor cushions along a carpeted wall, one pouring gahwa from a brass dallah into small finjan cups, a plate of dates and a smoking bakhoor burner on the carpet. All in white kanduras — one clean-shaven with the ghutra off beside him showing a white ghafiya cap, one in a turban-wrapped ghutra, one older with a grey-flecked beard, white ghutra and black agal — three distinct faces, three distinct skin tones from light olive to deep bronze. Warm single tungsten wall-light key camera-right, left sides in shadow, shot on a phone from a seated position, slight tilt, 4:3. Not staged, no readable text. A photograph, not a painting."*

---

## Failure modes & fixes (region-specific)

| Symptom | Fix |
|---|---|
| **Keffiyeh/beard/robe stereotype composite** on a neutral brief | Specify all five casting axes; state grooming (*clean-shaven*) and modern context explicitly |
| **One skin tone across the whole cast** (homogenization) | Assign a named tone + undertone per subject: *"light olive… golden tan… deep brown — no two faces alike"* |
| **Saudi collar/cuffs on an "Emirati" kandura** | *"collarless white kandura with the twisted tassel (farukhah) at the neckline"* |
| **Agal on a turban-wrapped ghutra** | Pick one: *"ghutra + black agal"* OR *"wrapped turban-style, no agal"* |
| **Every woman auto-veiled / niqab default** | State the actual style: *"shayla draped loosely, some hair visible"* / *"no head covering"* (expat cast) / *"niqab"* only if briefed |
| **Skin-tight abaya** | *"loose, flowing black crepe abaya, fabric moving with her step"* |
| **Mosque/dune/Burj backdrop on a lifestyle brief** | Name the real setting (mall, cafeteria, apartment, majlis) and add the local clutter ledger |
| **Climate mismatch** (outdoor picnics in midday sun, sweaters outdoors) | Indoor-AC default; exteriors at golden/blue hour or explicitly harsh bleached noon with its consequences |
| **Gold-and-supercar cartoon luxury** | *"quiet quality — a good watch, a clean interior"*; flex register only when briefed |
| **Model-invented Arabic gibberish** | Never improvise Arabic — quote exact native-checked copy, render on Pro, state RTL; else *"no readable text"* |
| **Warm grade re-tanning the subject** | *"preserve true skin tone under the warm light, white balance on skin"* |
| **All-Khaleeji background crowd in public Dubai** | Cast the crowd to the real mix (see demographic table) unless it's a Nationals-only setting |


<!-- ═══════ FILE: nano-banana-prompter/references/mena_casting.md ═══════ -->

# Nano Banana — MENA deep casting (beyond the Gulf)

The Middle East & North Africa module for everywhere the Gulf file doesn't cover — the **Levant, Egypt & Nubia, the Maghreb, Iraq, and Iran** — plus the region's large non-Arab and non-Muslim peoples (Amazigh, Kurds, Persians, Nubians, Copts, Levantine Christians, Assyrians). Extends `references/global_ethnicity_casting.md` (the five casting axes, tone-lock clause, deep-skin lighting craft, and realism stack all apply). For the **Gulf specifically** (Emirati/Saudi/Khaleeji dress, GCC UGC) use `references/uae_gulf_casting_and_ugc.md`; for **Turkey**, note it sits at the edge of this region and is culturally distinct.

**The three master errors this file kills:**
1. **The "generic Arab" composite** — the model's default is one olive-tan, keffiyeh-and-desert man or one abaya-and-kohl woman. MENA spans fair Levantine and Amazigh registers, golden Egyptian tones, and deep Nubian and Saharan-southern skin — cast by people and place, not by a costume cliché.
2. **"Arab = Muslim = veiled = desert."** The region is religiously plural (Sunni, Shia, Coptic and Levantine Christians, Druze, Alawite, Yazidi, historically Mizrahi Jewish) and mostly urban/coastal/mountain, not dune. Don't auto-veil; don't default to sand.
3. **Collapsing non-Arabs into "Arab."** Persians (Iran), Kurds (Iraq/Iran/Syria/Turkey), Amazigh (Maghreb), and Nubians are distinct peoples with their own dress, features, and language — never render them as generic Arabs.

Core rule (as everywhere): specify the five axes independently — skin tone + features + hair + wardrobe + context — and **vary faces within any same-heritage cast** (*"no two faces alike"*).

---

## Cast by sub-region

| Sub-region | Tone & undertone | Features & hair | Notes |
|---|---|---|---|
| **Levant (Lebanon, Syria, Jordan, Palestine)** | fair-to-olive, warm-neutral; light eyes (green/hazel/blue) occur, esp. Lebanon/Syria | dark wavy-to-curly hair, defined brows and noses, oval faces | religiously plural — Muslim + large Christian communities + Druze; don't default to hijab |
| **Egypt (Nile Delta & Cairo)** | golden-olive to warm medium-brown | dark eyes, thick dark hair, rounded-to-defined features | Copts (Christian) are a major community — a small wrist cross tattoo is a real Coptic marker |
| **Upper Egypt & Nubia (south, toward Sudan)** | deep warm brown to very deep | strong features, dense dark hair | Nubians are a distinct people — deeper skin, own dress and jewelry; use the deep-skin lighting craft, anti-ashy clause MANDATORY |
| **Maghreb — Amazigh (Berber) register** | fair-to-olive, some green/light eyes; ruddy in mountain communities | wavy-to-curly dark hair, strong brows | Amazigh are indigenous North Africans, not Arab; traditional women's **facial/hand tattoos (silver-blue geometric)** belong to older/rural generations and are declining — do NOT default them onto young modern subjects |
| **Maghreb — Arab-Andalusian (cities: Fez, Tunis, Algiers)** | olive to warm medium | dark hair and eyes | Andalusian heritage in dress and music |
| **Sahara & southern Maghreb (Tuareg, southern Algeria/Libya)** | deep brown | Tuareg men veil (the tagelmust, often indigo) — a real distinctive marker | indigo "blue men of the desert" dye rubs off on skin |
| **Iraq** | olive to warm brown; deeper toward the south | dark hair, strong features | Arab majority + large **Kurdish** north (own dress) + Assyrian/Chaldean Christians |
| **Iran (Persian — NOT Arab)** | fair-to-olive, warm; light eyes common | dark-to-brown hair, defined noses and brows | Persian is its own people and language (Farsi); Iran also holds Azeris, Kurds, Baloch, Gilaki — don't render as Arab |

**Vary within every sub-region** — each spans real range; the Levant alone runs from very fair with light eyes to warm olive.

---

## Heritage dress by people & occasion (name the garment, not "Arab robe")

**Levant.** The signature is **tatreez** — hand cross-stitch embroidery on the Palestinian **thobe**, mapping village and status: Ramallah bold red-and-black geometric, Bethlehem fine gold/silver **couching**, Hebron dense deep red-purple. The chest panel is the **qabbeh**. Keffiyeh patterns are political-geographic: **Palestinian black-and-white**, **Jordanian red-and-white**. Everyday modern Levant is ordinary Western/urban dress — reserve heritage dress for weddings, dabke, and cultural occasions.

**Egypt.** Men's **galabeya** (straight-cut, pale, practical; a wide neckline, sometimes an **amamma** turban) — farmers, Sufi dhikr, elders at mosque. Women's rural **galabeya bi wist** (fitted bodice, flared skirt, vibrant print). Sufi dervishes in the spinning **tanoura** (multicolored skirt). Nubian women in bright printed **gargara** with gold.

**Maghreb.** The **djellaba** (long hooded unisex robe) and the **tarbouche/fez**; the **kaftan** and formal **takchita** (two-layer, elaborate Andalusian embellishment, wide **mdamma** belt) for Moroccan women; the Algerian **karakou** (velvet, gold-embroidered jacket + trousers); the **burnous** (men's hooded wool cloak). Amazigh: handwoven vivid textiles, heavy **silver fibula** brooches and jewelry, indigo.

**Iraq / Kurdish.** Arab men in **dishdasha** + keffiyeh/agal; **Kurdish** dress is distinct — men in baggy **rank-o-choxa** trousers + cummerbund + jacket + turban, women in bright layered sequined gowns.

**Iran (Persian).** Modern urban dress predominates; heritage/festive registers draw on rich brocade and, historically, Qajar-era styles; ethnic dress varies (Kurdish, Baloch, Gilaki, Qashqai nomad textiles). Note the **legal hijab** context in public Iran, but private/family and diaspora scenes differ — state the actual scene.

---

## Settings & texture ledger (kills the desert cliché)

- **Levant:** old-city stone alleys and honey-limestone (Jerusalem, Damascus, Beirut), vine-shaded courtyards, cedar and terraced hills, mezze tables, dabke lines, Roman ruins (Baalbek, Palmyra).
- **Egypt:** Cairo's dense balconied streets and ahwa (coffeehouses) with shisha, the Nile and feluccas, Coptic churches, Islamic-Cairo minarets, koshary carts, Nubian riverbank villages painted blue and ochre. (Pyramids exist — but they are not the everyday backdrop.)
- **Maghreb:** medina souks and blue Chefchaouen, riad courtyards with zellige tile and horseshoe arches, tagines and mint tea poured high, Atlas-mountain villages, Saharan dunes only where actually relevant.
- **Iraq:** Tigris/Euphrates, marsh Arab reed houses (mudhif), Baghdad book-market streets, Kurdish green highlands.
- **Iran:** Isfahan's blue-tiled mosques and bazaars, Persian carpets and tea, Alborz peaks, poetry-garden courtyards.

**Truck-art equivalent motifs** (use as accents, not smother): zellige tile, tatreez patterns, Persian tilework, mashrabiya screens, Arabic/Persian calligraphy. Render Arabic/Persian in-image text only on Nano Banana Pro, quoted exactly (RTL) — see `references/text_rendering.md`.

---

## Worked frames

**Levantine grandmother, Ramallah tatreez (festive, warm interior)**
> *An elderly Palestinian woman in a black thobe with bold red-and-black Ramallah cross-stitch tatreez across the qabbeh chest panel, a white headscarf, seated at a laden mezze table in a honey-limestone room, mid-laugh with family. warm tungsten practicals, soft window key camera-left, gently desaturated warm grade. deep real skin texture — mottled colour, fine wrinkle channels, warm subsurface at the ears, wet asymmetric eyes with a matched catchlight; never smooth or plastic. cast Levantine — olive-fair skin, defined features, silver hair. film-scan finish: soft, low contrast, lifted colour-holding blacks, fine grain, faint halation on the lamp. 4:5, clean frame, no readable text.*

**Amazigh man, Atlas mountains (documentary daylight)**
> *A weathered Amazigh (Berber) man in his 60s in a hooded brown wool burnous over a djellaba, standing on a terraced Atlas-mountain slope at golden hour, looking off-lens. fair-olive ruddy mountain skin, green-hazel eyes, grey stubble; MODE D natural daylight, hard low sun with soft sky fill, held bloomed sky. real skin — pores, sun-weathering, broken specular, subsurface glow; never plastic. gently desaturated true colour, one warm anchor in the burnous, fine grain, mountain haze. 3:2, clean frame, no text.*

---

## Cross-contamination & failure-mode table

| Failure | Fix |
|---|---|
| **"Generic Arab" one-face composite** | cast the sub-region + vary faces; name tone + features + hair independently |
| **Auto-veiling every woman** | state the actual scene; Levantine/Egyptian Christians, Druze, and secular/urban women are uncovered; specify hijab only when intended |
| **Desert-and-camel default** | use the settings ledger — cities, mountains, rivers, medinas; deserts only where real |
| **Persian/Kurdish/Turkish rendered as Arab** | name the people and their distinct dress; Persian ≠ Arab (Farsi, own features/dress) |
| **Nubian/Saharan subjects lightened or ashy** | deep-skin lighting craft — expose for the face, specular sheen, warm fill, anti-ashy clause |
| **Amazigh facial tattoos on young modern subjects** | those are older/rural and declining — omit unless the brief is explicitly an elder/heritage portrait, and treat respectfully |
| **Keffiyeh pattern wrong for the story** | Palestinian black-white vs Jordanian red-white vs Gulf/Iraqi styles carry meaning — pick deliberately |
| **Orientalist "Aladdin" fantasy** | ground in real place, real dress, real light; drop harem/genie tropes |
| **Garbled Arabic/Persian signage** | Nano Banana Pro, quote the exact RTL string, or *"no readable text"* |

---

> **Not yet field-validated** (new module, 2026-07-06). Run a scored round on Nano Banana and log it in `references/field_findings.md` before promoting any register to "validated." Expect the model's strongest pulls here to be over-veiling, the desert default, and lightening Nubian/Saharan skin — the fixes above target exactly those.

## Sources
- [Tatreez and the Palestinian Thobe — TATTER](https://tatter.org/tatreez-and-the-palestinian-thobe/) · [Mapping the Jalabiya across MENA — CairoScene](https://cairoscene.com/Styled/Mapping-the-Jalabiya-Across-the-MENA-Region) · [Djellaba — Wikipedia](https://en.wikipedia.org/wiki/Djellaba) · [Traditional Arab dress, Gulf thobe to Moroccan kaftan — Rakwa](https://news.rakwa.com/2025/07/24/traditional-arab-dress-from-the-gulf-thobe-to-the-elegant-moroccan-kaftan/)


<!-- ═══════ FILE: nano-banana-prompter/references/south_asia_casting.md ═══════ -->

# Nano Banana — South Asia deep casting: India & Pakistan

The deep module for the subcontinent — the region the model flattens hardest, because "Indian" and "Pakistani" each cover more internal diversity than all of Europe. Extends the South Asia section of `references/global_ethnicity_casting.md`; the five casting axes, tone-lock clause, and realism stack all apply. For South Asians in the Gulf (the UAE's largest population bloc) see `references/uae_gulf_casting_and_ugc.md`.

> **Field-validated (Round 9, `field_findings.md`):** Tamil deep-tone lock, the no-bindi negation on Pakistani casting, Northeast-Indian explicit-feature casting, shalwar-kameez-daily + waistcoat, and the Pashtun register (pakol, light eyes) all confirmed live on Pro. Caveats from the round: Indian celebratory contexts add Hindu markers unprompted (negate on Muslim/Christian briefs); attributes slip between variants — restate the full identity block every generation; pin UGC register on dusk frames (*"muted realistic colors, no HDR glow"*).

**The two master errors this file kills:**
1. **The one-face "Indian":** the model's default South Asian is a single wheatish-tan, North-Indian-ish composite. India casts by REGION, not by country.
2. **"Pakistan = India lite":** the model renders Pakistanis as generic Indians with the wrong cultural markers (bindis on Pakistani women is a real, recurring cross-contamination fail). Pakistan is a different casting system — different ethnic map, different daily national dress, different religious register.

---

## INDIA — cast by region

India runs a documented north–south pigmentation cline plus an East-Asian-featured Northeast, with distinct undertone families per region. Name the state/community and the model has something real to aim at.

| Region | Tone spectrum & undertone | Features & hair | Notes |
|---|---|---|---|
| **Punjab / Haryana / Delhi (NW)** | fair to wheatish to tan, warm | taller builds common, straight thick hair, defined noses | Sikh casting is its own register (below) |
| **Kashmir / Himachal / Uttarakhand** | fair, cool-to-neutral; light eyes occur | sharp features, straight-to-wavy hair | often mis-rendered as generic "Indian tan" |
| **Hindi belt (UP / Bihar / MP / Rajasthan)** | wheatish to medium brown, warm | the model's default zone — still enumerate per subject | Rajasthan: moustache culture, vivid turban colors are regional-rural, not urban |
| **West (Gujarat / Maharashtra)** | golden-warm medium tones | rounded-to-defined mix | "golden warmth" is the Gujarati undertone signature |
| **East (Bengal / Odisha / Assam plains)** | brown to deep, **olive undertone** common | softer rounded features, large expressive eyes, wavy hair | olive undertone is the Bengali signature — say it |
| **South (Tamil Nadu / Kerala / Telangana / Andhra / Karnataka)** | warm deep brown to very deep, some with blue-black depth | strong brows, dense near-black hair (often oiled/braided), prominent noses | use the full deep-skin lighting craft (global file); the anti-lightening clause is MANDATORY — both the model and Indian media bias pull lighter |
| **Northeast (Nagaland / Manipur / Mizoram / Arunachal…)** | fair to golden, neutral | East/Southeast Asian features — monolids, straight black hair | the model essentially never produces this on "Indian" — must be explicitly specified; these are Indians too |

**Vary within region too** — every register above spans real variation; *"no two faces alike"* still applies.

### Markers with meaning (use only in the right context)

- **Bindi** — worn by many Hindu women (also as fashion); not on Muslim/Christian casting by default.
- **Sindoor** (vermilion in the hair parting) + **mangalsutra** necklace — married Hindu women specifically.
- **Sikh men:** the **dastar** (turban — state the style: crisp pointed Patiala vs rounded UK-style), uncut beard (flowing or fixed/rolled), **kara** steel bangle. Never a generic "Indian turban"; never on non-Sikh casting.
- **Nath** nose ring (bridal/regional), **gajra** jasmine strand in the hair (South Indian, everyday-to-festive), **tilak** on temple-visit frames.
- Indian Muslim and Christian communities are huge — brief their markers deliberately (hijab styles, Sunday-church wear in Kerala/Goa).

### Wardrobe — modern first

**Urban modern:** metros are mostly western/fusion — men in shirt-trousers or tees (a man in daily kurta-pajama is casual-home or festive, not office); women split western / **kurti over jeans or leggings** / daily sari depending on region, age, profession. Daily cotton saris remain genuinely everyday for many women (teachers, government offices, older generations, Bengal, the South).

**Heritage & occasion (name the garment + region):**
| Garment | Specifics |
|---|---|
| **Sari by region** | Banarasi silk (North bridal), **Kanjeevaram** silk with gold zari (South weddings), Kerala **kasavu** (cream + gold border, Onam), Bengali **lal-paar** (white/red border, Durga Puja), Maharashtrian **Nauvari** (nine-yard) |
| **Salwar kameez / churidar + dupatta** | northern daily-to-smart |
| **Lehenga choli** | weddings/sangeet — heavy embroidery, kundan/polki jewelry |
| **Sherwani + churidar** | grooms; **bandhgala/Nehru jacket** for smart-formal |
| **Veshti / mundu / lungi** | South Indian men — temple, festive, home; crisp white veshti + shirt is real Tamil formal |
| **Anarkali, patiala suit** | occasion registers |

**Beauty registers:** South Indian festive = oiled center-parted braid + gajra + gold temple jewelry; North bridal = red/maroon + heavy kundan + mehndi to the elbows; urban glam = soft-glam brows + kajal. Everyday realism: kajal is the one near-universal makeup cue.

> **Paste-ready — Tamil wedding guest:** *"A Tamil woman in her 50s at a Chennai wedding, deep brown skin with warm undertone — expose for her face, preserve the deep tone under the warm hall light, no lightening, no ashy cast — silver-streaked black hair oiled into a low braid with a jasmine gajra, gold temple-jewelry earrings and bangles, a deep-green Kanjeevaram silk sari with gold zari border, laughing mid-conversation, warm tungsten wash with a soft specular sheen on her cheekbones."*

> **Paste-ready — Delhi UGC:** *"Front-camera selfie in a Delhi metro carriage, 9:16, HDR push, mild over-sharpening. A Punjabi man in his mid-20s, wheatish-tan skin with visible pores and stubble, thick black hair with a fade, wearing a grey hoodie, one earbud in, mid-grin with eyes just off lens; behind him the crowded carriage — a Sikh man in a navy dastar reading his phone, women in kurtis, office workers — slight motion blur, cool metro lighting. Not staged, not retouched. A photograph, not a painting."*

---

## PAKISTAN — a different casting system

**Ethnic map (approx. shares):** Punjabi ~45%, Pashtun ~15%, Sindhi ~14%, Saraiki ~8%, Muhajir (Urdu-speaking, Karachi-centred) ~8%, Baloch ~4% — plus northern peoples (Gilgiti, Balti, Hunza/Burusho, Chitrali/Kho, Kalash) and Hazara. Name the group; each has a distinct register:

| Group | Casting register |
|---|---|
| **Punjabi** | fair-to-wheatish through tan, warm undertone; the same ethnic stock as Indian Punjab — the *difference is dress and markers, not faces* |
| **Pashtun** | often lighter skin (fair to light tan), prominent cheekbones, deep-set eyes, strong straight noses; green/hazel eyes and brown hair occur naturally; taller builds; men's full-beard register common |
| **Sindhi** | wheatish to deep tan, warm |
| **Baloch** | tan to deep bronze, weathered outdoor register in rural casting |
| **Muhajir / urban Karachi** | the full subcontinental spectrum — cast wide |
| **Northern (Hunza/Gilgit/Chitral)** | fair, ruddy-cheeked mountain register, light eyes not rare |
| **Hazara** | Central/East Asian features — a distinct face the model won't produce unnamed |

### The single biggest India/Pakistan wardrobe difference

**Shalwar kameez is Pakistan's real national DAILY dress — for men as much as women.** A Pakistani man in a solid-colour shalwar kameez (white, pastel, stone, grey) — often with a **waistcoat** over it — is normal office, street, mosque, and dinner wear at every social level. Rendering Pakistani men default-western (or Pakistani daily life in Indian registers) is the flattening error. Urban Karachi/Lahore/Islamabad also wear western dress — pick one register per subject and say it.

**Men's kit:** shalwar kameez + waistcoat, **Peshawari chappal** sandals, white kurta-shalwar for Friday prayers; caps by region — **pakol** (soft wool roll-brim, Pashtun/northern), **Sindhi topi** + **ajrak** shawl (the block-printed crimson/indigo cloth — Sindh's identity textile), karakul **Jinnah cap** (formal/older). Grooming: clean-shaven through stubble to full beard — all common; state it.

**Women's kit:** shalwar kameez in **printed lawn** — Pakistan's designer-lawn culture is its own institution; the light printed cotton suit is THE summer register — with the **dupatta** draped (state how: across the chest, loosely over the head, or a pinned hijab — three different looks, all real). Urban: kurta + cigarette trousers, or western in elite circles. Kajal + groomed brows is the everyday face; bridal is heavy — deep red/jewel **lehenga or gharara/sharara** (the flared-cuff trouser silhouette is a Pakistani/Muslim-wedding signature), gold jadau sets, mehndi; **mehndi-night** dress code is yellows/greens/orange with marigolds.

### Religious & cultural register

Pakistan is overwhelmingly Muslim: **no bindi, no sindoor, no mangalsutra on Pakistani casting** (the #1 cross-contamination fail); Friday-prayer and Ramadan/iftar/Eid rhythms are natural content moments; the **Pashtun turban** (loose wrap with a hanging tail, often over a cap) is NOT a Sikh dastar — different wrap, different meaning. Minorities are real (Hindu Sindhi, Christian Punjabi communities) — cast them deliberately, never accidentally.

### Settings that read as Pakistan

Lahore (Mughal-era brick, Badshahi silhouettes, food-street smoke, spring haze), Karachi (sea-breeze corniche, painted buses, dense mixed streets), Islamabad (wide clean avenues, Margalla hills backdrop), northern areas (Hunza terraces, poplar valleys). Texture ledger: **truck art** (riotously painted Bedfords), chai **dhaba** with karak-style doodh patti in glass cups, rickshaws, street cricket with a taped tennis ball, charpai rope beds, load-shedding generators, Ramzan bazaar lights.

> **Paste-ready — Lahore dhaba UGC:** *"Front-camera selfie at a roadside dhaba at dusk, 9:16, HDR push. A Pakistani Punjabi man in his late 20s, wheatish skin with visible pores and a trimmed beard, thick black hair, wearing a stone-grey shalwar kameez with a dark waistcoat, Peshawari chappals visible where he sits on a charpai. He's mid-laugh, eyes off lens, holding a glass cup of doodh patti chai; behind him a painted truck's tailgate glows under a bare bulb, steam off the tea stall, a friend motion-blurred mid-gesture. Mixed warm bulb and cool dusk light. Not staged, not retouched. A photograph, not a painting."*

> **Paste-ready — Karachi office, lawn season:** *"A Pakistani woman in her early 30s at her desk in a Karachi office, golden-wheatish skin — preserve the true tone under the cool office light — kajal-lined eyes, dark hair in a loose low bun, wearing a printed lawn kameez in blue-and-white florals with the dupatta draped across one shoulder, small gold studs. She's mid-explanation on a video call, hands gesturing; on the desk a chai cup, her phone, a stack of files; window light camera-left, her right cheek in soft shadow."*

> **Paste-ready — Pashtun elder:** *"An elderly Pashtun man outside a Peshawar mosque after Friday prayer, fair weathered skin with deep static lines and sun spots, pale green eyes, a full white beard, wearing a white kurta-shalwar with a brown wool pakol, prayer beads in hand, mid-conversation with someone off-frame. Hard afternoon sun from camera-right, the left side of his face in shadow, worshippers motion-blurred behind. A photograph, not a painting."*

### Bangladesh (adjoining register, one paragraph)

Bengali casting (see the East-India row: brown-to-deep tones, olive undertone, softer rounded features) with its own dress economy: women split sari (daily, incl. white/red lal-paar for Pohela Boishakh) and shalwar kameez; men in shirts urban, **lungi** at home/rural, white **panjabi** (the Bengali kurta) for Eid/Friday. Dhaka texture: cycle-rickshaws with painted hoods, river ghats, garment-district streets, monsoon sheen.

---

## India/Pakistan failure modes & fixes

| Symptom | Fix |
|---|---|
| **Bindi/sindoor on Pakistani (or Indian Muslim) women** | *"no bindi, no sindoor"* + state the actual markers (kajal, dupatta style) — check every output; this fail recurs |
| **Sari as Pakistani daily wear** | shalwar kameez / lawn suit registers; sari only for specific communities/occasions if briefed |
| **Pakistani men rendered default-western (or default-Indian)** | *"solid-colour shalwar kameez with a waistcoat"* — the national daily register |
| **Sikh dastar on Muslim casting / generic "Indian turban"** | dastar = Sikh only; Pashtun turban described as its own wrap; Rajasthani safa is regional-festive |
| **One wheatish composite face for all of South Asia** | cast by region/community from the tables; enumerate per subject |
| **South Indian / Sri Lankan subjects lightened** | tone-lock every turn: *"deep brown, warm undertone — do not lighten"* + deep-skin lighting craft |
| **Northeast Indians un-renderable as Indian** | state it: *"an Indian woman from Nagaland, East Asian features, monolid eyes, straight black hair"* |
| **Lawn prints rendered as solid fabric** | *"printed lawn cotton, small floral block print visible in the weave"* |
| **Dupatta physics wrong (glued/rigid)** | *"light chiffon dupatta draped across the chest, falling in soft folds, moving with her"* |
| **Kanjeevaram/Banarasi genericized** | name the sari + its signature (*"gold zari border"*, *"heavy silk sheen"*) |
| **Punjabi confusion across the border** | same faces, different systems: Indian Punjabi (Sikh/Hindu markers possible, Indian dress economy) vs Pakistani Punjabi (Muslim register, shalwar-kameez daily) — pick the country and its markers |


<!-- ═══════ FILE: nano-banana-prompter/references/southeast_asia_casting.md ═══════ -->

# Nano Banana — Southeast Asia deep casting

The module for the region the model flattens into a single "East Asian" face — **maritime SEA** (Indonesia, Malaysia, Philippines, Singapore, Brunei) and **mainland SEA** (Vietnam, Thailand, Cambodia, Laos, Myanmar). Extends `references/global_ethnicity_casting.md` (five casting axes, tone-lock, deep-skin lighting, realism stack all apply). SEA holds ~700 million people across hundreds of ethnicities, three major religions, and a skin-tone range from fair to deep brown to **Melanesian** — none of which the default "Asian" render captures.

**The three master errors this file kills:**
1. **The "generic East-Asian" default.** The model renders SEA subjects as pale, monolid, North-East-Asian. Real SEA runs warm-brown Malay/Filipino/Indonesian tones, rounder and more varied features, wavy-to-curly hair — and in eastern Indonesia, Timor, and parts of the Philippines, **Melanesian** subjects with deep skin and tightly-curled hair. Cast the actual people.
2. **One-country-for-all.** Thai temples, áo dài, and conical hats get sprayed onto every SEA brief. Each country (and each ethnicity within it) has distinct dress and settings.
3. **Erasing the religious/cultural map.** Indonesia and Malaysia are majority-Muslim (hijab common); the Philippines and Timor-Leste are majority-Christian; Thailand, Cambodia, Laos, Myanmar are majority-Theravada-Buddhist; Bali is Hindu. Don't default to one.

Core rule: specify skin tone + features + hair + wardrobe + context independently, and **vary faces within any same-heritage cast**.

---

## Cast by country / people

| People | Tone & undertone | Features & hair | Notes |
|---|---|---|---|
| **Javanese / Sundanese (Indonesia)** | warm light-brown to medium-brown | softer rounded features, straight-to-wavy black hair | world's largest Muslim population — hijab common but far from universal |
| **Batak / Minangkabau / other Indonesian** | medium to deeper brown | varied strong features | hundreds of ethnicities; don't homogenize |
| **Balinese (Indonesia)** | warm medium-brown | Hindu culture, temple dress | distinct Hindu register — sarong + sash, temple ceremonies |
| **Papuan / eastern Indonesian & Timorese** | deep brown | **Melanesian** — tightly curled hair, broad features | the model almost never produces this on "Indonesian/Asian" — must be specified explicitly; these are SEA people too |
| **Malay (Malaysia/Brunei/Singapore)** | warm light-to-medium brown | rounded features, straight-wavy hair | Malaysia is multiethnic: Malay + large Chinese + Indian (Tamil) populations |
| **Filipino (Philippines)** | warm tan to medium-brown; wide range | Austronesian base; rounded-to-defined; straight-wavy hair | plus **mestizo** (Spanish/Chinese admixture, lighter), **Chinese-Filipino**, **Moro** (Muslim Mindanao), and darker indigenous (Igorot, Lumad, Aeta — Aeta are Negrito, deep skin + curly hair) |
| **Kinh Vietnamese** | fair-to-light warm | often lighter, straight black hair, defined | 53 recognized minorities (Hmong, Tày, Dao…) with distinct highland dress |
| **Thai (Central)** | light-to-medium warm brown | straight black hair | plus Chinese-Thai (lighter), Isan (Lao-related, often deeper), and hill tribes (Karen, Akha, Hmong, Lisu) |
| **Khmer (Cambodia)** | medium-to-deeper warm brown | rounded-to-strong features, wavy-straight hair | often deeper-toned than Thai/Viet — resist the lightening pull |
| **Lao** | light-to-medium warm brown | straight black hair | closely related to Isan Thai |
| **Bamar (Myanmar)** | light-to-medium warm brown | straight black hair; **thanaka** yellow cheek paste is a distinctive everyday marker | plus Shan, Karen, Kachin, Chin, Mon, and Rohingya (Muslim minority) — a mosaic, not one look |

**Vary within every group.** Filipino and Indonesian casts especially span a very wide tone range in a single crowd — show it.

---

## Heritage dress by country & occasion

- **Indonesia:** **batik** (wax-resist patterned cloth, worn everywhere from formal to daily), **kebaya** (fitted lace/embroidered blouse) + **kain/sarong**, **beskap** and **blangkon** cap for Javanese men; Balinese temple dress (sarong + **udeng** headcloth + sash). Aceh and much of the country: hijab.
- **Malaysia / Brunei:** **baju kurung** (loose blouse + long skirt) and **baju kebaya** for women, **baju melayu** + **songkok** cap + **sampin** for men.
- **Philippines:** **barong tagalog** (sheer embroidered piña/jusi shirt) for men; **terno** / **Maria Clara** with stiff **butterfly sleeves** for women. Christian-majority; Moro dress (malong tube cloth) in the Muslim south.
- **Vietnam:** **áo dài** (long split silk tunic over trousers) + **nón lá** (conical hat); **áo gấm** brocade for men; highland-minority indigo and batik.
- **Thailand:** **chut thai** — **pha nung/pha sin** wrap, blouse, and diagonal **sabai/pha biang** silk sash; monks in saffron robes.
- **Cambodia:** **sampot** (wrap trousers/skirt) and the checked **krama** scarf.
- **Laos:** **sinh** (woven tube skirt) + **pha biang** sash.
- **Myanmar:** **longyi** (men) / **htamein** (women) sarong + **eingyi** blouse, **gaung baung** headwrap; **thanaka** paste on the cheeks; Chin heritage (older women's facial tattoos — declining, handle respectfully).

Everyday modern SEA is ordinary global/urban dress — reserve heritage garments for festivals, weddings, temple, and cultural contexts unless the brief is traditional.

---

## Settings & texture ledger

- **Indonesia:** Jakarta density and warungs, Balinese rice terraces and temples, batik workshops, volcanic peaks, Sumatran jungle, Papuan highlands.
- **Malaysia/Singapore:** shophouse rows and hawker centres, KL/Marina skylines, kampung stilt houses, mosque + temple + church in one street.
- **Philippines:** jeepneys, sari-sari stores, bahay-kubo and Spanish-colonial churches, banca outriggers, rice terraces (Banaue), Manila density.
- **Vietnam:** motorbike-swarm streets, French-colonial + lantern old towns (Hội An), rice paddies and conical-hat farmers, pho stalls.
- **Thailand:** wats and saffron monks, floating markets, street-food carts, tuk-tuks, Bangkok neon.
- **Cambodia/Laos/Myanmar:** Angkor and Bagan temple plains, Mekong life, alms-round at dawn, teak monasteries.

Use temple/landmark backdrops sparingly — everyday SEA is markets, streets, homes, and paddies, not a postcard.

---

## Worked frames

**Filipino barong, wedding (warm interior)**
> *A Filipino man in his 30s in a sheer cream barong tagalog with fine calado embroidery over an undershirt, at a family wedding in a warm church hall, mid-conversation. warm tan skin, defined Austronesian features, black hair; soft window key + warm practicals, gently desaturated warm grade. real skin — pores, cheek sheen, broken specular, subsurface at the ears, wet asymmetric eyes with a matched catchlight; never plastic. film-scan finish: soft, low contrast, lifted colour-holding blacks, fine grain. cast Filipino, varied faces. 4:5, clean frame, no text.*

**Papuan girl, highland daylight (anti-erasure test)**
> *A young Papuan (Melanesian) girl in eastern Indonesia, deep brown skin, tightly-curled dark hair, broad warm features, a simple modern tee, standing in a green highland village at golden hour, a shy half-smile. MODE D natural daylight, hard low sun with soft sky fill, held bloomed sky. deep-skin lighting — expose for the face, specular sheen on the cheekbones, warm subsurface, absolutely no ashy cast; real skin texture, never plastic. gently desaturated true colour, fine grain, mountain haze. 3:2, clean frame, no text.*

---

## Cross-contamination & failure-mode table

| Failure | Fix |
|---|---|
| **"Generic East-Asian" render (pale, monolid)** | name the people + warm-brown tone + rounder/varied features + wavy hair; tone-lock against the lightening pull |
| **Melanesian Papuans erased** | specify explicitly — deep brown, tightly-curled hair, broad features; deep-skin lighting craft |
| **Khmer/Isan/Filipino lightened** | anti-lightening clause; these skew deeper than the Thai/Viet default the model reaches for |
| **One-country dress on all SEA** | pick the country's actual garment (barong ≠ áo dài ≠ batik ≠ longyi) |
| **Temple/landmark backdrop everywhere** | use the settings ledger — markets, streets, homes, paddies |
| **Auto-hijab or auto-no-hijab** | Indonesia/Malaysia Muslim (often hijab), Philippines Christian, mainland Buddhist — state the actual context |
| **Homogenized crowd** | *"no two faces alike"*, span the real tone range (esp. Filipino/Indonesian) |
| **Chin/older facial tattoos as default** | omit unless an explicit elder/heritage portrait; treat respectfully |
| **Thanaka/conical-hat as the only "SEA" signifier** | use as a real detail in context, not a costume shortcut |

---

> **Not yet field-validated** (new module, 2026-07-06). Log a scored round in `references/field_findings.md` before trusting any register. Expect the model's strongest pulls to be the East-Asian-default face, lightening of Khmer/Filipino/Melanesian skin, and one-country dress clichés — the fixes above target exactly those.

## Sources
- [ASEAN national costumes — Thaiest](https://thaiest.com/blog/national-costumes-of-southeast-asian-countries) · [Traditional costumes of ten SEA countries — VietnamNet](https://vietnamnet.vn/en/traditional-costumes-of-ten-southeast-asian-countries-E97197.html) · [Woven Identities: ASEAN clothing traditions — Philstar](https://www.philstar.com/lifestyle/sunday-life/2016/01/16/1543267/woven-identities-clothing-traditions-asean-block)


<!-- ═══════ FILE: nano-banana-prompter/references/pakistan_ads_and_directors.md ═══════ -->

# Nano Banana — Pakistani advertising: framing, set design, directors & platform layout

The Pakistan-market advertising module. How Pakistani TVCs and digital ads are actually shot, the genre registers, the set/environment ledger, the local ad-director signature blocks, and how to reframe a hero still for YouTube and Instagram. This file makes the *ad frame*; it does **not** repeat casting or generic ad grammar:

- **Who is in the frame** → `references/south_asia_casting.md` (Pakistan ethnic map, shalwar-kameez-as-daily-dress, the no-bindi rule) and `references/global_ethnicity_casting.md` (five casting axes, tone-lock, deep-skin lighting).
- **Generic ad-framing grammar** (packshot angles, end-frame lockup, hand-model, scale discipline, built sets, splash/steam elements) → `references/commercial_framing_and_set_design.md`. This file adds only what is Pakistan-specific.
- **Assembling the finished post** (copy, type system, safe zones, carousel) → `references/creative_posts_copy_type_layout.md`. **Urdu / bilingual in-image text** → `references/text_rendering.md` (quote the exact Urdu string, name the nastaʿlīq/naskh style, render on Nano Banana Pro).
- **Director/DP signature-block grammar** → `references/director_styles_and_film_frames.md`. Same rule applies here: **never use a director's name alone — paste 3–4 concrete signatures.**

> **Field-validated (Rounds 10–11, `field_findings.md`) — ImagineArt, 2026-07-06.** The Ramadan iftar key-art register (R10, 20/22), the humor-telecom register, the FMCG masala food hero (R11, both PASS strong), and the Asim Raza emotional director block (R12, 21/22) all confirmed. Other registers/director blocks remain provisional until individually tested. Nano Banana makes **stills** — key art, thumbnails, posters, packshots, storyboard frames. For the moving TVC itself, hand the hero still to `seedance-2-prompter` / `kling-prompter`.

---

## 1. The Pakistani ad genre registers (paste-ready component blocks)

Like the film/commercial look blocks: never say "make it a Pakistani ad" — the model averages it to a generic South-Asian stock frame. Paste the register's components. One register per frame.

| Register | Component block |
|---|---|
| **Ramadan / Eid emotional (the flagship)** | warm tungsten + candle/fairy-light practicals, iftar *dastarkhwan* laden with dates, pakoras, fruit chaat, jug of Rooh Afza; three-generation family mid-reach at the table, soft golden grade, a held emotional beat (reunion, first bite at azaan), gentle haze, shallow focus on hands and faces |
| **Humor telecom (Ufone / Jazz register)** | bright even sitcom-flat light, saturated everyday palette, a mundane domestic or street setup with one absurd twist, expressive mid-reaction faces, character-comedy blocking (2–4 people), clean readable staging so the gag lands |
| **Emotional telecom (connection register)** | long-lens compression, golden-hour or blue-hour, a phone/video-call moment bridging distance (overseas son, village mother), single tear-catch light on the face, muted warm grade, negative space for the "connection" idea |
| **FMCG masala / food (Shan / National register)** | overhead and 25° hero of a *degh* or plated biryani/nihari, backlit steam ribbons, oil sheen and spice-red saturation, hands garnishing or serving, warm kitchen practicals, "ghar ka khana" homeliness, macro spice-texture cutaway |
| **Family-saga / durable goods (MoltyFoam register)** | soft window-lit domestic interiors, a life-milestone arc (daughter childhood → wedding), the product as silent witness in frame, warm nostalgic grade, tender parent-child blocking, lived-in set with real "today" clutter |
| **Jingle-driven FMCG (Peek Freans Sooper register)** | bright cheerful daylight, "seedhi saadhi khushi" everyday joy — tea break, gully cricket, family gathering, traffic — saturated friendly palette, ensemble candid energy, product shared not sold |
| **Lawn / fashion campaign** | high-key editorial daylight or studio strobe, model in a printed *lawn* three-piece, dupatta in motion, pastel or jewel colorway, heritage architecture or garden backdrop, magazine-clean styling, poster copy space |
| **Youth mobilink / brand-anthem** | energetic wide-to-close cutting energy in one frame, urban rooftops / murals / PSL cricket colors, diverse young cast mid-movement, high-saturation contemporary grade, brand-color accent lighting |
| **Bank / corporate trust** | blue-hour glass architecture or warm office, long-lens compression, one sincere human moment (small business owner, farmer, student) against institutional scale, clean mid-grey-to-warm grade |
| **Social / PSA (Surf Excel "Daag Achhe Hain" register)** | naturalistic available light, a child or ordinary person doing a small good deed, honest mess/stain celebrated not hidden, documentary-warm grade, real street or courtyard, emotion over polish |

**The through-line of Pakistani advertising:** emotion and cultural sincerity over hard selling — family, diaspora longing, festival, everyday joy, and humor with a twist carry the brand. Build the *feeling* first, place the product as the second read.

---

## 2. How Pakistani ads are actually shot (production reality → prompt cues)

- **Warm, golden, practical-lit.** The dominant look is warm tungsten + festive practicals (fairy lights, candles, lanterns), golden-hour exteriors, and soft window key indoors. Translate "cinematic lighting" into a *sourced* recipe: *"warm tungsten key from a table lamp camera-left, fairy-light bokeh behind, soft falloff, warm amber grade."*
- **Faces and hands do the work.** Emotional close-ups and insert shots of hands (serving food, holding a phone, a father's hand on a shoulder) are the core visual currency. Stack the realism layer (`references/realism_and_ugc.md`) — pores, subsurface scattering, real skin — so the emotion reads.
- **Homes are often built sets.** A documented industry habit: many "Pakistani home" ads are shot on studio sets (sometimes abroad — Turkey, Dubai, Thailand) dressed to look domestic. So you can prompt an idealized-but-believable interior; it doesn't need real-location grit unless the brief wants PSA realism.
- **Multi-generational casting is the norm.** Grandparents + parents + kids in one frame is the default family unit, not the nuclear couple.
- **Bilingual / Urdu supers.** Taglines and jingles are usually Urdu (often nastaʿlīq) or Roman-Urdu, sometimes bilingual. Render text on Nano Banana Pro; quote the exact string (`references/text_rendering.md`).
- **Saturated, festive color.** Pakistani ad palettes run warmer and more saturated than Western minimal-ad grades — reds, golds, greens, printed textiles. Don't default to muted teal-orange.

---

## 3. Pakistani-specific framing grammar (TVC shots → still frames)

Generic packshot/end-frame/hand-model grammar lives in `references/commercial_framing_and_set_design.md`. The frames below are the ones that recur specifically in Pakistani ads:

- **The iftar / dastarkhwan overhead.** True 90° or 45° high angle over a spread cloth loaded with dates, pakoras, samosas, chaat, jalebi, a Rooh Afza jug; hands reaching in from the edges; steam and warm light. *"45° high angle over a laden Ramadan dastarkhwan, hands reaching in from three sides, backlit steam, warm practical glow."*
- **The reunion / doorway reveal.** A returning family member framed in a doorway, family turning toward them; look-room on the arrival side. Pairs with emotional telecom and Eid registers.
- **The three-generation family wide.** Grandparent-parent-child arranged in depth (foreground/subject/background), warm interior, product used mid-scene. State the generations explicitly so the model doesn't collapse to one couple.
- **The emotional single (tear-catch).** Tight-to-medium close-up, one soft key catching a glistening eye, muted warm grade, mid-thought not posed. Core of Ramadan/telecom emotional spots.
- **The product-in-hand serve.** Hands presenting the food/product to the family — the Pakistani version of the hand-model frame, but warm and communal rather than clinical. Label to camera, natural finger compression.
- **The gully / mohalla ensemble.** Street-cricket or neighborhood group mid-action in a narrow lane; found-composition energy, washing lines and painted walls behind. Core of jingle-FMCG and youth registers.

---

## 4. Pakistani environment & prop ledger (set-design layer)

Give the set a "today" layer of the right regional objects — this is what kills the generic-South-Asian look. Pick a setting, then stack 3–6 of its props.

| Setting | Prop / texture stack |
|---|---|
| **Home interior (middle-class)** | patterned floor tiles or terrazzo, a *charpai* or wooden sofa-set, embroidered cushions, wall clock, framed calligraphy (Ayat-ul-Kursi / Bismillah), ceiling fan, steel water cooler, sheer curtains with warm light |
| **Ramadan / Eid home** | fairy lights, star-and-crescent decor, dates on a tray, Rooh Afza jug, prayer mat and cap folded aside, henna-hands on the women, new-clothes crispness at Eid |
| **Kitchen** | steel *degh* / pateeli, spice masala tins, rolling *chakla-belan*, gas stove flame, chopped coriander and green chilies, marble or steel counter, steam |
| **Mohalla street / gully** | narrow lane, painted/whitewashed walls, tangled overhead wires, washing lines, a hand-cart (*thela*), motorbike, painted shop signage in Urdu, dust-warm light |
| **Dhaba / roadside eatery** | truck-art color accents, steel tables, a *tandoor*, giant tea kettle (*doodh patti*), plastic chairs, hanging bananas, chalk menu in Urdu |
| **Bazaar** | dense stalls, hanging fabrics/bangles, fruit pyramids, brass and copper, crowd depth, string lights, saturated chaos |
| **Rooftop** | water tanks, satellite dishes, drying laundry, city skyline haze, kite-flying (Basant register), golden-hour warmth |
| **Wedding / shaadi** | marigold and rose *phool* strings, string lights, *mehndi* stage, gold-and-red textiles, dhol, ornate *rilli*/embroidery, festive crowd |
| **Village / rural** | mud-brick or brick walls, fields, buffalo/cattle, hand-pump, *charpai* under a tree, tractor, dupatta-covered women, earthy warm palette |

**Truck-art** is the single most identifiable Pakistani visual motif — chrome-bright florals, calligraphy, ornamental borders, jingling chains. Use it as an accent (dhaba, a truck, decorative panel) — powerful but don't smother every frame in it.

---

## 5. Casting & wardrobe for ads (pointer + occasion quick-table)

Full casting is in `references/south_asia_casting.md` — Pakistan's ethnic map (Punjabi, Pashtun, Sindhi, Baloch, Muhajir, northern peoples, Hazara), the tone-lock, and the **no-bindi / no-sindoor on Pakistani casting** rule. Vary faces within any same-ethnicity cast. Quick ad-wardrobe by occasion:

| Occasion | Wardrobe cues |
|---|---|
| **Everyday** | shalwar kameez (men often with waistcoat/*sadri*), women in kameez + dupatta or printed lawn suit, kids in casual western-mix |
| **Eid / festive** | crisp new shalwar kameez, embroidered/printed lawn, sherwani or bandhgala for men, *khussas*, women in vibrant three-piece with worked dupatta, henna |
| **Wedding** | heavy embroidered gharara/sharara/lehenga, sherwani, gold jewelry (*jhumka*, *tikka*, *nath*), red-gold palette |
| **Corporate / urban modern** | shirt-trouser or kurta with jeans, women in fusion kurta or western-smart, dupatta optional |
| **Rural** | simpler cotton shalwar kameez, turban or *pakol* (Pashtun), *ajrak* (Sindhi), chador for women |

Default register is warm and aspirational-but-relatable, not high-fashion, unless it's a lawn/fashion campaign.

---

## 6. Pakistani ad-director signature blocks

Rule from `director_styles_and_film_frames.md`: **never use the name alone — paste the signatures.** These are the directors who set the benchmark for the modern Pakistani ad film.

| Director | Paste these signatures |
|---|---|
| **Asim Raza** (The Vision Factory) | soulful emotional narrative, folk-and-family motifs fused with polished modern cinematography, warm aspirational grade, meticulous aesthetic beauty, tender human close-ups, music-video lyricism — *"a warm, beautifully lit family moment, folk-cultural texture, emotion carried in a held look"* |
| **Jami** (Azad Film Co.) | high-impact, bold and visually inventive, strong art direction and concept, cinematic contrast, striking single-image ideas, premium multinational-brand gloss — *"a bold high-concept frame, dramatic light, immaculate art direction, one strong visual idea"* |
| **Ahsan Rahim** (Tadpole Films) | witty character-comedy timing, bright readable staging, pop-culture energy, celebrity-led, music-video pace, the twist landed cleanly — *"bright even light, expressive comic reaction, clean staging for the gag, saturated everyday palette"* |
| **Saqib Malik** | elegant, fashion-literate, refined styling and color, editorial polish, women-centric beauty and grace — *"editorial-clean styling, refined palette, graceful posed elegance, beauty-lit"* |
| **Asad-ul-Haq** | crafted, design-forward, controlled color and composition, contemporary cool, strong graphic sensibility — *"considered composition, controlled palette, modern graphic restraint"* |
| **Adnan Malik** | naturalistic, sincere, human-documentary warmth, understated emotion — *"available-light naturalism, sincere unposed emotion, warm honest grade"* |
| **Second-gen (Soheb Akhtar, Babar Sheikh, Murtaza Chaudhry, Ayesha Jalil, Farooq Manan, Omair Nasir Ali)** | the current working benchmark — polished local production, business-driven storytelling, strong technical execution; pair the name with the *register* you want (emotional, comedic, food, fashion) rather than relying on the name |

Pick ONE director register per frame and pair with subject + one light idea. Stacking two cancels both.

---

## 7. Global ad-director blocks worth borrowing (advertising vocabulary)

When the brief wants a specific *ad* aesthetic beyond the local registers — many of the best commercial looks come from directors who built their DNA in advertising. Paste signatures, never the name alone.

| Register | Paste these signatures |
|---|---|
| **Ridley Scott** (ad-mode) | epic mini-film production value, atmospheric haze and shafts, painterly chiaroscuro, monumental scale, textured period or future worlds — *"smoke-shafted light, epic scale, painterly contrast, cinematic grandeur"* |
| **Michael Bay** (ad-mode) | hero low angles, orange-teal gloss, lens flares, rotating hero shot, high-energy polish, sunset backlight — *"low heroic angle, orange-teal grade, anamorphic flare, glossy high-octane sheen"* |
| **Spike Jonze** | kinetic DIY naturalism, playful surreal premise, handheld candor, emotional whimsy — *"loose handheld energy, one whimsical real-world twist, warm naturalism"* |
| **David Fincher** (ad-mode) | clinical precision, locked/smooth motion, green-amber low-key, immaculate sharpness, sourced practicals — *"controlled underexposure, green-amber grade, flawless sharp detail, motion-controlled calm"* |
| **Wes Anderson** | dead-center symmetry, flat-on planimetric walls, pastel palette, deadpan, top-down inserts — *"perfect central symmetry, pastel palette, frontal framing, deadpan whimsy"* |
| **Spike Lee** | double-dolly floating subject, saturated reds, direct-to-camera address, urban heat — *"a subject gliding as the world recedes, bold red, look to lens"* |
| **Tarsem Singh** | hyper-saturated painterly maximalism, surreal symmetry, couture set-pieces, jewel color — *"opulent surreal tableau, jewel-saturated palette, symmetrical grandeur"* |
| **Nicolai Fuglsig / Dougal Wilson / Frédéric Planchon** (modern spot register) | big single-idea spectacle, immaculate craft, emotional-or-witty core, naturalistic-yet-elevated light — *"one big beautifully-executed idea, elevated natural light, flawless craft"* |

Use these to *elevate* a Pakistani register (e.g. Ramadan-emotional shot with Ridley-Scott smoke-shafts and epic scale, or a humor-telecom frame with Wes-Anderson symmetry), not to replace the cultural content.

---

## 8. Platform framing — reframing the hero still for YouTube & Instagram

Nano Banana makes the still; these are the layout/aspect targets. Full post-assembly and safe-zone logic is in `references/creative_posts_copy_type_layout.md` — key points for Pakistani ad content:

**YouTube thumbnail (16:9, design at 1280×720).**
- One dominant face with a clear, big emotion; product/logo second-read; **≤3–4 words** of large high-contrast text (bilingual works — a bold Urdu word + English). Design to survive at ~small size. Keep text and face out of the **bottom-right ~10–15%** (the duration stamp overlays there).
- Prompt close: *"16:9 YouTube thumbnail, one expressive face filling left two-thirds, bold 3-word super top-right, high-contrast, subject and text clear of the bottom-right corner, saturated readable palette."*

**Instagram feed post.** Portrait **4:5** (max feed real estate) or **1:1**. Keep the hero and any key text within a centered safe area; leave breathing room top and bottom. Carousel = one consistent grid system across slides (see posts file).

**Reels / Stories cover (9:16).** Keep subject and text in the **center ~1080×1420 safe zone** — top ~250px (profile/username) and bottom ~420px (caption, buttons, CTA) get covered by UI. Prompt close: *"9:16 vertical, subject and headline centered in the safe zone, clear margins top and bottom for app UI."*

**One-master → reframe workflow.** Generate the hero at the richest ratio once, then re-crop/extend to 16:9, 4:5, and 9:16 rather than re-generating — keeps casting and grade consistent. Use Nano Banana's edit/extend to add headroom for the vertical.

**Urdu/bilingual supers:** render on Nano Banana Pro, quote the exact string, name the script style (nastaʿlīq for elegant/emotional, bold naskh or a heavy display face for punchy/comedy). Right-to-left is supported. See `references/text_rendering.md`.

---

## 9. Worked Nano Banana prompts

**A — Ramadan telecom key art (emotional flagship)**
> *"Generate a warm cinematic key-art still: a three-generation Pakistani family gathered around a laden iftar dastarkhwan at dusk — grandmother, parents, and two children mid-reach as the azaan breaks the fast, dates and Rooh Afza and pakoras on the spread. Warm tungsten key from a hanging lamp camera-left, fairy-light bokeh behind, soft golden grade, faint steam over the food. Realistic skin — visible pores, subsurface scattering, no beauty-filter smoothing. The mother's face catches a soft emotional highlight. Shot on 50mm, shallow depth of field, medium wide with the family arranged in three depth planes. Reserve clean warm space upper-right for a logo and Urdu tagline. Output 16:9."*

**B — Humor telecom still (Ufone/Jazz register)**
> *"Render a bright, sitcom-lit Pakistani domestic comedy frame: a wide-eyed uncle in a shalwar kameez and waistcoat handing gift bags to relatives in a warm living room, one overlooked cousin deadpan at the edge of frame. Even bright key, saturated everyday palette, patterned floor tiles, framed calligraphy on the wall, ceiling fan. Expressive mid-reaction faces, clean readable staging so the gag lands. Realistic skin texture. Output 16:9."*

**C — FMCG masala food hero (Shan/National register)**
> *"Compose a mouth-watering food hero: a steaming degh of chicken biryani being garnished by a woman's hands, backlit ribbons of steam, oil sheen and saffron-red rice saturation, fried onions and green chilies scattered. Warm kitchen practicals, steel and marble counter, a masala tin soft in the background. 45° hero angle, 100mm, appetizing shallow focus, rich warm grade. Realistic hands with natural finger compression. Output 4:5 for Instagram."*

**D — YouTube thumbnail for a Pakistani brand ad**
> *"Generate a 16:9 YouTube thumbnail: one Pakistani man's face filling the left two-thirds, big surprised-joyful expression, warm saturated light, a bright product held in his hand lower-right but clear of the very corner. Bold three-word super top-right reading 'EID MUBARAK!' in a heavy display font, high contrast with a thin outline. Punchy saturated palette, everything readable at small size, nothing important in the bottom-right corner. Output 16:9."*

---

## 10. Failure modes specific to Pakistani ads

- **"India lite" drift.** Model renders generic North-Indian faces with bindis/sindoor. Fix: cast per `references/south_asia_casting.md`, add the **no-bindi/no-sindoor** negation, specify Pakistani ethnic register and shalwar kameez.
- **Muted Western ad grade.** Comes back teal-orange and cool. Fix: name the warm festive palette explicitly — *"warm golden grade, saturated festive reds and golds, tungsten practicals."*
- **Nuclear-couple collapse.** Asked for a family, got two adults. Fix: enumerate generations — *"grandmother, mother, father, and two children."*
- **Truck-art everything.** One accent motif smothers the frame. Fix: confine truck-art to one object (a panel, a truck, a dhaba) and keep the rest grounded.
- **Garbled Urdu type.** Fix: Nano Banana Pro only, quote the exact string, name nastaʿlīq/naskh, verify glyphs; regenerate text-first if needed.
- **Over-polished PSA.** Social/PSA registers need honesty, not gloss. Fix: available light, real courtyard/street, a real stain/mess, documentary-warm grade, drop "lifestyle photography."
- **Generic "studio home."** Fine for aspirational brands, wrong for realism briefs. Fix: for grounded work, add the environment/prop ledger (§4) — tiles, charpai, wall clock, calligraphy, wires.
- **Product lost.** Emotion wins but the brand vanishes. Fix: state the read-order — *"first read the face, second read the product, only saturated hue on the pack."*

---

## Sources

- [Iconic Pakistani Ad Campaigns That Redefined the Marketing Game — Brandsynario](https://www.brandsynario.com/ad-mazing/famous-pakistani-advertisements/)
- [Are Our Ads Really Made in Pakistan? — Aurora / Dawn (Shoaib Qureshy)](https://aurora.dawn.com/news/1144603)
- [Asim Raza — Wikipedia](https://en.wikipedia.org/wiki/Asim_Raza) · [The Vision Factory — Overview](https://thevisionfactory.com.pk/overview/)
- [Ahsan Rahim — ads archive, AdsSpot](https://adsspot.me/creatives/ahsan-rahim-df726df6f524/ads-and-commercials)
- [Coke Studio Pakistan — Wikipedia](https://en.wikipedia.org/wiki/Coke_Studio_Pakistan) · [Craftpur: Coke Studio & street style](https://craftpur.com/blogs/our-journal/coke-studio-redefining-pop-culture-and-street-style-in-pakistan)
- [The 7 Best Commercials Made By Famous Directors — PremiumBeat](https://www.premiumbeat.com/blog/best-commercials-by-famous-directors/) · [Best Commercials by Famous Film Directors — Collider](https://collider.com/best-commercials-by-movie-directors-spike-lee-nike/)


<!-- ═══════ FILE: nano-banana-prompter/references/recent_ad_trends_and_directors.md ═══════ -->

# Nano Banana — what's working now (2025–26) & the auteur ad-director roster

The recency layer: the ad trends actually winning in 2025–26 translated into image-prompt implications, recent campaign registers you can borrow, and an expanded roster of auteur commercial directors. Pairs with:
- `references/pakistan_ads_and_directors.md` (Pakistan-market registers + local directors; global classics Ridley Scott / Michael Bay / Fincher / Wes Anderson / Spike Lee / Tarsem live there — this file adds the *auteur / recent* names and doesn't repeat them).
- `references/commercial_framing_and_set_design.md` (generic ad framing, packshot, built sets).
- `references/creative_posts_copy_type_layout.md` (post assembly, safe zones, anti-slop) and `references/realism_and_ugc.md` (the UGC/phone-look stack that most of these trends require).

> **Field-validated (Round 11, `field_findings.md`) — ImagineArt, 2026-07-06.** The social-native UGC ad register and the Dougal-Wilson auteur block scored PASS (strong). Other trend registers and auteur blocks remain provisional until individually tested.

---

## 1. What's working in 2025–26 (trend → image implication)

The macro shift: **ads aren't pushed, moments are created.** Winning work is conceived in *social language* first — cultural relevance, authenticity, humor, and shareability over glossy polish. Translate each trend into a prompt register:

| Trend (what's winning) | Prompt implication for the still |
|---|---|
| **Social-native, platform-first** | default to 9:16, phone-capture look, arm's-length framing — build with the UGC five-stack (`realism_and_ugc.md`), not the studio rig |
| **Authenticity over polish** | real-frame-from-video hero (available light, found composition, capture imperfection) — the `tonal_families.md` real-frame override; drop "lifestyle photography" |
| **Brand humor & self-awareness** (Heinz, Duolingo, Burger King) | bold graphic simplicity, character/mascot-led, one comic idea, high-contrast brand color, deadpan or absurd expression |
| **Creator/UGC collaboration** | "shot by a creator" register — handheld, mixed practical light, creator mid-talk to camera, real clutter |
| **Proof / "verified" formats** (Vaseline Verified) | demo, before/after, lab-test or evidence aesthetic — clean, honest, side-by-side with identical light/angle |
| **Nostalgia / retro** | era looks (`photographer_styles_and_eras.md`) — VHS, disposable-flash, Y2K, film grain |
| **Cultural-moment / topical** | meme-literate framing, of-the-second props and settings; readable at a glance |
| **Long-form campaign systems** (Coors month-long) | one consistent visual system across many frames — lock grade + type + layout, vary the scene |
| **Craft-as-flex vs AI** (Gavras' deliberately no-AI spot) | when the brief wants "obviously real," lean hard into practical-capture tells and human imperfection |

**The anti-slop reminder:** the 2025–26 penalty is the sanitized, over-produced, obviously-templated look. First read should feel like a real moment with an honest read on the audience's actual world.

---

## 2. Recent campaign registers (borrowable looks)

Reference blocks abstracted from what broke through — use the *look/approach*, not the brand.

| Campaign | Borrowable register |
|---|---|
| **Vaseline "Verified"** | proof/credibility aesthetic — a product claim shown being tested, clean evidence framing, a "seal/badge" graphic, trust-through-demonstration |
| **Heinz "Heinz vs Everyone"** | bold red graphic humor, the product as hero of a comic exaggeration, UGC parody energy, deadpan disappointment beat |
| **Duolingo** | irreverent mascot-led social chaos, on-brand absurdity, character reacting to a cultural moment, meme framing |
| **Burger King "Reclaim the Flame"** | honest comeback narrative + craveability — flame-grill texture, warm gloss, self-aware sincerity |
| **Coors Light "#caseoftheMondays"** | a single ownable visual gag stretched across a month — one motif, many executions, consistent system |

---

## 3. Auteur commercial-director signature blocks

The best commercial looks come from auteurs. **Never the name alone — paste 3–4 signatures.** (Ridley Scott, Michael Bay, Spike Jonze basics, Wes Anderson, Spike Lee, Tarsem are in `pakistan_ads_and_directors.md` §7; these are the additions.)

| Director | Paste these signatures |
|---|---|
| **Jonathan Glazer** (ad-mode) | hypnotic minimalism, one bold surreal idea executed with restraint, unsettling beauty, cool controlled palette, iconic simplicity (Sony Bravia bouncing balls; Guinness "Surfer") — *"one bold surreal idea, restrained cool palette, hypnotic minimal execution, unsettling calm"* |
| **Romain Gavras** | chaotic epic scale, real crowds and practical energy (deliberately no-AI), anamorphic wide, kinetic tracking, raw grandeur — *"epic real-crowd chaos, anamorphic wide, kinetic energy, gritty grandeur"* |
| **Spike Jonze** (ad-mode) | emotional whimsy, a dancing/moving human core, one delightful conceit, warm naturalism (Apple HomePod; Kenzo World mania; Kenzo) — *"one joyful human conceit, expressive movement, warm naturalism"* |
| **Melina Matsoukas** (ad-mode) | painterly cultural intelligence, charged tableau, sensual moody light, brand-meets-culture (Nike, Kenzo, Stella Artois) — *"painterly charged frame, cultural depth, moody sensual light"* |
| **Dougal Wilson** | emotional storytelling, warm humane craft, the tear-jerk narrative beat, immaculate naturalistic light (John Lewis Christmas register) — *"a warm emotional story beat, humane naturalism, flawless soft light"* |
| **Nicolai Fuglsig** | big single-idea spectacle with immaculate craft, epic-yet-clean, elevated natural light — *"one big beautifully-executed idea, epic clean craft, elevated natural light"* |
| **Frédéric Planchon** | precise minimal elegance, restrained palette, quiet premium mood — *"minimal precise elegance, restrained palette, quiet premium calm"* |
| **Traktor / Frank Budgen (classic spot DNA)** | iconic high-concept spectacle, bold visual hook, flawless production polish — *"a bold single hook, spectacle scale, flawless polish"* |

Use these to *elevate* a brief — e.g. a Pakistani Ramadan register with Dougal-Wilson emotional warmth, or an FMCG hero with Glazer minimal restraint. One register per frame.

---

## 4. Quick apply

1. Pick the **trend register** the brief lives in (social-native? proof? humor? nostalgia?).
2. Pick **one** director/aesthetic block to give it a spine.
3. Add the **realism/UGC stack** if authenticity is the point, or the studio rig if it's a hero packshot.
4. Set **platform ratio** and safe zones (`creative_posts_copy_type_layout.md`).
5. Run the critique rubric (`composition_posing_and_critique.md`) → audit → repair.

---

## Sources

- [Latest Marketing Campaigns 2025–2026 — Brandify PR](https://www.brandifypr.com/post/latest-marketing-campaigns-2025-2026-real-examples-what-marketers-can-learn)
- [Cannes Lions 2025 takeaways — Ad Age](https://adage.com/events-awards/cannes-lions/aa-cannes-lions-2025-takeaways/) · [Best Commercial Directors 2026 — Amos LeBlanc](https://www.amosleblanc.com/best-commercial-directors-2026)
- [Top marketing campaigns of 2025 — Pulse Advertising](https://www.pulse-advertising.com/resources/social-media-news/top-10-marketing-campaigns-of-2025/)
- [Music videos that influenced ad creatives — Creative Salon](https://creative.salon/articles/features/on-the-agenda-music-videos-gener8ion-storm)


<!-- ═══════ FILE: nano-banana-prompter/references/creative_posts_copy_type_layout.md ═══════ -->

# Nano Banana — Building finished social posts (copy, type systems, layout, formats)

The rest of this skill makes the **photograph**. This file assembles the **post** — the words, the type system, the layout, the platform sizing, the format — and kills the *design-level* AI slop that survives even a perfect photo.

Cross-references, never duplicated here: glyph mechanics (quote the text, name the font, localise) → `references/text_rendering.md`; photographic realism / anti-plastic skin → `references/realism_and_ugc.md`; the copy-space "hole", read-order beats, multi-format master → `references/campaign_and_specialist_genres.md`; the four creative-director levers → `references/creative_director_controls.md`; the critique rubric, generate→audit→repair loop, and AI-default-angle fixes → `references/composition_posing_and_critique.md`; the real-frame override and night-physics → `references/tonal_families.md`.

> **When to engage, and the two forks.** Use this module **only when the brief is to build a post / social content** (single, carousel, cover, story, card, ad). A plain image, portrait, product shot, or standalone film frame that isn't going out as a post → stay in the core skill. Within a post, one more fork: **type-hero formats** (quote/stat card, infographic) → type is the subject, no photo needed; **photo-hero formats** → the hero image **defaults to a real frame from a video** (§1), never a posed render.

> **Status: partially validated (Round 8, 2026-06-17).** A live Nano Banana Pro test confirmed the **real-frame-from-video hero, the carve-the-copy-hole-into-a-real-frame technique, the text supers, and the anti-slop close** — together they produced a genuinely usable launch post. Still untested: **carousel template-lock** and **safe-zone-as-%** — treat those as strong defaults. See `references/field_findings.md` Round 8.

---

## 1. A post is a stack, not a captioned photo

Brief the layers in order — each constrains the next:

1. **Goal + one message.** What single thing must a scroller take away? Can't say it in a line → cut scope.
2. **Copy** — headline / kicker / CTA *and* the caption (§2). Words first; they set how much room type needs.
3. **Type system** — hierarchy, pairing (§3).
4. **Layout + platform size** — grid, copy-hole, safe zones for the placement (§4).
5. **Image** — default to a real frame from a video (below); build it with the photographic stack, composed *around* the copy-hole.
6. **Brand marks** — logo lockup, palette (§6).
7. **Compliance + accessibility pass** before export (§8).

The most common reason an AI post fails: the image is made first and the words are jammed on after. Reverse it.

### Image priority — real frames from a video

The post's hero image should look like a **still pulled from a moving clip**, not a studio render — on-brand for imagine.art (frames from Seedance / film clips) and the strongest anti-slop move there is. Stack 2–4 cues:

- **Caught mid-motion** — subject mid-step / mid-gesture / mid-blink; *"a frame paused on a moving subject."*
- **Frame-grab imperfection** — slight motion blur on one moving element, a touch of focus softness, faint compression/rolling-shutter feel; *"a paused video frame, not a sharp photo."*
- **Found composition** — off-balance, partial occlusion, subject not posed at the lens, gaze off-camera.
- **Available light only** — motivated practical/daylight, no studio rig, no courtesy rim; apply the **real-frame override** (`references/tonal_families.md`), and night-physics if it's dark.
- **Capture register** — name the clip: *"a still from a handheld 24fps clip, 180° shutter motion blur"* / *"a paused phone video, slight HDR, 9:16."*

Close with: *"a single frame from a video clip — caught, not composed; not a posed photo, not an AI render."* If the user supplies an actual video frame, use it as the base/anchor (Framework 2/3) and keep its grade and grain.

### When the frame fights the type — the post audit loop

A real video frame is busy, dark, and low-contrast (exactly what the real-frame override pushes for) — and that's where overlay type dies. Reconcile the two doctrines deliberately:

- **Carve the copy-hole into the found frame.** Generate the frame with a **deliberately under-lit or empty quadrant** for type: *"the upper-left third falls into shadow / open sky / clean wall — low detail, no highlights, room for a headline."* A found frame still has to be art-directed to leave the hole.
- **If the frame won't give you a hole, add a plate, not a glow.** *"A subtle dark gradient scrim behind the text only, the rest of the frame untouched"* (the cover move, §5) — or drop the type on a solid band. Never a soft glow behind floating text (slop tell, §7).
- **Then audit, then repair.** Run the model-as-critic turn from `references/composition_posing_and_critique.md`, scoped to posts: *"List everything here that reads as templated AI design — default fonts, gradient, centered layout, glow — and tell me if the overlay text is legible against what's behind it."* Fix the top 2–3 in one edit turn, closing with *"keep everything else exactly the same."* This generate→audit→repair loop is the highest-leverage quality move for posts, same as for frames.

---

## 2. Creative texts (the copywriting)

`text_rendering.md` makes text render correctly. This makes it worth reading.

### Caption structures (pick one)

| Structure | Shape | Best for |
|---|---|---|
| **HVC** | Hook → Value → CTA | the default for almost any post |
| **PAS** | Problem → Agitate → Solve | product, pain-point, before/after |
| **Story → Lesson → CTA** | micro-story → takeaway → ask | founder/personal, LinkedIn |

### The hook is the first 1–3 lines

Captions truncate at "…more"; if the first line doesn't earn the tap, the rest is unseen. Keep the hook **under ~80 characters / 10–12 words**. Two engines that beat generic openers:

- **Tension hook** — start mid-conflict: *"We almost killed this feature in March."*
- **Transformation hook** — before→after gap: *"0 to 40k with one format change."*

Banned openers (read as AI/filler): *"In today's fast-paced world…", "Unlock the power of…", "Elevate your…", "Are you ready to…"*.

### On-image copy ≠ caption copy

Text *in* the image is a **super**: kicker (1–3 words), headline (≤6 words), CTA (≤3 words). Sentences live in the caption. Hand the image only what must be seen at a glance.

### CTA + discovery

Rotate CTAs; don't stack three sales asks in a row. Reply/save/share prompts (questions, opinions, *"save this for later"*) tend to travel further than click-bait — *treat that as current platform guidance, not a law.* For discovery: put **3–5 specific keywords/hashtags** in or below the caption (captions are searched now); skip generic tag-spam.

### Text-first workflow

> Turn 1: *"Write 3 hooks and 3 CTAs for an Instagram post announcing 4K export on imagine.art. Audience: solo creators. ≤10 words each, tension or transformation."*
> Turn 2: *"Use hook 2 + CTA 1. Render with [type system + layout below]."*

> **Anti-AI-copy tells to strip:** em-dash overload, "it's not just X, it's Y", tidy rule-of-three lists, "in a world where", hollow superlatives. Specific noun + number + verb beats every abstraction.

---

## 3. Professional type systems (as prompt language)

`text_rendering.md` makes text legible; this makes it *designed*. Spec the system, not just the string.

- **Hierarchy — 3 levels max** on one post. State the read order and each level's job: *"kicker 'NEW' (small tracked caps) → headline '4K exports, zero wait' (dominant) → CTA 'Try free' (small)."*
- **Hierarchy reads; numeric ratios don't.** The model renders "dominant / subordinate", not a measured scale — so say *"headline dominant, kicker and caption clearly smaller,"* not "5×". (Designers think in 1.25/1.333/1.5 steps; the renderer only honors *much bigger / much smaller*.)
- **Pairing — contrast by classification.** One display + one neutral text face; never two near-identical fonts. *"High-contrast didone headline (Bodoni-like) against a clean humanist grotesque for everything else."* Ceiling: **two typefaces, three weights.**
- **Type colour & placement.** Sit type on the lowest-contrast region (pairs with the copy-hole): *"headline on the open upper-left, off the busy speculars."* Verify the contrast *after* export (§8) — the model won't hit a target ratio on command.
- **Spacing as craft.** *"Loose tracking on the all-caps kicker, tight leading on the two-line headline, hanging punctuation, left edge optically aligned, generous outer margins."*

> **Render note.** Small text blurs at 1K and long paragraphs are still hard. **Render type-heavy posts at 2K–4K** — but 2K/4K requires Nano Banana 2 / Pro; the base model is 1K-only (see `SKILL.md` → capability table). Drop exact brand wordmarks in via post-processing (`text_rendering.md`).
> **Borrow what's already validated:** short labels/headlines render cleanly even at 1K — trust the text engine for them; and the model **invents background signage unprompted**, so add *"no readable text in the background"* to keep a post clean (both confirmed in `SKILL.md` field rounds).

---

## 4. Platform layouts & sizes

Two durable principles outlive any spec: **compose inside the safe zone as a percentage**, and **shoot one master, reframe to each placement.** Pixel dimensions and UI-overlay heights drift on every platform update — the px below are typical, not gospel; verify before a launch and rely on the ratios + percentages.

| Placement | Ratio (typical px) | Safe-zone logic (compose in %) |
|---|---|---|
| IG feed — portrait | **4:5** (1080×1350) | Most feed real estate. Keep key elements out of the top/bottom ~5%. |
| IG feed — square | 1:1 (1080×1080) | Predictable; grid-safe. |
| IG profile grid | center **1:1 crop** of the 4:5 | Faces/headline must read inside the center square. |
| IG/FB Stories & Reels | **9:16** (1080×1920) | Keep text + logo out of the **top ~13%** (username) and **bottom ~22%** (caption/CTA/progress). |
| TikTok | **9:16** | As Stories, plus a right-edge icon rail (~10%) and a wider bottom caption band — keep copy center-left. |
| LinkedIn feed | 1:1 or 1.91:1* | Plus **PDF "document" carousels** (4:5 / 1:1 pages). |
| X (Twitter) | 16:9 or 1:1 | In-feed crop favors 16:9; 1:1 for height. |
| Pinterest | **2:3** (1000×1500) | Tall; headline top third. |
| YouTube thumbnail | 16:9 (1280×720) | Must read at ~210px wide — see Covers (§5). |
| FB / OG link preview | 1.91:1* (1200×630) | Logo + ≤5 words; edges crop. |

\* **1.91:1 isn't a native Nano Banana output ratio.** Render the nearest supported ratio (16:9) and crop to spec. Native output ratios are in `SKILL.md` → "Resolution, aspect ratio, output controls".

**In the prompt:** state the ratio at the close *and* reserve the zone in the composition — *"Output 9:16. Keep all text and the logo in the central title-safe area — nothing important in the top 13% or bottom 22%, clear of the right-edge column."*

**One master → every placement:** generate a 4:5 or 16:9 master with subject and copy inside the center safe box, then reframe (re-crop, or re-generate at the target ratio re-feeding the master) without clipping limbs or the headline. Full discipline → `references/campaign_and_specialist_genres.md`.

---

## 5. Post formats — each has its own grammar

### Carousel

A swipe narrative, not N loose images.

- **Slide 1 = cover/hook** — biggest type, one promise, a swipe cue ("1/7", a peeking arrow).
- **Slides 2…N−1 = one idea per slide** — identical template every slide: same margins, type system, palette, footer, index.
- **Final slide = payoff + CTA.**
- **Consistency lock:** write a **template block** (grid + type system + palette hexes + logo position), paste it verbatim into every slide, generate **one slide at a time** re-feeding the previous slide as a style reference; lock any recurring subject with a reference image.
- **Ratio:** 4:5 (IG) or 1:1; LinkedIn = PDF document pages.

> Cover fragment: *"Carousel cover, 4:5. Headline '5 mistakes killing your reach' in heavy grotesque, left-aligned upper half, bone-white bg, single ink-black underline, small '1/6' bottom-right, footer logo bottom-left. Generous margins. Flat — no gradient, no glow."*

### Covers & thumbnails

Built to survive at ~210–400px. **One focal point**, **2–4 word super**, **extreme contrast** (text on a solid/darkened plate, never busy texture), legible expression if there's a face. **Shrink test:** scale to thumbnail — if the words or expression don't read, regenerate bigger/bolder.

> *"Reel cover, 9:16. A single face filling the upper two-thirds, genuinely surprised expression, the words 'I WAS WRONG' in heavy condensed sans, white on a dark plate behind the text only, legible at thumbnail size, nothing in the bottom 22%."*

### Text-dominant cards (quote · stat · hot-take · list)

Type *is* the post; image is texture or absent. Render at 2K+ (NB2/Pro).

- **Quote:** *"the quote in large humanist serif, attribution small below, wide margins, one restrained paper texture; no stock photo."*
- **Stat:** *"the number huge — the hero — label small beneath; one accent colour on the number only."*
- **List:** *"numbered rows, consistent leading, a clear title, one accent on the numerals."*

### Infographic / explainer / data

Nano Banana Pro's strength (the chai-recipe register). Spec: title, **3–5 labelled steps/segments**, consistent icon style, restrained palette, legible labels; render at 2K+. **Fact-check law:** the model renders plausible-but-wrong numbers — **never trust an AI-rendered chart's data.** Supply every figure/label and verify before posting.

### Meme / trend-native lo-fi

Deliberately undesigned — Impact caps top/bottom with black outline, or a plain system-font caption over a screenshot-grade image; slight compression. *"Make it look posted, not produced."*

---

## 6. Brand kit, templates & variants

- **Brand-kit block** (paste verbatim across every post, like the campaign block): logo lockup + placement + clear-space, palette **hexes**, the locked type pairing, margin/grid. This is what makes 30 posts read as one brand.
- **Logo:** state size, position, clear-space, light/dark variant; exact wordmarks finish best in post.
- **A/B variants:** generate 3 covers changing **one** variable (headline OR image OR palette) — never all three, or you can't tell what won.
- **Feed-grid cohesion:** alternate formats (photo / card / quote), hold palette + type constant, vary value and composition so the grid has rhythm.

---

## 7. The design-level AI-slop taxonomy

Distinct from the *photographic* slop the skill already fights (plastic skin, default angles). This lives in **design choices** — if a post could've come from any tool off any brief, it has these tells. Name the fix.

| The slop tell | Why it reads as AI | The fix |
|---|---|---|
| Default font (Inter / Roboto / Montserrat) | the median of every training-set UI | name an intentional pairing (§3) |
| Purple→blue / teal→magenta gradient | the "safe" SaaS gradient | name a real palette/hexes: *"flat — bone white, ink, one signal red; no gradients"* |
| Centered everything, symmetrical hero | the averaged layout | *"asymmetric on a 6-column grid, headline left, subject bleeding off the right"* |
| Three rounded icon-cards / feature row | landing-page boilerplate | *"one focal image, no card UI, no icon row"* |
| Glow + drop-shadow on every element | default depth crutch | *"flat — no glows, no drop shadows; depth from scale and overlap"* |
| Emoji / sparkle / "AI" badge confetti | decoration replacing design | *"no stickers, no emoji, no badges"* |
| Gibberish fake-UI / dashboard text | text engine left unguided | supply real copy, or *"no readable text in the device screen"* |
| Headline that says nothing ("Elevate your experience") | the model averaged every headline | force a number, a verb, a concrete claim |
| Posed at the lens, studio-lit, razor-sharp "render" look | the polished AI default | default to a **real frame from a video** (§1) — mid-motion, available light, found composition |

> **One-line anti-slop close:** *"intentional editorial design — named palette, deliberate type pairing, asymmetric grid, one focal point; not a template, no default gradient, no centered-card layout, no glows, no emoji."*

---

## 8. Compliance & accessibility (run before export)

**Provenance & AI labeling**
- Nano Banana output carries **C2PA Content Credentials + a SynthID watermark**. As of current (2026) policy, Meta and TikTok detect C2PA and apply an "AI info" / "AI-generated" label — *platform policies shift, so confirm the current rule;* plan for the label rather than fighting it.
- Some categories need a **visible** disclosure (paid synthetic people, realistic AI audio/video); **ads carry FTC truth-in-advertising duties**. Keep claims literally true; don't imply a real person endorses if synthetic.
- **Don't generate real, named public figures** (skill policy + likeness/legal risk).

**Accessibility**
- Verify overlay-text contrast after render (aim ≥ ~4.5:1 body / ~3:1 large) — the model won't hit it on command.
- Test legibility at **actual feed size**, not full-res.
- Never encode meaning in **colour alone**; write **alt text**; bake **captions** onto any text-on-video cover; avoid strobing.

---

## 9. Worked examples

### A — Product-launch single post (Instagram, 4:5), as a real video frame

*Caption (HVC):* Hook — *"We deleted the 'Export' progress bar."* Value — *"4K renders land before you finish your sentence."* CTA — *"Try it free — link in bio."*

*Prompt:*
> *"Compose a 4:5 (1080×1350) product post as a single frame from a handheld video clip. A creator's hands lift a phone showing a finished 4K render, caught mid-lift with slight 180°-shutter motion blur on the moving hand; the subject fills the lower-right two-thirds. Available warm desk light from camera-left — the right edges of the hands fall into shadow, the cast shadow running camera-right. Faint frame-grab softness, not a posed photo. Leave the upper-left third under-lit and low-detail for type. Headline '4K. No waiting.' in a high-contrast didone on that dark space; kicker 'NEW' in small tracked caps above; small 'imagine.art' wordmark bottom-left. Two typefaces max. Flat palette — warm neutral, ink, one signal accent; no gradient, no glow. Render at 2K (Nano Banana Pro). Keep text in the central safe area, nothing in the top/bottom 6%."*

Then audit: *"List anything here that reads as templated AI design, and tell me if 'No waiting' is legible on what's behind it."* Repair the top issues, *keep everything else the same.*

### B — Quote/stat carousel (Instagram, 4:5)

The new move vs Example A is **template reuse**: write one block and repeat it.

> Template block (paste into every slide): *"4:5, bone-white bg, ink humanist grotesque, one cobalt accent, 96px margins, footer 'imagine.art' bottom-left, page index bottom-right, flat."*
> Cover: *"+ headline 'The 3-second export changed our retention', swipe arrow + '1/5'."* · Inner: *"+ the stat '+38% day-7 retention' as the hero number, cobalt."* · Final: *"+ 'Save this for your next launch', small 'Follow @imagine.art'."*

Generate one slide at a time, re-feeding the prior slide as a style reference.

---

## 10. Pre-flight checklist (post-specific — complements the critique rubric)

1. One message a scroller gets in under 2 seconds?
2. Photo-hero defaults to a real frame from a video (mid-motion, available light, found composition) — and you carved a copy-hole into it?
3. Caption uses HVC/PAS/Story; hook ≤10 words, front-loaded?
4. On-image copy is supers (kicker ≤3, headline ≤6, CTA ≤3), not sentences?
5. Type: 3 levels, dominant→subordinate jump stated, ≤2 typefaces?
6. Correct ratio + safe zones reserved as %?
7. Carousel: template block locked, slides one-at-a-time? · Cover: passes the shrink test? · Infographic: every number supplied and verified?
8. Anti-slop close applied; ran the audit→repair turn?
9. Brand-kit block + logo placement/variant applied?
10. Compliance + accessibility pass (AI label planned, alt text, contrast verified, no colour-only)?
11. Type-heavy/data post rendered at 2K–4K on NB2/Pro; exact wordmark post-processed?

---

## 11. Failure modes & fixes (only the repairs not already on the checklist)

**Carousel slides drift** (margins/type wander). Fix: paste the template block verbatim each slide; generate one at a time re-feeding the previous slide.

**Slop gradient persists** after "no gradient." Fix: name the *positive* palette with hexes — positive framing beats the negative.

**Infographic numbers wrong.** Fix: supply every figure and verify; never let the model invent data.

**Type illegible on a real video frame.** Fix: carve the under-lit copy-hole at generation, or add a dark plate behind the text only (§1) — not a glow.

---

## 12. Out of scope (keep this a prompt-craft skill)

Not here, by design: content calendars, pillars, cadence, scheduling, analytics (tooling/connectors, e.g. the imagine.art platform); and legal clearance for real-person likeness, trademarks, or licensed music (flag the risk, don't advise). Motion/video posts: build the cover/still here, then hand the motion to `seedance-2-prompter` or `kling-prompter` (see `gen-media-router`).


<!-- ═══════ FILE: nano-banana-prompter/references/commercial_framing_and_set_design.md ═══════ -->

# Nano Banana — commercial frames, ad framing, set design & elements

The advertising counterpart to the film-look file: how commercial photography and TVC frames are actually built — genre look blocks, product framing grammar, built-set systems, and the practical-elements library (splashes, steam, condensation, powder). Builds on `references/campaign_and_specialist_genres.md` (copy holes, read order, the four genre deep-dives), `references/styling_and_set_design.md` (four-layer set dress, prop logic), and `references/photography_pro.md` (studio rigs) — this file does not repeat them. **Field-validated (Round 13):** the automotive dusk register + reflection-streak grammar (21/22) and the beverage crown-splash / high-speed liquid-physics element (20/22) both scored PASS (strong).

---

## 1. Commercial look blocks (the ad-genre registers)

Like film blocks: never say "make it look like an ad" — paste the register's components. One register per frame.

| Register | Component block |
|---|---|
| **Tech-minimal white** | seamless white infinity, product floating-weight on soft contact shadow, single huge soft top-key, cool-neutral grade, absolute geometry, nothing else in frame |
| **Premium dark tech** | black glass surface, low-key, one edge-light tracing the silhouette, deep reflections below, hairline speculars on chamfers, near-black grade |
| **Perfume surreal** | monolithic bottle at architectural scale, dream landscape or marble set, hard sun + long shadow, liquid-gold or dusk palette, one impossible element (floating silk, still water) |
| **Luxury watch/jewelry macro** | 100mm macro, black or deep-green velvet, hard focused speculars on facets and polished metal, painted-with-light gradients, dust-free blacks |
| **Sports grit** | sweat sheen, dark gym or wet track, hard cross-light + haze, frozen peak-action, charcoal grade with one team-color accent, chalk or spray mid-air |
| **Beverage refreshment** | backlit liquid glow, condensation-loaded bottle, crown splash or arcing pour frozen at high speed, citrus/ice in suspension, saturated product color against clean field |
| **Fast-food craveability** | cheese-pull or steam energy, backlight gloss on every surface, stacked hero at 10–25°, warm reds/yellows, messy-edge styling |
| **Skincare clinical-soft** | high-key daylight, cream and stone palette, water texture and glycerin droplets, product on wet stone or acrylic block, soft shadows, human hand contact |
| **Haircare motion** | hair mid-flip frozen sharp, rim-lit strands, seamless color paper, fan-blown volume, glossy specular ribbon along the hair |
| **Fashion-luxury flash** | direct on-camera flash, hard shadow on seamless or marble, deadpan pose, saturated color-block wardrobe, editorial emptiness |
| **Home-warmth (IKEA register)** | lived-in interior, golden window light, four-layer set dress with strong "today" layer, product used mid-scene, warm natural grade |
| **Pharma/wellness soft** | morning light through sheer curtains, pastel-neutral palette, gentle motion (stretching, breakfast), soft contrast, believable diverse casting |
| **Eco/organic craft** | kraft and linen textures, botanical props, raw wood, daylight only, matte grade, imperfect handmade arrangement |
| **Toy/kids pop** | saturated primary color paper sets, hard even light, overhead or dead-on graphic framing, props at playful scale |
| **Finance/corporate trust** | blue-hour glass architecture, clean mid-grey grade, long-lens compression, one human moment against scale |

---

## 2. Ad framing grammar

### Packshot angles (each has a job)

- **Dead-on straight** (0°, lens at product center) — clarity and trust; e-comm, packaging, comparison frames. *"Dead-on packshot, lens at label height, verticals parallel."*
- **Low hero** (10–20° below center, slight up-tilt) — dominance; premium launches. *"Low hero angle, camera just below the product's midline, product looms slightly."*
- **3/4 at 45°** — the natural tabletop view; shows face + one side, dimensional. Default for boxes, bottles, devices.
- **Overhead / knolling** — flat lays, ingredient stories, kit layouts: *"true 90° overhead, items aligned on a strict grid with even gutters."*
- **Macro detail crop** — one material truth (stitching, facet, nib, weave) filling the frame; pairs with a wide hero in a series.

### Scale discipline

State the product's share of frame: hero packshot = *"product fills 60–70% of frame height"*; lifestyle = *"product small but first-read — brightest value or only saturated color in frame"*; OOH = one object, readable at distance. Unstated scale is why ad frames come back with a tiny floating product.

### The end-frame / packshot lockup

The TVC closing frame is its own format: *"product centered or right-of-center at 50% frame height, clean field behind, flat even tone upper third reserved for logo and tagline, soft contact shadow, nothing competing."* Quote the exact tagline text or state *"no readable text"* — never let it improvise.

### The hand-model frame

Hands sell scale, use, and desire: *"manicured hand enters from frame-right holding the jar at 45°, fingers relaxed not gripping, product label to camera, realistic skin compression at the contact points."* Wrist angle natural; label unobstructed; compression stated (validated realism tell).

### Demo and benefit frames

- **Swatch/texture frame:** the product's material smeared/spread as the subject — *"a diagonal swipe of the cream across glass, sharp ridge detail, product jar soft in the corner."*
- **Before/after:** split framing, identical light and angle both sides — state *"same lighting, same angle, only the condition changes."*
- **In-use frame:** the product mid-job, owned not placed (prop logic), user's attention on the task, not the camera.

### Lifestyle-with-product framing

Product must win the first read without breaking candidness: give it the only saturated hue, the brightest highlight, or the leading-line convergence — *"first read: the bottle; second read: her laugh; third read: the kitchen."* (Read-order grammar from the campaign file.)

### OOH / billboard framing

The 3-second rule: **seven words or fewer**, one subject, one message. High-contrast type pairs (yellow/black, white/deep blue). *"Extreme simplicity: one product, one short line, flat high-contrast field, readable at 60 mph."* Design the frame at thumbnail size — if it fails small, it fails at 48-sheet.

---

## 3. Commercial set design systems

Named set builds — say the system, then dress it:

- **Seamless sweep / cyclorama:** paper or cove curving wall-to-floor with no horizon line. State color like a studio order: *"seamless sweep in muted sage paper, no visible seam or horizon."* White infinity for tech; deep colors for fashion/beauty.
- **Color-drench monochrome set:** walls, floor, plinths, props all one hue (the current trend register); product separated by tone or complementary accent — *"everything terracotta except the cobalt bottle."* Watch the flattening failure (below).
- **Plinths & podiums:** geometric blocks, cylinders, arches, steps at varied heights; matte plaster or stone finish; product on the tallest. *"Three plaster plinths at staggered heights, hard sun raking across, long clean shadows."*
- **Surface library (tabletop):** name the surface — honed travertine, terrazzo, brushed steel, wet slate, raw linen, butcher block, colored acrylic, fluted glass, mirror. The surface is half the set in a tabletop frame.
- **Water sets:** shallow ripple pool with product standing in it, wet-floor reflections, backlit ripples caustics on the backdrop. *"Product standing in 2cm of still water, mirror reflection, one ripple ring."*
- **Surreal-scale sets:** giant product as architecture (perfume register) or miniature world around a normal product — commit to one scale logic and keep shadows consistent with it.
- **Fabric sets:** silk dunes, draped backdrops, a single wind-blown ribbon — fabric behavior words from the styling file apply.
- **Botanical sets:** fresh (not plastic-looking) foliage, monstera/palm shadows as gobo patterns — *"hard light through out-of-frame palm leaves throwing sharp leaf shadows across the set."*
- **Shelf & vanity sets:** the "shelfie" — product among believable neighbors (prop logic: owned, not placed), tiled or marble context, one today-layer detail.
- **Mirror & acrylic sets:** infinity mirrors, colored acrylic sheets as floors/dividers — state what each reflection shows; impossible reflections are a hard fail.

**Trend register (2025–26, from current industry sources):** color drenching, bold Pantone-paper palettes, controlled-chaos maximal layering with clashing colors on one side; quiet-luxury restraint (stone, plaster, negative space) on the other. Pick a side and state it.

---

## 4. The elements library (practical FX in frame)

Every element needs a physical cause and a direction — sourceless effects read as AI. Stack max 2–3 per frame.

| Element | Paste-ready phrase + physics note |
|---|---|
| **Crown splash** | *"milk crown splash frozen at high speed, sharp individual droplets, crown rising around the berry's impact point"* — splash originates at an impact, not ambient |
| **Arcing pour** | *"a glossy ribbon of liquid arcing into the glass, sharp and frozen, collar of foam rising where it lands"* |
| **Carbonation** | *"fine bubble trails rising through backlit liquid, denser at the glass wall"* — carbonation dies fast in real shoots; render it fresh and lively |
| **Condensation** | *"dense micro-droplets over the bottle's shoulder, a few coalescing into runs"* — the stylist's glycerin look; uniform same-size droplets read fake |
| **Ice** | *"ice cubes floating at the surface, upper third proud of the liquid"* — real ice floats; sunken cubes are the acrylic-prop tell |
| **Steam** | *"a thin ribbon of steam rising from the cup, visible only against the dark background, backlit"* — steam needs backlight + dark field |
| **Smoke/haze** | *"low haze filling the set so the beam from camera-left becomes visible"* — haze exists to reveal light shafts |
| **Powder burst** | *"a burst of terracotta pigment powder frozen mid-air behind the product, radiating from one throw point"* |
| **Dust motes** | *"dust particles visible only inside the window beam"* |
| **Fabric in wind** | *"silk ribbon lifted by wind from frame-left, hem lagging the motion"* — one wind direction, everything obeys it |
| **Levitation** | *"product floating 10cm above the plinth, soft contact shadow directly below, slight rotation"* — floating + no shadow = broken frame |
| **Splash garnish** | *"citrus wheel entering the frame mid-air, droplets trailing its arc"* |
| **Sparks/embers** | *"grinder sparks streaking frame-right, lighting the worker's gloves"* — sparks are a light source |
| **Petals/confetti** | *"petals falling with varied rotation and focus, nearer ones motion-blurred"* — uniform sharp confetti reads pasted |
| **Water ripple/caustics** | *"sunlight caustics rippling across the product from off-frame water"* |
| **Cheese pull / drip** | *"one continuous cheese pull, strands thinning realistically; a single sauce drip mid-run"* — one hero drip, not many |

**The high-speed register:** for any frozen-liquid frame, name the capture: *"shot on a high-speed cinema camera, single frame from a 2000fps take, hard continuous light, razor-sharp droplets, zero motion smear."* This is the tabletop-commercial look (Phantom + motion-control rigs in real production) and it instructs the model's sharpness/lighting logic.

---

## 5. Failure modes & fixes

| Symptom | Fix |
|---|---|
| **Tiny floating product / wrong scale** | State frame-fraction: *"product fills 65% of frame height"* |
| **Product placed, not owned** (lifestyle) | Prop logic from the styling file: *"already open, used once, ring of condensation"* |
| **Splash with no impact point** | Tie the element to its cause: *"crown rising around the strawberry's impact"* |
| **Condensation like printed dots** | *"micro-droplets varied in size, a few coalescing runs down the label"* |
| **Sunken ice** | *"ice floating, upper third above the surface"* |
| **Steam invisible / everywhere** | *"backlit steam against the dark side of the set only"* |
| **Levitating product, no shadow** | *"soft contact shadow directly beneath, scaled to the hover height"* |
| **Color-drench set swallows the product** | Separate by tone or complement: *"set all warm sand; the bottle is the only cool object"* |
| **Logo/tagline garbled** | Quote exact text + name the type, or *"no readable text"* (Pro for final type) |
| **End frame cluttered** | *"clean field behind the product, upper third flat and empty for the lockup"* |
| **Set reads as showroom** | Four-layer dress; add the today layer — unless the register IS seamless/plinth minimal (then commit: nothing extra at all) |
| **Two competing hero elements** | One element leads; demote the rest: *"first read the splash, second the bottle — nothing else moves"* |
| **Mirror/acrylic set with impossible reflections** | State what each reflection shows; run the rubric's reflection check |

---

## 6. Build order for any commercial frame

1. **Register** from the look-block table (one only).
2. **Format & framing:** packshot angle or lifestyle read-order; product frame-fraction; copy hole if type will sit on it.
3. **Set system** named + surface + palette side (drench/maximal vs quiet-luxury minimal).
4. **Light:** one idea, sourced and directional (studio rigs in `photography_pro.md`).
5. **Elements:** max 2–3, each with cause + direction; high-speed register if liquids freeze.
6. **Materials pass:** product surfaces named (clear-coat depth, frosted glass, soft-touch plastic).
7. **Text:** quoted + font named, or "no readable text."
8. Critique rubric + the placed-vs-owned check.


<!-- ═══════ FILE: nano-banana-prompter/references/styling_and_set_design.md ═══════ -->

# Nano Banana — styling & set design

Two crafts that make a frame believable: what the subject wears and how it moves, and the world they stand in.

> **Field-validated (Round 15, `field_findings.md`) — ImagineArt, 2026-07-06.** The four-layer set dress (architecture / function / inhabitant / today) scored PASS (strong, 21/22) on a character-revealing watch-repairer's workshop — the room read its absent owner through props alone.

---

## 1. Stylist vocabulary

### Silhouette → fabric behavior → wear state

Spec wardrobe in that order. The silhouette sets the shape; the fabric sets how it catches light and moves; the wear state sets whether it reads real.

**Fabric light & movement cheat sheet** (describe behavior, not just name — validated):

| Fabric | Behavior phrase |
|---|---|
| Silk charmeuse | *"pours and ripples, liquid speculars, hem lags the turn"* |
| Matte cashmere | *"holds its shape, soft matte light, gentle fold"* |
| Crisp poplin | *"sharp creases, holds a fold, low sheen"* |
| Denim | *"stiff, structured break at the knee, fades at stress points"* |
| Chiffon | *"sheer, translucent at the hem, floats behind the motion"* |
| Leather | *"creases and burnishes, hard speculars on the highlights"* |
| Wool tweed | *"matte, hairy texture, heavy drape, no shine"* |
| Satin | *"high liquid sheen, bright rolling highlight"* |

### Brand-register dressing

Dress to a register: old-money (quiet luxury, tonal, no logos), streetwear (proportion + logos + sneakers), workwear (canvas, utility, worn), minimal (neutral, architectural), maximal (clash, layered). Name the register so accessories, fabrics, and grooming agree.

### The one-disobedient-element rule

A perfectly coordinated outfit reads as a costume. Add one element that breaks the system — *"immaculate tailoring but scuffed worn-in sneakers,"* *"a formal gown with a chipped manicure."* The disobedient element is what makes styling read as a real person dressed, not a mannequin.

---

## 2. Production design — the four-layer set dress

Dress a space in four layers; skip one and it reads as an empty stage:

1. **Architecture** — the bones: walls, floor, windows, period, material.
2. **Function** — what the room is FOR: the furniture and tools of its purpose.
3. **Inhabitant** — who lives/works here: personal objects that imply a person (a worn chair, a specific hobby, photos).
4. **Today** — the signs of recent life: a half-drunk coffee, an open book, mail on the counter, shoes by the door, today's mess.

Most AI rooms have layers 1–2 and read as showrooms. Layers 3–4 are what make a space inhabited.

### Class signaling

Spaces and wardrobe encode class — wealth reads in *materials and space*, not clutter (honed stone, deep negative space, restraint) vs lived-pressure (laminate, fullness, function over form). State it deliberately; the model defaults to a generic aspirational middle.

### Prop logic

Every prop earns its place — it must look **owned, not placed**. A product in a lifestyle frame must look used: *"the bottle already open, a ring of condensation, used once."* Placed-looking props are the ad tell.

### The set checklist (run before generating an environment)

1. All four layers present?
2. One light direction the room agrees with?
3. Three-plane depth (foreground object / mid / background)?
4. Class register stated and consistent?
5. A "today" detail that implies someone just left?
6. No showroom emptiness unless the brief wants it?

Pair with `references/composition_posing_and_critique.md` (depth, blocking), `references/campaign_and_specialist_genres.md` (interiors/architecture), and `references/apparel_and_beauty.md`.


<!-- ═══════ FILE: nano-banana-prompter/references/apparel_and_beauty.md ═══════ -->

# Nano Banana — apparel & beauty

Designing and shooting clothes, makeup, and hair. Spec garments like a designer (silhouette → fabric+weight → construction → trims → wear → behavior); spec faces like a makeup artist.

> **Field-validated (Round 13, `field_findings.md`) — ImagineArt, 2026-07-06.** The beauty clamshell rig with deep-skin exposure (expose for the face, specular sheen, no ashy cast) scored PASS (strong, 21/22) on a dark-skinned West African model. Round 14: the ghost-mannequin (invisible-mannequin) e-comm format — filled 3D shape, hollow collar/back-neck, seamless white, hardware/stitch detail — scored PASS (strong, 20/22).

---

## 1. Garment anatomy (name the parts)

- **Necklines:** crew, scoop, V, boat, cowl, halter, square, sweetheart, mock, turtleneck.
- **Collars:** point, spread, band/mandarin, camp, peak/notch lapel, shawl, Peter Pan.
- **Sleeves:** set-in, raglan, dolman, bishop, puff, bell, cap; cuffs: barrel, French, knit-rib.
- **Construction:** princess seams, darts, yokes, pleats, gathers, panels, topstitching, bias cut.
- **Closures:** button placket, exposed/invisible zip, snap, toggle, hook-and-eye, drawcord, magnetic.

## 2. Silhouette taxonomy

A-line, sheath, shift, fit-and-flare, empire, column, wrap, peplum, oversized/boxy, tailored, cocoon, bias-drape. State the silhouette first — it governs everything.

## 3. Print & colorway language

Solid, heather, marled, color-block, ombré, tie-dye; prints: stripe (breton/pin/awning), check (gingham/tartan/windowpane), floral (ditsy/botanical), polka, paisley, camo, animal, geometric, all-over vs placement print. Colorway = the named color combo of one design.

## 4. Designing NEW garments

| Output | Prompt shape |
|---|---|
| Concept render | *"a [silhouette] in [fabric+weight], [construction], [trims], on a model / on a stand, studio seamless, design-render clarity"* |
| Technical flat | *"front and back technical flat (vector-style, no model, no shadow), all seams/topstitching/closures shown, flat lay on white"* — render at 2K (small labels blur at 1K) |
| Tech-pack board | *"a spec board: the flat plus callouts for fabric, trims, stitching, measurements"* |
| Fabric swatch | *"a close macro swatch of [fabric], weave/knit visible, true colorway"* |
| Colorway edit | *"the same garment in [new colorway], keep cut and construction identical"* |
| Print placement | *"place [print] on [panel], [scale], aligned at the seams"* |

## 5. Commerce formats

- **On-model** — fit + drape + lifestyle; full body or 3/4, clean light.
- **Ghost mannequin** — invisible-mannequin hollow form showing interior collar; works for exterior volume (the interior back-neck label view is unreliable — shoot it as a separate detail crop).
- **Flat lay** — overhead, styled-flat, even light, props minimal.
- **Try-on / UGC** — phone-shot in a mirror; route to `references/realism_and_ugc.md`.

## 6. Makeup (MUA vocabulary)

- **Base:** sheer/medium/full coverage, dewy vs matte, skin-like not masked, visible pores under it.
- **Eyes:** cut-crease, smoky, halo, graphic liner, floating shadow, lash styles (natural/wispy/spiky), mascara separation.
- **Named looks:** clean girl / no-makeup-makeup, soft glam, full glam, grunge smudge, 60s mod, 90s brown lip, euphoria gem/graphic, editorial avant-garde.
- **Lip:** matte/satin/gloss, blurred/over-lined, ombré; **cheek:** cream vs powder, draped blush, sunburn blush.
- **Macro standard:** *"100mm macro — real lip texture under gloss, highlighter particles, mascara-separated lashes, pores visible; flawless but human, not surfaced."*

## 7. Hair & nails

Hair: blunt/layered/shag cut; sleek/blowout/wet-look/piecey/baby hairs laid; texture (3a–4c coils, beachy waves, pin-straight); updo/half-up/slick bun. Nails: length (short/almond/coffin/stiletto), finish (gloss/matte/chrome), French/ombré/art.

## 8. Failure modes

| Symptom | Fix |
|---|---|
| Fabric looks generic | describe behavior, not name — *"silk charmeuse pours and ripples, liquid speculars"* (validated) |
| Garment text soft | render flats/labels at 2K+ |
| Ghost mannequin interior label wrong | shoot label as a separate crop |
| Makeup looks masked/plastic | demand pores under base, "flawless but human, not poreless" |
| Reflective trims over-amplified | scope it — *"only the zipper tape reflects"* (validated) |

Pair with `references/streetwear_and_genz.md` (fits/tribes) and `references/styling_and_set_design.md` (wardrobe behavior).


<!-- ═══════ FILE: nano-banana-prompter/references/streetwear_and_genz.md ═══════ -->

# Nano Banana — streetwear & Gen-Z

Streetwear lives or dies on **proportion and wear-state**, not labels. Spec the proportion ratio + the tribe + how worn-in it is + the sneakers.

> **Field-validated (Round 14, `field_findings.md`) — ImagineArt, 2026-07-06.** A cleanfit fit-pic (oversized boxy tee / wide-leg trousers proportion ratio, crisp not distressed) scored PASS (strong, 21/22) — the proportion-ratio + tribe grammar holds.

---

## 1. Proportion grammar (the streetwear key — field-validated)

State proportions explicitly; the model defaults to slim-fit unless told otherwise:
- **Top:** boxy, dropped shoulder, hem at [hip / mid-thigh], sleeve [pushed / past the wrist].
- **Bottom:** [baggy / wide / puddle] denim or cargo, *"pooling with two stacks over the shoe."*
- **Ratio:** name the silhouette — *"oversized top, baggy bottom"* (full volume) vs *"fitted top, baggy bottom"* (balanced) vs *"cropped top, low-rise wide"* (Y2K).
- *"Hem at mid-thigh, puddle jeans pooling with two stacks"* rendered exact proportions in testing — proportion-ratio language is confirmed high-leverage.

## 2. Nine aesthetic tribe blocks

| Tribe | Signatures |
|---|---|
| Y2K | low-rise, baby tee with chrome/graphic text, butterfly clips, tinted shades, flip phone, C-41 flash |
| Gorpcore | technical shell, fleece, carabiner, cargo, trail sneakers, orange accents, drizzle |
| Blokecore | retro football jersey, straight jeans, Samba/terrace trainers, lager-lad casual |
| Skate | baggy carpenter/Dickies, graphic tee, beat-up Vans/Dunks, scuffed, deck in hand |
| Streetgoth | all-black layered, tech drape, harness, chunky boots, silver hardware |
| Cleanfit | minimal neutral palette, quality basics, crisp white sneakers, ironed, "quiet" |
| Athleisure | matching set, leggings/joggers, cropped hoodie, sleek trainers, gym-to-street |
| Chaos / maximal styling | clashing prints, layered logos, stacked accessories, deliberate "too much" |
| Quiet-street / Opium | washed black, distressed, pointed boots, skinny-meets-baggy, moody monochrome |

## 3. Wear-state realism

New ≠ real. Add age: *"faded to a soft grey, cracked screen-print, frayed hem, scuffed toe-box, creased leather, a small stain, pilling at the cuffs."* Brand-new everything reads as a render. State how worn each piece is.

## 4. Fit-pic capture registers

- **Mirror selfie** — phone visible, bathroom/bedroom, flash or ambient, *"mirror selfie, phone covering part of the face."*
- **Street fit-pic** — full-body, 35mm, candid sidewalk, slight low angle, motion.
- **Flash-on-camera night** — hard direct flash, deep background, glossy speculars on fabric.
- Route realism through `references/realism_and_ugc.md` (UGC five-stack, selfie geometry).

## 5. Garment graphics & type spec

Quote graphic text literally and place it: *"the words 'ANGEL' in chrome bubble type across the chest of the baby tee."* Name placement (chest, back, sleeve, hem), technique (screen-print, puff, embroidery, flock, distress), and scale. Garment text renders well when quoted — confirmed.

## 6. Gen-Z casting notes

Real, diverse, un-retouched skin (visible texture, acne, freckles, braces, body hair); natural or expressive hair; layered thrifted mix; candid expressions over posed; tattoos/piercings; *"looks cast off the street, not a model agency."*

Pair with `references/apparel_and_beauty.md` (garment anatomy) and `references/styling_and_set_design.md`.


<!-- ═══════ FILE: nano-banana-prompter/references/football_and_fifa_frames.md ═══════ -->

# Nano Banana — football / FIFA frames (action keyframes, crowd & fan POVs)

The module for making football (soccer) stills — match action keyframes, celebrations, stadium atmosphere, and audience POVs — timed to the **FIFA World Cup 2026**. Nano Banana makes the **still**; for motion hand the hero to `seedance-2-prompter` / `kling-prompter`. Builds on and does not repeat:
- **How the frame is finished (realism)** → `references/frame_realism_engine.md`. Match stills use its film-scan register or a broadcast-clean register; **freeze-vs-pan capture is the football-specific layer this file adds.**
- **Lens character, motion blur, grain, floodlight/flare** → `references/optics_grain_and_light.md`. **Sports-grit look block** → `references/commercial_framing_and_set_design.md`.
- **Peak-action posing & three-plane depth** → `references/composition_posing_and_critique.md`. **Casting the players/fans** → `references/global_ethnicity_casting.md` (+ regional files).

> **⚠️ Rights & likeness — read first.** Do NOT depict **real, named players** or reproduce **real team crests, sponsor logos, or the exact FIFA/World Cup marks**. Cast **fictional players**, invent generic kit colours and crests, and leave advertising boards blank or generic. This keeps the work clear of public-figure and trademark issues while still reading unmistakably as World-Cup-calibre football.

### FIFA World Cup 2026 — grounding facts (for atmosphere, not logos)
Hosted by **Canada, Mexico & the USA**, **11 June – 19 July 2026**, **16 host cities** (11 US incl. NY/NJ, LA, Dallas, Atlanta, Miami, Houston, Seattle, Philadelphia, SF Bay, Boston, Kansas City; Mexico City, Guadalajara, Monterrey; Toronto, Vancouver). First **48-team** edition, **104 matches**, new round of 32; **final 19 July at NY/NJ (MetLife)**. Official ball: **adidas TRIONDA** (render a generic modern paneled ball unless licensed). Summer tournament — expect **hot day matches and floodlit night games**, huge multinational crowds, and the three-nation fan mix.

---

## The core of "how these frames are made": FREEZE vs PAN

Every football action still is one of two capture decisions. State which.

- **FREEZE (peak-action sharp).** High shutter (**1/1000–1/2000s**), long telephoto (**300–600mm**, f/2.8–4), continuous AF, burst caught at the peak instant. The ball, the boot, the sweat, the turf spray all frozen crisp; background compressed to soft creamy bokeh so the player pops. Use for the strike, header, save, tackle. Prompt cue: *"frozen at 1/2000s, ball and turf-spray tack-sharp, long-lens compressed crowd bokeh."*
- **PAN (motion-blur speed).** Slow shutter (**1/60–1/125s**) tracking the runner: **subject sharp, background streaked** horizontally into speed lines. Use for the sprint, the break, the dribble down the wing. Prompt cue: *"panning motion blur, the sprinting player sharp, the stadium streaked into horizontal speed lines behind."*

Supporting layer every time: **long-lens compression** (300mm+ flattens depth, isolates the player against a wall of soft crowd), **shallow DOF** (one plane sharp), **stadium light** (floodlit night = multiple hard sources + rim/kick on wet grass + light bloom; day = hard sun + hard shadows; golden-hour = long shadows across the pitch), and **turf truth** (churned divots, chalk lines, grass debris kicked up).

---

## Action keyframe library (the peak instants)

| Keyframe | How to frame it |
|---|---|
| **The strike / shot** | low angle, striker's plant-foot planted and kicking-boot through the ball, ball leaving the boot deforming slightly, body torqued; freeze 1/2000s |
| **The header** | both feet off the ground, neck snapped through the ball, arms out for balance, defenders straining around; peak of the leap |
| **The bicycle / scissor kick** | full inversion, body horizontal above the turf, boot meeting the ball overhead, crowd blurred behind; the hero acrobatic frame |
| **The slide tackle** | low side angle, a fan of turf and water spraying off the sliding boot, both players' weight and strain visible |
| **The save** | goalkeeper full-stretch airborne, fingertips deflecting the ball, body arched, mud on the shirt; behind-goal or side angle |
| **The duel / dribble** | shoulder-to-shoulder contest, one player shielding the ball, the other lunging; tension and lean |
| **The free-kick wall** | the jumping wall of defenders mid-leap, arms crossed, the ball curling; shoot from behind the taker or side-on |
| **The penalty** | isolation and dread — striker over the ball, keeper crouched on the line, empty net tension; long lens, shallow |
| **The goal-line moment** | ball crossing (or clawed off) the line, net rippling, defenders lunging; behind-goal net-cam view |

Physics to keep honest: the **ball deforms** on hard contact; **motion blur direction** matches the movement; a struck/thrown ball may streak while the player is sharp; **turf spray** arcs with real gravity; boots and shins carry **grass stain and mud**.

---

## Celebration keyframes (emotion at peak)

The knee-slide (arms wide, turf spraying, roar); the arms-out primal roar to the crowd; the shirt-pull-over-head sprint; the team pile-on dogpile; the badge/crest kiss; the corner-flag charge; the leap into the stands; the bench eruption (subs sprinting on); the solo redemption (a lone player, hands on head or knees, tears); the manager's touchline fist. Frame for **raw emotion + a held peak** — mid-roar, mid-slide, eyes alive — not posed. Crowd behind explodes in soft bokeh; one saturated kit colour anchors the frame.

---

## Audience & POV registers (the "fan POV" ask)

| POV | Component block |
|---|---|
| **Fan-in-the-stands POV** | shot from a seat — heads, scarves and raised phones in the foreground, the tiny bright green pitch far below, a stadium tier curving away; slight phone-capture look for authenticity |
| **Ultras / tifo** | a whole stand as a giant choreographed mosaic or banner, flares and coloured smoke, flags and drums, dense bodies, deep saturated block of one colour |
| **Face-paint fan portrait** | a single fan in national-flag face paint (invented flag colours), scarf held overhead, mid-cheer or tears of joy, crowd bokeh behind, real skin under the paint |
| **Watch-party / fan-zone** | a crowd in a public square or bar reacting to a big screen, faces lit by the screen glow, arms up, mixed emotion across the crowd |
| **Pitchside photographer POV** | very low, long lens, sometimes **through the goal net** (soft net mesh in the near foreground), player filling the frame |
| **Behind-goal net-cam** | centered top-down-ish from behind the goalpost, goal-line clarity, the keeper and net in frame |
| **High gantry / master (broadcast view)** | wide from the halfway line, whole pitch geometry, tiny players, the game's shape |
| **Spidercam / aerial** | overhead cabled view swooping over the pitch, players small, patterns of movement, stadium bowl around |
| **Tunnel walkout** | players emerging from the dark tunnel into stadium light, kids' hands held, flags, the roar ahead |
| **Trophy lift / confetti** | the captain hoisting a (generic) trophy, gold confetti and streamers filling the air, teammates roaring below, floodlight bloom |

---

## Stadium & atmosphere ledger
Packed curving tiers of colour, tifo mosaics and giant flags, floodlight arrays with visible bloom and lens flare, **wet pitch specular** at night, coloured smoke and flares, gold confetti, corner flags bent in the wind, the goal net's soft mesh, blank/generic LED advertising boards, the fourth-official's substitution board, churned turf with chalk lines, breath-fog in a cold match, heat-shimmer in a summer day game. **Crowds must vary** — thousands of distinct faces, not clone-stamped; span the real multinational World-Cup mix (`global_ethnicity_casting.md` + regional files).

---

## Worked Nano Banana prompts

**A — Freeze-frame header, floodlit night (hero action key art)** · 16:9 · Pro
```
A dramatic football action still: a fictional midfielder in a plain red kit (invented crest, no logos) rising into a header at the peak of his leap, both feet off the ground, neck snapped through a generic white paneled ball that deforms slightly on contact, two defenders in white straining around him. floodlit night stadium, multiple hard light sources with rim/kick light on the wet green turf, packed crowd compressed into soft colourful bokeh behind. frozen at 1/2000s, 400mm long lens, f/2.8 shallow focus, the player and ball tack-sharp, turf and sweat crisp. real skin — pores, sweat sheen, strain, flushed exertion, no plastic; grass stain on the kit. film-scan finish: low contrast, lifted colour-holding blacks, soft highlight rolloff on the floodlights with faint halation, fine grain, one saturated red kit anchor — no HDR, no oversharpening, no readable text/logos. 16:9, clean frame.
```

**B — Pan-blur wing sprint (speed)** · 21:9 · Pro
```
A football speed frame: a fictional winger in a yellow kit sprinting down the touchline with the ball at his feet, caught in a panning motion blur — the player sharp, the stadium and crowd streaked into horizontal speed lines behind, the turf smeared beneath his boots. 1/60s pan, 300mm, day match with hard summer sun and hard shadows, heat-shimmer. real straining skin and grass-stained shins, one yellow anchor. film-scan finish — muted, low contrast, fine grain, no HDR, no logos, no readable text. 21:9, clean frame.
```

**C — Knee-slide celebration** · 16:9 · Pro
```
A football celebration keyframe: a fictional striker in a blue kit on a knee-slide across wet floodlit turf, arms flung wide, mouth open mid-roar, a fan of turf and water spraying up behind his sliding knees, teammates sprinting toward him out of focus. floodlit night, rim light on the spray, packed crowd exploding into soft bokeh. frozen 1/1600s, 300mm shallow. raw real emotion, sweat and grass stain, real skin never plastic, one blue anchor. film-scan finish — lifted blacks, soft floodlight halation, fine grain, no HDR, no logos or readable text. 16:9, clean frame.
```

**D — Fan-in-stands POV with tifo** · 9:16 · Pro
```
A fan's-eye view from deep in the stands at a World-Cup night match: out-of-focus heads, scarves and a few raised phones across the foreground, the small bright-green pitch far below, and across the far stand a huge choreographed tifo mosaic in bold colour with coloured smoke drifting and flags waving. authentic slightly-phone-capture look, mixed floodlight, thousands of distinct varied faces (no cloned faces), deep saturated crowd colour. real, not staged — no HDR glow, no readable text or brand logos, no camera UI. 9:16, clean frame.
```

**E — Face-paint fan portrait** · 4:5 · Pro
```
A close portrait of a jubilant football fan in the stands, cheeks painted in two invented national-flag colours, a scarf held taut overhead, mid-cheer with genuine joy, floodlit crowd compressed into soft bokeh behind. 135mm, shallow focus, frozen. real skin under the paint — pores, sweat, cheek flush, broken specular, subsurface at the ears, wet eyes with a matched catchlight; the paint sits on real skin texture, never plastic. film-scan finish — low contrast, lifted blacks, fine grain, one saturated anchor, no HDR, no readable text or logos. 4:5, clean frame.
```

---

## Failure modes

| Failure | Fix |
|---|---|
| **Real player likeness / real crests / sponsor logos** | cast fictional players, invent kit colours + crest, blank advertising boards, generic ball — state *"no logos, no readable text"* |
| **Mangled ball / limbs in a duel** | check finger/limb counts, one ball, plausible joints; state the exact action so bodies don't merge |
| **Motion blur wrong** | freeze = everything sharp; pan = subject sharp + background streaked in the direction of travel; struck ball may streak while player is sharp |
| **Clone-stamped crowd** | *"thousands of distinct varied faces, no repeated faces"*; span the real multinational mix |
| **Over-clean turf / kit** | churned divots, chalk lines, grass debris; grass-stained shins and mud on the keeper |
| **Floodlights clipped to white blobs** | soft highlight rolloff + faint halation, not blown discs |
| **Posed-at-lens players** | mid-action / mid-roar, eyes on the ball or the crowd, never smiling at camera |
| **Generic "stock soccer" flatness** | pick freeze-or-pan, a real angle (net-cam/pitchside/stands), one kit-colour anchor, floodlit specular + atmosphere |
| **Garbled scoreboard/banner text** | Nano Banana Pro + quoted exact text, or *"no readable text"* |

---

> **Not yet field-validated** (new module, 2026-07-06). Queue a scored round (Round 16) in `references/field_findings.md` — test a freeze header, a pan sprint, a knee-slide, a stands-POV tifo, and a face-paint fan. Expect the model's strongest pulls to be clone-crowds, over-clean turf, blown floodlights, and posed-at-lens players — the fixes above target exactly those.

## Sources
- [FIFA World Cup 2026 — Wikipedia](https://en.wikipedia.org/wiki/2026_FIFA_World_Cup) · [Host cities & dates — FIFA](https://www.fifa.com/en/tournaments/mens/worldcup/canadamexicousa2026/host-cities)
- [Camera settings for sports photography — Tamron](https://tamron-americas.com/blog/camera-settings-for-sports-photography/) · [Soccer photography tips — ExposureGuide](https://www.exposureguide.com/soccer-photography-tips/) · [Perfect settings for action & sports — Photography Mad](https://www.photographymad.com/pages/view/the-perfect-camera-settings-for-action-and-sports-photography)
- [Football broadcast camera positions — PTZOptics](https://ptzoptics.com/football/) · [World Cup camera angles — Why Is This Interesting](https://whyisthisinteresting.substack.com/p/the-world-cup-camera-angles-edition)


<!-- ═══════ FILE: nano-banana-prompter/references/closeups_and_interviews.md ═══════ -->

# Nano Banana — close-ups, interviews & dialogue frames

Talking heads, portraits at conversational distance, and two-handers. The genre where eyeline and a single good key do all the work.

> **Field-validated (Round 13, `field_findings.md`) — ImagineArt, 2026-07-06.** The seven-step cinematic-interview formula (Rembrandt key, shadow-side-to-camera, negative fill, off-lens eyeline + look-room, lavalier, practical bokeh) scored PASS (strong, 21/22) on a documentary talking-head.

---

## 1. Shot-size grammar (with the lens for each)

| Size | Frames | Lens | Job |
|---|---|---|---|
| ECU (extreme close-up) | eyes / mouth only | 100mm macro | emotion detail, inserts |
| CU (close-up) | head + a little shoulder | 85mm | the interview standard |
| MCU (medium close-up) | chest up | 50–85mm | dialogue default |
| MS (medium) | waist up | 35–50mm | gesture + context |
| MWS / cowboy | mid-thigh up | 35mm | two-handers, body language |
| WS (wide) | full figure + room | 24–35mm | establish, isolate in space |

Longer lens = more compression + softer background = more intimate. State the size AND the lens; "close-up" alone under-specifies the compression.

## 2. The seven-step cinematic interview formula

1. **Rembrandt key** — soft key 45° off-axis, high enough to put a small triangle of light on the shadow cheek.
2. **Shadow side to camera** — turn the lit side *away* slightly so the camera sees the shadow side; this is what makes it look lit, not flashed.
3. **Negative fill** — a black flag on the bright side to deepen the falloff (don't fill — subtract).
4. **Off-lens eyeline + look-room** — subject talks to an interviewer just off the lens; leave space on the side they look toward. *"Eyeline camera-left, room on the left."*
5. **Practical bokeh** — soft background with a couple of out-of-focus practicals (a lamp, a window) for depth, ~f/2.
6. **Lavalier mic** — a small clipped mic reads as "real interview"; include it.
7. **Mid-answer mouth** — *"caught mid-sentence, mouth slightly open"* — a closed neutral mouth reads as a posed portrait, not an interview.

> *"MCU on a 50-year-old man, 85mm at f/2, soft Rembrandt key from camera-right with a triangle of light on the near (shadow) cheek, black negative fill camera-left, eyeline just off the lens to camera-right with look-room on that side, a lavalier clipped to his collar, two soft practicals melting in the background, caught mid-answer."*

## 3. Talkie / dialogue frames

- **OTS (over-the-shoulder) pairs** — shoot both sides matched: same lens, same height, the foreground shoulder soft. Obey the 180° line so eyelines reverse correctly.
- **Listening shot** — the reverse on the person NOT talking; reactions sell scenes. *"holding on her listening, a flicker of doubt."*
- **Two-temperature phone call** — intercut two locations with different colour temps (warm room vs cold street) so the cut reads instantly.
- **Walk-and-talk** — 35mm, steadicam-style, subjects mid-stride, background sliding; *"shot walking backward ahead of them."*

## 4. Vox-pop register

Street-interview look: 35mm, available light, slightly imperfect framing, a handheld feel, a stick-mic or lav, a busy real background thrown soft. *"Looks grabbed on the sidewalk, not lit."*

## 5. Close-up craft

- **Focus on the near eye** — *"critical focus on the near eye, the far eye just softening."* The single biggest CU tell when wrong.
- **One catchlight** — a single clean catchlight at ~10–11 o'clock reads alive; two competing catchlights read fake.
- **Emotion as physical state, not label** — *"eyes glassy, jaw tight, a breath held"* beats "sad." See `references/composition_posing_and_critique.md`.

## 6. Validated finding — the eyeline coin-flip

Across a 20-frame test round, the model **flips eyeline direction about half the time** — it knows to look off-lens but picks the side at random. Fix: state the side as a *consequence*, twice — *"she looks toward camera-LEFT, the empty look-room on the LEFT, the back of her head toward the right edge."* And CHECK eyeline direction on every frame of a series; a flipped reverse breaks the 180° line on the cut. Restate wardrobe in full each frame of a series — the model drops accessories between generations.


<!-- ═══════ FILE: nano-banana-prompter/references/campaign_and_specialist_genres.md ═══════ -->

# Nano Banana — Campaign craft & specialist genres

How working creative teams compose for ads and how four specialist genres are actually shot.

> **Field-validated (Round 13, `field_findings.md`) — ImagineArt, 2026-07-06.** The automotive (21/22), architecture twilight-balance (21/22), and beverage/high-speed genres scored PASS (strong).

---

## 1. Campaign craft

### Composing for copy

A key visual is a photograph with a hole in it. Decide the hole first:
> *"Composition leaves the upper-left third as clean negative space — even tone, low detail, no highlights — for headline placement. Subject weighted lower-right, eyeline traveling INTO the copy space."*

Rules: copy space = lowest-contrast region; subject gaze or motion should point at it (gaze steers reading order); never put speculars or busy texture where type will sit. For known type color: *"copy area dark enough to hold white type."*

### Key-visual hierarchy

One read order, three beats: *"First read: her face. Second read: the product in her hand. Third read: the location context. Nothing else competes."* Stating reads explicitly is the strongest art-direction instruction Nano Banana takes.

### Multi-format from one concept

Shoot the master wide with protected zones, then re-frame:
> Master: *"16:9, subject center-right, action contained in the middle 60% — safe to crop to 1:1 and 9:16 without losing limbs or the product."*
Then per format: 9:16 = *"recompose vertical: subject full-height, copy space top"*; 1:1 = *"tight crop, face and product only"*; OOH 48-sheet = *"extreme simplicity, one subject one message, readable at 60mph."*

### Campaign series coherence

A campaign = one tonal family + one lighting register + one styling register across all frames; ONLY the scenario changes. Define a "campaign block" (like the film production-look block) and paste verbatim into every deliverable.

### Social-native ad craft

Feed-stopping ≠ polished: *"thumb-stop via one high-contrast anomaly — a red wall, an odd prop, an unexpected crop."* UGC-style ads: use the realism/UGC stack, then add the product with prop logic (it must look owned, not placed). Hold 20% bottom clear for platform UI overlays in 9:16.

---

## 2. Beauty & cosmetics close-up

The most demanding genre — skin at macro scale with commercial polish that still reads human.

- **Light:** clamshell default; *"large octa above lens, silver bounce below, white-out background or deep color seamless."* For texture stories: *"single hard light raking across the cheekbone showing skin grain."*
- **Skin standard:** *"flawless but human — pores visible at this scale, fine vellus hair on the cheek, real lip texture under the gloss; no blur retouch, color-corrected not surfaced."* The commercial retouch register is *even*, not *poreless*.
- **Makeup as subject:** name products like a makeup artist: *"matte terracotta lip with sharp edge, glossy lid catching a vertical highlight, brushed-up brows, no foundation flatness."*
- **Macro details:** *"100mm macro on the eye: iris fibers sharp, mascara-separated lashes, highlighter particles visible."*
- **Hands/product contact:** *"fingertips pressing the cream — realistic skin compression and product displacement."* Compression is the realism tell.

## 3. Automotive

- **The body is a mirror:** light cars by what reflects. *"One continuous softbox streak running the full body line; black studio walls so panels fall dark; the horizon line reflection unbroken along the shoulder."*
- **Location hero:** *"dusk, headlights on, 10 minutes after sunset — sky still holds gradient, body picks up cool sky from above and warm ground bounce below."* The dusk window is THE automotive cliché because it works.
- **Angles:** *"3/4 front low at bumper height, wheels turned toward camera"* (showroom) · *"rear 3/4 driving away on a mountain road"* (lifestyle) · *"dead side profile, long lens, panned motion blur on wheels and road"* (speed).
- **Wheel rule:** moving car = *"wheels blurred with rotation, body sharp"*; static = wheels posed at an angle, valve caps down (detail obsessives notice).
- **Surfaces:** *"deep paint with clear-coat depth, metallic flake visible in the highlight rolloff, realistic panel gaps."*

## 4. Food

- **Backlight is law:** *"key from behind the table through diffusion, front fill card only — steam, gloss, and translucency all come from backlight."*
- **The 10-minute rule:** food looks alive briefly — *"just-plated energy: steam rising, butter mid-melt, herbs still standing, one drip running."*
- **Messy-edge styling:** *"crumbs scattered with intent, sauce smear on the rim, torn bread not sliced"* — pristine plates read as plastic.
- **Angles by dish:** flat things (pizza, spreads) = overhead; stacked things (burgers, cakes) = 10-25° straight-on; bowls = 45°.
- **Color:** food wants warm — *"white balance slightly warm, greens kept vivid, no blue cast anywhere on the plate."*

## 5. Architecture & interiors

- **Verticals are sacred:** *"all vertical lines perfectly parallel — tilt-shift discipline, no keystone convergence."* The single biggest pro/amateur divider.
- **Twilight balance:** *"dusk exterior, interior lights on, exposure balanced so windows glow without clipping and sky holds color."*
- **One-light-direction interiors:** *"daylight from the window wall only, no mixed overheads; shadows agree."*
- **Staging:** apply the set-design four layers, but cleaner — interiors sell aspiration: inhabitant layer present but tidy (*"a book open on the arm of the chair"*), today layer minimal.
- **Lens:** 24mm for rooms (*"corners shown, no fisheye stretch on furniture"*), 50mm for vignettes, aerial/drone establishing for exteriors.

---

## Genre routing

Beauty close-up → clamshell + human-skin standard. Car → reflection-managed streak light or dusk window. Food → backlight + 10-minute energy. Space → straight verticals + balanced twilight. Campaign → copy hole + read order + campaign block. Always end with the critique rubric pass.
