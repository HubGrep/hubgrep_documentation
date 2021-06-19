## Localization

Using Flask-Babel, we generate catalogues by first extracting strings from the application. Strings from templates and
from code which uses "gettext" will be extracted into a .pot file which we then fill in translations for.

* First extract:

        pybabel extract -F babel.cfg -o messages.pot hubgrep

* MANUALLY fill in translation texts in empty "msgstr" fields in the `.pot` file.
* Update existing localization file or init a new one (if the lang doesn't previously exist in `/hubgrep/translations):
  
  Note: `YOUR_LANG` will be matched against language codes as recieved from Accept-Language in request headers. 
        These should resolve to defaults if specific header lang is not found; example `de-DE` should still use the `de` translation if not found. Finally, strings from code and templates are used as a last default.

        pybabel init -l [YOUR_LANG] -i messages.pot -d hubgrep/translations
        
        - OR -
        
        pybabel update -i messages.pot -d hubgrep/translations
    
* Lastly, compile the localization file for usage:

        pybabel compile -d hubgrep/translations -l [YOUR_LANG]
    
Strings should now be replaced by the appropriate locale variant when rendered.
