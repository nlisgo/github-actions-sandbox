---
name: Publish manuscript
about: Use this template for tracking publication of manuscripts.
title: "MSID %%msid%% DOI %%doi-suffix%%"
labels: 
assignees: 
---

### Step 1. Inform bioRxiv

Who can help: @QueenKraken, @nlisgo, @scottaubrey

- [ ] Manuscript is in data hub index (https://data-hub-api.elifesciences.org/enhanced-preprints/docmaps/v1/get-by-doi?preprint_doi=%%doi-prefix%%%2F%%doi-suffix%%)

or

- [ ] Confirmed with Ted at bioRxiv that MECA archive is available

Send the following email to Ted and wait for his reply.

```
Hi Ted,

Please can you prepare the preprint MECA for %%doi-prefix%%/%%doi-suffix%%%%doi-suffix2%%

Thanks
```

### Step 2. Create preview of manuscript

Who can help: @fred-atherden, @nlisgo, @scottaubrey

- [ ] Manuscript is available for preview (https://prod--epp.elifesciences.org/preview/%%doi-prefix%%/%%doi-suffix%%)

```
git clone git@github.com:elifesciences/enhanced-preprints-data.git
cd enhanced-preprints-data
git checkout -b import-%%doi-suffix%% origin/master
./scripts/fetch_meca_archive.sh %%doi-suffix%% incoming/
./scripts/extract_mecas.sh mecas/ data/
rm -rf incoming/
git add .
git commit -m 'incoming-%%doi-suffix%%'
git push -u origin import-%%doi-suffix%%
```

Create pull request: https://github.com/elifesciences/enhance/compare/master...import-%%doi-suffix%%

Merge in after CI passes and reviewing changes.

Manuscript should be available for preview shortly afterwards.
