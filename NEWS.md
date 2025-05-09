# News for Package <span class="pkg">finbif</span>

# finbif 0.9.10

## MINOR IMPROVEMENTS

   - Improvements have been made to the way errors in parsing json are handled. 

# finbif 0.9.9

## DEFUNCT

  - Importing `.ods` and `.xlsx` occurrence data files is now defunct. Users
    should use `.tsv` download files only.

## MINOR IMPROVEMENTS

  - Occurrence download progress indicator has been simplified.
  - Location data parsing (country, region, municipality and local area) has
    been improved.

# finbif 0.9.8

## DEPRECATION

  - Importing `.ods` and `.xlsx` occurrence data files has been
    deprecated and will be defunct in a future release.

## MINOR IMPROVEMENTS

  - Caching behaviour has been made more consistent.

# finbif 0.9.7

## NEW FEATURES

  - Record pagination has been simplified and improved so that it should
    not be possible to have duplicate records when using
    `finbif_occurrence`.

## MINOR IMPROVEMENTS

  - `finbif_last_mod` can be used without a `filter` argument value.

  - Error handling for API requests has been improved.

## BUG FIXES

  - Fixed an issue triggered when multi-filter set requests returned
    zero results.

  - Fixed bug triggered when dropping columns of all NA data.

  - Fixed an issue with file-based caches timing out correctly.

  - Fixed an issue triggered when selecting certain variables and zero
    records were returned.

# finbif 0.9.6

## MINOR IMPROVEMENTS

  - New undocumented variable and filter `local` added from upstream
    API.

## BUG FIXES

  - Fixed an issue that caused more records than requested to be
    returned for certain values of `n`.

# finbif 0.9.5

## MINOR IMPROVEMENTS

  - A more informative error message is given when requesting an access
    token for an email address that has already been assigned one.

## BUG FIXES

  - Fixed an issue with reading facts for FinBIF record download files.

  - Fixed an issue with reading column names using `data.table` package
    to ingest FinBIF record download files.

# finbif 0.9.4

## NEW FEATURES

  - New undocumented variable "source" can be selected with
    `finbif_occurrence`.

## MINOR IMPROVEMENTS

  - Record pagination should now often require less queries of FinBIF
    server and be should be faster.

  - FinBIF collections field names have been sanitised.

  - When filtering records by "collection\_id" a full URL ID can be used
    or a QName.

## BUG FIXES

  - Reading zero observation data downloads will now produce a zero row
    `data.frame` instead of triggering an error.

# finbif 0.9.3

## BUG FIXES

  - Fix a bug resulting in the incorrect region being assigned to
    occurrences records.

## MINOR IMPROVEMENTS

  - New undocumented variables `institution_code` and `collection_code`
    can be selected when using functions `finbif_collections` and
    `finbif_occurrence`.

# finbif 0.9.2

## BUG FIXES

  - Fixed a bug triggered when localising some variables and multiple
    pages of data had been requested.

# finbif 0.9.1

## NEW FEATURES

  - New option `finbif_use_cache_metadata` to set caching for metadata
    only. Is ignored if `finbif_use_cache` is `TRUE`.

## BUG FIXES

  - Fixed a bug triggered when trying to compute a variable from an
    identifier and data returned contained zero records.

# finbif 0.9.0

## NEW FEATURES

  - New function `finbif_update_cache` can be used to update all the
    cached objects that have reached their expiration and are no longer
    valid.

  - A restricted data API token can be explicitly declared via the
    `restricted_api` argument to `finbif_occurrence`.

  - Cached data can use a database as a backend by passing a `DBI`
    database connection object to the package option
    `finbif_cache_path`.

  - Cached data can be assigned a timeout by using a number (hours)
    instead of a logical value for the `cache` argument to `finbif_`
    functions or the package option `finbif_use_cache`.

  - Record aggregations with `finbif_occurrence` can now be combined
    with multi-filter requests. Removing duplicate records or aggregate
    record combinations can be controlled with the `duplicates` argument
    and adding a column indicating the filter sets can be added with the
    `filter_col` argument.

##### BUG FIXES

  - Fixed a bug causing an infinite recursion when determining page size
    during record download pagination.

  - Fix bug triggered when using aggregation with some selected
    variables.

## DEFUNCT

  - Mapping utilities `finland_map`, `breaks_xy`, `hist_xy` and the plot
    method for `finbif_occ` objects are now defunct.

  - User access to `finbif_records` and its classes and methods is now
    defunct.

# finbif 0.8.0

## DEPRECATION

  - Mapping utilities `finland_map`, `breaks_xy`, `hist_xy` and the plot
    method for `finbif_occ` objects have been deprecated as they are
    out-of-scope.

  - User access to `finbif_records` and its classes and methods is
    deprecated in favour of `finbif_occurrence`.

## NEW FEATURES

  - Record aggregations with `finbif_occurrence` can now include
    "individual" and "pair" sums.

# finbif 0.7.2

## MINOR IMPROVEMENTS

  - Updated deprecated use of tidy::pivot\_wider.

  - Added new filters and variables from upstream API.

# finbif 0.7.1

## NEW FEATURES

  - New function `finbif_mod_date` to get last modified date for FinBIF
    occurrence data.

  - Region is now a selectable variable for `finbif_occurrence` and can
    also be used to filter records.

## MINOR IMPROVEMENTS

  - For the sake of clarity "province" is now referred to as
    "bio-province".

  - Many variables, including `sex`, `life_stage` and `record_quality`
    are now localised.

  - The variable `restriction_reasons` is now referred to in the
    singular as `restriction_reason`.

  - For consistency, `lang` argument to `finbif_collections` has been
    changed to `locale`.

## BUG FIXES

  - Fixed bug that caused locale to be set incorrectly for multipage
    requests.

# finbif 0.7.0

## NEW FEATURES

  - New function `taxon_id` that returns FinBIF taxon identifiers given
    a scientific name, vernacular name or other taxon identifier.

  - New filters `complete_list_taxon_id` and `complete_list_type` now
    available.

  - New global option `finbif_hide_progress` to suppress progress bars
    when downloading, importing or processing FinBIF records.

  - For the sake of clarity and consistency the term "administrative
    status" is now referred to as "regulatory status" throughout.

  - Regulatory status, informal taxonomic group and habitat data are now
    localised.

  - Option `unlist` added to `finbif_occurrence` that casts list columns
    to strings. If a cell has multiple values the values are cast to a
    string separated by semi-colons.

  - New argument `facts` added to `finbif_occurrence` that can be used
    to automatically extract facts when downloading occurrence records.

## BUG FIXES

  - Fixed bug triggered by incorrect data type applied to
    `taxonomic_order`.

  - Fixed bug preventing locale switching of vernacular name data.

# finbif 0.6.6

## NEW FEATURES

  - New option to exclude all records with any NA values for any of the
    selected variables added to `finbif_occurrence`.

## MINOR IMPROVEMENTS

  - The warning/error message returned when an invalid taxon is
    requested with `finbif_occurrence` has been made more detailed,
    warning the user they may be using synonyms or other invalid taxon
    names.

## BUG FIXES

  - Fix applied for a print method error triggered by clashing class
    names.

  - Fixed issue with ordering by some variables.

# finbif 0.6.5

## NEW FEATURES

  - New variables and filters (currently undocumented) have been added
    for the forthcoming Finnish atlas of breeding birds.

  - Skip rows argument added to `finbif_occurrence_load` so files can be
    read in chunks.

## MINOR IMPROVEMENTS

  - For clarity, KKJ coordinate reference system is now referred to as
    YKJ.

  - When selecting all available variables for download file imports
    using `finbif_occurrence_load` "extra" variables will no longer be
    automatically added.

# finbif 0.6.4

## MINOR IMPROVEMENTS

  - New administrative statuses added.

  - The number of (and interval between) api request retries can be
    configured (currently undocumented).

  - For some museum collections scientific names have been added for
    non-Finnish species.

  - New fields have been added to citable download imports.

  - New argument `aggregate_counts` (defaulting to `TRUE`) added to
    `finbif_occurrence` to toggle the inclusion of aggregation count
    fields on and off.

  - New bird association area, occurrence types and location tag
    metadata added.

  - New filters and variables (currently undocumented) added from
    upstream API.

## BUG FIXES

  - Fix bug triggered when printing occurrence records where all records
    have no coordinate uncertainty.

# finbif 0.6.3

## MINOR IMPROVEMENTS

  - Argument `drop_na_facts` has been changed to `drop_facts_na` for
    function `finbif_occurrence_load` to avoid problems due to partial
    matching of argument `drop_na`.

  - Data quality description has been appended to description field in
    `data.frame` returned by `finbif_collections()`.

  - Occurrence record filtering can now be done using open-ended date
    ranges.

  - New administrative statuses added.

## BUG FIXES

  - Fix bug in importing of file downloads triggered by string quotation
    errors.

# finbif 0.6.2

## NEW FEATURES

  - New package option, `finbif_allow_query`, with default value,
    `TRUE`. If set to `FALSE` then remote API queries will trigger an
    error meaning only cached requests will run if a cache is found.

  - Records can now be aggregated by document.

## MINOR IMPROVEMENTS

  - A client-side error will be triggered if an attempt is made to
    filter by taxon and aggregate data by event with
    `finbif_occurrence`.

## BUG FIXES

  - Fix bug preventing loading of FinBIF archives that is triggered when
    all variables are selected with `select = "all"`.

  - Fix bug preventing `finbif_occ` objects from printing when one or
    more columns contain missing data only.

# finbif 0.6.1

## BUG FIXES

  - Fixed a regression in the last release that prevented collection
    names being converted from their URIs.

# finbif 0.6.0

## NEW FEATURES

  - New variables `lat_euref` and `lon_euref` available for occurrence
    record downloads. These new variables represent the central point of
    a bounding box encompassing a record's geographic coverage in the
    EUREF (ETRS89/ETRS-TM35FIN) coordinate system.

  - Option now available to retain the TSV data file when loading FinBIF
    occurrence data with `finbif_occurrence_load` from ZIP archive or
    online reference.

  - Option now available to extract "facts" when using
    `finbif_occurrence_load` to import records from a ZIP archive. The
    user must supply a named list, where the names refer to one or more
    fact types: "record", "event" and/or "document", and the list
    elements are character vectors indicating which "facts" to extract.

  - "Lite" download files (occurrence record datasets of less than
    10,000 records downloaded directly from laji.fi) can now be imported
    using `finbif_occurrence_load`.

  - New filters (currently undocumented) `ely_center_id` and `region_id`
    are available for `finbif_occurrence`.

  - New function, `from_schema`, to convert variable names from FinBIF
    schema to other styles.

  - New computed variable `date_time_ISO8601` (currently undocumented)
    can be selected when creating `finbif_occ` objects.

  - New computed variable `epsg` (currently undocumented). If selected,
    the column will have the EPSG code of the first column that contains
    geographic data.

## MINOR IMPROVEMENTS

  - Can now select all available variables when importing a FinBIF
    download request file using `finbif_occurrence_load` with `select =
    "all"`.

  - New option, `drop_na`, to drop columns that only contain missing
    data added to `finbif_occurrence` and `finbif_occurrence_load`.

  - User can now select columns multiple times and rename them on the
    fly by using a named character vector as the value of the 'select'
    argument.

  - The variable `taxon_rank` is now converted to a string on the fly
    via `taxon_rank_id`.

  - Variables that are computed from their identifiers are now localised
    when multiple languages are available.

## BUG FIXES

  - Fixed bug that prevented occurrence record counting when caching was
    not in use.

  - Fixed bug that triggered an error when selected a variable that had
    to be computed from its ID when using DWC style variable names.

# finbif 0.5.0

## NEW FEATURES

  - Getting records from FinBIF can now be speed up (\~1.5x) with
    asynchronous processing. If the `future` package is available and an
    asynchronous strategy (e.g., `plan(multisession, workers = 2)`) is
    selected then downloading records and processing them will occur
    simultaneously in separate threads, often leading to a significant
    speed up over sequential processing.

  - Occurrence records can now be requested using multiple sets of
    filters at the same time. If a list of filters (with unnamed
    elements) is supplied then a record request will be made for each
    set of filters and the results of all requests combined and all
    duplicate records removed.

  - Occurrence records can now be read directly from FinBIF download
    request files. The function `finbif_occurrence_load` can load data
    from a local file or remotely using a persistent identifier URI
    (e.g., `http://tun.fi/HBF.49381`).

  - Aggregation of records can now be performed at the recording "event"
    level as well as the "record" level.

# finbif 0.4.1

## NEW FEATURES

  - New functions `scientific_name` and `common_name` are now available
    to get scientific and common names for taxa (given a taxon name or
    FinBIF ID code) or extract names from a `finbif_taxa`- class object.

  - Add ability to extract complex record variables such as those
    associated with record media (currently undocumented).

## MINOR IMPROVEMENTS

  - Collection name can be selected as a variable for occurrence
    records. Previously it had to be manually translated from collection
    ID.

  - Variables `restriction_reasons_conservation`,
    `restriction_reason_embargo` and `restriction_reason_custom` are no
    longer in use upstream and can no longer be selected.

# finbif 0.4.0

## NEW FEATURES

  - Occurrence record requests can now be made with aggregation,
    `aggregate = c("records", "species", "taxa")`. This returns the
    number of records, and/or species or taxa for each combination of
    the selected variables instead of the occurrence records themselves.

## MINOR IMPROVEMENTS

  - Error is triggered when attempting to request less than one record.

  - New content on requesting aggregated occurrence records added to
    vignette: 2. Occurrence records from FinBIF.

## BUG FIXES

  - Fixed two bugs in print method for FinBIF occurrence records that
    were triggered when attempting to print only one row of data.

  - Fixed bug triggering error when attempting to print occurrence
    record objects with zero rows.

  - Fixed bug triggered when trying to print occurrence record data with
    NA values.

  - Fixed bug causing incorrect subsetting of occurrence records when
    using logical vectors to subset rows.

  - Fixed bug that printed occurrence records with multi-element data
    incorrectly when there was a single element.

  - Fixed bug triggered by some system locales (\#1).

# finbif 0.3.1

## NEW FEATURES

  - Occurrence records can be ordered by the total number of records or
    total number of Finnish records of the taxon (variables:
    `n_total_records` & `n_total_finnish_records`, currently
    undocumented).

  - New Finnish occurrence status, `records_only`, added.

  - New administrative statuses added to filters.

## MINOR IMPROVEMENTS

  - Filtering vignette updated to reflect changes to data quality
    filters.

# finbif 0.3.0

## NEW FEATURES

  - All user facing functions with a `finbif_` prefix can now also be
    used with the alternative shorter prefix `fb_`.

  - Crop Wild Relative, CWR, added to admin statuses.

  - There are two new utility functions, `to_dwc` and `to_native` for
    converting variable names to and from Darwin Core style.

  - Users can select and order by variables in Darwin Core style when
    using `finbif_occurrence`.

  - Some changes in variables and filters have flowed from upstream
    changes to "api.laji.fi". The variables `is_unidentifiable`,
    `record_reliable`, `collection_reliability`, `taxon_reliability`,
    `taxon_reliability_message` and `taxon_reliability_source` have been
    deprecated and replaced with `requires_verification`,
    `requires_identification`, `record_reliability` and
    `record_quality`. The filters `collection_reliability` and
    `taxon_reliability` have been deprecated and replaced with
    `requires_verification`, `collection_quality`, `record_reliability`,
    `record_quality`, and `expert_verified`.

  - Vernacular names are now localised. Users can select a language to
    use for taxon vernacular names. Missing names will fallback
    gracefully to other languages. A package-wide locale can be set and
    is by default set to the system locale (if not set or can't be
    determined it will default to English).

  - New vignettes on getting occurrence records, selecting and ordering
    variables, metadata and plotting have been added.

## MINOR IMPROVEMENTS

  - Caching defaults to in memory caching instead of relying on the
    temporary directory.

  - Front matter of vignettes is now visible when using the R help
    browser.

  - Retired "quiet" option for `on_check_fail` argument in function
    `finbif_occurrence()`.

  - Improved error messages when taxa fail checking in
    `finbif_occurrence()`.

  - Global option to set timezone, `finbif_tz`, as default value for
    "tzone" argument to `finbif_occurrence()`. Avoids having to set
    system environment variable TZ or specify "tzone" every time
    `finbif_occurrence()` is run.

  - Now when a record has no time information the start time is assumed
    to be midday. Previous behaviour was to assume start time was
    midnight, making errors potentially biased.

  - Package options are now documented in the package level man page.

  - News file is now accessible via R internal help system.

  - The number of default variables selected when accessing occurrence
    records has been reduced to speed up downloads and improve the
    display of `finbif_occ` objects.

  - The print method for occurrence record objects has been updated. It
    is now aware of console width and when truncating variable values is
    more considerate of the context.

  - Variables can now be "deselected" when using the `select` argument
    to `finbif_occurrence` by prepending the variable name with a "`-`".

  - After some failures, API requests are now automatically retried up
    to three times.

## BUG FIXES

  - Ordering by descending variables did not work when ordering by both
    ascending and descending variables.

  - Fixed bug in handling of duplicates that could result in an infinite
    recursion.

  - Fixed bug that (when `on_check_fail = "warn"`) all taxa failed
    checks `finbif_occurrence()` would proceed as if no taxa had been
    selected.

  - Fixed bug in print method for `finbif_occ` objects that caused error
    when trying to display a single column objects with a list-col only.

# finbif 0.2.0

## NEW FEATURES

  - Add capacity to request a random sample of FinBIF records.

## MINOR IMPROVEMENTS

  - Add more content to vignettes.

# finbif 0.1.0

  - Initial release.
