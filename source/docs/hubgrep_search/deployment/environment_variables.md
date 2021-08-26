# Environment Variables


## General

**HUBGREP_SQLALCHEMY_DATABASE_URI**  (default `False`)  
Where to find the database.  
(see <https://docs.sqlalchemy.org/en/14/core/engines.html#database-urls>)

**HUBGREP_SECURITY_PASSWORD_SALT** (default `False`)  
The salt for the user passwords.  
(see <https://pythonhosted.org/Flask-Security/configuration.html>)

**HUBGREP_SECRET_KEY** (default `False`)  
Used for signing the session cookie when logged in.  
(see <https://flask.palletsprojects.com/en/1.1.x/config/#SECRET_KEY>)

**HUBGREP_ABOUT_MARKDOWN_FILE**  (default `"hubgrep_about.md"`)  
Path to a markdown file to use as the about page.

**HUBGREP_INDEXER_URL**  (default `https://indexer.hubgrep.io/`)  
Domain of the indexer, to fetch updates for your local search index.
In case the indexer is down, we usually have a fairly recent copy of the data at `https://indexer.hubgrep.io/dummydata`

**HUBGREP_MANTICORE_HOST**  (default `manticore`)
The servername of manticore, out search backend.


## Mail

The following environment vars are passed to Flask-Mail.  
(see <https://pythonhosted.org/Flask-Mail/#configuring-flask-mail> for details)

**HUBGREP_MAIL_DEBUG**

**HUBGREP_MAIL_SERVER**

**HUBGREP_MAIL_PORT**

**HUBGREP_MAIL_USE_TLS**

**HUBGREP_MAIL_USE_SSL**

**HUBGREP_MAIL_USERNAME**

**HUBGREP_MAIL_PASSWORD**

**HUBGREP_MAIL_DEFAULT_SENDER**

**HUBGREP_MAIL_MAX_EMAILS**


## Contact in about page

used for online contact information - all optional (default `None`)

**HUBGREP_CONTACT_DESCRIPTION**
**HUBGREP_CONTACT_ADDRESS**
**HUBGREP_CONTACT_EMAIL**
**HUBGREP_CONTACT_PHONE**
