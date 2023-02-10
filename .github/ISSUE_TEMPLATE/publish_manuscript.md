---
name: Publish manuscript
about: Use this template for tracking publication of manuscripts.
title: "MSID %%msid% DOI %%doi%%"
labels: 
assignees: 
---

### Step 1. Inform bioRxiv

- [ ] Manuscript is in data hub index (https://data-hub-api.elifesciences.org/enhanced-preprints/docmaps/v1/get-by-doi?preprint_doi=10.1101%2F%%doi%%)

or

- [ ] Confirmed with Ted at bioRxiv that MECA archive is available

Send the following email to Ted and wait for his reply.

```
Hi Ted,

Please can you prepare the preprint MECA for 10.110/%%doi%%%%doi-suffix%%

Thanks
```

### Step 2. Create preview of manuscript

How can help: @nlisgo, @fred-atherden, @scottaubrey

- [ ] Manuscript is available for preview (https://prod--epp.elifesciences.org/preview/10.1101/%%doi%%)

```
git clone git@github.com:elifesciences/enhanced-preprints-data.git
cd enhanced-preprints-data
git checkout -b import-%%doi%% origin/master
./scripts/fetch_meca_archive.sh %%doi%% incoming/
./scripts/extract_mecas.sh mecas/ data/
rm -rf incoming/
git add .
git commit -m 'incoming-%%doi%%'
git push -u origin import-%%doi%%
```

Create PR: https://github.com/elifesciences/enhance/compare/master...import-%%doi%%

Merge in after CI passes and reviewing changes.

Manuscript should be available for preview shortly afterwards.

