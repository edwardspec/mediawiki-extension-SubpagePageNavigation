Archived: this functionality was moved into https://github.com/edwardspec/mediawiki-extension-PrevNextImageLinks (which has a better implementation).


mediawiki-extension-SubpageAnchorNavigation
====================

Extension:SubpageAnchorNavigation adds `{{#subpage_anchor_navigation:}}` syntax,
which finds all subpages of the current page,
then finds all HTML anchors like `<span id="pg123">` on these subpages,
then generates a navigation template that contains links to all these anchors.

For example, if current page is A and it has 3 subpages:
* `A/B` with "pg1", "pg2", "pg3"
* `A/C` with "pg7", "pg8", "pg9"
* `A/D` with "pg4", "pg5", "pg6"

... then using `{{#subpage_anchor_navigation:}}` on the page `A` will create 9 links,
from pg1 to pg9, ordered by page number (in the example above, `A/D` before `A/C`).

# Installation

After installing this extension, run the following maintenance script in MediaWiki directory:
```bash
php maintenance/runScript.php extensions/SubpageAnchorNavigation/maintenance/recalculateAnchors.php
```

This script will populate the cache of "which pages have which anchors" for existing pages.

You don't need to rerun this script later (if more anchors are added to pages),
because the cache is automatically updated when the pages with anchors are modified.
