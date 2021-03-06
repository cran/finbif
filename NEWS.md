# finbif 0.5.0

#### NEW FEATURES

-   Getting records from FinBIF can now be speed up (\~1.5x) with
    asynchronous processing. If the `future` package is available and an
    asynchronous strategy (e.g., `plan(multisession, workers = 2)`) is
    selected then downloading records and processing them will occur
    simultaneously in separate threads, often leading to a significant
    speed up over sequential processing.

-   Occurrence records can now be requested using multiple sets of
    filters at the same time. If a list of filters (with unnamed
    elements) is supplied then a record request will be made for each
    set of filters and the results of all requests combined and all
    duplicate records removed.

-   Occurrence records can now be read directly from FinBIF download
    request files. The function `finbif_occurrence_load` can load data
    from a local file or remotely using a persistent identifier URI
    (e.g., `http://tun.fi/HBF.49381`).

-   Aggregation of records can now be performed at the recording "event"
    level as well as the "record"" level.

# finbif 0.4.1

#### NEW FEATURES

-   New functions `scientific_name` and `common_name` are now available
    to get scientific and common names for taxa (given a taxon name or
    FinBIF ID code) or extract names from a `finbif_taxa`- class object.

-   Add ability to extract complex record variables such as those
    associated with record media (currently undocumented).

#### MINOR IMPROVEMENTS

-   Collection name can be selected as a variable for occurrence
    records. Previously it had to be manually translated from collection
    ID.

-   Variables `restriction_reasons_conservation`,
    `restriction_reason_embargo` and `restriction_reason_custom` are no
    longer in use upstream and can no longer be selected.

# finbif 0.4.0

#### NEW FEATURES

-   Occurrence record requests can now be made with aggregation,
    `aggregate = c("records", "species", "taxa")`. This returns the
    number of records, and/or species or taxa for each combination of
    the selected variables instead of the occurrence records themselves.

#### MINOR IMPROVEMENTS

-   Error is triggered when attempting to request less than one record.

-   New content on requesting aggregated occurrence records added to
    vignette: 2. Occurrence records from FinBIF.

#### BUG FIXES

-   Fixed two bugs in print method for FinBIF occurrence records that
    were triggered when attempting to print only one row of data.

-   Fixed bug triggering error when attempting to print occurrence
    record objects with zero rows.

-   Fixed bug triggered when trying to print occurrence record data with
    NA values.

-   Fixed bug causing incorrect subsetting of occurrence records when
    using logical vectors to subset rows.

-   Fixed bug that printed occurrence records with multi-element data
    incorrectly when there was a single element.

-   Fixed bug triggered by some system locales (\#1).

# finbif 0.3.1

#### NEW FEATURES

-   Occurrence records can be ordered by the total number of records or
    total number of Finnish records of the taxon (variables:
    `n_total_records` & `n_total_finnish_records`, currently
    undocumented).

-   New Finnish occurrence status, `records_only`, added.

-   New administrative statuses added to filters.

#### MINOR IMPROVEMENTS

-   Filtering vignette updated to reflect changes to data quality
    filters.

# finbif 0.3.0

#### NEW FEATURES

-   All user facing functions with a `finbif_` prefix can now also be
    used with the alternative shorter prefix `fb_`.

-   Crop Wild Relative, CWR, added to admin statuses.

-   There are two new utility functions, `to_dwc` and `to_native` for
    converting variable names to and from Darwin Core style.

-   Users can select and order by variables in Darwin Core style when
    using `finbif_occurrence`.

-   Some changes in variables and filters have flowed from upstream
    changes to "api.laji.fi". The variables `is_unidentifiable`,
    `record_reliable`, `collection_reliability`, `taxon_reliability`,
    `taxon_reliability_message` and `taxon_reliability_source` have been
    deprecated and replaced with `requires_verification`,
    `requires_identification`, `record_reliability` and
    `record_quality`. The filters `collection_reliability` and
    `taxon_reliability` have been deprecated and replaced with
    `requires_verification`, `collection_quality`, `record_reliability`,
    `record_quality`, and `expert_verified`.

-   Vernacular names are now localised. Users can select a language to
    use for taxon vernacular names. Missing names will fallback
    gracefully to other languages. A package-wide locale can be set and
    is by default set to the system locale (if not set or can't be
    determined it will default to English).

-   New vignettes on getting occurrence records, selecting and ordering
    variables, metadata and plotting have been added.

#### MINOR IMPROVEMENTS

-   Caching defaults to in memory caching instead of relying on the
    temporary directory.

-   Front matter of vignettes is now visible when using the R help
    browser.

-   Retired "quiet" option for "on\_check\_fail" argument in function
    `finbif_occurrence()`.

-   Improved error messages when taxa fail checking in
    `finbif_occurrence()`.

-   Global option to set timezone, "finbif\_tz", as default value for
    "tzone" argument to `finbif_occurrence()`. Avoids having to set
    system environment variable TZ or specify "tzone" every time
    `finbif_occurrence()` is run.

-   Now when a record has no time information the start time is assumed
    to be midday. Previous behaviour was to assume start time was
    midnight, making errors potentially biased.

-   Package options are now documented in the package level man page.

-   News file is now accessible via R internal help system.

-   The number of default variables selected when accessing occurrence
    records has been reduced to speed up downloads and improve the
    display of `finbif_occ` objects.

-   The print method for occurrence record objects has been updated. It
    is now aware of console width and when truncating variable values is
    more considerate of the context.

-   Variables can now be "deselected" when using the `select` argument
    to `finbif_occurrence` by prepending the variable name with a "`-`".

-   After some failures, API requests are now automatically retried up
    to three times.

#### BUG FIXES

-   Ordering by descending variables did not work when ordering by both
    ascending and descending variables.

-   Fixed bug in handling of duplicates that could result in an infinite
    recursion.

-   Fixed bug that (when "on\_check\_fail" = "warn") all taxa failed
    checks 'finbif\_occurrence()' would proceed as if no taxa had been
    selected.

-   Fixed bug in print method for `finbif_occ` objects that caused error
    when trying to display a single column objects with a list-col only.

# finbif 0.2.0

#### NEW FEATURES

-   Add capacity to request a random sample of FinBIF records.

#### MINOR IMPROVEMENTS

-   Add more content to vignettes.

# finbif 0.1.0

-   Initial release.
