# pedoman

A Claude skill that checks a document against the writing guideline it will be
graded against, and says exactly which clause it breaks.

Students rarely fail a tugas akhir on ideas. They get sent back because the cover is
the wrong colour, the left margin is 3 cm instead of 4, a bullet appears where the
pedoman forbids bullets, or a required subsection is missing by name. That is a
solved problem and it should not cost anyone a week.

## What it does

- **Audit** — you have a draft; it reports violations ranked by severity, each with
  its clause number, and never rewrites your prose.
- **Setup** — you are about to start typing; it gives the typography block and the
  section skeleton.
- **Lookup** — one question, one answer, one clause.

It also checks eligibility first, because formatting a document you cannot yet
submit is wasted work.

## Scope, in order of confidence

1. **Universitas Atma Jaya Makassar, Fakultas Teknologi Informasi** — encoded clause
   by clause from the primary guidelines for KKP/magang, usulan tugas akhir,
   Ringkasan Kapasitas Diri, skripsi, and the journal manuscript.
2. **Encoded from primary guidelines (status 25 September 2026):** UAJY Informatika,
   Atma Jaya Jakarta FEB, ITB, UI, IPB, UGM (Fak. Pertanian pascasarjana), UB
   (Pascasarjana Multidisiplin), ITS, Unair, Unhas (pascasarjana), UNS, Unpad (tesis),
   Undip (three master's programmes), and from wave 1 (25 Sept 2026): Unhas S1, UNM, UMI
   (FIKOM), UIN Alauddin, Unismuh (FKIP), PNUP (D-4), UGM (FIB), BINUS (Management) —
   22 Indonesian institutions including UAJM, most
   at one faculty or level only, as each file states. Five foreign institutions in
   `references/global-institutions.md`.
3. **Every other university** — not encoded. The skill gives the common axes, asks for
   the local pedoman, and follows it. It does not claim coverage it does not have.
4. Citation styles worldwide — APA, MLA, Chicago, IEEE, Vancouver, Harvard, and thesis norms.
5. Any language — formal register, writing direction, name and transliteration rules.

## Sources

`references/uajm-fti.md` was written from two primary documents, read in full:

- *Pedoman Kuliah Kerja Profesi*, Program Studi Informatika, FTI UAJM,
  18 January 2015.
- *Pedoman Penulisan Skripsi*, Program Studi Informatika, FTI UAJM,
  1 April 2015, revised 10 June 2015.

**The PDFs are not in this repository.** They belong to the university. Every rule
here carries its clause number so it can be checked against the original, which is
what citing a guideline means. Put your own copies in `sources/` if you want them
locally; that directory is ignored by git.

## Examples and tests

- [`examples/audit-kkp-contoh.md`](examples/audit-kkp-contoh.md) — a fictional KKP
  draft with deliberate violations, and the full audit of it, clause by clause.
- [`tests/cases.md`](tests/cases.md) — ten questions with expected answers and
  clause numbers: lookups, eligibility gates, the proposal vs Ringkasan Kapasitas
  Diri trap, an unknown campus, a foreign thesis, an Arabic document, and a
  plagiarism-score request the skill must refuse.

## Hard rules the skill follows

- Your own pedoman outranks everything in these files.
- Guidelines drift. The edition being applied is stated once per conversation.
- Never invent a rule. If the guideline is silent, it says so, then marks any
  suggestion as a suggestion.
- Never promise a plagiarism or AI-detector score.

## Related

- [`lugas`](https://github.com/bryankwandou/lugas) — prose quality. This skill does
  format only; the two do not overlap.
