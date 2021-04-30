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

**HUBGREP_HOSTING_SERVICE_REQUEST_TIMEOUT** (default `2`)
Timeout used for requests to Hosting Services.  
Setting `2` means two seconds of time until connection is established, and then two seconds to read the content, so you end up at a maximum of four seconds before timeout.  
(see <https://docs.python-requests.org/en/master/user/advanced/#timeouts>)

**HUBGREP_ABOUT_MARKDOWN_FILE**  (default `"hubgrep_about.md"`)  
Path to a markdown file to use as the about page.


## Cache

**HUBGREP_CACHE_BACKEND**   (default `None`)  
The cache backend used to store the Hosting Service responses.  
Possible values are `'none'`, `'redis'` and `'memory'`.  
In case of 'redis', HUBGREP_REDIS_URL needs to be set.

**HUBGREP_CACHE_TIME**  (default `3600`)  
Amount of seconds to cache the Hosting Service responses.

**HUBGREP_REDIS_URL** (default `None`)  
Redis URL to use.  
Accepts `redis-py` URLs (see <https://redis-py.readthedocs.io/en/stable/#redis.ConnectionPool.from_url>)


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
