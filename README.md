# Readme

1. `wget -r -l inf --no-remove-listing --page-requisites --no-verbose -o debug.log --convert-links --adjust-extension -e robots=off https://challenge.open-contracting.org`
1. Remove all references to `wp-json`:

    1. `rm -rf wp-json en/wp-json`
    1. Replace each of these with nothing:

            <link rel="alternate" type="(application/json|text/xml)\+oembed" href="\S+" />\n
            <meta name="msapplication-TileImage" content="\S+" />\n
            <script type="text/javascript">window.wp_data = {\S+};</script><link rel="icon" href="\S+" sizes="32x32" />\n
            <link rel="https://api.w.org/" href="\S+" />(<link rel="alternate" type="application/json" href="\S+" />)?<link rel="canonical" href="\S+" />\n

1. Fix broken URLs:

    1. Remove alternative language URLs with broken links, by replacing this with nothing:

        <link rel="alternate" hreflang="(en|ru)" href="\S+" title="\S+" />\n

    1. Replace Russian-to-English language switch URLs with homepage links, by replacing this with `$1$2en.html"`:

        (<a href="(?:((?:\.\./)*)index.html)%3Fp=148.html">Международный опыт</a>\n</div>\n                            <div class="dropdown">\n                    <div class="selected">Русский</div>\n                    <div class="dropdown-drop text-center">\n                                                    <a href=")https://challenge.open-contracting.org/\S+"

    1. Replace English-to-Russian language switch URLs with homepage links, by replacing this with `$1../$2"`:

        (<a href="((\.\./)*index.html)%3Fp=241.html">Best Practices</a>\n</div>\n                            <div class="dropdown">\n                    <div class="selected">English</div>\n                    <div class="dropdown-drop text-center">\n                                                    <a href=")https://challenge.open-contracting.org/\S+"

1. Check `debug.log` for errors.
1. Check for occurrences of `challenge.open-contracting.org`.
