# ADMX Template for LibreOffice
Windows Group Policy Template for [LibreOffice powered by CIB](https://libreoffice.cib.de/) (also usable with [LibreOffice](https://www.libreoffice.org/)).

### Attention
When you add a "policy" in the admx file, add the corresponding "presentation" in all adml files (not just in your language).
Otherwise, this causes the following error for users of these adml files:

    Resource "$(string.something)" referenced in attribute displayName could not be found. 
    File Path\to\something.admx, line xxx, column xxx

## Localization
[ITS Tool](http://itstool.org) is used to extract strings from adml file, and merge them back. The very simple `adml.its` file in this repository should be copied into e.g. `/usr/local/share/itstool/its/`. It sets one `preserveSpaceRule`.

Create the pot from the adml file (in the `en-US` directory):

    itstool -o LibreOffice-adml.pot LibreOffice.adml

Merge the translated strings to the adml file:

    itstool -m LibreOffice-adml.mo -o it-IT/ LibreOffice.adml
