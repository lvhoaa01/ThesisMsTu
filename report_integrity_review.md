# Report Integrity Review

Review date: 2026-05-25  
Reviewer role: academic integrity and report-quality audit. This review does not conclude that any paragraph is plagiarized or AI-generated; it identifies risk signals that should be corrected through legitimate academic revision.

## 1. Scope and Input Files

- Report file: `rpMisPh.md` at `C:\DDrive\ThesisMsTu\rpMisPh.md`. This is the only Markdown report found in the root folder. Size: 611 lines, about 399,353 characters. The file also contains embedded base64 images at the end, which were ignored for text-similarity analysis.
- PDF files in `docs/`:
  - `docs/Computational_Actuarial_Science_with_R_Chap07_08.pdf`: 58 pages; text extracted successfully with PyMuPDF.
  - `docs/DemoLab_Paper_01_2019_Trend_Longevity.pdf`: 69 pages; `pypdf` failed with `startxref not found`, but PyMuPDF extracted text from 66 non-empty pages. Because the PDF structure appears damaged, page-level comparison should be treated as approximate.
  - `docs/M3630Weeks2to3-f2019-annot.pdf`: 83 pages; text extracted from 33 non-empty pages.
  - `docs/M3630Weeks4to5-f2019.pdf`: 29 pages; text extracted successfully.
- Reference links extracted: 81 URL occurrences, 38 unique URLs. Many are duplicates, Google Search wrapper links, search-result pages, or bare/incomplete links.
- Limitations:
  - This is not a Turnitin report and does not access proprietary similarity databases.
  - Similarity checks used the report, the four local PDFs, and web sources that were accessible from this environment.
  - Online access varied: some pages returned 403, 404, SSL errors, or search pages rather than source documents.
  - Images/charts were not OCR-verified; only surrounding text was reviewed.
  - In-text citation extraction is approximate because the report mixes APA-like citations, Markdown links, raw URLs, and instructional notes.

## 2. Executive Summary

Overall risk level: High before revision. The largest risk is not one single copied passage, but the combination of draft artifacts, weak citation architecture, repeated self-corpus paragraphs, over-general academic prose, and inconsistent terminology.

Most serious issues:

- The report still contains non-report material: Vietnamese drafting instructions, "copy/dán" guidance, placeholder figure notes, and advice addressed to the writer. These must be removed before submission.
- The References area is not a clean reference list. It contains raw URLs, duplicate URLs, Google Search links, a broken bare link, and several sources that are not cited in the text.
- Several key claims use data from credible sources but cite the wrong URL or cite a Google Search wrapper instead of the original source. FINMA market figures are the clearest example.
- Large blocks are duplicated inside the same report, especially the female longevity analysis, survival-function explanation, policy-reform discussion, and market-size discussion.
- Terminology is often over-assertive or imprecise: `l_x` is called a "Survival Distribution Function", the Lexis Point is treated as a biological limit, TLE/HLE data are described as "up to 2024" although WHO values are 2021, and technical reserves/liabilities are reported inconsistently.

Revise first: remove draft artifacts, rebuild References, repair citation placement, delete duplicate blocks, then rewrite the high-risk analytical paragraphs with precise source support and cautious academic claims.

## 3. Risk Scale

- Mức 1 - Thấp: Common terminology, standard formulae, or properly cited content. Minor formatting, citation placement, or wording polish is enough.
- Mức 2 - Trung bình: Wording, structure, or logic is too close to a source or too generic; citations are present but incomplete, misplaced, or insufficiently precise. Needs academic paraphrase, clearer reasoning, or more specific citation.
- Mức 3 - Cao: Text likely to cause serious academic-integrity concern: near-copying, patchwriting, uncited specific claims, broken or wrong sources, draft instructions left in the report, misleading terminology, or claims unsupported by the cited source. Needs immediate correction.

## 4. Similarity / Plagiarism-like Risk

| No. | Location | Extract from report | Possible source / reason | Risk level | Explanation | Suggested fix |
|---|---|---|---|---|---|---|
| 1 | `Task 5`, lines 364-389 | "Bạn có thể copy các nguồn chuẩn..." and "Khi bạn dán đoạn văn..." | Report self-corpus / drafting notes | Mức 3 | These are instructions to the writer, not report content. They create high risk of appearing copied from a prompt/chat draft and are academically inappropriate. | Delete the entire instructional block. Convert only valid sources into a formal References section. |
| 2 | `Task1`, lines 58-78 and `Mẹo`, lines 415-433 | Female longevity and survival-curve explanation repeated nearly verbatim | Report self-corpus | Mức 3 | Exact or near-exact repetition can inflate similarity and signals an unedited compiled draft. | Keep one final version only. If both contain useful details, merge them into one concise analysis with source-linked chart values. |
| 3 | `Task1`, lines 162-168 and lines 477-486 | Policy reform discussion repeated with minor formatting changes | Report self-corpus | Mức 3 | The AHV 21 and 13th pension paragraphs reappear with overlapping logic and wording. | Retain the stronger version, cite BSV/FSIO directly, and remove the duplicate. |
| 4 | `Task3`, lines 210-238 and `Thẻ 8`, lines 500-510 | FINMA market-size and institutional-capacity discussion repeated | Report self-corpus and FINMA source material | Mức 2 | The same figures and phrases recur in separate sections, with partially inconsistent numbers. | Consolidate market-size discussion into one section; use one FINMA citation per cluster of related figures. |
| 5 | `Task1`, lines 44-48 | "three interconnected demographic markers... e0, e65 + 65, and the Lexis Point" | Internal PDF: `DemoLab_Paper_01_2019_Trend_Longevity.pdf` discusses the same marker set | Mức 2 | The marker selection and explanatory sequence closely follow the DemoLab paper. The concept is valid, but the report needs an explicit citation and independent application to Switzerland. | Cite Pitacco/Carmeci or the DemoLab paper when introducing the markers, then explain why these indicators are appropriate for Swiss HMD data. |
| 6 | `Task1`, lines 74-78 and lines 429-433 | "rectangularization" and "expansion" of survival curves | Internal PDF: DemoLab paper uses these two features for longevity trends | Mức 2 | The structure of the explanation tracks the source conceptually. It is not necessarily copied, but it is source-dependent. | Add a citation at the first use and rewrite with Switzerland-specific evidence from the chart, avoiding broad claims such as "perfectly reflects". |
| 7 | `Task1`, lines 30-34 | Curtate expectation formula and `l_x` explanation | Internal PDFs: actuarial lecture notes and Computational Actuarial Science chapter | Mức 1 | The formula is standard actuarial notation. Similarity is expected for formulae, but the source should be acknowledged. | Cite the actuarial textbook/lecture note near the formula and define the notation once. |
| 8 | `Task2`, line 191 | "directly validates the Pandemic theory" | Internal PDF: DemoLab paper discusses pandemic theory of morbidity/disability | Mức 3 | A named theory is used with a strong claim, but the reference is unclear and `Pitacco, 2014` is not properly listed in References. | Add the exact source, define the theory, and change "validates" to a cautious phrase such as "is consistent with". |
| 9 | `Task1`, line 112 | "Martinović et al. (2024)" | Online PMC article exists, but no full reference appears in the report | Mức 2 | The citation appears in text but is absent from a formal reference list. The sentence also uses the source to support a broad Swiss-specific claim. | Add a full APA reference and explain how the general prevention framework applies to Switzerland. |
| 10 | `Task3`, lines 214, 220, 238, 500, 508, 510 | FINMA figures cited through `google.com/search?q=...` or a broken FINMA news link | FINMA original source exists, but current citation is wrong | Mức 3 | Citing a search URL or a 404 page makes the evidence chain unreliable even when the numbers may be correct. | Replace all Google wrapper links with the FINMA report/news URL and cite the exact report year. |
| 11 | `Thẻ 8`, lines 546-573 | Swiss LTC product design and ADL-trigger claims | No sufficiently precise source in current References | Mức 2 | The passage contains specific product and benefit-design claims, but citation support is broad and unclear. | Add an insurance/product-regulation source or rewrite as a cautious overview. Distinguish mandatory health insurance, supplementary insurance, and life-insurance riders. |

## 5. AI-writing Risk

| No. | Location | Extract from report | AI-like signals | Risk level | Explanation | Suggested fix |
|---|---|---|---|---|---|---|
| 1 | `Task1`, line 15 | "The quantitative assessment of mortality assumptions..." | Very long sentence, generic framing, unresolved "(cần dẫn chứng)" | Mức 3 | The sentence is overloaded and still includes a note asking for citation. | Split into shorter claims. Add a source for dynamic mortality assumptions and connect directly to HMD/HMD life tables. |
| 2 | `Task1`, lines 58-68 | "exceptionally clear demonstration", "most vital original insight", "powerful empirical evidence" | Repeated intensifiers, formulaic structure, overclaiming | Mức 2 | The paragraph has data, but the language is more promotional than analytical. | Keep the numbers, reduce adjectives, and explain the mechanism using one or two measured comparisons. |
| 3 | `Task1`, lines 98-116 | "align seamlessly", "purely driven", "proving that background hazards..." | Absolute claims from a single model fit | Mức 3 | A Gompertz-Makeham fit cannot by itself prove background hazards are negligible in a broad social sense. | Use "suggests" or "is consistent with"; report coefficients, goodness-of-fit, and limitations. |
| 4 | `Task1`, lines 146-160 | "eradication proves", "successfully decoupled young male survival..." | Causal claims without direct evidence | Mức 2 | The text infers social causes from mortality curves without citing workplace, accident, or health-behavior data. | Add FSO/OECD/health-behavior sources or reframe as a hypothesis. |
| 5 | `Task2`, lines 176-199 | "absolute structural and economic justification" | Overconfident policy claim | Mức 2 | WHO TLE/HLE data support a morbidity burden, but do not by themselves prove AHV 21 policy design. | Separate demographic evidence from policy interpretation. Cite BSV for policy and use cautious causal language. |
| 6 | `Task3`, lines 206-255 | "monumental", "titans", "sovereign player", "capillary grid" | Grandiose style, business-journal tone | Mức 3 | The prose sounds generic and promotional, weakening academic credibility. | Rewrite in neutral academic English. Use exact FINMA variables, years, and denominators. |
| 7 | `Task5`, lines 397, 405, 411-413 | Figure placeholders and "Mẹo cho bạn..." | Draft scaffolding and conversational guidance | Mức 3 | These lines are direct evidence that the document is not submission-ready. | Delete all placeholders and replace them with final figure captions or references to actual figures. |
| 8 | `Thẻ 8`, lines 496-546 | "highly mature", "systemically vital", "immense", "indispensable macroeconomic pillar" | Dense generic praise with limited analytical movement | Mức 2 | The section uses many evaluative adjectives before establishing data and method. | Start with FINMA data, then interpret cautiously. |
| 9 | `Thẻ 8`, lines 546-573 | LTC discussion | Broad generalizations, product claims without specific source | Mức 2 | The text may be plausible but lacks the evidence density needed for specialized insurance claims. | Cite Swiss regulation or insurer product documents; specify whether claims refer to private life riders, supplementary health insurance, or social care funding. |
| 10 | `Abstract`, lines 5-11 | "Switzerland emerges as a representative example..." | Some generic academic phrasing | Mức 1 | The abstract is relatively coherent, but it should be tightened after the body is revised. | Add one or two concrete findings from the report, such as exact e0/e65 changes and the model used. |

## 6. Terminology Risk

| No. | Term | Location | Issue | Risk level | Suggested correction |
|---|---|---|---|---|---|
| 1 | `Survival Distribution Function (l_x)` | `Task1`, line 22 | `l_x` is the life-table survivorship function, not usually called a survival distribution function. A survival function is normally `S(x)` or normalized `l_x/l_0`. | Mức 3 | Use: "the life-table survivorship function `l_x`, normalized as `l_x/l_0` when interpreted as a survival probability." |
| 2 | `Curtate expectation of life` vs `life expectancy` | `Task1`, lines 30-40 and `Task2`, lines 176-184 | The report compares curtate life-table values with WHO TLE/HALE without explaining that WHO life expectancy is not necessarily curtate. | Mức 2 | Define `e_x` as curtate expectation from HMD life tables and distinguish it from WHO period life expectancy and HALE. |
| 3 | `Lexis Point` | `Task1`, lines 46, 64, 144 | The report treats it as a "natural biological lifespan" or "biological wall". That overstates what a modal age at death can prove. | Mức 3 | Define it as "modal age at death among adult-old ages" and avoid biological-limit language unless supported by literature. |
| 4 | `Pandemic theory` | `Task2`, line 191 | The term is not defined carefully and may be confused with COVID-19. | Mức 2 | Use "pandemic theory of morbidity/disability expansion" and cite the source where the theory is introduced. |
| 5 | `Mortality compression` vs morbidity compression | Multiple, especially `Task1` and `Task2` | The report sometimes moves from mortality compression to disability burden without clearly separating death timing from health-state timing. | Mức 2 | Add a sentence distinguishing mortality compression from compression/expansion of morbidity. |
| 6 | `Gompertz` and `Gompertz-Makeham` | `Task1`, lines 108-116 and 152-154 | The report says the fit "proves" pure senescent mortality. That is a methodological overclaim. | Mức 3 | Say the fit "suggests age-dependent mortality dominates over the fitted age range"; report parameters and residuals. |
| 7 | `APV`, `APVB` | `Task4`, lines 267-282 | `APVB` appears without a clean first definition and is mixed with broader APV wording. | Mức 1 | Define once: "Actuarial Present Value of Benefits (APVB)" and use consistently. |
| 8 | `Deferred Life Annuity Ordinary` | `Task4`, line 267 | The phrase is nonstandard/unclear. | Mức 2 | Use "deferred life annuity-immediate" or "deferred life annuity-due" depending on payment timing. |
| 9 | Technical reserves/liabilities | `Task3`, lines 220-228 | The report states CHF 512 billion in reserves, then later CHF 252.3 billion in technical liabilities and CHF 290.2 billion balance sheet. Denominator is unclear. | Mức 3 | State exactly whether the figure is total insurance sector, life sector, technical provisions, tied assets, or balance sheet total. Cite FINMA table. |
| 10 | `Group Life Segment 75% to 80%` | `Thẻ 8`, line 537 | Conflicts with a later/earlier reserve share of about 57.8%, unless one is GWP and the other is reserves. | Mức 3 | Specify metric and year: "group life share of life GWP/reserves in 2024 was X% according to FINMA table Y." |
| 11 | `Insurance penetration` and `insurance density` | `Thẻ 8`, lines 514-540 | The report mixes total-sector and life-sector figures without defining numerator and denominator. | Mức 2 | Define penetration as `GWP/GDP` and density as `GWP/population`; separate total insurance from life insurance. |
| 12 | `AHV/AVS`, `BVG/LPP`, `KVG/LaMal`, `VVG/LCA`, `SST`, `ALM`, `LTC`, `ADLs` | Multiple | Some abbreviations are used before a clean first definition. | Mức 1 | Define each abbreviation at first occurrence and keep one ordering, e.g. "AHV/AVS" or "AVS/AHV", not both. |
| 13 | `mortality liquidity` | `Task1`, around line 160 | Nonstandard phrase and unclear actuarial meaning. | Mức 2 | Replace with a standard concept such as "mortality pooling effect", "cross-subsidy from earlier deaths", or define the phrase explicitly. |
| 14 | Currency terms | `Task3` and `Task4` | Report shifts between CHF market figures and a EUR 400,000 benefit without explaining currency assumptions. | Mức 2 | Add a modeling assumption: benefit is denominated in EUR for valuation only, or convert to CHF using a specified exchange rate/date. |

## 7. Citation and Reference Check

### 7.1 In-text citations missing from References

The following cited or implied sources appear in the body but are missing, incomplete, or not formalized in a clean References section:

- Human Mortality Database (HMD): central data source for period life tables, but not included as a full reference with access date and table type.
- WHO 2024 / WHO data: used for TLE, HALE, and causes of death; the URL appears, but no full reference entry is provided.
- Swiss Federal Statistical Office (FSO): mentioned in the introduction and APVB discussion; current reference list only gives generic homepage or incomplete title.
- Aon Switzerland and Swiss Life BVG Generation Life Tables: mentioned in line 20; source URLs appear, but no precise in-text citations or formal references.
- FINMA 2025: heavily used for GWP, premium volume, profits, reserves, company counts, and intermediaries; current citations often point to Google Search wrappers or a broken page.
- Pitacco (2014): cited for "Pandemic theory" but not listed as a complete reference.
- Martinović et al. (2024): cited in line 112; the PMC article is accessible, but the reference is absent.
- Obsan / Swiss National Health Report 2020: mentioned in the discussion of neonatal and pediatric care, but not properly cited at the sentence level.
- FSIO/BSV and Federal Council sources for AHV 21 and 13th AHV pension: used in policy discussion, but the reference list contains broken or language-mismatched links.
- ASA/SVV 2025: cited for penetration/density and LTC claims; the linked URL tested as a Google Search wrapper and/or 404 for the target path.

### 7.2 References not cited in text

Several URLs appear in the raw reference block but are not clearly cited in the body or are not tied to a specific claim:

- `https://tvbhnt.com/bao-hiem.html`: Vietnamese insurance-history page; not clearly relevant to Swiss longevity or actuarial pricing.
- OECD mortality assumptions PDF: potentially relevant but not used in a visible in-text citation.
- LeNews search result page: search result, not a stable article citation.
- Swiss Re search page and sigma research landing page: too broad; no specific report is cited.
- Swiss Life individual/private customer page: broad commercial page, weak academic source unless tied to a specific product claim.
- EFV/KRB 2024 budget PDF: appears twice, but no clear in-text citation ties it to a fiscal claim.
- AHV-IV PDF `31.e`: appears as a PDF link but is not explicitly cited in the body.
- Statista market forecast: appears in References but no clear in-text citation; may also have paywall/replicability issues.
- BFS GDP page: appears but no visible calculation uses it with GDP year and formula.

### 7.3 Suspicious or unverifiable references

- `https://tvbhnt`: invalid bare URL. Remove.
- FINMA link `https://www.finma.ch/en/news/2025/04/20250408-mm-versicherungsbericht-2024/`: returned 404. Replace with FINMA's 03 September 2025 page for the 2024 insurance market report.
- `https://www.google.com/search?q=...`: not a source. Replace every Google wrapper with the direct original URL.
- FSIO reference at `https://www.bsv.admin.ch/bsv/en/home/social-insurance/ahv/ahv21.html`: returned 404 in this environment. Use the working BSV AHV 21 page or the English occupational-benefits page if it supports the claim.
- Swissinfo `swiss-vote-13th-pension-payment/73255744`: returned 404. Use a working Swissinfo article or BSV/Federal Council source.
- `https://svv.ch/en/mediathek/zahlen-und-fakten`: target tested as 404. Needs manual verification or replacement with a stable Swiss Insurance Association page.
- Some Swiss Life pages returned 403. If retained, add an accessible PDF/product document or cite another source.
- Obsan PDF produced an SSL error in this environment. It may still be valid, but should be manually checked and downloaded before submission.
- `Federal Council, 2026` appears as an in-text citation label for ch.ch pages. This is likely a mislabel; ch.ch should be cited as a Swiss Confederation public-information portal unless a Federal Council document is actually used.

### 7.4 URL/source relevance check

| Source checked | Access result | What the source supports | Relevance issue |
|---|---|---|---|
| WHO country page for Switzerland, `https://data.who.int/countries/756` | Accessible | Supports Switzerland population/health overview, life expectancy, HALE, and causes of death data through 2021. | Report should not describe WHO TLE/HLE values as "up to 2024" unless another dataset is added. |
| FINMA news, `https://www.finma.ch/en/news/2025/09/20250903-meldung-versicherungsmarktbericht/` | Accessible | Supports 2024 aggregate premium growth, life-insurance profit increase to CHF 1.6 billion, and life premium decline. | Current report often cites a broken 2025/04 FINMA URL or Google Search wrapper. |
| FINMA Insurance Market Report 2024 PDF | Accessible | Supports detailed market tables and sector-specific figures. | Exact reserve/liability figures must be checked against the correct table before final submission. |
| BSV AHV 21 page, `https://www.bsv.admin.ch/de/ahv-21` | Accessible | Supports the staged increase in women's reference retirement age: 64y3m in 2025, 64y6m in 2026, 64y9m in 2027, 65 from 2028. | Current English FSIO link is broken; replace with a stable page or archived English source. |
| BSV/OFAS 13th pension page | Accessible in French/German | Supports first 13th AHV pension payment in December 2026. | VAT-rate or financing details require a separate source if discussed. |
| ch.ch second and third pillar pages | Accessible | Supports general definitions of Swiss second and third pillars. | Does not prove all market-share or product-design claims. |
| tvbhnt insurance-history page | Accessible | General Vietnamese insurance-history content. | Not an academic or Swiss-specific source for this report. Remove unless the report has a historical-insurance paragraph. |
| Statista Switzerland life-insurance market forecast | Accessible | Market-forecast page. | Use cautiously; may not be fully reproducible without access and should not replace FINMA for official market statistics. |

### 7.5 Citation placement issues

- Citations are often placed after long paragraphs containing several figures and claims. Move citations next to the specific figure or assertion they support.
- Replace Markdown links embedded inside sentences with formal academic citations plus a complete reference entry.
- Remove citation labels that are not real authors, such as `Federal Council, 2026` if the source is actually ch.ch.
- Do not cite search-result pages. Cite the exact report, article, dataset, or PDF.
- Add source notes under figures and tables, especially charts derived from HMD life tables and WHO/FINMA data.
- Separate "References" from "draft source notes". The current `Task 5` block is not a valid reference section.

## 8. Priority Revision Plan

### Fix immediately

- Delete all Vietnamese drafting instructions, placeholder figure notes, and conversational guidance blocks.
- Rebuild the References section in one style, preferably APA 7 or the format required by the course.
- Replace Google Search links and broken URLs with direct working sources.
- Remove duplicated paragraphs and keep only one final version of each analysis.
- Resolve inconsistent FINMA figures for technical reserves/liabilities, life GWP, SST ratio, company counts, and market shares.
- Correct high-risk terminology: `l_x`, Lexis Point, pandemic theory, Gompertz-Makeham interpretation, and WHO TLE/HLE date range.

### Fix before submission

- Add citations for HMD, DemoLab/Pitacco, actuarial formulae, WHO, FINMA, BSV/FSIO, Obsan/FSO, and any market product claims.
- Rewrite over-generic or promotional paragraphs into data-led analysis.
- Add a short methodology note explaining year selection, HMD table type, sex categories, and whether life expectancy values are curtate or complete.
- Add figure captions with data source and calculation notes.
- Standardize abbreviations and variable names across all sections.

### Polish if time allows

- Tighten the Abstract after body revisions.
- Replace intensifiers such as "monumental", "flawlessly", "undeniable", "absolute", and "sovereign" with neutral academic wording.
- Check grammar, spacing around punctuation, and Markdown heading hierarchy.
- Convert raw URLs into complete reference entries with access dates for datasets/web pages.

## 9. Suggested Rewrites

### Rewrite 1

- Original issue: Introduction line 15 is too long, generic, and contains "(cần dẫn chứng)".
- Revised academic version:

```text
Mortality assumptions are central to the valuation of pension and annuity liabilities because they determine the expected timing and duration of future benefit payments. In long-term life-contingent contracts, systematic improvements in survival create longevity risk: annuitants may live longer than the mortality basis used for pricing and reserving. This report therefore examines historical changes in Swiss period life tables from the Human Mortality Database over 1988-2024, focusing on survivorship, curtate life expectancy, and old-age mortality patterns.
```

- Why this is better: It removes draft notes, reduces generic prose, and links the problem directly to the report's data and method.

### Rewrite 2

- Original issue: Lexis Point and rectangularization discussion overstates "biological limit" and mirrors DemoLab concepts without clear citation.
- Revised academic version:

```text
Following the longevity-marker approach used in the actuarial literature, the analysis compares three indicators: curtate life expectancy at birth, total expected age at 65, and the Lexis Point, defined here as the modal age at death among adult-old ages. In the Swiss HMD tables, the upward movement of the Lexis Point and the narrowing gap between these indicators suggest a stronger concentration of deaths at advanced ages. This pattern is consistent with survival-curve rectangularization, although it should be interpreted as a demographic regularity rather than as evidence of a fixed biological lifespan limit.
```

- Why this is better: It cites the conceptual lineage, keeps the Swiss contribution, and avoids unsupported biological claims.

### Rewrite 3

- Original issue: WHO TLE/HLE paragraph says "up to 2024" while the accessible WHO data support 2000-2021 values.
- Revised academic version:

```text
WHO country data for Switzerland report that life expectancy at birth increased from 79.7 years in 2000 to 83.3 years in 2021, while healthy life expectancy increased from 68.4 to 71.1 years over the same period. The difference between these indicators therefore widened from about 11.3 to 12.2 years. This does not by itself prove a specific morbidity theory, but it is consistent with the concern that additional years of life may include a substantial period lived with functional limitations.
```

- Why this is better: It aligns the time period with the source and replaces "directly validates" with a defensible interpretation.

### Rewrite 4

- Original issue: FINMA market-size paragraph cites a broken/Google URL and uses promotional wording.
- Revised academic version:

```text
FINMA's 2024 insurance market report indicates that aggregate Swiss insurance gross premiums increased by 6.7% to approximately CHF 150 billion in 2024. The life-insurance segment moved differently from the overall market: life premium volume declined by 8.4%, while life insurers' annual profits increased by 22% to CHF 1.6 billion. These figures suggest that the life segment should be evaluated separately from the broader insurance sector, especially when discussing premium volume, profitability, and balance-sheet capacity.
```

- Why this is better: It uses the correct source logic, separates total-sector and life-sector figures, and avoids inflated language.

### Rewrite 5

- Original issue: AHV policy paragraph links demographic findings too strongly to policy design.
- Revised academic version:

```text
The demographic findings provide useful context for recent Swiss pension reforms, but they should be distinguished from the legal rationale of the reforms themselves. Under AHV 21, the reference retirement age for women is being raised in stages: 64 years and 3 months in 2025, 64 years and 6 months in 2026, 64 years and 9 months in 2027, and 65 years from 2028. The approved 13th AHV pension will first be paid in December 2026. These reforms are therefore relevant to the report because they illustrate how longevity and retirement-duration concerns enter Swiss social-insurance policy debates.
```

- Why this is better: It cites policy facts without claiming the report's mortality analysis mathematically proves the reform.

## 10. Final Checklist Before Submission

- [ ] Similarity-sensitive paragraphs revised
- [ ] All borrowed ideas have citations
- [ ] Direct wording is quoted or paraphrased properly
- [ ] AI-like generic paragraphs are made more specific
- [ ] Key terms are defined consistently
- [ ] In-text citations match References
- [ ] URLs and sources are valid
- [ ] Report has consistent academic tone
