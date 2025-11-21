# Overview of PSDI metadata

- Date: 2024-10-14
- Modified Date: 2024-10-14
- Content custodian: Aileen Day (University of Southampton)
- Authors: Aileen Day (University of Southampton), Bryan Gillis (University of Southampton)

## Summary

This project hosts PSDI metadata, published online via GitHub Pages. Everything in this project is made publicly-available relative to the URL https://psdi-uk.github.io/metadata/.

Please see:

- [index.html](./index.html) for human-readable description of what is available in this repository via https://psdi-uk.github.io/metadata/
- [PSDI metadata guidance in the PSDI knowledgebase](https://psdi-uk.github.io/docusaurus-pages/docs/category/psdi-metadata) for guidance about it.

This project also hosts XML sitemaps for PSDI projects which do not otherwise provide their own, as well as the human-readable HTML sitemap made available at https://psdi-uk.github.io/metadata/sitemap/psdi-sitemap.html.

## Dependencies

The public website deployed by this project depends on the assets made public by PSDI's common style project at https://github.com/PSDI-UK/psdi-common-style. Any changes to these assets will be reflected in this project's website, and this project should ideally be tested with any changes before they're made live. An issue with retrieving these assets will appear as the website appear unstyled and missing its header and footer.

In case these assets become no longer available for some reason, the commit `517e74b99fba4920c4eea4b17131fdd42eb93f72` can be used as a reference to restore local versions of them.

## Workflows

To keep the sitemaps hosted in this project up-to-date, a workflow is regularly run to pull updates from the [metadata-processing project](https://github.com/PSDI-UK/metadata-processing). Please refer to that project's README.md for details on how it updates the sitemap. Here we will discuss how the updates are pulled to this project.

The workflow `ci-pull-sitemap-updates.yml` is triggered on a schedule to pull updates from the metadata-processing project.

**Important:** This uses a personal token to provide access to that project, which needs to be refreshed every year - see the documentation at the top of the workflow file for details on how to do this.

Once the project is checked out, the latest versions of the sitemaps are copied over to this project. The workflow then checks if there are any changes to these sitemaps (aside from the timestamp on the HTML sitemap). If there are, it opens a pull request with these changes for manual review.

When this pull request is opened, it requires human review to check that the changes appear to be desired. Sometimes a site may be down when it's crawled to generate a sitemap, resulting in its pages being missing from the resulting sitemap. There may also be other structural changes to a site which result in issues, such as pages being orphaned and not linked to from the root page (note that the crawler can only standard hyperlinks found in the HTML of a page when it's first loaded - page transitions via JavaScript and links added via script after the initial load will not be crawled).

If there are any issues with the changes to the sitemap, the pull request should be closed and the branch created for it deleted. The reviewer should then take appropriate steps to address the issue. If it was a simple issue of downtime, for instance, this can be handled by manually re-running the workflow to generate the sitemaps in the metadata-processing project, `ci-update-sitemaps.yml`, and then afterwards manually re-running the workflow here to pull those updates.

Other issues may require different solutions. If structural changes to a site result in pages which do exist not being found, consult with the team in charge of the site and decide on the best course of action. Perhaps the missing pages do not need to be included in the sitemap, so the changes can go ahead. Perhaps the site should be changed so the links are directly available. Perhaps the site should be left as-is, but the page still needs to be included in the sitemap - in this case, it can be added to the sources for the `make-all-sitemaps` script in the metadata-processing repo to ensure it's found, and then the `ci-update-sitemaps.yml` workflow there re-run, and `ci-pull-sitemap-updates.yml` here.

Alternatively, it may be the case that pages are being found by the crawler which you don't wish to include in the sitemap. For these, appropriate patterns can be added to the exclusion source configuration for the `make-all-sitemaps` script in the metadata-processing repo - see the documentation in that project for how to do this. And then of course, re-run the workflow there to generate new sitemaps and the workflow here to pull them.

Once the pull request opened here contains only desired changes, it can be accepted, and the branch created for it deleted. Doing this will result in the updated contents of this repository being automatically deployed, and the updated sitemaps should be live within a few minutes.
