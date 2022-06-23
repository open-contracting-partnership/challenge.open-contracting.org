# Readme

1. `wget -r -l inf --no-remove-listing --page-requisites --no-verbose -o debug.log --convert-links --adjust-extension -e robots=off https://challenge.open-contracting.org`
1. Remove all references to `wp-json`:

    1. `rm -rf wp-json en/wp-json`
    1. Replace each of these with nothing:

            <link rel="alternate" type="(application/json|text/xml)\+oembed" href="\S+" />\n
            <meta name="msapplication-TileImage" content="\S+" />\n
            <script type="text/javascript">window.wp_data = {\S+};</script><link rel="icon" href="\S+" sizes="32x32" />\n
            <link rel="https://api.w.org/" href="\S+" />(<link rel="alternate" type="application/json" href="\S+" />)?<link rel="canonical" href="\S+" />\n

1. Remove alternative URLs with broken links, by replacing each of these with nothing:

        <link rel="alternate" hreflang="(en|ru)" href="\S+" title="\S+" />\n

1. Check `debug.log` for errors.
1. Check for occurrences of `challenge.open-contracting.org`, ignoring errors, e.g. `challenge.open-contracting.org(?!/(en/)?(blog/)?(team/|wp-content/themes/hackathon/assets/fonts/icomoon))`
